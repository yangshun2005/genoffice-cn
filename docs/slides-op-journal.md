# 幻灯片：操作日志（协作基础）

状态：基础已落地；尚无网络传输。同进程共享已可用：
两个附加到同一个 `Session` 的 webContents（对已打开文件执行 `slides:open-path`，演示者观众）通过
`scheduleDeckBroadcast` 接收 `slides:deck-changed` 推送——这是"一方编辑，另一方看到"循环的第一个消费者。从 shell UI 触达它需要一个第二窗口或
分屏视图，而 shell 目前还没有这些（它会聚焦已有的标签页）。

## 现有内容

Slides 中的每一次文档变更都流经操作执行器（`runTxn`），并且每一个**已应用**的事务现在都会追加到按会话划分的日志中
（`apps/slides/src/main/session-state.ts` 中的 `Session.opLog`）：

```ts
interface OpLogEntry {
  seq: number // monotonic per session
  source: 'edit' | 'batch' | 'script' | 'generate' | 'reset'
  ops: Array<{ op: Op; slideId?: string; created?: string[] }>
}
```

- `edit` — UI 垫片和专用 AI 工具（`slides:edit-text`、填充、变换、表格、母版编辑等）
- `batch` — `apply_ops`（`slides:apply-txn`）
- `script` — `execute_slide_script`（`slides:apply-edit-script`）
- `generate` — 生成页面落地（`slides:land-generated-pages`），现在以
  `insertSlidePptx` 操作落地页面，而不是直接变更演示文稿
- `reset` — 发生了快照恢复（撤销/重做/AI 回滚）；日志
  无法将其表达为操作，因此消费者必须越过它进行完全重新同步

`slideId` 是执行器在应用时打上的持久 id；`created` 携带
由增量操作铸造的 id。载荷（例如图片字节、提取的页面
源）按原样保留；环形缓冲区上限为 200 条。

唯一的汇聚点是 `slides-main.ts` 中的 `journaledTxn`——模块中每一次非 dry 的 `runTxn`
调用都经过它。不要在 IPC
处理程序中添加直接的 `runTxn` 调用。

## 传输层仍需要的内容（第二阶段）

1. **排序权威。** 日志是按主进程划分的。多用户需要一个
   服务器来对操作排序并分发它们；客户端通过同一个执行器应用远程条目。
2. **内容寻址资源。** `addPicture` / `insertSlidePptx` 载荷以内联方式携带
   字节；传输层应将其替换为内容哈希加上一个
   上传通道。
3. **用于撤销的逆操作。** 目前撤销是基于快照的，这就是为什么恢复
   在日志中记录为 `reset`。`OpRecord.before` 已经被捕获；
   推导逆操作可以移除大多数 `reset` 标记。
4. **派生状态保持本地。** 文本操作之后的自动适配缩放/字体缩放回写
   是由每个客户端的后处理阶段完成的确定性重新推导；
   它们是演示文稿变更但不会作为操作记入日志——远程对等方通过
   相同的垫片路径重放文本操作来重新推导它们。
5. **整副替换。** `replace` 模式下的 `generate_deck` 会构建一个新的
   会话（新的文档标识）；日志重新开始。传输层应
   将其视为"打开一个不同的文档"。
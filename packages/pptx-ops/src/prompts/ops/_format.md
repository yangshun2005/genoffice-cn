# Op 文档格式（编写指南——不会加载进任何提示词）

`ops/*.md` 文件是模型了解规范编辑 op 的唯一事实来源。`shared/op-docs.ts` 在导入时将其解析为 `OP_DOCS`；`opVocabulary()` / `opUsage()` / `opSignatureIndex()` / `opGuide()` 均由该解析结果派生。`apps/slides/tests/op-docs*.test.ts` 中的测试断言：文档与 op 注册表完全一致、每个示例都能通过 fixture deck 校验、文件中不含 CJK 文本。

## 文件布局

```
# <分组标题>
> <load_guide 目录中显示的一行摘要>

<可选的分组级说明：寻址、单位、约定>

### <opName>
`<signature>`

<说明、字段表、示例、常见错误、相关 op>

### <nextOpName> (not-ai-callable)
`<signature>`
...
```

- 每个分组一个文件；文件名即分组 id（`text`、`element`、`insert`、`table`、`slide`、`deck`）。
- 一个块从 `### <opName>` 开始；`opName` 必须匹配已注册的 op。
- 标题后第一个非空行是**签名**，用单反引号包裹。它会原样输出为引导错误中的 `Usage: <opName> <signature>`，因此保持紧凑、不要含反引号。
- 标题括号中的后缀用于设置标志：`(not-ai-callable)` 将该 op 从词汇表和签名索引中隐藏（模型无法生成的字节 / 剪贴板 / 部件路径载荷）；`(pending)` 在注册分支合入前将其完全隐藏。可组合为 `(not-ai-callable, pending)`。
- AI 可调用 op 块内的每个 ```json 围栏代码块都是一个示例，测试套件会通过 `runTxn(dryRun)` 运行它。使用下面的占位符 id；测试会从其 fixture deck 中替换为真实 id。

## 示例中的占位符 id

| 占位符       | Fixture 元素                    |
| ------------ | ------------------------------- |
| `e_TEXT`     | 幻灯片 0 上的文本框             |
| `e_SHAPE`    | 幻灯片 0 上的圆角矩形           |
| `e_PICTURE`  | 幻灯片 0 上的图片               |
| `e_TABLE`    | 幻灯片 0 上的 2x2 表格          |
| `e_CHART`    | 幻灯片 0 上的柱状图             |
| `e_LINE`     | 幻灯片 0 上的直线连接符         |
| `e_GROUP`    | 幻灯片 0 上的组合               |
| `e_CHILD`    | 该组合的直接子元素              |
| `SECTION_ID` | 一个已存在的节 GUID             |

fixture deck 恰好有两张幻灯片（索引 0 和 1；持久 id 为 `s_1` 和 `s_2`）。

## 编写规则

- 仅用英文。示例文本内容（标题、标签、类别）也用英文。
- 除非字段名另有说明（`...Pt`、`...Pct`、`...Deg`），单位均为文档空间 EMU。请在字段表中注明。
- 字段表列出 op 的 `validate` / `apply` 读取的每个字段，而不只是签名中的字段。
- "常见错误"条目描述模型容易出错的地方及纠正措施，语气与引导错误一致。
- 每个分组文件保持在约 8 KB 以内；超出时应将分组拆分为子文件（并添加目录条目）。
```
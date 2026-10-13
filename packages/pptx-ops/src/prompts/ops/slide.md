# 幻灯片操作

> 整页操作：删除、复制、插入空白页或按版式插入、移动、背景、隐藏、切换、自动前进、动画、演讲者备注、评论。

幻灯片操作只接受 `target:{slide}`。`slide` 是 0 起始的索引，或大纲中持久化的 `"s_<n>"` id。结构性操作（删除、复制、插入、移动）会改变后续索引；在同一事务中批量执行时，后续操作仍按实时演示文稿解析，因此优先使用持久化 id，或按从最后一页到第一页的顺序排列批次。

### deleteSlide

`{}`

删除该页。演示文稿必须至少保留一张幻灯片。

```json
{ "op": "deleteSlide", "target": { "slide": 1 } }
```

### duplicateSlide

`{}`

在该页之后插入副本。`clearText:true` 会清空文本框，使副本成为保留版式的空白页。
副本落在源索引 + 1 处；结果只回显源 target，因此填充新页时请按该索引寻址。

```json
{ "op": "duplicateSlide", "target": { "slide": 0 } }
```

```json
{ "op": "duplicateSlide", "target": { "slide": 0 }, "clearText": true }
```

### addBlankSlide

`{} — 插入到 target.slide 之后`

在其后插入一张新的空白页（版式和背景与 `target.slide` 相同）。

```json
{ "op": "addBlankSlide", "target": { "slide": "s_1" } }
```

### addSlideWithLayout

`{layout:<name>|<index>} — 插入到 target.slide 之后（默认：最后一页之后）`

插入一页并绑定到演示文稿的某个版式，该版式的占位符作为空提示框。`layout` 是版式的画廊名称，或 `slides read --layouts` 列出的 0 起始索引；引用未命中时错误会列出所有版式。新幻灯片的 id 在 `created` 中报告。

```json
{ "op": "addSlideWithLayout", "target": { "slide": "s_1" }, "layout": "Blank" }
```

常见错误

- 从其他演示文稿猜测版式名称：先用 `slides read --layouts` 列出。
- 在同一批次中填充新占位符：它们只在插入后才获得 id；先 `slides read` 新幻灯片，再 `setText`。

### pasteSlide（不可由 AI 调用）

`{afterIndex,bundle|png,mode?} — 剪贴板载荷`

从内部剪贴板粘贴复制的幻灯片包。

### insertSlidePptx（不可由 AI 调用）

`{source,at?,replace?} — 生成页落地载荷（使用 generate_deck/regenerate_slide）`

将生成的一页 pptx 落入演示文稿；由生成工具调用。

### moveSlide

`{to} — 0 起始的目标索引`

将页面移动到新位置。

```json
{ "op": "moveSlide", "target": { "slide": 1 }, "to": 0 }
```

### setSlideLayout

`{layout?:<name>|<index>} — 省略：将占位符吸附回当前版式`

将页面重新链接到另一个版式（现有形状保持原位；缺失的版式占位符作为空提示框添加）。不带 `layout` 时重新应用当前版式，将占位符移回其版式位置。

```json
{ "op": "setSlideLayout", "target": { "slide": 0 }, "layout": 0 }
```

### setBackground

`{kind:"solid"|"gradient"|"reset"|"graphics"|"image",color?,from?,to?,angleDeg?,radial?,hidden?} — image 类型需要字节源（使用 set_slide_background）`

页面背景。作为背景的满版装饰矩形会随之重新着色。每个操作一张幻灯片；要设置"所有页面"，在同一事务中为每张幻灯片发送一个操作。

| 类型         | 字段                                 | 说明                                                                                  |
| ------------ | ------------------------------------ | ------------------------------------------------------------------------------------- |
| `"solid"`    | `color`                              | `"#RRGGBB"`                                                                           |
| `"gradient"` | `from`, `to`, `angleDeg?`, `radial?` | 双色渐变；`angleDeg` 以度为单位（默认 0）；`radial:true` 忽略角度                     |
| `"reset"`    | 无                                   | 移除页面覆盖并继承版式/母版背景                                                       |
| `"graphics"` | `hidden`                             | `true` 在此页隐藏母版的背景图形                                                       |
| `"image"`    | `source`                             | 字节或媒体部件载荷；无法从 `apply_ops` 使用                                           |

```json
{ "op": "setBackground", "target": { "slide": 0 }, "kind": "solid", "color": "#0B1F3A" }
```

```json
{
  "op": "setBackground",
  "target": { "slide": 1 },
  "kind": "gradient",
  "from": "#0B1F3A",
  "to": "#1A73E8",
  "angleDeg": 90
}
```

```json
{ "op": "setBackground", "target": { "slide": 1 }, "kind": "reset" }
```

常见错误

- 深色背景未调亮文字：随后对页面文字执行 `setFont` 颜色更改。
- 从模型使用 `kind:"image"`：请使用图片工具；该操作需要字节。

### setHidden

`{hidden:boolean}`

在幻灯片放映中隐藏或显示该页（仍保留在演示文稿中）。

```json
{ "op": "setHidden", "target": { "slide": 1 }, "hidden": true }
```

### setTransition

`{kind:"none"|"fade"|"push"|"wipe"|…}`

幻灯片切换。接受的类型：`none`、`morph`、`fade`、`push`、`wipe`、`split`、`circle`、`cover`、`pull`、`dissolve`、`zoom`、`random`。

```json
{ "op": "setTransition", "target": { "slide": 0 }, "kind": "fade" }
```

常见错误

- 使用其他工具的名称如 `"slide"` 或 `"cut"`：只接受上面列出的类型；错误会列出它们。

### setAdvanceTime

`{ms:number|null} — 自动前进；null 清除`

在给定毫秒数后自动前进；`null` 恢复为点击前进。

```json
{ "op": "setAdvanceTime", "target": { "slide": 0 }, "ms": 5000 }
```

### setAnimations（不可由 AI 调用）

`{items:[{spid,effect,trigger,durationMs,delayMs,…}]} — 按 spid 寻址（cNvPr id），尚无 id 转换`

重写页面的动画时间线；按原始形状 id 寻址，因此目前由 UI 动画面板负责。

### addAnimation

`{effect,kind?,trigger?,duration?,delay?,direction?,paragraph?,motionPath?,presetXml?,after?} — target:{slide, el}；向页面时间线追加一个效果`

为元素在页面时间线末尾（或紧接位置 `after` 之后）添加一个动画。时间线在 `slides read` 中以 `animations[]` 读回，每项包含其 `seq`（0 起始位置）、`el`、`effect`、`kind`、`trigger`、`durationMs`、`delayMs`。

| 字段       | 类型                                                                                                                                                                                                                                                                                   | 说明                                                                                                                                             |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| effect     | 进入 `appear` `fade` `flyIn` `wipe` `wipeDown` `splitIn` `bounce` `flipIn` `zoom`；强调 `pulse` `spin` `grow` `teeter`；退出 `disappear` `fadeOut` `flyOut` `wipeOut` `shrink` `zoomOut`；`motionPath`；媒体 `mediaPlay` `mediaPause` `mediaStop`（仅视频/音频元素） | 除非给出 `presetXml`，否则必填                                                                                                                   |
| kind       | `"entrance"` / `"emphasis"` / `"exit"` / `"path"` / `"media"`                                                                                                                                                                                                                          | 可选交叉校验；与效果不匹配时拒绝                                                                                                                 |
| trigger    | `"onClick"`（默认）/ `"withPrev"` / `"afterPrev"`                                                                                                                                                                                                                                      | `withPrev` 与前一个效果同时开始，`afterPrev` 在其结束后开始                                                                                       |
| duration   | 毫秒 >= 0                                                                                                                                                                                                                                                                              | 每个效果的默认值（appear 0、fade 500、spin 2000……）；也接受 `durationMs`                                                                          |
| delay      | 毫秒 >= 0                                                                                                                                                                                                                                                                              | 默认 0；也接受 `delayMs`                                                                                                                         |
| direction  | `"top"` / `"bottom"` / `"left"` / `"right"`                                                                                                                                                                                                                                            | 仅用于 `flyIn`、`flyOut`、`wipe`、`wipeOut`（默认 bottom）                                                                                        |
| paragraph  | 0 起始索引                                                                                                                                                                                                                                                                             | 为文本正文的某一段落设置动画，而非整个形状                                                                                                       |
| motionPath | `"M 0 0 L 0.25 0"`                                                                                                                                                                                                                                                                     | 配合 `effect:"motionPath"`；坐标为幻灯片尺寸的比例                                                                                               |
| presetXml  | 一个 `<p:par>…</p:par>` 块                                                                                                                                                                                                                                                             | 从 PowerPoint 为列表外的预设逐字导出的效果；每个 `<p:spTgt spid>` 必须是此元素的形状 id；逐字节保留                                                  |
| after      | seq                                                                                                                                                                                                                                                                                    | 紧接该时间线位置之后插入，而非追加                                                                                                               |

```json
{
  "op": "addAnimation",
  "target": { "slide": 0, "el": "e_TEXT" },
  "effect": "flyIn",
  "direction": "left",
  "trigger": "afterPrev",
  "duration": 600
}
```

### removeAnimation

`{seq} — target:{slide}；或 target:{slide, el} 删除该元素的所有动画`

按 `seq` 移除一个时间线项，或移除针对某元素的所有项。后续项会重新编号；下一批次前请重新读取页面。

```json
{ "op": "removeAnimation", "target": { "slide": 0, "el": "e_TEXT" } }
```

### reorderAnimation

`{seq,to} — target:{slide}；移动一个时间线项`

将 `seq` 处的项移动到位置 `to`（均为 0 起始，位于时间线内）。

```json
{ "op": "reorderAnimation", "target": { "slide": 0 }, "seq": 2, "to": 0 }
```

### setNotes

`{text} — 演讲者备注`

替换页面的演讲者备注（段落以换行分隔）。空字符串清除它们。备注不影响画布。

```json
{
  "op": "setNotes",
  "target": { "slide": 0 },
  "text": "Open with the headline number.\nPause for questions before the next section."
}
```

### addComment

`{text,author}`

向页面添加审阅评论。

```json
{
  "op": "addComment",
  "target": { "slide": 0 },
  "text": "Consider a stronger verb in the title.",
  "author": "AI Assistant"
}
```

### deleteComment

`{authorId,idx}`

移除由作者 id 和该页该作者评论中的索引标识的评论（两者均来自评论面板数据）。

```json
{ "op": "deleteComment", "target": { "slide": 0 }, "authorId": 0, "idx": 0 }
```
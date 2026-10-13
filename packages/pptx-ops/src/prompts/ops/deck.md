# 演示文稿操作

> 无目标的演示文稿级操作：页面尺寸、查找替换、页眉页脚、主题、节。

演示文稿操作不带 `target`。它们影响每张幻灯片（或演示文稿的元数据），因此请先阅读演示文稿大纲，当请求含义不明确时与用户确认范围。

### setSlideSize

`{cx,cy} — EMU 页面尺寸，整个演示文稿`

更改整个演示文稿的页面尺寸。元素位置不会重新缩放；需要重新排版内容时，请接着调用 `execute_slide_script`。
常用尺寸：16:9 为 12192000 x 6858000，4:3 为 9144000 x 6858000。

```json
{ "op": "setSlideSize", "cx": 12192000, "cy": 6858000 }
```

### findReplace

`{find,replace,matchCase?,slideIndex?} — 默认整个演示文稿，除非指定 slideIndex`

在文本框、形状、表格单元格和直接组子项内的 run 中替换文本。跨越两个格式不同 run 的匹配不会被替换。

| 字段       | 类型             | 说明                                        |
| ---------- | ---------------- | ------------------------------------------- |
| find       | 非空字符串       |                                             |
| replace    | 字符串           | 可为空以删除文本                            |
| matchCase  | 布尔值           | 默认 false                                  |
| slideIndex | 整数             | 限定到某一页                                |
| elementId  | 字符串           | 限定到某个元素（需配合 `slideIndex`）       |
| firstOnly  | 布尔值           | 仅替换第一个匹配                            |

```json
{ "op": "findReplace", "find": "2023", "replace": "2024" }
```

```json
{
  "op": "findReplace",
  "find": "Acme Corp",
  "replace": "Acme Corporation",
  "matchCase": true,
  "slideIndex": 0
}
```

常见错误

- 期望返回零更改的报告：无匹配时该操作会失败，因此"未找到"错误是正常反馈，而非故障。

### applyHeaderFooter

`{settings:{footer?,slideNum?,date?,dateAuto?}} — 每张幻灯片`

在每一页设置页脚文本、幻灯片编号和日期（通过母版的占位符）。

| 字段              | 类型             | 说明                                          |
| ----------------- | ---------------- | --------------------------------------------- |
| settings.footer   | 字符串或 `null`  | `null` 或空字符串隐藏页脚                     |
| settings.slideNum | 布尔值           | 显示页码                                      |
| settings.date     | 字符串或 `null`  | 固定日期文本；`null` 或空字符串隐藏           |
| settings.dateAuto | 布尔值           | 在 PowerPoint 中更新的动态日期字段            |

```json
{
  "op": "applyHeaderFooter",
  "settings": { "footer": "Acme Corporation - Confidential", "slideNum": true }
}
```

常见错误

- 重复发送相同的设置：该操作会将"无更改"作为错误报告；当值已就位时请跳过。

### setSections

`{sections:[{id,name,slideIndices},…]} — 完全替换`

替换整个节列表。每个节按顺序列出其幻灯片的从 0 开始的索引；每张幻灯片应恰好属于一个节。Id 是带花括号的 GUID；复用现有 id 以保持节的标识，为新节生成新 GUID。

```json
{
  "op": "setSections",
  "sections": [
    { "id": "SECTION_ID", "name": "Introduction", "slideIndices": [0] },
    { "id": "{6F1D2B0A-4C3E-4F58-9A21-0D7E5B3C9A11}", "name": "Details", "slideIndices": [1] }
  ]
}
```

相关：单项更改请用 `addSection`、`renameSection`、`removeSection`、`moveSection`。

### applyTheme

`{name,colors:{dk1?,lt1?,dk2?,lt2?,accent1?..accent6?,hlink?,folHlink?},majorFont?,minorFont?} — "#RRGGBB" 槽位，整个演示文稿`

重写整个演示文稿的主题配色方案（以及可选的标题/正文字体），并重新映射与旧方案匹配的显式颜色。没有自己背景的页面将获得新的 `lt1` 颜色。

| 字段      | 类型                                  | 说明                                                                                                   |
| --------- | ------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| name      | 非空字符串                            | 写入文件的主题名称                                                                                     |
| colors    | 方案槽位到 `"#RRGGBB"` 的对象         | 槽位：`dk1`、`lt1`、`dk2`、`lt2`、`accent1`..`accent6`、`hlink`、`folHlink`；六位十六进制，无 alpha     |
| majorFont | 字符串                                | 标题字体                                                                                               |
| minorFont | 字符串                                | 正文字体                                                                                               |

```json
{
  "op": "applyTheme",
  "name": "Ocean",
  "colors": {
    "dk1": "#0B1F3A",
    "lt1": "#FFFFFF",
    "dk2": "#1F3B5C",
    "lt2": "#E8F0FE",
    "accent1": "#1A73E8",
    "accent2": "#34A853",
    "accent3": "#FBBC04",
    "accent4": "#EA4335",
    "accent5": "#9AA0A6",
    "accent6": "#5F6368",
    "hlink": "#1A73E8",
    "folHlink": "#7B1FA2"
  },
  "majorFont": "Georgia",
  "minorFont": "Calibri"
}
```

常见错误

- 方案颜色带 alpha（`"#RRGGBBAA"`）：主题槽位只接受六位十六进制。
- 将 `colors` 作为数组传入：它是槽位到颜色的对象。

### addSection

`{atSlideIndex,name}`

在给定幻灯片处开始一个新节（该幻灯片及其后直到下一节之前的幻灯片移入其中）。

```json
{ "op": "addSection", "atSlideIndex": 1, "name": "Appendix" }
```

### renameSection

`{id,name}`

```json
{ "op": "renameSection", "id": "SECTION_ID", "name": "Overview" }
```

### removeSection

`{id} — 保留幻灯片`

移除节标题；其幻灯片并入前一个节。

```json
{ "op": "removeSection", "id": "SECTION_ID" }
```

### moveSection

`{id,dir:"up"|"down"}`

将该节（连同其所有幻灯片）与相邻节交换。

```json
{ "op": "moveSection", "id": "SECTION_ID", "dir": "down" }
```
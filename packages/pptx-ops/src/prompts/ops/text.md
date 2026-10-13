# 文本操作

> 替换或重设文本框、形状或表格的文本样式：整体重写（setText）、按 run 修补字体（setFont）、修补段落格式（setParagraphFormat）、排版数学公式（insertEquation）。

三者都接受 `target:{slide, el}`。`el` 是大纲或 `read_slide` 中的元素 id（`e_*` id 是持久化的）。若目标是组合的直接子元素，把子元素 id 填入 `target.el`，并加上 `group:"<group id>"`。

字号单位为磅。颜色为 `"#RRGGBB"`。

### setText

`{paragraphs:[{runs:[{text,bold?,italic?,fontSize?,color?}],align?}]}（组合子元素：加上 group:"<group id>"）`

用给定段落替换元素的全部文本。未重设样式的 run 会按位置继承它所替换 run 的格式，因此纯 `{text}` run 会保留原有字号、颜色和字体。从未有过文本的形状会创建文本主体（自选图形默认文本居中）。

| 字段                                                     | 类型                                                                                          | 说明                                                                                                                                                                                                                   |
| -------------------------------------------------------- | --------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| paragraphs                                               | array                                                                                         | 必填，每个段落一个对象；空数组会清空文本                                                                                                                                                                               |
| paragraphs[].runs                                        | `{text, bold?, italic?, underline?, strike?, fontSize?, fontFamily?, color?, link?}` 的数组 | `fontSize` 单位为磅；`link` 为 `{kind:"url",url}`、`{kind:"slide",slideIndex}`、`{kind:"action",action}`（`nextslide` / `previousslide` / `firstslide` / `lastslide` / `lastslideviewed` / `endshow`）或 `null` 表示移除 |
| paragraphs[].align                                       | `"left"` / `"center"` / `"right"` / `"justify"`                                               | 可选                                                                                                                                                                                                                   |
| paragraphs[].level                                       | 0..8                                                                                          | 多级列表的缩进级别                                                                                                                                                                                                     |
| paragraphs[].bullet                                      | `"char"` / `"number"` / `"none"`                                                              | 可选；`bulletChar` 设置自定义字形                                                                                                                                                                                      |
| paragraphs[].lineSpacingPct, spaceBeforePt, spaceAfterPt | number                                                                                        | 可选，段落间距                                                                                                                                                                                                         |
| paragraphs[].rtl                                         | boolean                                                                                       | 可选，基础方向                                                                                                                                                                                                         |
| group                                                    | string                                                                                        | 仅用于组合的直接子元素：组合 id                                                                                                                                                                                        |

```json
{
  "op": "setText",
  "target": { "slide": 0, "el": "e_TEXT" },
  "paragraphs": [
    { "runs": [{ "text": "Quarterly Review", "bold": true, "fontSize": 36 }], "align": "left" },
    { "runs": [{ "text": "Q3 highlights and outlook" }] }
  ]
}
```

```json
{
  "op": "setText",
  "target": { "slide": 0, "el": "e_CHILD" },
  "group": "e_GROUP",
  "paragraphs": [{ "runs": [{ "text": "Step 1" }] }]
}
```

常见错误

- 只传改动的段落：数组会替换整个主体，所以要发送所有应保留的段落。
- 以图片、图表或连接线为目标：只有文本框、形状和表格单元格（`setTableCell`）能承载文本。
- 向组合子元素写入文本时未加 `group`：仅凭子元素 id 无法在幻灯片上解析。

相关：`setFont`（不改文字只重设样式）、`setTableCell`（表格单元格）、`findReplace`（整份演示文稿替换）。

### setFont

`{font:{fontFamily?,fontSizePt?,fontSizeStep?,bold?,italic?,underline?,strike?,color?}} — 合并到元素的每个 run 上`

将给定属性应用到元素的每个 run（或表格的每个单元格），其余保持不变。用于"把标题改成蓝色加粗"这类请求；文字有变化时用 `setText`。

| 字段                                 | 类型        | 说明                                     |
| ------------------------------------ | ----------- | ---------------------------------------- |
| font.fontFamily                      | string      | 省略则保留主题字体（推荐）               |
| font.fontSizePt                      | number > 0  | 磅                                       |
| font.fontSizeStep                    | {dir, mode} | 按 run 相对调整：'ladder' 档位或 'point' ±1 |
| font.bold, italic, underline, strike | boolean     | 只有传入的键会改变                       |
| font.color                           | `"#RRGGBB"` | 显式颜色；清除主题色继承                 |
| group                                | string      | 仅用于组合的直接子元素                   |

```json
{
  "op": "setFont",
  "target": { "slide": 0, "el": "e_TEXT" },
  "font": { "color": "#1A73E8", "bold": true }
}
```

```json
{ "op": "setFont", "target": { "slide": 0, "el": "e_TABLE" }, "font": { "fontSizePt": 12 } }
```

常见错误

- 使用 `"blue"` 这类颜色名：只接受十六进制 `"#RRGGBB"`。
- `fontSizePt` 为 0 或负数：必须是正数的磅值。
- 期望只改部分 run：该修补作用于整个元素；要改单个词请用 `setText` 并逐 run 设置样式。

### setParagraphFormat

`{format:{align?,bullet?,lineSpacingPct?,spaceBeforePt?,spaceAfterPt?}}`

对元素的每个段落设置段落级格式：对齐、项目符号、间距、方向、缩进级别。

| 字段                                      | 类型                                            | 说明                                  |
| ----------------------------------------- | ----------------------------------------------- | ------------------------------------- |
| format.align                              | `"left"` / `"center"` / `"right"` / `"justify"` |                                       |
| format.bullet                             | `"char"` / `"number"` / `"none"`                | `"char"` 使用 `bulletChar` 或圆点符号 |
| format.bulletChar                         | string                                          | 自定义字形，配合 `bullet:"char"`      |
| format.bulletSizePct                      | number >= 0                                     | 文本大小的百分比（100 = 相同）        |
| format.bulletColor                        | `"#RRGGBB"`                                     |                                       |
| format.bulletHangEmu                      | number >= 0                                     | 悬挂缩进，单位 EMU                    |
| format.lineSpacingPct                     | number >= 0                                     | 100 = 单倍行距                        |
| format.spaceBeforePt, format.spaceAfterPt | number >= 0                                     | 磅                                    |
| format.rtl                                | boolean                                         | 基础方向                              |
| format.indentDelta                        | 1 或 -1                                         | 移动列表级别（限制在 0..8）           |
| group                                     | string                                          | 仅用于组合的直接子元素                |

```json
{
  "op": "setParagraphFormat",
  "target": { "slide": 0, "el": "e_TEXT" },
  "format": { "bullet": "char", "lineSpacingPct": 120, "spaceAfterPt": 6 }
}
```

常见错误

- 间距值为负：所有 `...Pct` / `...Pt` / `...Emu` 字段都必须 >= 0。
- 用 `setParagraphFormat` 改字号：那是 run 属性，请用 `setFont`。

### insertEquation

`{latex,position?} — target:{slide, el}；或用 {latex,box:{x,y,cx,cy}} 为它创建文本框`

在文本或形状元素的 `position`（`"end"`，默认，或 `"start"`）处添加一个排版好的公式（PowerPoint 自带的数学格式）作为居中段落，或在 `box`（EMU，允许单位后缀）处的新文本框中添加。较旧的阅读器和 GenOffice 预览显示线性化文本（`E=mc²`）；PowerPoint 2010+ 会渲染公式。LaTeX 子集：`\frac`、`\sqrt[n]`、`^`、`_`、带上下限的 `\sum`/`\int`/`\prod`、`\left(` `\right)`、矩阵、希腊字母、重音符号、`\text{}`。

```json
{
  "op": "insertEquation",
  "target": { "slide": 0, "el": "e_TEXT" },
  "latex": "E = mc^2"
}
```

```json
{
  "op": "insertEquation",
  "target": { "slide": 0 },
  "box": { "x": 914400, "y": 2743200, "cx": 4572000, "cy": 914400 },
  "latex": "\\frac{a}{b} + \\sqrt{x^2 + y^2}"
}
```
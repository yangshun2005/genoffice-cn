# 插入操作

> 在幻灯片上创建新元素：文本框、预设形状和线条（addElement）、粘附到形状的连接线、表格、原生图表、SmartArt 风格图示。

插入操作接收 `target:{slide}`（不含 `el`）和文档空间 EMU 中的 `offset:{x,y,cx,cy}` 框架。它们会在 `created` 中报告新元素 id；同一事务中后续操作尚不能引用它，因此先插入，在下一次调用中设置样式，或在操作支持时内联传入样式。

### addElement

`{kind:"textbox"|<preset geometry>,offset:{x,y,cx,cy},paragraphs?,fill?,stroke?,adjustments?:{<gd name>:val},bodyPr?:{autoFit?:"shrink"|"resize"}}`

添加文本框、预设几何形状或线条/连接线。

| 字段        | 类型                                                                                           | 说明                                                                                                                                                                                                                                              |
| ----------- | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kind        | string                                                                                         | `"textbox"`；预设几何形状（`rect`、`roundRect`、`ellipse`、`triangle`、`diamond`、`rightArrow`、`chevron`、`star5`、`hexagon`、`wedgeRoundRectCallout` 等）；或线条类型 `line`、`lineArrow`、`lineArrowDouble`、`lineBent`、`lineCurved` |
| offset      | `{x, y, cx, cy}` EMU                                                                           | 必填                                                                                                                                                                                                                                           |
| paragraphs  | `{runs:[{text, bold?, italic?, underline?, fontSize?, fontFamily?, color?}], align?}` 数组 | 可选文本；`fontSize` 单位为 pt                                                                                                                                                                                                                    |
| fill        | `"#RRGGBB"` 或 `"#RRGGBBAA"`                                                                   | 纯色填充；文本框默认无填充                                                                                                                                                                                                        |
| stroke      | `{color, widthEmu}`                                                                            | 轮廓；线条默认为 1 pt 黑色描边                                                                                                                                                                                                      |
| adjustments | `{<gdName>: number}`                                                                           | 预设调整值，例如 `{"adj": 25000}` 表示 roundRect 圆角半径                                                                                                                                                                                 |
| bodyPr      | `{autoFit?, wrap?, anchor?, insetsEmu?}`                                                       | `autoFit` 为 `"shrink"` 或 `"resize"`；`wrap` 为 `"square"`/`"none"`；`anchor` 为 `"t"`/`"ctr"`/`"b"`                                                                                                                                                       |

```json
{
  "op": "addElement",
  "target": { "slide": 1 },
  "kind": "textbox",
  "offset": { "x": 914400, "y": 685800, "cx": 7315200, "cy": 914400 },
  "paragraphs": [
    { "runs": [{ "text": "Key Takeaways", "bold": true, "fontSize": 32 }], "align": "left" }
  ],
  "bodyPr": { "autoFit": "shrink" }
}
```

```json
{
  "op": "addElement",
  "target": { "slide": 1 },
  "kind": "roundRect",
  "offset": { "x": 914400, "y": 2286000, "cx": 3200400, "cy": 1600200 },
  "fill": "#E8F0FE",
  "stroke": { "color": "#1A73E8", "widthEmu": 12700 },
  "adjustments": { "adj": 16667 },
  "paragraphs": [
    { "runs": [{ "text": "Card title", "bold": true, "color": "#1A73E8" }], "align": "center" }
  ]
}
```

```json
{
  "op": "addElement",
  "target": { "slide": 1 },
  "kind": "lineArrow",
  "offset": { "x": 4572000, "y": 3048000, "cx": 1828800, "cy": 0 }
}
```

常见错误

- 在空白演示文稿上逐元素构建整个页面：应使用 `generate_deck`；`addElement` 用于向已设计好的页面添加内容。
- 使用像素框架：用 `read_slide` 中的 px 转 EMU 系数进行转换。
- `autoFit` 值不是 `"shrink"`/`"resize"`。

### addConnector

`{from,to,kind?:"straight"|"elbow"|"curved",fromSide?,toSide?,arrow?:"none"|"end"|"both",line?:{color?,widthPt?,dash?}}`

绘制粘附到两个形状的连接线（`a:stCxn`/`a:endCxn`），因此 PowerPoint 及后续 `setTransform` 移动都会保持其附着。省略 `fromSide`/`toSide`（`top`/`left`/`bottom`/`right`）时，会选择彼此最接近的一对边中点。框架由两个连接点推导得出；新元素 id 在 `created` 中。

| 字段            | 类型                                    | 说明                                                                        |
| ---------------- | --------------------------------------- | ---------------------------------------------------------------------------- |
| from, to         | 元素 id                             | `target.slide` 上两个不同的顶层元素                           |
| kind             | `straight`（默认）、`elbow`、`curved` |                                                                              |
| fromSide, toSide | 边名称                               | 固定一端或两端；省略的边自动选择                 |
| arrow            | `none`、`end`（默认）、`both`         | 箭头位于 `to` 端、两端或无箭头                                |
| line             | `{color?, widthPt?, dash?}`             | 默认 1 pt 黑色实线；`dash` 为 OOXML 预设值（`dash`、`sysDot` 等） |

```json
{
  "op": "addConnector",
  "target": { "slide": 0 },
  "from": "e_SHAPE",
  "to": "e_PICTURE",
  "kind": "elbow",
  "line": { "color": "#1A73E8", "widthPt": 1.5 }
}
```

常见错误

- 用 `addElement` 绘制自由线条并期望它跟随形状：只有 `addConnector`（或带 `start`/`end` 的 `setConnectorEndpoints`）才会附着。
- 在组合子元素与形状之间使用：应连接到组合（仅限顶层 id）。

### addPicture（不可由 AI 调用）

`{bytes:base64|dataURL,ext?,offset} — 请改用 insert_web_image`

将图像字节嵌入为新图片。模型通过 `insert_web_image`（URL）插入图像，由主进程下载并居中裁剪。

### replacePicture（不可由 AI 调用）

`{bytes:base64|dataURL,ext?} — 请改用 replace_image`

就地替换图片的字节。模型使用带 URL 的 `replace_image`。

### addTable

`{rows,cols,offset:{x,y,cx,cy},colWidthsEmu?,rowHeightsEmu?,cellProps?:[[{gridSpan?,rowSpan?,hMerge?,vMerge?,anchor?}]]}`

插入使用 PowerPoint 默认样式的原生表格，单元格为空。之后用 `setTableCell` 填充单元格（每个单元格一个操作，从第一个结果得知表格 id 后，同一事务中即可）。

| 字段         | 类型                                                                | 说明                                                                    |
| ------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| rows, cols    | 整数 >= 1                                                        |                                                                          |
| offset        | `{x, y, cx, cy}` EMU                                                | 除非指定宽度/高度，否则列和行均分框架 |
| colWidthsEmu  | number[]                                                            | 恰好 `cols` 个正值                                           |
| rowHeightsEmu | number[]                                                            | 恰好 `rows` 个正值                                           |
| cellProps     | `{gridSpan?, rowSpan?, hMerge?, vMerge?, anchor?}` 的行数组 | 行优先；`anchor` 为 `"t"`/`"ctr"`/`"b"`；用于预合并表头      |

```json
{
  "op": "addTable",
  "target": { "slide": 1 },
  "rows": 3,
  "cols": 3,
  "offset": { "x": 914400, "y": 1371600, "cx": 7315200, "cy": 2286000 }
}
```

```json
{
  "op": "addTable",
  "target": { "slide": 1 },
  "rows": 2,
  "cols": 2,
  "offset": { "x": 914400, "y": 1371600, "cx": 5486400, "cy": 1371600 },
  "colWidthsEmu": [1828800, 3657600],
  "cellProps": [
    [{ "gridSpan": 2 }, { "hMerge": true }],
    [{}, {}]
  ]
}
```

常见错误

- `colWidthsEmu` 数量错误：必须为每列恰好列出一个宽度。
- 在此传入单元格文本：该操作创建空单元格；用 `setTableCell` 写入文本。

### addChart

`{kind:"bar"|"barStacked"|"line"|"area"|"pie"|"doughnut"|"scatter"|"radar"|"comboBarLine",categories:[…],series:[{name,values:[…]}],offset,title?,colorScheme?:["#RRGGBB"],holeSizePct?}`

插入原生、可在 PowerPoint 中编辑的图表。

| 字段       | 类型                                              | 说明                                                                                                                                                                                                     |
| ----------- | ------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kind        | 见签名                                     | `comboBarLine` 将最后一个系列绘制为次坐标轴上的折线                                                                                                                                        |
| categories  | string[]                                          | 至少一个；x 轴标签                                                                                                                                                                           |
| series      | `{name, values:number[]}` 数组                | 至少一个；每个 `values` 长度应与 `categories` 长度相等                                                                                                                                       |
| offset      | `{x, y, cx, cy}` EMU                              |                                                                                                                                                                                                           |
| title       | string                                            | 可选图表标题                                                                                                                                                                                      |
| colorScheme | `"#RRGGBB"[]`                                     | 可选系列颜色，循环使用；省略则跟随主题                                                                                                                                                  |
| holeSizePct | number                                            | 圆环孔径大小（10..90）                                                                                                                                                                               |
| barDir      | `"bar"`                                           | 可选：水平条形而非柱形                                                                                                                                                              |
| dataSource  | `"user"` / `"document"` / `"search"` / `"sample"` | 数字来源；由 apply_ops 在批次运行前检查（不属于操作本身）。`"search"` 需要本次对话中有 web_search；`"sample"` 数据必须向用户披露 |

```json
{
  "op": "addChart",
  "target": { "slide": 1 },
  "kind": "bar",
  "title": "Revenue by quarter",
  "categories": ["Q1", "Q2", "Q3", "Q4"],
  "series": [{ "name": "Revenue", "values": [120, 135, 150, 170] }],
  "offset": { "x": 914400, "y": 1371600, "cx": 7315200, "cy": 3657600 },
  "dataSource": "user"
}
```

```json
{
  "op": "addChart",
  "target": { "slide": 1 },
  "kind": "doughnut",
  "holeSizePct": 55,
  "categories": ["Direct", "Partner", "Online"],
  "series": [{ "name": "Share", "values": [45, 30, 25] }],
  "offset": { "x": 2743200, "y": 1371600, "cx": 3657600, "cy": 3657600 },
  "colorScheme": ["#1A73E8", "#34A853", "#FBBC04"]
}
```

常见错误

- 编造数字：每个值都需要来源（用户、演示文稿或本次对话中的搜索）；若无来源，使用示意性数值并向用户说明。
- `values` 比 `categories` 短或长。
- 用 `addChart` 编辑现有图表：应使用 `edit_chart` 工具，它会保留位置和 z 顺序。

### addSmartArt

`{layout,items:[…],offset}`

插入由组合形状构建的 SmartArt 风格图示。

| 字段  | 类型                                                                                     | 说明                     |
| ------ | ---------------------------------------------------------------------------------------- | ------------------------- |
| layout | `"list"` / `"process"` / `"cycle"` / `"hierarchy"` / `"pyramid"` / `"matrix"` / `"venn"` |                           |
| items  | string[]                                                                                 | 1..8 个节点文本，按顺序 |
| offset | `{x, y, cx, cy}` EMU                                                                     |                           |

```json
{
  "op": "addSmartArt",
  "target": { "slide": 1 },
  "layout": "process",
  "items": ["Discover", "Design", "Deliver"],
  "offset": { "x": 914400, "y": 1828800, "cx": 7315200, "cy": 1828800 }
}
```

### addMedia（不可由 AI 调用）

`{kind:"video"|"audio",bytes:base64|dataURL,ext,offset}`

嵌入视频或音频文件；字节载荷来自 UI 文件选择器。

### addModel3d（不可由 AI 调用）

`{bytes,ext,offset} — 字节载荷`

嵌入 3D 模型；字节载荷来自 UI 文件选择器。

### pasteElements（不可由 AI 调用）

`{items,dx,dy} — 剪贴板载荷`

粘贴复制的元素；载荷来自内部剪贴板。
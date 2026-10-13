# 表格操作

> 编辑已有表格元素：单元格文本、合并、行/列结构、行高、列宽、单元格锚点、样式预设和边框。

所有操作都接收 `target:{slide, el}`，其中 `el` 是表格的 id（大纲中类型为 `table`）。`row` 和 `col` 从 0 开始计数。图表编辑（`setChart`）位于 `edit_chart` 工具中。

### setTableCell

`{row,col,paragraphs}`

替换单个单元格的文本。未重新设置样式的 run 会继承单元格当前格式，因此纯 `{text}` run 会保留字号、颜色和加粗。

| 字段       | 类型                                                                                            | 说明                    |
| ---------- | ----------------------------------------------------------------------------------------------- | ----------------------- |
| row, col   | integer                                                                                         | 从 0 开始计数           |
| paragraphs | `{runs:[{text, bold?, italic?, fontSize?, color?}], align?, bullet?, lineSpacingPct?}` 的数组 | 与 `setText` 结构相同   |

```json
{
  "op": "setTableCell",
  "target": { "slide": 0, "el": "e_TABLE" },
  "row": 0,
  "col": 0,
  "paragraphs": [{ "runs": [{ "text": "Metric", "bold": true }], "align": "center" }]
}
```

常见错误

- 把单元格文本当作字符串传入：它必须是段落数组。
- 行或列超出网格范围：操作会报告出错的 (row, col)。

### tableMerge

`{kind:"merge-right"|"merge-down"|"split",row,col}`

将 (row, col) 处的单元格与其右侧或下方相邻单元格合并，或将已合并的单元格拆回其网格单元格。

```json
{
  "op": "tableMerge",
  "target": { "slide": 0, "el": "e_TABLE" },
  "kind": "merge-right",
  "row": 0,
  "col": 0
}
```

常见错误

- 跨越已有合并边界进行合并：操作会拒绝；请先拆分。

### tableStructure

`{kind:"insert-row"|"delete-row"|"insert-col"|"delete-col",index,before?}`

插入或删除一行或一列。除非 `before:true`，否则插入位置在 `index` 之后。

```json
{
  "op": "tableStructure",
  "target": { "slide": 0, "el": "e_TABLE" },
  "kind": "insert-row",
  "index": 1
}
```

```json
{
  "op": "tableStructure",
  "target": { "slide": 0, "el": "e_TABLE" },
  "kind": "delete-col",
  "index": 0
}
```

常见错误

- 含合并单元格的表格会拒绝行/列手术：请先拆分合并（`tableMerge` 配合 `kind:"split"`）。

### setTableRowHeight

`{row,hEmu}`

以 EMU 设置单行高度（表格框架会相应增大或缩小）。

```json
{ "op": "setTableRowHeight", "target": { "slide": 0, "el": "e_TABLE" }, "row": 0, "hEmu": 457200 }
```

### setTableCellAnchor

`{row,col,anchor:"top"|"middle"|"bottom"}`

单个单元格内文本的垂直对齐方式。

```json
{
  "op": "setTableCellAnchor",
  "target": { "slide": 0, "el": "e_TABLE" },
  "row": 0,
  "col": 1,
  "anchor": "middle"
}
```

### setTableColWidth

`{col,wEmu}`

以 EMU 设置单列宽度。

```json
{ "op": "setTableColWidth", "target": { "slide": 0, "el": "e_TABLE" }, "col": 0, "wEmu": 2743200 }
```

### setTableStyle

`{styleName} | {styleId?,firstRow?,lastRow?,firstCol?,lastCol?,bandRow?,bandCol?,keepFormatting?,shadingColor?,borderColor?,borderWidthPt?,borderPreset?}`

重新设置整个表格的样式：通过 `styleName` 应用一个固定颜色预设，通过 `styleId` 选择 PowerPoint 74 种内置样式之一（图库名称如 `"Medium Style 2 - Accent 1"` 或其 GUID；它们遵循演示文稿的主题颜色），或更改单个区域标志、单元格底纹和边框线。预设优先于其他字段；预设或 `styleId` 会像 PowerPoint 的样式图库一样清除直接单元格填充和边框（`keepFormatting: true` 会保留它们）。`slides read` 会显示表格当前的 `style`。

| 字段                                | 类型                  | 说明                                                                                                                                                                                                                                           |
| ----------------------------------- | --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| styleName                           | string                | `none`、`lightGrid`、`zebraBlue`、`zebraGray`、`headerDarkBlue`、`headerOrange`、`noBorder`、`fullBorder`                                                                                                                                      |
| styleId                             | string                | 内置图库名称或 `{GUID}`：`No Style, No Grid`、`No Style, Table Grid`、`Themed Style 1/2 - Accent N`、`Light Style 1/2/3 [- Accent N]`、`Medium Style 1/2/3/4 [- Accent N]`、`Dark Style 1 [- Accent N]`、`Dark Style 2 [- Accent N]` |
| firstRow                            | boolean               | 标题行强调                                                                                                                                                                                                                                     |
| lastRow, firstCol, lastCol, bandCol | boolean               | 汇总行、首/末列强调、带状列                                                                                                                                                                                                                    |
| bandRow                             | boolean               | 带状行                                                                                                                                                                                                                                         |
| keepFormatting                      | boolean               | 配合 `styleId`：保留直接单元格填充/边框，而不是清除它们                                                                                                                                                                                        |
| shadingColor                        | `#RRGGBB` 或 `"none"` | 每个单元格的填充                                                                                                                                                                                                                               |
| borderColor                         | `#RRGGBB`             | 边框线颜色                                                                                                                                                                                                                                     |
| borderWidthPt                       | number (pt)           | 边框线宽度；0 < pt <= 1584                                                                                                                                                                                                                     |
| borderPreset                        | `"all"` 或 `"none"`   | 绘制所有边框线，或清除它们                                                                                                                                                                                                                     |

```json
{ "op": "setTableStyle", "target": { "slide": 0, "el": "e_TABLE" }, "styleName": "zebraBlue" }
```

```json
{
  "op": "setTableStyle",
  "target": { "slide": 0, "el": "e_TABLE" },
  "styleId": "Medium Style 2 - Accent 1",
  "firstRow": true,
  "bandRow": true
}
```

```json
{
  "op": "setTableStyle",
  "target": { "slide": 0, "el": "e_TABLE" },
  "firstRow": true,
  "borderPreset": "all",
  "borderColor": "#BFBFBF",
  "borderWidthPt": 1
}
```

常见错误

- 传入颜色名称（`"blue"`）：颜色格式为 `#RRGGBB`。
- 将 `styleName` 与其他字段混用：预设会被应用，其余字段被忽略。
- 在 `styleName` 中传入内置名称：图库名称和 GUID 应放在 `styleId` 中。
- 重新设置单个单元格文本的样式：那是 `setTableCell` 配合带样式的 run，不是此操作。

### setChart（不可由 AI 调用）

`{patch:ChartEdit} — 请改用 edit_chart 工具`

更改图表的类型、数据、颜色或元素。`edit_chart` 工具以经过验证的 Schema 暴露此功能。
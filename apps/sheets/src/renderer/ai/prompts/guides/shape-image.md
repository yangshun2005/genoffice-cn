# 形状与图片指南 (shape-image)

## 插入形状/文本框（支持）

`{op:"add_shape", sheetId, shapeType, anchorCell:"E2", fillColor?, text?}`

- shapeType：插入画廊中任意 OOXML prstGeom 名称——矩形（"rect"、"roundRect"、剪角/圆角变体）、基本形状（"ellipse"、"triangle"、"diamond"、"hexagon"、"heart"、"cloud"、"donut"、"smileyFace" 等）、块箭头（"rightArrow"、"quadArrow"、"chevron" 等）、星形/横幅（"star5"、"star12"、"ribbon"、"wave" 等）、流程图节点（"flowChartProcess"、"flowChartDecision"、"flowChartDocument" 等）、标注（"wedgeRectCallout"、"cloudCallout" 等），或 "textbox"
- textbox 默认为白色背景并显示 "Text"；其他形状默认为浅蓝色填充。text 可以直接承载注释内容。
- 布局类：可以与内容/格式操作共享一个批次，但不能与结构性操作共享；仅对导入的 xlsx 有效，通过 ⌘S 写入。

### 常见用法

- **标注/注释框**：在关键数据旁放置一个 `textbox`，将解读作为 text（例如 "+23% YoY, all-time high"）。
- **流程/关系图**：组合 `rect`/`roundRect` + `rightArrow`，错开 anchorCell 以实现布局。
- **强调块**：使用带半透明填充的 `roundRect` 框住一组关键指标。

## 单元格内迷你图（SPARKLINE，支持）

无需图表对象——用公式在单元格内绘制迷你趋势图：

- 折线迷你图：`=SPARKLINE(B2:M2)`
- 柱状迷你图：`=SPARKLINE(B2:M2, {"charttype","column"})`
- 胜负图：`=SPARKLINE(B2:M2, {"charttype","winloss"})`

非常适合在每个汇总行末尾添加一个 "Trend" 列——趋势一目了然，且比插入大量图表更轻量。

```json
{
  "op": "set_formula",
  "sheetId": "s1",
  "address": "N2",
  "formula": "=SPARKLINE(B2:M2,{\"charttype\",\"column\"})"
}
```

## 单元格内图片/链接（支持）

- 嵌入图片：`=IMAGE("https://example.com/logo.png")`
- 可点击链接：优先使用 `set_hyperlink`（参见数据指南）；公式版本 `=HYPERLINK("https://...", "Click here")`。

## 规则

- 形状/图片用于**辅助表达**——不要让它们喧宾夺主；正确性优先。
- 迷你图/IMAGE 是随单元格值更新的公式；图表对象是独立的图层（参见图表指南）。
- 大量趋势展示优先使用 SPARKLINE（轻量）；单一聚焦分析使用 add_chart（重量级）。
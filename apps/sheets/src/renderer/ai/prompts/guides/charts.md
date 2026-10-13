# 图表与形状指南（图表）

## 创建图表

`{op:"add_chart", sheetId, chartType:"column"|"bar"|"line"|"area"|"pie"|"doughnut"|"scatter"|"radar"|"combo", dataRange:"A1:C10", title?, anchorCell?}`

- 适用于导入的 xlsx 文件和演示工作簿。在 xlsx 文件中，保存（⌘S）会将图表作为全新的图表部件写入文件；演示工作簿中的图表仅存在于内存中（可用 ⌘Z 撤销），目前尚无法保存到文件。
- dataRange 是图表的数据源（最多 2000 个单元格）：如果第一行包含文本，则将其视为系列名称表头；如果第一列包含文本，则将其视为分类轴。**在提议之前，请先使用 read_range 读取数据以确认其结构**——未加载的单元格读取结果为空。
- 至少需要一个数值列，否则该操作将被拒绝。在演示工作簿中，公式单元格没有缓存值（读取结果为空）——请勿将 dataRange 指向纯公式结果区域。
- anchorCell 是图表框左上角的锚点单元格；默认情况下，图表放置在数据范围右侧两列处。
- title 默认值：单系列时为系列名称，多系列时为 "Chart Title"。
- 新建的柱状图/条形图默认带有数值数据标签（每个柱条标注其值）；如果不需要，可随后使用 `edit_chart` 将 `dataLabels` 设置为 "none"。
- 类型选择：时间序列 → 折线图/面积图；分类比较 → 柱状图/条形图；占比 → 饼图（饼图仅使用第一个数值列——多系列数据请勿选择饼图）；量级差异很大的两个指标（例如金额 + 百分比）→ 组合图。
- combo（柱状图 + 折线图）：最后一个系列绘制在右侧次坐标轴上作为折线，其余系列在左侧坐标轴上作为簇状柱条；需要 ≥2 个系列——单系列会退化为普通柱状图。组合图创建后无法转换为其他类型。
- 图表/形状/图片也可以直接插入到本次会话中创建的工作表上。

## 编辑现有图表

`{op:"edit_chart", chartPath:"xl/charts/chart1.xml", title?, chartType?, seriesColors?, legend?, dataLabels?, grouping?, axisTitles?, seriesData?}` —— 至少需要一个属性：

- 要查看工作簿中有哪些图表，请查看 get_workbook_context 中的 "Charts in the workbook" 列表：每个条目会给出 chartPath、当前标题、类型和所属 sheetId。**chartPath 必须来自该列表**——切勿自行编造。
- 文件自带的图表其 chartPath 形如 `xl/charts/chart1.xml`；本次会话添加的图表和演示工作簿中的图表使用列表中的视觉 id（如 `added-chart-…` / `demo-chart-…`）作为 chartPath，同样可以编辑。
- `title`：图表标题（≤255 个字符）
- `chartType`："column" | "bar" | "line" | "area" | "pie" | "doughnut" —— 只有具有**单一绘图区**的图表才能在这些类型之间转换；组合图、散点图和 3D 图表不支持转换（类型转换提议会在预览阶段被拒绝）——此时只能更改标题/颜色，或向用户说明
- `seriesColors`：{"0":"#4472C4", "1":"#ED7D31"} —— 键为系列索引（字符串），值为 6 位十六进制颜色
- `legend`："none"（隐藏）| "right" | "bottom" | "top" | "left"
- `dataLabels`："none" | "value"（数值）| "percent"（百分比，饼图）| "category-percent"（名称 + 百分比，饼图）
- `grouping`："clustered" | "stacked" | "percentStacked" —— 仅适用于柱状图/条形图/折线图/面积图
- `axisTitles`：{category?, value?} —— 坐标轴标题，null 表示清除；饼图/圆环图没有坐标轴，不适用
- `seriesData`：[{index, name?, valuesRange?:"B2:B13", categoriesRange?:"A2:A13", sheetId?}] —— 重命名系列或**重新指向其数据范围**（单行或单列；sheetId 默认为图表所在的工作表）。应用时，当前工作表的值会同步到图表缓存中，引用公式也会写入文件。
- 系列颜色应作为整体进行更改（保持同一调色板）——仅重新着色单个系列会破坏视觉一致性；请遵循高对比度、低饱和度的调色板。

## 插入形状/文本框

`{op:"add_shape", sheetId, shapeType, anchorCell:"E2", fillColor?, text?}`

- shapeType：插入库中任意 OOXML prstGeom 名称（"rect"、"roundRect"、"ellipse"、"heart"、"star5"、"flowChartProcess"、"wedgeRectCallout" 等；参见形状图片指南）或 "textbox"
- textbox 默认为白色背景，文本为 "Text"；其他形状默认为浅蓝色填充。text 可以直接携带注释。
- 同样仅适用于导入的 xlsx 文件；保存时写入文件。

## 编辑形状 / 插入图片

- `{op:"edit_shape", visualId, text?, fillColor?, anchorCell?}` —— 编辑**本次会话添加的**形状/文本框（更改文本、更改填充、移动；尺寸保持不变）。从 read_sheet_features 获取 visualId；文件自带的形状无法修改。
- `{op:"add_image", sheetId, path:"~/logo.png", anchorCell:"B2"}` —— 插入图片（PNG/JPEG/GIF）。path 可以是用户指定的本地文件（≤20MB，绝对路径或 ~/ 前缀——**必须由用户明确给出**，切勿猜测文件位置），也可以是 image_search / generate_image 返回的 https URL。尺寸根据图片的宽高比自动计算；保存时写入文件。

## 规则

- add_chart / edit_chart / add_shape 均属于布局类操作：它们可以与内容/格式操作共享同一批次，但不能与结构性操作（行/列或工作表的插入/删除）共享。
- 应用时，更改会立即渲染到画布上并记录在编辑日志中；⌘S 将其保存到文件。对现有图表的编辑是精准重写——其他所有内容保持逐字节不变。
- 先写入数据再创建图表：在同一批次中可以先 set_range 再 add_chart，但 add_chart 读取的是**当前值**——如果数据尚未写入工作表，请拆分为两个批次（先写入数据，应用，然后创建图表）。

## 图表类型选择（按数据意图）

| 数据意图             | 推荐类型                                 | 说明                                                         |
| -------------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 时间趋势 / 连续变化  | `line` / `area`                          | 多周期趋势用折线图；强调累计量/总量用面积图                  |
| 分类比较             | `column`（垂直）/ `bar`（水平）          | 当分类名称较长或较多时使用条形图（水平方向更易阅读）         |
| 占比（≤ 6 项）       | `pie`                                    | 仅使用第一个数值列；项目较多时改用条形图                     |
| 两个变量之间的关系   | scatter                                  | 第一列作为 X（必须为数值），其余列作为 Y                     |

选择原则：一张图表回答一个问题；对于多个比较维度，优先使用柱状图（细节）+ 饼图（占比）作为互补。

## 图表规范

- 标题**必须有意义并包含单位**（例如 "Sales by department (USD thousands)"）——切勿使用 "Chart Title"/"Chart 1"。
- 当存在明确的数值比较时，**建议添加图表**——不要只交付裸数据。
- 当分类轴标签较长时，优先使用条形图（水平）以避免标签倾斜。
- 多个系列共享同一调色板（高对比度、低饱和度）；将 seriesColors 作为整体进行更改。

## 删除图表/形状/图片（delete_visual）

`{op:"delete_visual", visualId}` —— visualId 请使用 get_workbook_context 图表列表中的路径（图表）或 read_sheet_features 中的视觉 id（形状/图片）。文件原生对象和本次会话添加的对象均可删除；删除文件图表时也会移除其图表部件。

## 迷你图（add_sparkline）

`{op:"add_sparkline", sheetId, type:"line"|"column"|"stacked", dataRange:"B2:F9", targetCell?, color?}` —— 每行数据生成一个单元格内迷你图，放置在 dataRange 右侧一列处（或从 targetCell 开始向下放置）。stacked 表示盈亏。仅适用于导入的 xlsx 文件；保存为 Excel 原生的 x14 sparklineGroups。
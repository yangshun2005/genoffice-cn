# 数据透视表指南（pivot）

## 何时用数据透视表，何时用公式聚合

- 用户要求"数据透视表"，或希望结果在 Excel 中可交互（拖拽字段、刷新）→ **add_pivot**（真正的数据透视表）。
- 用户只想"按维度汇总"，并会基于汇总值继续计算/绘图 → 公式聚合表也可以（见备选方案）：结果是真实的单元格公式，可继续计算。

## 创建数据透视表（add_pivot）

`{op:"add_pivot", sheetId, sourceRange:"A1:F1000", targetCell:"H1", targetSheetId?, rowFields, columnField?, pageFields?, values:[{field, agg, showDataAs?, name?}], name?}`

- **sourceRange 的第一行必须是表头**（非空且互不重复）；rowFields/columnField/values.field 均使用表头文本。
- rowFields：行维度，1–8 个（字符串或数组，**最外层在前**）；多层级时，行按层级分组，并自动添加各级小计行。columnField：列维度（可选，最多 1 个；**指定 columnField 时，values 只能有 1 项**）。
- values：`{field:"Amount", agg:"sum"|"count"|"average"|"max"|"min"|"product"|"countNums", showDataAs?, name?}`，1–8 项；values 字段不能同时作为行/列/页维度；`name` 覆盖"Sum of Amount"标题。
- showDataAs（值显示方式，可选）：`"percentOfTotal"`（占总计百分比）| `"percentOfRow"`（占行汇总百分比）| `"percentOfCol"`（占列汇总百分比）| `"percentOfParentRow"` | `"percentOfParentCol"`（占上一级百分比）| `"index"`；百分比模式默认以 0.00% 格式显示。
- pageFields（报表筛选，可选，≤4）：表头名称或 `{field, item}`；它们渲染为表格上方的"字段 | (All)"行（外加一空行），指定 `item` 后整个报表仅限匹配的源行。
- targetCell：输出区域左上角，**不得与源区域重叠**（放在源区域右侧空白处，或用 targetSheetId 放到汇总表上）。
- 生效方式：应用时，聚合结果（含小计和总计行/列）直接写入目标单元格并立即可见；保存时写入原生数据透视表部件（refreshOnLoad），因此**文件在 Excel 中打开即为可交互的实时数据透视表**。
- 限制：源区域 ≤ 10,000 数据行 × 200 列；每个行维度层级 ≤ 10,000 个不同成员；同一批次不能同时对源/目标表做行/列插入删除或工作表管理（先保存）。
- 保存后输出区域受保护（不可直接编辑）——不要在其上叠加 set_cell。

```json
{
  "op": "add_pivot",
  "sheetId": "s1",
  "sourceRange": "A1:D500",
  "targetCell": "F1",
  "rowFields": ["Region", "Product"],
  "values": [
    { "field": "Sales", "agg": "sum" },
    { "field": "Sales", "agg": "sum", "showDataAs": "percentOfTotal" }
  ],
  "name": "RegionProductSummary"
}
```

## 刷新已有数据透视表（refresh_pivot）

`{op:"refresh_pivot", sheetId}` —— 重新计算该工作表上所有数据透视表的数据区域并写回。源数据变更后用它更新透视结果。

- 源数据出现**新类别**时，布局自动扩展：新成员追加到所在层级末尾（多层级布局会新增小计行），输出区域随之扩大——但扩展占用的区域必须为空，否则报错并要求先清空。
- 仍会明确报错的情况：表头重命名/数据源移动、计算字段、分组字段、值筛选，以及紧凑（非表格）布局的扩展。其他边界情况见数据指南的"数据透视表"章节。

## 备选方案：公式聚合表（适用于不规则数据或需要实时公式时）

用 `SUMIFS`/`COUNTIFS`/`AVERAGEIFS` 直接计算汇总网格：

**单维度汇总**（按地区统计销售额）：

```json
[
  { "op": "set_range", "sheetId": "s2", "range": "A1:B1", "values": [["Region", "Sales"]] },
  {
    "op": "set_range",
    "sheetId": "s2",
    "range": "A2:A5",
    "values": [["East"], ["South"], ["North"], ["West"]]
  },
  {
    "op": "set_formula",
    "sheetId": "s2",
    "address": "B2",
    "formula": "=SUMIFS(Sheet1!$C:$C,Sheet1!$A:$A,A2)"
  }
]
```

（将 B2 公式向下填充至 B5；条件区域指向源表的地区/金额列。）

**二维交叉表**（地区 × 月份）：行表头放地区，列表头放月份，每个交叉点用双条件 `=SUMIFS(src!amount, src!region, $rowHeader, src!month, colHeader$)`（注意 `$` 锁定方向以便填充）。

**维度值去重**：源维度值未知时，先 `read_range` 读取源列，将去重后的维度值写入方案中的行/列表头，再附加 SUMIFS。

## 配套步骤

- 汇总表算好后，按 `charts` 指南添加图表（类别对比 → 柱状图，占比 → 饼图）。
- 对金额列应用 `financial-formatting` 货币格式。
- 公式聚合表的合计行用 `=SUM(...)`，加粗 + 浅灰填充（add_pivot 自带总计）。
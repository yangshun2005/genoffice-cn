# 财务报表格式化指南（financial-formatting）

适用于资产负债表、利润表、现金流量表、损益表、财务分析及其他会计/财务表格。所有操作均使用 `format_range` / `set_cell` / `merge_cells` / `set_hyperlink` DSL；格式类和内容类操作可以共用同一批次，结构性变更（插入/删除行或列）需要单独批次。

## 数字格式（会计级）

- **锁定货币区域设置**（防止在中文本地化 Excel 中 `$` 被重映射为 `¥`）：美元 `[$$-409]#,##0`，人民币 `[$¥-804]#,##0.00`。
- **负数以红色括号显示**：`[$$-409]#,##0;[Red]([$$-409]#,##0)`。
- **零显示为短横线**（0 显示为 `—`；空白表示数据缺失）：`[$$-409]#,##0;[Red]([$$-409]#,##0);"-"`。
- 数字**右对齐**，同一列内小数位数保持一致；在表头中注明千/百万单位（如 "Amount (thousands)"）。

```json
{"op":"format_range","sheetId":"s1","range":"B5:F20",
 "format":{"numberFormat":"[$$-409]#,##0;[Red]([$$-409]#,##0);\"-\"","horizontalAlign":"right"}}
```

## 层级可视化

- 父级行项目**加粗**；子项通过 format_range 的 `indent` 字段表达父子关系（每级 +1，在屏幕和文件中均生效）。
- 不要用前导空格模拟缩进——空格会污染单元格文本，破坏查找和公式引用。

```json
{"op":"set_cell","sheetId":"s1","address":"A6","value":"Accounts receivable"}
{"op":"format_range","sheetId":"s1","range":"A6","format":{"indent":1}}
```

## 合计 / 小计行

加粗 + 浅灰色填充 `#F2F2F2`，用细上边框 + 双下边框分隔：

```json
[
 {"op":"format_range","sheetId":"s1","range":"A20:F20","format":{"bold":true,"fillColor":"#F2F2F2"}},
 {"op":"format_range","sheetId":"s1","range":"A20:F20","format":{"border":{"type":"top","color":"#000000"}}},
 {"op":"format_range","sheetId":"s1","range":"A20:F20","format":{"border":{"type":"bottom","color":"#000000"}}}
]
```

## 表头

- 章节标题（如 "Balance Sheet"）：**跨列合并 + 居中 + 加粗 + 视觉上更大（用加粗来补偿——本应用不会为此改变字号）**。
- 期间列（"FY2024 | FY2023 | FY2022"）：加粗 + 居中，用中等粗细的下边框分隔。

```json
[
 {"op":"merge_cells","sheetId":"s1","range":"A1:F1"},
 {"op":"set_cell","sheetId":"s1","address":"A1","value":"Balance Sheet"},
 {"op":"format_range","sheetId":"s1","range":"A1:F1","format":{"bold":true,"horizontalAlign":"center"}},
 {"op":"format_range","sheetId":"s1","range":"B2:F2","format":{"bold":true,"horizontalAlign":"center"}}
]
```

## 配色方案（保守、专业）

- 表头：藏青色 `#1F3864` 填充 + 白色文字 `#FFFFFF` + 加粗
- 小计行：浅灰色 `#F2F2F2`
- 数据行：白色
- 隔行着色（可选）：极浅蓝色 `#F8FAFC`
- 细网格分隔线：`#D9D9D9`（边框内线）

```json
{"op":"format_range","sheetId":"s1","range":"A2:F2","format":{"fillColor":"#1F3864","fontColor":"#FFFFFF","bold":true}}
```

## 财务模型输入着色（构建模型时）

- 硬编码输入 → 蓝色文字 `#0000FF`
- 公式计算 → 黑色文字（默认）
- 跨表引用 → 绿色文字 `#008000`

## 布局

- 用 `set_col_width` 将第一列（行项目名称）加宽至约 200px；数值列统一约 100px。
- 使用边框内线（`#D9D9D9`）形成浅网格；避免使用粗重的外框。

## 数据来源标注

财务数据必须注明来源（参见 `data-attribution` 指南）：斜体小号页脚文字 + 超链接，例如 "Source: SEC 10-K FY2024"。

```json
[
 {"op":"set_cell","sheetId":"s1","address":"A22","value":"Source: SEC 10-K Filing, FY2024"},
 {"op":"format_range","sheetId":"s1","range":"A22","format":{"italic":true,"fontColor":"#666666"}},
 {"op":"set_hyperlink","sheetId":"s1","address":"A22","target":"https://sec.gov/Archives/edgar/..."}
]
```

## GAAP / IFRS 惯例

- 恒等式：资产 = 负债 + 所有者权益
- 按逻辑对行项目分组，流动项目在前、非流动项目在后
- 利润表顺序：收入 → 销货成本 → 毛利 → 营业费用 → 营业利润 → 净利润
- 现金流量表：经营活动 → 投资活动 → 筹资活动 → 现金净变动

## 纪律

- **样式失败绝不阻塞**：如果格式操作被拒绝，优先交付正确的数据；不要反复重试样式。
- 每个事实性数据单元格都需要来源；用公式推导数值，绝不要心算后硬编码。
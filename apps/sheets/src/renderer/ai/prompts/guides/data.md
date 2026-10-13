# 数据工具指南（data）

以下所有操作均属于**布局类**操作：它们可以与内容/格式类操作共享同一批次，但不能与结构性操作（行/列或工作表的插入/删除）共享批次。它们仅对导入的真实 xlsx 文件生效；应用后会被记录到编辑日志中，⌘S 保存时会写入文件。

**修改现有设置之前，请先使用 read_sheet_features**：它会读取当前的筛选范围和列条件、所有条件格式规则、数据验证规则、定义名称，以及形状/图片清单。

## 超链接

- `{op:"set_hyperlink", sheetId, address:"B2", target:"https://example.com"}` — target 也可以是工作簿内引用 "Sheet1!A1"（会自动添加 #）；裸域名会自动在前面加上 https://。
- `{op:"set_hyperlink", sheetId, address, target:null}` — 移除链接（并清除链接样式）。
- 设置链接后单元格会呈现蓝色下划线样式；单元格内容不变。

## 自动筛选

- `{op:"set_filter", sheetId, range:"A1:D100"}` — 在指定范围上创建自动筛选（已有的筛选会被替换）；range 的第一行是筛选表头。
- `{op:"clear_filter", sheetId}` — 移除整个自动筛选。
- `{op:"set_filter_criteria", sheetId, column:"B", values:["East","South"]}` — 复选框式列条件：**显示文本**在 values 中的行保持可见，其他行被隐藏。要求工作表上已有自动筛选。values:null 清除该列的条件。
- 写入 values 之前请先用 read_range 查看该列实际存在哪些值；文本必须逐字匹配。

## 条件格式

`{op:"add_conditional_format", sheetId, range, rule}` — rule 通过 kind 区分：

- `{kind:"number", operator:"greaterThan"|"greaterThanOrEqual"|"lessThan"|"lessThanOrEqual"|"equal"|"notEqual"|"between"|"notBetween", value, value2?, format}` — between/notBetween 需要 value2
- `{kind:"text", operator:"contains"|"notContains"|"beginsWith"|"endsWith", text, format}`
- `{kind:"blank", blank:true|false, format}` — true 高亮空白单元格，false 高亮非空白单元格
- `{kind:"duplicate", unique?, format}` — 默认高亮重复值；unique:true 则高亮唯一值
- `{kind:"top10", rank:10, percent?, bottom?, format}`
- `{kind:"formula", formula:"=B2>100", format}` — formula 以 = 开头，使用以范围左上角单元格为锚点的相对引用
- `{kind:"colorScale", minColor:"#63BE7B", midColor?, maxColor:"#F8696B"}` — 色阶（无 format 字段）
- `{kind:"dataBar", color?}` — 数据条（无 format 字段）

format：`{fillColor?, fontColor?, bold?, italic?}`，至少包含一个属性。高亮颜色遵循低饱和度原则（浅背景、深文字），例如红色 #FFC7CE/#9C0006、绿色 #C6EFCE/#006100、黄色 #FFEB9C/#9C6500。

`{op:"clear_conditional_formats", sheetId}` — 清除工作表上**所有**条件格式规则（包括文件自带的规则）；执行前请与用户确认。

## 数据验证

`{op:"set_data_validation", sheetId, range, validation}` — validation 通过 kind 区分：

- `{kind:"list", values:["Yes","No"]}` — 下拉列表（≤100 项）
- `{kind:"listRef", range:"H1:H20"}` — 下拉选项取自某个单元格范围的值
- `{kind:"numberBetween", min, max}`
- `{kind:"dateBetween", start:"2026-01-01", end:"2026-12-31"}` — ISO 日期
- `{kind:"checkbox"}`
- `{kind:"formula", formula:"=LEN(A1)<=10"}`
- `validation:null` — 清除该范围上的验证规则

## 批注

- `{op:"set_note", sheetId, address:"B2", text:"This figure includes tax"}` — 添加/编辑单元格批注（黄色便签，悬停时显示）。
- `{op:"set_note", sheetId, address, text:null}` — 删除批注。
- 保存为 Excel 旧式批注；在 Excel 中悬停单元格时可见。请先用 read_sheet_features 读取现有批注。

## 数据透视表

- `{op:"add_pivot", sheetId, sourceRange, targetCell, rowFields, columnField?, values:[{field, agg, showDataAs?}]}` — **创建原生数据透视表**（真正的 OOXML，在 Excel 中打开时可交互、可刷新）；rowFields 支持 1–8 级行分组，showDataAs 支持占总计/行/列的百分比。用法和限制见 `pivot` 指南（load_guide）。
- `{op:"refresh_pivot", sheetId}` — **重新计算工作表上的所有数据透视表**：使用文件中记录的布局，根据当前源数据重新计算数据区域并写回（保存时还会让 Excel 在打开文件时重建缓存）。在源数据发生变化后使用它来使透视结果保持最新。
- 如果刷新在源数据中发现**新的类别成员**，布局会自动扩展（追加新成员、扩展输出区域——扩展区域必须为空）；移动了字段列、重命名了表头，或使用了计算字段/分组/值筛选的透视表仍会以明确的错误失败（这种情况下建议用户在 Excel 中刷新）。
- read_sheet_features 会列出每个数据透视表的行/列/值字段、源范围，以及是否可重新计算。
- 尚不支持修改现有数据透视表的字段布局；输出区域为只读（直接由 AI 写入会被拒绝）。
- 当数据不规范、需要实时公式做进一步计算，或超出 add_pivot 的限制时，退回到**公式汇总表**（SUMIFS/COUNTIFS，参见 pivot 指南的备选方案）。
- 汇总表遵循格式指南中的表格样式规则（表头、对齐、总计行）。

## 定义名称

- `{op:"add_defined_name", name:"SalesRegion", ref:"Sheet1!$A$1:$B$10"}` — name 以字母/下划线开头；ref 是 A1 引用（建议使用绝对 $ 引用）或常量。
- `{op:"delete_defined_name", name}` — 删除该名称（引用它的公式文本不受影响，但这些公式会变成 #NAME? — 删除前请确认没有公式使用它）。
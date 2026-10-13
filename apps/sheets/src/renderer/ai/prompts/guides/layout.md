# 排序与布局指南（layout）

## 排序

`{op:"sort_range", sheetId, range:"A1:C10", byColumn:"B", order:"asc"|"desc", hasHeader?:true}`

- 按**当前值**稳定排序：数字 < 文本 < 布尔值；空单元格始终排在最后，与方向无关；字符串比较会识别数字（item2 < item10）。
- byColumn 必须落在 range 内；hasHeader 为 true 时首行不参与排序。
- ≤2000 个单元格的区域会在预览中展开为逐单元格变更（带并发保护），用户能看到每个单元格的前后值；该区域必须先加载（read_range 会加载）。
- 更大的区域（最多 200,000 个单元格）作为一次区域级操作应用：执行器自行加载每个区域，批量写入重排后的行——没有逐单元格预览。
- 只移动值；每个单元格的格式留在原位（不同于 Excel，Excel 会随行拖动格式）。在混合数字格式的列上，移动的值会采用其落点所在行的格式。
- **包含公式的区域会被直接拒绝**——移动公式文本会悄悄改变相对引用的指向。向用户解释原因（可建议先把公式列转为值）；不要试图绕过。
- 整表一起排序：range 必须覆盖所有相关列——只排一列会把行拆散。

## 合并

- `{op:"merge_cells", sheetId, range:"A1:C1"}` — 与已有合并区域重叠时被拒绝；至少需要两个单元格。
- `{op:"unmerge_cells", sheetId, range}` — 清除与该区域相交的所有合并。
- 合并主要用于标题行/分类表头；避免在数据区域合并（会破坏排序和公式填充）。
- 标题类内容优先用"合并 + 居中 + 填充色"，而不是零散的独立单元格。

## 行高与列宽

- `{op:"set_row_height", sheetId, row:2, count?:1, heightPoints:24}` — 高度以磅为单位（2–409）。
- `{op:"set_col_width", sheetId, column:"B", count?:1, widthPx:120}` — 宽度以像素为单位（10–2000）。
- 给报表标题行加大高度（如 24–28pt）；调整数据列宽使内容不溢出，相似列保持同宽。

## 隐藏行/列

- `{op:"set_rows_hidden", sheetId, row:5, count?:1, hidden:true|false}` — row 从 1 开始；hidden:false 取消隐藏。
- `{op:"set_cols_hidden", sheetId, column:"C", count?:1, hidden:true|false}`
- 隐藏不删除数据，公式引用不受影响；适合隐藏辅助计算列。要删除数据请用 delete_rows/delete_cols（注意批处理纪律）。

## 冻结窗格

`{op:"set_freeze", sheetId, rows:1, columns:0}` — 冻结顶部 rows 行和左侧 columns 列；`rows:0, columns:0` 取消冻结。立即在画布上生效，保存时写入文件。典型用法：用 `rows:1` 冻结表头行。

## 页面设置（打印）

`{op:"set_page_setup", sheetId, orientation?, paperSize?, scale?, fitToWidth?, fitToHeight?, margins?, printGridlines?, printHeadings?, printArea?, printTitles?, header?, footer?, rowBreaks?, colBreaks?}` — 至少一个属性，仅对导入的 xlsx 文件有效，保存时写入：

- `orientation`："portrait" | "landscape"
- `paperSize`：OOXML 纸张代码（1=Letter，8=A3，9=A4，11=A5）
- `scale`：打印缩放 10–400(%)；与 fitToWidth/fitToHeight **互斥**（fit 表示"适应 N 页宽/高"，0=自动）
- `margins`："normal" | "wide" | "narrow"
- `printGridlines` / `printHeadings`：打印网格线 / 行列标题
- `printArea`："A1:H40" 设置打印区域，null 清除
- `printTitles`："1:1" 在每页顶部重复这些行，null 清除
- `header` / `footer`：`{left?, center?, right?}` 打印文本；Excel 代码可用（&P 页码，&N 总页数，&D 日期，&F 文件名，&A 工作表名）；null 清除
- `rowBreaks` / `colBreaks`：从 1 开始的行/列号，在其后开始新页；该列表替换手动分页符，[] 清除
- 设置仅写入文件（打印时生效）；画布不显示分页。
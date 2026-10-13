# 结构化表格指南（table）

## 何时使用结构化表格

当数据是规整的"表头 + 同构记录行"形态时，优先用 Table：自动隔行填充、筛选下拉，保存后在 Excel 中是原生表格对象（自动扩展、结构化引用）。

## 创建表格（add_table）

`{op:"add_table", sheetId, range:"A1:D10", name?, style?, bandedRows?}`

- **range 首行必须是表头**：先用 set_range/set_cell 写入表头和数据，再 add_table。表头必须非空且互不重复——空表头自动补为 Column1/Column2，重复表头加数字后缀，两者都会写回单元格。
- range 至少两行（表头 + ≥1 数据行），且不能与合并单元格、已有表格、工作表筛选（set_filter）区域重叠——冲突会在保存时被拒绝。
- name：表格名（字母/下划线开头，可含中文；工作簿内唯一，与定义名称共用命名空间）。**建议始终显式命名**；默认 Table1、Table2…（若与文件中已有表格重名，保存报错）。
- style：内置样式 `TableStyleLight1..21` / `TableStyleMedium1..28` / `TableStyleDark1..11`，默认 `TableStyleMedium2`。
- bandedRows：隔行填充，默认 true。

```json
[
  {
    "op": "set_range",
    "sheetId": "s1",
    "range": "A1:C1",
    "values": [["Product", "Quantity", "Amount"]]
  },
  {
    "op": "add_table",
    "sheetId": "s1",
    "range": "A1:C20",
    "name": "SalesDetail",
    "style": "TableStyleMedium2"
  }
]
```

注意：

- 创建表格后可直接用 `add_table_row` / `add_table_column` 等扩展结构，无需先保存。但文件自带的表格（打开时已存在）不能用这些操作修改——请让用户保存后重新打开。
- 不要在表格数据内 merge_cells；不要在表头行叠加 set_filter（表格自带筛选）。

## 结构化引用

引擎会为 get_sheet_features 列出的每个表格（文件表格和本次会话新增的表格）求值 Excel 结构化引用，同表或跨表均可：

- `TableName[Column]`、`TableName[[ColA]:[ColB]]`、`TableName[#All]`、`TableName[#Headers]`、`TableName[#Data]`、`TableName[[#This Row],[Column]]`（仅限表格自身行内）。
- 表格名和列名**区分大小写**——请严格照 get_sheet_features 列出的写法复制。

不支持（请改用普通 A1 区域）：`[@Column]` / `TableName[@Column]` 简写、带工作表限定的表格名（`Sheet1!Table[Col]`）、`[#Totals]`（文件表格的汇总行不在注册范围内），以及没有表头行的表格。

## 插入/删除行列

> **前提**：这四个操作仅对**本次会话通过 add_table 创建的表格**有效；文件自带的表格不支持（报错：请保存后重新打开再修改）。

### add_table_row — 插入数据行

```json
{ "op": "add_table_row", "sheetId": "s1", "tableName": "SalesDetail", "row": 3, "count": 2 }
```

- `row`（可选，从 1 开始，相对数据区）：插入位置；省略 = 追加到末尾。
- `count`（可选，默认 1）：插入行数，1–1000。
- 操作后用 set_range/set_cell 填充新行。

### delete_table_row — 删除数据行

```json
{ "op": "delete_table_row", "sheetId": "s1", "tableName": "SalesDetail", "row": 2, "count": 1 }
```

- `row`（必填，从 1 开始）：要删除的首行（相对数据区，不含表头）。
- `count`（可选，默认 1）：删除行数。
- 至少保留 1 个数据行；全部删除会被拒绝。

### add_table_column — 插入列

```json
{
  "op": "add_table_column",
  "sheetId": "s1",
  "tableName": "SalesDetail",
  "column": 3,
  "columnName": "Notes",
  "count": 1
}
```

- `column`（可选，从 1 开始）：插入位置；省略 = 追加到最右侧。
- `columnName`（必填）：新列的表头名；不能与表格中已有列重复。
- `count`（可选，默认 1）：插入列数。count>1 时，后续列名加数字后缀（Notes、Notes2…）。

### delete_table_column — 删除列

```json
{
  "op": "delete_table_column",
  "sheetId": "s1",
  "tableName": "SalesDetail",
  "column": 4,
  "count": 1
}
```

- `column`（必填，从 1 开始）：要删除的首列（相对表格左边缘）。
- `count`（可选，默认 1）：删除列数。
- 至少保留 1 列；全部删除会被拒绝。

### 典型流程

1. 用 `add_table` 创建并命名表格（**建议显式命名**）。
2. 用 `add_table_row` / `add_table_column` 扩展结构，再用 `set_range` / `set_cell` 填充数据。
3. 完成后提醒用户保存（⌘S）；保存后文件中的表格引用会自动更新。

## 兜底方案（真实表格不适用时）

当数据不规整（有小计行、多列合并表头）时，不要创建 Table——用普通区域模拟外观：

```json
[
  {
    "op": "format_range",
    "sheetId": "s1",
    "range": "A1:D1",
    "format": { "bold": true, "fillColor": "#4472C4", "fontColor": "#FFFFFF" }
  },
  {
    "op": "add_conditional_format",
    "sheetId": "s1",
    "range": "A2:D100",
    "rule": {
      "kind": "formula",
      "formula": "=MOD(ROW(),2)=0",
      "format": { "fillColor": "#F2F7FF" }
    }
  },
  { "op": "set_filter", "sheetId": "s1", "range": "A1:D100" }
]
```

- 用 `MOD(ROW(),2)` 条件格式实现隔行填充（自动适应行的插入/删除）。
- 首行筛选（`set_filter`）近似 Table 的筛选下拉。

## 删除表格（delete_table）

`{op:"delete_table", sheetId, tableName}` — 只能删除本次会话通过 add_table 创建的表格；语义是"转为普通区域"：值和格式保留，仅移除 Table 对象（样式隔行/筛选随之消失）。文件自带的表格不能删除。
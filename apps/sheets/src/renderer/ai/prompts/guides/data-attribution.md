# 数据来源标注指南（data-attribution）

当使用外部数据（网络搜索、抓取、API 等）填充工作表时，你必须留下可追溯的来源引用。通过 `set_hyperlink` + `set_cell` + `format_range` 来实现它们。

## 何时需要标注来源

| 数据类型 | 是否必需？ | 推荐方法 |
|---|---|---|
| 财务数据（SEC、财报） | 必需 | 页脚行或专用的 Sources 工作表 |
| 网络搜索结果 | 必需 | 来源列 |
| 用户上传的数据 | 不需要 | — |
| 由公式/计算得出的值 | 不需要 | — |
| 常识（日期、单位换算） | 不需要 | — |

## 方法 1：来源列

在数据右侧添加一个“Source”列，每一行都带有指向原始数据的超链接。适用于每行来源不同的情况。

```json
[
 {"op":"set_cell","sheetId":"s1","address":"G1","value":"Source"},
 {"op":"format_range","sheetId":"s1","range":"G1","format":{"bold":true}},
 {"op":"set_cell","sheetId":"s1","address":"G2","value":"SEC 10-K FY2024"},
 {"op":"set_hyperlink","sheetId":"s1","address":"G2","target":"https://sec.gov/..."},
 {"op":"format_range","sheetId":"s1","range":"G2:G20","format":{"fontColor":"#0563C1"}}
]
```

## 方法 2：页脚来源行

在表格下方留一个空行，然后写入一个“Sources:”部分，每行一个带超链接的来源。适用于整个表格共享几个共同来源的情况。

```json
[
 {"op":"set_cell","sheetId":"s1","address":"A23","value":"Sources:"},
 {"op":"format_range","sheetId":"s1","range":"A23","format":{"bold":true,"italic":true,"fontColor":"#666666"}},
 {"op":"set_cell","sheetId":"s1","address":"A24","value":"SEC EDGAR - NVIDIA 10-K FY2024"},
 {"op":"set_hyperlink","sheetId":"s1","address":"A24","target":"https://sec.gov/..."},
 {"op":"format_range","sheetId":"s1","range":"A24:A26","format":{"italic":true,"fontColor":"#0563C1"}}
]
```

## 方法 3：专用的 Sources 工作表

当来源很多且需要完整可追溯性时，创建一个新的“Sources”工作表（结构性操作，单独批次），包含以下列：数据点 / 来源 / URL / 检索日期。

```json
[
 {"op":"add_sheet","name":"Sources"}
]
```

在其应用后，写入新工作表：

```json
[
 {"op":"set_range","sheetId":"sSources","range":"A1:D1","values":[["Data point","Source","URL","Retrieved"]]},
 {"op":"format_range","sheetId":"sSources","range":"A1:D1","format":{"bold":true,"fillColor":"#F2F2F2"}},
 {"op":"set_range","sheetId":"sSources","range":"A2:D2","values":[["FY2024 revenue","SEC 10-K","https://sec.gov/...","2026-07-24"]]},
 {"op":"set_hyperlink","sheetId":"sSources","address":"C2","target":"https://sec.gov/..."}
]
```

## 准则

- **绝不捏造数据**：每个事实性单元格都需要来源（用户提供 / 已在工作表中 / 通过工具读取）；标注来源使来源可验证。
- 派生值通过公式计算并说明其方法——它们不需要来源追溯。
- 当超链接目标是裸域名时，系统会自动在前面加上 `https://`；工作簿内引用请使用“Sheet!A1”。
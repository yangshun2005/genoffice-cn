# 结构变更指南（structure）

## 操作定义

- `{op:"insert_rows", sheetId, row:2, count:1}` — row 从 1 开始计数；新行插入到该行**之前**。
- `{op:"delete_rows", sheetId, row, count}` — 从 row 开始删除 count 行。
- `{op:"insert_cols", sheetId, column:"C", count}` — 新列插入到该列之前；column 使用列字母。
- `{op:"delete_cols", sheetId, column, count}`
- `{op:"add_sheet", name, rows?, columns?}` — 创建空白工作表（无需 sheetId）。网格默认为 **1000 行 × 20 列**；超出网格的写入会被拒绝，公式溢出会在网格边缘截断，因此当数据量更大时，传入按预期数据量（加少量余量）设置的 `rows`/`columns` — 例如在向其中复制约 6600 行之前，先 `{op:"add_sheet", name:"ja", rows:6700}`。
- `{op:"delete_sheet", sheetId}` — 删除工作表；最后一个工作表不能删除。其他工作表上引用被删除工作表的公式会变成 #REF!（在预览警告中列出）；对于真实的 xlsx 文件，保存时还有额外的失败关闭保护（被公式/图表/定义名称引用的工作表拒绝删除）。
- `{op:"duplicate_sheet", sheetId, name?}` — 复制整个工作表（内容和格式）；省略时 name 自动生成。大文件流式模式下不可用；包含透视表的工作表不能复制。
- `{op:"set_sheet_hidden", sheetId, hidden:true|false}` — 隐藏/显示工作表；至少一个工作表必须保持可见。
- `{op:"move_sheet", sheetId, position:1}` — 移动到从 1 开始的标签位置。

## 工作表保护

`{op:"protect_sheet", sheetId, protected:true|false, password?, allow?}` — **布局类**，可与内容/格式操作共享同一批次（不受下方批处理纪律约束）。保存时写入文件，并在编辑器中强制执行（锁定单元格拒绝编辑）。`password` 为可选明文：保护时进行哈希处理，取消受密码保护的工作表时需要提供。`allow` 列出保护期间仍允许的操作（selectLockedCells、selectUnlockedCells、formatCells、formatColumns、formatRows、insertColumns、insertRows、insertHyperlinks、deleteColumns、deleteRows、sort、autoFilter、pivotTables、objects、scenarios）；未列出的标志为 false，两个 select 标志除外。

## 强制批处理纪律

结构操作会移动单元格地址，**不能与内容/格式/排序布局操作出现在同一批次**。正确的节奏：

1. 先单独提交结构变更（多个结构操作可共享同一批次，按顺序应用，提交时生效）
2. 再次调用 get_workbook_context / read_range 获取移位后的布局
3. 然后提交内容/格式变更

## 公式引用

- 插入/删除行或列时，工作簿公式中的所有 A1 引用会自动重写以适应移位（包括绝对 $ 引用和跨工作表前缀引用）。
- 引用目标被完全删除的公式会变成 **#REF!** — 预览警告会精确列出受影响的单元格。出现这种情况时，请用户确认，或主动建议修复方案。
- 区域引用（如 SUM(B2:B10)）在部分删除时会自动收缩 — 无需手动修复公式。

## 常见错误

- ❌ insert_rows 后在同一批次中写入"新行" — 被混合批次规则拒绝，且新行的地址在应用前不存在。
- ❌ 结构变更应用后立即用旧地址继续写入 — 先重新读取上下文。
- ❌ 使用 delete_rows 清除数据 — 只想清除内容时，使用 clear_range（结构不变，公式引用不受影响）。
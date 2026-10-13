# @genoffice/cli

`genoffice` 是 GenOffice 命令行。它无需打开窗口，即可将套件的文档引擎暴露给脚本和 AI 代理：打包后的应用在自己的 Node 运行时（`ELECTRON_RUN_AS_NODE`）上运行内置 CLI，因此无需额外安装任何东西。

```
genoffice info report.docx
genoffice convert scan.pdf --to docx
genoffice convert data.csv --to xlsx --out out/data.xlsx
genoffice open report.docx
genoffice convert scan.pdf --to pptx --json
genoffice guide slides                         # op 分组；`genoffice guide slides insert` 查看单个分组，`genoffice guide slides setText` 查看单个 op
genoffice slides read deck.pptx [--full] --json # 持久 id + 几何信息，代理据此定位 op；--full：全文、表格、备注；文本元素增加 `effective`（首个 run 的显示样式 + `src` = 每个值的继承来源层）
genoffice slides read deck.pptx --units in --json # 框和尺寸以英寸为单位（或 cm、pt、96 dpi 下的 px），并标注 `unit`；默认 emu
genoffice create --type pptx --ops deck.json --out deck.pptx
genoffice create --type pptx --spec deck/pages --outline deck/outline.json --out deck.pptx   # 每张幻灯片一个页面规格文件（`genoffice guide slides design|spec`）
genoffice create --type pptx --spec deck.json --out deck.pptx --render deck/previews --audit   # 同一次调用中额外生成每张幻灯片的 PNG（detail.previews）和几何审计（detail.audit）
genoffice slides check deck/outline.json | deck/pages/03.json   # 大纲规则（出错时退出码 1）/ 构建并审计单个页面文件
genoffice slides replace deck.pptx --slide 2 --spec deck/pages/03.json   # 从页面文件重建单张幻灯片
genoffice slides apply deck.pptx --ops edit.json [--dry-run] [--out copy.pptx]
genoffice slides audit deck.pptx [--slide 0] --json            # out_of_bounds / off_slide / text_overflow / text_overflow_width / overlap / picture_distorted：带持久 id 的类型化问题，几何可修复时附带 setTransform `suggest`
genoffice slides render deck.pptx --out shots/ [--scale 2]     # 通过应用的 PDF 导出为每张幻灯片生成一个 PNG
genoffice render report.docx|book.xlsx|page.html|file.pdf --out shots/ [--page 3] [--scale 2]   # 为任意文档的每一页生成一个 PNG，用于查看生成结果
genoffice render deck.pptx --out shots/ --el e_12 [--pad 16]   # 额外生成裁剪到该元素的页面（<stem>-NN-e_12.png）
genoffice render deck.pptx --out shots/ --grid [--cols 4] [--tile 320]   # 额外生成 <stem>-grid.png：所有页面拼在一张联系表上
genoffice create --type xlsx --from table.json --out book.xlsx   # 二维数组或 {sheets:[{name,rows}]}；"=..." 单元格为公式
genoffice create --type xlsx --from data.csv --out data.xlsx [--header] [--decimal ,]   # ISO 日期变为真实日期；sep= 行会被识别
genoffice sheet read book.xlsx [--sheet Data] [--range A1:D20] [--formats] --json   # 值、公式、工作表特性；--formats 增加样式、列宽、行高
genoffice sheet apply book.xlsx --cells cells.json    # [{cell:"B2", value|formula, style?, sheet?}]
genoffice sheet apply book.xlsx --ops ops.json [--dry-run]   # 工作簿 DSL：单元格、格式、图表、表格、筛选、条件格式、验证、链接、备注、窗格、页面设置、工作表（`genoffice guide sheets`）
genoffice sheet check book.xlsx --json                # 公式错误、缺失工作表引用、损坏的定义名称、图表范围偏离数据、### 列（建议：set_col_width）、占位文本、现有规则；退出码 0
genoffice create --type docx --from report.md --out report.docx      # 或 --from fragment.html（受限 HTML）
genoffice convert notes.md --to docx|html
genoffice convert report.docx --to html               # Word 编辑器的独立 HTML 导出
genoffice convert page.html --to docx                 # html2docx，与 HTML 应用的"导出为 Word"相同
genoffice convert report.docx --to md                 # 通过 markdown 编辑器的序列化器生成 GFM
genoffice convert book.xlsx --to csv [--sheet Data]   # 单个工作表，单元格文本按显示内容，UTF-8 BOM，CRLF
genoffice capabilities --json                        # GenOffice 已配置哪些云功能（不发起网络调用）
genoffice search "electron headless export" [--images] [--max 6] --json
genoffice image "isometric office, soft light" --aspect 16:9 --out hero.png
genoffice media photo.jpg --ask "What text is in this picture?" --json
genoffice docs read report.docx [--range 0-9] [--html] [--full] [--comments] [--revisions] [--header-footer] --json   # 块（--full：全文）、评论线程、修订、页眉/页脚文本
genoffice docs apply report.docx --ops ops.json [--dry-run]           # apply_ops 条目 + insert_content / replace_blocks / insert_image / insert_chart / edit_chart / set_header_footer / reply_comment / resolve_comment
genoffice docs check report.docx --json                               # 无结果的域、损坏的书签引用、过期目录、缺失图片、空图表/标题、标题级别跳跃、占位文本、待处理修订、未关闭评论；退出码 0
genoffice merge invoice-template.docx --data values.json --out invoice.docx [--force] [--strict]   # 填充 docx/pptx/xlsx 模板中的 {{key}} 占位符；报告已使用、未使用和未解析的键（或 --data '{"name":"Ada"}'）
genoffice pdf read scan.pdf [--page 3 | --range 1-5] [--full] --json     # 逐页读取文本层（默认第 1-20 页，每页 4000 字符），含页面尺寸和元数据；无头 pdfium，无应用进程
genoffice guide docs                                                   # op 签名 + 受限 HTML 规则（`guide <domain> --json` = 包含每个 op 的 schema 和指纹的目录）
genoffice selection report.docx --json   # 用户在显示该文件的编辑器中所选的内容
genoffice skill list   # 本机发现的编码代理及各自拥有的技能版本
genoffice skill install --dir ./skills --force   # 将内置技能复制到技能目录
genoffice install-cli   # 将 genoffice 放入 PATH
genoffice mcp --http 3000 [--host 127.0.0.1] [--token secret]   # 为其他机器上的客户端提供 Streamable HTTP；省略 --http 则使用 stdio
genoffice mcp --compact-schemas   # 将 ops/cells/data 声明为普通数组而非逐 op schema（更小的 tools/list；也可用 GENOFFICE_MCP_COMPACT_SCHEMAS=1）
genoffice mcp install all   # 向所有发现的编码代理注册 stdio 服务器（或指定一个：claude-code、codex、cursor、gemini、copilot、opencode、windsurf）
genoffice mcp list          # 每个代理的 MCP 配置及 genoffice 是否已注册；`mcp uninstall <agent>` 移除条目
```

Word 和 Markdown 命令在 jsdom 下运行 docs 和 markdown 编辑器（每个进程安装一次，惰性加载）。这些模块通过相对路径从应用渲染器导入，直到它们迁移到各自的包中。

工作簿写入经过 `@genoffice/xlsx-gateway`（应用的保存路径）。内存中的工作簿验证并应用单元格、格式和结构 op；快照无法容纳的 op（图表、图片、表格、筛选、条件格式、验证、超链接、备注、窗格、页面设置、保护、定义名称、标签顺序）成为网关的声明式保存载荷，与应用编辑日志的做法一致。`add_pivot` 和 `add_sparkline` 也可无头运行；只有 `refresh_pivot` 以及对编辑器会话中创建的对象的编辑（`add_table_row` / `add_table_column`、`delete_table_row` / `delete_table_column` / `delete_table`、`edit_shape`、`delete_visual`）在无头模式下被拒绝。写入公式后，genoffice 用 xlsx sidecar 求值并将结果存储为缓存值，因此 `sheet read` 和普通读取器看到的是数字而非空白。

`create`/`slides apply` 接受与应用内 AI 相同的 op（`@genoffice/pptx-ops`），以 JSON 数组或 `{ "ops": [...] }` 形式传入；`--ops -` 从 stdin 读取。图片 op 在其 `bytes` 字段中接受本地文件路径。被拒绝的 op 返回引导性错误及其用法行，以便调用方修复后重试；原子事务保持文件不变。

`create --type pptx --spec` 是应用幻灯片生成流水线（`@genoffice/pipelines`）的 CLI 端：调用方的代理按照 `genoffice guide slides design` 完成设计工作，编写样式表、大纲和每张幻灯片一个页面规格文件（`genoffice guide slides spec`），应用使用的同一页面构建器将它们转换为 pptx，测量每个文本框并使其随内容增长。应用将各阶段分离为模型调用，CLI 则将它们分离为文件：`slides check` 根据规划规则验证大纲，并构建和审计单个页面文件，然后对照其大纲条目和样式表调色板进行检查（两者都在页面文件旁边找到），`create --spec <dir>` 对每个文件运行相同检查，并拒绝组装缺少页面或页面与大纲不符的幻灯片组，`slides replace` 从文件重建单张幻灯片。`slides audit` 运行应用的确定性布局审计；`slides render` 为代理提供可查看的 PNG。genoffice 内部不发生任何模型调用。

每个命令默认打印一行人类可读摘要，或使用 `--json` 打印单个 JSON 对象（`{ status, command, summary, output_path?, warnings?, detail? }`）；`warnings[]`（`{ code, message, suggestion? }`）携带关于仍然成功的结果的提示。错误为 `{ status: "error", code, error, message, suggestion?, detail? }`：`code` 是退出码，`error` 是稳定的 snake_case 原因（`unknown_op`、`target_not_found`、`out_of_range`、`sheet_not_found`、`file_open_in_gui` 等），`suggestion` 是下一步（对单字符拼写错误提供 `did you mean …?`）；代理重试所需的事实（有效范围、可用 id、工作表名称、用法行）作为 `detail` 中的字段返回，而不仅仅在消息内。退出码：`0` 成功，`1` 用法错误，`2` 文件错误，`3` 转换失败，`4` 应用不可用。

## 模板合并

`genoffice merge <template> --data <values> --out <file>` 从 JSON 对象（文件、内联 JSON 或 `-` 表示 stdin）填充 `.docx`、`.pptx` 或 `.xlsx` 模板中的 `{{key}}` 占位符。嵌套对象展平为点分键（`{{a.b}}`）；数组不展开，并在 `detail.ignored_keys` 中返回；花括号内的空白被容忍。填充在引擎自身的查找/替换路径上运行：docs 编辑器中的 `findReplace`（带占位符且有值的表格块通过其受限 HTML 上的 `replace_blocks` 处理，因为 `findReplace` 无法到达单元格；没有填充的表格保持原样），pptx-ops 中的幻灯片级 `findReplace` 加 `setNotes`，以及工作簿 DSL 的 `set_cell`，每个占位符单元格一次：恰好是一个占位符的单元格采用值的类型（数字变为数字单元格），其他所有单元格将替换后的文本作为字面文本（`type: "text"`，因此以 `=` 开头的值不会变成公式）。

结果列出 `used_keys`、`unused_keys` 和 `unresolved_placeholders`（`{ placeholder, key, reason, location }`，含块索引、幻灯片和元素 id，或工作表和单元格）。`reason: no_key` 是数据未覆盖的占位符；`split_placeholder` 是 Word 或 PowerPoint 中跨不同格式的多个 run 存储的占位符，run 级替换无法匹配（请在一个 run 中重新输入）；`unreachable_nested` 位于嵌套的 pptx 组或组中的表格内，幻灯片级 `findReplace` 无法到达（请取消分组）。未解析的占位符保持原位，结果携带 `unresolved_placeholder` 警告；`--strict` 将它们变为同名错误且不写入任何内容。输出以原子方式写入，已存在的文件需要 `--force`，GUI 打开检查和 `GENOFFICE_ALLOWED_ROOTS` 与其他所有写入一样适用。

## MCP 服务器

`genoffice mcp` 在 stdio 上将相同命令作为 Model Context Protocol 工具提供，适用于无法或不应运行 shell 的客户端（Claude Desktop、Cursor、沙箱代理）。机器上无需其他东西：该进程像其他所有命令一样在应用的 Node 运行时上运行，GenOffice 本身仅在需要其渲染器的转换时隐藏启动。

```bash
claude mcp add --transport stdio genoffice -- genoffice mcp
```

```json
{ "mcpServers": { "genoffice": { "command": "genoffice", "args": ["mcp"] } } }
```

`genoffice mcp install <agent|all> [--dir <path>] [--force]` 为你写入该条目，指向绝对启动器路径，因此无需 `genoffice` 在 PATH 上即可工作（在 Windows 上，MCP 客户端无 shell 启动，条目以 Node 方式运行 `GenOffice.exe` 加载内置的 `genoffice.cjs`，并设置 `ELECTRON_RUN_AS_NODE=1`，与应用设置片段显示的条目相同）：`~/.claude.json`（Claude Code，用户范围；遵循 `CLAUDE_CONFIG_DIR`）、`~/.codex/config.toml`（`[mcp_servers.genoffice]`；`CODEX_HOME`）、`~/.cursor/mcp.json`、`~/.gemini/settings.json`、`~/.copilot/mcp-config.json`（Copilot CLI）、`~/.config/opencode/opencode.json` 和 `~/.codeium/windsurf/mcp_config.json`。仅触及 `genoffice` 键；启动其他程序的同名条目报告为 `occupied` 且不修改，除非使用 `--force`，无法解析的文件报告为 `manual` 并附上要粘贴的片段。`--dir` 为单个代理指定其配置文件夹；`mcp uninstall <agent|all>` 移除条目；`mcp list` 显示每个代理（无论是否检测到）及其配置路径和状态（`--json` 输出结构化行）。

工具表是 `src/mcp/tools.ts`：每个命令动词一个工具（`docs_read`、`docs_apply`、`sheet_apply`、`slides_render`、`convert` 等），每个参数取自命令自身的选项列表，因此两个界面不会漂移。Ops、单元格列表、规格和 Markdown 内联传入，并在调用期间落在临时目录中；`render` 和 `slides_render` 将 PNG 作为图像内容返回。结果与 `--json` 打印的 JSON 信封相同；错误返回 `isError` 和相同的 `error` 原因。`ops`、`cells` 和 `data` 参数携带 `guide <domain> --json` 的逐 op schema（每个 op 一个变体及其字段），因此客户端无需阅读指南即可看到字段；`genoffice mcp --compact-schemas`（或 `GENOFFICE_MCP_COMPACT_SCHEMAS=1`）为上下文预算较小的客户端将它们声明为普通数组。op 参考也是资源（`genoffice://guide/docs`、`…/sheets`、`…/slides`、`…/slides/design`、`…/slides/spec`）。

新幻灯片组经过 `deck_start`（样式表 + 大纲，返回设计和规格指南）、`deck_page`（每次调用一页，对照其大纲条目和调色板检查）、`deck_build` 和 `deck_replace`（`src/mcp/deck.ts`）。幻灯片组目录即状态，布局与命令行的分阶段流程完全一致，因此从任一侧开始的幻灯片组都可以从另一侧完成。

在反向代理后面，设置 `GENOFFICE_TRUST_PROXY_HEADERS=1`，使服务器提供的下载 URL 使用转发的 host 和 scheme；默认忽略 `X-Forwarded-*` 头。

`genoffice mcp --http <port> [--host <addr>] [--token <secret>]` 通过 Streamable HTTP 为其他机器上的客户端提供相同工具（`src/mcp/http.ts`）。文件随调用传输：`PUT /files/<name>` 上传一个文件并返回 URL，每个路径参数也接受 http(s) URL（拉取到会话的临时目录，`src/mcp/files.ts`），写入文件的工具返回 `output_url`，并在文件较小时作为嵌入资源返回字节，否则返回 `resource_link`（`src/mcp/remote.ts`）。每个会话有自己的临时目录、工作目录和幻灯片组状态；`open` 和 `selection` 不注册；未设置 `GENOFFICE_ALLOWED_ROOTS` 时，工具被限制在服务器的文件存储中。

## 将 genoffice 放入 PATH

- **macOS**
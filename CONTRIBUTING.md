# 为 GenOffice 做贡献

感谢你有兴趣参与贡献。本文档涵盖本地环境搭建、变更必须通过的检查，以及本仓库使用的约定。

## 变更如何合入

这个 GitHub 仓库是镜像：开发在私有代码树中进行，此处的 `main` 通过单个压缩快照提交（`Sync snapshot (<date>)`）推进。因此同步时每个文件都显示相同的最后提交信息，也正因如此，任何人——包括维护者——都不会直接推送到 `main`。

欢迎外部 Pull Request，并会在此处审查。变更被接受后，维护者会将其导入私有代码树，并通过 `Co-authored-by:` 尾注保留你的作者身份，随后随下一个快照发布到 `main`；你的 PR 会被关闭，并附上说明指向承载该变更的快照。GitHub 会将 PR 显示为"closed"而非"merged"——代码和署名仍会合入。Issue 和功能请求照常直接在本仓库处理。

## 仓库结构

- `apps/*` — 七个 Electron 应用（docs、sheets、slides、pdf、markdown、html、shell）。
  每个应用是一个 npm 工作区，拥有自己的 `src/main`（Electron 主进程）、`src/renderer`（React UI）和 `tests/`。
- `packages/*` — 纯 TypeScript 引擎和共享包（不依赖 Electron，有单元测试）：docx/pptx 引擎、AI agent 核心、providers、i18n、UI 套件。
- `apps/sheets/native/xlsx-engine` — Rust xlsx 引擎（作为 sidecar 进程运行），用于 xlsx 导入/导出。

## 引擎包

全部为纯 TypeScript，不依赖 Electron，有单元测试（UI 套件除外）：

- `packages/docx-engine` — docx 解析 → 块树（带 `docxIndex` 锚点和透传）、OOXML 片段生成、字节级段落修补。
- `packages/pptx-engine` / `packages/pptx-render` — pptx 模型与渲染。
- `packages/pdf2docx` — 本地 PDF → DOCX 转换：PDFium 字符级提取、纯几何版面分析、通过 `docx-engine` 重建；同一套分析驱动 PDF 应用的 PowerPoint 和 Excel 导出。
- `packages/html2docx` — 本地 HTML → DOCX 转换：页面在应用自带的 Chromium 中渲染，在浏览器内归约为文档意图树，再用 `docx` 库写成原生 OOXML；只有 Word 无对应物的视觉元素才截图。驱动 HTML 应用的"导出为 Word"。
- `packages/file-parse` — AI 附件的文本提取（office 格式、文本格式）。
- `packages/agent-core` — 所有应用共享的 AI agent 循环和技能组合。
- `packages/ai-provider` — 模型后端的 provider 抽象与流式传输。
- `packages/ai-search` — Genspark 认证 + 网页/图片搜索工具。
- `packages/i18n`、`packages/ui`、`packages/project-store`、
  `packages/electron-utils` — 共享 i18n 核心、React UI 套件、最近文件存储和 Electron 主进程辅助工具。

### 架构说明（docx 往返）

```
open docx ─► archive original by hash (never touched)
          ─► docx-engine parses word/document.xml top-level elements (w:p / w:tbl / …)
          ─► Block tree, each block anchored by docxIndex + original XML slice
          ─► Tiptap streaming editor (manual + AI editing, dirty tracking)
save      ─► dirty blocks → OOXML fragments (referencing existing styles only)
          ─► splice into original document.xml (untouched blocks keep original bytes)
          ─► repack zip; all other entries copied byte-for-byte
```

sheets 和 slides 遵循同样的理念：原始文件是唯一事实来源，编辑以窄补丁形式应用，编辑器未触及的一切在往返中保持原样。

## 快速开始

前置条件：Node 22+、npm 10+，以及 Rust 工具链（`cargo` 在 PATH 中，仅 sheets xlsx sidecar 需要）。

```bash
npm install
npm run fixtures     # generate test .docx fixtures (one-time, and after docx-engine changes)
npm run dev          # all editors + shell against Vite dev servers
npm run dev:docs     # or run a single app
```

## 每次变更必须通过的检查

CI 会在每个 PR 上运行这些检查；请先在本地运行：

```bash
npm run format:check # Prettier check for uncommitted changed/new files
npm run lint         # ESLint across the repo (0 errors required; warnings allowed)
npm run typecheck    # tsc --noEmit across every workspace
npm test             # engine + app unit tests (also runs the Rust sidecar tests)
npm run licenses     # production dependency licenses within the permissive allowlist
```

格式化刻意采用增量方式：除非现有文件属于你的变更，否则不会重新格式化。提交前请运行以下确切命令：

```bash
npm run format                              # format uncommitted changed/new files
npm run format:check                        # verify uncommitted changed/new files
npm run format:check -- --base origin/main  # verify committed files on your branch
```

CI 会自动提供 PR 或 push 的基线，只检查相对该基线变更的文件。这样格式化门禁既有效，又不会产生全仓库的格式化差异。

## 构建安装包

在仓库根目录运行——它们会重新生成第三方声明，并在打包前构建全部七个应用：

```bash
npm run dist:mac   # dmg + zip
npm run dist:win   # nsis installer
```

环境中没有 Apple 或 Windows 签名凭据时，产物未签名：代码签名和公证会被跳过并给出警告，而非失败。这是贡献者构建的预期结果。

在 macOS 上，从位于 exFAT/FAT32 卷（例如外接 USB 盘）的仓库打包会失败，因为操作系统会在构建输出旁写入隐藏的 `._` AppleDouble sidecar 文件，electron-builder 会因此出错。请将输出目录指向 APFS 路径，而不是移动仓库：

```bash
BUILD_DIR=/tmp/genoffice-release npm run dist:mac
```

`dist:win` 还要求 xlsx sidecar 位于 MinGW 交叉编译路径。在 Windows 上构建会将其留在 MSVC 目标下，因此需先将其放置到位：

```bash
cargo build --release --target x86_64-pc-windows-gnu   # from apps/sheets/native/xlsx-engine
```

或将现有的 `target/release/xlsx-sidecar.exe` 复制到
`target/x86_64-pc-windows-gnu/release/`。

## 环境变量

全部非必需——这些变量都不设置时应用也能运行。它们用于测试和本地覆盖：

| 变量                                                                                              | 作用                                                                             |
| ------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `BUILD_DIR`                                                                                       | 覆盖 electron-builder 输出目录（默认 `apps/shell/release`）                       |
| `GENOFFICE_USER_DATA`                                                                             | 覆盖 Electron userData 目录（测试隔离）                                          |
| `GENOFFICE_LANG`                                                                                  | 强制 UI 语言，而非跟随操作系统区域设置                                           |
| `GENOFFICE_FAKE_UPDATE`                                                                           | 在没有真实发布源的情况下演练更新器 UI                                            |
| `GENOFFICE_CLOUD_SLIDE`, `GENOFFICE_CLOUD_SLIDE_TIER`                                             | 将幻灯片生成路由到云端端点                                                        |
| `GSK_API_KEY`, `GSK_CLI_PATH`                                                                     | 内置 AI provider 的 Genspark 凭据 / CLI 位置                                     |
| `AI_SEARCH_DISABLE_GSK`, `SERPER_API_KEY`, `SERPLY_API_KEY`, `TAVILY_API_KEY`, `PARALLEL_API_KEY` | 禁用 gsk 搜索后端 / 提供 Serper、Serply、Tavily 或 Parallel 密钥                 |
| `XLSX_SIDECAR_PATH`, `XLSX_OPEN_PATH`, `XLSX_DEBUG_PORT`                                          | 指向本地构建的 xlsx sidecar 及其调试端口                                          |
| `*_DEV_PORT`, `*_RENDERER_URL`                                                                    | 各应用的 Vite 开发服务器端口和 renderer URL（由 `npm run dev` 设置）              |

没有凭据时 AI 功能会降级而非中断：请求会显示内联登录提示，网页搜索会回退到无需密钥的后端（Parallel 的免费 Search MCP，然后是 DuckDuckGo）。

## 编码约定

- 代码、注释、提交信息和文档**仅用英文**。面向用户的字符串走 i18n 资源（`src/renderer/i18n/`，以及 `src/main/` 中的内联主进程字典），这是非英文文本唯一该出现的地方（测试夹具文本除外）。
- 全程使用 TypeScript；在精确类型成本很低时，避免新增 `any` 表面。
- 测试位于 `apps/*/tests` 和 `packages/*/tests`（vitest）。新的引擎行为需要单元测试；仅 renderer 的 UI 调整通常不需要。
- Playwright/Electron 验收驱动器和 Office 应用对比脚本（任何驱动已构建应用或你机器上 Word/Excel/PowerPoint 的东西）是本地按需工具：不要放入代码树（它们已被 gitignore），也绝不要接入 CI。
- 避免文件无限增长：如果要向已经很大的文件添加大量新关注点，优先新建模块。

## 提交和 PR 指南

- 小而聚焦的提交，使用祈使句英文主题行
  （例如 `fix docx table border round-trip`、`add slides chart legend parsing`）。
- PR 应说明变更**为何**需要，并提及你运行了上述哪些检查。
- 文件格式保真是核心产品承诺：涉及打开/保存路径（docx/xlsx/pptx）的变更，需包含往返测试，证明未触及的内容逐字节保留。

## 报告 bug 和请求功能

使用 Issue 模板。对于疑似安全问题，**不要**开公开 Issue——请遵循 [SECURITY.md](SECURITY.md)。

## 行为准则

所有社区空间遵循
[Contributor Covenant](CODE_OF_CONDUCT.md)；参与即表示接受。

## 许可证和 CLA

没有 CLA（贡献者许可协议），我们也不打算添加。参与贡献即表示你同意你的贡献按覆盖本项目的 [Apache License 2.0](LICENSE) 许可——依据 Apache-2.0 §5，入站 = 出站。由于社区贡献保留其 Apache-2.0 条款，开源核心无法被追溯性地重新许可。

`ee/` 目录保留给未来的企业模块，采用[单独许可证](ee/LICENSE)，不接受外部贡献——维护者团队之外的 Pull Request 不得修改 `ee/` 下的文件（通过 [CODEOWNERS](.github/CODEOWNERS) 强制执行）。
<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 开源 AI 办公套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个功能完备的开源 AI 办公套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件，由你和你的 AI 共同编辑，以真实格式保存回磁盘。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="许可证：Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="最新版本"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="下载量"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub Star 数"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <b>Čeština</b> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>Web</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是面向 macOS、Windows 和 Linux 的免费开源 Microsoft Office 替代品。它能打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown 和 HTML，并为每个文档配备 AI 智能体——不是贴上去的聊天窗口，而是能读取文件、执行所需修改并精确展示改动位置的编辑器。

- **真实格式，字节级保留。** 只重写你修改的内容，文件中其余部分保持字节完全一致，文档在 Word、Excel 和 PowerPoint 中继续正常工作。
- **可审查的 AI。** 修改以修订和差异形式呈现，一键即可还原。表格获得实时公式，而非粘贴的数字。演示文稿和页面直接在画布上生成，且完全可编辑。
- **本地优先。** 文件的打开、编辑、保存和转换都在你的电脑上完成。PDF → Word / Excel / PowerPoint 以及 Markdown → Word、HTML → Word 全程在设备上运行。只有 AI 调用会离开设备，且发往你自己选择的服务商。
- **用自己的密钥，或不用密钥。** 通过 Genspark 登录即无需密钥，也可使用自己的密钥接入 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty 或任何 OpenAI 兼容端点，包括本地服务器。
- **可脚本化，面向智能体。** 应用内置 `genoffice` 命令行和面向 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的 skill，编码智能体可在你的电脑上创建、转换、读取和编辑真实的 Office 文件，无需打开任何窗口。

**下载：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情和要求见[下载](#download)部分。

## 演示

六个应用、一个 AI 面板，以及为你的编码智能体准备的命令行。每张截图都来自 macOS 上的真实应用，AI 由面板中可读的提示词驱动。

### 1 · Docs — 打开并编辑 `.docx`，AI 修改可审查

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 渲染双栏年报页面，含整页封面图、带底色的 KPI 表格、页眉页脚，80% 缩放，AI 面板已折叠"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：公司概览含横幅图片；AI 精简了 Overview 部分并插入新的项目符号部分，面板提供一键还原"></td>
</tr>
<tr>
<td><b>按 Word 的排版精确打开文件</b>——双栏分节、整页图片、带底色表格、页眉页脚、按 Word 行距度量分页。样式、批注、修订、公式和手写批注原样保留。</td>
<td><b>输入修改指令</b>——AI 只读取需要的块，重写 Overview 部分并插入新的项目符号部分。每轮 AI 都是一个可还原的快照；开启<b>修订</b>后，修改以 Word 风格的修订形式呈现。</td>
</tr>
</table>

### 2 · Sheets — `.xlsx` 带实时公式和图表，而非粘贴的数字

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 添加了 Summary 工作表，用 SUMIF 公式按地区和类别汇总收入，并插入柱状图，报告已完成 43 处修改，带撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：对于 Q2 收入哪个地区领先的提问，AI 回答欧洲并附类别明细，以可点击引用的形式标注所用单元格，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td><b>创建</b>——一句话即可让智能体添加 Summary 工作表，用真正的 <code>SUMIF</code> 公式按地区和类别汇总，插入柱状图，43 处修改作为一批可还原操作执行。</td>
<td><b>提问</b>——对工作簿的查询返回推理过程和具体单元格作为可点击引用。底层：自研 Rust 引擎处理 `.xlsx`、数据透视表、筛选、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资人演示文稿的延时记录：AI 在面板中规划大纲，幻灯片逐步出现在画布上，完成的演示文稿以行动号召结尾" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 生成的 Aurora Home 投资人演示文稿封面幻灯片在画布上，面板中显示原始单行提示词和 AI 对所做工作的总结"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的设计结尾幻灯片，左侧缩略图条，AI 面板总结叙事线"></td>
</tr>
<tr>
<td><b>一行输入</b>——“为 Aurora Home 创建一份 10 页投资人演示文稿……”。GenOffice 规划叙事线、查找数据，并在画布上逐页生成真正的 `.pptx` 文件。</td>
<td><b>输出完整演示文稿</b>——十一页设计一致的幻灯片，含统一排版、图片和结尾行动号召；可继续用母版、版式、智能参考线和无损裁剪编辑，或让面板改样式、重写和重排。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，在设备上转换 PDF 为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：编辑文本模式在页面上勾勒每个文本块以就地编辑，AI 面板回答关于报告的提问并附页码引用"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 显示从 Helios 季度 PDF 报告本地转换的 Word 文档，在第二个标签页中与原始 PDF 并排打开"></td>
</tr>
<tr>
<td><b>直接在页面上编辑</b>——编辑文本模式勾勒每个文本块以就地重写；内容流通过 PDFium 重写并保留原始字体，而非用遮盖注释。向 AI 提问长报告，获得带页码引用的回答。</td>
<td><b>设备上转换</b>——<b>PDF Converter → PDF to Word</b> 生成可编辑的 `.docx`，在 Docs 中与源文件并排打开，保留标题、统计行和段落。Excel 和 PowerPoint 目标同理；扫描页走系统 OCR。</td>
</tr>
</table>

### 5 · HTML — AI 页面和界面构建器，先出设计简报

告诉它页面用途和面向对象。AI 先设计**设计简报**——钩子、配色、排版和风格方向——再依据这些 token 生成单个独立 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 改变 Lumen 落地页样式的延时记录：面板中一个 Restyle 请求将深色 Midnight Studio 页面变为温暖的 Solar Daybreak 版本，所有区块和内容保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的深色 Midnight Studio 风格落地页，在实时预览中显示，AI 面板总结刚创建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一 Lumen 落地页被 AI 重新设计为温暖的 Solar Daybreak 风格：纸质背景、衬线标题和橙色强调色，所有区块和文本保留"></td>
</tr>
<tr>
<td><b>一个提示词生成</b>——为 Lumen 生成醒目的 hero、功能卡片、定价和等候名单表单，采用 Midnight Studio 风格。点击任意元素即可改样式，双击编辑文本，或切换到 CodeMirror 源码视图。</td>
<td><b>同一设计，新方向</b>——一个 <b>Restyle</b> 请求替换简报 token，页面随之调整：温暖纸张、编辑风衬线字体、日光橙强调色，内容不重写。可全屏演示，或导出为 PDF 或原生可编辑 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为独立设计师生成的个人仪表盘界面，温暖亚麻风格，含左侧栏、页脚问候语和四个指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：生成的电动汽车市场数据报告，报纸风格，含页脚报头、1730 万主数据和统计行"></td>
</tr>
<tr>
<td><b>界面设计</b>——“个人仪表盘”起始模板将人物设定变为可用布局：左侧栏、问候语、计费工时迷你图、发票和利用率卡片——全是真实 HTML，可交给开发者。</td>
<td><b>数据故事</b>——“数据报告”起始模板生成编辑风报纸：页脚报头、一个主数据、分隔线统计行、内联 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown — 基于纯 `.md` 的块编辑器，带 Ask AI 功能

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中段落显示 Ask AI 弹窗，含输入指令和建议芯片如改进、精简、扩展和修正语法，以及立即发送和加入队列按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 渲染含表格、Mermaid 流程图和任务列表的发布说明文档，左侧为 AI 面板起始提示词"></td>
</tr>
<tr>
<td><b>对选中内容提问 AI</b>——选中任意文本即出现 <b>Ask AI</b> 芯片：输入指令或选择建议，立即发送，或将多个锚定修改加入队列批量执行。每个应用都有相同入口。</td>
<td><b>渲染并保存为纯 Markdown</b>——Tiptap 块编辑器中的标题、列表、表格、图片、代码块和 Mermaid 图表，写回纯 `.md` 文件，<b>Markdown → Word</b> 导出完全本地。</td>
</tr>
</table>

### 7 · CLI — 你的编码智能体驱动 GenOffice，在你的电脑上

GenOffice 内置 `genoffice` 命令行和智能体 skill。安装 skill 后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 可通过与应用相同的引擎创建、转换、读取和编辑真实 Office 文件，无需打开任何窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示编码智能体通过 genoffice 命令行创建的八页太阳系演示文稿：画布上的封面幻灯片，左侧八个缩略图，AI 面板已打开" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的八张渲染幻灯片并排：标题、探索时间线、四个关键数字、行星平均直径柱状图、岩石世界与气态巨行星、太阳占 99.8% 的主数据、四颗巨行星网格和结论"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置，集成页面：genoffice skill 已安装到 Claude Code，Codex 和 Cursor 旁有安装按钮"></td>
</tr>
<tr>
<td><b>给你的智能体一个提示词</b>——“创建一份关于太阳系的八页演示文稿。”智能体读取 skill，编写样式表、大纲和每页规格，用 <code>genoffice image</code> 生成两张图片，让 <code>genoffice slides check</code> 拒绝任何溢出或重叠的内容，再由 <code>genoffice create</code> 组装 <code>.pptx</code>，<code>slides render</code> 返回每页一张 PNG 供检查。</td>
<td><b>在设置 → 集成中一次安装</b>——GenOffice 列出本机找到的编码智能体，并将 skill 写入你选择的每个智能体。也可下载 skill 的 zip，或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行和智能体 skill</a>部分。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 使用相同工具

每个 `genoffice` 命令同时也是 MCP 工具。Claude Code、Claude Desktop、Cursor 及任何其他 MCP 客户端都可自行启动 `genoffice mcp`——无需安装 skill，无需打开窗口——获得 29 个工具以及作为资源（resources）的操作参考指南。应用内的第二个 HTTP 服务器让智能体在你眼前直接在可见的编辑器标签页中构建 Word 文档。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 genoffice MCP 服务器构建八页可再生能源投资人演示文稿的加速记录：搜索图片和照片，用 media 检查每张候选照片，deck_start 写入样式表和大纲，deck_page 每次添加一页已检查的页面，deck_build 组装 .pptx，slides_render 返回每张幻灯片的图片；完成的演示文稿随后在 GenOffice Slides 中打开" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/mcp-deck-in-app.webp" alt="GenOffice Slides 显示 Claude Code 通过 genoffice M
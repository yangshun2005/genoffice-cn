<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 开源 AI 驱动的 Office 套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个功能完整的开源 AI Office 套件</b><br>
Word、Excel、PowerPoint 和 PDF 文件由你和你的 AI 共同编辑，保存回真实格式</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="License: Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="Latest release"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="Downloads"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub stars"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <b>ไทย</b> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>网站</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是 Microsoft Office 的免费开源替代品，支持 macOS、Windows 和 Linux。原生打开和保存 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown 和 HTML，并将 AI 智能体置于每份文档旁边——不是贴在一旁的聊天框，而是能读取文件、执行编辑并清晰展示修改了哪些内容的编辑器。

- **真实格式，逐位保留** 只有你修改的部分会被重写，文件其余部分保持逐字节不变，文档在 Word、Excel 和 PowerPoint 中继续可用
- **可审查的 AI** 编辑以修订痕迹和 diff 形式呈现，附带一键回退按钮。电子表格获得实时计算的公式，而非覆盖的数值。幻灯片和文档页面在画布上生成，且仍可完整编辑
- **设计上本地运行** 文件在你的机器上打开、编辑、保存和转换。PDF → Word / Excel / PowerPoint、Markdown → Word 和 HTML → Word 全部本地完成。只有 AI 调用会离开机器，发往你选择的服务商
- **用自己的密钥，或完全不用** 使用 Genspark 登录即可跳过密钥配置，或使用你自己的密钥对接 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty 或任何兼容 OpenAI 的端点，包括本地模型服务器
- **可脚本化，为智能体就绪** 应用自带 `genoffice` 命令行和适用于 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的技能，让编码智能体无需打开任何窗口即可在你的机器上创建、转换、读取和编辑真实的 Office 文件

**下载：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详细信息和系统要求见[下载](#download)章节

## 演示

六个应用，一个 AI 面板，以及为你的编码智能体准备的命令行。每张截图都是运行在 macOS 上的真实应用，AI 由你在面板中可读到的提示词驱动。

### 1 · Docs — 打开并编辑 `.docx`，AI 可审查

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 显示一份双栏年度报告页面，包含全宽封面图、带阴影的 KPI 表格、页眉和页脚，缩放 80%，AI 面板已折叠"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：公司概览页面带横幅图，AI 已精简 Overview 部分并插入新的项目符号部分，面板中有一键回退按钮"></td>
</tr>
<tr>
<td><b>按 Word 的排版打开文件</b> — 双栏部分、全页图片、带阴影的表格、页眉和页脚、按 Word 行尺度分页、样式、批注、修订痕迹、公式和手写内容在每次打开-保存循环中保持不变</td>
<td><b>请求编辑</b> — AI 读取所需区块，重写 Overview 部分并插入新的项目符号部分。每次 AI 操作都是可回退的快照，开启 <b>Track changes</b> 后编辑以 Word 风格的修订呈现</td>
</tr>
</table>

### 2 · Sheets — 带实时计算公式和图表的 `.xlsx`，而非覆盖的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 添加了 Summary 工作表，包含按地区和类别使用 SUMIF 公式的收入及柱状图，并报告 43 项更改及 Undo 按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：当被问及哪个地区 Q2 收入领先时，AI 回答欧洲，附按类别明细及所用单元格的可点击引用，位于 Orders 工作表旁"></td>
</tr>
<tr>
<td><b>创建它</b> — 从一句话开始，智能体添加 Summary 工作表，包含按地区和类别使用真实 <code>SUMIF</code> 公式，插入柱状图，并将全部 43 项更改合并为一个可回退的批次</td>
<td><b>询问它</b> — 关于工作簿的问题会得到带推理和实际使用单元格的答案，以可点击引用形式呈现。背后是自研的 Rust `.xlsx` 引擎，支持数据透视表、切片器、条件格式和公式溯源</td>
</tr>
</table>

### 3 · Slides — 从提示词到 `.pptx` 幻灯片

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 为 Aurora Home 投资者演示创建幻灯片的延时摄影：AI 在控制面板中规划叙事，幻灯片逐张出现在画布上，完成的演示文稿以 closing ask 收尾" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 在画布上为 Aurora Home 投资者数据演示生成的封面幻灯片，面板中显示原始单行提示词和 AI 创建内容的摘要"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的设计收尾幻灯片，左侧有缩略图条，AI 面板总结叙事"></td>
</tr>
<tr>
<td><b>只需一行</b> — "为 Aurora Home 创建一份 10 页投资者演示文稿……" GenOffice 规划叙事、研究数据，并将每张幻灯片作为真实 `.pptx` 绘制到画布上</td>
<td><b>获得完整演示文稿</b> — 11 张设计幻灯片，排版和图像风格一致，以行动号召收尾。可用母版、版式、智能参考线和无损裁剪继续编辑，或让面板帮助调整样式、重写和重新排序</td>
</tr>
</table>

### 4 · PDF — 原位编辑 PDF 文本，本地将 PDF 转换为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：Edit text 模式为页面上每个文本块绘制边框以便原位编辑，AI 面板回答关于报告的问题并附页码引用"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 显示从 Helios 季度报告 PDF 本地转换而来的 Word 文档，在第二个标签页中打开，旁边是原始 PDF"></td>
</tr>
<tr>
<td><b>在页面上编辑</b> — Edit text 模式为每个文本块绘制边框以便原位输入覆盖，content stream 通过 PDFium 使用原字体重写，而非粘贴文本覆盖。向 AI 询问长报告并获得带页码引用的答案</td>
<td><b>本地转换</b> — <b>PDF Converter → PDF to Word</b> 生成可编辑的 `.docx`，在 Docs 中与源文件并排打开，标题、数据行和段落完整保留。Excel 和 PowerPoint 目标同样工作，扫描页面通过系统 OCR 处理</td>
</tr>
</table>

### 5 · HTML — AI 网页和 UI 构建器，从设计简报开始

告诉它这个页面是做什么的、面向谁，AI 会先提出一份**设计简报**——hook、配色、排版和风格方向——然后按这些 token 生成单文件 `.html`。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 为 Lumen 落地页重新设计样式的延时摄影：控制面板中一次 Restyle 请求将深色 Midnight Studio 页面变为温暖的 Solar Daybreak 版本，所有部分和内容保持原位" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，Midnight Studio 深色风格，在实时预览中显示，AI 面板总结已创建的内容"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="Lumen 落地页被 AI 重新设计为温暖的 Solar Daybreak 风格：纸色背景、衬线标题和橙色强调色，所有部分和内容保持原位"></td>
</tr>
<tr>
<td><b>从单一提示词构建</b> — 为 Lumen 创建醒目的 hero、功能卡片、定价和 waitlist 表单，采用 Midnight Studio 风格。点击任意元素调整样式，双击编辑文本，或通过 CodeMirror 切换到源代码视图</td>
<td><b>相同设计，新方向</b> — 一次 <b>Restyle</b> 请求切换简报 token，页面随之调整：温暖的纸色背景、编辑风格衬线字体、阳光橙强调色，无需重写任何内容。全屏展示，或导出为 PDF 或可编辑的原生 Word 文档</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由职业设计师生成的个人仪表盘页面，温暖的亚麻风格，带侧边栏、衬线问候语和四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：以报纸风格生成的电动汽车市场数据报告，带衬线标题、1730 万醒目数字和数据行"></td>
</tr>
<tr>
<td><b>UI 模型</b> — "personal dashboard" 起始模板将人物画像转化为可用布局：侧边栏、问候语、可计费小时迷你图、发票和使用卡片，全部是真实 HTML，可交给开发者</td>
<td><b>数据叙事</b> — "data report" 起始模板构建报纸社论：衬线标题、单一醒目数字、带分隔线的数据行、内联 SVG 图表和方法说明</td>
</tr>
</table>

### 6 · Markdown — 纯文本 `.md` 文件之上的块编辑器，带 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中的段落显示 Ask AI 弹出框，包含已输入的指令和建议芯片，如 Polish、Make more concise、Expand 和 Fix grammar，以及 Send now 和 Add to queue 按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 显示一份发布说明文档，包含表格、Mermaid 流程图和任务列表，左侧有 AI 面板的起始提示词"></td>
</tr>
<tr>
<td><b>就选中文本询问 AI</b> — 选中任意文本，<b>Ask AI</b> 芯片即出现：输入指令或选择建议，立即发送，或将多个位置锚定的编辑排队后一次性运行。所有应用都有相同的入口点</td>
<td><b>渲染后保存回纯 Markdown</b> — Tiptap 块编辑器中的标题、列表、表格、图片、代码块和 Mermaid 图表写回纯 <code>.md</code>，并支持完全本地的 <b>Markdown → Word</b> 导出</td>
</tr>
</table>

### 7 · CLI — 你的编码智能体在你的机器上驱动 GenOffice

GenOffice 自带 `genoffice` 命令行和智能体技能。安装技能后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 即可通过与应用相同的引擎创建、转换、读取和编辑真实 Office 文件，无需打开任何窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示编码智能体通过 genoffice 命令行创建的 8 页太阳系演示文稿：画布上的封面幻灯片、左侧 8 张缩略图和打开的 AI 面板" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的全部 8 张渲染幻灯片并排：封面、探索时间线、四个关键数字、行星直径柱状图、岩石行星对比气态巨行星、太阳占比 99.8% 的醒目数字、四张气态巨行星网格和总结"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice Settings 的 Integrations 页面：genoffice 技能已安装到 Claude Code，Codex 和 Cursor 旁有 Install 按钮"></td>
</tr>
<tr>
<td><b>一个提示词到你的智能体</b> — "创建一份关于太阳系的 8 页演示文稿"。智能体读取技能，编写样式表、大纲和每页规格，用 <code>genoffice image</code> 生成两张照片，让 <code>genoffice slides check</code> 拒绝任何溢出或重叠的内容，然后 <code>genoffice create</code> 组装 <code>.pptx</code>，<code>slides render</code> 返回每张幻灯片一张 PNG 供查看</td>
<td><b>从设置 → 集成一次性安装</b> — GenOffice 列出本机找到的编码智能体，并将技能写入你选择的每个智能体，或将技能下载为 zip，或运行 <code>npx skills add genspark-ai/genoffice</code>。完整命令和工作流见<a href="#command-line-and-agent-skill">命令行和智能体技能</a></td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 使用同一套工具

每个 `genoffice` 命令同时也是 MCP 工具。Claude Code、Claude Desktop、Cursor 和其他 MCP 客户端可以自行调用 `genoffice mcp`，无需安装技能，无需打开任何窗口，即可获得 29 个工具及作为 resource 的工作流参考文档。应用内的第二个 HTTP 服务器还让智能体在可见的编辑器标签页中创建 Word 文档，供你实时观看。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 genoffice MCP 服务器创建 8 页可再生能源投资者简报的延时摄影：用 search 查找数据和照片，用 media
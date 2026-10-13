<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 开源 AI Office 套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个功能最完整的开源 AI Office 套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件，由你和你的 AI 共同编辑，以真实格式保存。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="License: Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="Latest release"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="Downloads"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub stars"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <b>Bahasa Melayu</b> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是 Microsoft Office 的免费开源替代品，支持 macOS、Windows 和 Linux。它能打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown 和 HTML，并将 AI 智能体置于每份文档旁边——不是贴在旁边的聊天框，而是能读取文件、做出修改、并精确告诉你改动了什么的编辑器。

- **真实格式，逐位保留。** 只有你编辑的部分会被重写。文件中其余内容逐位保留，因此文档在 Word、Excel 和 PowerPoint 中依然正常。
- **可审查的 AI。** 编辑以修订（tracked changes）形式呈现，支持 diff 和一键回滚。表格获得实时公式，而非粘贴的数值。幻灯片和页面直接在画布上生成，且完全可编辑。
- **本地优先设计。** 文件在你的机器上打开、编辑、保存和转换。PDF → Word / Excel / PowerPoint、Markdown → Word 和 HTML → Word 全部在本地运行。只有 AI 调用会离开你的机器，发送给你选择的提供商。
- **用自己的密钥，或完全不用。** 使用 Genspark 登录则无需任何密钥，或自带 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty 或任何兼容 OpenAI 的端点（包括本地服务器）的密钥。
- **可脚本化，面向智能体。** 应用附带 `genoffice` 命令行和适用于 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的技能，编码智能体无需打开任何窗口即可在你的机器上创建、转换、读取和编辑真实的 Office 文件。

**获取：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情和要求见[下载](#download)。

## 演示

六个应用、一个 AI 面板，以及一条供编码智能体使用的命令行。每张截图都是 macOS 上的真实应用，AI 由面板中可读的提示词驱动。

### 1 · Docs — 打开并编辑 `.docx`，AI 可审查

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 显示双栏年度报告页面，含全宽封面图、带底纹的 KPI 表格、页眉和页脚，80% 缩放，AI 面板折叠"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：带横幅图的公司概览；AI 精简 Overview 部分并插入新的项目符号部分，面板提供一键回滚"></td>
</tr>
<tr>
<td><b>按 Word 的排版方式打开文件</b>——双栏分节、全宽图片、带底纹表格、页眉页脚、基于 Word 行度量的页码。样式、批注、修订、公式和墨迹在往返后依然完整。</td>
<td><b>请求编辑</b>——AI 读取所需块，重写 Overview 部分并插入新的项目符号部分。每轮 AI 都是一个可回滚的快照；开启 <b>Track changes</b> 后，编辑以 Word 风格修订呈现。</td>
</tr>
</table>

### 2 · Sheets — 带实时公式和图表的 `.xlsx`，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 添加 Summary 工作表，使用 SUMIF 公式按地区和类别汇总收入，并添加柱状图，报告已应用 43 项更改，带 Undo 按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：被问及哪个地区 Q2 收入最高时，AI 回答欧洲并给出类别明细，以可点击链接引用所用单元格，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td><b>构建它</b>——从一句话开始，智能体添加 Summary 工作表，使用真实的 <code>SUMIF</code> 按地区和类别汇总，插入柱状图，并将 43 项更改作为一个可撤销的批次执行。</td>
<td><b>询问它</b>——关于工作簿的问题通过推理回答，并引用实际使用的单元格作为可点击参考。底层：自研 Rust <code>.xlsx</code> 引擎、数据透视表、切片器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 延时摄影生成 Aurora Home 投资者演示文稿：AI 在面板中规划故事线，幻灯片逐一出现在画布上，完成的演示文稿以 closing ask 结束" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 生成的 Aurora Home 投资者演示文稿封面幻灯片在画布上，面板中有一行原始提示词和 AI 构建内容摘要"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一 11 页演示文稿的结尾幻灯片，左侧有缩略图条，AI 面板总结故事线"></td>
</tr>
<tr>
<td><b>一行输入</b>——“Create a 10-slide investor pitch deck for Aurora Home…”。GenOffice 规划故事线、研究数据，并直接在画布上以真实 <code>.pptx</code> 起草每张幻灯片。</td>
<td><b>完成的演示文稿输出</b>——十一张设计精良的幻灯片，排版一致、图片统一、结尾有行动号召；继续用母版、版式、智能参考线和无损裁剪编辑，或让面板重新设计样式、重写和重排。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，本地将 PDF 转换为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：Edit text 模式在页面上勾勒每个文本块以便就地重新编辑，AI 面板以页码引用回答关于报告的问题"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 显示从 Helios 季度回顾 PDF 本地转换而来的 Word 文档，在原始 PDF 旁边的第二个标签页中打开"></td>
</tr>
<tr>
<td><b>在页面内编辑</b>——Edit text 模式勾勒每个文本块以便就地重新输入；内容流通过 PDFium 用原始字体重写，而非仅覆盖的注释。向 AI 询问长报告并获得带页码引用的回答。</td>
<td><b>本地转换</b>——<b>PDF Converter → PDF to Word</b> 生成可编辑的 <code>.docx</code>，在 Docs 中与源文件并排打开，标题、统计行和段落完整。Excel 和 PowerPoint 目标同理；扫描页通过系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — AI 辅助的页面和 UI 构建器，设计摘要优先

说明页面的用途和面向对象。AI 先提出**设计摘要**——钩子、配色、排版和风格方向——再基于这些 token 构建单个自包含 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 延时摄影重新设计 Lumen 落地页样式：面板中一次 Restyle 请求将深色 Midnight Studio 页面变为温暖的 Solar Daybreak 版本，同时每个区块和所有内容保持原位" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，采用深色 Midnight Studio 方向，在实时预览中显示，AI 面板总结刚构建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一 Lumen 落地页被 AI 重新设计为温暖的 Solar Daybreak 方向：纸感背景、衬线标题和橙色点缀，每个区块和所有文本均保留"></td>
</tr>
<tr>
<td><b>从一条提示词生成</b>——Lumen 的大胆 hero、功能卡片、定价和候补表单，以 Midnight Studio 方向构建。点击任意元素重新设计样式，双击编辑文本，或切换到 CodeMirror 源码视图。</td>
<td><b>相同设计，全新方向</b>——一次 <b>Restyle</b> 请求切换这些摘要 token，页面随之改变：温暖纸张、编辑衬线、日光橙点缀，无需重写任何内容。全屏展示，或导出为 PDF 或可编辑的原生 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由设计师生成的个人仪表盘 UI，采用温暖亚麻风格，带左侧栏、衬线问候语和四张指标卡"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：以大字报风格生成的电动汽车市场数据报告，带衬线报头、1730 万主数字和统计行"></td>
</tr>
<tr>
<td><b>UI 设计</b>——“个人仪表盘”提示词将一个人设转化为可用布局：左侧栏、问候语、充电时钟迷你图、发票和使用卡片，全部是可交给开发者的真实 HTML。</td>
<td><b>数据故事</b>——“数据报告”提示词构建编辑风格的大字报：衬线报头、一个主数字、分隔线统计行、内联 SVG 图表和方法论说明。</td>
</tr>
</table>

### 6 · Markdown — 基于纯 `.md` 的块编辑器，带 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中的段落显示 Ask AI 弹出框，含已输入的指令和建议芯片如 Polish、Make more concise、Expand 和 Fix grammar，以及 Send now 和 Add to queue 按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 显示发布说明文档，含表格、Mermaid 流程图和任务列表，左侧有 AI 面板起始提示词"></td>
</tr>
<tr>
<td><b>对选中文本询问 AI</b>——选中任意句子，<b>Ask AI</b> 芯片出现：输入指令或选择建议，立即发送，或排队多个锚定编辑并一次性执行。同一入口存在于每个应用中。</td>
<td><b>渲染显示，保存为纯 Markdown</b>——Tiptap 块编辑器中的标题、列表、表格、图片、代码块和 Mermaid 图表，重写为纯 <code>.md</code>，并支持完全本地的 <b>Markdown → Word</b> 导出。</td>
</tr>
</table>

### 7 · CLI — 你的编码智能体在你的机器上驱动 GenOffice

GenOffice 附带 `genoffice` 命令行和智能体技能。安装该技能后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 可通过与应用相同的引擎创建、转换、读取和编辑真实 Office 文件，无需打开任何窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示编码智能体通过 genoffice 命令行构建的八页太阳系演示文稿：画布上的封面幻灯片、左侧八个缩略图和打开的 AI 面板" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="八页太阳系演示文稿并排显示：封面、探索时间线、四个关键数字、行星直径柱状图、岩石世界对巨行星、太阳占 99.8% 的关键数字、四颗巨行星网格和总结"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice Settings 的 Integrations 页面：genoffice 技能已安装到 Claude Code，Codex 和 Cursor 旁边有 Install 按钮"></td>
</tr>
<tr>
<td><b>向你的智能体发一条提示词</b>——“Build an eight-slide deck about the Solar System.” 智能体读取技能，编写样式表、大纲和每页规格，用 <code>genoffice image</code> 生成两张照片，让 <code>genoffice slides check</code> 拒绝任何溢出或重叠的内容，再由 <code>genoffice create</code> 组装 <code>.pptx</code>，<code>slides render</code> 返回每页 PNG 供查看。</td>
<td><b>一次安装，从 Settings → Integrations</b>——GenOffice 列出在此计算机上发现的编码智能体，并将技能写入你选择的每一个。或下载技能 zip，或运行 <code>npx skills add genspark-ai/genoffice</code>。完整命令和工作流见<a href="#command-line-and-agent-skill">命令行和智能体技能</a>。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 使用相同工具

每条 `genoffice` 命令同时也是 MCP 工具。Claude Code、Claude Desktop、Cursor 和任何其他 MCP 客户端可自行启动 `genoffice mcp`，无需安装技能、无需打开窗口，即可获得 29 个工具以及作为资源（resources）的操作参考。应用内的第二个 HTTP 服务器让智能体在可见的编辑器标签页中构建 Word 文档，同时你可以观看。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 genoffice MCP 服务器构建八页可再生能源投资者简报的延时录像：搜索图表和照片，用 media 检查每张候选图片，deck_start 写入样式表和大纲，deck_page 一次添加一页并检查，deck_build 组装 .pptx，slides_render 返回每页图片；完成的演示文稿随后在 GenOffice Slides 中打开" width="100%">
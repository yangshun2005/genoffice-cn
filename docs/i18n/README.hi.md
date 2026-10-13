<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 开源 AI 办公套件：内置 AI 面板，支持 Docs、Sheets、Slides、PDF、Markdown 和 HTML" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个功能完备的开源 AI 办公套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件由你和你的 AI 共同编辑，并以原始格式保存。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="License: Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="Latest release"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="Downloads"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub stars"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <b>हिन्दी</b> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是 Microsoft Office 的免费开源替代品，支持 macOS、Windows 和 Linux。它能打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown 和 HTML，并为每个文档配备一个 AI 智能体——它不是嵌在边上的聊天框，而是一个能读取文件、做出修改、并精确展示改动位置的编辑器。

- **原生格式，字节级保留。** 只重写你实际编辑的部分，文件其余部分逐字节保持不变，因此文档在 Word、Excel 和 PowerPoint 中表现如初。
- **可审阅的 AI。** 编辑以修订标记和差异的形式呈现，一键即可回滚。电子表格得到的是实时公式，而非粘贴的数字。幻灯片和页面在画布上生成，始终保持完全可编辑。
- **设计上即本地优先。** 文件的打开、编辑、保存和转换全在你的机器上完成。PDF → Word / Excel / PowerPoint、Markdown → Word、HTML → Word 均在设备本地转换。只有 AI 调用会离开本机，且仅发往你选择的提供商。
- **用你的密钥，或不用密钥。** 登录 Genspark 免去密钥烦恼，或自带密钥接入 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty 或任何 OpenAI 兼容端点——包括本地服务器。
- **可脚本化，面向智能体。** 应用自带 `genoffice` 命令行，以及适用于 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的 skill，让编码智能体无需打开任何窗口，即可在你的机器上创建、转换、读取和编辑真正的 Office 文件。

**获取：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情与要求见[下载](#download)。

## 演示

六个应用，一个 AI 面板，外加一条供编码智能体使用的命令行。每张截图都来自 macOS 上运行的真实应用，AI 由面板中可见的提示词驱动。

### 1 · Docs — 打开并编辑 `.docx`，AI 改动可审阅

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 以 80% 缩放显示一份双栏年度报告页面，包含全宽封面图、带底色的 KPI 表格、页眉和页脚，AI 面板处于折叠状态"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：一份带横幅图片的公司概览；AI 精简了概览并新增了一个项目符号小节，面板提供一键回滚选项"></td>
</tr>
<tr>
<td><b>按 Word 的排版方式打开文件</b> — 双栏小节、全出血图片、带底色表格、页眉页脚，以及基于 Word 行度量标准的分页。样式、批注、修订、公式和墨迹均无损往返。</td>
<td><b>直接说出要改什么</b> — AI 读取相关区块，重写概览并新增一个项目符号小节。AI 的每一轮都是一个可回滚的快照；开启 <b>Track changes</b> 后，编辑以 Word 风格的修订形式呈现。</td>
</tr>
</table>

### 2 · Sheets — `.xlsx` 配实时公式和图表，而非粘贴的数字

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 使用 SUMIF 公式新增了一张按地区和类别汇总营收的 Summary 工作表，并插入柱状图，报告了 43 项已应用的更改，配有 Undo 按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：当被问及 Q2 营收哪个地区领先时，AI 在 Orders 工作表旁给出 Europe 的答案及类别明细，并将所用单元格引用为链接"></td>
</tr>
<tr>
<td><b>创建</b> — 一句话，智能体就新增一张按地区和类别使用真实 <code>SUMIF</code> 的 Summary 工作表，插入柱状图，并将 43 项更改作为单个可撤销批次应用。</td>
<td><b>提问</b> — 关于工作簿的问题会得到带推理的答案，所用单元格以可点击引用形式给出。底层：自研 Rust <code>.xlsx</code> 引擎，支持数据透视表、切片器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 一句提示词生成 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资者演示文稿的延时过程：AI 面板规划故事线，幻灯片逐张出现在画布上，成品以 closing ask 收尾" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：画布上 AI 生成的 Aurora Home 投资者演示文稿封面页，附原始单行提示词及面板中 AI 对生成内容的总结"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的设计感收尾页，左侧缩略图条，AI 面板总结故事线"></td>
</tr>
<tr>
<td><b>输入一行</b> — “为 Aurora Home 制作一份 10 页投资者路演演示文稿……”。GenOffice 规划故事线、研究数据，并将每张幻灯片作为真正的 <code>.pptx</code> 在画布上生成。</td>
<td><b>输出成品演示文稿</b> — 十一张设计精良的幻灯片，排版、图像和收尾行动号召风格统一；可继续用母版、版式、智能参考线和非破坏性裁剪编辑，或让面板重新设计风格、重写和重排。</td>
</tr>
</table>

### 4 · PDF — 直接在原位编辑 PDF 文本，在设备本地将 PDF 转为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：Edit text 模式勾勒出页面上每个文本块以支持原位编辑，AI 面板则用页码引用回答关于报告的问题"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 中显示从 Helios 季度回顾 PDF 本地转换而来的 Word 文档，与原始 PDF 并排在不同标签页中打开"></td>
</tr>
<tr>
<td><b>在页面内编辑</b> — Edit text 模式勾勒出每个文本块以支持原位重新输入；内容流通过 PDFium 以原始字体重写，而非覆盖式批注。向 AI 询问长篇报告，可获得带页码引用的答案。</td>
<td><b>在设备本地转换</b> — <b>PDF Converter → PDF to Word</b> 生成可编辑的 <code>.docx</code>，在 Docs 中与源文件并排打开，标题、数据行和段落完整保留。Excel 和 PowerPoint 目标同理；扫描页走系统 OCR。</td>
</tr>
</table>

### 5 · HTML — AI 页面与 UI 构建器，先出设计简报

说明页面面向谁、目的为何。AI 先给出**设计简报**——钩子、配色、排版和风格方向——再基于同一套设计令牌生成单个自包含 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时过程：面板中的 Restyle 请求将深色 Midnight Studio 页面变为暖色 Solar Daybreak 版本，同时每个小节和全部内容保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，采用深色 Midnight Studio 方向，在实时预览中展示，AI 面板总结刚生成的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="AI 将同一 Lumen 落地页重新设计为暖色 Solar Daybreak 方向：纸质背景、衬线标题和橙色点缀，同时每个小节和全部文案保持不变"></td>
</tr>
<tr>
<td><b>一句提示词生成</b> — 为 Lumen 打造醒目主视觉、功能卡片、定价和候补名单表单，采用 Midnight Studio 方向。点击任意元素即可重新设计风格，双击编辑文本，或切换到 CodeMirror 源码视图。</td>
<td><b>同一设计，全新方向</b> — 一次 <b>Restyle</b> 请求更换简报令牌，整个页面随之改变：暖色纸张、编辑风衬线、日光橙点缀——无需重写任何内容。可全屏演示，或导出为 PDF 或原生可编辑 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由设计师生成的个人仪表盘 UI，采用暖色亚麻风格，包含左侧栏、衬线问候语和四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：生成的 EV 市场数据报告，采用宽幅风格，包含衬线报头、1730 万的头条数字和数据行"></td>
</tr>
<tr>
<td><b>UI 原型</b> — “personal dashboard” 起始模板将人物设定变为可运行的布局：左侧栏、问候语、带标签的工时迷你折线图、发票和利用率卡片——全是真实 HTML，可直接交给开发者。</td>
<td><b>数据叙事</b> — “data report” 起始模板生成编辑风宽幅版面：衬线报头、头条数字、以分隔线隔开的数据行、内联 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown — 纯 `.md` 的块编辑器，配 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中段落上显示 Ask AI 弹窗，包含已输入的指令和 Polish、Make more concise、Expand、Fix grammar 等建议标签，以及 Send now 和 Add to queue 按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 渲染一份发布说明文档，包含表格、Mermaid 流程图和任务列表，左侧 AI 面板显示起始提示词"></td>
</tr>
<tr>
<td><b>对选中内容使用 Ask AI</b> — 选中任意片段即出现 <b>Ask AI</b> 标签：输入指令或选择建议，立即发送，或将多个锚定编辑排队一次性执行。同一入口存在于每个应用中。</td>
<td><b>渲染显示，纯 Markdown 保存</b> — Tiptap 块编辑器支持标题、列表、表格、图片、代码块和 Mermaid 图表，全部写回纯 <code>.md</code>，并支持完全本地的 <b>Markdown → Word</b> 导出。</td>
</tr>
</table>

### 7 · CLI — 你的编码智能体在你的机器上驱动 GenOffice

GenOffice 自带 `genoffice` 命令行和智能体 skill。安装 skill 后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 即可通过应用所用的同一套引擎，无需打开任何窗口，创建、转换、读取和编辑真正的 Office 文件。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 中显示一份由编码智能体通过 genoffice 命令行生成的八页太阳系演示文稿：画布上为封面页，左侧八个缩略图，AI 面板打开" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的八张渲染幻灯片一览：封面、探索时间线、四个关键数据、行星直径柱状图、岩质行星与巨行星对比、太阳占 99.8% 的头条数字、四颗巨行星网格和核心结论"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置中的 Integrations 页面：genoffice skill 已安装到 Claude Code，Codex 和 Cursor 旁有 Install 按钮"></td>
</tr>
<tr>
<td><b>给智能体一句提示词</b> — “制作一份关于太阳系的八页演示文稿。” 智能体读取 skill，编写风格表、大纲和每页规格，用 <code>genoffice image</code> 生成两张图片，并让 <code>genoffice slides check</code> 拒绝任何溢出或重叠的内容；随后 <code>genoffice create</code> 组装 <code>.pptx</code>，<code>slides render</code> 返回每页 PNG 供查看。</td>
<td><b>一次安装，从设置 → 集成</b> — GenOffice 列出本机检测到的编码智能体，并将 skill 写入你选择的每个智能体。也可下载 skill 的 zip 包，或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行和智能体 skill</a>。</td>
</tr>
</table>

### 8 · MCP — 同一套工具，走 Model Context Protocol

每条 `genoffice` 命令同时也是 MCP 工具。Claude Code、Claude Desktop、Cursor 及任何其他 MCP 客户端都可自行启动 `genoffice mcp`，无需安装 skill，无需打开窗口，即可获得 29 个工具和以 resources 形式提供的操作参考。应用内另有一个 HTTP 服务器，让智能体在可见的编辑器标签页中创建 Word 文档，你可实时观看。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 gen
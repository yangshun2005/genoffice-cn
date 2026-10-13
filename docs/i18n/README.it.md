<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 开源 AI Office 套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个开源且完整的 AI Office 套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件，由你和你的 AI 共同编辑，保存为相同的真实格式。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="License: Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="Latest release"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="Downloads"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub stars"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <b>Italiano</b> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是 Microsoft Office 的免费开源替代品，支持
macOS、Windows 和 Linux。它能打开并保存原生 `.docx`、`.xlsx` 和 `.pptx`
文件，可编辑 PDF、Markdown 和 HTML，并为每个文档配备 AI 智能体——不是
贴在旁边的聊天窗口，而是一个能读取文件、应用修改并精确展示改动内容的
编辑器。

- **真实格式，逐字节保留。** 只重写你修改的部分。文件其余内容逐字节
  保持不变，因此文档在 Word、Excel 和 PowerPoint 中依然正常工作。
- **可控的 AI。** 修改以修订标记和 diff 形式呈现，一键即可还原。电子表格
  获得实时公式，而非粘贴的数值。演示文稿和页面直接在画布上生成，且完全
  可编辑。
- **本地优先设计。** 文件在你的电脑上打开、编辑、保存和转换。PDF → Word /
  Excel / PowerPoint、Markdown → Word 和 HTML → Word 的转换全部在本地完成。
  只有 AI 调用会离开本机，发往你选择的提供商。
- **用你的密钥，或不用密钥。** 使用 Genspark 登录则无需任何配置，也可以
  使用你自己的 Claude、OpenAI、Gemini、DeepSeek、Kimi、
  GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty 或任何兼容
  OpenAI 的端点密钥，包括本地服务器。
- **可脚本化，面向智能体。** 应用内置 `genoffice` 命令行和面向 Claude Code、
  Codex、Cursor、Gemini CLI、GitHub
  Copilot、OpenCode 和 Windsurf 的技能，让编程智能体无需打开窗口即可在你的
  电脑上创建、转换、读取和修改真实的 Office 文件。

**下载：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情和要求见[下载](#download)部分。

## 演示

六个应用、一个 AI 面板，以及一条供编程智能体使用的命令行。每张截图都展示
macOS 上的真实应用，AI 由面板中可读的提示词驱动。

### 1 · Docs — 用可控的 AI 打开并编辑 `.docx`

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 显示一页双栏年度报告，带有全宽封面图、彩色背景的 KPI 表格、页眉和页脚，缩放 80%，AI 面板已最小化为图标"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：一份带横幅图片的公司概览；AI 精简了 Overview 段落并插入了一个新的项目符号列表章节，面板提供一键还原"></td>
</tr>
<tr>
<td><b>按 Word 的排版方式打开文件</b> — 双栏分节、全页图片、彩色背景表格、页眉和页脚，行度量与 Word 一致。样式、批注、修订、公式和手写输入均原样保留。</td>
<td><b>提出修改要求</b> — AI 读取所需的块，重写 Overview 并插入新的项目符号列表章节。每次 AI 操作都是一个可还原的快照；开启<b>修订</b>后，修改以 Word 风格的修订呈现。</td>
</tr>
</table>

### 2 · Sheets — 带实时公式和图表的 `.xlsx` 文件，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 使用 SUMIF 公式添加了一个按地区和类别统计收入的 Summary 工作表，并附柱状图，提示已应用 43 项修改并提供撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：当被问及哪个地区推动了 Q2 收入时，AI 回答欧洲并给出按类别的细分，并将所用单元格作为可点击链接引用，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td><b>构建它</b> — 从一句话开始，智能体添加一个 Summary 工作表，按地区和类别使用真正的 <code>SUMIF</code>，插入柱状图，并将 43 项修改作为单个可撤销批次应用。</td>
<td><b>询问它</b> — 关于工作簿的问题会得到回答，附带推理过程和作为可点击引用的确切单元格。幕后：自研的 Rust <code>.xlsx</code> 引擎、数据透视表、数据筛选、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资者演示文稿的延时：AI 在面板中规划叙事，幻灯片逐张出现在画布上，完成的演示文稿以最终请求收尾" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 在画布上生成的 Aurora Home 投资者演示文稿封面页，面板中显示原始的一行提示词和 AI 关于所创建内容的摘要"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的设计感结尾页，左侧是缩略图条，AI 面板总结了故事线"></td>
</tr>
<tr>
<td><b>输入一行</b> — “为 Aurora Home 创建一份 10 页的投资者演示文稿……”。GenOffice 规划故事线、查找数据，并在画布上将每张幻灯片绘制为真正的 <code>.pptx</code>。</td>
<td><b>输出完整演示文稿</b> — 十一张设计好的幻灯片，排版和图片风格一致，并有收尾的行动号召；可继续使用母版、版式、智能参考线和非破坏性裁剪进行编辑，或让面板更改样式、重写和重新排序。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，本地将 PDF 转换为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：文本编辑模式为页面上每个文本块划定边界以便就地编辑，AI 面板回答关于报告的问题并附页码引用"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 显示一份从 Helios quarterly review PDF 本地转换而来的 Word 文档，在原始 PDF 旁边的第二个标签页中打开"></td>
</tr>
<tr>
<td><b>直接在页面中编辑</b> — 文本编辑模式为每个文本块划定边界以便就地重写；内容流通过 PDFium 用原始字体重写，而非用覆盖文本的注释。向 AI 询问长篇报告的信息，即可获得带页码引用的回答。</td>
<td><b>本地转换</b> — <b>PDF Converter → PDF to Word</b> 生成可编辑的 <code>.docx</code>，在 Docs 中与原始文件并排打开，标题、统计行和段落完好无损。转换为 Excel 和 PowerPoint 同理；扫描页面通过系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — 从设计简报出发的 AI 页面和界面生成器

描述页面的用途和受众。AI 首先提出一份**设计简报**——钩子、配色、排版和
风格方向——然后基于这些 token 构建一个自包含的 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时：面板中的一次 Restyle 请求将深色 Midnight Studio 页面转换为温暖的 Solar Daybreak 版本，所有章节和文本保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，采用深色 Midnight Studio 方向，在实时预览中显示，AI 面板总结了刚创建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一个 Lumen 落地页被 AI 重新设计为温暖的 Solar Daybreak 方向：纸张背景、衬线标题和橙色点缀，所有章节和文本均保留"></td>
</tr>
<tr>
<td><b>由单个提示词生成</b> — 为 Lumen 打造醒目的 hero、功能卡片、定价和等候名单表单，采用 Midnight Studio 方向。点击任意元素更改样式，双击编辑文本，或切换到 CodeMirror 源码视图。</td>
<td><b>相同设计，全新方向</b> — 一次 <b>Restyle</b> 请求替换简报 token，页面随之调整：温暖纸张、编辑感衬线、太阳橙点缀，无需重写任何内容。全屏展示，或导出为 PDF 或原生可编辑的 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由设计师生成的个人仪表盘界面，采用温暖亚麻风格，带左侧边栏、衬线问候语和四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：关于电动汽车市场生成的数据报告，采用大报风格，带衬线报头、1730 万的主要数字和一行统计数据"></td>
</tr>
<tr>
<td><b>UI 原型</b> — “personal dashboard”起始模板将一个人物转化为可用的布局：侧边栏、问候语、可计费小时迷你图、发票和使用情况卡片，全是可交付给开发者的真实 HTML。</td>
<td><b>数据故事</b> — “data report”起始模板构建编辑感大报：衬线报头、突出数字、以细线分隔的统计行、内联 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown — 基于纯 `.md` 文件的块编辑器，带 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中的段落显示 Ask AI 弹窗，带有已输入的指令和建议标签如改进、精简、扩展和修正语法，以及立即发送和加入队列按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 显示一份发布说明文档，带表格、Mermaid 流程图和任务列表，左侧是 AI 面板的起始提示词"></td>
</tr>
<tr>
<td><b>对选区使用 Ask AI</b> — 选中任意段落即出现 <b>Ask AI</b> 标签：输入指令或选择建议，立即发送，或将多个锚定修改加入队列并一次性执行。每个应用都有相同的入口。</td>
<td><b>所见即所得，保存为纯 Markdown</b> — 标题、列表、表格、图片、代码块和 Mermaid 图表在 Tiptap 块编辑器中呈现，重写为纯 <code>.md</code>，并支持完全本地的 <b>Markdown → Word</b> 导出。</td>
</tr>
</table>

### 7 · CLI — 你的编程智能体在你的电脑上驱动 GenOffice

GenOffice 内置 `genoffice` 命令行和智能体技能。安装技能后，Claude Code、
Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 即可使用与
应用相同的引擎创建、转换、读取和修改真实的 Office 文件，无需打开窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示一份由编程智能体通过 genoffice 命令行创建的八页太阳系演示文稿：画布上的封面页、左侧八个缩略图和已打开的 AI 面板" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的八张渲染幻灯片并排显示：封面、探索历史、四个关键数字、行星直径柱状图、岩石世界与气态巨行星、太阳 99.8% 的突出数字、四颗巨行星网格和结论"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置中的集成页面：genoffice 技能已安装到 Claude Code，Codex 和 Cursor 旁边有安装按钮"></td>
</tr>
<tr>
<td><b>向智能体发一条提示词</b> — “创建一份关于太阳系的八页演示文稿。”智能体读取技能，编写样式表、大纲和每页的页面规格，用 <code>genoffice image</code> 生成两张图片，让 <code>genoffice slides check</code> 在 <code>genoffice create</code> 组装 <code>.pptx</code> 之前拒绝所有溢出或重叠的内容，并由 <code>slides render</code> 返回每页的 PNG 供检查。</td>
<td><b>一次安装，从设置 → 集成</b> — GenOffice 列出在此电脑上找到的编程智能体，并将技能写入你选择的每一个。也可以将技能下载为 zip，或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行和智能体技能</a>。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 使用相同工具

每个 `genoffice` 命令也是一个 MCP 工具。Claude Code、Claude
Desktop、Cursor 和任何其他 MCP 客户端都可以自行启动 `genoffice mcp`，无需
安装任何技能，也无需打开窗口，即可获得 29 个工具以及作为资源的操作参考。
应用内的第二个 HTTP 服务器让智能体在你观察时在可见的编辑器标签页中构建
Word 文档。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 genoffice 的 MCP 服务器构建一份关于可再生能源的八页投资者演示文稿的
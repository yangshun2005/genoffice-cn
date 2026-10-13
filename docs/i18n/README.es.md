<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice：开源 AI 办公套件，包含 Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个完整的开源 AI 办公套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件，由你和你的 AI 共同编辑，并以真实格式保存。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="许可证：Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="最新版本"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="下载量"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub Star 数"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <b>Español</b> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是 Microsoft Office 的免费开源替代品，支持 macOS、Windows 和 Linux。它可以打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown 和 HTML，并在每个文档旁放置一个 AI 智能体：不是贴在一侧的聊天框，而是一个能读取文件、执行修改并精确展示改动内容的编辑器。

- **真实格式，字节级保留。** 只重写你编辑的内容。文件中其他所有部分逐字节保留，因此文档在 Word、Excel 和 PowerPoint 中依然可用。
- **可审查的 AI。** 改动以修订标记和可一键回滚的差异形式呈现。电子表格获得实时公式，而非粘贴的数值。演示文稿和页面在画布上生成，且完全可编辑。
- **本地优先设计。** 文件在你的设备上打开、编辑、保存和转换。PDF → Word / Excel / PowerPoint、Markdown → Word 和 HTML → Word 全部在设备端运行。只有 AI 调用会离开你的设备，发送到你选择的提供商。
- **用你的密钥，或不用密钥。** 使用 Genspark 登录即可免密钥，或使用你自己的 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty 密钥，或任何兼容 OpenAI 的端点，包括本地服务器。
- **可自动化，面向智能体。** 应用内置 `genoffice` 命令行和适用于 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的 skill，编程智能体无需打开窗口即可在你的设备上创建、转换、读取和编辑真实的 Office 文件。

**获取方式：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情和要求见[下载](#download)。

## 演示

六个应用、一个 AI 面板，以及一条供编程智能体使用的命令行。每张截图都是 macOS 上的真实应用，AI 由面板中可读的提示词驱动。

### 1 · Docs — 打开并编辑 `.docx`，AI 改动可审查

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 显示一页双栏年度报告，包含全宽封面图、带底纹的 KPI 表格、页眉和页脚，缩放 80%，AI 面板已收起"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：一份带横幅图片的公司概览；AI 调整了 Overview 部分并插入了一个新的项目符号部分，面板提供一键撤销更改"></td>
</tr>
<tr>
<td><b>按 Word 排版方式打开文件</b> — 双栏分节、全出血图片、带底纹的表格、页眉和页脚，分页按 Word 的行度量计算。样式、批注、修订、公式和墨迹在往返编辑中完整保留。</td>
<td><b>提出修改要求</b> — AI 读取所需的块，重写 Overview 部分并插入新的项目符号部分。每一轮 AI 操作都是一个可回滚的快照；开启 <b>Track changes</b> 后，改动以 Word 风格的修订形式呈现。</td>
</tr>
</table>

### 2 · Sheets — 带实时公式和图表的 `.xlsx`，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 添加了一个 Summary 工作表，使用 SUMIF 公式按地区和类别统计收入，并添加了柱状图，报告已应用 43 项更改，带撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：询问第二季度哪个地区收入领先时，AI 回答欧洲并给出按类别的明细，引用所用单元格作为可点击链接，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td><b>创建</b> — 只需一句话，智能体便添加一个 Summary 工作表，包含按地区和类别的真实 <code>SUMIF</code> 公式，插入柱状图，并将 43 项更改作为单个可撤销批次应用。</td>
<td><b>提问</b> — 关于工作簿的问题会附带推理过程和所用确切单元格作答，以可点击引用形式呈现。底层：自研的 Rust <code>.xlsx</code> 引擎，支持数据透视表、切片器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资者演示文稿的延时：AI 在面板中规划叙事，幻灯片在画布上逐一出现，完成的演示文稿以最终提案收尾" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 在画布上生成的 Aurora Home 投资者演示文稿封面幻灯片，面板中显示原始的一行指令和 AI 对构建内容的总结"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的设计感结尾幻灯片，左侧是缩略图条，AI 面板总结叙事线索"></td>
</tr>
<tr>
<td><b>只需一行</b> — 「为 Aurora Home 投资者创建一份 10 页演示文稿……」。GenOffice 规划叙事线索、研究数据，并在画布上将每页幻灯片撰写为真正的 <code>.pptx</code>。</td>
<td><b>完成的演示文稿</b> — 十一页幻灯片，排版和图片风格一致，结尾有行动号召；可继续使用母版、版式、智能参考线和非破坏性裁剪进行编辑，或让面板重新设计样式、重写和重排。</td>
</tr>
</table>

### 4 · PDF — 直接编辑 PDF 文本，在设备端将 PDF 转换为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：编辑文本模式高亮页面中每个文本块的轮廓以便直接编辑，AI 面板则用页码引用回答关于报告的问题"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 显示一份从 Helios 季度回顾 PDF 本地转换而来的 Word 文档，在第二个标签页中与原始 PDF 并排打开"></td>
</tr>
<tr>
<td><b>在页面内编辑</b> — 编辑文本模式高亮每个文本块的轮廓以便直接重写；内容流通过 PDFium 使用原始字体重写，而非用注释遮盖文本。可就长篇报告向 AI 提问，获得带页码引用的回答。</td>
<td><b>在设备端转换</b> — <b>PDF Converter → PDF to Word</b> 生成可编辑的 <code>.docx</code>，在 Docs 中与原始文件并排打开，标题、统计行和段落完好无损。Excel 和 PowerPoint 目标同理；扫描页通过系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — AI 驱动的页面和界面生成器，设计简报优先

说明页面用途和受众。AI 首先提出一份**设计简报**——核心卖点、配色、排版和风格方向——然后按照这些 token 构建一个自包含的 `.html` 单文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时：面板中一次 Restyle 请求将深色的 Midnight Studio 页面转换为温暖的 Solar Daybreak 版本，同时每个部分和所有内容保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，采用 Midnight Studio 深色风格方向，在实时预览中显示，AI 面板总结刚构建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一个 Lumen 落地页被 AI 重新设计为温暖的 Solar Daybreak 风格：纸质背景、衬线标题和橙色点缀，保留所有部分和全部文本"></td>
</tr>
<tr>
<td><b>从提示词生成</b> — 为 Lumen 打造的醒目 hero、功能卡片、定价和等候名单表单，采用 Midnight Studio 风格方向。点击任意元素可重新设计样式，双击可编辑文本，或切换到 CodeMirror 代码视图。</td>
<td><b>同一设计，另一种方向</b> — 一次 <b>Restyle</b> 请求即可更改简报 token，页面随之适配：温暖纸张、编辑衬线、太阳橙点缀，无需重写任何内容。可全屏展示，或导出为 PDF 或原生可编辑的 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由设计师生成的个人面板界面，采用温暖亚麻风格，包含左侧边栏、衬线字体问候语和四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：关于电动汽车市场的数据报告，采用大报风格，包含衬线报头、1730 万的醒目数字和一行统计数据"></td>
</tr>
<tr>
<td><b>界面原型</b> — 「personal dashboard」起始模板将一个人物转化为功能性设计：左侧边栏、问候语、可计费小时迷你图、发票和利用率卡片，全部为可交付给开发者的真实 HTML。</td>
<td><b>数据故事</b> — 「data report」起始模板构建一份编辑风格报纸：衬线报头、醒目数字、以分隔线隔开的统计行、内联 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown — 基于纯 `.md` 的块编辑器，支持 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中的段落显示 Ask AI 弹出框，包含已输入的指令和 Polish、Make more concise、Expand、Fix grammar 等建议标签，以及 Send now 和 Add to queue 按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 显示一份发布说明文档，包含表格、Mermaid 流程图和任务列表，左侧是 AI 面板的初始建议"></td>
</tr>
<tr>
<td><b>对选中内容 Ask AI</b> — 选中任意段落即出现 <b>Ask AI</b> 标签：输入指令或选择建议，立即发送，或将多个锚定编辑排队后一次性执行。所有应用都有相同的入口。</td>
<td><b>渲染显示，保存为纯 Markdown</b> — 在 Tiptap 块编辑器中支持标题、列表、表格、图片、代码块和 Mermaid 图表，写回为纯 <code>.md</code>，并提供完全本地的 <b>Markdown → Word</b> 导出。</td>
</tr>
</table>

### 7 · CLI — 你的编程智能体在你的设备上操作 GenOffice

GenOffice 内置 `genoffice` 命令行和智能体 skill。安装 skill 后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 即可使用与应用相同的引擎创建、转换、读取和编辑真实的 Office 文件，无需打开窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示一份由编程智能体通过 genoffice 命令行构建的关于太阳系的八页演示文稿：画布上的封面幻灯片、左侧八个缩略图，AI 面板已打开" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的八页幻灯片并排展示：封面、探索时间线、四个关键数字、行星直径柱状图、岩石世界与气态巨行星、太阳 99.8% 的醒目数字、四颗巨行星网格和结论"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置，集成页面：genoffice skill 已安装到 Claude Code，Codex 和 Cursor 旁有安装按钮"></td>
</tr>
<tr>
<td><b>向智能体发一条提示词</b> — 「创建一份关于太阳系的八页演示文稿」。智能体读取 skill，编写样式表、大纲和每页幻灯片的规格，用 <code>genoffice image</code> 生成两张图片，让 <code>genoffice slides check</code> 在 <code>genoffice create</code> 组装 <code>.pptx</code> 之前拒绝所有溢出或重叠的内容，再由 <code>slides render</code> 返回每页幻灯片的 PNG 供审查。</td>
<td><b>从设置 → 集成一次性安装</b> — GenOffice 显示在此设备上找到的编程智能体，并将 skill 写入你选择的每一个。也可将 skill 下载为 zip，或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行和智能体 skill</a>。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 使用相同工具

每个 `genoffice` 命令也是一个 MCP 工具。Claude Code、Claude Desktop、Cursor 和任何其他 MCP 客户端都可以自行启动 `genoffice mcp`，无需安装任何 skill 或打开窗口，即可获得 29 个工具以及作为资源的操作参考。应用内的第二个 HTTP 服务器让智能体可以在你眼前可见的编辑器标签页中构建 Word 文档。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 genoffice MCP 服务器构建一份关于可再生能源的八页投资演示文稿的延时：搜索数据和照片，用 media
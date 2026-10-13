<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 开源 AI Office 套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球功能最全的开源 AI Office 套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件，由你和你的 AI 共同编辑，并以原始格式保存回去。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="License: Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="Latest release"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="Downloads"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub stars"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <b>Bahasa Indonesia</b> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>网站</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是面向 macOS、Windows 和 Linux 的免费开源 Microsoft Office 替代品。它能打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown 和 HTML，并在每个文档旁边配备 AI 智能体——不是贴在屏幕边上的聊天框，而是能读取文件、做出修改、并精确指出改了哪里的编辑器。

- **原生格式，字节保留。** 只有你编辑的部分会被重写。文件其余部分逐字节保持不变，文档在 Word、Excel 和 PowerPoint 中照常可用。
- **可审查的 AI。** 修改以修订标记和 diff 形式记录，支持一键回滚。电子表格得到的是实时公式，而非粘贴的数值。演示文稿和页面直接在画布上生成，且完全可编辑。
- **设计上本地化。** 文件在你自己的设备上打开、编辑、保存和转换。PDF → Word / Excel / PowerPoint、Markdown → Word、HTML → Word 的转换全部在设备上运行。只有 AI 调用会离开设备，发往你选择的提供商。
- **用你自己的 API 密钥，或完全不用密钥。** 用 Genspark 登录即可跳过 API 密钥，或使用你自己的密钥接入 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty，或任何兼容 OpenAI 的端点，包括本地服务器。
- **可脚本化，面向智能体。** 应用自带 `genoffice` 命令行和面向 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的技能，编码智能体无需打开任何窗口，就能在你机器上创建、转换、读取和编辑原生 Office 文件。

**在此下载：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情和要求见 [下载](#download) 部分。

## 演示

六个应用，一个 AI 面板，以及一条供编码智能体使用的命令行。每张截图都是 macOS 上的原生应用，AI 由面板中可读的提示词驱动。

### 1 · Docs — 打开并编辑 `.docx`，AI 修改可审查

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 显示一页双栏年度报告，含整页宽封面图、带背景色的 KPI 表格、页眉页脚，缩放 80%，AI 面板已折叠"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：带横幅图片的公司摘要；AI 精简 Overview 部分并插入新的项目符号部分，面板提供一键回滚"></td>
</tr>
<tr>
<td><b>按 Word 版式打开文件</b> — 双栏部分、整页出血图片、带背景色的表格、页眉页脚、基于 Word 行度量的页码。样式、批注、修订、公式和手写（ink）在重新打开时保持完整。</td>
<td><b>提出你想要的修改</b> — AI 读取所需区块，重写 Overview 部分，并插入新的项目符号部分。每次 AI 交互都是一个可回滚的快照；开启 <b>Track changes</b> 后，修改以 Word 风格修订呈现。</td>
</tr>
</table>

### 2 · Sheets — 带实时公式和图表的 `.xlsx`，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 使用 SUMIF 公式添加按地区和类别统计收入的 Summary 工作表，并添加柱状图，报告已应用 43 项修改，带 Undo 按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：被问及哪个地区在 Q2 收入领先时，AI 回答欧洲并附类别明细，引用所用单元格作为可点击链接，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td><b>构建工作表</b> — 从一句话开始，智能体添加带真实按地区和类别 <code>SUMIF</code> 公式的 Summary 工作表，插入柱状图，并将 43 项修改作为一个可整体撤销的批次应用。</td>
<td><b>直接提问</b> — 关于工作簿的问题得到带推理过程的完整回答，所用单元格以可点击引用呈现。底层：自研 Rust `.xlsx` 引擎、数据透视表、切片器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 制作 Aurora Home 投资人演示文稿的延时：AI 在面板中构建故事线，幻灯片逐一出现在画布上，完成的演示文稿以收尾诉求结束" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 在画布上生成的 Aurora Home 投资人演示文稿封面幻灯片，面板中显示原始单行提示词和 AI 对其所创建内容的摘要"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿中已设计好的收尾幻灯片，左侧为缩略图条，AI 面板总结其故事线"></td>
</tr>
<tr>
<td><b>输入一行提示词</b> — “为 Aurora Home 制作一份 10 页投资人演示文稿……”。GenOffice 设计故事线，研究数据，并将每张幻灯片直接排布到画布上，生成真正的 `.pptx`。</td>
<td><b>输出完成的演示文稿</b> — 十一张设计好的幻灯片，排版、视觉风格一致，并有收尾行动号召；继续用母版、版式、智能参考线和非破坏性图片裁剪编辑，或让面板调整风格、重写和重新排序。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，设备上转换 PDF 到 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：编辑文本模式标记页面上每个文本块以便就地编辑，AI 面板回答关于报告的问题并附页码引用"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 显示从 PDF Helios quarterly review 本地转换而来的 Word 文档，在第二个标签页中与原始 PDF 并排打开"></td>
</tr>
<tr>
<td><b>直接在页面内编辑</b> — 编辑文本模式标记每个文本块以便就地重新输入；内容流通过 PDFium 用原始字体重写，而非叠加批注。向 AI 询问长报告，得到带页码引用的回答。</td>
<td><b>设备上转换</b> — <b>PDF Converter → PDF to Word</b> 生成可编辑的 `.docx`，在 Docs 中与源文件并排打开，标题、统计行和段落保持完整。Excel 和 PowerPoint 目标同理；扫描页通过系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — 基于 AI 的页面和 UI 构建器，从设计简报开始

说明页面用途和受众。AI 会先提出 **设计简报**——钩子、配色、排版和视觉风格方向——然后基于这些 token 构建单个自包含 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时：面板中一次 Restyle 请求将深色 Midnight Studio 页面变为温暖的 Solar Daybreak 版本，同时每个部分和所有内容保持原位" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，采用深色 Midnight Studio 风格方向，在实时预览中显示，AI 面板总结其刚创建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一 Lumen 落地页，AI 将其风格改为温暖的 Solar Daybreak 方向：纸感背景、衬线标题和橙色点缀，每个部分和全部文本均保留"></td>
</tr>
<tr>
<td><b>从一行提示词生成</b> — Lumen 的大胆 hero、功能卡片、定价和候补名单表单，以 Midnight Studio 方向构建。点击任意元素调整样式，双击编辑文本，或切换到 CodeMirror 源码视图。</td>
<td><b>同一设计，全新方向</b> — 一次 <b>Restyle</b> 请求替换简报 token，页面随之调整：温暖纸感背景、编辑风衬线、太阳橙点缀，无任何内容被重写。全屏模式演示，或导出为 PDF 或可编辑的原生 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由设计师生成的个人仪表盘 UI，采用温暖亚麻风格，带左侧栏、衬线问候语和四张指标卡"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：以宽幅报纸风格生成的电动汽车市场数据报告，带衬线报头、1730 万主要数字和统计行"></td>
</tr>
<tr>
<td><b>UI 原型</b> — “personal dashboard” 起始模板将一个人物设定转化为真正可用的布局：左侧栏、问候语、计费小时迷你图、发票和利用率卡片，全部是可交给开发者的原生 HTML。</td>
<td><b>数据故事</b> — “data report” 起始模板构建编辑风宽幅报纸：衬线报头、一个主要数字、分隔线统计行、内联 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown — 基于普通 `.md` 的块编辑器，带 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中段落显示 Ask AI 弹窗，含已输入指令和建议标签如 Polish、Make more concise、Expand 和 Fix grammar，以及 Send now 和 Add to queue 按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 渲染含表格、Mermaid 流程图和任务列表的发布说明文档，左侧为 AI 面板起始提示词"></td>
</tr>
<tr>
<td><b>对选中内容 Ask AI</b> — 选中任意文本，<b>Ask AI</b> 标签出现：输入指令或选择建议，立即发送，或收集多个锚定编辑并一次批量运行。每个应用都有相同入口。</td>
<td><b>渲染，保存为普通 Markdown</b> — Tiptap 块编辑器中的标题、列表、表格、图片、代码块和 Mermaid 图表，写回为普通 `.md`，<b>Markdown → Word</b> 导出完全本地运行。</td>
</tr>
</table>

### 7 · CLI — 你的编码智能体在你机器上运行 GenOffice

GenOffice 自带 `genoffice` 命令行和一个智能体技能。安装该技能后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 就能通过与应用相同的引擎创建、转换、读取和编辑原生 Office 文件，无需打开任何窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示编码智能体通过 genoffice 命令行制作的八页太阳系演示文稿：画布上为封面幻灯片，左侧八个缩略图，AI 面板打开" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿渲染出的八张幻灯片并排：封面、探索时间线、四个关键数字、行星直径柱状图、岩石行星与气态巨行星、太阳 99.8% 主要数字、四颗巨行星网格和结论"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice Settings 的 Integrations 页面：genoffice 技能已安装在 Claude Code 中，Codex 和 Cursor 旁有 Install 按钮"></td>
</tr>
<tr>
<td><b>向你的智能体发一条提示词</b> — “制作一份关于太阳系的八页演示文稿。”智能体读取技能，编写样式表、大纲和每页一份规格，用 <code>genoffice image</code> 生成两张图片，让 <code>genoffice slides check</code> 拒绝任何溢出或重叠的内容，然后 <code>genoffice create</code> 组装 <code>.pptx</code>，<code>slides render</code> 返回每页一张 PNG 供查看。</td>
<td><b>从设置 → 集成一次安装</b> — GenOffice 显示在本机发现的编码智能体，并将技能写入你选择的每个智能体。或下载技能 zip，或运行 <code>npx skills add genspark-ai/genoffice</code>。完整命令和工作流见 <a href="#command-line-and-agent-skill">命令行和智能体技能</a>。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 使用相同工具

每条 `genoffice` 命令同时也是 MCP 工具。Claude Code、Claude Desktop、Cursor 和其他 MCP 客户端可以自行运行 `genoffice mcp`，无需安装技能，也无需打开窗口，即可获得 29 个工具以及作为资源的 op 参考。应用内的第二个 HTTP 服务器让智能体在你眼前可见的编辑器标签页中构建 Word 文档。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 genoffice MCP 服务器构建八页可再生能源投资人简报的延时录屏：搜索数据和照片，用 media 检查每张候选照片，deck_start 写入样式表和大纲，deck_page
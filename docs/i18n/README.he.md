<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 基于 AI 的开源办公套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center" dir="rtl">GenOffice</h1>

<p align="center" dir="rtl"><b>全球首个基于 AI 的开源全功能办公套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件，由您和您的 AI 共同编辑，并以原始格式保存回去。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="License: Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="Latest release"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="Downloads"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub stars"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <b>עברית</b></p>

<p align="center" dir="rtl">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是 Microsoft Office 的免费开源替代品，支持 macOS、Windows 和 Linux。它能打开并保存原生的 `.docx`、`.xlsx` 和 `.pptx` 文件，支持编辑 PDF、Markdown 和 HTML，并在每个文档旁配备 AI 智能体——不是贴在旁边的聊天框，而是能读取文件、执行修改、并精确展示改动内容的编辑器。

- **真实格式，字节级精确保存。** 只有您编辑的部分会被重写。文件中其余内容逐字节原样保留，因此文档在 Word、Excel 和 PowerPoint 中依然可用。
- **可审查的 AI。** 修改以修订模式（tracked changes）和 diff 形式呈现，一键即可还原。电子表格获得的是实时公式，而非粘贴的数值。演示文稿和页面直接在画布上生成，且完全可编辑。
- **天生本地化。** 文件的打开、编辑、保存和转换都在您的电脑上完成。PDF → Word / Excel / PowerPoint、Markdown → Word 和 HTML → Word 的转换全部在设备本地运行。只有 AI 调用会离开设备，发送到您选择的服务商。
- **用您的密钥，或不用密钥。** 使用 Genspark 登录即可跳过密钥配置，或自带密钥用于 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty，或任何兼容 OpenAI 的端点，包括本地服务器。
- **可脚本化，为智能体而生。** 应用自带 `genoffice` 命令行和适用于 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的 skill，让代码智能体无需打开窗口即可在您的电脑上创建、转换、读取和编辑真实的 Office 文件。

**下载：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）—
详情和要求见[下载](#download)部分。

## 演示

六个应用，一个 AI 面板，以及为您的代码智能体准备的一条命令行。每张截图都来自 macOS 上的真实应用，AI 由面板中可读的提示词驱动。

### 1 · Docs — 打开并编辑 `.docx`，AI 可审查

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 展示一份双栏年度报告页面，含全宽封面图、带底纹的 KPI 表格、页眉页脚，以 80% 缩放显示，AI 面板已折叠"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：带横幅图片的公司概览；AI 精炼了 Overview 段落并新增了一个带项目符号的段落，面板提供一键还原"></td>
</tr>
<tr>
<td dir="rtl"><b>完全按 Word 的排版打开文件</b> — 双栏分节、延伸到页边距的图片、带底纹的表格、页眉页脚，以及基于 Word 行度量（line metrics）的页码。样式、批注、修订跟踪、公式和手写标注都能无损往返。</td>
<td dir="rtl"><b>提出修改要求</b> — AI 读取所需的块，重写 Overview 段落并新增一个带项目符号的段落。每次 AI 交互都是可还原的快照；当<b>修订跟踪</b>开启时，修改以 Word 风格的修订形式呈现。</td>
</tr>
</table>

### 2 · Sheets — 带实时公式和图表的 `.xlsx`，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 新增了一个 Summary 工作表，使用 SUMIF 公式按地区和类别统计收入，并添加了柱状图，报告已应用 43 处修改，带撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：在回答第二季度哪个地区收入领先时，AI 回答欧洲并附类别明细，以可点击链接形式引用所用单元格，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td dir="rtl"><b>构建它</b> — 一句话，智能体就新增一个 Summary 工作表，按地区和类别使用真实的 <code>SUMIF</code> 公式，添加柱状图，并将 43 处修改作为一批可撤销的变更应用。</td>
<td dir="rtl"><b>询问它</b> — 关于工作簿的问题会得到答案，附带推理逻辑和所用精确单元格，以可点击引用形式呈现。底层：用 Rust 编写的内部 `.xlsx` 引擎，支持数据透视表、切片器（slicers）、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资者演示文稿的延时摄影：AI 在面板中规划故事线，幻灯片逐一出现在画布上，完成的演示文稿以 closing ask 收尾" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 生成的 Aurora Home 投资者演示文稿封面幻灯片，位于画布上，附一行原始提示词和面板中 AI 对已构建内容的总结"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的设计感结尾幻灯片，左侧是缩略图条，AI 面板总结故事线"></td>
</tr>
<tr>
<td dir="rtl"><b>输入一行</b> — “为 Aurora Home 创建一份 10 页投资者演示文稿……”。GenOffice 规划故事线，研究数据，并直接在画布上生成每一页幻灯片，作为真实的 <code>.pptx</code> 文件。</td>
<td dir="rtl"><b>输出完整演示文稿</b> — 十一页设计精美的幻灯片，排版和图片风格一致，结尾有行动号召；可继续使用母版（masters）、版式、智能参考线和无损图片裁剪进行编辑，或让面板重新设计、重写和重排。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，并在设备上转换 PDF 为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：'编辑文本'模式用轮廓标出每个文本块以便就地编辑，同时 AI 面板回答关于报告的问题并引用页码"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 展示一份从 Helios 季度总结 PDF 本地转换而来的 Word 文档，在第二个标签页中与原始 PDF 并排打开"></td>
</tr>
<tr>
<td dir="rtl"><b>在页面内编辑</b> — “编辑文本”模式用轮廓标出每个文本块以便就地重新输入；内容流使用 PDFium 结合原始字体重写，而非覆盖注释。向 AI 询问长报告，获得带页码引用的答案。</td>
<td dir="rtl"><b>在设备上转换</b> — <b>PDF Converter → PDF to Word</b> 生成可编辑的 <code>.docx</code> 文件，与原始文件并排在 Docs 中打开，保留标题、数据行和完整段落。Excel 和 PowerPoint 目标同理；扫描页面通过系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — 基于 AI 的页面和界面构建器，从设计简报开始

描述页面的用途和受众。AI 先提出**设计简报**（design brief）——开场句、配色方案、排版和风格方向——然后据此构建一个独立的 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时摄影：面板中一次 Restyle 请求将 Midnight Studio 的深色页面变为 Solar Daybreak 的暖色版本，所有区块和内容保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，采用 Midnight Studio 深色设计方向，在实时预览中显示，AI 面板总结所构建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一个 Lumen 落地页，由 AI 重新设计为 Solar Daybreak 暖色方向：纸色背景、衬线标题和橙色点缀，保留所有区块和文案"></td>
</tr>
<tr>
<td dir="rtl"><b>一句话生成</b> — 为 Lumen 打造的醒目 hero 区、功能卡片、定价和等候名单注册表单，采用 Midnight Studio 方向构建。点击任意元素重新设计，双击编辑文本，或切换到 CodeMirror 源代码视图。</td>
<td dir="rtl"><b>同一设计，全新方向</b> — 一次 <b>Restyle</b> 请求替换简报参数，页面随之调整：暖色纸张、报刊衬线字体、阳光橙点缀，无需重写任何内容。可全屏展示，或导出为 PDF 或可编辑的真实 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为设计领域自由职业者生成的个人仪表盘界面，采用暖色 'Linen' 风格，左侧导航栏、衬线字体问候语和四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：电动汽车（EV）市场数据报告，采用 'Broadsheet' 报刊风格，衬线大标题、1730 万的头条数据和统计行"></td>
</tr>
<tr>
<td dir="rtl"><b>从 mockup 到界面</b> — “个人仪表盘”起点将人物画像转化为可用的布局：导航栏、问候语、计费小时 sparkline、发票和利用率卡片——全是可交给开发者的真实 HTML。</td>
<td dir="rtl"><b>数据叙事</b> — “数据报告”起点构建报刊风格的大幅面页面：衬线大标题、一个头条数据、分隔线统计行、内嵌 SVG 图表和方法论注释。</td>
</tr>
</table>

### 6 · Markdown — 基于普通 `.md` 文件的块编辑器，带 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中的段落显示 Ask AI 弹出框，含已输入的提示词和建议芯片如 Polish、Make more concise、Expand 和 Fix grammar，以及 Send now 和 Add to queue 按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 展示一份发布说明文档，含表格、Mermaid 流程图和任务列表，左侧是 AI 面板的起始提示词"></td>
</tr>
<tr>
<td dir="rtl"><b>对选中片段询问 AI</b> — 选中任意片段，<b>Ask AI</b> 芯片就会出现：输入提示词或选择建议，立即发送，或将多个锚定修改排队一次性执行。每个应用都有相同的入口。</td>
<td dir="rtl"><b>可视化呈现，保存为普通 Markdown</b> — 基于 Tiptap 的块编辑器中支持标题、列表、表格、图片、代码块和 Mermaid 图表，写回为普通 <code>.md</code> 文件，Markdown → Word 导出完全本地运行。</td>
</tr>
</table>

### 7 · CLI — 您的代码智能体在您的电脑上驱动 GenOffice

GenOffice 自带 `genoffice` 命令行和智能体 skill。安装 skill 后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 即可通过驱动应用的同一批引擎创建、转换、读取和编辑真实的 Office 文件，无需打开窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 展示一份由代码智能体通过 genoffice 命令行构建的八页太阳系演示文稿：画布上的封面幻灯片、左侧八个缩略图和打开的 AI 面板" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="这份太阳系演示文稿的八页渲染幻灯片并排展示：封面、探索时间线、四个关键数字、行星直径柱状图、岩石世界对巨行星、太阳 99.8% 的醒目数字、四颗巨行星网格和结论"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置，Integrations 页面：genoffice skill 已安装在 Claude Code 中，Codex 和 Cursor 旁有 Install 按钮"></td>
</tr>
<tr>
<td dir="rtl"><b>给智能体一句话</b> — “创建一份关于太阳系的八页演示文稿。”智能体读取 skill，编写样式表，为每页幻灯片规划大纲和规格，用 <code>genoffice image</code> 生成两张图片，让 <code>genoffice slides check</code> 拒绝任何溢出或重叠的内容，然后 <code>genoffice create</code> 组装 <code>.pptx</code>，<code>slides render</code> 返回每页幻灯片的 PNG 供查看。</td>
<td dir="rtl"><b>一次安装，从设置 → 集成</b> — GenOffice 显示在这台电脑上找到的代码智能体，并将 skill 写入您选择的每一个。或下载 skill 的 zip 包，或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行和智能体 skill</a>。</td>
</tr>
</table>

### 8 · MCP
<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice – 开源 AI 办公套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个功能完整的开源 AI 办公套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件，由你和你的 AI 共同编辑，以原生格式保存。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="许可证：Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="最新版本"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="下载量"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub 星标"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <b>Deutsch</b> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是 Microsoft Office 的免费开源替代品，支持 macOS、Windows 和
Linux。它能打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、
Markdown 和 HTML，并为每个文档配备一个 AI 智能体——不是外挂的聊天框，
而是一个能读取文件、执行修改、并精确展示改动内容的编辑器。

- **原生格式，字节保留。** 只重写你编辑的部分，文件中其余内容逐字节
  保留，确保文档在 Word、Excel 和 PowerPoint 中继续正常工作。
- **可审查的 AI。** 改动以修订标记和差异形式呈现，一键即可撤销。表格
  获得真实公式而非粘贴的数值。演示文稿和页面直接在画布上生成，完全
  可编辑。
- **从底层本地化。** 文件在你的电脑上打开、编辑、保存和转换。PDF → Word /
  Excel / PowerPoint、Markdown → Word 和 HTML → Word 全部在本地运行。
  只有 AI 调用会离开电脑——发送给你选择的提供商。
- **用你的密钥，或不用密钥。** 使用 Genspark 登录无需密钥，或自带密钥
  接入 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、
  MiniMax、Grok、Mistral、OpenRouter、Requesty 或任何 OpenAI 兼容端点——
  也支持本地服务器。
- **可脚本化，面向智能体。** 应用自带 `genoffice` 命令行和适用于
  Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和
  Windsurf 的 Skill，让编码智能体无需打开窗口即可在你的电脑上创建、
  转换、读取和编辑真实的 Office 文件。

**快速开始：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详细信息和系统要求见[下载](#download)。

## 演示

六个应用、一个 AI 面板，以及一条供编码智能体使用的命令行。
每张截图都展示 macOS 上的真实应用，AI 由面板中可读的提示词驱动。

### 1 · Docs – 打开并编辑 `.docx`，AI 改动可审查

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 展示一个双栏商业报告页面，包含全宽标题图片、带底纹的 KPI 表格、页眉页脚，80% 缩放，AI 面板已折叠"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：一份带横幅图片的公司概览；AI 精简了概览并新增了一个项目符号章节，面板提供一键撤销"></td>
</tr>
<tr>
<td><b>按 Word 的排版方式打开文件</b>——双栏分节、无边框图片、带底纹表格、页眉页脚、按 Word 行度量分页。样式、批注、修订标记、公式和墨迹输入在往返编辑后保持不变。</td>
<td><b>提出修改要求</b>——AI 读取所需区块，重写概览并新增一个项目符号章节。每次 AI 操作都是一个快照，可随时回滚；启用<b>修订标记</b>后，编辑以 Word 风格的修订形式呈现。</td>
</tr>
</table>

### 2 · Sheets – `.xlsx` 使用真实公式和图表，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 新增了一个按地区和类别汇总的 Summary 工作表，使用 SUMIF 公式和柱状图，并报告已应用 43 项更改，带撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：当被问及哪个地区的 Q2 营收领先时，AI 回答为欧洲并附类别明细，将所用单元格作为证据链接，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td><b>构建它</b>——仅凭一句话，智能体就新增了一个 Summary 工作表，按地区和类别使用真实的 <code>SUMIF</code>，插入柱状图，并将 43 项更改作为一次可撤销的操作应用。</td>
<td><b>询问它</b>——关于工作簿的问题会附带推理过程和实际使用的单元格作为可点击证据。底层是自研的 Rust <code>.xlsx</code> 引擎，支持数据透视表、切片器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides – 从提示词到 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 创建 Aurora Home 投资者演示文稿的延时摄影：AI 在面板中规划故事线，幻灯片依次出现在画布上，完成的演示文稿以最终诉求收尾" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 生成的 Aurora Home 投资者演示文稿的标题幻灯片显示在画布上，面板中显示原始的一行提示词和 AI 创建内容的摘要"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的设计精美的结尾幻灯片，左侧是缩略图栏，AI 面板总结了故事线"></td>
</tr>
<tr>
<td><b>输入一行</b>——“为 Aurora Home 创建一份 10 页投资者演示文稿……”。GenOffice 规划故事线、研究数据，并直接在画布上设计每一页为真实的 <code>.pptx</code>。</td>
<td><b>输出完整演示文稿</b>——十一页设计精美的幻灯片，排版统一、视觉语言一致，并以行动号召收尾；可用母版、版式、智能参考线和无损裁剪继续编辑，或让面板重新设计样式、重写和重新排序。</td>
</tr>
</table>

### 4 · PDF – 直接编辑 PDF 文本，本地将 PDF 转换为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：文本编辑模式为页面上的每个文本块加框以便直接编辑，AI 面板回答关于报告的问题并附页码引用"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 展示一份从 Helios 季度报告 PDF 本地转换而来的 Word 文档，在第二个标签页中与原始 PDF 并排打开"></td>
</tr>
<tr>
<td><b>直接在页面上编辑</b>——文本编辑模式为每个文本块加框以便直接重新输入；内容流通过 PDFium 使用原始字体重写，而非覆盖注释。向 AI 询问长篇报告，获得带页码引用的回答。</td>
<td><b>本地转换</b>——<b>PDF 转换器 → PDF 转 Word</b> 生成可编辑的 <code>.docx</code>，在 Docs 中与源文件并排打开，标题、指标行和段落完好无损。Excel 和 PowerPoint 目标同理；扫描页面通过系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML – AI 页面和 UI 构建器，先出设计简报

说明页面的用途和受众。AI 首先提出一份**设计简报**——主题、配色方案、
排版和风格方向——然后按此规范构建一个独立的 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时摄影：面板中的一次 Restyle 请求将深色 Midnight Studio 页面转变为温暖的 Solar Daybreak 版本，同时每个章节和所有文本保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，采用深色 Midnight Studio 风格，在实时预览中显示，AI 面板总结了刚创建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一个 Lumen 落地页，由 AI 重新设计为温暖的 Solar Daybreak 风格：纸质背景、衬线标题和橙色点缀，每个章节和所有文本保持不变"></td>
</tr>
<tr>
<td><b>从提示词生成</b>——为 Lumen 打造醒目的主视觉区、功能卡片、定价和等候名单表单，采用 Midnight Studio 风格。点击任意元素重新设计样式，双击编辑文本，或切换到 CodeMirror 源码视图。</td>
<td><b>同一设计，新方向</b>——一次 <b>Restyle</b> 请求替换简报中的规范，页面随之改变：温暖的纸张、编辑风格的衬线字体、太阳橙点缀，无需重写任何内容。可全屏展示，或导出为 PDF 或原生可编辑的 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由职业设计师生成的个人仪表盘 UI，采用温暖的亚麻风格，包含左侧栏、衬线字体问候语和四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：生成的大报风格电动汽车市场数据报告，包含衬线标题、1730 万的标题数字和指标行"></td>
</tr>
<tr>
<td><b>UI 原型</b>——“个人仪表盘”模板将人物画像转化为可用的布局：左侧栏、问候语、可计费小时迷你图、发票和利用率卡片——全部是真实 HTML，可直接交给开发者。</td>
<td><b>数据故事</b>——“数据报告”模板构建编辑风格的大报：衬线标题、标题数字、线条分隔的指标行、内嵌 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown – 纯 `.md` 的块编辑器，支持 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：在选中的段落上出现 Ask AI 弹出框，包含已输入的指令和建议标签如“Polish”“Make more concise”“Expand”和“Fix grammar”，以及“Send now”和“Add to queue”按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 渲染一份包含表格、Mermaid 流程图和任务列表的发布说明文档，左侧是 AI 面板的启动提示词"></td>
</tr>
<tr>
<td><b>对选中内容 Ask AI</b>——选中任意文本，出现 <b>Ask AI</b> 标签：输入指令或选择建议，立即发送，或将多个锚定更改排队一次性执行。每个应用都有相同的入口。</td>
<td><b>渲染显示，保存为纯 Markdown</b>——Tiptap 块编辑器中的标题、列表、表格、图片、代码块和 Mermaid 图表，写回为纯 <code>.md</code>，并支持完全本地的 Markdown → Word 导出。</td>
</tr>
</table>

### 7 · CLI – 你的编码智能体在你的电脑上操控 GenOffice

GenOffice 自带 `genoffice` 命令行和智能体 Skill。
安装 Skill 后，Claude Code、Codex、Cursor、Gemini CLI、GitHub
Copilot、OpenCode 或 Windsurf 可以通过与应用相同的引擎创建、转换、
读取和编辑真实的 Office 文件，无需打开窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 展示一份由编码智能体通过 genoffice 命令行创建的八页太阳系演示文稿：画布上的标题幻灯片、左侧八个缩略图和已打开的 AI 面板" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的八页渲染幻灯片并排展示：标题、探索时间线、四项指标、行星直径柱状图、岩石行星与巨行星、太阳占 99.8% 的主视觉数字、四颗巨行星网格和核心要点"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置中的集成页面：genoffice Skill 已安装到 Claude Code，Codex 和 Cursor 旁边有安装按钮"></td>
</tr>
<tr>
<td><b>向智能体发送一条提示词</b>——“创建一份关于太阳系的八页演示文稿。”智能体读取 Skill，编写样式表、大纲和每页的页面规范，用 <code>genoffice image</code> 生成两张照片，让 <code>genoffice slides check</code> 拒绝任何溢出或重叠的内容，然后 <code>genoffice create</code> 组装 <code>.pptx</code>，<code>slides render</code> 返回每页的 PNG 供查看。</td>
<td><b>安装一次，在设置 → 集成中</b>——GenOffice 列出在此电脑上找到的编码智能体，并将 Skill 写入你选择的每一个。也可下载 Skill 的 Zip 包或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行和智能体 Skill</a>。</td>
</tr>
</table>

### 8 · MCP – 通过 Model Context Protocol 使用相同工具

每个 `genoffice` 命令也是一个 MCP 工具。Claude Code、Claude Desktop、
Cursor 和任何其他 MCP 客户端都可以自行启动 `genoffice mcp`，无需安装
Skill，也无需打开窗口，即可获得 29 个工具以及作为资源的 Op 参考。应用
中的第二个 HTTP 服务器让智能体在可见的编辑器标签页中构建 Word 文档，
你可以实时观看。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 genoffice MCP 服务器构建一份八页可再生能源投资者演示文稿的延时摄影：搜索插图和照片，用 media 检查每个候选图片，deck_start 编写样式表和大纲，deck_page 逐
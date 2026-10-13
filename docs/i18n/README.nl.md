<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 开源 AI 办公套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个全功能开源 AI 办公套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件，由你和 AI 共同编辑，以真实格式保存。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="许可证：Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="最新发布版本"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="下载量"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub 星标"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <b>Nederlands</b> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是面向 macOS、Windows 和 Linux 的免费开源 Microsoft Office 替代品。它能打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown 和 HTML，并为每个文档配备一个 AI 智能体——不是旁边贴一个聊天小窗口，而是一个能读取文件、执行修改并精确展示改动内容的编辑器。

- **真实格式，字节保留。** 只重写你编辑的部分。文件中其余内容逐字节保留，文档在 Word、Excel 和 PowerPoint 中照常使用。
- **可控的 AI。** 修改以修订标记和 diff 形式呈现，一键撤销。电子表格使用实时公式，而非粘贴的数值。演示文稿和页面在画布上生成，完全可编辑。
- **本地优先设计。** 文件在你的机器上打开、编辑、保存和转换。PDF → Word / Excel / PowerPoint、Markdown → Word 和 HTML → Word 全部在设备端运行。只有 AI 调用会离开本机，发送到你选择的提供商。
- **用自己的密钥，或不用密钥。** 用 Genspark 登录即可开箱即用，或使用自己的密钥接入 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty，或任何 OpenAI 兼容端点，包括本地服务器。
- **可脚本化，面向智能体。** 应用附带 `genoffice` 命令行和适用于 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的 skill，让编程智能体无需打开窗口即可在本机创建、转换、读取和编辑真实的 Office 文件。

**在此获取：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情和要求见[下载](#download)。

## 演示

六个应用、一个 AI 面板，以及面向编程智能体的命令行。每张截图都展示 macOS 上的真实应用，AI 由面板中可见的提示词驱动。

### 1 · Docs — 打开并编辑 `.docx`，AI 可控

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 展示年报页面，双栏布局，全宽封面图，带底纹的 KPI 表格，页眉页脚，80% 缩放，AI 面板已折叠"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：公司概览带横幅图片；AI 精简了 Overview 并新增了项目符号章节，面板提供一键撤销"></td>
</tr>
<tr>
<td><b>按 Word 的排版精确打开文件</b> — 双栏分节、满幅图片、带底纹的表格、页眉页脚、基于 Word 行度量的分页。样式、批注、修订、比较和墨迹原样保留。</td>
<td><b>提出修改要求</b> — AI 读取所需区块，重写 Overview 并新增项目符号章节。每次 AI 操作都是一个可撤销的快照；启用 <b>Track changes</b> 后，修改以 Word 风格的修订呈现。</td>
</tr>
</table>

### 2 · Sheets — `.xlsx` 使用实时公式和图表，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 新增了 Summary 工作表，通过 SUMIF 公式按地区和类别汇总收入，并添加了柱状图，报告 43 项已应用修改，带撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：询问 Q2 哪个地区收入领先，AI 回答欧洲并给出按类别的明细，以链接形式引用所用单元格，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td><b>构建</b> — 一句话即可让智能体新增 Summary 工作表，包含按地区和类别的真实 <code>SUMIF</code> 公式，插入柱状图，并将 43 项修改作为一批应用，可一次性撤销。</td>
<td><b>提问</b> — 关于工作簿的问题会返回推理过程和精确单元格的可点击引用。底层：自研 Rust <code>.xlsx</code> 引擎，支持数据透视表、切片器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资者演示文稿的延时：AI 在面板中规划叙事，幻灯片逐一出现在画布上，完成的演示文稿以结束语收尾" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 生成的 Aurora Home 投资者演示文稿的首页在画布上，面板中显示原始的一行提示词和 AI 对构建内容的总结"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的设计感尾页，左侧缩略图条和 AI 面板总结叙事线"></td>
</tr>
<tr>
<td><b>一行输入</b> — "Create a 10-slide investor pitch deck for Aurora Home…"。GenOffice 确定叙事线，查找数据，并将每页作为真实的 <code>.pptx</code> 放到画布上。</td>
<td><b>成品演示文稿</b> — 十一页设计幻灯片，排版、图像和结尾行动号召一致；可继续用母版、版式、智能参考线和无损裁剪编辑，或让面板调整样式、文本和顺序。</td>
</tr>
</table>

### 4 · PDF — 直接在页面上编辑 PDF 文本，在设备端将 PDF 转换为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：Edit text 模式框选页面上的每个文本块以便就地编辑，AI 面板用页码引用回答关于报告的问题"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 展示从 Helios 季度报告 PDF 本地转换而来的 Word 文档，在第二个标签页中与原始 PDF 并排打开"></td>
</tr>
<tr>
<td><b>在页面内编辑</b> — Edit text 模式框选每个文本块以便就地重写；内容流通过 PDFium 用原始字体重写，而非覆盖贴纸。向 AI 提问长报告，获得带页码引用的回答。</td>
<td><b>在设备端转换</b> — <b>PDF Converter → PDF to Word</b> 生成可编辑的 <code>.docx</code>，在 Docs 中与源文件并排打开，标题、数字行和段落完整保留。Excel 和 PowerPoint 目标同理；扫描页面走系统 OCR。</td>
</tr>
</table>

### 5 · HTML — AI 页面和 UI 构建器，先出设计简报

告诉 AI 页面的用途和受众。AI 先提出一份**设计简报**——钩子、配色、排版和风格方向——然后基于这些 token 构建单个独立的 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 对 Lumen 落地页换肤的延时：面板中一次 Restyle 请求将深色 Midnight Studio 页面变为温暖的 Solar Daybreak 版本，每个章节和所有内容保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：生成的太阳能台灯落地页，深色 Midnight Studio 风格，在实时预览中显示，AI 面板总结刚构建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一个 Lumen 落地页，由 AI 转换为温暖的 Solar Daybreak 风格：纸质背景、衬线标题和橙色点缀，保留每个章节和所有文本"></td>
</tr>
<tr>
<td><b>从一条提示词生成</b> — Lumen 的大胆 hero、功能卡片、定价和等候名单表单，以 Midnight Studio 风格构建。点击任意元素调整样式，双击编辑文本，或切换到 CodeMirror 源码视图。</td>
<td><b>同一设计，新方向</b> — 一次 <b>Restyle</b> 请求即可切换简报的 token，页面随之调整：温暖纸张、编辑衬线、太阳橙点缀，不重写任何内容。全屏演示，或导出为 PDF 或原生可编辑的 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由设计师生成的个人仪表盘 UI，温暖亚麻风格，左侧导航栏、衬线问候语和四张指标卡"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：生成的电动汽车市场数据报告，大报风格，衬线标题、1730 万的主数字和一行核心指标"></td>
</tr>
<tr>
<td><b>UI 原型</b> — "personal dashboard" 模板将人物画像转化为可用布局：左侧导航栏、问候语、可计费工时迷你图、发票和利用率卡片，全是可直接交给开发者的真实 HTML。</td>
<td><b>数据故事</b> — "data report" 模板构建编辑式大报：衬线标题、一个主数字、用线条分隔的核心指标行、内联 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown — 基于纯 `.md` 的块编辑器，支持 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中段落后出现 Ask AI 弹窗，含输入的指令和建议芯片如 Polish、Make more concise、Expand 和 Fix grammar，以及 Send now 和 Add to queue 按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 展示含表格、Mermaid 流程图和任务列表的发布说明文档，左侧是 AI 面板的启动提示词"></td>
</tr>
<tr>
<td><b>对选区使用 Ask AI</b> — 选中任意段落即出现 <b>Ask AI</b> 芯片：输入指令或选择建议，直接发送，或收集多个锚定文本的修改后一次性执行。每个应用都有相同入口。</td>
<td><b>渲染显示，保存为纯 Markdown</b> — Tiptap 块编辑器中的标题、列表、表格、图片、代码块和 Mermaid 图表，写回为纯 <code>.md</code>，支持完全本地的 <b>Markdown → Word</b> 导出。</td>
</tr>
</table>

### 7 · CLI — 编程智能体在本机驱动 GenOffice

GenOffice 附带 `genoffice` 命令行和智能体 skill。安装 skill 后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 即可通过与应用相同的引擎创建、转换、读取和编辑真实 Office 文件，无需打开窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 展示编程智能体通过 genoffice 命令行构建的八页太阳系演示文稿：画布上的首页、左侧八个缩略图和打开的 AI 面板" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的八页渲染幻灯片并排展示：封面、太空探索时间线、四个核心数字、行星直径柱状图、岩石行星与气态巨行星对比、太阳 99.8% 的主数字、四颗巨行星网格和结论"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置，Integrations 页面：genoffice skill 已安装到 Claude Code，Codex 和 Cursor 旁边有安装按钮"></td>
</tr>
<tr>
<td><b>给智能体一条提示词</b> — "构建一个关于太阳系的八页演示文稿。" 智能体读取 skill，编写样式表、大纲和每页的页面规格，用 <code>genoffice image</code> 生成两张图片，让 <code>genoffice slides check</code> 拒绝所有溢出或重叠的内容，然后 <code>genoffice create</code> 组装 <code>.pptx</code>，<code>slides render</code> 返回每页的 PNG 供查看。</td>
<td><b>一次安装，通过设置 → Integrations</b> — GenOffice 显示在这台电脑上找到的编程智能体，并将 skill 写入你选择的每个智能体。或下载 skill 的 zip，或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行和智能体 skill</a>。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 使用相同工具

每个 `genoffice` 命令也是 MCP 工具。Claude Code、Claude Desktop、Cursor 和任何其他 MCP 客户端都能自行启动 `genoffice mcp`，无需安装 skill，无需打开窗口，获得 29 个工具以及作为资源的指南。应用内的第二个 HTTP 服务器让智能体在你眼前于可见的编辑器标签页中构建 Word 文档。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 genoffice MCP 服务器构建八页可再生能源投资者演示文稿的延时：搜索数据和照片，用 media 检查每张候选图片，deck_start 写入样式表和大纲，deck_page 逐页添加受控页面，deck_build 组装 .pptx，slides_render 返回每页图片；完成的演示文稿随后在 GenOffice Slides 中打开" width="100%">

<table>
<tr>
<td width="50%"><img
<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 开源 AI 办公套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个功能完整的开源 AI 办公套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件，由你和你的 AI 共同编辑，并以真实格式保存回去。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="许可证：Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="最新版本"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="下载量"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub 星标"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <b>Português (Brasil)</b> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是 Microsoft Office 的免费开源替代品，支持 macOS、Windows 和 Linux。它能打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown 和 HTML，并在每个文档旁配备一个 AI 智能体——不是嵌在侧边的聊天框，而是一个能读取文件、执行修改并精确展示改动位置的编辑器。

- **真实格式，逐字节保留。** 只重写你编辑的内容。文件其余部分逐字节保持不变，因此文档在 Word、Excel 和 PowerPoint 中依然正常工作。
- **可审查的 AI。** 编辑以修订和 diff 形式呈现，一键即可撤销。电子表格获得实时公式，而非粘贴的数值。演示文稿和页面直接在画布上生成，且完全可编辑。
- **本地优先设计。** 文件在本机打开、编辑、保存和转换。PDF → Word / Excel / PowerPoint、Markdown → Word 和 HTML → Word 均在本地运行。只有 AI 调用会离开本机，发送到你选择的提供商。
- **用你的密钥，或不用密钥。** 使用 Genspark 登录即可免密钥，或使用你自己的密钥接入 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty，或任何兼容 OpenAI 的端点，包括本地服务器。
- **可自动化，面向智能体。** 应用内置 `genoffice` 命令行和适用于 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的 skill，让编程智能体无需打开窗口即可在本机创建、转换、读取和编辑真实的 Office 文件。

**下载：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情和要求见[下载](#download)。

## 演示

六个应用、一个 AI 面板，以及一条供编程智能体使用的命令行。每张截图均来自 macOS 上的真实应用，AI 由面板中可见的提示词触发。

### 1 · Docs — 打开并编辑 `.docx`，AI 编辑可审查

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 渲染一份双栏年度报告页面，含全宽封面图、带底纹的 KPI 表格、页眉页脚，80% 缩放，AI 面板已收起"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：一份带横幅图片的公司概览；AI 精简了 Overview 部分并插入了一个新的项目符号部分，面板提供一键撤销"></td>
</tr>
<tr>
<td><b>按 Word 的组织方式打开文件</b> —— 双栏分节、出血图片、带底纹表格、页眉页脚，分页遵循 Word 的行度量。样式、批注、修订、公式和数字墨迹往返后完好无损。</td>
<td><b>下达编辑指令</b> —— AI 读取所需区块，重写 Overview 部分并插入新的项目符号部分。每次 AI 交互都是一个可撤销的快照；开启<b>修订</b>后，编辑以 Word 风格的修订形式呈现。</td>
</tr>
</table>

### 2 · Sheets — `.xlsx` 带实时公式和图表，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 添加了一个 Summary 工作表，使用 SUMIF 公式按地区和类别统计收入，并插入柱状图，报告已应用 43 处更改并提供撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：当被问及哪个地区在 Q2 收入领先时，AI 回答欧洲并给出按类别的明细，引用所用单元格作为可点击链接，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td><b>构建</b> —— 仅凭一句话，智能体添加一个 Summary 工作表，按地区和类别使用真实的 <code>SUMIF</code>，插入柱状图，并将 43 处更改作为单个可撤销批次应用。</td>
<td><b>提问</b> —— 关于工作簿的问题会返回推理过程和所用确切单元格作为可点击引用。底层：自研的 Rust `.xlsx` 引擎、数据透视表、切片器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资者演示文稿的延时：AI 在面板中规划叙事，幻灯片逐一出现在画布上，最终完成的演示文稿以收尾行动号召结束" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 在画布上生成的 Aurora Home 投资者演示文稿封面幻灯片，面板中显示原始的一行提示词和 AI 关于所构建内容的摘要"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的最终设计幻灯片，左侧是缩略图条，AI 面板总结叙事"></td>
</tr>
<tr>
<td><b>一行输入</b> —— “为 Aurora Home 创建一份 10 页的投资者演示文稿……”。GenOffice 规划叙事、查找数据，并直接在画布上以真实 `.pptx` 形式起草每张幻灯片。</td>
<td><b>一份完成的演示文稿</b> —— 十一张设计幻灯片，排版和图片一致，并有收尾行动号召；可继续使用母版、版式、智能参考线和非破坏性裁剪编辑，或让面板重新设计样式、重写和重排。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，在设备上转换 PDF 为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：编辑文本模式为页面上每个文本块绘制边框以便就地编辑，AI 面板回答关于报告的问题并附页码引用"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 显示一份从 Helios 季度评审 PDF 本地转换而来的 Word 文档，在第二个标签页中打开，旁边是原始 PDF"></td>
</tr>
<tr>
<td><b>在页面内编辑</b> —— 编辑文本模式为每个文本块绘制边框以便就地重新输入；内容流通过 PDFium 使用原始字体重写，而非遮盖注释。向 AI 询问长篇报告，可获得带页码引用的回答。</td>
<td><b>在设备上转换</b> —— <b>PDF 转换器 → PDF 转 Word</b> 生成可编辑的 `.docx`，在 Docs 中与原始文件并排打开，标题、统计行和段落完好无损。Excel 和 PowerPoint 目标同理；扫描页通过系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — AI 页面和界面构建器，设计简报优先

告诉 AI 页面的用途和受众。AI 首先提出一份**设计简报**——钩子、配色、排版和风格方向——然后基于这些 token 构建单个自包含的 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时：面板中的 Restyle 请求将深色 Midnight Studio 页面转换为温暖的 Solar Daybreak 版本，所有部分和文本保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，采用深色 Midnight Studio 方向，在实时预览中显示，AI 面板总结刚构建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一 Lumen 落地页被 AI 重新设计为温暖的 Solar Daybreak 方向：纸质色调背景、衬线标题和橙色高亮，所有部分和文本保留"></td>
</tr>
<tr>
<td><b>从提示词生成</b> —— Lumen 的醒目 hero、功能卡片、定价和等候列表表单，以 Midnight Studio 方向构建。点击任意元素即可重新设计样式，双击编辑文本，或切换到 CodeMirror 代码视图。</td>
<td><b>同一设计，新方向</b> —— 一次<b>重新设计样式</b>请求即可更换简报 token，页面随之变化：温暖纸张、编辑衬线、太阳橙高亮，无需重写。全屏演示，或导出为 PDF 或原生可编辑的 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由设计师生成的个人仪表盘界面，采用温暖的亚麻风格，含侧边栏、衬线问候语和四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：关于电动汽车市场的数据报告，以报纸风格生成，含衬线标题、1730 万的醒目数字和统计行"></td>
</tr>
<tr>
<td><b>界面原型</b> —— “个人仪表盘”模板将人物画像转化为可用布局：侧边栏、问候语、可计费工时迷你图、发票和使用率卡片，全部为真实 HTML，可交付给开发者。</td>
<td><b>数据叙事</b> —— “数据报告”模板构建一份编辑式报纸：衬线标题、醒目数字、分隔线统计行、内联 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown — 基于纯 `.md` 的块编辑器，支持 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中的段落显示 Ask AI 弹出框，含已输入的指令和建议芯片如改进、精简、扩展和修正语法，以及立即发送和加入队列按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 渲染一份发布说明文档，含表格、Mermaid 流程图和任务列表，左侧是 AI 面板的初始提示词"></td>
</tr>
<tr>
<td><b>对选中内容询问 AI</b> —— 选中任意片段即出现 <b>Ask AI</b> 芯片：输入指令或选择建议，立即发送，或将多个锚定编辑加入队列后一次性执行。所有应用都有相同入口。</td>
<td><b>渲染后保存为纯 Markdown</b> —— Tiptap 块编辑器中的标题、列表、表格、图片、代码块和 Mermaid 图表，写回为纯 `.md`，并支持完全本地的 <b>Markdown → Word</b> 导出。</td>
</tr>
</table>

### 7 · CLI — 你的编程智能体在本机指挥 GenOffice

GenOffice 内置 `genoffice` 命令行和智能体 skill。安装 skill 后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 即可使用与应用相同的引擎创建、转换、读取和编辑真实的 Office 文件，无需打开窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示一份关于太阳系的八页演示文稿，由编程智能体通过 genoffice 命令行构建：画布上的封面幻灯片、左侧八个缩略图和打开的 AI 面板" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的八张渲染幻灯片并排显示：封面、探索时间线、四个关键数字、行星直径柱状图、岩石世界与气态巨行星、太阳 99.8% 的醒目数字、四颗巨行星网格和结论"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置，集成页面：genoffice skill 已安装到 Claude Code，Codex 和 Cursor 旁有安装按钮"></td>
</tr>
<tr>
<td><b>给你的智能体一个提示词</b> —— “创建一份关于太阳系的八页演示文稿。”智能体读取 skill，编写样式表、大纲和每页规格，用 <code>genoffice image</code> 生成两张图片，让 <code>genoffice slides check</code> 拒绝任何溢出或重叠的内容，然后 <code>genoffice create</code> 组装 <code>.pptx</code>，<code>slides render</code> 返回每页一张 PNG 供检查。</td>
<td><b>一次安装，在设置 → 集成中</b> —— GenOffice 列出本机找到的编程智能体，并将 skill 写入你选择的每个智能体。也可下载 skill 的 zip，或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行和智能体 skill</a>。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 使用相同工具

每个 `genoffice` 命令也是一个 MCP 工具。Claude Code、Claude Desktop、Cursor 和任何其他 MCP 客户端都可以自行启动 `genoffice mcp`，无需安装任何 skill 或打开窗口，并获得 29 个工具以及作为资源的操作参考。应用内的第二个 HTTP 服务器允许智能体在你眼前于可见的编辑器标签页中构建 Word 文档。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 genoffice MCP 服务器构建一份关于可再生能源的八页投资者演示文稿的加速序列：它获取数据和照片，用 media 检查每张候选图片，deck_start 写入样式表和大纲，deck_page 逐页添加并验证，deck_build 组装 .pptx，slides_render 返回每张幻灯片的图像；完成的演示文稿随后在 GenOffice Slides 中打开" width="100%">

<table
<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 内置 AI 面板的开源 AI 办公套件：Docs、Sheets、Slides、PDF、Markdown、HTML" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个功能完备的开源 AI 办公套件。</b><br>
Word、Excel、PowerPoint、PDF 文件由你和你的 AI 共同编辑，并以真实格式原样保存。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="许可证：Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="最新发布版本"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="下载量"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub 星标数"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>网站</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是一款免费开源的 Microsoft Office 替代品，支持 macOS、Windows 和 Linux。它能打开并保存原生 `.docx`、`.xlsx`、`.pptx` 文件，编辑 PDF、Markdown、HTML，并在每份文档旁配备 AI 智能体——不是附加的聊天机器人，而是能读取文件、执行修改，并展示具体改动了什么的编辑器。

- **保留真实格式，逐字节不变。** 只有编辑过的部分会被重写，文件其余部分逐字节保持原样，文档在 Word、Excel、PowerPoint 中仍能正常打开。
- **可审查的 AI。** 编辑以修订和 diff 形式呈现，支持一键回滚。电子表格中写入的是实时生效的公式，而非粘贴的数值。幻灯片和页面直接在画布上生成，可继续自由编辑。
- **本地优先设计。** 文件在你的设备上打开、编辑、保存和转换。PDF → Word / Excel / PowerPoint、Markdown → Word、HTML → Word 转换全部在设备内完成。只有 AI 调用会发送到你选择的提供商。
- **有 API 密钥可以，没有也行。** 登录 Genspark 即可免密钥直接使用；也可以自行接入 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty，以及任何 OpenAI 兼容端点（含本地服务器）。
- **可脚本化，智能体即用。** 应用自带 `genoffice` 命令行和适用于 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode、Windsurf 的技能，让编码智能体无需打开窗口，就能在你电脑上创建、转换、读取、编辑真实的 Office 文件。

**下载：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详见[下载](#download)章节了解详情和要求。

## 演示

六个应用，一个 AI 面板，以及面向编码智能体的命令行。所有截图均为 macOS 上实际运行的应用，AI 由面板中可见的提示词直接驱动。

### 1 · Docs — 用可审查的 AI 打开并编辑 `.docx`

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 以 80% 缩放比例渲染一份双栏年度报告页面，包含全宽封面图、带底纹的 KPI 表格、页眉和页脚，AI 面板处于折叠状态"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：在一份带横幅图片的公司概览文档中，AI 润色了概览章节并插入了新的项目符号章节，面板提供一键回滚"></td>
</tr>
<tr>
<td><b>按 Word 排版的原始样式打开文件</b> — 双栏布局、无边框全幅图片、底纹表格、页眉页脚，以及遵循 Word 逐行计量标准的换页，全部原样保留。样式、批注、修订、公式、墨迹注释也完好无损。</td>
<td><b>提出你想要的编辑</b> — AI 读取所需区块，重写概览并插入新的项目符号章节。AI 的每项操作都留下可回滚的快照；开启<b>修订</b>后，编辑以 Word 风格的修改标记呈现。</td>
</tr>
</table>

### 2 · Sheets — 带实时公式和图表的 `.xlsx`，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 使用 SUMIF 公式添加了按地区和类别统计销售额的 Summary 工作表和一个柱状图，并提示已应用 43 项更改，附带撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：询问哪个地区主导了第二季度销售额时，AI 回答为欧洲并附类别明细，同时以可点击链接形式引用所用单元格（显示在 Orders 工作表旁）"></td>
</tr>
<tr>
<td><b>直接帮你创建</b> — 一句请求，智能体就添加了含按地区和类别统计的真实 <code>SUMIF</code> 公式的 Summary 工作表，插入柱状图，并将 43 项更改作为一个可撤销的批次应用。</td>
<td><b>尽管提问</b> — 关于工作簿的问题会附带依据回答，所用确切单元格以可点击来源返回。底层运行自研的 Rust <code>.xlsx</code> 引擎，支持透视表、切片器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 一句提示词完成的 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资者演示文稿的延时：AI 在面板中构思故事线，幻灯片依次出现在画布上，完成的文稿以收尾建议结束" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：画布上显示 AI 生成的 Aurora Home 投资者演示文稿封面幻灯片，面板中可见原始单行提示词和 AI 所生成内容的摘要"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页文稿设计完成的最后一页幻灯片，左侧为缩略图列表，AI 面板显示完整故事线摘要"></td>
</tr>
<tr>
<td><b>只需输入一行</b> — 比如“为 Aurora Home 制作一份 10 页的投资者路演文稿……”。GenOffice 会构建故事线、调研所需数据，并将所有幻灯片以真实 <code>.pptx</code> 形式草拟到画布上。</td>
<td><b>得到一份完成的文稿</b> — 11 页设计完成的幻灯片，排版一致、配图齐全，并以行动号召收尾。可用母版、版式、智能参考线、非破坏性裁剪继续编辑，或在面板中要求更改风格、重写、重新排序。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，在设备内转换为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：文本编辑模式显示页面上所有文本块以便直接编辑，同时 AI 面板回答关于报告的问题并附页码来源"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 在第二个标签页中打开从 Helios 季度报告 PDF 本地转换而来的 Word 文档，旁边是原始 PDF"></td>
</tr>
<tr>
<td><b>在页面内直接编辑</b> — 文本编辑模式显示所有文本块，可就地重新输入；不是覆盖式注释，而是通过 PDFium 重写内容流本身，保留原始字体。对长报告向 AI 提问，可获得带页码来源的回答。</td>
<td><b>在设备内转换</b> — 运行 <b>PDF 转换器 → PDF 转 Word</b> 会生成可编辑的 <code>.docx</code>，在 Docs 中于原文件旁打开，标题、统计行、段落均保留。Excel 和 PowerPoint 转换同样如此，扫描页面则经过系统 OCR。</td>
</tr>
</table>

### 5 · HTML — 先给出设计简报的 AI 页面与 UI 构建器

告诉页面用途和目标受众。AI 会先提出一份**设计简报**——包括钩子文案、配色方案、排版、风格方向——然后基于这些 token 生成一个完全独立的 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时：面板中一次 Restyle 请求将深色 Midnight Studio 页面变为温暖的 Solar Daybreak 版本，但所有章节和文案保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：以深色 Midnight Studio 风格生成的太阳能台灯落地页显示在实时预览中，AI 面板总结刚创建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一 Lumen 落地页被 AI 重新设计为温暖的 Solar Daybreak 风格：纸质纹理背景、衬线标题、橙色强调色，但所有章节和文案保持不变"></td>
</tr>
<tr>
<td><b>一次提示词即可生成</b> — Midnight Studio 风格下醒目的主视觉区、功能卡片、定价、Lumen 的等候名单表单。点击元素可改样式，双击可编辑文本，也可切换到 CodeMirror 源码视图。</td>
<td><b>设计不变，方向不同</b> — 一次<b>更改风格</b>请求即改变简报中的 token，页面随之变化：温暖的纸质纹理、编辑风衬线字体、鲜明的橙色强调色，内容保持不变。可全屏演示，或导出为 PDF、可编辑的原生 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由职业设计师生成的个人仪表盘 UI，采用温暖的亚麻风格，含左侧栏、衬线问候语、四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：以报纸格式生成的电动汽车市场数据报告，含衬线报头、1730 万的头条数字、统计行"></td>
</tr>
<tr>
<td><b>UI 原型</b> — “个人仪表盘”起始模板将人物设定转化为可实际运行的布局：左侧栏、问候语、可计费时间迷你折线图、发票和使用率卡片，全部是可直接交给开发者的真实 HTML。</td>
<td><b>数据叙事</b> — “数据报告”起始模板生成报纸风格的编辑内容：衬线报头、一个头条数字、以分隔线划分的统计行、内联 SVG 图表、方法论说明。</td>
</tr>
</table>

### 6 · Markdown — 基于纯 `.md` 的块编辑器，带 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中段落后弹出 Ask AI 浮层，显示输入的指令以及润色、更简洁、扩展、修正语法等建议标签，还有立即发送和加入队列按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 渲染一份含表格、Mermaid 流程图、待办列表的发布公告文档，左侧显示 AI 面板的起始提示词"></td>
</tr>
<tr>
<td><b>对选中内容向 AI 提问</b> — 选中想要的部分会出现 <b>Ask AI</b> 标签：可直接输入指令或选择建议，立即执行，或将多个定位编辑加入队列一次性执行。同一入口在所有应用中都有。</td>
<td><b>渲染显示，但保存为纯 Markdown</b> — Tiptap 块编辑器支持标题、列表、表格、图片、代码块、Mermaid 图表，保存时仍以纯 <code>.md</code> 原样写入，并支持完全本地运行的 <b>Markdown → Word</b> 导出。</td>
</tr>
</table>

### 7 · CLI — 编码智能体在你电脑上驱动 GenOffice

GenOffice 自带 `genoffice` 命令行和智能体技能。安装技能后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode、Windsurf 就能通过与应用相同的引擎，无需打开窗口即可创建、转换、读取、编辑真实的 Office 文件。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示编码智能体用 genoffice 命令行制作的 8 页太阳系演示文稿：画布上为封面幻灯片，左侧有八个缩略图，AI 面板处于打开状态" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的八张渲染幻灯片并排显示：封面、探索时间线、四项核心数据、行星直径柱状图、岩石行星与巨行星、太阳占 99.8% 的头条数字、四颗巨行星网格、总结"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置中的集成页面：genoffice 技能已安装到 Claude Code，Codex 和 Cursor 旁显示安装按钮"></td>
</tr>
<tr>
<td><b>给智能体一句提示词</b> — “制作一份关于太阳系的 8 页演示文稿。”智能体会读取技能，编写样式表、大纲和每页一份的页面规格，用 <code>genoffice image</code> 生成两张图片，用 <code>genoffice slides check</code> 筛掉溢出或重叠的元素，再用 <code>genoffice create</code> 组装 <code>.pptx</code>，并用 <code>slides render</code> 获取每页一张 PNG 来确认。</td>
<td><b>在设置 → 集成中一次安装</b> — GenOffice 列出在这台电脑上找到的编码智能体，并将技能写入你选择的每个智能体。也可下载技能 zip 或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行与智能体技能</a>。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 提供同样的工具

所有 `genoffice` 命令同时也是 MCP 工具。Claude Code、Claude Desktop、Cursor 及其他所有 MCP 客户端无需安装技能或打开窗口，直接运行 `genoffice mcp` 即可获得 29 个工具和以资源形式提供的任务参考。应用内的第二个 HTTP 服务器还能让智能体在可见的编辑器标签页中实时观看 Word 文档的创建过程。

<img src="../assets/readme
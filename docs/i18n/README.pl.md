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
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="最新发布版本"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="下载量"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub 星标数"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <b>Polski</b> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是 macOS、Windows 和 Linux 上 Microsoft Office 的免费开源替代品。它能打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown 和 HTML，并为每个文档配备 AI 智能体——不是外挂的聊天窗口，而是能读取文件、做出修改并精确展示改动位置的编辑器。

- **真实格式，逐位保留。** 只有你编辑的部分会被重写。文件其余内容逐位保持不变，因此文档在 Word、Excel 和 PowerPoint 中依然可用。
- **可验证的 AI。** 改动以修订标记和差异呈现，一键即可还原。电子表格得到的是实时公式，而非粘贴的数字。演示文稿和页面在画布上生成，且完全可编辑。
- **本地优先是设计原则。** 文件在你的设备上打开、编辑、保存和转换。PDF → Word / Excel / PowerPoint、Markdown → Word 和 HTML → Word 转换均在本地完成。只有 AI 请求会离开你的机器——并发送到你自行选择的提供商。
- **用你的密钥，或者不用。** 通过 Genspark 登录即可免密钥，或使用你自己的 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty 密钥，或任何兼容 OpenAI 的端点，包括本地服务器。
- **可脚本化，面向智能体。** 应用提供 `genoffice` 命令行以及适用于 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的智能体技能，编码智能体无需打开窗口即可在你的电脑上创建、转换、读取和编辑真实的 Office 文件。

**下载：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情和要求见[下载](#download)部分。

## 演示

六个应用、一个 AI 面板，以及为你的编码智能体准备的命令行。每张截图都来自 macOS 上的真实应用，AI 由面板中可见的提示词驱动。

### 1 · Docs — 打开并编辑 `.docx`，AI 改动可验证

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 渲染双栏年度报告页面，封面为全幅照片，带底纹的 KPI 表格、页眉和页脚，80% 缩放，AI 面板已折叠"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：带横幅图片的公司概览；AI 精简了 Overview 部分并插入新的项目符号部分，面板提供一键还原"></td>
</tr>
<tr>
<td><b>按 Word 的排版方式打开文件</b> — 双栏分节、全宽图片、带底纹的表格、页眉页脚，按 Word 行度量分页。样式、批注、修订、公式和手写内容原样返回。</td>
<td><b>提出修改要求</b> — AI 读取所需片段，重写 Overview 部分并插入新的项目符号部分。每一步 AI 操作都是一个可还原的快照；开启<b>修订</b>后，编辑以 Word 风格的修订形式呈现。</td>
</tr>
</table>

### 2 · Sheets — `.xlsx` 带实时公式和图表，而非粘贴的数字

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 使用 SUMIF 公式添加了按地区和类别统计收入的 Summary 工作表，并添加柱状图，报告已应用 43 项更改，带 Undo 按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：对于 Q2 收入哪个地区领先的问题，AI 回答欧洲并给出类别细分，同时以可点击链接形式提供所用单元格，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td><b>一句话构建</b> — 智能体根据一句话添加 Summary 工作表，包含按地区和类别的真实 <code>SUMIF</code> 公式，插入柱状图，并将 43 项更改作为一组统一撤销。</td>
<td><b>提问</b> — 关于工作簿的问题会返回推理依据和具体单元格，作为可点击引用。底层：自研 Rust `.xlsx` 引擎、数据透视表、筛选器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资演示文稿的延时摄影：AI 在面板中规划叙事，幻灯片逐张出现在画布上，完成的演示文稿以最终行动号召收尾" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 生成的投资演示文稿 Aurora Home 的标题幻灯片显示在画布上，面板中有原始单行提示词和 AI 对构建内容的总结"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的设计感结尾幻灯片，左侧为缩略图栏，AI 面板总结叙事"></td>
</tr>
<tr>
<td><b>输入一行</b> — “为 Aurora Home 创建一份 10 页投资演示文稿……”。GenOffice 规划叙事、核对数据，并在画布上逐页生成真正的 `.pptx` 文件。</td>
<td><b>输出完整演示文稿</b> — 十一张设计统一的幻灯片，排版、图形和结尾行动号召一致；可继续用母版、版式、智能参考线和非破坏性裁剪编辑，或让面板更改样式、重写和调整顺序。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，本地将 PDF 转换为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：Edit text 模式高亮页面上每个文本块以便就地编辑，AI 面板回答关于报告的问题并引用页码"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 显示从 Helios 季度 PDF 报告本地转换而来的 Word 文档，在第二个标签页中与原始 PDF 并排打开"></td>
</tr>
<tr>
<td><b>在页面内编辑</b> — Edit text 模式高亮每个文本块以便就地重新输入；内容流由 PDFium 重写，保留原始字体，而非用注释覆盖。向 AI 提问长报告，可获得带页码引用的回答。</td>
<td><b>本地转换</b> — <b>PDF Converter → PDF to Word</b> 生成可编辑的 `.docx`，在 Docs 中与源文件并排打开，保留标题、统计行和段落。转换为 Excel 和 PowerPoint 同理；扫描页通过系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — 从设计简报开始的页面和界面 AI 构建器

告诉它页面用途和目标受众。AI 首先提出**设计简报**——标语、配色、排版和风格方向——然后按这些准则构建单个独立的 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 为 Lumen 落地页换肤的延时摄影：面板中一条 Restyle 请求将深色 Midnight Studio 页面变为温暖的 Solar Daybreak 版本，每个部分和全部内容保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，采用深色 Midnight Studio 方向，在实时预览中显示，AI 面板总结刚构建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一个 Lumen 落地页被 AI 重新设计为温暖的 Solar Daybreak 方向：纸质背景、衬线标题和橙色点缀，所有部分和内容保持不变"></td>
</tr>
<tr>
<td><b>一句话生成</b> — Lumen 的大胆 hero、功能卡片、定价和等候名单表单，按 Midnight Studio 方向构建。点击任意元素更改样式，双击编辑文本，或切换到 CodeMirror 源码视图。</td>
<td><b>同一设计，全新方向</b> — 一条 <b>Restyle</b> 请求替换简报准则，页面随之调整：温暖纸张、编辑感衬线、阳光橙点缀，无需从头重写。可全屏演示，或导出为 PDF 或原生可编辑 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由职业设计师生成的个人仪表盘界面，温暖的亚麻风格，带左侧边栏、衬线问候语和四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：生成的电动汽车市场数据报告，报纸风格，带衬线报头、1730 万的头条数字和统计行"></td>
</tr>
<tr>
<td><b>界面原型</b> — “personal dashboard” 模板将人物设定变为可用布局：左侧边栏、问候语、计费小时迷你图、发票和使用卡片——全部是真实 HTML，可交给开发者。</td>
<td><b>数据故事</b> — “data report” 模板生成编辑感报纸报告：衬线报头、一个头条数字、分隔线统计行、内嵌 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown — 基于普通 `.md` 文件的块编辑器，带 Ask AI 功能

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中段落显示 Ask AI 弹窗，已输入指令和提示词标签，如 Polish、Make more concise、Expand 和 Fix grammar，还有 Send now 和 Add to queue 按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 渲染带表格、Mermaid 流程图和任务列表的发布说明文档，左侧有 AI 面板起始提示"></td>
</tr>
<tr>
<td><b>对选中内容 Ask AI</b> — 选中任意片段即出现 <b>Ask AI</b> 标签：输入指令或选择提示词，立即发送，或将多个编辑排队并一次性执行。每个应用都有相同功能。</td>
<td><b>渲染显示，保存为普通 Markdown</b> — Tiptap 块编辑器中的标题、列表、表格、图片、代码块和 Mermaid 图表，保存回普通 `.md` 文件，<b>Markdown → Word</b> 导出完全本地完成。</td>
</tr>
</table>

### 7 · CLI — 你的编码智能体在你的电脑上驱动 GenOffice

GenOffice 提供 `genoffice` 命令行和智能体技能。安装技能后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 即可通过与应用相同的引擎创建、转换、读取和编辑真实 Office 文件，无需打开窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示编码智能体通过 genoffice 命令行构建的八页太阳系演示文稿：画布上的标题幻灯片、左侧八个缩略图和打开的 AI 面板" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的八张渲染幻灯片并排显示：封面、探索时间线、四个关键数字、行星直径柱状图、岩石行星对比气态巨行星、太阳占 99.8% 的头条数字、四颗巨行星网格和结论"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置，集成页面：genoffice 技能已安装到 Claude Code，Codex 和 Cursor 旁有安装按钮"></td>
</tr>
<tr>
<td><b>给你的智能体一句话</b> — “构建一份关于太阳系的八页演示文稿”。智能体读取技能，编写样式表、大纲和每页一份页面规格，用 <code>genoffice image</code> 生成两张图片，让 <code>genoffice slides check</code> 在 <code>genoffice create</code> 组装 <code>.pptx</code> 前剔除所有溢出或重叠内容，再由 <code>slides render</code> 输出每页一张 PNG 供查看。</td>
<td><b>在设置 → 集成中安装一次</b> — GenOffice 显示在这台电脑上找到的编码智能体，并将技能写入你选择的每一个。也可下载技能 zip 或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行和智能体技能</a>部分。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 使用相同工具

每条 `genoffice` 命令也是 MCP 工具。Claude Code、Claude Desktop、Cursor 和任何其他 MCP 客户端都能自行启动 `genoffice mcp`，无需安装任何技能，也无需打开窗口，并获得 29 个工具以及作为资源的操作参考。应用内的第二个 HTTP 服务器让智能体在你眼前于可见的编辑器标签页中构建 Word 文档。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 genoffice MCP 服务器构建八页可再生能源投资演示文稿的定格动画：搜索插图和照片，用 media 检查每张候选图片，deck_start 保存样式表和大纲，deck_page 逐页添加已验证页面，deck_build 组装 .pptx，slides_render 返回每张幻灯片的图像；完成的演示文稿随后在 GenOffice Slides 中打开" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/
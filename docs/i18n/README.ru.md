<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 免费开源、带 AI 的办公套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个全功能开源 AI 办公套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件由你和你的 AI 共同编辑，并以真实格式保存回去。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="许可证：Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="最新发布版本"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="下载量"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub 星标"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <b>Русский</b> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是面向 macOS、Windows 和 Linux 的免费开源 Microsoft Office 替代品。
它能打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown 和 HTML，
并在每份文档旁放置一个 AI 智能体——不是挂在侧边的聊天框，而是一个能读取文件、
做出修改、并精确告诉你改动了哪里的编辑器。

- **真实格式，逐字节保存。** 只重写你编辑的部分，文件其余内容逐字节保留，
  因此文档仍能在 Word、Excel 和 PowerPoint 中打开。
- **可核验的 AI 工作。** 改动以修订标记和 diff 呈现，一键回滚。表格中生成的是
  实时公式，而非粘贴的数字。演示文稿和页面直接在画布上生成，且完全可编辑。
- **全程本地运行。** 文件在你的电脑上打开、编辑、保存和转换。PDF → Word / Excel /
  PowerPoint、Markdown → Word 和 HTML → Word 的转换均在设备本地完成。
  只有 AI 请求会离开你的电脑——发往你选择的提供商。
- **自带密钥或无需密钥。** 通过 Genspark 登录即可完全不用密钥，也可使用自己的密钥
  接入 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、
  Mistral、OpenRouter、Requesty，或任何兼容 OpenAI 的端点，包括本地服务器。
- **可脚本化，面向智能体。** 应用自带 `genoffice` 命令行和适用于 Claude Code、
  Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的技能，
  编码智能体无需打开任何窗口，即可在你电脑上创建、转换、读取和编辑真实的 Office 文件。

**下载：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情和系统要求见[下载](#download)章节。

## 演示

六个应用、一个 AI 面板，以及为你的编码智能体准备的命令行。
每张截图都是 macOS 上的真实应用，AI 操作由面板上可读的提示词触发。

### 1 · Docs — 打开并编辑 `.docx`，AI 工作可核验

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 以 80% 缩放显示双栏年度报告页面，含全宽封面图、深色 KPI 表格、页眉页脚，AI 面板处于折叠状态"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：带横幅图片的公司概览；AI 精简了 Overview 章节并新增了一个列表章节，面板提供一键回滚"></td>
</tr>
<tr>
<td><b>打开文件，版式与 Word 一致</b>——双栏章节、整页图片、深色表格、页眉页脚，按 Word 行度量分页。样式、批注、修订、公式和手写内容在打开并保存后保持不变。</td>
<td><b>让 AI 做出改动</b>——AI 读取相关区块，重写 Overview 章节并新增一个列表章节。AI 的每一步都保存为可回滚的快照；开启<b>修订记录</b>后，改动以 Word 风格的修订形式呈现。</td>
</tr>
</table>

### 2 · Sheets — `.xlsx` 含实时公式和图表，而非粘贴的数字

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 新增了 Summary 工作表，用 SUMIF 公式按地区和类别汇总收入，并插入柱状图，报告已应用 43 处改动，带撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：被问及第二季度哪个地区收入领先时，AI 回答「欧洲」并附类别明细，以可点击引用标出精确单元格，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td><b>生成汇总</b>——一句话，智能体就新增 Summary 工作表，用真正的 <code>SUMIF</code> 公式按地区和类别汇总，插入柱状图，并将全部 43 处改动作为一个可撤销的批次应用。</td>
<td><b>提问</b>——关于工作簿的问题会返回解释和精确单元格的可点击引用。底层：自研 Rust `.xlsx` 引擎、数据透视表、切片器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到成品 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 为 Aurora Home 生成投资者演示文稿的延时：AI 在面板中规划叙事线，幻灯片在画布上逐一出现，成品以最终行动号召收尾" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 生成的 Aurora Home 投资者演示文稿封面幻灯片显示在画布上，面板中有原始单行提示词和 AI 关于所构建内容的摘要"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的精美收尾幻灯片，左侧有缩略图栏，AI 面板总结叙事线"></td>
</tr>
<tr>
<td><b>输入一行</b>——「为 Aurora Home 创建一份 10 页投资者演示文稿……」。GenOffice 构建叙事线、收集数据，并在画布上逐页生成真正的 <code>.pptx</code> 文件。</td>
<td><b>输出成品演示文稿</b>——十一页精美幻灯片，排版统一、配图完整、以行动号召收尾；可用母版、版式、智能参考线和无损裁剪继续编辑，或让面板改样式、重写文字、调整幻灯片顺序。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，在设备上转换 PDF 为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：文本编辑模式框出页面上每个文本块以便就地编辑，AI 面板回答关于报告的问题并附页码引用"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 显示从 Helios 季度报告 PDF 本地转换而来的 Word 文档，在第二个标签页中与原始 PDF 并排打开"></td>
</tr>
<tr>
<td><b>直接在页面上编辑</b>——文本编辑模式框出每个文本块以便就地重新输入；页面内容流通过 PDFium 重写，保留原始字体，而非叠加遮盖注释。向 AI 询问长报告，可获得带页码引用的回答。</td>
<td><b>在设备上转换</b>——<b>PDF Converter → PDF to Word</b> 生成可编辑的 <code>.docx</code> 文件，在 Docs 中与源文件并排打开，保留标题、统计行和段落。Excel 和 PowerPoint 同理；扫描页通过系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — 从设计简报开始的页面和界面 AI 构建器

告诉它页面用途和面向对象。AI 先提出**设计简报**——核心创意、配色、排版和风格
方案——再基于这些 token 构建单个自包含的 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 为 Lumen 落地页改版的延时：面板中一次 Restyle 请求将深色页面 Midnight Studio 变为温暖的 Solar Daybreak 版本，所有章节和文字保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：生成的太阳能台灯落地页，采用深色 Midnight Studio 风格，在实时预览中显示，AI 面板总结刚创建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一个 Lumen 落地页，由 AI 改版为温暖的 Solar Daybreak 风格：纸质背景、衬线标题和橙色点缀，所有章节和文字保留"></td>
</tr>
<tr>
<td><b>一个提示词生成</b>——Lumen 的醒目 hero 区、功能卡片、定价和等候名单表单，以 Midnight Studio 风格创建。点击任意元素可改样式，双击可编辑文字，或切换到 CodeMirror 查看源码。</td>
<td><b>同一设计，全新风格</b>——一次 <b>Restyle</b> 请求替换简报 token，页面随之调整：温暖纸张、编辑风衬线字体、阳光橙点缀——无需重写任何内容。可全屏演示，或导出为 PDF 或原生可编辑 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由职业设计师生成的个人仪表盘界面，采用温暖的「亚麻」风格，含侧边栏、衬线问候语和四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：生成的电车市场报告，采用宽幅报纸风格，含衬线页头、关键数字 1730 万和统计行"></td>
</tr>
<tr>
<td><b>界面原型</b>——「个人仪表盘」起始模板将人物画像变为可用原型：侧边栏、问候语、计费工时迷你图、账单和上传卡片——全部是真正的 HTML，可直接交给开发者。</td>
<td><b>数据驱动的叙事</b>——「数据报告」起始模板构建编辑风报纸版面：衬线页头、一个关键数字、带分隔线的统计行、内嵌 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown — 面向普通 `.md` 的块编辑器，带「询问 AI」功能

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中段落后弹出「询问 AI」窗口，含已输入的指令和提示词芯片，如「润色」「缩短」「扩展」「修正语法」，以及「立即发送」和「加入队列」按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 显示含表格、Mermaid 流程图和任务列表的发布说明文档，左侧有 AI 面板起始提示词"></td>
</tr>
<tr>
<td><b>对选中片段询问 AI</b>——选中任意片段，出现<b>询问 AI</b>芯片：输入指令或选择提示词，立即发送，或将多个关联修改加入队列一次执行。每个应用都有同样的入口。</td>
<td><b>渲染精美，保存为普通 Markdown</b>——Tiptap 块编辑器中的标题、列表、表格、图片、代码块和 Mermaid 图表，写回为普通 <code>.md</code> 文件，<b>Markdown → Word</b> 导出完全本地完成。</td>
</tr>
</table>

### 7 · CLI — 你的编码智能体在你电脑上操控 GenOffice

GenOffice 自带 `genoffice` 命令行和智能体技能。安装技能后，Claude Code、Codex、
Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 即可通过与应用相同的引擎
创建、转换、读取和编辑真实的 Office 文件，无需打开任何窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示编码智能体通过 genoffice 命令行构建的八页太阳系演示文稿：画布上的封面幻灯片、左侧八个缩略图和打开的 AI 面板" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的八页渲染幻灯片并排展示：封面、探索时间线、四个关键数字、行星直径柱状图、岩石世界与巨行星、太阳 99.8% 的关键数字、四颗巨行星网格和结论"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice Settings 的 Integrations 页面：genoffice 技能已安装到 Claude Code，旁边是 Codex 和 Cursor 的 Install 按钮"></td>
</tr>
<tr>
<td><b>给你的智能体一个提示词</b>——「做一份八页的太阳系演示文稿」。智能体读取技能，编写样式表、大纲和每页规格，通过 <code>genoffice image</code> 生成两张图片，让 <code>genoffice slides check</code> 拒绝任何越界或重叠的内容，再由 <code>genoffice create</code> 组装 <code>.pptx</code>，<code>slides render</code> 返回每页一张 PNG 供查看。</td>
<td><b>在「设置 → 集成」中一次安装</b>——GenOffice 列出本机找到的编码智能体，并将技能写入你选择的每一个。也可下载技能 zip 或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行和智能体技能</a>章节。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 使用相同工具

每个 `genoffice` 命令同时也是一个 MCP 工具。Claude Code、Claude Desktop、Cursor
及任何其他 MCP 客户端都能自行启动 `genoffice mcp`，无需安装技能、无需打开窗口，
即可获得 29 个工具以及作为资源的操作指南。应用内的第二个 HTTP 服务器让智能体
在你眼前的编辑器标签页中直接构建 Word 文档。

<img src="../assets/readme/mcp-deck-motion.webp" alt="Claude Code 通过 genoffice MCP 服务器构建八页可再生能源投资者演示文稿的加速录像：搜索插图和照片，用 media 检查每张候选照片，
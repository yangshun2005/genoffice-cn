<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 开源 AI 驱动的办公套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center" dir="rtl">GenOffice</h1>

<p align="center" dir="rtl"><b>全球首个功能完整的开源 AI 驱动 Office 套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件，由你和你的 AI 共同编辑，以原始格式保存。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="许可证：Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="最新版本"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="下载量"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub Stars"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <b>العربية</b> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center" dir="rtl">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>网站</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是 macOS、Windows 和 Linux 上 Microsoft Office 的免费开源替代品。
它直接打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown
和 HTML 文件，并在每个文档旁放置一个 AI 智能体——不是随意附着的聊天框，
而是一个能读取文件、执行修改、并明确告诉你它改动了什么的编辑器。

- **原生格式，字节级保存。** 只重写你编辑的部分，文件其余部分逐字节保持不变，
  文档在 Word、Excel 和 PowerPoint 中继续正常工作。
- **可审查的 AI。** 修改以修订标记和差异（diff）形式呈现，一键即可撤销。
  电子表格获得实时公式而非粘贴的数值；幻灯片和页面直接在画布上生成，
  且完全可编辑。
- **本地优先设计。** 文件在你的设备上打开、编辑、保存和转换。所有转换——
  PDF 转 Word / Excel / PowerPoint、Markdown 转 Word、HTML 转 Word——均在
  本地运行。只有 AI 请求会离开你的设备，且仅发送到你选择的服务提供商。
- **用你的密钥，或不用密钥。** 通过 Genspark 登录免去密钥管理，或使用你自己的
  密钥搭配 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、
  MiniMax、Grok、Mistral、OpenRouter、Requesty，或任何兼容 OpenAI 的端点，
  包括本地服务器。
- **可编程，为智能体而生。** 应用附带 `genoffice` CLI 和适用于 Claude Code、
  Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的技能，
  让编程智能体无需打开任何窗口即可在设备上创建、转换、读取和编辑真实的
  Office 文件。

**获取方式：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情和要求见[下载](#download)。

## 演示

六个应用，一个 AI 面板，以及为你的编程智能体准备的一条命令行。每张截图都
来自 macOS 上的实际应用，其中的 AI 输出对应面板中可读的提示词（prompt）。

### 1 · Docs — 打开并编辑 `.docx`，AI 修改可审查

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 应用展示一份双栏年度报告页面，含全页宽封面图、带底纹的 KPI 表格、页眉和页脚，缩放 80%，AI 面板折叠"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：公司概览含横幅图片；AI 更紧凑地重写了概览部分并新增了项目符号列表部分，面板提供一键撤销"></td>
</tr>
<tr>
<td dir="rtl"><b>完全按 Word 的呈现方式打开文件</b> — 双栏分节、全页宽图片、带底纹表格、页眉页脚，以及按 Word 行高度分页。保存时样式、批注、修订标记、公式和墨迹书写保持原样不变。</td>
<td dir="rtl"><b>下达修改指令</b> — AI 读取所需的文本块，重写概览部分并新增项目符号列表部分。每次 AI 操作都是一个可撤销的快照；启用<b>修订标记</b>后，修改以 Word 风格的修订形式呈现。</td>
</tr>
</table>

### 2 · Sheets — `.xlsx` 含实时公式和图表，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 新增了一个摘要工作表，使用 SUMIF 公式按地区和类别展示收入，并添加了柱状图，显示 43 项更改已应用及撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：当被问及第二季度收入最高的地区时，AI 回答为欧洲并附类别明细，引用所用单元格为链接，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td dir="rtl"><b>构建</b> — 一句话，智能体就新增一个摘要工作表，含按地区和类别的真实 <code>SUMIF</code> 公式，插入柱状图，并将 43 项更改作为一批可撤销操作应用。</td>
<td dir="rtl"><b>提问</b> — 关于工作簿的问题得到回答，附带推理说明和所用精确单元格的可点击引用。幕后：Rust 编写的内部 <code>.xlsx</code> 引擎、数据透视表、切片器（slicer）、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到完整的 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 创建 Aurora Home 投资者演示文稿的延时截图：AI 在面板中规划故事线，幻灯片逐一出现在画布上，最终完成的演示文稿以收尾请求结束" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 在画布上为 Aurora Home 投资者演示文稿生成的封面幻灯片，含单行原始提示词和 AI 在面板中对所构建内容的摘要"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的收尾幻灯片，左侧为缩略图栏，AI 面板总结叙事线"></td>
</tr>
<tr>
<td dir="rtl"><b>一行输入</b> — “为 Aurora Home 创建一份 10 页的投资者演示文稿……”。GenOffice 规划叙事线，查找数据，在画布上起草每张幻灯片，生成真实的 <code>.pptx</code> 文件。</td>
<td dir="rtl"><b>完整演示文稿输出</b> — 十一张幻灯片，字体和图片风格统一，含收尾行动号召；可通过母版、版式、智能参考线和非破坏性裁剪继续编辑，或让面板重新设计、改写或重新排序。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，本地将 PDF 转为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：文本编辑模式高亮页面中每个文本块以便就地编辑，AI 面板回答关于报告的问题并附页码引用"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 应用展示从 Helios 季度评审 PDF 本地转换而来的 Word 文档，在第二个标签页中与原始 PDF 并排打开"></td>
</tr>
<tr>
<td dir="rtl"><b>页面内编辑</b> — 文本编辑模式高亮每个文本块以便就地重写；内容流通过 PDFium 用原始字体重写，而非在文本上叠加遮盖层。向 AI 询问长报告，获得带页码引用的答案。</td>
<td dir="rtl"><b>本地转换</b> — <b>PDF Converter → PDF to Word</b> 生成可编辑的 <code>.docx</code> 文件，在 Docs 中与源文件并排打开，标题、统计行和段落保持完整。Excel 和 PowerPoint 目标格式同理；扫描页面通过操作系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — AI 驱动的页面和界面构建器，从设计简报开始

告诉 AI 页面的用途和目标受众。AI 首先提出一份**设计简报（design brief）**——
涵盖核心创意、配色方案、字体和风格方向——然后基于这些元素（token）构建
一个完全独立的 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时截图：面板中一次 Restyle 请求将 Midnight Studio 深色页面转换为温暖的 Solar Daybreak 版本，同时每个区块和所有内容保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，采用 Midnight Studio 深色方向，在实时预览中展示，AI 面板总结刚构建的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一 Lumen 落地页经 AI 重新设计为温暖的 Solar Daybreak 方向后：纸色背景、衬线标题、橙色点缀，所有区块和文本保持不变"></td>
</tr>
<tr>
<td dir="rtl"><b>从一条提示词生成</b> — Lumen 页面的大胆主视觉、功能卡片、定价和等候名单表单，以 Midnight Studio 方向构建。点击任意元素重新设计，双击编辑文本，或切换到 CodeMirror 源代码视图。</td>
<td dir="rtl"><b>同一设计，全新方向</b> — 一次<b>重新设计（Restyle）</b>请求替换简报元素，页面自动跟随：温暖的纸色背景、编辑风衬线字体、阳光橙点缀，不重写任何文本。全屏查看，或导出为 PDF 或可编辑的原生 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由设计师生成的个人仪表盘界面，采用温暖亚麻风格，含左侧边栏、衬线欢迎语和四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：电动汽车市场数据报告，采用大报风格生成，含衬线页眉、1730 万的主标题数字和统计行"></td>
</tr>
<tr>
<td dir="rtl"><b>界面原型（UI mockup）</b> — “个人仪表盘”起始模板将虚构人物转化为实用布局：侧边栏、欢迎语、可计费工时迷你图（Sparkline）、发票和利用率卡片，全部为可交付给开发者的真实 HTML。</td>
<td dir="rtl"><b>数据故事</b> — “数据报告”起始模板构建编辑风大报：衬线页眉、单一主标题数字、分隔线统计行、内联 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown — 纯文本 `.md` 文件上的块编辑器，含 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中段落显示 Ask AI 弹窗，含已输入指令和建议标签如 Polish、Make more concise、Expand、Fix grammar，以及 Send now 和 Add to queue 按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 应用展示一份发布说明文档，含表格、Mermaid 流程图和任务列表，左侧为 AI 面板的起始提示词"></td>
</tr>
<tr>
<td dir="rtl"><b>对选中文本使用 AI</b> — 选中任意段落即出现 <b>Ask AI</b> 面板：输入指令或选择建议，立即发送，或将多个针对特定位置的编辑加入队列一次性执行。所有应用都有相同入口。</td>
<td dir="rtl"><b>可视化渲染，纯文本 Markdown 保存</b> — 标题、列表、表格、图片、代码块和 Mermaid 图表在 Tiptap 块编辑器中呈现，写回为纯文本 <code>.md</code> 文件，<b>Markdown → Word</b> 导出完全本地运行。</td>
</tr>
</table>

### 7 · CLI — 你的编程智能体驱动 GenOffice，在本地运行

GenOffice 附带 `genoffice` CLI 和智能体技能。安装技能后，Claude Code、Codex、
Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf 即可通过应用使用的
相同引擎创建、转换、读取和编辑真实的 Office 文件，无需打开任何窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 展示由编程智能体通过 genoffice CLI 构建的八页太阳系演示文稿：画布上的封面幻灯片、左侧八个缩略图、AI 面板打开" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的八张渲染幻灯片并排展示：封面、探索时间线、四个关键数字、行星直径柱状图、岩石世界与气态巨行星、太阳 99.8% 的醒目数字、四大巨行星网格、要点总结"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置，Integrations 页面：genoffice 技能已安装到 Claude Code，Codex 和 Cursor 旁有 Install 按钮"></td>
</tr>
<tr>
<td dir="rtl"><b>一条提示词交给你的智能体</b> — “创建一份关于太阳系的八页演示文稿。”智能体读取技能，编写样式表、大纲和每页一页的规格，通过 <code>genoffice image</code> 生成两张图片，让 <code>genoffice slides check</code> 拒绝任何越界或重叠的元素，然后 <code>genoffice create</code> 组装 <code>.pptx</code>，<code>slides render</code> 返回每页的 PNG 供审阅。</td>
<td dir="rtl"><b>一次安装，从设置 → 集成</b> — GenOffice 列出在此设备上找到的所有编程智能体，并将技能写入你选择的每个智能体。或下载技能 zip 包，或运行 <code>npx skills add genspark-ai/genoffice</code>。命令和完整工作流见<a href="#command-line-and-agent-skill">命令行和智能体技能</a>。</td>
</tr>
</table>

###
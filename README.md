

> **[中文化] genoffice**
>
> 此项目是 [genspark-ai/genoffice](https://github.com/genspark-ai/genoffice) 的中文翻译版本。
> - 原项目 Stars: 9580
> - 主语言: TypeScript
> - 许可证: Apache-2.0
> - 翻译日期: 2026-10-14
> - 原始 README: [README_en.md](README_en.md)
>
> 说明：下方 README 正文为**原项目文档的中文翻译**，力求忠于原文；本页顶部的「中文快速上手」为**面向中文用户的补充导读**（非原文内容），目的是让你不用读完整篇 README 就能先把项目跑起来。
>
> 如有翻译不准确之处，欢迎提 Issue 或 PR。

---


## 🚀 中文快速上手（补充导读，非原文）

### 这是什么 / 解决什么问题
GenOffice 是一个开源 AI 办公套件，定位为 Microsoft Office 的免费替代品，支持 macOS、Windows 和 Linux。它能打开并保存原生的 `.docx`、`.xlsx`、`.pptx` 文件，也能编辑 PDF、Markdown 和 HTML，并在每个文档旁内置 AI 编辑能力。它解决的核心痛点是：让 AI 直接读写真实的 Office 文件格式（而非另存为私有格式），且只重写你改动的部分，其余内容按字节保留，文件仍能在 Word、Excel、PowerPoint 中正常使用。

### 快速上手（最短路径）
1. 下载安装包：前往 [Releases 页面](https://github.com/genspark-ai/genoffice/releases/latest)，按平台选择——macOS（Apple Silicon 与 Intel）、Windows（x64 与 Arm）、Linux（deb、rpm、AppImage）。
2. 安装并启动应用（具体安装步骤原文未说明）。
3. 打开或新建文档，在 AI 面板中输入你的编辑需求。
4. 如需从源码构建：原文未提供明确的构建/启动命令，请参考下方 README 正文（材料中仅给出 `package.json` 的 scripts，未说明完整构建流程）。
5. 如需命令行或让编码代理操作文件：应用自带 `genoffice` 命令行，以及面向 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode、Windsurf 的 skill（具体用法原文未说明）。

### 环境要求
- 操作系统：macOS（Apple Silicon 与 Intel）、Windows（x64 与 Arm）、Linux（deb、rpm、AppImage）。
- 硬件：原文未说明具体硬件要求。
- 依赖（仅从源码构建时）：Node.js `>=22.12.0`，npm `>=10`（来自 `package.json` 的 `engines` 字段）。
- 版本要求：项目版本 `0.1.0`。
- 国内网络提示：原文未提及镜像源或加速下载相关内容。

### 常见坑与注意事项
- AI 功能需要密钥或登录：可登录 Genspark 跳过密钥，或自备 Claude、OpenAI、Gemini 等（含任意 OpenAI 兼容端点、本地服务器）的 API Key；只有 AI 调用会离开本机。
- 本地优先：文件打开、编辑、保存、转换（PDF→Word/Excel/PowerPoint、Markdown→Word、HTML→Word）均在本机完成，但 AI 请求会发送到你选择的提供商。
- 从源码构建需注意 Node/npm 版本门槛（Node `>=22.12.0`、npm `>=10`），且 `postinstall` 会执行 `install-electron`。
- 原文未说明其他明显坑点。

---



---

<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="docs/assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="docs/assets/readme/hero.webp" alt="GenOffice — 开源 AI Office 套件：Docs、Sheets、Slides、PDF、Markdown 和 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个功能完备的开源 AI Office 套件。</b><br>
Word、Excel、PowerPoint 和 PDF 文件，由你和你的 AI 共同编辑，以真实格式保存回原文件。</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="License: Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="Latest release"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="Downloads"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub stars"></a>
  <a href="https://x.com/merrickbuilds"><img src="https://img.shields.io/badge/follow-%40merrickbuilds-000000?logo=x&logoColor=white" alt="Follow @merrickbuilds on X"></a>
</p>

<p align="center"><b>English</b> · <a href="docs/i18n/README.es.md">Español</a> · <a href="docs/i18n/README.pt-BR.md">Português (Brasil)</a> · <a href="docs/i18n/README.de.md">Deutsch</a> · <a href="docs/i18n/README.fr.md">Français</a> · <a href="docs/i18n/README.zh-CN.md">简体中文</a> · <a href="docs/i18n/README.zh-TW.md">繁體中文</a> · <a href="docs/i18n/README.ko.md">한국어</a> · <a href="docs/i18n/README.ja.md">日本語</a> · <a href="docs/i18n/README.ar.md">العربية</a> · <a href="docs/i18n/README.ru.md">Русский</a> · <a href="docs/i18n/README.it.md">Italiano</a> · <a href="docs/i18n/README.nl.md">Nederlands</a> · <a href="docs/i18n/README.pl.md">Polski</a> · <a href="docs/i18n/README.cs.md">Čeština</a> · <a href="docs/i18n/README.id.md">Bahasa Indonesia</a> · <a href="docs/i18n/README.ms.md">Bahasa Melayu</a> · <a href="docs/i18n/README.th.md">ไทย</a> · <a href="docs/i18n/README.hi.md">हिन्दी</a> · <a href="docs/i18n/README.he.md">עברית</a></p><!-- lang-switcher · public-hygiene: allow -->

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="https://x.com/merrickbuilds"><b>X</b></a> ·
  <a href="PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是 Microsoft Office 的免费开源替代品，支持 macOS、Windows 和 Linux。它能打开并保存原生 `.docx`、`.xlsx` 和 `.pptx` 文件，编辑 PDF、Markdown 和 HTML，并在每个文档旁配备一个 AI 智能体——不是侧边挂一个聊天框，而是一个能读取文件、执行修改、并精确展示改动内容的编辑器。

- **真实格式，字节级保留。** 只重写你编辑的部分，文件中其余内容逐字节保留，因此文档在 Word、Excel 和 PowerPoint 中依然可用。
- **可审查的 AI。** 编辑以修订和差异形式呈现，支持一键回滚。电子表格使用实时公式，而非粘贴的数值。幻灯片和页面在画布上生成，保持完全可编辑。
- **本地优先设计。** 文件在你的机器上打开、编辑、保存和转换。PDF → Word / Excel / PowerPoint、Markdown → Word 和 HTML → Word 全部在本地运行。只有 AI 调用会离开本机，发送至你选择的提供商。
- **按内容查找文件。** 主屏幕通过本地 SQLite 索引搜索 `.docx`、`.xlsx`、`.pptx`、PDF、Markdown 和 HTML 文件的名称、文件夹和全文，支持中日韩文字。可选地，排名靠前的结果由 **[TypeSafe Jev](https://typesafe.ai/)**（System One 判断模型）重新排序，让能回答你问题的文件排在前面。
- **向文件提问，附带来源。** 收藏一组文档后，主屏幕的 **Ask AI** 可跨文档回答问题，每个论断都标注来源文件，方便你打开核实。
- **用你的密钥，或不用密钥。** 使用 Genspark 登录即可免密钥，或自带 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty、Opper、Cheaper Inference、Atlas Cloud 的密钥，或任何 OpenAI 兼容端点，包括本地服务器。
- **可脚本化，适配智能体。** 应用自带 `genoffice` 命令行和适用于 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 和 Windsurf 的技能，让编码智能体无需打开窗口即可在你机器上创建、转换、读取和编辑真实的 Office 文件。

**获取：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 和 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 和 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详情和要求见[下载](#download)。

## 演示

六个应用，一个 AI 面板，由 TypeSafe Jev 重新排序的文件搜索，从收藏文件带来源回答问题的 Ask AI，以及为编码智能体准备的命令行。每张截图都是 macOS 上的真实应用，AI 由面板中可读的提示词驱动。

### 1 · Docs — 打开并编辑 `.docx`，AI 编辑可审查

<table>
<tr>
<td width="50%"><img src="docs/assets/readme/docs-report.webp" alt="GenOffice Docs 渲染一份双栏年报页面，含全宽封面图、带底纹的 KPI 表格、页眉页脚，80% 缩放，AI 面板已折叠"></td>
<td width="50%"><img src="docs/assets/readme/docs-ai.webp" alt="GenOffice Docs：一份带横幅图的公司概览；AI 精简了 Overview 并插入新的项目符号章节，面板提供一键回滚"></td>
</tr>
<tr>
<td><b>按 Word 的排版打开文件</b> —— 双栏分节、全出血图片、带底纹表格、页眉页脚，基于 Word 行度量分页。样式、批注、修订、公式和墨迹往返后原样保留。</td>
<td><b>直接下达编辑指令</b> —— AI 读取所需区块，重写 Overview 并插入新的项目符号章节。每次 AI 操作都是一个可回滚的快照；开启<b>修订</b>后，编辑以 Word 风格修订呈现。</td>
</tr>
</table>

### 2 · Sheets — `.xlsx` 使用实时公式和图表，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="docs/assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 添加了 Summary 工作表，使用 SUMIF 公式按地区和类别统计收入，并插入柱状图，报告 43 项已应用更改，带撤销按钮"></td>
<td width="50%"><img src="docs/assets/readme/sheets-qa.webp" alt="GenOffice Sheets：询问哪个地区 Q2 收入领先，AI 回答欧洲并给出类别明细，以链接形式引用所用单元格，旁边是 Orders 工作表"></td>
</tr>
<tr>
<td><b>构建</b> —— 一句话即可让智能体添加 Summary 工作表，按地区和类别使用真实的 <code>SUMIF</code>，插入柱状图，并将 43 项更改作为单个可撤销批次应用。</td>
<td><b>提问</b> —— 关于工作簿的问题会返回推理过程和所用确切单元格作为可点击引用。底层：自研 Rust <code>.xlsx</code> 引擎，支持数据透视表、切片器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从提示词到 `.pptx` 演示文稿

<img src="docs/assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资者演示文稿的延时：AI 在面板中规划故事线，幻灯片依次出现在画布上，完成的演示文稿以结尾请求收尾" width="100%">

<table>
<tr>
<td width="50%"><img src="docs/assets/readme/slides-cover.webp" alt="GenOffice Slides：画布上 AI 生成的 Aurora Home 投资者演示文稿封面幻灯片，面板中显示原始一句话提示词和 AI 对构建内容的总结"></td>
<td width="50%"><img src="docs/assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿设计好的结尾幻灯片，左侧是缩略图条，AI 面板总结故事线"></td>
</tr>
<tr>
<td><b>一句话输入</b> —— “为 Aurora Home 创建一份 10 页投资者路演演示文稿……”。GenOffice 规划故事线，研究数据，并将每页幻灯片作为真实 <code>.pptx</code> 起草到画布上。</td>
<td><b>完整演示文稿输出</b> —— 十一页设计好的幻灯片，排版、图像一致，结尾有行动号召；可继续用母版、版式、智能参考线和无损裁剪编辑，或让面板重新设计样式、重写和重排。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，本地将 PDF 转换为 Word

<table>
<tr>
<td width="50%"><img src="docs/assets/readme/pdf-edit.webp" alt="GenOffice PDF：编辑文本模式勾勒页面上的每个文本块以便就地编辑，同时 AI 面板回答关于报告的问题并附页码引用"></td>
<td width="50%"><img src="docs/assets/readme/pdf-convert.webp" alt="GenOffice Docs 显示从 Helios 季度审查 PDF 本地转换的 Word 文档，在原始 PDF 旁边的第二个标签页中打开"></td>
</tr>
<tr>
<td><b>在页面内编辑</b> —— 编辑文本模式勾勒每个文本块以便就地重新输入；内容流通过 PDFium 重写，保留原始字体，而非遮盖注释。向 AI 询问长报告，获得带页码引用的回答。</td>
<td><b>本地转换</b> —— <b>PDF 转换器 → PDF 转 Word</b> 生成可编辑的 <code>.docx</code>，在 Docs 中与源文件并排打开，标题、数据行和段落完好。Excel 和 PowerPoint 目标同理；扫描页通过系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — AI 页面和 UI 构建器，设计简报优先

说明页面的用途和受众。AI 首先提出**设计简报**——钩子、配色、排版和风格方向——然后基于这些设计令牌构建单个自包含的 `.html` 文件。

<img src="docs/assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时：面板中一次 Restyle 请求将深色 Midnight Studio 页面变为温暖的 Solar Daybreak 版本，所有章节和文案保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="docs/assets/readme/html-ai.webp" alt="GenOffice HTML：为太阳能台灯生成的落地页，采用深色 Midnight Studio 方向，在实时预览中显示，AI 面板总结刚构建的页面"></td>
<td width="50%"><img src="docs/assets/readme/html-restyle.webp" alt="同一个 Lumen 落地页被 AI 重新设计为温暖的 Solar Daybreak 方向：纸质背景、衬线标题和橙色点缀，所有章节和文案保留"></td>
</tr>
<tr>
<td><b>一句话生成</b> —— 为 Lumen 生成醒目的主视觉、功能卡片、定价和等候名单表单，采用 Midnight Studio 方向。点击任意元素重新设计样式，双击编辑文本，或切换到 CodeMirror 源码视图。</td>
<td><b>同一设计，全新方向</b> —— 一次 <b>Restyle</b> 请求替换简报的设计令牌，页面随之变化：温暖纸质、编辑衬线、太阳橙点缀，内容不变。全屏演示，或导出为 PDF 或原生可编辑 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="docs/assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由设计师生成的个人仪表盘 UI，采用温暖亚麻风格，含左侧栏、衬线问候语和四张指标卡"></td>
<td width="50%"><img src="docs/assets/readme/html-report.webp" alt="GenOffice HTML：生成的电动汽车市场数据报告，采用大报风格，含衬线报头、1730 万头条数字和数据行"></td>
</tr>
<tr>
<td><b>UI 原型</b> —— “个人仪表盘”模板将人物画像转化为可用布局：左侧栏、问候语、计费工时迷你图、发票和利用率卡片，全是可交给开发者的真实 HTML。</td>
<td><b>数据故事</b> —— “数据报告”模板构建编辑式大报：衬线报头、一个头条数字、分隔线数据行、内联 SVG 图表和方法说明。</td>
</tr>
</table>

### 6 · Markdown — 纯 `.md` 上的块编辑器，带 Ask AI

<table>
<tr>
<td width="50%"><img src="docs/assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中段落显示 Ask AI 弹出框，含输入的指令和建议标签如 Polish、Make more concise、Expand 和 Fix grammar，以及 Send now 和 Add to queue 按钮"></td>
<td width="50%"><img src="docs/assets/readme/markdown-render.webp" alt="GenOffice Markdown 渲染一份发布说明文档，含表格、Mermaid 流程图和任务列表，左侧是 AI 面板的起始提示词"></td>
</tr>
<tr>
<td><b>对选中内容 Ask AI</b> —— 选中任意段落即出现 <b>Ask AI</b> 标签：输入指令或选择建议，立即发送，或排队多个锚定编辑一次性运行。每个应用都有相同入口。</td>
<td><b>渲染显示，保存为纯 Markdown</b> —— Tiptap 块编辑器中的标题、列表、表格、图片、代码块和 Mermaid 图表，写回为纯 <code>.md</code>，并支持完全本地的 <b>Markdown → Word</b> 导出。</td>
</tr>
</table>

### 7 · 搜索 — 找到能回答问题的文件，由 TypeSafe Jev 驱动

工作文件夹中的每个文件都在本地建立索引：Word、Excel、PowerPoint、PDF、Markdown 和 HTML 文件的名称、文件夹和提取文本，存入支持中日韩分词的 SQLite 全文索引。开启 **Jev 搜索重排序**后，本地排名前 20 的结果由 [TypeSafe Jev](https://typesafe.ai/blog/introducing-system-one-models-and-jev) 评判，该 System One 模型在单次调用中为每个文档返回一个校准的相关性分数，而非生成文本。列表按该分数重新排序；若调用失败或超时，保持本地顺序。

<img src="docs/assets/readme/search-jev-motion.webp" alt="GenOffice 主屏幕录屏：输入 laptop refresh policy 时，浏览器缓存策略、品牌刷新计划和仪表盘刷新计划排在前列，设备标准文档排最后；设置页面显示在 AI Media & Search 下开启 Jev 搜索重排序，使用 TypeSafe 端点；同一搜索随后显示设备标准文档排第一，结果计数旁有 Jev 徽章" width="100%">

<table>
<tr>
<td width="50%"><img src="docs/assets/readme/search-jev-before-after.webp" alt="查询 laptop refresh policy 的两组结果并排对比：无 Jev 时仪表盘刷新计划、品牌刷新计划和浏览器缓存刷新策略领先，公司设备标准文档排第五；有 Jev 时说明三年笔记本更换周期的设备标准文档排第一"></td>
<td width="50%"><img src="docs/assets/
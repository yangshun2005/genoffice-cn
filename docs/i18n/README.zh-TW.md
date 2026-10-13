<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 开源 AI 办公套件：Docs、Sheets、Slides、PDF、Markdown 与 HTML，内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首款功能完整的开源 AI 办公套件。</b><br>
Word、Excel、PowerPoint 与 PDF 文件，由你与你的 AI 共同编辑，并以原生格式存回。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="License: Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="Latest release"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="Downloads"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub stars"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <b>繁體中文</b> · <a href="README.ko.md">한국어</a> · <a href="README.ja.md">日本語</a> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>官网</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是一套免费、开源的 Microsoft Office 替代方案，支持 macOS、
Windows 与 Linux。它能打开并保存原生的 `.docx`、`.xlsx` 与 `.pptx`
文件，也能编辑 PDF、Markdown 与 HTML，并在每份文档旁放上一个 AI
代理——不是硬塞在旁边的聊天窗口，而是真正读懂文件、动手修改，
并清楚告诉你它改了哪里的编辑器。

- **原生格式，位元级保留。** 只有你编辑的部分会被重写，文件里其他
  内容都会原样保留，文档在 Word、Excel 与 PowerPoint 中依然能正常工作。
- **AI 的每一步都能查看。** 编辑以修订标记与差异呈现，一键即可撤销。
  电子表格拿到的是实时公式，不是粘贴的数字。幻灯片与页面会直接生成在
  画面上，且完全可再编辑。
- **本地优先的设计。** 文件的打开、编辑、保存与转换都在你的设备上完成。
  PDF → Word / Excel / PowerPoint、Markdown → Word、HTML → Word 全部
  在本地执行。只有 AI 调用会离开这台设备，且仅发送至你选择的服务商。
- **用你自己的密钥，或完全不用。** 用 Genspark 登录即可省去密钥设置，
  或自行带入 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、
  Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty，或任何兼容 OpenAI 接口
  的服务端点，也支持本地服务器。
- **可写成脚本，也随时能交给代理。** 应用内置 `genoffice` 命令行，
  并附上一份给 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、
  OpenCode 与 Windsurf 使用的 agent skill，让程序开发代理无需打开任何
  窗口，就能在你的设备上创建、转换、读取与编辑真正的 Office 文件。

**立即获取：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 与 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 与 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）——
详细内容与系统需求请见[下载](#download)。

## Demo

六款应用，一个 AI 面板，再加上一套给程序开发代理使用的命令行。
每张截图都是在 macOS 上实际操作的真实画面，AI 的动作皆由面板中可见的
提示词驱动。

### 1 · Docs — 打开并编辑 `.docx`，每一步 AI 编辑都能查看

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 呈现一份双栏年度报告页面，含满版封面图片、灰底 KPI 表格、页眉与页脚，缩放 80%，AI 面板收起"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：一份含横幅图片的公司概览；AI 精简了概览段落并插入新的列表区块，面板提供一键撤销"></td>
</tr>
<tr>
<td><b>按 Word 排版方式打开文件</b>——双栏版面、满版出血图片、灰底表格、
页眉页脚，分页按 Word 的行距测量。样式、批注、修订标记、公式与手写
笔迹都能原样往返不受影响。</td>
<td><b>直接说出想要的修改</b>——AI 只读取需要的区块，重写概览段落并插入
新的列表区块。每一次 AI 操作都是可撤销的快照；打开<b>修订标记</b>后，
编辑会以 Word 样式修订呈现。</td>
</tr>
</table>

### 2 · Sheets — `.xlsx` 有实时公式与图表，不是粘贴的数字

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 新增了一张摘要工作表，用 SUMIF 公式按地区与类别统计营收，并加上柱状图，报告应用了 43 项变更并提供撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：询问哪个地区在第二季度营收领先，AI 回答欧洲并附上分类明细，同时将用到的单元格以链接形式引用，旁边是订单工作表"></td>
</tr>
<tr>
<td><b>直接建好</b>——只凭一句话，代理就能新增一张摘要工作表，用真正的
<code>SUMIF</code> 公式按地区与类别统计，插入柱状图，并把 43 项变更
整合成一次可撤销的批量操作。</td>
<td><b>直接询问</b>——对工作簿的提问会附上推理过程，并把实际使用的
单元格做成可点击的引用链接。背后是自研的 Rust `.xlsx` 引擎、数据透视表、
筛选器、条件格式与公式追踪。</td>
</tr>
</table>

### 3 · Slides — 从一句提示词到一份 `.pptx` 幻灯片

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资人演示文稿的延时过程：AI 在面板中规划故事线，幻灯片依次出现在画布上，最终演示文稿以收尾的诉求结束" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：画面上是 AI 生成的 Aurora Home 投资人演示文稿封面幻灯片，附原始的一行提示词与 AI 在面板中对已完成内容的摘要"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿的收尾页设计完成，左侧是缩略图列，AI 面板总结了整份演示文稿的叙事脉络"></td>
</tr>
<tr>
<td><b>只需一句话</b>——「为 Aurora Home 制作一份 10 页的投资人演示文稿……」。
GenOffice 会规划叙事脉络、研究相关数据，并把每一页直接生成在画面上，
成为一份真正的 `.pptx`。</td>
<td><b>拿到的是完整成品</b>——十一页设计完整的幻灯片，字体排版、图像
风格一致，并以行动号召收尾；可继续用母版、版式、智能参考线与
不破坏原图的裁剪功能编辑，或请面板重新设计风格、改写文字、调整顺序。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文字，在本地把 PDF 转成 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：编辑文字模式为页面上每个文字区块画出边框以供就地编辑，同时 AI 面板正在回答一则关于报告的问题并附上页码引用"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 显示由 Helios 季度报告 PDF 在本地转换而成的 Word 文档，于第二个标签页打开，旁边是原始 PDF"></td>
</tr>
<tr>
<td><b>直接在页面内编辑</b>——编辑文字模式为每个文字区块画出边框以供
重新输入；内容流是通过 PDFium 用原始字体重写，而不是覆盖式的批注。
向 AI 询问长篇报告的问题，也能得到附页码引用的回答。</td>
<td><b>在本地完成转换</b>——<b>PDF 转换器 → PDF 转 Word</b> 会产生可
编辑的 `.docx`，在 Docs 中与源文件并排打开，标题、统计行与段落皆完整
保留。Excel 与 PowerPoint 的转换方式相同；扫描页面则交由系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — 先出设计简报，再由 AI 创建网页与界面

说明这个网页是做什么用的、给谁看。AI 会先提出一份**设计简报**——
主打亮点、色板、字体与风格方向——再依这些设计标记建出一个完整
独立的 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时过程：面板中一次 Restyle 请求就把深色的 Midnight Studio 页面变成暖色的 Solar Daybreak 版本，而每个区块与所有文案都保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：以深色 Midnight Studio 风格方向生成的太阳能台灯落地页，画面显示实时预览，AI 面板总结了刚完成的页面"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一份 Lumen 落地页由 AI 重新设计成温暖的 Solar Daybreak 风格方向：纸质背景、衬线标题与橙色强调色，所有版块与文案皆保留"></td>
</tr>
<tr>
<td><b>一句提示词就能生成</b>——为 Lumen 打造的醒目主视觉、功能卡片、
价格方案与候补名单表单，皆以 Midnight Studio 风格方向建成。点击任何
元素即可重新设计样式，双击即可编辑文字，也能切换到 CodeMirror
源码视图。</td>
<td><b>同一份设计，换个方向</b>——一次<b>重新设计</b>请求就会换掉设计简报
的标记，页面随之调整：温暖的纸质、杂志风衬线字体、日落橙强调色，
文案完全不重写。可全屏展示，或导出为 PDF 或原生可编辑的 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由职业设计师生成的个人仪表板界面，采温暖亚麻风格，含左侧导航栏、衬线问候语与四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：以报纸版式生成的电动车市场数据报告，含衬线报头、一项 1730 万的头条数字与一列统计数据"></td>
</tr>
<tr>
<td><b>界面原型</b>——「个人仪表板」模板能把一个角色设定变成可用的
版面：左侧导航栏、问候语、计费工时走势图、发票与使用率卡片，全都是
可以直接交给工程师的真实 HTML。</td>
<td><b>数据叙事</b>——「数据报告」模板会建出一份杂志式报纸版面：衬线
报头、一个头条数字、以分隔线隔开的统计行、内嵌 SVG 图表，以及一段
方法论说明。</td>
</tr>
</table>

### 6 · Markdown — 以区块编辑器编辑纯 `.md`，并内置 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选取一段文字后出现 Ask AI 弹出窗口，内含输入的指令与建议选项，如「润色」「更精简」「扩写」「修正语法」，并附「立即发送」与「加入队列」按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 呈现一份上线公告文档，内含表格、Mermaid 流程图与待办清单，左侧是 AI 面板的起始提示词"></td>
</tr>
<tr>
<td><b>针对选取内容询问 AI</b>——选取任意段落即会出现<b>Ask AI</b>选项：
输入指令或挑选建议，可立即发送，也能把多个定位好的编辑加入队列一次
执行。这个入口在每个应用中都是相同的。</td>
<td><b>渲染显示，仍以纯 Markdown 保存</b>——标题、列表、表格、图片、
代码块与 Mermaid 图表都在 Tiptap 区块编辑器中呈现，存回时仍是
纯 `.md`，并支持完全在本地执行的 <b>Markdown → Word</b> 导出。</td>
</tr>
</table>

### 7 · CLI — 让你的程序开发代理在本地驱动 GenOffice

GenOffice 内置 `genoffice` 命令行与一份 agent skill。安装这份 skill 之后，
Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 或 Windsurf
就能通过与应用程序相同的引擎，创建、转换、读取与编辑真正的 Office 文件，
完全无需打开窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示一份由程序开发代理通过 genoffice 命令行创建的八页太阳系演示文稿：画布上是封面幻灯片，左侧有八张缩略图，AI 面板处于打开状态" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿渲染出的八张幻灯片并排呈现：封面、探索时间线、四个关键数字、行星直径条形图、岩质行星与巨行星的对比、太阳占 99.8% 的主视觉数字、四大巨行星的网格排列与重点整理"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置的「集成」页面：genoffice skill 已安装到 Claude Code，Codex 与 Cursor 旁边显示着「安装」按钮"></td>
</tr>
<tr>
<td><b>对代理下一句提示词</b>——「做一份关于太阳系的八页演示文稿。」代理读取 skill，
写出一份样式表、一份大纲与每张幻灯片各一份的页面规格，用
<code>genoffice image</code> 生成两张照片，再让 <code>genoffice slides check</code>
拦下所有溢出或重叠的内容，最后由 <code>genoffice create</code> 组装出
<code>.pptx</code>，并以 <code>slides render</code> 交回每张幻灯片各一张 PNG
供你查看。</td>
<td><b>在设置 → 集成中一次安装</b>——GenOffice 会列出在这台电脑上找到的
程序开发代理，并把 skill 写入你勾选的每一个。也可以把 skill 下载成 zip
压缩包，或执行 <code>npx skills add genspark-ai/genoffice</code>。命令与完整
工作流程请见<a href="#command-line-and-agent-skill">命令行与 agent skill</a>。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 提供相同的工具
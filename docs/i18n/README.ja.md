<p align="center">
  <a href="https://genoffice.ai/">
    <picture>
      <source srcset="../assets/readme/hero-dark.webp" media="(prefers-color-scheme: dark)">
      <img src="../assets/readme/hero.webp" alt="GenOffice — 开源 AI 办公套件：Docs、Sheets、Slides、PDF、Markdown、HTML 与内置 AI 面板" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">GenOffice</h1>

<p align="center"><b>全球首个功能完备的开源 AI 办公套件。</b><br>
让你和你的 AI 编辑 Word、Excel、PowerPoint、PDF 文件，并以真实文件格式保存。</p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/github/license/genspark-ai/genoffice" alt="License: Apache-2.0"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases/latest"><img src="https://img.shields.io/github/v/release/genspark-ai/genoffice" alt="Latest release"></a>
  <a href="https://github.com/genspark-ai/genoffice/releases"><img src="https://img.shields.io/github/downloads/genspark-ai/genoffice/total" alt="Downloads"></a>
  <a href="https://github.com/genspark-ai/genoffice/stargazers"><img src="https://img.shields.io/github/stars/genspark-ai/genoffice?style=flat" alt="GitHub stars"></a>
</p>

<p align="center"><a href="../../README.md">English</a> · <a href="README.es.md">Español</a> · <a href="README.pt-BR.md">Português (Brasil)</a> · <a href="README.de.md">Deutsch</a> · <a href="README.fr.md">Français</a> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a> · <a href="README.ko.md">한국어</a> · <b>日本語</b> · <a href="README.ar.md">العربية</a> · <a href="README.ru.md">Русский</a> · <a href="README.it.md">Italiano</a> · <a href="README.nl.md">Nederlands</a> · <a href="README.pl.md">Polski</a> · <a href="README.cs.md">Čeština</a> · <a href="README.id.md">Bahasa Indonesia</a> · <a href="README.ms.md">Bahasa Melayu</a> · <a href="README.th.md">ไทย</a> · <a href="README.hi.md">हिन्दी</a> · <a href="README.he.md">עברית</a></p>

<p align="center">
  <a href="#download"><b>下载</b></a> ·
  <a href="#command-line-and-agent-skill"><b>CLI</b></a> ·
  <a href="#mcp-server"><b>MCP</b></a> ·
  <a href="https://genoffice.ai/"><b>网站</b></a> ·
  <a href="https://genoffice.ai/join"><b>社区</b></a> ·
  <a href="../../PRIVACY.md"><b>隐私</b></a>
</p>

GenOffice 是一款免费开源的 Microsoft Office 替代品，支持 macOS、Windows 和 Linux。它既能打开并保存原生 `.docx`、`.xlsx`、`.pptx` 文件，也支持编辑 PDF、Markdown、HTML，并在每个文档旁配备 AI 智能体。它不是生硬附加的聊天框，而是一个能读取文件、做出修改、并准确告诉你改了什么、怎么改的编辑器。

- **真实文件格式，字节级保留。** 只重写被编辑的部分，其余部分在文件内按字节原样保留，因此文档在 Word、Excel、PowerPoint 中依然正常工作。
- **可审查的 AI。** 编辑以修订记录和差异形式呈现，一键即可撤销。电子表格里写入的是真正可用的公式，而非粘贴的数值。幻灯片和页面在画布上生成，可随意继续编辑。
- **本地优先设计。** 文件的打开、编辑、保存、转换全部在你的机器上完成。PDF → Word / Excel / PowerPoint、Markdown → Word、HTML → Word 的转换也全部在设备本地执行。离开机器的只有你选择的 AI 提供商的调用。
- **用不用密钥由你决定。** 登录 Genspark 即可免密钥使用；也可以自带 API 密钥，接入 Claude、OpenAI、Gemini、DeepSeek、Kimi、GLM、Qwen、Doubao、MiniMax、Grok、Mistral、OpenRouter、Requesty，或任意 OpenAI 兼容端点（包括本地服务器）。
- **可脚本化，也能被智能体调用。** 应用内置 `genoffice` 命令行，以及面向 Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode、Windsurf 的技能，让编码智能体无需打开任何窗口，就能在你的机器上创建、转换、读取、编辑真正的 Office 文件。

**获取方式：** [macOS](https://github.com/genspark-ai/genoffice/releases/latest)（Apple Silicon 与 Intel）·
[Windows](https://github.com/genspark-ai/genoffice/releases/latest)（x64 与 Arm）·
[Linux](https://github.com/genspark-ai/genoffice/releases/latest)（deb、rpm、AppImage）—
详见[下载](#download)了解详情与要求。

## 演示

6 个应用、1 个 AI 面板，以及面向编码智能体的命令行。所有截图均在 macOS 上的真实应用中拍摄，AI 由面板中显示的提示词驱动。

### 1 · Docs — 打开 `.docx`，用可审查的 AI 编辑

<table>
<tr>
<td width="50%"><img src="../assets/readme/docs-report.webp" alt="GenOffice Docs 以 80% 缩放显示一份双栏年度报告页面，含全宽封面图、带底纹的 KPI 表、页眉和页脚（AI 面板已折叠）"></td>
<td width="50%"><img src="../assets/readme/docs-ai.webp" alt="GenOffice Docs：带横幅图片的公司简介页面。AI 润色了 Overview 并插入新的项目符号章节，面板中显示可一键撤销的按钮"></td>
</tr>
<tr>
<td><b>以 Word 相同的布局打开文件</b> — 还原双栏分节、无边框图片、带底纹的表格、页眉页脚，以及基于 Word 行度量的分页。样式、批注、修订记录、公式、手写（墨迹）也一并保留。</td>
<td><b>让 AI 编辑</b> — AI 读取所需区块，重写 Overview 并插入新的项目符号章节。AI 的每一轮操作都记录为可回滚的快照；启用<b>修订记录</b>后，编辑会以 Word 格式的修订形式呈现。</td>
</tr>
</table>

### 2 · Sheets — 带真正可用公式和图表的 `.xlsx`，而非粘贴的数值

<table>
<tr>
<td width="50%"><img src="../assets/readme/sheets-ai.webp" alt="GenOffice Sheets：AI 用 SUMIF 公式添加了按地区与类别汇总销售额的 Summary 工作表及柱状图，并显示已应用的 43 项更改和撤销按钮"></td>
<td width="50%"><img src="../assets/readme/sheets-qa.webp" alt="GenOffice Sheets：对于「Q2 销售额最高的地区是哪里？」的提问，AI 回答 Europe，并在 Orders 工作表旁显示按类别的明细及指向所引用单元格的链接"></td>
</tr>
<tr>
<td><b>让 AI 生成</b> — 一句指令，智能体便添加了使用真正 `SUMIF` 公式、按地区与类别汇总的 Summary 工作表，插入柱状图，并将 43 项更改作为一次可撤销的操作应用。</td>
<td><b>向 AI 提问</b> — 关于工作簿的提问会附带推理依据，以及指向实际使用单元格的可点击引用。底层运行着自研的 Rust `.xlsx` 引擎、数据透视表、切片器、条件格式和公式追踪。</td>
</tr>
</table>

### 3 · Slides — 一个提示词生成 `.pptx` 演示文稿

<img src="../assets/readme/slides-generate.webp" alt="GenOffice Slides 生成 Aurora Home 投资人演示文稿的延时过程：AI 在面板中设计故事线，幻灯片在画布上依次出现，完成的演示文稿以收尾的诉求结束" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/slides-cover.webp" alt="GenOffice Slides：AI 生成的 Aurora Home 投资人演示文稿封面幻灯片显示在画布上，面板中显示原始的一行提示词及 AI 创建内容的摘要"></td>
<td width="50%"><img src="../assets/readme/slides-ai.webp" alt="GenOffice Slides：同一份 11 页演示文稿中经过设计的收尾幻灯片。左侧为缩略图列表，AI 面板中显示故事线摘要"></td>
</tr>
<tr>
<td><b>只需输入一行</b> — 「为 Aurora Home 制作一份 10 页的投资人路演演示文稿…」。GenOffice 会搭建故事线、调研数据，并将所有幻灯片作为真正的 `.pptx` 绘制到画布上。</td>
<td><b>得到一份完成的演示文稿</b> — 11 页设计好的幻灯片，拥有统一的排版与图片，以及收尾的行动号召。你可以用母版、版式、智能参考线、非破坏性裁剪继续编辑，也可以让面板修改设计、重写文案、调整顺序。</td>
</tr>
</table>

### 4 · PDF — 就地编辑 PDF 文本，并在设备本地转换为 Word

<table>
<tr>
<td width="50%"><img src="../assets/readme/pdf-edit.webp" alt="GenOffice PDF：文本编辑模式用边框标出页面内所有文本块，支持就地编辑；同时 AI 面板带页码引用回答关于报告的问题"></td>
<td width="50%"><img src="../assets/readme/pdf-convert.webp" alt="GenOffice Docs 在第二个标签页中打开由 Helios 季度回顾 PDF 本地转换而来的 Word 文档，旁边是原始 PDF"></td>
</tr>
<tr>
<td><b>在页面中直接编辑</b> — 文本编辑模式用边框标出每个文本块，可就地改写。它不是覆盖在上面的注释，而是通过 PDFium 直接重写内容流本身，并保留原字体。对于长报告，向 AI 提问会得到带页码引用的回答。</td>
<td><b>设备本地转换</b> — 使用 <b>PDF 转换器 → PDF 转 Word</b>，可生成保留标题、统计行、段落的可编辑 `.docx`，并在 Docs 中打开于原 PDF 旁边。转换为 Excel 或 PowerPoint 同理，扫描页则通过系统 OCR 处理。</td>
</tr>
</table>

### 5 · HTML — 从设计简报出发的 AI 页面／UI 构建器

只需说明页面目的和目标读者。AI 会先提出一份**设计简报**（钩子、配色、排版、风格方向），再依据这些设计令牌组装出单个自包含的 `.html` 文件。

<img src="../assets/readme/html-restyle-motion.webp" alt="GenOffice HTML 重新设计 Lumen 落地页的延时过程：面板中一次 Restyle 请求，将深色的 Midnight Studio 页面变为暖色调的 Solar Daybreak 版本，同时所有区块和文案保持不变" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/html-ai.webp" alt="GenOffice HTML：为 Solar Desk Lamp 生成的深色 Midnight Studio 风格落地页实时预览，AI 面板中显示所创建页面的摘要"></td>
<td width="50%"><img src="../assets/readme/html-restyle.webp" alt="同一个 Lumen 落地页被 AI 重新设计为暖色调的 Solar Daybreak 风格：纸质背景、衬线标题、橙色点缀，同时所有区块和文案保持不变"></td>
</tr>
<tr>
<td><b>一个提示词即可生成</b> — 为 Lumen 构建了大胆的主视觉、功能卡片、价格表、候补名单表单，采用 Midnight Studio 风格。你可以点击任意元素重新设计、双击编辑文本，或切换到 CodeMirror 源码视图。</td>
<td><b>同一设计，只换风格</b> — 只需一次<b>重新设计</b>请求，简报令牌便整体替换，整个页面随之改变：温暖的纸质质感、编辑风格的衬线体、太阳般的橙色点缀。文案不会被重写。你还可以全屏演示，或导出为 PDF 或可编辑的原生 Word 文档。</td>
</tr>
</table>
<table>
<tr>
<td width="50%"><img src="../assets/readme/html-dashboard.webp" alt="GenOffice HTML：为自由设计师生成的暖色亚麻质感个人仪表盘 UI。含左侧栏、衬线问候语、四张指标卡片"></td>
<td width="50%"><img src="../assets/readme/html-report.webp" alt="GenOffice HTML：以宽幅报纸风格生成的 EV 市场数据报告。含衬线报头、17.3 million 的主数字、统计行"></td>
</tr>
<tr>
<td><b>UI 原型</b> — 「personal dashboard」模板将人物设定直接转化为可运行的布局：左侧栏、问候语、可计费时间迷你折线图、账单与利用率卡片。全部是可交给开发者的真实 HTML。</td>
<td><b>数据故事</b> — 「data report」模板组装出编辑风格的宽幅报纸版式：衬线报头、一个主数字、带分隔线的统计行、内联 SVG 图表，以及关于方法的注释。</td>
</tr>
</table>

### 6 · Markdown — 面向纯 `.md` 的块编辑器，带 Ask AI

<table>
<tr>
<td width="50%"><img src="../assets/readme/markdown-ai.webp" alt="GenOffice Markdown：选中段落上显示 Ask AI 弹窗，含已输入的指令、Polish・Make more concise・Expand・Fix grammar 等建议标签，以及「立即发送」和「加入队列」按钮"></td>
<td width="50%"><img src="../assets/readme/markdown-render.webp" alt="GenOffice Markdown 显示一份含表格、Mermaid 流程图、任务列表的发布说明文档，左侧列出 AI 面板的起始提示词"></td>
</tr>
<tr>
<td><b>对选区使用 Ask AI</b> — 选中任意文字都会显示 <b>Ask AI</b> 标签。输入指令或选择建议，可就地发送，也可将多项编辑加入队列后批量执行。所有应用中的操作方式一致。</td>
<td><b>显示丰富，保存为纯 Markdown</b> — 在基于 Tiptap 的块编辑器中处理标题、列表、表格、图片、代码块、Mermaid 图，保存时写回纯 `.md`。<b>Markdown → Word</b> 导出也完全在本地完成。</td>
</tr>
</table>

### 7 · CLI — 编码智能体在你的机器上操作 GenOffice

GenOffice 内置 `genoffice` 命令行和智能体技能。安装技能后，Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode、Windsurf 就能通过与应用相同的引擎创建、转换、读取、编辑真正的 Office 文件，无需打开窗口。

<img src="../assets/readme/cli-deck-in-app.webp" alt="GenOffice Slides 显示由编码智能体通过 genoffice 命令行组装的 8 页太阳系演示文稿：画布上为封面幻灯片，左侧有 8 张缩略图，AI 面板已打开" width="100%">

<table>
<tr>
<td width="50%"><img src="../assets/readme/cli-slides-grid.webp" alt="太阳系演示文稿的 8 张渲染幻灯片并排展示：封面、探索年表、四个关键数字、行星直径柱状图、岩石行星与巨行星对比、太阳占 99.8% 的主数字、四颗巨行星网格、总结"></td>
<td width="50%"><img src="../assets/readme/cli-integrations.webp" alt="GenOffice 设置中的集成页面：genoffice 技能已安装到 Claude Code，Codex 和 Cursor 旁显示安装按钮"></td>
</tr>
<tr>
<td><b>给智能体一个提示词</b> — 「制作一份关于太阳系的 8 页演示文稿」。智能体读取技能，编写样式表、大纲和每页规格，用 `genoffice image` 生成两张图片，让 `genoffice slides check` 拦截溢出或重叠的元素，再用 `genoffice create` 组装 `.pptx`，最后通过 `slides render` 获取每页 PNG 进行核对。</td>
<td><b>在设置 → 集成中安装一次即可</b> — GenOffice 会列出本机上检测到的编码智能体，并向你选择的每个写入技能。你也可以将技能下载为 zip，或运行 `npx skills add genspark-ai/genoffice`。完整的命令与工作流见<a href="#command-line-and-agent-skill">命令行与智能体技能</a>。</td>
</tr>
</table>

### 8 · MCP — 通过 Model Context Protocol 提供同样的工具

`genoffice` 的每条命令同时也是 MCP 工具。Claude Code、Claude
Desktop、Cursor 以及其他任意 MCP 客户端无需安装技能、也无需打开窗口，即可自行启动 `genoffice mcp`，获得 29 个工具，以及以资源形式提供的操作参考。应用内置的另一个 HTTP 服务器，则让你能看着智能体在可见的编辑器标签页中组装 Word
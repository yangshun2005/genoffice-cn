# 从规格设计一套幻灯片

这是 GenOffice 应用生成演示文稿时运行的同一套工作流，但面向的是自己思考、让引擎负责构建的智能体。在应用里，每个阶段是一次独立的模型调用；在这里，每个阶段是一个独立的文件，CLI 会在下一阶段开始前检查每个文件。自上而下工作；绝不要从放置元素开始。

一套幻灯片的文件，放在它们自己的文件夹（`deck/`）里：

| 阶段 | 文件 | 检查 |
| ------------- | ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| 1 样式表 | `deck/style.md` | 每页之前重新读一遍 |
| 2 大纲 | `deck/outline.json` | `genoffice slides check deck/outline.json --json` |
| 3 页面 | `deck/pages/01.json`、`02.json`……每个大纲页一个文件 | 每写完一个后运行 `genoffice slides check deck/pages/NN.json --json`（同时对照大纲条目和样式表） |
| 4 构建 | `deck/deck.pptx` | `genoffice create --type pptx --spec deck/pages --outline deck/outline.json --out deck/deck.pptx --json` |
| 5 质检 | `deck/shots/*.png` | `genoffice slides render`、`genoffice slides audit`、`genoffice slides replace` |

绝不要在一个文件里放超过一页，也绝不要在大纲条目存在之前写页面：构建会拒绝运行，直到每个大纲页都有对应文件；而一次专注地写完一页、面前摆着样式表和该页的简介，正是让一套 20 页幻灯片保持一致的关键。把这三个文件放在一起：`slides check`、`create --spec` 和 `slides replace` 会在页面文件旁边和上一级文件夹里查找 `outline.json` 和 `style.md`，对照每个页面的大纲条目（文件 `NN.json` 对应条目 `pages[N-1]`）和样式表的颜色进行检查，并在任一文件缺失时于 `detail.notes` 中说明。

## 0. 检查机器能做什么

运行一次 `genoffice capabilities --json`。它读取 GenOffice 自身的设置，无需网络调用即可报告是否配置了网页搜索、图片搜索、图片生成和媒体分析（开启云工具的 Genspark 登录，或用户在设置中输入的密钥）。只有当某项功能已配置时，幻灯片才可以使用它；什么都没配置时，就用手头的材料工作，用排版、色块和形状代替照片。绝不要仅仅为了一套幻灯片就让用户去配置密钥。

## 1. 先写样式表（每套幻灯片一份）

在任何内容之前先确定设计系统，写入 `deck/style.md`；每页之前重新读一遍该文件。使用以下结构，填入具体值：

- **背景**：主背景；每种页面类型一个（封面、内容、数据、结尾）。优先遵循明确的基调（深色主题、品牌色），再回退到浅色中性色。内容页共用一个背景。
- **颜色**：正文、主强调色、次强调色、卡片背景、边框，写成 `#RRGGBB` 值。整套幻灯片用一个强调色系统：即使比较多家公司或多个选项，也不要给每个都配自己的颜色。强调色绝不超过两个。页面检查会报告页面使用的、样式表未命名的每一种颜色（`detail.style.offPalette`）；白色和黑色始终允许。
- **字体**：标题字体（若幻灯片混用文字系统，则含拉丁文和 CJK）、正文字体、标题字号范围、正文字号范围。使用目标机器上存在的字体；不确定时，省略 `font`，让引擎的默认值生效。
- **布局库**（每种页面类型至少两个变体）：
  - 封面：`cover_typography_hero`（巨大字体，无图）、`cover_dark_minimal`、`cover_split_color`（60/40 色块）、`cover_full_image_overlay`（照片加深色遮罩）、`cover_magazine`、`cover_split_image`（左文右图）
  - 内容：`left_text_right_image`、`three_column_cards`、`hero_big_number`、`two_column_comparison`、`timeline_horizontal`、`full_image_text_overlay`
  - 数据：`kpi_cards_row`、`chart_with_insight`、`two_by_two_grid`
  - 结尾：`closing_cta`、`closing_thank_you`
- **整体风格**：一句话描述设计语言。

## 2. 大纲，逐页写

写 `deck/outline.json`：

```json
{
  "topic": "…",
  "core_hook": "one sentence with tension, a number or a counter-intuitive contrast",
  "pages": [
    {
      "title": "…",
      "type": "cover | content | data | closing",
      "layout": "one variant from the style sheet's library for that type",
      "brief": "what goes in each region, with the real facts and figures",
      "image_queries": ["English scene query or http(s) URL", "…"]
    }
  ]
}
```

然后运行 `genoffice slides check deck/outline.json --json`：错误（未知布局、内容布局连续重复、占位文案、缺少核心钩子）会以退出码 1 退出，必须在文件中修复；警告是建议。检查强制执行的规则，以及它无法检查的规则：

- 整套幻灯片一个核心钩子：一句话，带张力、一个数字或一个反直觉的对比。
- 一套幻灯片里的内容页不得连续重复同一布局变体，且整套幻灯片应至少使用三种不同变体。
- 根据内容选择变体：三个并列要点 → `three_column_cards`；一个关键数字 → `hero_big_number`；对比 → `two_column_comparison` 或 `two_by_two_grid`；一个序列 → `timeline_horizontal`；指标 → `kpi_cards_row`。
- 不要占位符（"XX%"、"lorem"）：每个数字和名称都来自你手头的材料。配置了网页搜索时，在写页面之前先查好简介所需的事实和数字（`genoffice search "<query>" --json`）。既无材料又无搜索时，告诉用户哪些数字是示意性的；绝不要把编造的数字当作事实呈现。
- 照片：配置了图片搜索时，给每个照片位一个具体场景的英文查询（"harbor cranes at dawn"，而不是 "logistics"），并用 `genoffice search --images "<query>" --max 6 --json` 获取候选；把结果的 `imageUrl` 直接放进页面的图片元素（构建器会下载它），并保留其 `sourceUrl`（图片来自的页面）用于结尾页的署名：`imageUrl` 往往是搜索提供商的代理地址，不说明来源或授权。给图片框大致匹配图片的宽高比；一张竖构图被塞进扁长条里会被居中裁剪成一条细缝，并被 `slides check` 报告。配置了图片生成时，`genoffice image "<prompt>" --aspect 16:9 --out assets/p3.jpg` 会按幻灯片配色生成照片或插图。两者都没有时，就规划不需要照片的页面。

## 3. 写每个页面规格，一次一个文件

对于第 N 页：重新读 `deck/style.md` 和该页的大纲条目，把它的 `image_queries` 解析为文件或 URL，写 `deck/pages/NN.json`（两位数，一个页面对象，见 `genoffice guide slides spec`），在对象顶部回显条目的 `title`、`type` 和 `layout`，然后运行 `genoffice slides check deck/pages/NN.json --json`。它会单独构建该页，返回被丢弃的元素、无法读取的图片和几何审计（越界、文字高于其框、重叠），然后对照大纲条目 N 检查该页（`detail.outline.findings`：回显字段不一致或占位文案是错误，退出码 1；页面文本中缺少标题或计划中的照片没有图片元素是警告），并对照样式表检查（`detail.style.offPalette`）。修复文件，直到 `audit`、`findings` 和 `offPalette` 都为空，再进入第 N+1 页。不要批量处理页面：一步一页、逐页检查，正是关键所在。

画布为 1280 × 720 px，原点在左上角，只用整数；任何元素都不得越过边缘。元素按数组顺序绘制：背景和装饰形状在前，然后图片，文字最后。

**文本框尺寸**（框内边距为零；左上角就是第一个字形开始的地方）：

- 在 `lineSpacingPct` 为 110 时，一行高约 `sizePt × 1.8` px
- 一个 CJK 字符宽约 `sizePt × 1.35` px，一个拉丁字符宽约 `sizePt × 0.7` px
- 文字在框宽处换行：数出换行后的行数，把框做成那么高再加一行备用
- 构建器会重新测量每个纯文本框并增大以适配；它从不缩小，所以过小的框会挤到下方元素里。要正确设置尺寸，而不是依赖这个修正。

**间距**：文字与卡片边缘之间 ≥ 8 px，标题与其副标题之间 ≥ 20 px，堆叠文本块之间 ≥ 5 px。输出前检查每一对。

**字号层级（pt）**：大标题 32 到 48，副标题 18 到 24，正文 12 到 15，主视觉数字最高 80。

**填满页面**：把内容铺满整个画布；不要把内容挤在上半部分、下方留一片空白。让文字和图片尽可能大，只要布局允许。

**视觉元素**：照片只能来自你确实拥有的来源（本地文件、搜索结果、生成的图片）。没有照片时，用排版、色块和形状工作；绝不要用灰框假装照片。类图标装饰使用允许的形状，每页最多四五个，且与内容相关。不要用 emoji。数据可视化由 `rect`、`donut` 和 `line` 形状组合而成，尺寸与真实值成比例。只用纯色（允许 alpha）。

## 4. 反模式（视为缺陷）

- 每张卡片左侧一条细竖强调条、卡片顶部一条色条、标题左侧一条小条。用背景、字重和大小对比来表达层级。
- 彩虹卡片：每个条目一个不同的强调色。
- 装饰性角块或短线；在页面之间到处移动的装饰。
- 每页都是"形状 + 粗体副标题 + 描述"的列表。封面不能只是平淡的标题加副标题：给它一个视觉锚点（一个大色块、一个几何构图、一个巨大数字、一张主视觉图）。
- 每页都带一个含页面标题的整套幻灯片页眉栏。变化构图。
- 相邻卡片的主视觉数字混用不同指标（市场份额挨着价格挨着数量）：一行、一个单位、一个来源。数字的标签必须准确说明来源测量的是什么（骨传导份额不是运动耳机份额）。
- 两行说同一件事：复述图表标题的副标题、重复要点的结论。

## 5. 构建、查看、审计、修复

1. `genoffice create --type pptx --spec deck/pages --outline deck/outline.json --out deck/deck.pptx --json`（当文件就在文件夹旁边时，`--outline` 可以省略）。页面文件按名称顺序读取；当某个大纲页没有文件，或某个页面文件与其条目不一致时，构建会拒绝运行。阅读 `detail.issues`、`detail.imageFailures`、`detail.outline.findings` 和 `detail.style.offPalette`：每一项都会指出页面文件。
2. `genoffice slides render deck/deck.pptx --out deck/shots --json`，查看每一张 PNG（需要安装 GenOffice）。检查溢出、碰撞、对比度、裁剪、层级、留白。
3. `genoffice slides audit deck/deck.pptx --json`，找出眼睛漏掉的几何问题。findings 中的元素 id 就是 `genoffice slides read` 和 `genoffice slides apply` 使用的那些。
4. 在页面的规格文件中修复该页，并用 `genoffice slides replace deck/deck.pptx --slide <n> --spec deck/pages/NN.json --json` 放回去（第 n 张幻灯片就是第 n+1 个页面文件；该页会先对照大纲条目 n 检查）；其他幻灯片不受影响。小的微调也可以通过 `genoffice slides apply` 操作（`setTransform`、`setText`、`setTextStyle`、`setFill`……）完成。最多两轮修复；然后报告剩余问题。

只修复客观缺陷和克制的润色：保留文案、事实、配色和构图。不要重新设计一个已经干净的页面。
# `genoffice create --type pptx --spec` 的幻灯片规格

设计幻灯片路径（`genoffice guide slides design`）保持每页一个文件：

```
deck/pages/01.json   { "title": "The 40% squeeze", "type": "cover", "layout": "cover_typography_hero", "background": "#0E1A2B", "elements": [ ... ] }
deck/pages/02.json   { "title": "Where the margin went", "type": "content", "layout": "three_column_cards", "background": "#FFFFFF", "elements": [ ... ] }
```

`title`、`type` 和 `layout` 与页面的大纲条目对应；构建器忽略它们，检查器则比对它们。`genoffice slides check deck/pages/01.json` 构建并审计单个文件，然后对照 `outline.json` 和 `style.md`（在文件旁边和上一级文件夹查找，或用 `--outline <file>` 指定）进行检查：文件 `NN.json` 对应大纲条目 `pages[N-1]`；对应字段不一致或存在占位文案则退出码为 1，缺少标题或计划中的图片没有对应图像是警告，样式表未命名的颜色会列在 `detail.style.offPalette` 中。`genoffice create --type pptx --spec deck/pages [--outline deck/outline.json] --out deck.pptx` 按名称顺序（`01`、`02`、……`10`）读取文件夹中所有 `*.json`，每个文件生成一张幻灯片，对每个文件运行相同的检查，当页数与大纲不符或某页与其条目不一致时拒绝构建。`genoffice slides replace deck.pptx --slide n --spec deck/pages/NN.json` 在对照条目 n 检查后，从文件重建第 n 张幻灯片。

`--spec` 也接受单个文件包含整个幻灯片集，格式为 `{ "pages": [ {...}, {...} ] }`、纯页面数组或单个页面对象。最多 60 页。每页生成一张 16:9 幻灯片；画布为 **1280 × 720 px**，原点在左上角，所有 `x` `y` `w` `h` 均为整数像素。元素按数组顺序绘制（第一个在最底层）。颜色为 `#RRGGBB` 或 `#RRGGBBAA`（`AA` 为透明度，`00` 为全透明）。

## 大纲

`deck/outline.json` 是页面编写所依据的计划；`genoffice slides check` 会校验它：

```json
{
  "topic": "Regional logistics review 2024",
  "core_hook": "Margins fell 40% while volume grew",
  "pages": [
    {
      "title": "The 40% squeeze",
      "type": "cover",
      "layout": "cover_typography_hero",
      "brief": "Main title, subtitle with the period, presenter line; dark background from the style sheet.",
      "image_queries": []
    },
    {
      "title": "Where the margin went",
      "type": "content",
      "layout": "three_column_cards",
      "brief": "Three cards: fuel +31%, wages +18%, spot rates -22% (2024 vs 2022), one source line each.",
      "image_queries": ["container port cranes at dawn"]
    }
  ]
}
```

`type` 为 `cover`、`content`、`data` 或 `closing`；`layout` 是该类型在设计指南布局库中的某个变体。`image_queries` 为每个图片槽位保存一个英文场景查询或现成的 `http(s)` URL；无图片的页面用 `[]`。检查报出的错误：未知的 type 或 layout、缺少 title、brief、core hook 或 image_queries 条目、占位文案（`XX%`、`lorem`、`TBD`）、content 或 data 布局在连续页面上重复。警告：brief 过于简略、查询非英文、正文页面中布局变体少于三种、首页不是 cover、末页不是 closing 页。

## 元素类型

**Shape**

```json
{
  "type": "shape",
  "shape": "roundRect",
  "x": 80,
  "y": 120,
  "w": 360,
  "h": 200,
  "fill": "#1F3A5F",
  "stroke": { "color": "#FFFFFF", "widthPt": 1 },
  "valign": "middle",
  "paragraphs": [
    { "align": "center", "runs": [{ "text": "Label", "sizePt": 14, "color": "#FFFFFF" }] }
  ]
}
```

`shape` 为 `rect`、`roundRect`、`ellipse`、`triangle`、`rightArrow`、`leftArrow`、`upArrow`、`downArrow`、`chevron`、`diamond`、`parallelogram`、`trapezoid`、`hexagon`、`pentagon`、`pie`、`donut`、`star5`、`heart`、`cloud`、`line`、`lineArrow` 之一。`line` 和 `lineArrow` 绘制其框的对角线，从左上到右下，需要 `stroke`；添加 `"flipV": true` 改为从左下到右上绘制，或 `"flipH": true` 水平镜像；水平分隔线是 `h: 1` 的框。这两个标志可镜像任何形状——带 `"flipH": true` 的 `rightArrow` 指向左侧。形状需要 `fill` 或 `stroke`（或两者）。`paragraphs` 是可选的标签文本，默认垂直居中，除非 `valign` 另有指定。

**Text**

```json
{
  "type": "text",
  "x": 80,
  "y": 60,
  "w": 800,
  "h": 90,
  "valign": "top",
  "paragraphs": [
    {
      "align": "left",
      "lineSpacingPct": 110,
      "spaceAfterPt": 6,
      "bullet": false,
      "runs": [
        {
          "text": "Headline",
          "sizePt": 36,
          "bold": true,
          "color": "#0E1A2B",
          "font": "Helvetica Neue"
        }
      ]
    }
  ]
}
```

Run 字段：`text`（必填）、`sizePt`（6 到 160）、`bold`、`italic`、`color`、`font`。Paragraph 字段：`runs`（必填）、`align`（`left` `center` `right` `justify`）、`lineSpacingPct`（60 到 300）、`spaceBeforePt` 和 `spaceAfterPt`（0 到 96）、`bullet`（true = 带悬挂缩进的 • 项目符号）。一个段落可以混合不同大小、粗细和颜色的 run（大数字 run 旁边是小单位 run）。文本框内边距为零，按宽度换行；构建器会测量每个纯文本框，内容更高时向下扩展（绝不缩小框）。

**Image**

```json
{ "type": "image", "url": "./assets/hero.jpg", "x": 660, "y": 80, "w": 540, "h": 560 }
```

`url` 是本地文件路径（绝对路径，或相对于当前目录再相对于 spec 文件所在文件夹）、`data:` URL，或 genoffice 会下载的 `http(s)` URL。图像居中裁剪以填满其框（object-fit: cover），因此框应大致符合图片的宽高比：保留图片不足一半的框（竖版产品图放在扁平条带中）仍会生成，但会报告为警告。每页最多 8 张图像。无法读取的图像会被丢弃并列入 `detail.imageFailures`。

## 校验

缺少数值几何信息、完全位于画布之外或类型未知的元素会被丢弃并给出警告；超出画布的框会被裁剪到画布内。没有任何文本的文本元素以及没有 fill 或 stroke 的形状会被丢弃。同一页上两个文本完全相同或几乎相同的文本框（副标题重复图表说明）会保留但给出警告，裁剪掉图片一半以上的图像框也是如此。没有任何存活元素的页面会失败；仅当没有任何页面存活时整个幻灯片集才失败。所有被丢弃或警告的内容按页报告在 `detail.issues` 中。每页最多 48 个元素。

## 构建之后

元素获得持久 id（`e_*`），幻灯片获得 `s_<n>`；`genoffice slides read deck.pptx --json` 会列出它们，供后续 `genoffice slides apply` 操作使用。`genoffice slides audit` 使用相同的 id 报告每张幻灯片的越界、文本溢出和重叠；`genoffice slides render` 为每张幻灯片输出一张 PNG 供视觉审查；`genoffice slides replace --slide n --spec <page.json>` 用重建的页面替换一张幻灯片（其元素 id 是新的）。
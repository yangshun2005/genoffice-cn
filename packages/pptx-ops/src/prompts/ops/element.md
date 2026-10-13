# 元素操作

> 修改一个已有元素：填充、描边、位置与大小、裁剪、不透明度、z 轴顺序、分组、形状几何、文本主体属性、效果、超链接、删除。

除非签名另有说明，此处每个操作都接受 `target:{slide, el}`（`flipElements` 和 `groupElements` 接受 `els` 中的列表）。标注为"分组子元素"的操作，当你添加 `group:"<group id>"` 并将子元素 id 放入 `target.el` 时，可接受分组的直接子元素。

几何单位为文档空间 EMU：1 pt = 12700 EMU，在标准 1280 px 宽的幻灯片上 1 px = 9525 EMU（`read_slide` 会报告当前幻灯片的精确换算系数）。除非字段另有说明，角度单位为度。

### deleteElement

`{} — 除 target 外无其他字段`

删除一个顶层元素。要删除分组中的某个成员，请先 `ungroupElement` 该分组（其子元素变为顶层并获得新 id）。

```json
{ "op": "deleteElement", "target": { "slide": 0, "el": "e_SHAPE" } }
```

常见错误

- 直接删除分组子元素：该 id 在顶层无法解析；请先取消分组或删除整个分组。

### setFill

`{fill:"#RRGGBB"|"none"|{stops:[{pos,color}],angle?}}`

文本框或形状的纯色、半透明或渐变填充。图片、表格、图表和连接线没有填充。图片填充为 `setImageFill`（仅 UI）。

| 字段        | 类型                                                                      | 说明                                                       |
| ----------- | ------------------------------------------------------------------------- | ---------------------------------------------------------- |
| fill        | `"none"`、`"#RRGGBB"`、`"#RRGGBBAA"` 或 `{stops, angle?, radial?, path?}` | Alpha 字节 `AA`：00 透明 .. FF 不透明                      |
| fill.stops  | `{pos, color}` 数组                                                       | 至少两个；`pos` 0..1                                       |
| fill.angle  | number                                                                    | 线性渐变角度，单位为 1/60000 度（90 度 = 5400000）         |
| fill.radial | boolean                                                                   | 使用径向渐变而非线性渐变                                   |
| group       | string                                                                    | 仅用于分组的直接子元素                                     |

```json
{ "op": "setFill", "target": { "slide": 0, "el": "e_SHAPE" }, "fill": "#1A73E8" }
```

```json
{
  "op": "setFill",
  "target": { "slide": 0, "el": "e_SHAPE" },
  "fill": {
    "stops": [
      { "pos": 0, "color": "#1A73E8" },
      { "pos": 1, "color": "#FFFFFF" }
    ],
    "angle": 5400000
  }
}
```

常见错误

- 用 `null` 移除填充：应使用 `"none"`。
- 渐变只有一个色标：至少需要两个色标。
- 以图片为目标：请改用 `setPictureOpacity` / `setImageFill`。

相关：`setStroke`、`setBackground`（页面背景，属于幻灯片操作）。

### setStroke

`{stroke:{color:"#RRGGBB",widthEmu}|null} — null 移除轮廓`

文本框、形状或图片的轮廓（图片边框）。

| 字段            | 类型                                                        | 说明                                                           |
| --------------- | ----------------------------------------------------------- | -------------------------------------------------------------- |
| stroke          | object 或 `null`                                            | `null` 移除轮廓                                                |
| stroke.color    | `"#RRGGBB"`                                                 | stroke 为对象时必填                                            |
| stroke.widthEmu | number > 0                                                  | 12700 EMU = 1 pt                                               |
| stroke.dash     | string                                                      | 预设虚线名称（`"dash"`、`"sysDot"` 等）；`"solid"` 清除        |
| stroke.cap      | `"flat"` / `"rnd"` / `"sq"`                                 | 可选                                                           |
| stroke.compound | `"sng"` / `"dbl"` / `"thickThin"` / `"thinThick"` / `"tri"` | 可选                                                           |
| stroke.join     | `"round"` / `"bevel"` / `"miter"`                           | 可选                                                           |
| stroke.gradient | `{stops:[{pos,color}], angle}`                              | 渐变线条；角度单位为 1/60000 度                                |
| group           | string                                                      | 仅用于分组的直接子元素                                         |

```json
{
  "op": "setStroke",
  "target": { "slide": 0, "el": "e_SHAPE" },
  "stroke": { "color": "#333333", "widthEmu": 19050 }
}
```

```json
{ "op": "setStroke", "target": { "slide": 0, "el": "e_PICTURE" }, "stroke": null }
```

常见错误

- 宽度用点：`widthEmu` 是 EMU；将点数乘以 12700。
- 使用 `remove:true` 或 `"none"`：通过传入 `stroke: null` 移除轮廓。

### setTransform

`{box:{x,y,cx,cy},rotDeg?}（分组子元素：用 absBox 代替 box，并加上 group:"<group id>"）`

移动、调整大小和旋转元素。`box` 是完整的 EMU 新框架；即使只改一个值也要传入全部四个数字（从 `read_slide` 或 `execute_slide_script` 的 `els` 条目读取当前值）。

| 字段            | 类型                 | 说明                                                                       |
| --------------- | -------------------- | -------------------------------------------------------------------------- |
| box             | `{x, y, cx, cy}` EMU | 顶层元素必填                                                               |
| rotDeg          | number               | 顺时针度数；省略 = 0                                                       |
| absBox          | `{x, y, cx, cy}` EMU | 仅分组子元素：文档空间框架（操作会转换为子元素空间）                       |
| group           | string               | 仅分组子元素                                                               |
| resizeTableGrid | boolean              | 仅表格：将列/行重新分配到新框架                                            |

```json
{
  "op": "setTransform",
  "target": { "slide": 0, "el": "e_TEXT" },
  "box": { "x": 914400, "y": 685800, "cx": 7315200, "cy": 1143000 }
}
```

```json
{
  "op": "setTransform",
  "target": { "slide": 0, "el": "e_CHILD" },
  "group": "e_GROUP",
  "absBox": { "x": 1828800, "y": 1828800, "cx": 1828800, "cy": 914400 },
  "rotDeg": 15
}
```

常见错误

- `box` 中使用像素值：请用 `read_slide` 中的 px 转 EMU 系数换算。
- 只传 `cx`/`cy`：矩形必须携带 x、y、cx、cy 全部四个值。
- 对多个元素做相对运算（对齐、分布）时，优先使用 `execute_slide_script`，它会基于实时几何计算。

### setConnectorEndpoints

`{p1:{x,y},p2:{x,y},start?:{targetId,idx}|null,end?:{targetId,idx}|null}`

重新规划连接线在两点之间的路径，并可选地将其端点附加到形状上，使其跟随后续移动。该元素必须是连接线（直线、箭头、肘形或曲线连接线）。

| 字段       | 类型                                 | 说明                                                                                                  |
| ---------- | ------------------------------------ | ----------------------------------------------------------------------------------------------------- |
| p1, p2     | `{x, y}` EMU                         | 必填；框架和翻转由它们推导                                                                            |
| start, end | `{targetId, idx}`、`null` 或省略     | 附加到元素的连接点 `idx`；`null` 分离；省略则保持当前附加状态                                          |

```json
{
  "op": "setConnectorEndpoints",
  "target": { "slide": 0, "el": "e_LINE" },
  "p1": { "x": 914400, "y": 914400 },
  "p2": { "x": 3657600, "y": 2743200 },
  "start": { "targetId": "e_SHAPE", "idx": 3 },
  "end": null
}
```

常见错误

- 用于普通形状：只接受连接线；形状请使用 `setTransform`。
- `targetId` 不在幻灯片上：操作会失败而非静默分离；传入 `null` 以分离。

### flipElements

`{els:[id,…],axis:"h"|"v"} — 不使用 target.el`

围绕元素自身中心水平或垂直镜像一个或多个元素。任何带框架的元素都可翻转（形状、文本框、图片、分组）。

| 字段  | 类型           | 说明                                             |
| ----- | -------------- | ------------------------------------------------ |
| els   | string[]       | `target.slide` 上元素 id 的非空列表              |
| axis  | `"h"` 或 `"v"` |                                                  |
| group | string         | 可选：改为翻转该分组内的子元素                   |

```json
{ "op": "flipElements", "target": { "slide": 0 }, "els": ["e_SHAPE", "e_PICTURE"], "axis": "h" }
```

### setPictureSrcRect

`{srcRect:{l,t,r,b}|null} — 裁剪比例 0..1，null 移除裁剪`

图片的非破坏性裁剪：每一侧是从该边缘移除的源图比例。框架保持不变；剩余图像拉伸以填满框架。可选地传入 `box` 在同一操作中缩小框架。

| 字段    | 类型                         | 说明                                                                       |
| ------- | ---------------------------- | -------------------------------------------------------------------------- |
| srcRect | `{l?, t?, r?, b?}` 或 `null` | 每个 0..1（不含 1）；`l + r < 1` 且 `t + b < 1`；缺失的边 = 0              |
| box     | `{x, y, cx, cy}` EMU         | 可选，与裁剪一起应用的新框架                                               |

```json
{
  "op": "setPictureSrcRect",
  "target": { "slide": 0, "el": "e_PICTURE" },
  "srcRect": { "l": 0.1, "t": 0, "r": 0.1, "b": 0.2 }
}
```

```json
{ "op": "setPictureSrcRect", "target": { "slide": 0, "el": "e_PICTURE" }, "srcRect": null }
```

常见错误

- 使用百分比如 10：比例是 0..1，所以 10% 是 0.1。
- 相对两侧的裁剪之和达到或超过 1：将没有可见内容。

### setRedaction

`{label: string|null}`

对模型隐藏图片、视频或音频形状，或停止隐藏。`label` 是模型代替该形状看到的唯一名称；`null` 清除它并保持形状原样。

读者借此隐藏不得披露的图片，同时模型仍可围绕它布局幻灯片。形状本身不受影响——不删除任何字节，文件在任何地方都能打开。

文本的隐藏方式不同，通过文本编辑界面进行，它标记选区下的文本段而非元素。此操作仅接受图片。

```json
{ "op": "setRedaction", "target": { "slide": 0, "el": "e_PICTURE" }, "label": "company logo" }
```

```json
{ "op": "setRedaction", "target": { "slide": 0, "el": "e_PICTURE" }, "label": null }
```

### setPictureOpacity

`{opacity:0..1}`

图片的整体透明度。`1` 为完全不透明并移除该效果。

```json
{ "op": "setPictureOpacity", "target": { "slide": 0, "el": "e_PICTURE" }, "opacity": 0.6 }
```

常见错误

- 使用百分比值：60% 是 `0.6`。
- 非图片目标：形状通过 `setFill` 配合 `"#RRGGBBAA"` 颜色实现半透明。

### reorderElement

`{dir:"front"|"back"|"forward"|"backward"}`

更改元素在其幻灯片上的 z 轴顺序（堆叠顺序）。

```json
{ "op": "reorderElement", "target": { "slide": 0, "el": "e_SHAPE" }, "dir": "back" }
```

常见错误

- 对已处于该极端的元素重复 `front`/`back` 会失败；请先检查大纲顺序。

### groupElements

`{els:[id,id,…]} — 至少两个 id；不使用 target.el`

将两个或更多顶层元素分组。结果在 `created` 中报告新分组 id；子元素可通过 `group:"<group id>"` 保持可编辑。

```json
{ "op": "groupElements", "target": { "slide": 0 }, "els": ["e_SHAPE", "e_TEXT"] }
```

### ungroupElement

`{} — target.el 是分组`

解散分组；其直接子元素变为顶层元素并获得新 id（位置保留）。编辑它们之前请重新读取幻灯片。

```json
{ "op": "ungroupElement", "target": { "slide": 0, "el": "e_GROUP" } }
```

### setShapeGeometry

`{prst:"<OOXML preset geometry name>"}`

替换形状的预设几何（例如将 `rect` 改为 `roundRect`、`ellipse`、`triangle`、`rightArrow`、`chevron`、`star5`、`hexagon`）。文本、填充、描边和框架保持不变。

```json
{ "op": "setShapeGeometry", "target": { "slide": 0, "el": "e_SHAPE" }, "prst": "hexagon" }
```

常见错误

- 应用于图片、表格或图表：只有带预设几何的形状才符合条件。

### setShapeAdjust

`{adjust:{<gdName>:number,…}} — 预设几何 avLst 值（分组子元素：加上 group）`

设置预设几何的调整手柄，例如圆角矩形的圆角半径（`adj`，0..50000）或箭头头部比例（`adj1`、`adj2`）。

```json
{ "op": "setShapeAdjust", "target": { "slide": 0, "el": "e_SHAPE" }, "adjust": { "adj": 16667 } }
```

常见错误

- 使用 0.25 这样的分数：调整值是原始 avLst 数字（大多数预设中范围的 25% 是 25000）。

### setShapeCustomGeometry

`{path:{w,h,cmds:[{op:"M"|"L"|"C"|"Q"|"Z",pts:[…]}]}} — 用自由路径替换形状几何（分组子元素：加上 group）`

将形状变为自由形状（PowerPoint 的"编辑顶点"）：预设或先前的自定义几何被一条闭合或开放路径替换。`w`/`h` 设置路径坐标空间，通常等于元素的 `cx`/`cy`（EMU），这样 `pts` 就是元素框内的 EMU。第一个命令必须是 `M`；`pts` 对 `M`/`L` 包含 2 个数字，对 `Q` 包含 4 个，对 `C` 包含 6 个，对 `Z` 无。填充、线条、文本和效果保留。

```json
{
  "op": "setShapeCustomGeometry",
  "target": { "slide": 0, "el": "e_SHAPE" },
  "path": {
    "w": 1828800,
    "h": 914400,
    "cmds": [
      { "op": "M", "pts": [0, 914400] },
      { "op": "L", "pts": [914400, 0] },
      { "op": "L", "pts": [1828800, 914400] },
      { "op": "Z", "pts": [] }
    ]
  }
}
```

常见错误

- 图片、表格、图表和连接线：只有文本框和形状接受路径。
- 点超出 0..w / 0..h 会绘制到元素框外（允许，但选择框仍为元素框）。

### setTextAnchor

`{anchor:"top"|"middle"|"bottom"}`

文本在其框内的垂直对齐。

```json
{ "op": "setTextAnchor", "target": { "slide": 0, "el": "e_TEXT" }, "anchor": "middle" }
```

### setTextBodyProps

`{props:{vert?:"horz"|"eaVert"|"vert"|"vert270"|"wordArtVert",autofit?:"none"|"shrink"|"resize",insets?:{l?,t?,r?,b?} (EMU),wrap?:boolean}}`

文本主体属性：书写方向、自动调整行为、内部边距和自动换行。至少传入一个属性。

| 字段          | 类型                                                             | 说明                                                            |
| ------------- | ---------------------------------------------------------------- | --------------------------------------------------------------- |
| props.vert    | `"horz"` / `"eaVert"` / `"vert"` / `"vert270"` / `"wordArtVert"` | `"horz"` 清除竖排文本                                           |
| props.autofit | `"none"
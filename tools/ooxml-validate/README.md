# ooxml-validate

`.pptx` 输出的 Schema 校验门。`validate-pptx.mjs` 将每个
PresentationML / DrawingML 部件经 Markup Compatibility 预处理后，
用 `xmllint` 对照 `schemas/` 中的 ISO/IEC 29500-4（Transitional）
XML Schema 进行校验。

格式良好性检查和 python-pptx 看不到 `a:rPr` 中的第二个填充子元素、
`a:effectLst` 之后的 `a:ln`，或 `sz="50"`；PowerPoint 能看到，并弹出修复
提示，丢弃形状。本工具也能看到。

```bash
node tools/ooxml-validate/validate-pptx.mjs deck.pptx                 # absolute
node tools/ooxml-validate/validate-pptx.mjs --base original.pptx edited.pptx   # only what the edit introduced
node tools/ooxml-validate/validate-pptx.mjs --json ...                # machine-readable
```

需要 `xmllint`（macOS 自带；Debian/Ubuntu：`libxml2-utils`）。

使用方：`packages/pptx-engine/tests/ooxml-schema.test.ts`（引擎输出
必须通过校验；fixture 编辑不得新增违规）和
`packages/pptx-engine/tests/corpus-edit-fuzz.test.ts`，后者以 `--base`
运行，这样外部 deck 的既有问题不会算到本次编辑头上。

## Schema

`schemas/*.xsd` 是 ISO/IEC 29500-4:2016 Transitional Schema（与
ECMA-376 Part 4 相同），取自 python-docx 的 `ref/xsd` 目录。仅保留
PresentationML 闭包：`pml`、`dml-main`、`dml-chart`、
`dml-chartDrawing`、`dml-diagram`、`dml-lockedCanvas`、`dml-picture`、
`shared-commonSimpleTypes`、`shared-relationshipReference`。

本地修订（文件中标记为 `GenOffice amendment`）：

- `dml-main.xsd` 的 `CT_TextBulletSizePercent/@val` 绑定到 `ST_TextBulletSize`
  （包含 25000..400000 十进制形式的联合类型）。已发布的
  Schema 仅将其绑定到百分比字符串形式，会拒绝 PowerPoint 写入的每个
  `a:buSzPct`。

校准：41 个 PowerPoint 制作的 deck（内置主题和版式）
校验通过；对它们的编辑副本相比原始版本不新增违规。

## MCE 预处理

不将任何扩展命名空间视为已理解：`mc:Ignorable` 命名空间中的
属性和元素被丢弃，每个 `mc:AlternateContent` 折叠为其 `mc:Fallback`，
`mc:*` 属性被移除。`a:ext` / `p:ext` 中的扩展载荷在 Schema 中为 `lax`，
原样通过。
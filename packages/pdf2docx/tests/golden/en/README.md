# en — 拉丁语系黄金用例

目标覆盖范围：自适应词间距阈值（紧凑/宽松字距、大字号）、行尾连字符连接、左/居中/右对齐、首行缩进。将 pdf2docx issue #103（丢失/多余词间距）移植为 `issue-103-*`。

P3 布局用例（测试夹具由 `tests/helpers/fixtures.ts` 动态生成，在 `tests/integration.test.ts` 中进行端到端断言）：

- `buildStreamTablePdf` — 无边框三线（booktabs）表格：3 行对齐的行仅由水平线框定 → 必须转换为真正的 docx 表格。
- `buildTwoColumnPdf` — 两个均衡的文本列 → w:cols 节，左列先于右列读取；绝不能检测为表格（pdf2docx issue #136，"假表格"失败）。
- `buildSpacedPdf` — 标题位置较低，上下有大片空白 → before_space 链将其恢复为段落 spacingBefore。
- 流检测器的负向用例族（普通段落、诗歌、目录点线引导、代码块、无横线的 2 行标签/值对）位于 `tests/stream.test.ts` — 将未来上游误报报告移植到此处作为 `issue-<n>-*` 用例。
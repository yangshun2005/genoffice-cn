# ar — 阿拉伯语黄金测试用例

P2 状态：RTL 页面不再降级为位图。该流水线覆盖了 pdf2docx issue #73（整串反转）、RTL 文本中数字串的方向、呈现形式 NFKC 折叠以及括号镜像——由 `tests/rtl.test.ts`（单元测试，手工构建的视觉顺序字符）以及 `tests/integration.test.ts` 中的 `integration: ar/he RTL` describe（通过 PDFium 使用系统字体进行端到端测试）进行断言。

目前尚未提交任何 PDF 二进制文件：生成一个 PDF 需要嵌入支持阿拉伯语的字体，而本地可用的字体（macOS Arial Unicode）不适合再分发。因此，端到端测试用例会即时构建其测试夹具，并在不存在合适系统字体时跳过。一旦将自由许可的阿拉伯语字体（例如 Amiri、SIL OFL）添加到夹具工具链中，就可以在此处放置一个已提交的示例。
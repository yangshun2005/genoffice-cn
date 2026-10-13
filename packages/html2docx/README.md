# @genoffice/html2docx

HTML → DOCX 转换，用于 HTML 应用的"导出为 Word"：页面在真实浏览器中渲染，归约为文档意图树（标题、段落、列表、表格、卡片、KPI 行、表单字段、页面背景……），再用 `docx` 库写出为原生 OOXML。只有 Word 无法对应的视觉元素（图表、图标、装饰框）才截图。

流水线、IR 和 OOXML 映射见 [ARCHITECTURE.md](./ARCHITECTURE.md)。

## 用法

```ts
import { convertHtmlToDocx } from '@genoffice/html2docx'

const { docx, stats } = await convertHtmlToDocx({ url }, driver, {
  onProgress: ({ stage, pct }) => …,   // load | extract | screenshot | generate
  signal,                               // AbortSignal
})
```

`driver` 是一个 `BrowserDriver`（`src/driver.ts`）：宿主拥有浏览器，并提供类页面适配器。`src/drivers/playwright.ts` 基于 playwright-core 和本地安装的 Chrome 实现它，供测试和 CLI 使用；应用则提供 Electron `webContents` 实现。转换器从不关闭 driver。

CLI（单文件，需要 Chrome；`CHROME_PATH` 可覆盖查找路径）：

```bash
npx tsx packages/html2docx/tools/cli.ts input.html output.docx --verbose
```

## 目录结构

- `src/browser/` — 页面内代码，纯 JS 原样保留：`core/*.js` 是一个 `extractIR()` 函数体的切片（在 `src/extract.ts` 中通过 `?raw` 导入组装），其余文件安装 `__html2docx*` 辅助全局变量。
- `src/convert.ts` — 编排：视口/作者宽度检测、图片懒加载预热、提取器注入、元素截图、生成。
- `src/generate/` — IR → OOXML（`docx` 库）。
- `tests/features.test.ts` — 66 个端到端用例，每个都在 Chrome 中渲染。

生成层从无类型的 CommonJS 移植而来，使用 `strict: false`；类型正逐文件收紧，不改动逻辑。
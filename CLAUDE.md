# CLAUDE.md

为在本仓库中工作的 AI 代理和人类贡献者提供指导。

## 主题规则（强制）

本套件支持浅色 / 深色 / 跟随系统三种 UI 主题。切换机制是 `<html>` 上的 `data-theme` 属性，加上在 `packages/ui/src/tokens.css` 中一次性定义的 CSS 自定义属性（浅色默认值在 `:root`，覆盖值在 `[data-theme='dark']`，跟随系统模式则由 `prefers-color-scheme` 媒体查询兜底）。

1. **UI 界面颜色必须使用语义化 token。** 绝不要在渲染器 CSS 规则或界面相关的内联样式中写裸 `#hex` / `rgb()` —— 应引用 `packages/ui/src/tokens.css` 中的 `var(--surface)`、`var(--text)`、`var(--hover)` 等。原始值只允许出现在自定义属性定义行（`--x: #...;` —— token、强调色或应用级变量定义）。CI 会对新增/变更的渲染器 CSS 行强制执行此规则（`tools/check-theme-colors.mjs`）。
2. **每个新 token 都要给出全部三种值。** 新增 token 意味着要在 `tokens.css` 的三个块中都添加（浅色、深色、跟随系统的深色兜底）。
3. **强调色按应用各自定义。** 每个应用在自己的 `styles.css` 中定义 `--accent` / `--accent-dark` / `--accent-soft`（及其深色调整值）。共享规则引用 `var(--accent)`，从而继承应用的品牌色。
4. **文档内容绝不由主题重新生成。** 页面表面、单元格填充、幻灯片内容、PDF 页面位图、导出/打印样式表、图表调色板、高亮色映射、图章和艺术字预设都属于文档数据：它们保持硬编码，不得引用界面 token，且每条保存/导出/打印路径在两种主题下都必须产出完全相同的输出。Word/Excel 风格的 _深色页面_（Sheets 通过 Univer 的 `darkMode`，Docs 通过 `apps/docs/src/renderer/editor/dark-page.ts`）仅是显示时的重映射：作者设定的颜色仍是真实声明，重映射的副本只存在于仅屏幕显示的 `--dk-*` / `.page-dark` 层中，打印/导出永远看不到它。
5. **Canvas 绘制的 UI 元素须走常量表。** Konva/canvas 编辑界面元素（选区框、参考线、控制柄）从应用的 canvas 颜色表（如 `canvas-colors.ts`）按当前主题读取 —— 绘制调用中不得内联 hex。

## 构建陷阱

- 应用主进程代码（`apps/*/src/main`）会被编译进 **shell** 构建。改动后需重新构建 shell，否则改动会静默不生效。
- 开发模式下，preload 改动需要重新构建 —— 过期的 preload 会导致渲染器白屏。
- 应用 `dependencies` 中列出的工作区包，也必须加入 `externalizeDepsPlugin` 的 `exclude` 列表，否则打包后的应用启动时会崩溃。
- `useI18n()` 的 `t` 引用不稳定；绝不要把它放进 Hook 依赖数组。应存储 key，在渲染时再翻译。

## UI 字符串（i18n）

- 大型字典按语言分片：`i18n/strings-<domain>.ts` 是对 `i18n/<domain>/<lang>.ts` 的薄聚合层（每种语言一个文件，`zh` 定义 key 集合）。新增 key 时要在 `zh.ts` 和每个同级分片中都添加；每个分片上的 `satisfies Record<keyof typeof zh, string>` 会把缺失或多余的 key 变成类型错误。绝不要把聚合层重新膨胀回单个 19 语言的对象。
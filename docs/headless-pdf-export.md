# 无头 PDF 导出

GenOffice 中每条"导出为 PDF"的路径都可以在没有可见编辑器窗口的情况下驱动，统一走一个入口：

```
<app binary> --headless-export <input-file> --to pdf --out <path> [--json]
```

应用不创建可见窗口，隐藏 macOS Dock 图标，向 stdout 写入恰好一行后退出。它**不**获取单实例锁，因此可与 GUI 实例并行运行。

```
$ GenOffice --headless-export report.docx --to pdf --out report.pdf --json
{"status":"ok","summary":"Exported /w/report.docx to /w/report.pdf","output_path":"/w/report.pdf"}
```

不加 `--json` 时，同一行输出为纯文本句子。`--flag value` 和 `--flag=value` 两种写法均受支持。

## 退出码

| 代码 | 含义                                                                       |
| ---- | -------------------------------------------------------------------------- |
| 0    | PDF 已写入                                                                 |
| 1    | 参数错误（缺少 `--out`、目标不是 `pdf`、无输出目录）                       |
| 2    | 输入文件问题（不存在、不是文件、扩展名无模块可渲染）                       |
| 3    | 转换失败（文档无法读取、渲染器崩溃、超时）                                 |

失败时 JSON 信封为
`{"status":"error","summary":…,"error":…}` —— 单行，换行符已折叠。

## 支持的输入

| 扩展名                        | 模块     |
| ----------------------------- | -------- |
| `.docx`                       | docs     |
| `.xlsx` `.xlsm` `.xls` `.csv` | sheets   |
| `.pptx`                       | slides   |
| `.md` `.markdown`             | markdown |
| `.html` `.htm`                | html     |

## 工作原理

语法、退出码和渲染器侧的等待辅助函数位于
`packages/electron-utils/src/headless-export.ts`；渲染器部分通过
`@genoffice/electron-utils/headless-export` 子路径导入，因此渲染器 bundle 永远不会引入 `node:` 内置模块。

`apps/shell/src/main/headless-export.ts` 校验路径，并按扩展名路由到每个模块对应的隐藏窗口导出器
（`exportDocsPdfHeadless`、`exportSheetsPdfHeadless`……）。每个导出器：

1. 创建一个 `show: false` 的 BrowserWindow，使用该模块常规的 preload、sandbox 和 `backgroundThrottling: false`；
2. 通过模块现有的待打开路径排队输入，使渲染器运行其常规加载流水线；
3. 让渲染器等待文档稳定（docs：分页切片数量连续两次不变；slides：所有图片解码完成且私有 Office 字体注册完毕；sheets：工作簿完全预加载），然后调用**与文件菜单相同的导出函数**，用 CLI 的路径替代保存对话框；
4. 在渲染器报告后 resolve，并销毁窗口。

每个模块只有一个导出函数——GUI 不传路径并弹出对话框，无头模式传路径且不弹——因此 GUI 与 CLI 的输出不会产生偏差。在四份文档上实测，两条路径产出的 PDF 仅嵌入的创建时间戳不同。

`isHeadlessMode()`（`packages/electron-utils/src/headless-mode.ts`）在任何编辑器模块启动前设置；它抑制成功写入后所有会弹出 UI 的行为（在标签页中打开导出文件、在文件管理器中显示），以及 slides 的最近文件记录。

## 值得了解的行为

- **无法读取的输入是错误，不是空白页。** docs 和 slides 对损坏文件会返回一个无标题空白文档；无头模式将"文档已挂载但并非来自磁盘"视为退出码 3。
- **受密码保护的文档**无法在没有用户的情况下处理，因此会在就绪超时后失败，而非立即失败。
- **大型工作簿**通常需等待用户点击"完全加载"后才允许 PDF 导出。无头模式自行完成该调用。
- **电子表格仅导出活动工作表**，与 GUI 完全一致。
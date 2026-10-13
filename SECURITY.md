# 安全策略

## 报告漏洞

请通过本仓库的 GitHub [私密漏洞报告](https://github.com/genspark-ai/genoffice/security/advisories/new)私下报告疑似漏洞。不要为安全报告创建公开 Issue。我们会在 72 小时内确认收到报告。

## 进程安全态势

所有应用窗口均运行在完整的 Electron 渲染进程锁定模式下：

- 每个文档窗口和标签页视图（docs、sheets、slides、pdf、markdown、shell、updater）均启用 `contextIsolation: true`、`nodeIntegration: false`、`sandbox: true`。
- 渲染进程只能通过类型化、经过校验的 IPC 通道访问主进程（载荷在主进程中做 Schema 校验；sheets 全程使用 zod）。
- 每次 `shell.openExternal` 调用都经过统一的共享网关（`@genoffice/electron-utils` → `safeExternalUrl`），该网关解析 URL 并强制执行协议白名单（http/https；pdf 链接注释额外允许 mailto）。`file:`、`javascript:` 和自定义协议一律拒绝。
- 没有硬编码的 API 密钥。AI 请求默认通过已登录账户代理；用户提供的密钥保存在操作系统级设置存储中。

## 威胁模型：AI 生成的布局脚本（slides）

slides AI 可以通过生成一小段脚本来调整幻灯片布局，该脚本由 Acorn 解析，并由受限的 AST 解释器执行（`apps/slides/src/renderer/ai/layout-script-interpreter.ts`）。源码看起来像 JavaScript 的一个小型同步子集，以便兼容模型，但它不会作为可执行源码传给 `eval`、`Function`、VM 上下文、worker 或 JavaScript 引擎。

**脚本按设计能做的事：** 读取 `els`/`canvas` 的无原型 JSON 副本，执行有界算术/控制流，使用显式实现的字符串/数组/正则/Math 辅助函数，以及调用 `setBox/moveBy/resizeBy/setText/setStyle/setFill/setStroke/log`。每个编辑原语都会校验参数（元素是否存在、只读标志、有限数字、十六进制颜色），并且只写入一个操作缓冲区，该缓冲区通过与手动编辑相同的命令流水线应用。

**解释器边界：**

1. 标识符只在解释器自有的词法作用域中解析，作用域中预置了文档化的数据和可调用对象。不存在环境全局变量、模块加载器、DOM、网络、IPC 桥、定时器、进程 API 或动态代码原语。
2. 属性读取按值类型分发。数据对象只暴露自身的 JSON 字段；数组、字符串和正则只暴露一个小型方法白名单。宿主原型和函数属性永远不会被遍历，包括通过计算属性名。
3. 调用只接受解释器创建的函数或显式内置函数。通过构造函数/原型链获取的宿主函数无法被表示。
4. 进入编辑原语的输入和值都会递归复制为类 JSON、无原型的数据。出错会丢弃所有缓冲的操作；日志有上限。
5. 执行有语句/表达式和调用深度限制，以约束失控的循环或递归。正则表达式在解释器自有的匹配器上运行，该匹配器有自己的步数预算（受支持的子集；无原生回溯），因此灾难性模式不会在这些限制之外拖住渲染进程。

Electron 渲染进程沙箱仍是纵深防御，但它不是布局脚本的安全边界。解释器的设计目标是让布局脚本从一开始就无法获得渲染进程能力。

如果你发现布局脚本能触及注入原语之外的任何东西（网络、存储、按设计不可达的 IPC 通道，或主进程），那就是漏洞——请报告。

## 威胁模型：渲染 AI 生成的 HTML

有三条流水线在隐藏的 `BrowserWindow` 中渲染 AI 生成或不受信任的 HTML。每个窗口都被视为敌意内容：完整渲染进程锁定（`sandbox: true`、`contextIsolation: true`、`nodeIntegration: false`），无 preload 脚本，无 IPC 暴露面。slides 的隐藏窗口只加载应用自身的渲染进程和打印 HTML（PDF 导出、打印、无头导出）；AI-HTML 转 pptx 在 slides 渲染进程内运行，从不在隐藏窗口中进行。HTML 应用的 DOCX 导出和 docs 的 altChunk 转换仅通过 `executeJavaScript` 在看门狗超时下驱动其窗口（`Promise.race` 对比固定超时，然后 `destroy()`），因此脚本永不退让的页面无法拖住隐藏窗口。HTML→DOCX 转换在启用脚本的情况下渲染页面，并且转换前不对标记做净化——输出是文档，不是沙箱逃逸；如果你发现从转换后的页面进入主进程的途径，请作为漏洞报告。

## 不在范围内

- 本客户端所通信的云 AI 服务由独立方运营，不属于本仓库；其问题应通过服务提供商的渠道报告。
- 需要机器已被攻陷或二进制已被修改的漏洞。这包括为本地开发故意设置的环境变量覆盖点（`GSK_CLI_PATH`、`XLSX_SIDECAR_PATH`）：设置它们需要控制进程环境，等同于在机器上执行代码。
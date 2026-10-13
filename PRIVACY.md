# GenOffice 隐私政策

最后更新：2026 年 8 月 26 日

GenOffice 在本地打开、编辑和保存文档。文档编辑不会将文件上传到 GenOffice。AI 功能需要网络连接，且仅在你使用时才发送请求。

## 使用分析

打包的官方构建默认启用使用分析，包括在引导提示显示前的首次应用启动。引导会说明收集哪些数据以及在哪里关闭。

你可以随时在 **设置 → 通用 → 发送匿名使用统计** 中关闭上报。明确的关闭选择会被记住，并停止后续所有分析事件。

### 事件与参数

启用后，应用会发送以下事件：

- `install_first_launch` — 标记新分配的匿名 `client_id` 首次启用分析的使用；用于留存队列
- `app_launch` — 无事件专属参数
- `file_open` — `ext`，文件扩展名，如 `docx` 或 `xlsx`
- `file_new` — `kind`，取值为 `docx`、`xlsx`、`pptx`、`md` 或 `pdf`
- `login_click` — 无事件专属参数
- `login_success` — 无事件专属参数

每个事件都包含：

- `app_version`
- `platform`
- `os_version`
- `ui_lang`
- 基于进程启动时间生成的每进程 `session_id`
- `engagement_time_msec`，固定值为 `100`

在可用时，载荷还会包含 `country_id`，即来自操作系统区域设置的双字母国家代码。这可能与用户的实际位置不同。

Google Analytics 4 载荷还使用随机安装 UUID 作为 `client_id`。国家代码通过 GA4 仅含国家的 `user_location` 字段发送；应用不发送城市或地区。这两个标识符都不是 Genspark 账号或电子邮件地址。

## 网络信息

事件通过 HTTPS 上的 Measurement Protocol 发送到 Google Analytics 4。作为 HTTPS 接收方，Google 必然会看到连接的公共 IP 地址和传输元数据，并可能将其用于粗略地理定位以及安全或垃圾滥用处理。GenOffice 不会将 IP 地址添加到事件载荷中。

## 分析不收集的数据

GenOffice 分析绝不发送：

- 文档内容
- 文件名
- 文件路径
- Genspark 账号身份
- 电子邮件地址

分析元数据仅注入打包的官方构建，不属于本仓库。没有该打包元数据的源码构建和 Fork 会安装空操作跟踪器，不发送任何使用分析；所有功能完全相同。
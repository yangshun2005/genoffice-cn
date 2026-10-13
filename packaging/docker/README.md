# Docker：无头批量转换

一个自包含镜像，用 GenOffice 自带的无头导出流水线（`<app binary> --headless-export`，见 `docs/headless-pdf-export.md`）将整棵 Office/Markdown/HTML 文档树转换为 PDF。它封装官方发布的 deb——不重新编译 GenOffice 源码——因此每个输出都与桌面应用「文件 ▸ 导出」的结果一致。

这是 Docker 需求（genoffice#1808）中的批量转换部分；它是一个 CLI 工具镜像，不是那里讨论的服务端/协作形态。

## 构建

```sh
docker build -t genoffice-batch packaging/docker
```

在 Apple 芯片 / 其他非 amd64 主机上，构建会在 qemu 下运行 amd64 deb（使用 buildx 时，deb 的架构会自动选择 `--platform linux/amd64`）；构建更慢，但产出的镜像是 amd64，与发布 deb 一致。

## 转换目录

将文档挂载到 `/data`（只读即可），将一个空目录挂载到 `/output`。输出树镜像输入树，扩展名为 `.pdf`：

```sh
docker run --rm -v "$PWD/docs:/data:ro" -v "$PWD/pdf:/output" genoffice-batch
```

```
==> reports/q1.docx
{"status":"ok","summary":"Exported /data/reports/q1.docx to /output/reports/q1.pdf","output_path":"/output/reports/q1.pdf"}
...
{"status":"ok","total":7,"converted":7,"failed":0}
```

退出码：`0` 全部转换成功，`1` 用法错误，`2` 未找到可转换的输入，`3` 部分文件失败（其 `==> <file> (failed, exit N)` 块携带上游错误信封）。

## 可调项（环境变量）

| 变量                                      | 默认值    | 含义                                                                                                                                                                |
| ----------------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `GENOFFICE_INPUT_DIR`                     | `/data`   | 输入卷                                                                                                                                                           |
| `GENOFFICE_OUTPUT_DIR`                    | `/output` | 输出卷                                                                                                                                                          |
| `GENOFFICE_TO`                            | `pdf`     | 导出目标——镜像只接好了 `pdf`（应用也支持将文档导出为 html、将 html 导出为 docx）；其他值会以退出码 1 拒绝，而不是静默忽略 |
| `GENOFFICE_PARALLEL`                      | `1`       | 并发转换数（每个都是独立的 Electron 进程；在大型主机上 2-4 有帮助）                                                                                    |
| `GENOFFICE_INCLUDE` / `GENOFFICE_EXCLUDE` | —         | 可选的 `grep -E` 过滤器，作用于 `/data` 相对路径                                                                                                                   |
| `GENOFFICE_FLAGS`                         | —         | 透传给 `--headless-export` 的额外标志                                                                                                                      |
| `GENOFFICE_XVFB`                          | `1`       | 自行提供显示时设为 `0`（例如用 `xvfb-run` 包裹）                                                                                              |

示例：

```sh
# 仅 reports 文件夹，一次四个转换
docker run --rm -v "$PWD/docs:/data:ro" -v "$PWD/pdf:/output" \
  -e GENOFFICE_INCLUDE='^reports/' -e GENOFFICE_PARALLEL=4 \
  genoffice-batch

# 跳过草稿文档
docker run --rm -v "$PWD/docs:/data:ro" -v "$PWD/pdf:/output" \
  -e GENOFFICE_EXCLUDE='draft' genoffice-batch
```

## 值得了解的行为

- **可转换输入**正是无头导出表所列：
  `.docx`、`.xlsx`/`.xlsm`/`.xls`/`.csv`/`.tsv`、`.pptx`、`.md`/`.markdown`、
  `.html`/`.htm`。输入树中的 PDF 文件刻意不再重新导入。
- **命名冲突**（`a.md` 和 `a.docx` 都想输出 `a.pdf`）时，第二个占用者会确定性地解析为
  `a.md.pdf` / `a.docx.pdf`。
- **沙箱**：容器传入 `--no-sandbox`，因为 Chromium 的 setuid 辅助程序无法在镜像层内工作；进程以 uid 1000 运行（相应映射你的卷，或用 `--user` 覆盖）。
- **字体**：已安装 Noto CJK/Core/Emoji，因此 CJK 文档不会渲染成豆腐块；其他特殊字体可挂载到 `/usr/local/share/fonts`。
- **更新按设计关闭**：镜像中移除了 deb 的 `app-update.yml`（与 fork/PR 构建中禁用更新器的机制相同），因此镜像本身就是更新通道——新版本发布时重新构建，并在 Dockerfile 中更新
  `GENOFFICE_VERSION` + `GENOFFICE_DEB_SHA256`。
- 每个文件启动一次 Electron 是封装已发布二进制的代价；进程内多文件批处理（一次启动，N 次导出）属于上游无头导出功能，而非打包问题。
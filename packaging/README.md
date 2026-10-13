# Linux 打包：Flatpak、NixOS 和 Docker

发布流水线会产出 AppImage、deb 和 rpm 构建产物（见
`apps/shell/electron-builder.cjs`）。本目录补充了 genoffice#1858 中请求的社区维护方案。它们都封装已发布的构建产物——不重新构建 Electron/Rust 源码树——因此与官方二进制逐位一致。

这些文件按原样提供，CI 不会运行它们；依赖前请在真实系统上验证。

## Flatpak

`flatpak/com.genoffice.app.json` 通过 Flatpak 的 `extra-data` 机制安装 deb：flatpak 在安装时从 GitHub Releases 下载固定版本的 deb（校验大小 + sha256），首次启动时将其解包到 `/app/extra/app`（`apply_extra`，纯 Python 3），并通过 Zypak 启动。Zypak 由 `org.electronjs.Electron2.BaseApp` 提供，负责将 Electron 自带的沙箱适配到 Flatpak 沙箱。

从仓库检出本地构建并安装：

```sh
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.repo
flatpak install flathub org.freedesktop.Sdk//24.08 org.electronjs.Electron2.BaseApp//24.08
flatpak-builder --user --install --force-clean build-dir packaging/flatpak/com.genoffice.app.json
flatpak run com.genoffice.app
```

说明：

- 文件类型关联、图标集和桌面入口来自仓库
  （`apps/shell/build/icons`）；deb 的载荷只提供应用本身。
- 内置的 `genoffice` 命令行在沙箱内可用，例如：
  `flatpak run --command=/app/extra/app/opt/GenOffice/resources/cli/genoffice com.genoffice.app --help`
- deb 内置了针对原生安装布局的应用内更新源；在 Flatpak 下 `/app` 是只读的，因此更新必须通过 Flatpak，而非应用的更新对话框。
- 清单固定为 v0.11.0。新版本发布时，更新 `extra-data` 源的 `url`、`sha256` 和
  `size`（以及 `com.genoffice.app.metainfo.xml` 中的 `<release>` 条目）；`x-checker-data` 块可让 Flathub 机器人自动提议新 URL。

## NixOS

`nix/genoffice.nix` 用 `appimageTools` 封装上游 AppImage（不重新构建源码），安装仓库的图标集和桌面入口，并声明 Electron 从宿主 dlopen 的两个库（`libsecret` 用于基于密钥环的 API 密钥存储，`nss`）：

```sh
nix-build packaging/nix
./result/bin/genoffice
```

该表达式会读取仓库的图标文件，因此需从仓库检出运行。新版本发布时，更新 `nix/genoffice.nix` 中的 `version` 和 `hash`。

已知问题：nix store 以 `nosuid` 挂载，因此当 AppImage 的 `chrome-sandbox` 存在但未设置 setuid 时，Chromium 会以 "The SUID sandbox helper binary was found, but is not configured correctly" 中止。此时用 `genoffice --no-sandbox` 启动（该标志会透传给封装脚本）；Flatpak 方案则通过 Zypak 保留真正的沙箱。

## Docker

`docker/` 构建用于批量 PDF 转换的无头镜像；见
`docker/README.md`。
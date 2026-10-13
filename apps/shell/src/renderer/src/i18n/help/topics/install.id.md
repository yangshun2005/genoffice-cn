# 安装 GenOffice

每个构建都发布在[发布版本页面](https://github.com/genspark-ai/genoffice/releases/latest)。所有构建均来自 `main`；macOS 和 Windows 的安装程序已签名。

## 为你的电脑选择文件

| 平台                                 | 要求                                                  | 文件                   |
| ------------------------------------ | ----------------------------------------------------- | ---------------------- |
| **macOS** — Apple Silicon            | macOS 11+                                             | `.dmg` (arm64)         |
| **macOS** — Intel                    | macOS 11+                                             | `.dmg` (x64)           |
| **Windows** — 大多数 PC              | Windows 10+，Intel/AMD                                | `-x64.exe` 安装程序    |
| **Windows** on Arm                   | Windows 11 on Arm（Snapdragon X 及同类）              | `-arm64.exe` 安装程序  |
| **Linux** — Debian / Ubuntu          | x86_64，glibc 2.34+（Ubuntu 22.04 或更新）            | `.deb`                 |
| **Linux** — Fedora / RHEL / openSUSE | x86_64，glibc 2.34+（Fedora 35+，RHEL 9+，Leap 15.6+） | `.rpm`                 |
| **Linux** — 其他                     | x86_64，glibc 2.34+，FUSE 2                           | `.AppImage`            |

旧版本仍保留在发布版本页面。

## 在 macOS 上

打开 `.dmg`，将 **GenOffice** 拖入 Applications。在 Intel 构建上，首次启动会要求你确认打开：在 Applications 中右键点击应用 ▸ 打开。这是 Gatekeeper 遇到了看似未签名的磁盘映像，而非下载损坏。

## 在 Windows 上

运行 `.exe` 安装程序。它会将 GenOffice 放入开始菜单，并注册 `.docx`、`.xlsx`、`.pptx`、`.pdf` 等文件类型，双击文件即可直接打开。

## 在 Linux 上

**Debian / Ubuntu**

```sh
sudo apt install ./genoffice_<version>_amd64.deb
```

**Fedora / RHEL / openSUSE**

```sh
sudo dnf install ./genoffice-<version>.x86_64.rpm     # Fedora / RHEL family
sudo zypper install ./genoffice-<version>.x86_64.rpm  # openSUSE
```

**AppImage** — 放在哪里都能运行，无需安装步骤：

```sh
chmod +x GenOffice-<version>.AppImage
./GenOffice-<version>.AppImage
```

它需要 FUSE 2 运行时。如果你不想安装它，可以用 `--appimage-extract-and-run` 运行，沙箱仍会从解压目录中运行。

## 你正在运行的构建

**设置 ▸ 关于**是应用报告你所使用的构建、所跟随的更新渠道以及项目地址的地方。当该渠道发布更新的构建时，同一面板会提供更新；Flatpak、Nix 或 Docker 安装则不会，因为它们都由安装它们的工具来更新。

![设置 ▸ 关于，显示已安装版本、应用跟随的更新渠道以及项目的 GitHub 链接](img/install.png)

## 另外三条途径

三者都封装已发布的构建产物，而非重新构建应用，因此始终跟随官方二进制文件。

- **Flatpak** — 通过 Flatpak 的 `extra-data` 机制安装 `.deb`，并在 Zypak 下运行，后者适配 Electron 自带的沙箱。`/app` 目录树为只读，因此更新通过 Flatpak 进行，而非应用内的更新对话框。
- **Nix** — 包表达式，可用 `nix-build packaging/nix` 从仓库的本地副本构建；参见 `packaging/nix`。
- **Docker** — 无界面的批量转换镜像（`packaging/docker`）。它通过应用自身的导出路径将整个 Office 文档、Markdown 和 HTML 目录树转换为 PDF，因此结果与文件 ▸ 导出所生成的相同。这是命令行工具，不是服务器。

## 命令行也随之附带

每次安装都附带 `genoffice` 命令，它与窗口使用同一引擎，因此两者对文件的处理永远不会产生分歧。在 macOS 和 Windows 上，该命令位于应用包内；`genoffice install-cli` 会将其放入你的 `PATH`。参见**命令行与代理**了解它能做什么。
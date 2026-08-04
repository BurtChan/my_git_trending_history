# Fastfetch 项目分析

> 一句话总结：Fastfetch 是一款用 C 语言编写的、高性能且功能丰富的系统信息展示工具，是经典 neofetch 的现代替代品。

---

## 基本信息

| 项目 | 详情 |
|------|------|
| 项目名称 | Fastfetch |
| GitHub 地址 | https://github.com/fastfetch-cli/fastfetch |
| Stars | ~19.6k |
| Forks | ~665 |
| 许可证 | MIT License |
| 主要语言 | C |
| 当前维护者 | @CarterLi |
| 原始作者 | @LinusDierheimer |
| 支持平台 | Linux、macOS、Windows 8.1+、Android (Termux)、FreeBSD、OpenBSD、NetBSD、DragonFly BSD、Haiku、SunOS (illumos, Solaris) |
| 构建系统 | CMake |
| 配置格式 | JSONC (JSON with comments) |
| 代码签名 | SignPath.io 免费提供 |

---

## 解决什么问题

在终端中展示系统硬件和软件信息（如操作系统、CPU、GPU、内存、磁盘、网络等）是 Linux/Unix 用户和系统管理员的常见需求。经典的 neofetch 工具曾长期占据这一领域，但 neofetch 存在以下问题：

1. **已停止维护**：neofetch 已经不再积极更新，bug 和兼容性问题无法得到及时修复。
2. **性能不佳**：neofetch 使用 Bash 编写，执行速度慢，不适合放在 shell 启动脚本中。
3. **功能不够完善**：对 Wayland 等新协议的支持不准确，信息展示格式不够统一。
4. **可定制性有限**：配置灵活性不足，无法满足高级用户的需求。

Fastfetch 应运而生，旨在提供一个**持续维护、性能优先、功能丰富、高度可定制**的系统信息展示工具。它用 C 语言从零编写，在不牺牲功能的前提下将执行速度做到了极致，让用户可以无顾虑地将其加入 `.bashrc` / `.zshrc` 中，在每次打开终端时瞬间看到系统信息。

---

## 核心功能

### 1. 全面的系统信息检测

Fastfetch 通过模块化设计支持大量系统信息检测模块，涵盖：

- **OS / Host**：操作系统名称、版本、主机型号
- **Kernel**：内核版本
- **Uptime**：系统运行时间
- **Packages**：已安装包数量（支持 dpkg、rpm、pacman、pip、npm、brew 等多种包管理器）
- **Shell**：当前使用的 shell 及版本
- **Display**：显示器信息，包括分辨率、刷新率（支持 Wayland 多显示器不同刷新率）
- **DE / WM**：桌面环境和窗口管理器检测（支持第三方窗口管理器插件检测）
- **WM Theme / Theme / Icons**：系统主题、图标主题
- **CPU**：处理器型号、核心数、频率
- **GPU**：显卡信息（通过 Vulkan、OpenCL、OpenGL 等多种途径检测）
- **Memory**：内存使用情况（精确到小数点后两位）
- **Swap**：交换分区使用情况
- **Disk**：磁盘使用信息
- **Local IP / Public IP**：本地和公网 IP 地址
- **Battery**：电池状态
- **Bluetooth**：蓝牙设备
- **Wifi**：无线网络信息
- **Sound / Media / Player**：音频设备、当前播放媒体
- **Camera**：摄像头设备
- **Terminal / Terminal Font**：终端模拟器及字体信息
- **Command**：自定义 shell 命令输出（支持运行任意命令并展示结果）

### 2. 极致的性能表现

- 使用 C 语言编写，启动速度远超 Bash 实现的 neofetch
- 支持多线程并行检测，充分利用多核处理器
- 动态加载库：运行时按需加载依赖库，不影响基本功能
- 可安全地放入 shell 配置文件中自动运行，不会拖慢终端启动

### 3. 丰富的 Logo 自定义

- 内置几乎所有主流 Linux 发行版的 ASCII Logo
- 支持自定义 ASCII 艺术作为 Logo
- 支持图片 Logo（通过 sixel、kitty、iTerm 等图像协议）
- 支持 FIGlet 文字生成 Logo
- Logo 颜色可通过 `--logo-color-[1-9]` 灵活调整
- 支持从 neofetch 迁移自定义 Logo

### 4. JSONC 配置系统

- 使用 JSONC（带注释的 JSON）格式配置，兼具结构化和可读性
- 提供 JSON Schema 支持，可在 VSCode 等 IDE 中获得自动补全
- 每个模块都有独立的 `format` 格式化字符串
- 内置预设配置文件（`presets` 目录），方便快速上手
- 支持 `--gen-config` 生成最小配置，`--gen-config-full` 生成完整配置

### 5. 多平台广泛支持

- **Linux**：几乎所有主流发行版均已有官方包（Arch、Debian、Ubuntu、Fedora、Gentoo、Alpine、NixOS、openSUSE 等）
- **macOS**：通过 Homebrew 和 MacPorts 安装
- **Windows**：通过 scoop、Chocolatey、winget 安装
- **BSD 系列**：FreeBSD、NetBSD、OpenBSD、DragonFly BSD
- **Android**：通过 Termux 安装
- **其他**：Haiku、SunOS (illumos, Solaris)
- 提供 nightly 构建，方便体验最新功能

### 6. JSON 格式输出

- 支持 `--format json` 以 JSON 格式输出所有检测数据
- 便于脚本集成和自动化处理
- 方便程序化获取系统信息

---

## 技术栈

| 类别 | 技术 |
|------|------|
| 核心语言 | C |
| 辅助语言 | C++（部分模块） |
| 构建系统 | CMake |
| 依赖检测 | pkg-config |
| 配置格式 | JSONC (JSON with comments) |
| Schema 支持 | JSON Schema |
| 图形检测 | Vulkan、OpenGL (EGL/GLX)、OpenCL |
| 显示服务集成 | X11 (XCB/RandR)、Wayland、DRM |
| 图像渲染 | ImageMagick (sixel/kitty 协议)、chafa (ASCII art) |
| 系统接口 | D-Bus、GIO/DConf、PulseAudio |
| 数据库 | SQLite3（包管理器计数） |
| Windows 支持 | CppWinRT、Vulkan Loader、OpenCL ICD |
| CI/CD | GitHub Actions |
| 代码签名 | SignPath.io |
| 包管理覆盖 | Repology 跟踪的全平台包仓库 |

### 编译器要求

- **Linux/macOS/BSD**：GCC 或 Clang
- **Windows**：GCC 或 Clang（MSVC 不支持），推荐使用 MSYS2 CLANG64 环境

### 核心设计原则

- **动态库加载**：编译时可选择启用/禁用可选依赖，运行时按需加载库
- **优雅降级**：缺少某个库时，仅该功能不可用，不影响其他功能
- **最小依赖**：Linux 上硬依赖仅有 libc、libdl、libm、libpthread

---

## 使用场景

### 1. 终端启动展示（最常见用途）

将 `fastfetch` 写入 `.bashrc`、`.zshrc` 或 `config.fish`，每次打开终端时展示系统信息，兼顾美观和实用。由于执行速度极快，不会拖慢终端启动体验。

### 2. 系统信息快速查看

系统管理员和开发者需要快速了解服务器或工作站的基本配置（CPU、GPU、内存、磁盘、IP 等），一条 `fastfetch` 命令即可获得全面信息，无需分别运行 `lscpu`、`free`、`df`、`ip addr` 等多个命令。

### 3. 虚拟机/远程服务器管理

Fastfetch 的 `Local IP` 模块在终端启动时自动展示本机 IP，方便 SSH 连接虚拟机或远程服务器，省去了手动执行 `ip addr` 的步骤。

### 4. 桌面截图展示（Ricing 社区）

Linux 桌面美化（Ricing）社区广泛使用系统信息展示工具配合自定义主题截图分享。Fastfetch 提供丰富的 Logo、颜色和格式自定义选项，是展示个性化桌面的理想工具。

### 5. 脚本集成与自动化

通过 `--format json` 输出结构化数据，可以将 Fastfetch 集成到 Shell 脚本、监控工具或配置管理工具中，用于自动化系统信息采集和处理。

### 6. 跨平台系统信息采集

Fastfetch 支持 Linux、macOS、Windows、BSD、Android 等几乎所有主流操作系统，是跨平台环境下统一获取系统信息的理想选择。

### 7. 硬件诊断辅助

通过 GPU 模块（Vulkan/OpenCL/OpenGL 多途径检测）、Display 模块、Camera 模块等，Fastfetch 可以辅助快速确认硬件是否被系统正确识别。

---

## 与 neofetch 的对比

| 特性 | Fastfetch | Neofetch |
|------|-----------|----------|
| 编写语言 | C | Bash |
| 执行速度 | 极快（毫秒级） | 较慢（秒级） |
| 维护状态 | 积极维护 | 已停止维护 |
| Wayland 支持 | 完整支持 | 实际不支持 |
| 配置系统 | JSONC + JSON Schema | Shell 脚本 |
| 模块数量 | 更多 | 基础集合 |
| 包管理计数 | 准确（排除已移除包） | 不准确（包含 rc 包） |
| 内存显示 | 精确（555.00 MiB） | 近似（555 MiB） |
| JSON 输出 | 原生支持 | 不支持 |
| 多线程 | 支持 | 不支持 |
| Windows 原生 | 支持 | 不支持 |
| Android 支持 | 支持 | 不支持 |

---

## 安装示例

```bash
# Linux (Arch)
pacman -S fastfetch

# Linux (Ubuntu/Debian)
apt install fastfetch

# macOS
brew install fastfetch

# Windows
scoop install fastfetch
# 或
winget install fastfetch

# Android (Termux)
pkg install fastfetch
```

---

## 相关链接

- GitHub 仓库：https://github.com/fastfetch-cli/fastfetch
- Wiki 文档：https://github.com/fastfetch-cli/fastfetch/wiki
- 构建指南：https://github.com/fastfetch-cli/fastfetch/wiki/Building
- 配置文档：https://github.com/fastfetch-cli/fastfetch/wiki/Configuration
- Nightly 构建：https://nightly.link/fastfetch-cli/fastfetch/workflows/ci/dev?preview
- Repology 打包状态：https://repology.org/project/fastfetch/versions

---

> 一句话总结：Fastfetch 是 neofetch 的现代高性能继任者，用 C 语言打造，跨平台支持广泛，执行速度极快，配置灵活，功能全面，是终端系统信息展示的最佳选择。

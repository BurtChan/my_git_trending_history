# Microsoft PowerToys 项目分析

## 项目名称

**Microsoft PowerToys** — 一套用于增强 Windows 生产力与自定义体验的实用工具集合。

- **GitHub 地址**：https://github.com/microsoft/PowerToys
- **开源许可证**：MIT License
- **最新版本**：v0.99.0

---

## 项目概述

Microsoft PowerToys 是由微软官方开发并开源的一套 Windows 系统增强工具集，旨在帮助用户提升工作效率和系统自定义能力。该项目最初源自 Windows 95 时代的经典系统工具，2019 年以开源形式在 GitHub 上重新发布，并持续活跃开发至今。目前包含超过 30 个实用工具模块，覆盖窗口管理、快捷操作、文件处理、系统监控等多个方面，是 Windows 高级用户和开发者必备的工具箱之一。

PowerToys 采用模块化架构设计，每个工具都可以独立启用或禁用，用户可根据自身需求灵活配置。项目由微软官方团队维护，同时拥有活跃的开源社区贡献者参与开发和改进。2026 年 4 月发布的 v0.99.0 版本新增了 Power Display（显示器控制）和 Grab And Move（Linux 风格窗口拖拽）两个实用工具，并持续优化 Command Palette、Keyboard Manager 等核心模块。

该项目在 GitHub 上拥有超过 12.9 万颗 Star，是微软旗下最受欢迎的开源项目之一，也是 Windows 生态中 star 数量最高的生产力工具项目。PowerToys 不仅是实用工具集，更代表了微软拥抱开源社区的决心，部分最受欢迎的功能（如 PowerToys Run 的搜索能力）已逐步被整合到 Windows 系统本身中。

---

## 核心功能

| 工具名称 | 功能描述 |
|---------|---------|
| **PowerToys Run** | 快速启动器（Alt+Space），可搜索应用、文件、系统设置等 |
| **FancyZones** | 高级窗口管理器，支持自定义窗口布局区域 |
| **Command Palette** | 命令面板，提供类似 VS Code 的快捷命令访问方式 |
| **PowerRename** | 批量重命名工具，支持正则表达式和搜索替换 |
| **Color Picker** | 系统级取色器，支持从任意位置选取颜色 |
| **Text Extractor** | 屏幕 OCR 文字提取工具（Win+Shift+T），离线识别 |
| **Always on Top** | 快速将窗口置顶（Win+Ctrl+T） |
| **Awake** | 防止系统进入睡眠状态 |
| **Keyboard Manager** | 键盘按键和快捷键重映射工具 |
| **File Locksmith** | 查看和解除文件锁定 |
| **Image Resizer** | 右键菜单批量调整图片大小 |
| **Peek** | 快速预览文件内容（Space 键） |
| **Environment Variables** | 图形化环境变量编辑器 |
| **ZoomIt** | 屏幕缩放和标注工具，支持滚动截图 |
| **Workspaces** | 工作区管理，保存和恢复窗口布局 |
| **Mouse Without Borders** | 跨多台电脑共享鼠标键盘 |
| **File Explorer Add-ons** | 文件资源管理器增强（预览面板支持更多格式） |
| **New+** | 增强的新建文件菜单 |
| **Crop and Lock** | 裁剪并锁定窗口区域 |
| **Power Display** | 系统托盘显示器控制（亮度、对比度、色彩配置） |
| **Grab and Move** | Linux 风格的窗口拖拽（Alt+鼠标） |
| **Light Switch** | 自动定时切换明暗主题 |
| **Hosts File Editor** | 图形化 Hosts 文件编辑器 |
| **Registry Preview** | 注册表文件预览工具 |
| **Screen Ruler** | 屏幕像素标尺 |
| **Quick Accent** | 快速输入特殊字符 |
| **Shortcut Guide** | 快捷键指南（按住 Win 键显示） |
| **Advanced Paste** | 高级粘贴，支持纯文本粘贴等模式 |

---

## 技术栈

| 技术组件 | 说明 |
|---------|------|
| **C#** | 主要开发语言，用于 UI 逻辑和工具模块 |
| **C++/WinRT** | 部分性能敏感模块和底层系统交互 |
| **WinUI 3** | 现代化 Windows 原生 UI 框架 |
| **Windows App SDK** | WinUI 3 的交付载体，提供现代 Windows API |
| **XAML** | 界面标记语言，用于构建用户界面 |
| **.NET** | 运行时框架（.NET 8+） |
| **MSIX** | 现代 Windows 应用打包格式 |
| **CMake / Visual Studio** | 构建系统和 IDE |
| **PowerShell** | 部分辅助脚本和自动化 |
| **Windows OCR API** | Text Extractor 的光学字符识别引擎 |
| **WebView2** | 部分需要 Web 内容渲染的模块 |

---

## 项目亮点

1. **微软官方背书与开源社区驱动**：PowerToys 是微软少数由官方团队直接维护的大型开源项目之一，兼具企业级质量保证和开源社区的活力。项目代码规范、文档完善，贡献流程清晰，是学习 Windows 桌面应用开发的优秀参考。

2. **模块化架构设计**：30+ 个工具模块各自独立，用户可按需启用/禁用。每个模块拥有独立的设置界面和快捷键绑定，互不干扰，体现了良好的软件设计理念。同时，这种架构也降低了社区贡献的门槛，开发者可以独立为某个模块贡献代码。

3. **紧跟 Windows 生态演进**：从早期的 WPF 迁移到 WinUI 3，从 C++/CX 迁移到 C++/WinRT，PowerToys 始终采用微软最新的技术栈。v0.99.0 新增的 Grab And Move（借鉴 Linux 窗口管理）和 Power Display 等功能，持续填补 Windows 系统功能缺口。部分热门功能已被微软反向整合进 Windows 系统。

4. **活跃的迭代节奏**：项目保持每月左右一次的发布频率，持续引入新工具和优化现有功能。v0.98.1 于 2026 年 3 月发布，v0.99.0 紧随其后，开发路线图清晰（已规划至 v0.100），社区反馈响应迅速。

---

## 应用场景

1. **高效办公与生产力提升**：PowerToys Run 快速启动应用和搜索文件，FancyZones 实现多窗口高效布局管理，Command Palette 提供统一命令入口，Advanced Paste 简化粘贴操作。对于需要频繁切换和操作多个窗口的办公用户而言，这套工具可显著提升日常操作效率。

2. **开发者工具箱**：Environment Variables 图形化编辑器、Registry Preview 注册表预览、Hosts File Editor 等工具直接服务于开发者的日常需求。File Locksmith 帮助排查文件占用问题，Screen Ruler 辅助 UI 设计调试，是开发者工作流的有力补充。

3. **系统自定义与个性化**：Light Switch 实现明暗主题自动切换，Keyboard Manager 重映射按键，Mouse Without Borders 跨设备控制鼠标键盘。这些工具让 Windows 系统高度适配个人使用习惯，尤其适合从 Linux/macOS 切换到 Windows 的用户。

4. **内容创作与设计辅助**：Color Picker 提供系统级取色功能，Text Extractor 从屏幕任意位置提取文字（离线 OCR），Image Resizer 批量调整图片尺寸，ZoomIt 屏幕标注和滚动截图，为设计师、内容创作者和演示者提供便捷工具。

---

## Star 数据

| 指标 | 数据 |
|------|------|
| **总 Stars** | ~129,000+ |
| **总 Forks** | ~7,700+ |
| **今日新增** | Trending 项目（持续增长中） |
| **开源许可证** | MIT License |
| **主要语言** | C# (~60%)，C++ (~30%)，XAML 等 |
| **最新版本** | v0.99.0 |
| **支持平台** | Windows 10 (1809+) / Windows 11 |
| **架构支持** | x64、ARM64 |

---

## 📋 更新记录

### 更新 1 — 2026 年 7 月 31 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：Microsoft PowerToys 持续稳定增长，Star 数从 129,000 增长至约 137,304（+8,304）。v0.100.2 版本（2026 年 6 月 26 日）是重大里程碑版本，引入了全新 Shortcut Guide、改进的 Command Palette、新 WinUI 3 键盘管理编辑器（默认启用）、Mouse Without Borders 新增 Refresh Connections 操作、Image Resizer 设置热更新（无需重启）以及 Quick Accent 在高 DPI 和多显示器场景的可靠性提升。启动速度显著优化，显示器识别更可靠，新增 Max Compatibility Mode 兼容不完全支持 DDC 的显示器。PowerToys 已成为 Windows 用户必备的系统增强工具套件。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 129,000 | 137,304 | +8,304 |
| 总 Forks | 8,368 | 8,368 | — |

**核心变化概要**：
- v0.100 里程碑版本发布，Star 数增长超 8,300，逼近 14 万大关
- 全新 Shortcut Guide 和 Command Palette 改进
- WinUI 3 键盘管理编辑器默认启用，UI 现代化
- Mouse Without Borders 新增连接刷新功能，Image Resizer 支持热更新

---

## 总结

Microsoft PowerToys 是 Windows 生态中当之无愧的"瑞士军刀"，以开源形式提供了 30 余个精心打磨的系统增强工具，覆盖窗口管理、文件操作、键盘鼠标定制、屏幕辅助等方方面面。作为微软官方主导的开源项目，它不仅拥有企业级的代码质量和持续活跃的开发节奏，更通过 WinUI 3 等前沿技术栈展示了 Windows 桌面应用开发的最佳实践。无论是追求效率的办公用户、需要系统工具的开发者，还是希望深度自定义 Windows 的高级用户，PowerToys 都是不可或缺的装机必备工具集。

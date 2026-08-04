# optimizerDuck 项目分析

> 一句话总结：optimizerDuck 是一款免费、开源的 Windows 系统优化工具，以现代 WinUI 界面提供 30+ 项性能、隐私和 GPU 优化，内置系统管理工具，具备完整的回滚机制和零遥测保障，是 Windows 玩家和技术爱好者的理想优化利器。

---

## 基本信息

| 项目 | 详情 |
|------|------|
| 项目名称 | optimizerDuck |
| GitHub 地址 | https://github.com/itsfatduck/optimizerDuck |
| Stars | ~3,603 |
| Forks | ~158 |
| 许可证 | GPL v3（含自定义条款，详见仓库） |
| 主要语言 | C# |
| 作者 | @itsfatduck |
| 支持平台 | Windows 10（x64）、Windows 11（x64） |
| 创建时间 | 2025-10-31 |
| 提交记录 | 503 个 Commit |
| 官方网站 | https://optimizerduck.vercel.app/ |
| 文档地址 | https://optimizerduck.vercel.app/docs/guides/getting-started |
| 社区频道 | Discord（discord.gg/tDUBDCYw9Q） |

---

## 解决什么问题

Windows 系统虽然功能强大，但默认配置往往存在大量冗余，困扰着追求性能和隐私的用户：

1. **后台资源浪费**：Windows 预装了大量服务、计划任务和遥测程序，在后台安静运行，持续消耗 CPU、RAM 和磁盘资源。
2. **隐私泄露隐患**：系统默认开启遥测数据收集、错误报告、广告 ID、位置追踪等，用户隐私难以保障。
3. **GPU 性能未释放**：AMD/NVIDIA/Intel 显卡的默认电源管理和调度策略偏保守，未针对游戏和高负载场景优化。
4. **臃肿软件泛滥**：OEM 厂商预装大量无用应用，且 Windows Update 会反复尝试重新安装。
5. **优化工具鱼龙混杂**：市面上许多优化工具闭源且不可信，或功能单一、激进粗暴，容易导致系统不稳定。
6. **手动调整繁琐**：通过注册表编辑器和服务管理器逐项调整需要大量专业知识和时间。

optimizerDuck 应运而生，以**安全、透明、可逆、现代化**为设计原则，通过精美的 GUI 界面将经过充分验证的优化项呈现给用户，每一项都标注风险等级，所有更改均可一键回滚，让 Windows 优化变得简单且可控。

---

## 核心功能

### 1. 系统优化（30+ 项，分 6 大类）

每项优化均附带清晰的中文描述和风险评级（安全/中等/风险），来源均经过知名工具、社区指南和硬件厂商推荐验证：

#### 性能优化（Performance）
- **服务主机调优**：将部分服务进程移至 RAM 运行，减少磁盘 I/O
- **进程优先级调整**：优化前台进程调度策略
- **键盘延迟降低**：减少键盘输入响应延迟（游戏玩家福音）
- **多媒体调度器优化**：调整 MMCSS 调度策略，减少对游戏和应用的干扰

#### 隐私保护（Privacy）
- **禁用遥测**：关闭 Windows 遥测数据收集（Diagnostic Tracking Service）
- **禁用错误报告**：关闭 Windows Error Reporting
- **禁用广告 ID**：阻止基于设备 ID 的定向广告
- **禁用位置追踪**：关闭位置服务和历史记录
- **禁用 Cortana 和 Copilot**：移除 AI 助手相关服务和集成
- **禁用内容投递**：关闭 Windows 内容投递和推荐

#### GPU 优化（GPU）
针对三大显卡厂商提供专用注册表调整：
- **AMD**：电源状态管理、时钟门控控制、显示延迟优化
- **NVIDIA**：电源管理策略、帧率优化、显示延迟降低
- **Intel**：集成显卡电源状态、显示性能调整

#### 电源管理（Power）
- **禁用休眠**：释放 hiberfil.sys 占用的磁盘空间
- **禁用快速启动**：解决部分兼容性问题
- **USB 选择性挂起**：防止 USB 设备意外断连
- **自定义高性能电源计划**：创建并激活优化后的电源方案
- **禁用电源节流**：防止系统在后台限制 CPU 性能

#### 臃肿清理与服务管理（Bloatware & Services）
- **阻止 OEM 应用重装**：从注册表层面阻止 Windows Update 重新安装已移除的 OEM 应用
- **200+ Windows 服务启动类型微调**：将不必要的服务设为手动或禁用，释放系统资源

#### 用户体验优化（User Experience）
- **移除菜单延迟**：消除右键菜单和开始菜单的动画延迟
- **禁用任务栏动画**：去除任务栏切换动画
- **禁用透明效果**：减少 GPU 渲染负担

### 2. 系统定制（4 大类）

| 类别 | 功能项 |
|------|--------|
| **桌面** | 显示/隐藏图标（此电脑、回收站、网络、用户文件、控制面板）、移除快捷方式箭头 |
| **偏好设置** | 任务栏对齐方式、小组件、任务视图/结束任务按钮、时钟秒数、深色模式、文件扩展名、隐藏文件、剪贴板历史、紧凑视图、贴靠助手、经典右键菜单、Bing 搜索 |
| **游戏** | 游戏模式、游戏栏、后台录制、鼠标加速、全屏优化、硬件加速 GPU 调度 |
| **系统** | 启动时启用数字锁定 |

### 3. 内置工具

| 工具 | 功能说明 |
|------|----------|
| **System Dashboard** | 在同一面板中查看 CPU、RAM、GPU、存储、操作系统详细信息 |
| **Startup Manager** | 查看/切换开机启动应用和任务，可直接打开文件所在位置 |
| **Scheduled Tasks** | 浏览、运行、停止、启用、禁用、删除 Windows 计划任务 |
| **Disk Cleanup** | 清理临时文件、缓存、更新残留、预读取数据、缩略图缓存、回收站、崩溃转储、旧 Windows 安装 |
| **Bloatware Remover** | 列出可移除的 AppX 包，标注风险等级（安全/注意/未知） |

---

## 技术架构

| 类别 | 技术/方式 |
|------|-----------|
| 核心语言 | C# |
| 运行框架 | .NET 10（WPF） |
| UI 库 | WPF UI Library（Fluent Design 风格） |
| 主题系统 | 深色（默认）、浅色、高对比度，支持 Mica 背景效果 |
| 回滚系统 | 4 种类型（注册表、服务、计划任务、Shell），JSON 持久化状态，线程安全 I/O |
| 优化发现 | 基于反射 + 自定义特性的自动发现机制 |
| 部署方式 | 单一 `.exe` 便携版，无需安装 |
| CI/CD | GitHub Actions 自动构建 |
| 遥测 | 完全零遥测，纯离线运行 |

### 项目结构

```
optimizerDuck/
├── optimizerDuck/                  # 主项目（WPF 应用程序）
├── optimizerDuck.Resources/        # 资源文件（图标、本地化等）
├── optimizerDuck.Test/             # 单元测试项目
├── .github/                        # GitHub Actions 工作流
├── .agents/skills/                 # AI 代理技能配置
├── CONTRIBUTING.md                 # 贡献指南
├── DISCLAIMER.md                   # 免责声明
├── PRIVACY.md                      # 隐私政策
├── LICENSE                         # GPL v3 许可证
└── README.md                       # 多语言 README
```

---

## 使用方式

### 快速开始

1. 前往 [GitHub Releases](https://github.com/itsfatduck/optimizerDuck/releases/latest) 下载最新版本
2. 直接运行 `.exe` 文件——**无需安装**
3. 在界面中浏览各项优化，选择需要的项目
4. 点击应用，根据提示重启系统

> **提示**：首次使用前建议创建系统还原点。

### 安全机制

optimizerDuck 在安全性方面做了周全设计：

1. **自动备份**：每项更改执行前自动创建回滚文件
2. **一键还原**：可在界面中单独撤销任意优化，或一键全部还原
3. **风险评级**：每项优化标注安全/中等/风险等级，用户可自主判断
4. **默认不执行**：不会自动应用任何优化，所有操作需用户手动选择
5. **还原点提示**：首次优化前建议创建 Windows 还原点

### SmartScreen 警告说明

由于未购买代码签名证书（费用高昂），Windows SmartScreen 可能会发出警告。用户可点击「更多信息 > 仍要运行」，或自行从源码构建验证。

---

## 多语言支持

| 语言 | 翻译者 |
|------|--------|
| 英语（美国） | 主语言（推荐） |
| 越南语 | itsfatduck |
| 繁体中文 | abc0922001 |
| 简体中文 | wcxu21 |
| 俄语 | Foodhead |
| 法语 | Robocnop |
| 韩语 | klfnn |
| 西班牙语 | thexxtt |

支持通过 CONTRIBUTING.md 指南贡献新语言翻译。

---

## 应用场景

### 1. 游戏性能优化

PC 玩家通过 GPU 厂商专用优化、电源管理调整、游戏模式配置和键盘延迟降低，最大化释放硬件性能，获得更流畅的游戏体验。

### 2. 新系统初始化

购买新电脑或重装系统后，使用 optimizerDuck 一键清理 OEM 臃肿软件、禁用遥测和后台服务、配置隐私保护，快速获得干净高效的 Windows 环境。

### 3. 隐私保护

隐私敏感用户通过禁用遥测、错误报告、广告 ID、位置追踪、Cortana 和 Copilot，最大程度减少数据向微软和第三方泄露。

### 4. 旧设备性能提升

通过禁用不必要的服务、计划任务和视觉效果优化，释放系统资源，延长老旧硬件的使用寿命。

### 5. 系统管理与维护

利用内置的 Startup Manager、Scheduled Tasks、Disk Cleanup 和 Bloatware Remover，全面管理和维护系统，无需依赖多个独立工具。

---

## 与同类工具对比

| 特性 | optimizerDuck | O&O ShutUp10++ | Win11Debloat | Chris Titus Tech Debloat |
|------|-------------|-----------------|-------------|--------------------------|
| 界面 | 现代 GUI（Fluent Design） | 传统 GUI | 命令行 | 命令行 |
| 语言 | C#（.NET/WPF） | C++（闭源） | PowerShell（开源） | PowerShell（开源） |
| GPU 优化 | 支持（AMD/NVIDIA/Intel） | 不支持 | 不支持 | 不支持 |
| 性能优化 | 全面（服务/优先级/键盘） | 基础 | 基础 | 基础 |
| 隐私保护 | 支持 | 支持（最精细） | 支持 | 支持 |
| 臃肿清理 | 支持（含风险评级） | 不支持 | 支持（90+ 应用） | 支持 |
| 服务管理 | 200+ 服务微调 | 支持 | 不支持 | 部分支持 |
| 内置工具 | Dashboard/启动/任务/磁盘 | 无 | 无 | 无 |
| 回滚机制 | 全自动（4 种类型） | 支持 | 支持（还原点） | 一般 |
| 开源协议 | GPL v3 | 免费（非开源） | MIT | 开源 |
| 多语言 | 8 种语言 | 多语言 | 英语 | 英语 |
| 便携运行 | 单 exe 无需安装 | 需安装 | 脚本直接运行 | 脚本直接运行 |
| 零遥测 | 是 | 是 | 是 | 是 |

optimizerDuck 的独特优势在于：**现代 GUI 界面**、**GPU 厂商专用优化**、**内置系统管理工具**和**全面的回滚机制**四者的结合，使其既适合技术爱好者精细调优，也适合普通用户一键优化。

---

## 相关链接

- GitHub 仓库：https://github.com/itsfatduck/optimizerDuck
- 官方网站：https://optimizerduck.vercel.app/
- 使用文档：https://optimizerduck.vercel.app/docs/guides/getting-started
- Discord 社区：https://discord.gg/tDUBDCYw9Q
- 最新版本下载：https://github.com/itsfatduck/optimizerDuck/releases/latest
- 贡献指南：https://github.com/itsfatduck/optimizerDuck/blob/master/CONTRIBUTING.md
- 隐私政策：https://github.com/itsfatduck/optimizerDuck/blob/master/PRIVACY.md

---

> 一句话总结：optimizerDuck 以仅 503 次提交和不到一年时间斩获 3,600+ Stars，凭借现代 Fluent Design 界面、GPU 厂商级优化、200+ 服务微调和全方位回滚机制，成为 Windows 优化工具领域的后起之秀——它是玩家追求极致性能、用户保护隐私、以及任何想要干净高效 Windows 体验之人的理想选择。

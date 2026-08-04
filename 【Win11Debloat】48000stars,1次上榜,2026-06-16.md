# Win11Debloat 项目分析

> 一句话总结：Win11Debloat 是一款轻量级 PowerShell 脚本，用于移除 Windows 10/11 预装应用、禁用遥测追踪、关闭 AI 功能并进行系统定制，是 Windows 去臃肿和隐私保护的一站式解决方案。

---

## 基本信息

| 项目 | 详情 |
|------|------|
| 项目名称 | Win11Debloat |
| GitHub 地址 | https://github.com/Raphire/Win11Debloat |
| Stars | ~47,921 |
| Forks | ~1,932 |
| 许可证 | MIT License |
| 主要语言 | PowerShell |
| 作者 | @Raphire |
| 支持平台 | Windows 10、Windows 11 |
| 创建时间 | 2020-10-27 |
| 发布版本 | 32 个 Release |
| 提交记录 | 431 个 Commit |
| 最新版本 | 2026.06.14 |

---

## 解决什么问题

Windows 10 和 Windows 11 预装了大量用户可能不需要的应用（如 Candy Crush、Netflix、Copilot 等），同时系统默认开启了大量遥测数据收集、建议内容推送和 AI 功能，这些问题困扰着追求简洁和隐私的用户：

1. **预装应用泛滥**：OEM 厂商和微软预装了大量不需要的应用，占用磁盘空间和系统资源，影响系统启动速度。
2. **遥测与隐私问题**：Windows 默认收集大量遥测数据、位置信息和搜索历史，用户隐私难以保障。
3. **AI 功能强制推送**：Windows 11 24H2+ 强制集成 Copilot、Recall 等 AI 功能，用户难以简单关闭。
4. **手动设置繁琐**：通过系统设置和注册表逐一手动调整需要大量时间和专业知识，容易遗漏。
5. **缺乏统一工具**：市面上虽有各类 debloat 工具，但多数功能单一或过于激进，容易导致系统不稳定。

Win11Debloat 应运而生，以**安全、轻量、可逆、可定制**为设计原则，通过单一的 PowerShell 脚本覆盖从应用移除到系统定制的全方位需求，所有更改均可轻松恢复，降低用户使用风险。

---

## 核心功能

### 1. 预装应用移除（App Removal）

支持移除 90+ 个预装应用，分为三大类：

- **微软自家应用（38 个）**：3D Builder、3D Viewer、Bing 系列应用、Copilot、Cortana、Teams、Clipchamp、Xbox Console Companion、PC Manager 等
- **第三方应用（52 个）**：Netflix、Spotify、Facebook、Instagram、TikTok、Amazon、Candy Crush 系列游戏、Adobe Photoshop Express、WinZip 等
- **OEM 臃肿软件**：HP、Dell、Lenovo 等厂商预装的厂商工具和推广软件

支持通过配置文件（`Config/Apps.json`）自定义移除列表，也可通过命令行参数指定移除特定应用。

### 2. 隐私与建议内容（Privacy & Suggested Content）

- **禁用遥测**：关闭遥测数据收集、诊断数据和定向广告
- **禁用建议内容**：移除开始菜单、设置、通知和资源管理器中的提示和建议
- **禁用位置服务**：关闭位置功能并通过组策略锁定设置
- **禁用设备查找**：停止向微软发送周期性位置数据
- **禁用搜索历史**：清除本地搜索历史记录
- **禁用 Bing 集成**：移除 Windows 搜索中的 Bing 网络搜索、Bing AI 和 Cortana

### 3. AI 功能控制（AI Features）

针对 Windows 11 和 Copilot+ PC 的 AI 功能提供精细控制：

- **禁用 Copilot**：关闭并移除 Microsoft Copilot
- **禁用 Recall**：关闭 AI 快照历史工具（Copilot+ PC）
- **禁用 Click to Do**：关闭 AI 文本/图像分析工具
- **禁用 Edge AI / Paint AI / Notepad AI**：分别关闭各应用中的 AI 功能
- **禁用 AI 服务自动启动**：将 `WSAIFabricSvc` 设为手动启动

### 4. 系统与 Windows 更新（System & Windows Update）

- 控制自动更新行为
- 管理交付优化（Delivery Optimization）设置
- 支持创建系统还原点（24 小时内仅创建一次）
- 注册表自动备份（2026.05.10 版本起）

### 5. 界面外观定制（Appearance）

- 启用深色模式
- 禁用锁屏上的建议和提示
- 管理透明效果和动画
- 系统主题相关设置

### 6. 开始菜单与搜索（Start Menu & Search）

- 清除所有固定应用 / 替换固定应用模板
- 隐藏"推荐"区域并切换为"更多固定"
- 隐藏"所有应用"列表（Win 11）
- 更改"所有应用"视图样式（分类/网格/列表）
- 禁用 Phone Link 集成

### 7. 任务栏定制（Taskbar）

- 任务栏图标左对齐
- 按钮合并方式控制（始终/标签满时/从不）
- 多显示器任务栏模式（全部显示/仅主活动/当前活动）
- 搜索框控制（隐藏/图标/标签/完整搜索框）
- 隐藏任务视图、聊天按钮等

### 8. 文件资源管理器（File Explorer）

- 移除文件资源管理器中的建议和推广内容
- 清理资源管理器侧边栏中的多余项目
- 恢复经典上下文菜单

### 9. 多任务处理（Multi-tasking）

- 管理贴靠布局（Snap Layouts）设置
- 控制多任务处理相关功能

### 10. 可选 Windows 功能（Optional Windows Features）

- 管理可选 Windows 功能组件的启用和禁用

---

## 技术架构

| 类别 | 技术/方式 |
|------|-----------|
| 核心语言 | PowerShell |
| 入口脚本 | Win11Debloat.ps1 |
| 快速启动 | 一行 PowerShell IEX 命令远程下载执行 |
| 传统启动 | Run.bat 批处理文件 |
| 配置文件格式 | JSON（DefaultSettings.json、Apps.json） |
| 功能定义 | Assets/Features.json（完整功能列表） |
| 注册表备份 | 自动在修改前备份注册表 |
| 系统还原点 | 通过 PowerShell 创建 |
| 日志系统 | 支持自定义日志路径 |

### 项目结构

```
Win11Debloat/
├── Win11Debloat.ps1      # 核心脚本（主要逻辑）
├── Run.bat               # 传统启动入口
├── Config/               # 配置文件目录
│   ├── DefaultSettings.json  # 默认调优设置
│   └── Apps.json             # 默认移除应用列表
├── Regfiles/             # 注册表文件
├── Scripts/              # 辅助脚本
├── Schemas/              # JSON Schema 定义
└── Assets/               # 资源文件
    └── Features.json     # 完整功能参数列表
```

---

## 使用方式

### 快速方法（一行命令）

通过 PowerShell 直接从 GitHub 下载并运行：

```powershell
irm https://raw.githubusercontent.com/Raphire/Win11Debloat/master/Win11Debloat.ps1 | iex
```

### 传统方法

```bat
Run.bat
```

### 命令行高级用法

```powershell
# 应用默认设置（含应用移除）
.\Win11Debloat.ps1 -RunDefaults

# 仅应用默认调优（不移除应用）
.\Win11Debloat.ps1 -RunDefaultsLite

# 静默模式运行
.\Win11Debloat.ps1 -RunDefaults -Silent

# 移除特定应用
.\Win11Debloat.ps1 -RemoveApps -Apps "Microsoft.OneDrive,Microsoft.Whiteboard"

# 为其他用户应用更改
.\Win11Debloat.ps1 -RunDefaults -User "OtherUser"

# Sysprep 模式（影响新建用户）
.\Win11Debloat.ps1 -RunDefaults -Sysprep
```

### 配置文件自定义

修改 `Config/DefaultSettings.json` 中的 `"Value"` 字段来控制各项功能的启用/禁用：

```json
{
    "Name": "TaskbarAlignLeft",
    "Value": true
},
{
    "Name": "EnableDarkMode",
    "Value": true
}
```

修改 `Config/Apps.json` 中的 `"SelectedByDefault"` 字段来控制应用的默认移除选择。

---

## 安全与可逆性

Win11Debloat 的核心设计理念之一是**安全性**和**可逆性**：

1. **注册表备份**：自 2026.05.10 版本起，脚本在应用任何更改前自动创建系统注册表备份。
2. **系统还原点**：支持通过 `-CreateRestorePoint` 参数创建系统还原点，确保严重问题可回滚。
3. **应用可恢复**：几乎所有被移除的应用都可以通过 Microsoft Store 重新安装。
4. **配置可定制**：通过配置文件精确控制每项功能的开启和关闭，避免不必要的修改。
5. **详细日志**：所有操作均有日志记录，便于排查问题。

---

## 高级特性（系统管理员与高级用户）

- **强大的命令行接口**：支持数十个命令行参数，可精确控制每一项功能
- **静默执行模式**（`-Silent`）：无需用户交互，适合自动化部署
- **Windows Audit 模式支持**：可在系统审核模式下运行
- **跨用户修改**（`-User <USERNAME>`）：可为其他已登录过的用户账户应用设置
- **Sysprep 模式**（`-Sysprep`）：修改默认用户配置文件，影响所有新建账户
- **自定义配置文件**：支持通过 GUI 生成的配置文件重复使用
- **自定义应用列表生成器**：通过 `-RunAppsListGenerator` 生成自定义移除列表

---

## 应用场景

### 1. 新系统初始化

购买新电脑或重装系统后，使用 Win11Debloat 一键清理所有预装臃肿软件、禁用遥测和推送内容，获得干净的 Windows 环境。

### 2. 企业批量部署

IT 管理员利用命令行接口和静默模式，在批量部署时统一应用企业标准的安全和隐私策略，减少不必要的企业员工干扰。

### 3. 隐私保护

隐私敏感用户通过一键禁用遥测、位置服务、Bing 搜索等所有隐私相关功能，最大程度保护个人数据安全。

### 4. AI 功能管理

对于不希望使用 AI 功能的用户（尤其是 Copilot+ PC 用户），可精细控制 Recall、Copilot、Click to Do 等 AI 功能的启用和禁用。

### 5. 游戏性能优化

通过 `-RemoveGamingApps` 等参数移除 Xbox 相关冗余组件，配合系统服务优化，为游戏环境提供更纯粹的 Windows 体验。

### 6. 旧设备性能提升

移除不必要的预装应用和后台服务，释放系统资源，提升老旧硬件的运行效率。

---

## 与同类工具对比

| 特性 | Win11Debloat | O&O ShutUp10++ | Chris Titus Tech Debloat |
|------|-------------|-----------------|--------------------------|
| 语言 | PowerShell（开源） | C++（闭源） | PowerShell（开源） |
| 应用移除 | 支持（90+ 应用） | 不支持 | 支持 |
| 遥测禁用 | 支持 | 支持（更精细） | 支持 |
| AI 功能控制 | 支持（精细） | 部分支持 | 部分支持 |
| 可逆性 | 高（注册表备份+还原点） | 支持（可撤销） | 一般 |
| 配置文件 | JSON 配置文件 | GUI 界面 | 脚本内配置 |
| 命令行支持 | 完整 CLI | 有限 | 完整 CLI |
| 跨用户操作 | 支持 | 不支持 | 不支持 |
| Sysprep 支持 | 支持 | 不支持 | 不支持 |
| 开源协议 | MIT | 免费（非开源） | 开源 |
| 维护活跃度 | 高（431 commits） | 高 | 高 |

Win11Debloat 的独特优势在于**应用移除能力**和**系统管理员级功能**（跨用户、Sysprep）的结合，使其既是普通用户的首选，也是企业部署的有力工具。

---

## 相关链接

- GitHub 仓库：https://github.com/Raphire/Win11Debloat
- 项目 Wiki：https://github.com/Raphire/Win11Debloat/wiki
- 默认设置文档：https://github.com/Raphire/Win11Debloat/wiki/Default-Settings
- 命令行接口文档：https://github.com/Raphire/Win11Debloat/wiki/Command%E2%80%90line-Interface
- 恢复更改指南：https://github.com/Raphire/Win11Debloat/wiki/Reverting-Changes
- Releases 页面：https://github.com/Raphire/Win11Debloat/releases

---

> 一句话总结：Win11Debloat 是 Windows 去臃肿领域最受欢迎的开源工具，以近 4.8 万 Stars 证明了其价值——它安全、轻量、可逆、可定制，覆盖从隐私保护到 AI 功能管理的全方位需求，是每位 Windows 用户的系统优化利器。

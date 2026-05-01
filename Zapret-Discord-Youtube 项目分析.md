# Zapret-Discord-Youtube 项目分析

## 项目名称

**zapret-discord-youtube** — 俄罗斯 DPI 绕过工具，用于解除 Discord 和 YouTube 等服务的封锁

- **GitHub**: [Flowseal/zapret-discord-youtube](https://github.com/Flowseal/zapret-discord-youtube)
- **许可证**: MIT

---

## 项目概述

zapret-discord-youtube 是一个针对 Windows 平台的 DPI（深度包检测）绕过工具，由开发者 Flowseal 基于 bol-van 的 zapret 项目 fork 并优化而来。项目的核心目标是帮助用户在俄罗斯联邦通信监管局（Roskomnadzor）实施的互联网封锁下，正常访问 Discord、YouTube、Instagram、Telegram 等被限制的互联网服务。项目已获得 26,000+ Stars，是 GitHub 上俄罗斯用户群体中最受欢迎的开源工具之一。

DPI 绕过技术的原理是通过对网络数据包进行特定的修改（如伪造数据包、修改 TTL 值、注入干扰载荷等），使 ISP 的深度包检测设备无法正确识别和封锁特定协议的流量。与 VPN 不同，DPI 绕过工具不需要建立加密隧道或连接远程服务器，因此不会引入额外的网络延迟，也不需要消耗带宽资源。zapret-discord-youtube 使用 WinDivert 驱动在内核层面拦截和修改网络数据包，实现了高效的流量伪装。

项目提供了多种预配置的绕过策略（.bat 脚本），用户只需下载、解压并以管理员权限运行对应脚本即可。工具还支持作为 Windows 服务安装，实现开机自动启动和后台持续运行。项目内置了自动更新功能，可以定期更新 IPSet 列表和 Hosts 文件以适应不断变化的封锁规则。

---

## 核心功能

### 1. 多策略 DPI 绕过
提供多种预配置的绕过策略脚本，针对不同的封锁方式使用不同的数据包伪装技术（fake payload、TTL 修改、QUIC 伪装等），用户可逐一尝试找到最佳方案。

### 2. WinDivert 内核驱动
基于 WinDivert 实现内核级流量拦截和修改，性能开销极低，不影响正常网络通信速度。

### 3. Hosts 文件自动更新
自动更新 hosts 文件，将被封锁服务的域名指向正确的 IP 地址，绕过 DNS 层面的封锁。

### 4. IPSet 过滤
支持 IPSet 列表管理，对特定 IP 和域名进行过滤，支持自动更新列表以应对封锁规则的变更。

### 5. Windows 服务模式
支持作为 Windows 系统服务安装运行，开机自动启动，后台持续提供绕过功能，无需手动操作。

### 6. 游戏过滤模式
提供专门的游戏流量过滤模式，在绕过封锁的同时不影响在线游戏的正常连接。

### 7. 诊断工具
内置诊断功能，可检测 WinDivert 驱动状态、服务运行状态，帮助用户快速排查问题。

### 8. 广泛的服务覆盖
不仅支持 Discord 和 YouTube，还可用于绕过 Instagram、Telegram、Google Drive、Reddit 等多种被封锁服务的限制。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **编程语言** | Batchfile（71.5%）、PowerShell（28.5%） |
| **核心驱动** | WinDivert（内核级流量拦截） |
| **运行平台** | Windows |
| **底层项目** | Fork 自 bol-van/zapret（DPI bypass 多平台工具） |
| **安装方式** | 便携式（下载解压即用，无需安装） |
| **服务管理** | Windows 服务（winws.exe） |
| **最新版本** | 1.9.7b |
| **贡献者** | 39 人 |

---

## 项目亮点

### 零配置、开箱即用
用户只需下载解压、以管理员权限运行 .bat 脚本即可，无需复杂配置。相比 VPN 方案，不需要注册账号、选择服务器或安装额外软件，使用门槛极低。

### 无额外延迟，体验无损
与 VPN 建立加密隧道不同，DPI 绕过只在本地修改数据包特征，不会增加网络跳数或加密开销，因此不影响网络速度和延迟，特别适合对延迟敏感的应用场景。

### 持续维护和社区支持
项目活跃维护，已发布 37 个版本，持续更新绕过策略以应对 Roskomnadzor 不断升级的封锁手段。拥有 39 名贡献者和活跃的社区讨论区，用户反馈问题能快速得到响应。

### 开源透明，安全可信
完全开源（MIT 许可证），所有流量处理逻辑公开透明，不涉及任何第三方服务器或数据收集，用户可完全掌控自己的网络安全。

---

## 应用场景

### 俄罗斯境内用户访问被封锁服务
帮助俄罗斯用户在 Roskomnadzor 封锁下正常访问 Discord（语音通话、社区交流）、YouTube（视频观看）等日常必需的互联网服务。

### 企业远程协作
俄罗斯境内的跨国企业员工需要使用 Discord、Slack、Google Workspace 等协作工具时，可通过该工具绕过封锁保障正常工作。

### 游戏社区与直播
游戏玩家使用 Discord 进行语音组队、观看 YouTube 游戏直播时，该工具可在不影响游戏延迟的前提下保障流畅体验。

### 信息获取与自由通信
帮助用户绕过对 Instagram、Telegram 等社交媒体和通讯工具的封锁，获取不受限制的信息和进行自由通信。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 26,874 |
| **总 Forks** | 2,100 |
| **今日新增 Stars** | 165 |
| **许可证** | MIT |
| **主要语言** | Batchfile |

---

## 总结

zapret-discord-youtube 是一个专为 Windows 平台设计的 DPI 绕过工具，26k+ Stars，由 Flowseal 基于 bol-van/zapret 项目优化而来。它利用 WinDivert 内核驱动在本地对网络数据包进行伪装修改，帮助用户绕过俄罗斯 Roskomnadzor 对 Discord、YouTube、Instagram 等服务的封锁。与 VPN 方案相比，该项目具有零配置、无额外延迟、完全本地运行等优势，是当前俄罗斯用户群体中最受欢迎的互联网自由工具之一。

---

*数据来源：GitHub 仓库 (Flowseal/zapret-discord-youtube)（2026 年 5 月访问）*

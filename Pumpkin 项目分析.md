# Pumpkin 项目分析

## 项目名称
**Pumpkin** — 用 Rust 打造的高性能 Minecraft 服务器
- **GitHub**: [Pumpkin-MC/Pumpkin](https://github.com/Pumpkin-MC/Pumpkin)
- **许可证**: GPL-3.0
- **官网**: [pumpkinmc.org](https://pumpkinmc.org/)

---

## 项目概述

Pumpkin 是一个完全用 Rust 编写的 Minecraft 服务器软件，旨在提供高性能、高效率和高度可定制的游戏服务器体验，同时严格遵循原版 Vanilla 游戏机制。项目创建于 2024 年 7 月，目前处于活跃开发阶段（尚未发布 1.0.0 正式版），已积累 2,438 次提交和 8,200+ Stars。

Minecraft 服务器软件领域长期由 Java 生态主导（Spigot、Paper、Fabric 等），Pumpkin 的出现代表了「Rust 化」趋势向游戏服务器领域的延伸。利用 Rust 的零成本抽象、无 GC（垃圾回收）暂停和内存安全特性，Pumpkin 在多线程性能上具有天然优势。项目同时支持 Java 版和基岩版（Bedrock）的 Minecraft 协议，这意味着一个 Pumpkin 实例可以同时服务两种客户端。

项目采用模块化的 Rust workspace 架构，将协议处理、世界管理、背包系统、NBT 解析、编解码器、游戏数据、配置、插件 API 等解耦为独立的 crate，具有良好的代码组织结构和可扩展性。支持 Docker、Nix、Pterodactyl 面板和 Dev Container 等多种部署方式。

---

## 核心功能

| 功能模块 | 当前状态 | 说明 |
|----------|----------|------|
| **网络协议** | ✅ 已完成 | 服务器 Ping、加密、数据包压缩、Java/Bedrock 双协议支持 |
| **世界系统** | 🔄 进行中 | 玩家列表、计分板、世界加载/保存、光照、实体生成、Boss 栏、区块加载（三种策略）、方块保存 |
| **玩家系统** | 🔄 进行中 | 皮肤、传送、移动、动画、背包、经验值、饥饿值、副手、进度、进食 |
| **实体系统** | 🔄 进行中 | 玩家实体、状态效果、实体保存、Boss、村民；开发中：非生物实体、生物 AI |
| **服务器管理** | 🔄 进行中 | Query、RCON、粒子、聊天、权限、翻译；开发中：插件系统、命令系统 |
| **代理支持** | ✅ 已完成 | BungeeCord、Velocity 代理兼容 |
| **战斗系统** | 🔄 进行中 | 基础战斗开发中 |
| **红石系统** | 🔄 进行中 | 红石电路开发中 |
| **液体物理** | 🔄 进行中 | 水流/岩浆流模拟开发中 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | Rust（100%） |
| 架构模式 | 模块化 Workspace（13 个独立 crate） |
| 配置管理 | TOML |
| 容器化 | Docker + Docker Compose |
| 包管理 | Nix Flakes |
| 面板集成 | Pterodactyl Egg |
| 开发环境 | Dev Container |
| 插件系统 | WIT 接口（WebAssembly Component Model） |
| 过程宏 | pumpkin-macros / pumpkin-api-macros |

---

## 项目亮点

### Rust 在游戏服务器领域的极致性能探索

Minecraft 服务器是典型的 CPU 密集型 + IO 密集型混合负载：需要处理大量玩家并发连接（IO）、实时物理模拟和红石电路计算（CPU）、以及频繁的世界数据读写（IO）。Rust 的零成本抽象和无 GC 暂停特性使其在这个场景下具有独特优势——Java 版服务器在 GC 暂停时会导致 TPS（每秒 tick 数）下降，而 Rust 版可以保持稳定的 tick 频率。对于追求极致性能的大型服务器来说，这是一个关键差异。

### Java 版与基岩版双协议支持

Minecraft 的两个主要版本（Java 版和基岩版）使用完全不同的网络协议，传统上需要运行两个独立的服务器软件。Pumpkin 通过统一的协议处理层同时支持两种客户端，这意味着一个 Pumpkin 实例可以同时服务 PC 端和移动端/主机端玩家，简化了跨平台服务器的部署和管理。

### WIT 接口的插件系统设计

Pumpkin 的插件 API 采用 WIT（WebAssembly Interface Types）接口，这是一种基于 WebAssembly Component Model 的新一代跨语言接口标准。这意味着插件开发者可以用任何编译为 WASM 的语言（Rust、C++、Go、AssemblyScript 等）编写插件，而不是被限制在 Java 生态中。这种设计在 Minecraft 服务器领域是开创性的。

### 模块化 Workspace 架构的工程价值

13 个独立 crate 的模块化设计使得每个子系统可以独立开发、测试和替换。例如，NBT 解析（pumpkin-nbt）和编解码器（pumpkin-codecs）作为独立 crate 可以在其他 Rust 项目中复用。这种架构设计体现了 Rust 生态中「小 crate、强组合」的工程哲学。

---

## 应用场景

### 高性能 Minecraft 服务器托管

对于需要服务大量玩家（100+ 同时在线）的 Minecraft 服务器，Pumpkin 的多线程 Rust 实现可以提供比 Java 版服务器更稳定的 TPS 表现，尤其在红石电路密集或实体数量众多的场景下优势明显。

### 跨平台 Minecraft 社区服务器

双协议支持使 Pumpkin 非常适合需要同时服务 PC 玩家和移动端/主机端玩家的社区服务器。例如教育机构或家庭网络中，不同设备的学生或家庭成员可以使用各自平台上的 Minecraft 客户端连接同一个 Pumpkin 服务器。

### Minecraft 服务器技术研究与学习

对于对游戏服务器底层实现感兴趣的开发者，Pumpkin 的模块化 Rust 代码库是一个优秀的学习资源。从网络协议解析到世界管理、从实体系统到物理模拟，每个子系统都有清晰的代码边界，便于深入研究和理解 Minecraft 服务器的核心原理。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 8,224 |
| **总 Forks** | 580 |
| **主要语言** | Rust |
| **创建时间** | 2024-07-28 |
| **今日新增 Stars** | 96 |

---


---

## 📋 更新记录

### 更新 1 — 2026 年 07 月 25 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
Pumpkin 作为用 Rust 构建的高性能 Minecraft 服务器持续活跃开发，目前已有 2487 次提交。项目在协议支持方面进展显著：Java Edition 已支持加密、数据包压缩、服务器状态/Ping 等核心功能，Bedrock Edition 正在开发中。世界系统支持多种区块加载模式（Vanilla、Linear、Pump），实体系统支持玩家皮肤、传送、移动、动画、物品栏、经验、饥饿等。服务器功能已支持 Bungeecord 和 Velocity 代理。项目采用模块化架构，核心模块包括 pumpkin-protocol、pumpkin-world、pumpkin-inventory、pumpkin-nbt 等，支持 Docker 和 Nix flakes 部署。随着 Rust 在游戏服务器领域的应用日益广泛，Pumpkin 作为完全用 Rust 编写的 Minecraft 服务器替代方案受到越来越多关注。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 8,224 | 9,484 | +1,260 |
| 总 Forks | 537 | 631 | +94 |

**核心变化概要**：
- 2487 次提交，项目持续活跃开发
- Java Edition 核心协议基本完备，Bedrock Edition 开发中
- 支持 Bungeecord/Velocity 代理
- 模块化 Rust 架构（pumpkin-protocol/world/inventory/nbt）
- 今日新增 565 Stars，总 Star 接近 10,000

---

## 📋 更新记录

### 更新 1 — 2026 年 7 月 26 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：项目再次登上 GitHub Trending 榜单，显示这款 Rust 编写的 Minecraft 服务器持续受到关注。自上次分析以来，Pumpkin 已接近 v0.1.0 正式发布，支持 Minecraft 协议 1.21.11，同时支持 Java 和 Bedrock 两个版本。其宣称的性能指标包括比 Vanilla 快 1000 倍的启动速度和仅 1/18 的内存占用已通过社区测试验证。主要新增功能包括插件系统、权限系统和配置系统的完善。OceanHost 已宣布赞助 PumpkinMC，将很快提供托管服务。多位 YouTube 创作者发布评测视频，认为其有潜力挑战 PaperMC。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 8,224 | 9,484 | +1,260 |
| 总 Forks | 500 | 615 | +115 |

**核心变化概要**：
- 接近 v0.1.0 正式发布，支持 Minecraft 协议 1.21.11
- 同时支持 Java 和 Bedrock 两个版本
- 性能指标经社区测试验证，OceanHost 宣布赞助
- 新增插件系统、权限系统和配置系统
- 多位 YouTube 创作者评测，认为有潜力挑战 PaperMC

## 总结

Pumpkin 是 Minecraft 服务器 Rust 化浪潮中的领军项目，以 8.2K Stars 证明了社区对高性能游戏服务器软件的强烈需求。其 Java/基岩版双协议支持和 WIT 接口插件系统设计在同类项目中独具特色，模块化的 Rust workspace 架构也为游戏服务器开发树立了工程标杆。虽然尚未发布 1.0.0 正式版，但活跃的提交节奏（2,438 次）和完善的部署支持（Docker/Nix/Pterodactyl）表明项目正在快速成熟。

---

*数据来源：GitHub 仓库 (Pumpkin-MC/Pumpkin)，2026 年 7 月 24 日 访问*
*最近更新：2026 年 7 月 24 日
*首次分析：2026 年 7 月*
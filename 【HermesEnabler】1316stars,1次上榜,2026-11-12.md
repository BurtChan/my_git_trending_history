# HermesEnabler 项目分析

## 项目名称
**HermesEnabler 2** — 在任意 Apple Watch 上启用 Hermès 官方表盘的工具
- **GitHub**: [pookjw/HermesEnabler](https://github.com/pookjw/HermesEnabler)
- **许可证**: MIT
- **语言**: Objective-C

---

## 项目概述

HermesEnabler 2 是一个针对 watchOS 的小型系统级工具，解决一个非常具体但真实存在的用户痛点：Hermès 表盘是 Apple Watch 上最受欢迎的官方表盘之一，但苹果将它与「Apple Watch Hermès」硬件型号绑定——普通 Apple Watch 用户即使愿意付费也无法使用。HermesEnabler 通过读取和修改设备的 MobileGestalt 配置，让系统认为当前设备是 Hermès 型号，从而解锁全部 Hermès 表盘。

项目以 IPA 侧载（Sideloadly）或 Xcode 直接构建两种方式分发，无需越狱，仅支持 watchOS 27.0 至 27.3 beta 1。它内置了完整的备份与恢复机制：修改 MobileGestalt 前自动备份，删除应用前必须先在应用内恢复备份，避免设备配置异常。

值得注意的是，该项目内置了来自 Gester 项目的代码，并且开发者明确标注「Use at your own risk」。单日 +390 Stars 的增速（总 1,316）说明这一「解锁付费硬件专属功能」的诉求在 Apple Watch 用户中相当普遍。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| Hermès 表盘解锁 | 修改 MobileGestalt 使普通 Apple Watch 识别为 Hermès 型号，解锁全部 Hermès 表盘 |
| MobileGestalt 备份/恢复 | 修改前自动备份设备配置，应用内一键恢复，防止配置损坏 |
| IPA 侧载安装 | 通过 Sideloadly 安装 IPA 到 Apple Watch，无需越狱 |
| Xcode 源码构建 | 提供 Xcode 工程，可将 Apple Watch 作为运行目标直接构建部署 |
| 多语言支持 | 英/韩/简繁中文/日/西/法/德/葡九种语言 README |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 开发语言 | Objective-C |
| 目标平台 | watchOS 27.0 – 27.3 beta 1 |
| 系统机制 | MobileGestalt 配置修改 |
| 分发方式 | IPA 侧载（Sideloadly）/ Xcode 构建 |
| 依赖代码 | Gester（sasobhabha/Gester） |

---

## 项目亮点

### 1. 精准命中硬件歧视痛点
Hermès 表盘本质上是软件功能，却被苹果绑定在特定硬件型号上。这个项目用极小的代码量撬动了数百万普通 Apple Watch 用户的潜在需求——单日近 400 Star 的增长正是这种「一人写、万人需」项目的典型爆发曲线。

### 2. 安全意识内建
修改 MobileGestalt 属于系统级敏感操作，项目在应用内强制要求「删除前先恢复备份」的安全路径，并固定 Bundle Identifier 保证更新时数据保留，把用户最可能踩的坑都提前堵住了。

### 3. 无需越狱的轻量方案
相比传统的越狱方案，IPA 侧载的门槛低得多，普通用户跟着 README 四步即可完成，这也是它能快速传播的关键。

---

## 应用场景

### 1. 普通 Apple Watch 解锁 Hermès 表盘
非 Hermès 型号用户免费获得官方付费型号专属的全部 Hermès 表盘（含表盘配色与表带搭配界面）。

### 2. watchOS 版本兼容研究
对 MobileGestalt 机制和 watchOS 系统配置感兴趣的逆向工程/系统研究者的参考实现。

### 3. 侧载工具链实践
学习 Sideloadly 侧载、固定 Bundle ID 管理与 Apple Watch 应用安装流程的实操案例。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 1,316 |
| 总 Forks | 124 |
| 今日新增 | +390 |
| Open Issues | 50 |
| 主要语言 | Objective-C |
| 许可证 | MIT |
| 创建时间 | 2024-12-14 |

---

## 总结

HermesEnabler 2 用一个 Objective-C 小工具解决了一个被苹果人为制造的支付墙——Hermès 表盘的硬件绑定，凭借「无需越狱 + 备份可恢复 + 四步侧载」的低门槛体验在 watchOS 27 时代迅速走红，是典型的「系统小补丁、用户大需求」型爆发项目。

---

*数据来源：GitHub 仓库 (pookjw/HermesEnabler)，2026 年 11 月访问*

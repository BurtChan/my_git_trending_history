# Headunit Revived 项目分析

## 项目名称
**Headunit Revived** — 将 Android 平板或手机转变为 Android Auto 车载接收器的开源应用
- **GitHub**: https://github.com/andreknieriem/headunit-revived
- **许可证**: AGPL-3.0

---

## 项目概述

Headunit Revived 是原始 headunit 项目的复兴分支，旨在让任何支持 USB Host 模式的 Android 设备（如平板电脑、旧手机等）充当 Android Auto 的接收端。用户只需将开启了 Android Auto 的手机连接到运行该应用的设备上，即可在更大的屏幕上使用导航、音乐、通话等 Android Auto 功能，无需购买专用的车载主机。

项目自 2019 年 2 月创建以来，已累计发布 73 个版本，拥有超过 1,184 次提交，展现出极高的开发活跃度和社区维护热情。它同时上架了 Google Play 和 Amazon Appstore，降低了普通用户的安装门槛。

该应用提供了三种连接方式：传统的有线 USB 直连、通过无线 Helper 模块实现 Wi-Fi 连接（最为可靠），以及通过 Intent 广播触发的无线连接方式（可配合 Tasker、MacroDroid 或 ADB 命令实现自动化）。无论哪种方式，都能稳定地将 Android Auto 界面投射到接收设备上。

## 核心功能

| 功能 | 描述 |
|------|------|
| Android Auto 接收 | 将 Android 设备作为 Android Auto 的显示与交互终端 |
| 有线 USB 连接 | 通过 USB 数据线直连，稳定可靠 |
| 无线 Helper 连接 | 通过 Wi-Fi 无线连接，体验最流畅可靠 |
| Intent 无线连接 | 通过广播 Intent 触发连接，支持 Tasker/MacroDroid/ADB 自动化 |
| 导航支持 | 支持 geo:、google.navigation:、android.intent.action.NAVIGATE 等导航协议 |
| MediaSession | 支持 MediaSession 媒体控制，可操控音乐播放等 |
| 多平台分发 | 同时上架 Google Play 和 Amazon Appstore |

## 技术栈

| 组件 | 技术 |
|------|------|
| 开发语言 | Kotlin |
| 目标平台 | Android 4.1+（API 16） |
| 硬件要求 | USB Host 模式 |
| 分发渠道 | Google Play、Amazon Appstore |
| 开源协议 | AGPL-3.0 |

## 项目亮点

1. **项目复兴精神**：作为已停滞的原始 headunit 项目的社区复兴分支，展现了开源社区的强大生命力，持续迭代至今已有 73 个版本和 1,184 次提交。
2. **多连接方式设计**：提供有线、无线 Helper、Intent 自动化三种连接方式，满足不同使用场景和技术水平的用户需求，其中 Intent 连接方式对自动化玩家尤为友好。
3. **极低硬件门槛**：最低仅需 Android 4.1+ 系统和 USB Host 支持即可运行，用户可以充分利用闲置的旧手机或廉价平板打造车载 Android Auto 系统。
4. **便捷的分发渠道**：同时上架 Google Play 和 Amazon Appstore，普通用户无需 sideload 即可安装，降低了使用门槛。

## 应用场景

1. **DIY 车载信息娱乐系统**：将旧平板安装在车内仪表台上，连接带有 Android Auto 的手机，打造低成本的车机替代方案。
2. **自行车/摩托车导航终端**：将手机固定在车把上作为 Android Auto 源，通过无线连接投射到背包中的平板或头盔显示器上查看导航。
3. **桌面开发与测试**：开发者可利用该应用在普通 Android 设备上测试 Android Auto 应用的兼容性和显示效果。
4. **智能家居/固定显示终端**：在家中固定一块平板作为 Android Auto 的常驻显示设备，通过无线方式连接手机进行媒体播放或信息查看。

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Star 数 | 1,359 |
| 总 Fork 数 | 112 |
| 今日新增 Star | 79 |
| 主要语言 | Kotlin |
| 发布版本数 | 73 |
| 总提交数 | 1,184 |
| 创建时间 | 2019-02-08 |

## 总结

Headunit Revived 是一个极具实用价值的开源 Android Auto 接收器应用，它以 Kotlin 编写、采用 AGPL-3.0 协议开源，通过有线 USB、无线 Helper 和 Intent 自动化三种连接方式，让任意支持 USB Host 的 Android 设备都能成为 Android Auto 终端。该项目凭借低硬件门槛、多分发渠道和活跃的社区维护（1,184 次提交、73 个版本），为 DIY 车载系统和 Android Auto 开发测试提供了优秀的解决方案，今日获得 79 个新增 Star 也印证了其持续增长的社区影响力。

---

*数据来源：GitHub 仓库 (andreknieriem/headunit-revived)，2026 年 6 月访问*

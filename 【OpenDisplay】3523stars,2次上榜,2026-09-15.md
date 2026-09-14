# OpenDisplay 项目分析

## 项目名称
**OpenDisplay** — 把闲置 Apple 设备变成 Mac 的第二块显示器：免费、开源、无订阅
- **GitHub**: [peetzweg/opendisplay](https://github.com/peetzweg/opendisplay)
- **许可证**: GPL-3.0（v0.4.x 及之前为 MIT）

---

## 项目概述

OpenDisplay 解决的是一个"早已被解决但每个方案都有坑"的问题：把 iPhone、iPad 或闲置 Mac 变成 Mac 的真·扩展显示器。Apple Sidecar 免费但要求两台设备同一 Apple ID、完全不支持 iPhone；Duet Display 转向了订阅制；Luna Display 需要购买硬件加密狗。OpenDisplay 给出了缺失的那个选项：免费、开源、无需账号、无需加密狗，用你手上已有的 iOS 设备做一块真正意义上的第二屏——不是镜像，而是可以在系统设置里拖拽排列的真扩展屏。

技术上它走的是一条相当硬核的路线：Mac 侧用 `CGVirtualDisplay` 私有 API（BetterDisplay 和 DeskPad 同款）创建虚拟显示器，ScreenCaptureKit 采集画面，VideoToolbox 硬件 H.264 实时编码（无 B 帧），TCP_NODELAY + 丢帧背压 + 关键帧恢复，iOS 侧用 `AVSampleBufferDisplayLayer` 解码渲染；触控输入通过 JSON 控制消息回传、`CGEvent` 注入实现点击/拖拽/双指滚动。传输层"手机监听、Mac 连接"的顺序设计让同一套代码同时工作在 USB（走 macOS 内置 usbmuxd）与 WiFi（Bonjour 自动发现）之上。

项目 2026 年 6 月中旬创建，三个月收获 3,300+ Stars，当前单日 +314、140 个开放 issue 反映出社区热度与活跃的反馈流。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 真扩展屏 | macOS 把设备当作真实第二显示器（可拖窗口、可在系统设置排列），镜像模式亦可切换 |
| USB 有线低延迟 | 走 macOS 内置 usbmuxd 经 Lightning/USB-C 传输，即插即用，无网络抖动 |
| WiFi 零配置 | iPhone 通过 Bonjour 自广播，Mac 侧下拉列表直接选择 |
| Retina/HiDPI | 虚拟显示器逐像素匹配设备面板（@2x），文字锐利 |
| 触控输入 | iPhone 变成 macOS 触摸屏：点按点击、拖拽拖拽、双指滚动近似触控板手感；Apple Pencil 在路线图中 |
| 竖屏横屏 | 旋转设备即以原生分辨率重建为竖向显示器 |
| 闲置 Mac 做显示器 | 老 Mac 装 OpenDisplay Receiver（macOS 12+），其他 Mac 可经 WiFi 或雷雳/网线以原生 Retina 分辨率扩展上去 |
| 自托管隐私 | 画面不经过任何人的服务器：两个小应用、一条 TCP 连接而已 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 主语言 | Swift |
| 虚拟显示器 | CGVirtualDisplay（CoreGraphics 私有 API） |
| 画面采集 | ScreenCaptureKit |
| 视频编码 | VideoToolbox H.264（硬件实时模式） |
| 传输 | TCP（4 字节长度前缀 + Annex B 帧）+ usbmuxd / Bonjour |
| iOS 渲染 | AVSampleBufferDisplayLayer |
| 输入回传 | JSON 控制消息 + CGEvent 注入 |
| 协议文档 | PROTOCOL.md / COMPATIBILITY.md 明文规范 |

---

## 项目亮点

### 对比表直接打三大商业方案
README 首屏的价格/能力对比表（对 Sidecar、Duet、Luna）逐项列明：iPhone 做屏、不同 Apple ID、有线、真扩展、触控、自托管可审计——OpenDisplay 是唯一全勾的选项，价值主张一目了然。

### 双传输同构的工程巧思
"手机监听、Mac 连接"的顺序让 USB（usbmuxd 隧道）和 WiFi 共用完全相同的代码路径；设备端上报原生面板尺寸，Mac 精确以一半 points 建 @2x 虚拟屏再回推像素。协议（framing、发现、视频格式、每条控制消息）全部写进 PROTOCOL.md，跨版本演进有 COMPATIBILITY.md 兜底——这是开源硬件相邻项目里少见的规范意识。

### 坦诚的边界声明
项目明说 CGVirtualDisplay 是私有 API，"这正是它上不了 App Store、只能住在 GitHub 的原因"，并指路 BetterDisplay/DeskPad 同源先例；License 章节说明 v0.4.x 前是 MIT、之后转 GPL-3.0 且旧版本仍可按 MIT 取用。对限制与历史的诚实陈述降低了使用者的预期风险。

---

## 应用场景

### 闲置 iOS 设备再利用
抽屉里的旧 iPhone/iPad 立刻变成 Mac 的竖屏状态栏、聊天窗或文档屏，零成本扩展工作区；家中多 Mac 的用户还能让老 MacBook 当副屏。

### 出差/移动办公轻装上阵
不带便携显示器，一根 USB 线 + 手机即可获得低延迟第二屏，有线模式摆脱会议 WiFi 的抖动。

### 隐私敏感环境
投屏内容不出本机局域网/USB 链路，适合代码评审、财务报表等不方便经过第三方云服务的场景。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ 总 Stars | 3,523 |
| 🍴 总 Forks | 246 |
| 📈 今日新增 | +205 |
| 📅 创建时间 | 2026 年 6 月 10 日 |
| 📄 开源协议 | GPL-3.0（≤v0.4.x 为 MIT） |
| 🏷️ 主要标签 | macos, iphone, ipad, swift, virtual-display, second-monitor, sidecar, duet-display |

---

## 📋 更新记录

### 更新 1 — 2026 年 9 月 15 日（连续第二天登上 Trending）

OpenDisplay 连续第二天登上 Trending：Star 从 3,318 增至 3,523（+205），Fork 从 239 增至 246（+7）。基于 CGVirtualDisplay 私有 API + 硬件 H.264 编码的极简自托管架构，使其作为「免费的 iPad 第二屏」方案持续吸引 macOS/iOS 用户的关注，三天内两度在榜。

**Star 数据**

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|------|------|------|
| 总 Stars | 3,318 | 3,523 | +205 |
| 总 Forks | 239 | 246 | +7 |
| 今日新增 | — | 258 | — |

**核心变化**

- Star 3,318 → 3,523（+205），两日在榜累计 +519
- Fork 239 → 246（+7），自托管部署实践稳步增长

---

## 总结

OpenDisplay 用 CGVirtualDisplay 私有 API + 硬件 H.264 + 一条 TCP 连接的极简自托管架构，把 Sidecar/Duet/Luna 各自的坑全部填平，三个月 3,300 星证明"免费的第二屏"是真实而普遍的需求。

---

*数据来源：GitHub 仓库 (peetzweg/opendisplay)，2026 年 9 月 15 日访问*
*首次分析：见文件头部 | 最近更新：2026 年 9 月 15 日*

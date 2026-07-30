# WorldMonitor 项目分析

## 项目名称

**World Monitor** — 实时全球情报态势感知仪表盘，AI 驱动的新闻聚合、地缘政治监控与基础设施追踪平台

- **GitHub**: [koala73/worldmonitor](https://github.com/koala73/worldmonitor)
- **许可证**: GNU AGPL v3

---

## 项目概述

World Monitor 是一个开源的实时全球情报监控仪表盘，由开发者 Elie Habib（koala73）创建。它将 AI 驱动的新闻聚合、地缘政治事件追踪、军事态势监控、金融信号分析和关键基础设施态势感知整合到一个统一的界面中。项目在 GitHub 上获得 48,900+ Stars，83 位贡献者参与开发。

项目的核心理念是**一个屏幕、全球态势**：用户可以通过交互式 3D WebGL 地球和各种面板组件，实时了解全球正在发生的重大事件，包括军事冲突、自然灾害、金融市场异动、网络中断等。平台提供多种变体版本，分别聚焦地缘政治（World Monitor）、科技产业（Tech Monitor）、全球金融（Finance Monitor）和正面新闻（Happy Monitor），满足不同领域的监控需求。

World Monitor 强调隐私与本地化处理——其本地 AI 摘要功能基于 Transformers.js（ONNX）实现，所有数据均在用户设备上进行推理，不将任何数据上传到云端。项目支持 Web、PWA 和桌面端（Windows/macOS/Linux，基于 Tauri）多种部署方式，可自托管部署到 Vercel 或本地运行。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **AI 新闻聚合** | 整合 100+ 精选新闻源，AI 自动生成情报简报 |
| **3D 地理可视化** | 基于 deck.gl + MapLibre GL JS 的 3D WebGL 地球，支持 40+ 可切换数据图层 |
| **实时军事追踪** | 追踪军机飞行、海军舰艇动向和卫星火点检测 |
| **基础设施监控** | 实时监控全球网络中断、电力异常等关键基础设施状态 |
| **金融信号监测** | 跟踪全球金融市场信号、央行政策和 WTO 贸易动态 |
| **信号情报系统** | 实时监控 12 种信号类型，覆盖多领域异常检测 |
| **本地 AI 摘要** | 基于 Transformers.js 的浏览器端 AI 推理，数据不出设备 |
| **多平台支持** | Web 应用、PWA、原生桌面客户端（Windows/macOS/Linux） |
| **多种变体** | World/Tech/Finance/Happy Monitor 四种主题变体，聚焦不同领域 |
| **视频直播流** | 集成 150+ RSS 源和实时视频流，直接在仪表盘内观看 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | TypeScript 5.x（57.5%）、JavaScript（37.6%） |
| **构建工具** | Vite |
| **地图渲染** | deck.gl + MapLibre GL JS |
| **桌面框架** | Tauri（Rust 内核，0.3%） |
| **浏览器 ML** | Transformers.js（ONNX 格式） |
| **测试框架** | Playwright |
| **缓存** | Upstash Redis |
| **部署** | Vercel Edge Functions |
| **传输中继** | Railway（Node.js） |
| **样式** | CSS（3.8%） |
| **许可证** | GNU AGPL v3 |

---

## 项目亮点

### 🌍 全域态势感知
将地缘政治、军事动态、自然灾害、金融信号、网络状态等多维度情报整合在同一仪表盘，提供前所未有的全球态势感知能力，真正实现"一个屏幕了解全球"。

### 🔒 隐私优先的本地 AI
基于 Transformers.js + ONNX 的浏览器端 AI 推理，所有智能分析在用户本地完成，不依赖云端 API，完全保护用户隐私和敏感查询数据。

### 🗺️ 3D 交互式地球
基于 deck.gl 和 MapLibre GL JS 构建的高性能 3D WebGL 地球，支持 40+ 可切换数据图层（军事、金融、卫星、气候等），提供直观的地理空间可视化体验。

### 🧩 多变体架构
独创的多变体设计模式，同一套技术栈衍生出 World Monitor（地缘政治）、Tech Monitor（科技产业）、Finance Monitor（全球金融）、Happy Monitor（正面新闻）四种专注不同领域的监控平台。

---

## 应用场景

### 📰 新闻记者与媒体
监控突发新闻，识别虚假信息和宣传内容，导出 AI 生成的情报简报用于报道参考，提升新闻生产效率和准确性。

### 🛡️ 安全专业人员
追踪全球冲突区域动态、军事部署变化和网络威胁态势，结合信号情报系统进行安全评估和风险预警。

### 💹 金融分析师
识别全球市场趋势、央行政策信号和贸易政策变化，结合地缘政治风险分析辅助投资决策。

### 🏛️ 学术研究与 NGO
进行冲突发生、升级和解决的量化研究，监控人道主义数据和人口暴露情况，为政策制定提供数据支撑。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 48,900+ |
| **总 Forks** | 8,000+ |
| **今日新增 Stars** | ~343 |
| **许可证** | GNU AGPL v3 |
| **主要语言** | TypeScript |
| **贡献者** | 83 人 |
| **发布版本** | 43 个 |

---

---

## 📋 更新记录

### 更新 1 — 2026 年 7 月 28 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
WorldMonitor 持续保持开源情报（OSINT）领域的领先地位，Stars 从约 63.5K 增长至约 74.8K，单日新增 3,175 颗 Star。技术架构进一步扩展：新增 **MCP Server**（Streamable HTTP 端点 `worldmonitor.app/mcp`）、**REST API**（OpenAPI 规范）及 **Python/Ruby/Go 三语言零依赖 SDK**，支持 Agent 驱动的程序化查询。CLI 工具 `npx worldmonitor` 可直接执行临时查询。Agent 发现机制通过 `.well-known/` 下的 `llms.txt`、`agent-skills` manifest 和 `api-catalog` 实现标准化服务暴露。

数据源方面，外部数据提供商扩展至 **65+ 个**，覆盖地缘政治、金融、能源、气候、航空、网络、军事、基础设施和新闻情报 9 大领域，500+ 策展信息流由 35 个源组的新鲜度监控器追踪。**国家不稳定指数（CII）v8** 对 31 个一级国家进行服务器端权威压力评分。

部署架构升级：Vercel Edge Functions（60+）+ Railway 中继 + Redis（Upstash）三级缓存 + CDN + Service Worker。协议层使用 Protocol Buffers 定义 **281 个 proto** 和 **35 个服务**。安全方面，Cody Richard 于 2026 年披露了三项安全发现（IPC 命令暴露、渲染器到 sidecar 信任边界分析、fetch patch 凭证注入架构），项目已修复。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 63,552 | 74,786 | +11,234 |
| 总 Forks | 10,801 | 10,801 | - |

**核心变化概要**：
- 新增 MCP Server、REST API 及 Python/Ruby/Go SDK，支持 Agent 驱动查询
- 外部数据提供商扩展至 65+，500+ 策展信息流覆盖 9 大领域
- CII v8 对 31 个一级国家进行服务器端权威评分
- Protocol Buffers 定义 281 个 proto、35 个服务
- 6 个站点变体（World/Tech/Finance/Commodity/Happy/Energy）和 Tauri 2 桌面应用均稳定运行

---

### 更新 1 — 2026 年 7 月 29 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
WorldMonitor 持续快速迭代，近期新增多项重要功能：引入 **Telegram Intel 面板**用于社交情报监控，将 **伊朗打击事件**集成至 CII 评分和国家简报中；新增 **Security Advisories 面板**展示政府旅行安全警报；为实时新闻检测添加住宅代理和 gzip 解压缩支持。基础设施方面，新增 **Cloudflare 边缘缓存**，并将 52 个 API 端点从 POST 转换为 GET 以启用边缘缓存，显著提升全球访问性能。

- Star 持续高速增长，从 74,786 增长至 75,800
- 社区活跃度显著提升

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 74,786 | 75,800 | +1,014 |
| 总 Forks | 10,801 | 11,300 | +499 |

**核心变化概要**：
- 新增 Telegram Intel 面板，支持社交情报实时监控
- 伊朗打击事件集成至 CII v8 评分体系和国家简报
- 新增 Security Advisories 面板，展示政府旅行安全警报
- 引入 Cloudflare 边缘缓存，52 个 API 端点转为 GET 支持边缘缓存
- 新增复合升级告警（军事行动 + 地缘政治目标）和用户面板自由调整大小功能

## 总结

World Monitor 是一款**开源实时全球情报态势感知平台**，76.8k+ Stars。它基于 TypeScript + Vite + deck.gl 构建，将 AI 新闻聚合、地缘政治监控、军事追踪、金融信号分析和基础设施监测整合到统一的 3D 交互式仪表盘中。项目最大的亮点在于隐私优先的本地 AI 推理（Transformers.js + ONNX）和多变体架构设计（World/Tech/Finance/Happy 四种版本），适用于新闻媒体、安全分析、金融研究和学术研究等多个领域，是开源情报（OSINT）领域的重要工具。

---

## 📰 最新动态

### 2026年7月31日 — Star 数突破 76,000，生态持续扩张

WorldMonitor 在过去一周内 Star 数从约 72,000 飙升至 76,800，单周增长约 4,800 颗，今日再次以 +3,175 的单日增速登上 GitHub Trending 榜首。项目生态规模已相当庞大：**65+ 外部数据提供商**覆盖地缘政治、金融、能源、气候、航空、网络、军事、基础设施和新闻情报 9 大领域，**500+ 策展信息流**横跨 15 个类别，由 AI 实时综合为情报简报。地图可视化引擎全面升级，支持 globe.gl 3D 地球和 deck.gl WebGL 平面地图**双引擎模式，56 种地图图层类型**，实现军事、经济、灾害和升级信号的跨流关联分析。

项目已从单纯的 Web 应用演进为全栈情报平台：**6 个站点变体**（World/Tech/Finance/Commodity/Happy/Energy）各自聚焦不同领域，**Tauri 2 原生桌面应用**覆盖 macOS、Windows 和 Linux 三大平台。开发者工具链日趋完善——**MCP Server 端点**支持 Agent 驱动的程序化查询，Protocol Buffers 协议层定义了 **290 个 proto 和 35 个服务**，Python、Ruby、Go 三语言零依赖 SDK 以及 `npx worldmonitor` CLI 工具为开发者提供了灵活的集成方式。**国家不稳定指数（CII）v8** 对 31 个一级国家进行权威压力评分，金融雷达覆盖 29 个证券交易所、大宗商品和加密货币，提供 7 信号市场综合指数。项目支持 25 种语言（含 RTL 布局），所有 AI 功能均可通过 Ollama 在本地运行，无需 API 密钥，充分体现了"隐私优先"的设计理念。详见 → [2026-07-31 更新](./2026-07-31_WorldMonitor_更新.md)

---

### 2026年7月24日 — Star 数逼近 72,000，今日爆发增长 3,196 颗

WorldMonitor 今日单日新增 3,196 颗 Star，Star 总数从上次分析的 64,730 增长至 71,228。项目近期在移动端体验、边缘缓存策略和世界时钟面板等方面持续改进。详见 → [2026-07-24 更新](./2026-07-24_WorldMonitor_更新.md)

---

*数据来源：GitHub 仓库 (koala73/worldmonitor)，2026 年 7 月 24 日 访问*
*数据来源：GitHub 仓库 (koala73/worldmonitor), 2026 年 7 月访问*
*首次分析：2026 年 7 月 | 最近更新：2026 年 7 月*
---
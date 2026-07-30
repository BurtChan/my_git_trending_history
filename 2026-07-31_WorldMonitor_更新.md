# WorldMonitor 更新 — 2026年7月31日

## 项目基本信息

- **项目名称**: World Monitor
- **GitHub**: [koala73/worldmonitor](https://github.com/koala73/worldmonitor)
- **许可证**: AGPL-3.0
- **更新原因**: 再次登上 GitHub Trending 榜单，单日新增 3,175 颗 Star

---

## 最新 Star 数据

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 72,000 | 76,800 | +4,800 |
| 总 Forks | 10,200 | 11,400 | +1,200 |
| Watching | - | 459 | - |
| 总 Commits | - | 5,191 | - |
| 今日新增 Stars | - | 3,175 | - |

---

## 更新概要

### 2026年7月31日 — Star 数突破 76,000，生态持续扩张

WorldMonitor 在过去一周内 Star 数从约 72,000 飙升至 76,800，单周增长约 4,800 颗，今日再次以 +3,175 的单日增速登上 GitHub Trending 榜首。项目生态规模已相当庞大：**65+ 外部数据提供商**覆盖地缘政治、金融、能源、气候、航空、网络、军事、基础设施和新闻情报 9 大领域，**500+ 策展信息流**横跨 15 个类别，由 AI 实时综合为情报简报。地图可视化引擎全面升级，支持 globe.gl 3D 地球和 deck.gl WebGL 平面地图**双引擎模式，56 种地图图层类型**，实现军事、经济、灾害和升级信号的跨流关联分析。

项目已从单纯的 Web 应用演进为全栈情报平台：**6 个站点变体**（World/Tech/Finance/Commodity/Happy/Energy）各自聚焦不同领域，**Tauri 2 原生桌面应用**覆盖 macOS、Windows 和 Linux 三大平台。开发者工具链日趋完善——**MCP Server 端点**支持 Agent 驱动的程序化查询，Protocol Buffers 协议层定义了 **290 个 proto 和 35 个服务**，Python、Ruby、Go 三语言零依赖 SDK 以及 `npx worldmonitor` CLI 工具为开发者提供了灵活的集成方式。**国家不稳定指数（CII）v8** 对 31 个一级国家进行权威压力评分，金融雷达覆盖 29 个证券交易所、大宗商品和加密货币，提供 7 信号市场综合指数。项目支持 25 种语言（含 RTL 布局），所有 AI 功能均可通过 Ollama 在本地运行，无需 API 密钥，充分体现了"隐私优先"的设计理念。

---

## 关键数据一览

| 维度 | 数值 |
|------|------|
| 数据提供商 | 65+ |
| 策展信息流 | 500+ |
| 信息类别 | 15 |
| 地图图层类型 | 56 |
| 覆盖国家（CII v8） | 31 |
| 股票交易所 | 29 |
| 站点变体 | 6 |
| 支持语言 | 25 |
| Proto 定义 | 290 |
| gRPC 服务 | 35 |
| Vercel Edge Functions | 60+ |

## 技术架构

| 组件 | 技术 |
|------|------|
| 核心语言 | Vanilla TypeScript |
| 构建工具 | Vite |
| 3D 地球 | globe.gl + Three.js |
| 平面地图 | deck.gl + MapLibre GL |
| 桌面框架 | Tauri 2（Rust），Node.js sidecar |
| AI/ML | Ollama / Groq / OpenRouter，Transformers.js |
| API 协议 | Protocol Buffers |
| 部署 | Vercel Edge Functions + Railway 中继 |
| 开发者工具 | MCP Server、REST API、CLI、SDK（Python/Ruby/Go） |

---

*数据来源：GitHub 仓库 (koala73/worldmonitor)，2026 年 7 月 31 日访问*

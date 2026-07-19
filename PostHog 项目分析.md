# PostHog 项目分析

## 项目名称

**PostHog** — 一站式开源产品分析平台，替代 Mixpanel、Amplitude、FullStory 等 8-10 个付费工具

- **GitHub**: [PostHog/posthog](https://github.com/PostHog/posthog)
- **许可证**: MIT（核心）

---

## 项目概述

PostHog（🦔）是一个**一站式开源开发者平台**，旨在帮助产品团队理解用户、快速发布功能、管理所有使用数据和客户数据。它将产品分析、Web 分析、会话回放、Feature Flags、A/B 测试、错误追踪、用户调查、CDP、数据仓库等功能整合到一个统一的平台中，替代 Mixpanel、Amplitude、FullStory、LaunchDarkly、Sentry、Typeform、Segment 等多个碎片化的 SaaS 工具。

PostHog 的核心价值在于**消除工具碎片化和数据孤岛**。传统产品团队需要订阅 8-10 个不同的 SaaS 服务，每个工具都有独立的定价、数据管道和集成复杂度。PostHog 将所有这些能力统一在一个平台中，提供单一数据源和一致的分析体验。

项目采用 MIT 开源许可证（核心部分），支持完全自托管，满足 GDPR、SOC 2 等合规要求。同时提供慷慨的免费层——98% 的用户可以免费使用，包含每月 100 万事件、5000 次会话回放、100 万次 Feature Flag 请求和 15 万次异常捕获。PostHog 以极度透明的公司运营方式著称，公开了公司手册、定价逻辑、架构决策、路线图甚至营收数据。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **产品分析** | 基于事件的分析，支持自动采集或手动埋点。提供趋势、漏斗、留存、路径分析、队列构建等 |
| **Web 分析** | 网站流量分析，作为 Google Analytics 的替代方案，提供实时仪表盘 |
| **会话回放** | 录制并回放用户会话，理解 UX 问题和调试问题。支持 Web 和移动端 |
| **Feature Flags** | 通过目标规则、多变体 Flags 和渐进式发布来增量推出功能 |
| **A/B 测试** | 运行具有统计显著性测试的实验，基于 Feature Flags 基础设施 |
| **错误追踪** | 捕获、分组和分析应用错误和异常 |
| **用户调查** | 应用内调查，直接在产品中收集用户反馈 |
| **数据仓库 & CDP** | 客户数据平台，将事件路由到目标端；数据仓库用于查询和分析所有产品数据 |
| **AI 助手** | AI 驱动的助手，帮助分析数据、调试代码并生成跨平台的洞察 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **前端** | TypeScript、JavaScript、React、Vue.js、D3.js、WebSocket |
| **后端** | Python（Django）、TypeScript/JavaScript（Node.js）、Rust |
| **分析数据库** | ClickHouse（列式数据库，亚秒级查询数十亿事件） |
| **操作数据库** | PostgreSQL |
| **缓存** | Redis / Valkey |
| **事件流** | Apache Kafka / WarpStream |
| **任务编排** | Celery、Temporal、Dagster |
| **容器编排** | Kubernetes |
| **CI/CD** | GitHub Actions |
| **监控** | Prometheus、Grafana |
| **安全** | OAuth 2.0、SAML 2.0、TLS 1.3、AES-256、RBAC |
| **合规** | GDPR、SOC 2 |

---

## 项目亮点

### 真正的一站式平台
一个平台替代 8-10 个付费工具（Mixpanel、Amplitude、FullStory、LaunchDarkly、Sentry、Typeform、Segment 等），大幅降低工具成本和数据碎片化。

### MIT 开源核心 + 极致免费层
核心分析引擎采用 MIT 许可证，完全可自托管。免费层包含 100 万事件/月等，98% 的用户无需付费。

### 极度透明的公司运营
公开公司手册、定价逻辑、架构决策、路线图和营收数据。这种激进的透明度在 SaaS 行业极为罕见，深受开发者社区信任。

### 工程师优先的设计
提供 20+ 语言/框架的 SDK、CLI 工具、API 优先设计。底层使用 ClickHouse 实现数十亿事件的亚秒级查询，技术架构成熟可靠。

---

## 应用场景

### 初创产品分析与增长
早期创业团队使用 PostHog 追踪激活漏斗、留存队列、DAU/MAU 和功能采纳率，免费替代 Mixpanel/Amplitude。

### Feature Flags 与安全发布
工程团队使用 PostHog 的 Feature Flags 渐进式推出新功能、运行 A/B 实验，替代 LaunchDarkly/Optimizely。

### 会话回放 + 错误追踪调试
支持和工程团队结合会话回放与错误追踪，重现 Bug、理解错误前的用户操作路径，替代 FullStory + Sentry。

### 受监管行业的数据主权
医疗、金融或欧盟地区的企业自托管 PostHog，保持完全数据主权和审计能力，满足 GDPR/SOC 2 要求。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 36,279 |
| 总 Forks | 3,012 |
| 许可证 | MIT |
| 主要语言 | Python |
| 创建时间 | 2020 年 1 月 |


---

---

## 📋 更新记录

### 更新 1 — 2026 年 7 月 19 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
PostHog 以 438 颗今日新增 Star 再次登上 Trending 榜单，总 Star 数从约 36,279 增长至 36,333。项目作为一站式开源产品分析平台的定位持续巩固，"自动驾驶产品"的理念正在获得更多开发者的认同。

PostHog 在 2026 年持续扩展其平台能力，最新的产品定位已从"产品分析平台"升级为"自动驾驶产品平台"——强调其 AI 驱动的自动化能力。平台新增了 AI 可观测性（AI Observability）功能，使团队能够监控和分析 AI Agent 的行为、成本和性能。这使 PostHog 在 AI Agent 爆发的时代背景下更具前瞻性。

社区方面，多个专业评测文章对 PostHog 进行了深入分析，将其与 UserPilot、Mixpanel 等商业竞品进行全面对比。Vision Labs 等专业服务机构发布了详尽的 PostHog 使用教程（超过 30 分钟的视频教程），覆盖了产品分析、会话回放、LLM 分析、工作流自动化、调查等全功能模块。PostHog 的 LLM 成本追踪功能允许用户按模型（GPT、Claude 等）监控 AI 使用成本，这在当前 AI 应用爆发期具有极高的实用价值。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 36,279 | 36,333 | +54 |
| 今日新增 | — | 438 | — |
| 总 Forks | 3,012 | 3,013 | +1 |

**核心变化概要**：
- 产品定位升级为'自动驾驶产品平台'，强调 AI 驱动自动化
- 新增 AI 可观测性功能，监控 AI Agent 行为和成本
- LLM 成本追踪支持按模型分类监控 AI 使用支出
- 专业评测对比文章增加，市场认知度提升
- 工作流自动化和 Slack/Web 集成进一步增强


---
## 📋 更新记录

### 更新 1 — 2026 年 7 月 20 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单，今日新增 438 Stars

**最新动态**：
PostHog 以 438 颗今日新增 Star 连续第三天登上 Trending 榜单，总 Star 数达到 36,333。项目作为"自动驾驶产品平台"的定位持续巩固，AI 可观测性功能在 AI Agent 爆发时代背景下越来越受到关注。

PostHog 近期在博客中发布了多项产品更新，包括用户行为分析的多模态 LLM 实现、LLM traces 的自动聚类功能，以及 Notebooks（笔记本）功能的介绍。UserPilot 发布了详尽的 PostHog 2026 深度评测文章，将 PostHog 与商业竞品进行全面功能对比。Vision Labs 发布了超过 29 分钟的 PostHog 2026 完整教程视频，覆盖了从产品分析到 LLM 成本追踪的全功能模块，在 YouTube 上获得了 6,803 次观看和 110 个点赞。

PostHog 的 LLM 分析功能允许团队按模型（GPT、Claude 等）分类追踪 AI 使用成本和性能，这在当前 AI 应用快速爆发的背景下具有极高的实用价值。平台对 HogQL（直接 SQL 访问）的持续优化和 Array 1.43.0 的"大幅性能改进"进一步巩固了其技术竞争力。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 36,279 | 36,333 | +54 |
| 总 Forks | 3,012 | 3,013 | +1 |

**核心变化概要**：
- 连续第三天登上 Trending，自动驾驶产品平台定位巩固
- Vision Labs 29 分钟完整教程获 6,800+ 观看
- UserPilot 发布深度评测，市场认知度提升
- LLM 分析支持按模型追踪成本和性能


## 总结

PostHog 是目前最成功的**开源产品分析平台**，32.8k+ Stars。它将产品分析、会话回放、Feature Flags、A/B 测试、错误追踪、调查、CDP、数据仓库和 AI 助手整合到一个 MIT 开源的平台中，98% 的用户可免费使用。技术栈基于 Python/Django + React/TypeScript + ClickHouse，支持完全自托管，是开发者驱动产品团队的理想选择。

---

*数据来源：GitHub 仓库 (PostHog/posthog)、posthog.com（2026 年 4 月访问）*

*首次分析：见文件头部 | 最近更新：2026 年 7 月*

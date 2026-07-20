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

### 更新 2 — 2026 年 7 月 20 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：PostHog 今日新增 438 颗 Star，总星数逼近 37,000，持续扩大其在开源产品分析领域的领先优势。作为一站式开源产品分析平台，PostHog 近期在 AI 集成方面取得重大进展——推出了 PostHog AI 数据分析功能和 MCP（Model Context Protocol）集成，用户可以通过 AI 直接构建和查询分析洞察，进一步降低了产品分析的使用门槛。项目还推出了 Notebooks 功能，为数据探索提供了类似 Jupyter Notebook 的交互式体验。PostHog 持续推进「自动驾驶产品」愿景，让产品团队无需手动配置就能自动发现用户行为模式和异常。其核心架构 Array 引擎近期发布了 1.43.0 版本，带来了大规模性能提升，通过合并 persons 和 events 数据结构实现了高达 400% 的查询加速。PostHog 以极端透明的公司运营方式著称，公开了定价逻辑、架构决策和路线图。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 36,333 | 36,771 | +438 |
| 总 Forks | 3,013 | 3,040 | +27 |

**核心变化概要**：
- Star 数从 36,333 增长至 36,771（+438），增长势头稳健
- 推出 PostHog AI 数据分析和 MCP 集成，降低分析使用门槛
- 新增 Notebooks 交互式数据探索功能
- Array 1.43.0 引擎发布，查询性能提升高达 400%

---

## 📋 更新记录

### 更新 1 — 2026 年 7 月 21 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
PostHog 在 2026 年 7 月持续强化其"开发者操作系统"定位，已从一个产品分析工具发展为集成产品分析、Web 分析、会话回放、错误追踪、Feature Flags、实验、调查、数据仓库、CDP 和 AI 产品助手的统一平台。对于初创团队，PostHog 提供开源根基、自托管能力和适合早期阶段的定价，有效替代 Mixpanel、Amplitude、FullStory 等 8-10 个付费工具。

AI 能力方面，PostHog 新增了 LLM 分析和 LLM 成本追踪功能，支持按模型（GPT、Claude 等）跟踪 AI 使用成本。MCP 集成使开发者可以自然语言构建洞察报告。产品矩阵持续扩展，包括工作流自动化（邮件和 Slack 通知）、调查定制、笔记本文档功能和页面分析（Beta）。PostHog 在开源产品分析领域持续保持领先地位。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 36333 | 36,771 | +438 |
| 总 Forks | 3013 | 3,013 | +0 |

**核心变化概要**：
- 定位从分析工具升级为'开发者操作系统'，集成 10+ 产品能力
- 新增 LLM 分析和成本追踪，支持按模型追踪 AI 使用
- MCP 集成支持自然语言构建洞察报告
- 工作流自动化和调查功能完善了产品反馈闭环

## 总结

PostHog 是目前最成功的**开源产品分析平台**，32.8k+ Stars。它将产品分析、会话回放、Feature Flags、A/B 测试、错误追踪、调查、CDP、数据仓库和 AI 助手整合到一个 MIT 开源的平台中，98% 的用户可免费使用。技术栈基于 Python/Django + React/TypeScript + ClickHouse，支持完全自托管，是开发者驱动产品团队的理想选择。

---

*数据来源：GitHub 仓库 (PostHog/posthog)、posthog.com（2026 年 4 月访问）*

*首次分析：见文件头部 | 最近更新：2026 年 7 月*

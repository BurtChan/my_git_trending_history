# Knowledge Work Plugins 项目分析

## 项目名称

**Knowledge Work Plugins** — Anthropic 官方开源的 Claude Cowork / Claude Code 插件集合，将通用 AI 助手转化为各职能岗位的领域专家

- **GitHub**: [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins)
- **许可证**: Apache License 2.0

---

## 项目概述

Knowledge Work Plugins 是 Anthropic 于 2026 年 1 月随 Claude Cowork 插件系统一同发布的开源插件仓库。它为知识工作者提供了一系列即装即用的领域插件，覆盖销售、产品管理、工程、财务、法务、市场营销、人力资源、设计、运营、数据、生物科研等十余个核心业务职能。

项目核心价值在于**角色专业化**：将 Claude 从通用助手变为特定职能专家，具备该领域的最佳实践、工作流和工具集成。插件采用纯 Markdown/JSON 文件结构（无代码），企业可轻松定制工作流、替换连接器、注入公司专属术语和流程。

通过 MCP（Model Context Protocol）连接器，插件将 Claude 对接到企业已有的工具链（如 Slack、Notion、HubSpot、Jira、Salesforce、Snowflake、GitHub 等 40+ 外部工具），实现跨平台数据打通。项目同时兼容 Claude Cowork（面向非技术知识工作者）和 Claude Code（面向开发者）两种使用场景。

---

## 核心功能

| 插件名称 | Skills 数 | Commands 数 | 关键连接器 |
|---|---|---|---|
| **Productivity（生产力）** | 2 | 2 | Slack, Notion, Asana, Linear, Jira |
| **Sales（销售）** | 6 | 3 | HubSpot, Close |
| **Customer Support（客户支持）** | 5 | 5 | Intercom, HubSpot |
| **Product Management（产品管理）** | 6 | 7 | Linear, Figma |
| **Marketing（市场营销）** | 5 | 7 | Canva, Figma |
| **Engineering（工程）** | 6 | 6 | GitHub, PagerDuty |
| **Design（设计）** | 6 | 6 | Figma, Intercom |
| **Data（数据）** | 7 | 6 | Snowflake, Databricks |
| **Finance（财务）** | 6 | 5 | Snowflake, Databricks |
| **Legal（法务）** | 6 | 7 | Box, Egnyte |
| **HR（人力资源）** | 6 | 6 | MS365, Notion |
| **Operations（运营）** | 6 | 6 | ServiceNow, Asana |
| **Enterprise Search（企业搜索）** | 3 | 2 | Slack, Notion |
| **Bio-Research（生物科研）** | 5 | 1 | PubMed, Benchling |

总计 **85+ Skills**、**69+ Commands**、**40+ MCP Connectors**。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要编程语言** | Python |
| **插件内容格式** | Markdown（技能描述）、JSON（清单和配置） |
| **外部工具协议** | MCP（Model Context Protocol） |
| **兼容平台** | Claude Cowork、Claude Code |
| **安装方式** | claude plugin marketplace add 或在线安装 |
| **版本控制** | Git / GitHub |

---

## 项目亮点

### 纯文件驱动、零代码门槛
插件全部由 Markdown 和 JSON 文件构成，无需编写代码或搭建基础设施，降低了企业定制门槛。

### 研究优先工作流
插件遵循"研究 → 综合 → 起草 → 执行"的模式，确保输出质量。

### 多源工具集成
每个插件集成 5-10+ 外部工具，实现跨平台数据打通。

### 官方背书
由 Anthropic 官方团队直接维护，质量有保障，与 Claude 产品深度整合。

---

## 应用场景

### 销售团队
潜在客户调研、通话准备、销售管道管理、竞品 Battle Card 制作。

### 产品管理
需求文档撰写、路线图规划、用户研究、竞品分析。

### 工程团队
代码审查辅助、On-call 管理、工单处理、技术文档。

### 财务与法务
日记账、账户对账、合同审查、NDA 分诊、合规导航。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 24,853+ |
| **总 Forks** | 2,967+ |
| **今日新增 Stars** | +318 |
| **许可证** | Apache License 2.0 |
| **创建时间** | 2026 年 1 月 |
| **主要语言** | Python |

## 📋 更新记录

### 更新 1 — 2026年9月16日（时隔近 4 个月再登 Trending）

**更新原因**：项目时隔近 4 个月再次登上 GitHub Trending 榜单，Star 数从 16,565 增长至 24,129（+7,564），涨幅约 46%。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 16,565 | 24,129 | +7,564 |
| 总 Forks | 1,945 | 2,913 | +968 |

- Star 数 16,565 → 24,129（+7,564），Fork 数 1,945 → 2,913（+968）
- Anthropic 官方持续运营的企业职能插件集（金融/法律/营销/销售/人力等），零代码 Markdown/JSON 格式 + MCP 协议打通 40+ 企业工具的定位未变
- 企业 AI 助手定制化需求升温带动项目回榜，Apache 2.0 许可

> 更新依据：GitHub Trending 2026-09-16 数据，Star 数由 GitHub API 实时获取


### 更新 2 — 2026年9月18日（连续第二日在榜）

**更新原因**：登上 GitHub Trending（2026 年 9 月 18 日），企业职能插件集热度延续。

**最新 Star 数据**：

| 总 Stars | 24,129 | 24,535 | +406 |
| 总 Forks | 2,913 | 2,939 | +26 |

- Star 数 24,129 → 24,535（+406），连续第二日在榜
- Anthropic 面向 Claude Cowork 的企业职能插件集持续扩充，仓库 9/17 仍有推送

> 更新依据：GitHub Trending 2026-09-18 数据，Star 数由 GitHub API 实时获取

### 更新 3 — 2026年9月19日（连续第三日在榜，豁免单日阈值）

**更新原因**：连续第三天登上 GitHub Trending（9 月 16 日至今），按连续在榜 ≥3 天规则豁免单日 500 stars 阈值。Star 数保持稳定增长；仓库近期高频迭代——9 月 18 日新增 Wingspan 插件、更新 Qodo 与 Airwallex 合作伙伴元数据，并批量 bump Leadfeeder、Modern Web Guidance、Signoz 等多个插件版本，企业插件生态持续扩张。

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 24,535 | 24,853 | +318 |
| 总 Forks | 2,939 | 2,967 | +28 |
| Open Issues | — | 80 | — |


---

## 总结

Knowledge Work Plugins 是 **Anthropic 在 AI 助手企业化方向上的核心布局**，24.8k+ Stars。它通过插件化架构将 Claude 从通用 AI 变为各职能领域的专家助手，采用零代码的 Markdown/JSON 文件格式极大降低企业定制门槛，通过 MCP 协议打通 40+ 企业工具。项目代表了 AI 助手从"对话工具"向"领域专家工作平台"演进的重要趋势。

---

*数据来源：GitHub 仓库 (anthropics/knowledge-work-plugins)，2026 年 5 月访问*
*首次分析：2026 年 5 月 28 日 | 最近更新：2026 年 9 月 19 日*

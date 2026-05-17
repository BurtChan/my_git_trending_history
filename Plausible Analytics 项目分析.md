# Plausible Analytics 项目分析

## 项目名称

**Plausible Analytics** — 开源、隐私优先的轻量级网站分析工具

- **GitHub**: [plausible/analytics](https://github.com/plausible/analytics)
- **许可证**: GNU Affero General Public License v3.0 (AGPL-3.0)

---

## 项目概述

Plausible Analytics 是一款开源的、以隐私为核心的网站分析工具，定位为 Google Analytics 的轻量级替代方案。项目的核心理念是"简单、隐私、合规"——提供一个清爽的分析界面，不使用 Cookie，不收集个人数据，完全符合 GDPR、CCPA、PECR 等隐私法规要求。

Plausible 的追踪脚本极其轻量（不到 1KB），相比 Google Analytics 庞大的脚本大幅减少了页面加载时间。它不存储 IP 地址，不使用 Cookie，不进行跨站追踪，所有数据都是聚合统计而非个人用户画像。这种设计不仅保护了访客隐私，也简化了网站所有者的合规负担——使用 Plausible 不需要在网站上显示 Cookie 同意横幅。

在功能方面，Plausible 将所有关键洞察集中在一个页面上，无需在多层菜单中导航或创建自定义报告。它支持自定义目标和转化追踪、自定义事件和维度、实时流量监控、邮件和 Slack 报告、公共仪表板分享、Google Search Console 集成以及 API 数据导出等功能。项目提供自托管版本（Plausible CE）和托管云服务两种使用方式，技术栈采用 Elixir + Phoenix + ClickHouse + PostgreSQL 构建。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **隐私分析** | 无 Cookie、无个人数据收集，完全合规 GDPR/CCPA/PECR |
| **轻量追踪脚本** | 不到 1KB 的脚本大小，不影响页面加载速度 |
| **单页仪表板** | 所有关键指标一页呈现，直观清晰 |
| **自定义目标** | 追踪转化目标和自定义事件 |
| **实时分析** | 监控实时网站流量和访客活动 |
| **报告与分享** | 邮件报告、Slack 通知和公共仪表板分享 |
| **搜索洞察** | 集成 Google Search Console 的搜索关键词数据 |
| **API 与导出** | 提供 API 接口和统计数据导出功能 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **后端语言** | Elixir |
| **Web 框架** | Phoenix |
| **分析数据库** | ClickHouse |
| **关系数据库** | PostgreSQL |
| **前端样式** | Tailwind CSS |
| **追踪脚本** | JavaScript (MIT 许可证) |
| **部署方式** | 自托管 / 云托管 |

---

## 项目亮点

1. **极致隐私保护**：无 Cookie、无 IP 存储、无跨站追踪，使用 Plausible 无需 Cookie 同意横幅
2. **超轻量脚本**：追踪脚本不到 1KB，是 Google Analytics 的数十分之一，不影响网站性能
3. **合规即服务**：内置 GDPR、CCPA、PECR 合规能力，大幅简化隐私合规工作
4. **商业模式可持续**：通过托管云服务获得收入支持开发，确保项目长期健康发展

---

## 应用场景

1. **个人博客分析**：博主追踪网站流量，无需复杂的隐私合规措施
2. **企业网站分析**：企业替代 Google Analytics，简化隐私合规流程
3. **隐私敏感行业**：医疗、金融、法律等隐私敏感行业的网站分析
4. **开源项目与 SaaS**：开源项目和小型 SaaS 产品的用户行为分析

---

## Star 数据

| 指标 | 数据 |
|------|------|
| **总 Stars** | 25,104 |
| **Forks** | 1,433 |
| **今日新增 Stars** | 趋势项目 |
| **许可证** | AGPL-3.0 (服务端) / MIT (追踪脚本) |
| **主要语言** | Elixir |

---

## 总结

Plausible Analytics 是隐私优先网站分析领域的标杆项目，以"轻量、隐私、合规"为三大核心理念，为 Google Analytics 提供了优秀的开源替代方案。项目采用 Elixir + Phoenix + ClickHouse 技术栈构建，追踪脚本不到 1KB，不使用 Cookie 和个人数据，完全符合 GDPR 等隐私法规。凭借 25,000+ Stars 和可持续的商业模式，Plausible 已成为重视用户隐私的网站所有者的首选分析工具。

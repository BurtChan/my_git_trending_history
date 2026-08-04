# OpenSRE 项目分析

## 项目名称

**OpenSRE** — 构建属于你自己的 AI SRE 智能代理，AI 时代的开源 SRE 工具包

- **GitHub**: [Tracer-Cloud/opensre](https://github.com/Tracer-Cloud/opensre)
- **许可证**: Apache License 2.0

---

## 项目概述

OpenSRE 是一个面向 AI 时代的开源 SRE（站点可靠性工程）智能代理框架，旨在帮助运维和开发团队构建自主化的 AI SRE Agent，实现生产环境事故的自动调查、根因分析和故障修复建议。项目由 Tracer Cloud 团队开发并维护，核心定位是解决 SRE 团队在事件响应中反复、低效、高上下文切换的痛点。

传统 SRE 工作流中，团队平均需要在告警触发后花费 45 分钟以上进行分流和初步调查，每次事件都依赖大量人工经验（tribal knowledge），且需要频繁切换 Prometheus、Grafana、Datadog、日志系统等多个工具。OpenSRE 通过 AI Agent 架构，将事件调查流程自动化：一个"规划者 Agent"（Planner Agent）协调多个专业化子 Agent 并行工作，同时查询 Kubernetes、指标、日志、链路追踪等多个数据源，生成结构化的调查报告并提供可能的根因。

OpenSRE 的独特之处在于其**情景记忆（Episodic Memory）** 和 **知识图谱（Knowledge Graph）** 能力——每次调查都会被保存，Agent 在处理新事件时会自动检索历史上相似的事件，积累机构知识，避免每次都从零开始。这使其不仅是工具，更是一个持续学习、越用越聪明的 AI SRE 助手。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 自动事故调查 | 告警触发后自动启动 AI Agent 进行结构化事件调查 |
| 情景记忆与历史召回 | 存储每次调查记录，通过多因子相似度匹配自动召回历史经验 |
| 知识图谱与服务拓扑映射 | 自动映射服务依赖关系，支持爆炸半径分析 |
| 多 Agent 并行调查 | 规划者 Agent 调度专业子 Agent 并行查询多个系统 |
| 结构化根因分析报告 | 生成包含可能根因、证据链和建议下一步的结构化报告 |
| Runbook 感知推理 | 基于运维手册和文档进行有据可依的推理 |
| 预测性故障检测 | 提前识别潜在故障趋势 |
| 40+ 工具集成 | 支持 Kubernetes、Prometheus、Grafana、Datadog、Elastic、Splunk 等 |
| 46 个内置调查技能 | 覆盖各类调查场景的开箱即用技能 |
| 自定义技能与工作流 | 支持用户定义自己的调查技能和工作流 |
| LLM 灵活切换 | 支持 OpenAI、Anthropic 等多种大语言模型 |
| Slack/PagerDuty 通知 | 自动将调查摘要推送到 Slack 或 PagerDuty |
| 完全自托管 | 数据不离开用户基础设施，保障安全与隐私 |

---

## 技术栈

| 类别 | 技术 |
|------|------|
| 主要编程语言 | Python |
| AI/LLM 提供商 | OpenAI、Anthropic 等（可插拔） |
| 容器编排 | Kubernetes、Docker |
| 可观测性 | Prometheus、Grafana、Datadog、Elastic、Splunk、Jaeger、New Relic |
| 错误追踪 | Sentry |
| 云平台 | AWS、GCP |
| 数据库 | PostgreSQL |
| 协作/通知 | Slack、PagerDuty、Microsoft Teams、GitHub、Confluence、Notion |
| CI/CD | GitHub Actions |

---

## 项目亮点

1. **100% 开源、Apache 2.0 许可**：无供应商锁定，完全自托管，数据不离开用户基础设施，企业可放心使用和定制。
2. **情景记忆 + 知识图谱双引擎**：区别于传统规则引擎，OpenSRE 通过记忆系统积累组织知识，每次调查都比上一次更高效，真正实现"越用越聪明"的 AI SRE。
3. **40+ 深度集成**：覆盖主流可观测性、云平台、协作工具和数据库，用户无需更换现有工具链即可接入，极大降低采用门槛。
4. **多 Agent 并行调查架构**：模仿资深 SRE 分配任务给团队的模式，规划者 Agent 协调多个专业化子 Agent 并行工作，大幅缩短事件调查时间（MTTR）。

---

## 应用场景

1. **生产环境故障自动排查**：当 PagerDuty/Slack 收到告警时，OpenSRE 自动启动调查流程，在人工介入前就已给出初步诊断和根因分析，大幅缩短 MTTR。
2. **大规模微服务架构的故障定位**：通过知识图谱自动映射服务依赖关系，在复杂微服务拓扑中快速定位故障源头和爆炸半径。
3. **跨团队事件知识管理**：将 SRE 团队的历史调查经验转化为可复用的组织知识资产，避免关键人员离职导致的"知识断层"。
4. **7×24 无人值守运维**：在非工作时间自动响应和处理告警，生成结构化报告，团队上班后即可直接基于 AI 分析结果做出决策。

---

## Star 数据

| 指标 | 数据 |
|------|------|
| 总 Stars | ⭐ 1,113 |
| 总 Forks | 🍴 150 |
| 主要语言 | Python |
| 许可证 | Apache License 2.0 |
| 当前状态 | 活跃更新中 |

---

## 总结

**OpenSRE（Tracer-Cloud/opensre）** 是一个基于 Python 的开源 AI SRE 智能代理框架，通过多 Agent 并行调查架构、情景记忆和知识图谱技术，实现生产环境事故的自动化根因分析。项目集成了 40+ 主流运维工具（包括 Kubernetes、Grafana、Datadog、AWS 等），采用 Apache 2.0 许可证完全自托管，无供应商锁定。作为 AI 时代 SRE 工具链的创新者，OpenSRE 开源首月即获得 800+ Stars（现已超 1,100），展现了强大的社区关注度和应用前景，是希望用 AI 赋能事件响应和降低 MTTR 的运维团队值得关注的优质开源项目。

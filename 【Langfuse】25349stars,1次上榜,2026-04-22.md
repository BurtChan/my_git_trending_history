# Langfuse 项目分析

## 项目名称

**Langfuse** — 开源 LLM 工程平台，提供全链路可观测性、评估与 Prompt 管理

- **GitHub**: [langfuse/langfuse](https://github.com/langfuse/langfuse)
- **许可证**: MIT

---

## 项目概述

Langfuse 是一款面向 LLM 应用的**开源工程平台**，由 Marc Klingenberg 和 Max Deichmann 于 2023 年创立，是 Y Combinator W23 批次项目。它为开发团队提供了 LLM 应用全生命周期的可视化、调试和优化能力，涵盖从 Prompt 开发到生产监控的完整链路。

在 LLM 应用开发中，开发者常面临「黑箱」困境：不知道模型收到什么 Prompt、返回什么结果、花了多少 Token、延迟几何。Langfuse 通过**应用追踪（Tracing）**技术，结构化记录每次请求的完整上下文——包括输入 Prompt、模型响应、Token 用量、延迟以及中间的工具调用和检索步骤——让 LLM 应用的运行过程完全透明。

Langfuse 与 OpenTelemetry 原生集成，支持 LangChain、OpenAI SDK、LiteLLM、CrewAI、LlamaIndex 等主流框架的一键接入。项目基于 TypeScript + Python 开发，提供云端托管（Langfuse Cloud）和本地自部署两种部署模式，Cloud 版已通过 HIPAA 合规认证，可安全用于医疗场景。

---

## 核心功能

### 1. 应用追踪（Tracing）
结构化记录每次 LLM 调用的完整上下文，包括输入、输出、Token 用量、延迟、工具调用链路等，支持按 Trace、Session、Observation 三级结构组织数据。

### 2. Prompt 管理
可视化 Prompt 编辑器，支持版本管理、A/B 测试、文件夹组织，支持通过 SDK 和 API 直接拉取 Prompt 到应用中。

### 3. LLM 评估（Evals）
提供 LLM-as-a-Judge、人工标注队列、自定义评估指标等多种评估方式，支持对 Traces 批量运行评估，自动计算准确率等指标。

### 4. 自定义仪表盘
提供丰富的图表组件（直方图、透视表、时间序列等），可自由组合构建项目级仪表盘，实时监控 LLM 应用的成本、延迟和质量。

### 5. 成本追踪
精确追踪每次 LLM 调用的 Token 消耗和成本，支持自定义模型定价，提供成本趋势和异常报警。

### 6. Playground
内置 LLM Playground，支持在 Web 界面直接测试和调试 Prompt，支持工具调用（Tool Calling）和 JSON 结构化输出。

### 7. 数据集管理
支持创建和管理评估数据集，结合 Evals 进行系统化的模型性能对比和回归测试。

### 8. 多模型支持
支持 GPT-4.5、Claude 3.7、Gemini 2.5 Pro/Flash、o3-pro 等最新模型的 Playground 测试和成本追踪。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **后端语言** | TypeScript / Python |
| **前端框架** | Next.js |
| **数据库** | PostgreSQL（主存储）、ClickHouse（分析查询） |
| **缓存** | Redis |
| **可观测性** | OpenTelemetry 原生集成 |
| **SDK** | Python SDK、JavaScript/TypeScript SDK、Java SDK |
| **部署** | Docker / Kubernetes（Helm Chart）/ Terraform（AWS/GCP） |
| **集成框架** | LangChain、OpenAI SDK、LiteLLM、CrewAI、LlamaIndex、Haystack 等 |
| **认证** | SSO / SAML / HIPAA（Cloud 版） |

---

## 项目亮点

### 全链路透明
从用户请求到模型响应的每一步操作都被记录和可视化，开发者可以像使用 Chrome DevTools 调试网页一样调试 LLM 应用。

### OpenTelemetry 原生支持
无需修改应用代码，通过 OpenTelemetry 自动采集 LLM 调用数据，与现有可观测性栈（Grafana、Datadog 等）无缝集成。

### 强大的评估体系
支持 LLM-as-a-Judge 自动评估、人工标注队列、Session 级评分等多维度评估，让 LLM 应用质量可量化、可追踪。

### 企业级部署
提供 HIPAA 合规的 Cloud 版本和完整的企业级自部署方案（K8s Helm Chart、Terraform Module），满足不同规模和合规需求。

---

## 应用场景

### LLM 应用调试
开发 RAG、Agent 等复杂 LLM 应用时，追踪每次工具调用和检索步骤，快速定位异常和性能瓶颈。

### Prompt 工程优化
在 Playground 中迭代 Prompt，利用 A/B 测试和评估数据集量化优化效果，系统化管理 Prompt 版本。

### 成本管控
精确追踪各应用、各模型、各团队的 LLM 调用成本，通过仪表盘实时监控，发现异常消费及时预警。

### AI 质量保障
建立评估数据集和自动化评估流水线，在模型升级或 Prompt 变更时自动运行回归测试，防止质量退化。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 25,349 |
| **总 Forks** | 2,575 |
| **今日新增 Stars** | ~67 |
| **许可证** | MIT |
| **主要语言** | TypeScript |

---

## 总结

Langfuse 是**LLM 应用可观测性领域的事实标准**，25k+ Stars。它用 TypeScript 构建，为开发团队提供从 Prompt 管理到生产监控的全链路平台，支持 OpenTelemetry 原生集成和 40+ 框架一键接入。项目已通过 HIPAA 合规认证，提供 Cloud 和自部署两种模式，是构建可靠 LLM 应用的基础设施级工具。

---

*数据来源：GitHub 仓库 (langfuse/langfuse)、langfuse.com（2026 年 4 月访问）*

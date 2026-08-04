# Onyx 项目分析

## 项目名称

**Onyx** — 开源企业级 AI 智能平台，连接团队文档、应用与知识库

- **GitHub**: [onyx-dot-app/onyx](https://github.com/onyx-dot-app/onyx)
- **官网**: [onyx.app](https://onyx.app)
- **许可证**: MIT（社区版）/ Onyx Enterprise License（企业版）

---

## 项目概述

Onyx 是一款**开源的企业级 AI 对话与知识搜索平台**，由 DanswerAI, Inc. 开发（前身为 Danswer）。它将企业内部文档、应用程序和团队知识连接起来，通过混合检索、高级 RAG（检索增强生成）、上下文检索和 LLM 知识图谱等技术，为团队提供精准可靠的 AI 问答体验。

Onyx 的核心设计理念是**知识驱动的企业 AI 助手**：不是简单的 ChatGPT 包装器，而是一个完整的 AI 平台，具备 50+ 数据连接器、Agentic RAG、深度研究、代码执行、文件创建、MCP 支持等高级功能。它支持自托管部署，可在完全离线/内网环境中运行，满足企业对数据隐私和合规的要求。

项目由 Python 后端和 Next.js 前端构成，提供标准模式和轻量模式（Lite）两种部署方案。轻量模式内存占用不到 1GB，适合快速测试或专注于聊天和 Agent 功能的小团队；标准模式包含全部功能，适合生产环境的大团队使用。目前已被 Ramp 等公司用于日常生产，每周回答数千个问题，被誉为"企业 AI 搜索的最佳选择"。

---

## 核心功能

### 1. Agentic RAG（智能检索增强生成）
结合混合索引（关键词 + 语义向量）与 AI Agent 进行信息检索，提供业界领先的搜索和回答质量。在 99 个真实工作场景问题、22 万份内部文档的基准测试中，Onyx 的回答质量超越了 ChatGPT Enterprise、Claude Enterprise 和 Notion AI。

### 2. 50+ 数据连接器
开箱即用的企业数据集成，支持 Google Drive、Confluence、Slack、Jira、GitHub、Notion、SharePoint、Salesforce 等主流企业工具，实时同步更新，并尊重原有的细粒度访问控制权限。

### 3. 深度研究（Deep Research）
自动进行多轮搜索、分析和综合，针对复杂问题生成详尽的研究报告，适合技术调研、竞品分析等场景。

### 4. MCP（Model Context Protocol）支持
原生支持 MCP 协议，可扩展连接外部工具和数据源，增强 AI Agent 的能力边界。

### 5. 代码执行与文件创建
内置安全的代码执行沙箱，支持 AI 辅助生成和编辑文件，可直接在工作流中处理数据。

### 6. 多 LLM 支持
兼容所有主流 LLM 提供商，包括 OpenAI、Anthropic Claude、Google Gemini、自托管模型（通过 Ollama 等），灵活配置切换。

### 7. 企业级安全与合规
提供 SOC 2 Type II 认证、GDPR 合规、细粒度权限控制、安全部署选项，满足金融、医疗、航空航天等行业的严格要求。

### 8. 灵活部署
支持 Docker、Kubernetes、Helm/Terraform 等多种部署方式，兼容各大云平台，也可完全离线内网部署。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **后端语言** | Python |
| **前端框架** | Next.js (React) |
| **检索引擎** | 混合索引（关键词 + 向量语义搜索） |
| **RAG 架构** | Agentic RAG + 上下文检索 + LLM 知识图谱 |
| **AI 模型** | 支持所有主流 LLM（OpenAI、Anthropic、Gemini、自托管等） |
| **协议支持** | MCP（Model Context Protocol） |
| **部署方式** | Docker / Kubernetes / Helm / Terraform |
| **部署模式** | Standard（全功能） / Lite（轻量，<1GB 内存） |
| **数据连接器** | 50+（Google Drive、Slack、Confluence、Jira、GitHub 等） |
| **认证授权** | 细粒度权限控制，SSO 支持 |
| **合规标准** | SOC 2 Type II、GDPR |

---

## 项目亮点

### 企业级 RAG 基准测试领先
在 99 个真实工作场景问题、22 万份内部文档的独立盲测中，Onyx 的回答准确率超越了 ChatGPT Enterprise、Claude Enterprise 和 Notion AI，证明其 RAG 架构在生产环境中的可靠性。

### 开源自托管，数据完全可控
支持完全离线部署，所有数据留在企业自己的基础设施上，不依赖外部云服务。社区版采用 MIT 许可证，企业版提供高级功能和支持。

### 真正的企业级产品
已被 Ramp（金融科技独角兽）等企业用于日常生产，每周处理数千个查询任务，被客户评价为"尝试了多种 AI 工具中回答可靠性最高的"。

### 灵活的架构设计
Lite 模式适合快速试用和小团队（<1GB 内存），Standard 模式满足大团队全功能需求，同时提供 Onyx Cloud 云服务选项，降低部署门槛。

---

## 应用场景

### 企业内部知识搜索
将分散在 Google Drive、Confluence、Slack、Jira 等工具中的知识统一索引，员工通过自然语言提问即可获得精准答案，大幅减少信息查找时间。

### 工程团队效率提升
连接 GitHub 代码库、技术文档、设计文档等，工程师可以快速获取代码上下文、架构决策历史、API 文档等信息，加速开发和排障流程。

### 销售与客服支持
实时访问所有客户对话记录和产品更新信息，销售团队快速回答客户问题，客服团队跨全产品线提供准确支持。

### 深度研究与报告
利用 Deep Research 功能进行技术调研、竞品分析、市场研究等复杂任务，自动完成多轮搜索和综合分析，生成结构化研究报告。

### 合规敏感行业 AI 部署
金融、医疗、航空航天、国防等行业，通过自托管部署和细粒度权限控制，在满足合规要求的前提下为团队提供 AI 能力。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 27,400+ |
| **总 Forks** | 3,600+ |
| **今日新增 Stars** | ~5,500 |
| **许可证** | MIT（社区版）/ Enterprise License |
| **创建时间** | 2023 年 4 月 |
| **主要语言** | Python / TypeScript |
| **Watchers** | 150 |
| **Open Issues** | 338 |

---

## 总结

Onyx 是**企业级开源 AI 知识平台的事实标准**，27k+ Stars。它以 Python + Next.js 构建，提供 50+ 数据连接器、Agentic RAG、深度研究、MCP 支持等完整功能，支持自托管部署和完全离线运行。在真实企业场景的基准测试中，Onyx 的回答质量超越了 ChatGPT Enterprise 和 Claude Enterprise，已被 Ramp 等独角兽企业用于日常生产。项目兼具开源灵活性和企业级安全性（SOC 2 Type II、GDPR），是需要数据自主权和合规保障的团队部署 AI 助手的首选方案。

---

*数据来源：GitHub 仓库 (onyx-dot-app/onyx)、onyx.app 官网（2026 年 4 月访问）*

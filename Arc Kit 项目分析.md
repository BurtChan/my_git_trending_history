# Arc Kit 项目分析

## 项目名称

**ArcKit** — 面向企业架构治理与供应商采购的 AI 原生工具包

- **GitHub**: [tractorjuice/arc-kit](https://github.com/tractorjuice/arc-kit)
- **许可证**: MIT

---

## 项目概述

ArcKit 是一个面向**企业架构治理与供应商采购**的专业工具包（Enterprise Architecture Governance & Vendor Procurement Toolkit）。它将架构治理从分散的文档管理转变为系统化、AI 辅助的工作流程，覆盖从架构原则制定、需求分析、供应商选择到设计评审的完整生命周期。

项目由 Mark Craddock 开发维护，采用 Python 编写，基于 Typer + Rich CLI 框架构建，提供 68 个斜杠命令和 10 个自主研究代理。ArcKit 深度集成了多个主流 AI 平台（Claude Code、Gemini CLI、GitHub Copilot、Codex CLI、OpenCode），以 Claude Code 为主要开发平台，提供最完整的体验。

ArcKit 特别适配英国政府合规环境，内置对 HM Treasury Orange Book（风险管理）、Green Book（商业论证）、GDS 服务标准、Technology Code of Practice、NCSC CAF、MOD JSP 936 AI 保障、UK GDPR 等框架的支持。同时集成了 Wardley Mapping 战略分析工具，支持价值链、教义、博弈、气候等多维度分析。

---

## 核心功能

| 类别 | 功能 |
|------|------|
| **治理工作流** | 项目规划、架构原则、利益相关者分析、风险管理（Orange Book）、商业论证（Green Book） |
| **需求与数据** | 需求文档、数据建模、ERD 图、GDPR 合规、数据治理、数据源发现 |
| **供应商采购** | RFP 生成、UK Digital Marketplace 搜索、供应商评估框架、采购工作流 |
| **设计与架构** | Wardley Mapping 战略分析、Mermaid 架构图、架构决策记录、设计评审（HLD/DLD） |
| **英国政府合规** | GDS 服务标准、TCoP、NCSC CAF、MOD JSP 936、DPIA、Secure by Design |
| **其他工具** | ServiceNow 设计、FinOps 云成本管理、MLOps 策略、路线图、质量分析、演示文稿生成 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要语言** | Python (≥3.11) |
| **CLI 框架** | Typer + Rich |
| **HTTP 客户端** | httpx（支持 SOCKS 代理） |
| **构建系统** | Hatchling |
| **AI 平台集成** | Claude Code、Gemini CLI、GitHub Copilot、Codex CLI、OpenCode |
| **MCP 服务器** | AWS Knowledge、Microsoft Learn、Google Developer Knowledge |
| **图表/可视化** | Mermaid（架构图）、MARP（演示文稿） |

---

## 项目亮点

1. **AI 原生架构治理**：深度集成 Claude Code、Gemini、Copilot 等多个 AI 平台，以 AI 辅助驱动整个架构治理流程
2. **系统化 16 阶段工作流**：从原则制定到文档发布的完整架构治理生命周期，68 个斜杠命令覆盖所有环节
3. **英国政府深度适配**：内置对 HM Treasury、GDS、NCSC、MOD 等英国政府框架的完整支持
4. **Wardley Mapping 集成**：内建战略技术分析工具，支持价值链、教义、博弈等多维度战略分析
5. **完整的供应商采购工作流**：从 RFP 生成到供应商评估的全流程管理

---

## 应用场景

1. **企业架构治理**：大型组织的架构原则制定、设计标准执行、技术选型管理
2. **英国政府 IT 项目合规**：GDS 服务标准评估、技术行为准则审计、数据保护影响评估
3. **供应商采购管理**：RFP 文档生成、供应商评估框架搭建、采购决策支持
4. **战略技术分析**：使用 Wardley Mapping 进行技术战略规划和构建与购买决策分析

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | ~576 |
| **Forks** | ~88 |
| **今日新增** | 📈 Trending |
| **许可证** | MIT |
| **主要语言** | Python |

---

## 总结

ArcKit 是一个面向企业架构师的专业工具包，通过 AI 辅助工作流将传统上分散的架构治理文档转化为系统化、可追溯的流程。项目特别适合在英国政府合规环境下工作的团队，内置了对 HM Treasury、GDS、NCSC 等核心框架的完整支持。68 个斜杠命令、10 个自主研究代理和 Wardley Mapping 战略分析的深度集成，使其成为企业架构治理领域最全面的 AI 原生工具之一。MIT 开源许可证和活跃的开发迭代（967 commits）进一步增强了其社区吸引力。

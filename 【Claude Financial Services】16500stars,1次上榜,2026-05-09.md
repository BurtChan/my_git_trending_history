# Claude Financial Services 项目分析

## 项目名称

**Claude Financial Services** — Anthropic 官方金融行业 AI Agent 参考架构，提供投行、研究、PE、财富管理的端到端工作流模板

- **GitHub**: [anthropics/financial-services](https://github.com/anthropics/financial-services)
- **许可证**: Apache License 2.0

---

## 项目概述

Claude Financial Services 是 Anthropic 官方推出的开源金融行业 AI Agent 参考架构，专为金融服务业最耗时的四大垂直领域提供即用型 Agent 模板：**投资银行**、**股票研究**、**私募股权**和**财富管理**。项目将每个 Agent 封装为 **Claude Cowork 插件**（可在 Claude Cowork 和 Claude Code 中使用）和 **Claude Managed Agent 模板**（可通过 `/v1/agents` API 部署），使团队能在数天而非数月内将 Claude 投入实际金融工作。

仓库包含 **十个即用型 Agent 模板**，分为两大类：**研究与客户覆盖**（Pitch Builder、Meeting Preparer、Earnings Reviewer、Model Builder、Market Researcher）和 **财务与运营**（Valuation Reviewer、GL Reconciler、Month-End Closer、Statement Auditor、KYC Screener）。每个模板整合了三要素：**技能**（任务相关的领域知识和指令）、**连接器**（对金融数据源的受控访问）和**子代理**（用于特定子任务如可比公司选择或方法论校验的额外 Claude 模型）。

项目还提供了丰富的 **MCP（模型上下文协议）集成**，连接 FactSet、S&P Capital IQ、MSCI、PitchBook、Morningstar、LSEG、Daloopa、Moody's 等 15+ 家金融数据提供商。此外包含 Microsoft 365（Excel、PowerPoint、Word、Outlook）的部署工具，可在 Claude Opus 4.7 的强大推理能力驱动下实现跨应用的上下文传递和知识协同。

---

## 核心功能

### 1. Agent 工作流模板（10个）

| Agent | 功能描述 |
|-------|---------|
| **Pitch Builder** | 公司研究 + 数据拉取 → 大纲 → 首版 Pitchbook |
| **Meeting Preparer** | CRM 笔记 + 最新公告 → 会议准备简报 |
| **Earnings Reviewer** | 财报电话会议 + 公告 → 模型更新 → 研报初稿 |
| **Model Builder** | DCF、LBO、三表联动、可比公司分析 — 在 Excel 中实时构建 |
| **Market Researcher** | 基于投资逻辑的深度研究 → 结构化报告 |
| **Valuation Reviewer** | 估值模型合理性校验，标记异常 |
| **GL Reconciler** | 自动对账总账条目 |
| **Month-End Closer** | 自动化月末结账检查清单 |
| **Statement Auditor** | 审计财务报表中的问题 |
| **KYC Screener** | KYC 文件审查与问题标记 |

### 2. 垂直行业插件包

- **投资银行**: CIM、Teaser、流程函、买方名单、合并模型、项目跟踪
- **股票研究**: 财报笔记、首次覆盖、模型更新、投资逻辑与催化剂跟踪
- **私募股权**: 项目寻源、筛选、尽调清单、IC 备忘录、投后监控
- **财富管理**: 理财顾问工作流

### 3. MCP 数据连接器

集成 FactSet、S&P Capital IQ、MSCI、PitchBook、Morningstar、LSEG、Daloopa、Moody's、Dun & Bradstreet、Third Bridge、Verisk 等 15+ 家金融数据提供商。

### 4. Claude Managed Agent 部署模板

提供 `agent.yaml` 配置、子代理设置、转向事件示例和每个 Agent 的安全注意事项。

### 5. Microsoft 365 集成

管理工具支持将 Claude 作为加载项部署到 Excel、PowerPoint、Word 和 Outlook。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Python（86.5%）、Shell（7.1%）、JavaScript（6.4%） |
| **平台** | Claude Cowork、Claude Code、Claude Managed Agents API |
| **协议** | Model Context Protocol（MCP） |
| **配置格式** | YAML（agent.yaml）、Markdown（技能/提示词） |
| **办公集成** | Microsoft 365（Excel、PowerPoint、Word、Outlook） |
| **数据连接** | FactSet、Capital IQ、PitchBook、Morningstar 等 15+ 家 |
| **推荐模型** | Claude Opus 4.7 |

---

## 项目亮点

### Anthropic 官方出品
这是 Anthropic 官方维护的金融行业参考架构，而非社区项目，确保了企业级代码标准和最佳实践。

### 三合一 Agent 架构
每个 Agent 模板整合了技能（领域知识）、连接器（数据访问）和子代理（子任务处理），形成完整的端到端工作流，而非简单的提示模板。

### 双模式部署
同时支持 Claude Cowork 插件模式（交互式使用）和 Claude Managed Agent API 模式（自动化部署），灵活适配不同使用场景。

### 强大的模型支撑
Claude Opus 4.7 在 Vals AI 的 Finance Agent 基准测试中得分 64.37%，领先行业，为这些 Agent 提供了强大的底层推理能力。

---

## 应用场景

### 投资银行自动化
自动生成 CIM（公司信息备忘录）、Teaser、买方名单、合并模型和项目跟踪材料，大幅减少分析师制作 Pitchbook 的时间。

### 股票研究与分析
自动化财报电话会议分析、财务模型更新（DCF、LBO、三表联动、可比公司分析）、研究报告起草和催化剂跟踪，将研究周期从数周缩短至数天。

### 私募股权全流程管理
覆盖从项目寻源、筛选、尽职调查清单、投资委员会备忘录到投后监控的完整 PE 工作流。

### 财务运营与合规
自动化总账对账、月末结账、财务报表审计和 KYC 审查等中后台运营流程，提升合规效率和准确性。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | ~16,500 |
| **总 Forks** | ~2,067 |
| **今日新增 Stars** | ~3,660 |
| **许可证** | Apache License 2.0 |
| **主要语言** | Python |
| **贡献者** | 7 |
| **Trending 排名** | 全球第 1 |

---

## 总结

Claude Financial Services 是 **Anthropic 官方推出的金融行业 AI Agent 参考架构**，约 16,500 Stars，今日新增约 3,660 Stars，位列 GitHub Trending 全球第一。项目以 Python 为主要语言，提供 10 个即用型 Agent 模板覆盖投行、研究、PE 和运营四大金融垂直领域，通过 MCP 协议连接 15+ 家金融数据提供商，支持 Claude Cowork 插件和 Managed Agent API 双模式部署。它是金融机构快速将 Claude AI 能力融入实际业务工作流的一站式解决方案。

---

*数据来源：GitHub 仓库 (anthropics/financial-services)，2026 年 5 月访问*

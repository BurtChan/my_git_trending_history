# CWC Workshops 项目分析

## 项目名称
**CWC Workshops（Code with Claude Workshops）** — Anthropic 官方 Claude 代理开发实战工作坊课程合集
- **GitHub**: [anthropics/cwc-workshops](https://github.com/anthropics/cwc-workshops)
- **许可证**: Apache-2.0

---

## 项目概述

CWC Workshops 是 Anthropic 官方发布的"Code with Claude"（CWC）系列工作坊的教学材料仓库，涵盖了从模型选择到多代理协作、记忆系统、评估驱动开发等 AI 代理开发的全方位主题。该仓库包含 9 个独立的工作坊，每个工作坊都围绕 Claude Managed Agents、MCP（Model Context Protocol）和 Claude Code 这三大 Anthropic 核心平台展开，提供完整的代码、配置和评估套件。

这个仓库的价值不仅在于教授 Claude 的使用方法，更在于展示了 Anthropic 对 AI 代理开发的最佳实践理解。每个工作坊都强调"可衡量的改进"而非主观感觉——通过评估套件（eval）量化每次提示变更的效果，这与 Anthropic 在 CWC 系列中一贯倡导的"Eval-Driven Agent Development"理念一脉相承。仓库虽然标注为"Not maintained and not accepting contributions"，但其教学内容对理解 Anthropic 代理生态的技术架构仍具有极高的参考价值。

项目以 TypeScript 和 Python 为主要语言（分别占 43.4% 和 26.8%），辅以 JavaScript、Shell、HTML 和 CSS，反映了现代 AI 代理开发中全栈技术栈的融合趋势。每个工作坊的代码量不大，但都经过精心设计，确保在 45 分钟至数小时内可以完成，适合快速上手和实验。

## 核心功能

| 工作坊 | 主题 | 核心内容 |
|--------|------|----------|
| rightmodel | 选择正确的模型 | 审计 LLM 评估套件，扫描模型与推理参数，找到最优的质量性价比和质量每秒配置 |
| agent-decomposition | 多代理系统组合 | 将 400 行的 inventory agent 拆解为 Skills + 代码执行 + Callable Agents，含逐步验证 evals |
| how-we-claude-code | 我们如何使用 Claude Code | 三阶段 AI 辅助产品工作流：访谈→规格→四路设计探索→Vite + React 应用（机器可读 DOM 契约） |
| ship-your-first-managed-agent | 发布你的首个管理代理 | Streamlit 事故仪表盘 + 离线 SRE Agent，实现 7 个核心函数，grep 7 万行日志并识别问题提交 |
| agent-battle | 代理对战 | 45 分钟竞赛，配置 Claude Managed Agent（系统提示、Skills、MCP 服务器、模型），驱动游戏机器人 |
| agents-that-remember | 有记忆的代理 | 将 agent 从"金鱼"变为"同事"，叠加记忆存储 + Dreaming Service（记忆巩固服务） |
| eval-driven-agent-development | 评估驱动的代理开发 | 迭代 PPTX 生成代理的 6 个变体，双层评分系统（编程指标 + LLM 裁判） |
| production-ready-agent | 生产就绪代理（Deal Desk） | 聊天优先 UI + 多代理 M&A 研究团队，协调器委派 4 个并行研究子代理 + 记忆存储 + Linear 集成 |
| research-desk | 研究台 | SEC 文件研究台，自托管 Next.js 控制台，子代理专家 + 共享记忆 + 每周备忘录部署 |

## 技术栈

| 组件 | 技术 |
|------|------|
| 主要语言 | TypeScript (43.4%)、Python (26.8%)、JavaScript (14.0%) |
| 辅助语言 | Shell (5.5%)、HTML (5.5%)、CSS (4.5%)、Dockerfile (0.3%) |
| 代理平台 | Claude Managed Agents、Claude Code |
| 工具协议 | MCP（Model Context Protocol） |
| 前端框架 | Streamlit、Next.js、Vite + React |
| 许可证 | Apache-2.0 |

## 项目亮点

### Anthropic 代理开发的"官方教科书"

CWC Workshops 是 Anthropic 官方出品的代理开发教学材料，涵盖了从入门到进阶的完整路径。9 个工作坊由浅入深——从"选择正确的模型"到"生产就绪代理"，涵盖了 AI 代理开发中几乎所有关键议题。每个工作坊都不是空洞的理论讲解，而是提供可运行的代码和配置，学习者可以在自己的环境中复现和修改。这种"官方出品"的权威性使其成为理解 Anthropic 代理生态最可靠的学习资源。

### 评估驱动开发的系统化方法论

项目中反复强调"Eval-Driven Agent Development"理念，即通过系统化的评估套件量化代理的改进效果。例如在 eval-driven-agent-development 工作坊中，迭代 PPTX 生成代理经过 6 个变体（朴素→视觉→排版→配色→密度→QA 循环），每个变体都通过编程指标和 LLM 裁判双重评分验证。这种"每次提示变更都被衡量，而非凭感觉"的方法论，代表了 AI 代理开发从"提示工程"向"代理工程"成熟化的重要方向。

### 记忆与协作的完整方案

agents-that-remember 和 production-ready-agent 两个工作坊展示了 AI 代理的两大高级能力——持久化记忆和团队协作。前者通过记忆存储（Memory Store）实现跨会话持久化，通过 Dreaming Service（做梦服务）整合过去的对话记录，将 agent 从"金鱼"变为"同事"。后者通过协调器（Coordinator）将复杂任务分配给多个专业子代理（研究、分析、写作），配合共享记忆存储实现团队级别的知识积累和复用。

### 实战竞赛与游戏化教学

agent-battle 工作坊采用"代理对战"的竞赛形式，参与者在 45 分钟内配置 Claude Managed Agent（系统提示、Skills、MCP 服务器、模型选择），使其驱动本地游戏机器人收集钻石。评分机制为"钻石最多者胜，令牌最少者打破平局"，并配有快速 `--eval` 决策探测循环（约 30 秒测试后进行 5 分钟正式运行）。这种游戏化设计使抽象的代理配置概念变得具体可感，极大地降低了学习门槛。

## 应用场景

### AI 代理开发者快速入门

对于刚接触 Claude 代理生态的开发者，CWC Workshops 提供了一条结构化的学习路径。从 ship-your-first-managed-agent 入门（实现 7 个核心函数即可获得一个可工作的 SRE 代理），到 production-ready-agent 进阶（构建多代理研究团队），每个工作坊都可在 45 分钟到数小时内完成，降低了学习曲线。

### 企业 AI 代理架构参考

production-ready-agent 和 research-desk 两个工作坊展示了企业级 AI 代理的典型架构——协调器 + 专业子代理 + 记忆存储 + 外部集成（Linear、SEC 文件等）。企业团队可以参考这些工作坊的架构设计，快速搭建自己的 AI 辅助研究、客服或分析系统。

### 代理评估体系建设

eval-driven-agent-development 工作坊提供的双层评分系统（编程指标 + LLM 裁判）是构建代理评估体系的实用参考。对于需要量化代理性能的团队，可以直接借鉴其评估设计，为自己的代理应用建立可重复、可比较的评估流程。

### AI 工程团队培训材料

CWC Workshops 的 9 个工作坊覆盖了 AI 代理开发的核心技能，适合作为企业内部 AI 工程团队的培训材料。特别是 agent-decomposition 和 agents-that-remember 两个工作坊，涵盖了代理拆解和记忆管理两大高阶主题，可以帮助团队快速提升代理开发能力。

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 1,500 |
| 🍴 Forks | 478 |
| 📅 创建时间 | 2026-05-06 |
| 🌐 语言 | TypeScript / Python / JavaScript |
| 📜 许可证 | Apache-2.0 |


---

## 📋 更新记录

### 更新 1 — 2026年07月20日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
CWC Workshops 仓库在 2026 年 5 月 Anthropic 旧金山 Code with Claude 大会后持续获得关注。大会结束后，Anthropic 公布了主要 sessions 的录制视频，工作坊的代码仓库（即本仓库）也随之获得了更多开发者关注。虽然仓库本身标注为"Not maintained and not accepting contributions"，但其 9 个工作坊的教学内容仍然具有很高的参考价值。特别值得一提的是 research-desk 工作坊展示的 SEC 文件研究台架构（自托管 Next.js 控制台 + 子代理专家 + 共享记忆 + 每周备忘录部署），以及 eval-driven-agent-development 工作坊的评估驱动方法论，持续被社区引用和学习。Stars 从 1,500 增长到 1,668，Forks 从 478 增长到 491。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 1,500 | 1,668 | +168 |
| 总 Forks | 478 | 491 | +13 |

**核心变化概要**：
- Code with Claude 2026 大会视频录制公开后持续获得关注
- 9 个工作坊的教学内容被广泛引用和学习
- Stars 从 1,500 增长至 1,668（+168），Forks 从 478 增长至 491（+13）

---

## 📋 更新记录

### 更新 2 — 2026 年 7 月 21 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：Anthropic 的 CWC Workshops（Code with Claude Workshops）仓库在 Code with Claude 2026 大会后持续获得关注。大会所有 Workshop 的代码仓库已在 GitHub 公开发布，开发者可自行在家完成实践。仓库涵盖了 Agent 架构设计、Eval 评估体系、MCP 工具开发等多个前沿主题。与此同时，Claude Code 本身也在快速迭代——新增后台 /fork 会话管理、更智能的 /resume 历史会话恢复、WebSearch 安全增强、子代理安全防护和 Bash 执行安全措施等。CWC 仓库作为 Anthropic 官方维护的教学实践合集，已成为 Claude Code 生态中不可或缺的学习资源。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 1,500 | 1,713 | +213 |
| 总 Forks | 477 | ~491 | +14 |

**核心变化概要**：
- Code with Claude 2026 大会所有 Workshop 代码仓库已公开发布
- 社区贡献者持续增长，覆盖 Agent 架构、Eval 评估等多个主题
- Claude Code 新增后台 /fork 会话、更智能的 /resume 和安全增强

## 总结

CWC Workshops 是 Anthropic 官方出品的 Claude 代理开发实战教程合集，通过 9 个精心设计的工作坊，系统性地涵盖了从模型选择、代理拆解、记忆管理到评估驱动开发和生产级部署的完整代理开发知识体系。它不仅是一套教学材料，更是 Anthropic 对 AI 代理最佳实践的官方阐述，对于任何希望深入理解 Claude 代理生态的开发者来说都具有极高的参考价值。

---

*数据来源：GitHub 仓库 (anthropics/cwc-workshops)，2026 年 7 月访问*

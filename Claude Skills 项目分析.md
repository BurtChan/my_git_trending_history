# Claude Skills 项目分析

## 项目名称

**Claude Skills** — 面向 13 种 AI 编码工具的 354 个开源技能与插件库

- **GitHub**: [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills)
- **许可证**: MIT

---

## 项目概述

Claude Skills 是目前**最全面的开源 AI 编码技能库**，由 Alireza Rezvani 创建维护。项目收录了 354 个生产级可用的技能（Skills）、30+ 个智能体（Agents）、70+ 个自定义命令和 711 个参考文档，覆盖 18 个专业领域。这些技能以结构化指令包的形式赋予 AI 编码工具它们原本不具备的领域能力。

项目原生支持 Claude Code、OpenAI Codex、Gemini CLI、OpenClaw、Hermes Agent、Mistral Vibe 六种 AI 编码工具，并通过自动转换脚本兼容 Cursor、Aider、Windsurf、Kilo Code、OpenCode、Augment、Antigravity 等七种工具，总计覆盖 13 种 AI 编码平台。这种"一次编写、到处运行"的设计使其成为 AI 编码工具生态中极其重要的共享技能基础设施。

每个技能包含 SKILL.md 结构化指令、593 个纯 Python 标准库 CLI 脚本（零依赖安装）和领域特定的参考文档。技能按领域分为工程核心、工程高级（POWERFUL 层）、产品管理、市场营销、生产力、学术研究、项目管理、合规与质量管理、C 级管理层、商业运营等 18 个类别，从日常编码到企业战略全覆盖。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 354 个生产级技能 | 覆盖工程、产品、营销、合规、C 级顾问等 18 个领域的技能包 |
| 13 种 AI 工具支持 | 原生支持 Claude Code、Codex、Gemini CLI 等，转换兼容 Cursor、Aider 等 |
| 零依赖 CLI 脚本 | 593 个 Python CLI 工具全部基于标准库，无需 pip 安装 |
| 技能/智能体/角色三层架构 | Skills（如何做）、Agents（做什么）、Personas（谁在思考）分离设计 |
| 一键安装与转换 | 支持 `/plugin install` 一键安装和跨平台自动转换 |
| 711 个参考文档 | 模板、检查清单和领域知识文件 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | Python（stdlib only） |
| 技能格式 | SKILL.md（YAML frontmatter + Markdown） |
| 转换脚本 | Bash（自动转换为不同 AI 工具格式） |
| 许可证 | MIT |

---

## 项目亮点

### 史无前例的技能覆盖面

354 个技能横跨 18 个专业领域，从安全审计（security-auditor）、RAG 架构设计（rag-architect）到 C 级管理层顾问（CEO/CTO/CFO 全覆盖），从 ISO 医疗器械法规到 GDPR/SOC 2 合规框架。这种广度和深度的组合在开源 AI 技能库中前所未有。

### 三层架构的精细设计

项目明确区分了 Skills（执行指南）、Agents（任务定义）和 Personas（思考角色）三个层次。Skills 回答"怎么做"，Agents 回答"做什么"，Personas 定义"谁在思考"。这种架构使 AI 编码工具的使用从简单的代码生成提升为结构化的专业知识调用。

### 跨平台一键转换

通过自动转换脚本，一个技能包可以同时适配 13 种 AI 编码工具，包括原生支持（Claude Code、Codex、Gemini CLI）和转换兼容（Cursor、Aider 等）。约 15 秒即可将全部 345 个技能转换为 9 种目标工具格式，极大降低了跨工具使用的门槛。

---

## 应用场景

### 全栈开发者日常提效

安装核心工程技能（架构设计、前端、后端、QA、DevOps）后，AI 编码工具可按最佳实践执行任务，减少反复的人工指导。

### 企业级合规开发

内置 ISO 13485、MDR 2017/745、FDA、ISO 27001、GDPR、SOC 2 等法规相关的技能包，帮助医疗设备、金融科技等受监管行业的开发团队在编码阶段就遵循合规要求。

### 营销与产品团队 AI 赋能

48 个市场营销技能（内容、SEO、CRO、增长、情报）和 17 个产品管理技能，让非技术团队也能利用 AI 编码工具完成内容创作、SEO 审计、产品规划等工作。

### C 级管理层 AI 顾问

68 个 C 级顾问技能涵盖 CEO、CTO、CFO、CMO、CRO、CPO、COO、CHRO、CISO 等全部 C-suite 角色，为高层管理者提供基于 AI 的战略分析和决策支持。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 19,948 |
| 🍴 Forks | 2,737 |
| 今日新增 | 130 stars |
| 主要语言 | Python |
| 创建时间 | 2025-10-19 |
| 许可证 | MIT |

---

## 总结

Claude Skills 是 AI 编码工具生态中规模最大、覆盖最全面的开源技能库。其 354 个技能覆盖从底层编码到企业战略的全链路，三层架构设计（Skills/Agents/Personas）提供了精细化的知识组织方式，而跨 13 种 AI 工具的一键转换能力使其成为 AI coding agent 领域的"共享技能基础设施"。对于任何使用 AI 编码工具的开发者和团队而言，Claude Skills 都是不可或缺的能力扩展库。

---

*数据来源：GitHub 仓库 (alirezarezvani/claude-skills)，2026 年 7 月访问*

# Harness 项目分析

## 项目名称

**Harness** — Claude Code 的团队架构工厂，通过元技能自动设计领域专属的 Agent 团队

- **GitHub**: [revfactory/harness](https://github.com/revfactory/harness)
- **许可证**: Apache 2.0

---

## 项目概述

Harness 是一个面向 Claude Code 的**元技能（Meta-Skill）**，它位于 Claude Code 生态的 **L3 Meta-Factory 层**——即「生成其他 Harness 的工厂」。其核心理念是：用户只需输入一句领域描述（如「为这个项目构建一个 Harness」），系统便会自动分析任务需求，从 6 种预定义的团队架构模式中选择最合适的方案，生成专门的 Agent 定义（`.claude/agents/`）和技能文件（`.claude/skills/`）。

在 AI Agent 从「单兵作战」迈向「团队协作」的趋势下，Harness 回答了一个关键问题：**如何让一群 AI Agent 高效协同工作？** 传统的做法是手动编写每个 Agent 的角色定义和协作规则，而 Harness 将这一过程自动化——从架构设计到 Agent 定义再到技能生成，一站式完成。

根据项目团队进行的对照实验（A/B Test），在 15 个软件工程任务中，使用 Harness 的 Claude Code 输出质量从平均 49.5 分提升至 79.3 分（满分 100），**质量提升达 60%**。更重要的是，任务越复杂，改进幅度越大：基础任务 +23.8 分、高级任务 +29.6 分、专家级任务 +36.2 分。这证明了结构化的团队预配置在复杂任务中的巨大价值。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **团队架构自动设计** | 输入领域描述，自动选择最优团队架构模式并生成完整配置 |
| **6 种架构模式** | Pipeline（流水线）、Fan-out/Fan-in（扇出/扇入）、Expert Pool（专家池）、Producer-Reviewer（生产-审核）、Supervisor（监督者）、Hierarchical Delegation（层级委派） |
| **Agent 定义生成** | 自动创建 `.claude/agents/` 目录下的专业化 Agent 配置文件 |
| **技能文件生成** | 自动创建 `.claude/skills/` 目录下的领域知识增强文件 |
| **多语言支持** | 支持英语（"Build a harness"）、韩语（"하네스 구성해줘"）、日语（"ハーネスを構成して"）等触发指令 |
| **生态协作** | 可与 Archon（运行时配置）、ECC（跨 Harness 工作流）、meta-harness（Codex 运行时移植）等生态工具协同 |
| **质量量化** | 提供标准化的 A/B 测试框架，量化评估团队架构对输出质量的提升效果 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | HTML / Markdown（Claude Code 技能文件格式） |
| **运行环境** | Claude Code（需启用 `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`） |
| **输出格式** | `.claude/agents/` + `.claude/skills/` 目录结构 |
| **架构层** | L3 Meta-Factory（Claude Code 生态最高层） |
| **子层定位** | Team-Architecture Factory（团队架构工厂） |
| **许可证** | Apache 2.0 |

---

## 项目亮点

### 1. 元工厂级别的抽象
Harness 不只是生成一个团队配置，它是一个「工厂的工厂」——通过分析领域描述，在更高层面设计整个团队架构，再逐层生成具体的 Agent 和技能。这种元层级的设计使其具备极强的通用性和可扩展性。

### 2. 6 大架构模式覆盖全场景
从简单的流水线到复杂的层级委派，6 种预定义模式几乎覆盖了所有多 Agent 协作场景。系统根据任务特征智能选择最匹配的模式，无需用户具备系统设计经验。

### 3. 质量提升可量化
60% 的平均质量提升不是凭感觉，而是通过严格的 A/B 对照实验得出。更关键的是「难度越高收益越大」的特性，使得 Harness 在真正有挑战性的项目中价值最为突出。

### 4. 丰富的应用用例
项目提供了大量现成的用例参考，包括深度研究、网站开发、漫画制作、YouTube 内容规划、代码审查、技术文档、数据管道设计、营销活动等，用户可以快速上手。

---

## 应用场景

### 复杂软件开发
大型软件项目需要前端、后端、测试、架构等多个角色协同。Harness 可自动拆分任务为专业化 Agent 团队，通过 Producer-Reviewer 模式确保代码质量。

### 内容创作与媒体制作
从 Webtoon 制作到 YouTube 视频策划，Harness 通过 Pipeline 或 Fan-out/Fan-in 模式将创意工作流自动化——一个 Agent 负责剧本、一个负责分镜、一个负责审核。

### 深度研究与报告
学术研究或市场调研需要信息收集、分析、撰写、校对等多环节协作。Expert Pool 模式可以动态调度不同领域的专家 Agent 处理跨学科任务。

### 企业级任务自动化
营销活动策划、数据管道设计、技术文档编写等企业场景，Hierarchical Delegation 模式可模拟真实组织的层级分工，从总监到专员各司其职。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 3,819 |
| **总 Forks** | 577 |
| **今日新增 Stars** | 68 |
| **许可证** | Apache 2.0 |
| **创建时间** | 2026 年 3 月 |
| **主要语言** | HTML |

---

## 总结

Harness 是 **Claude Code 多 Agent 协作领域的创新项目**，3.8k+ Stars。它以元技能的形式运行在 Claude Code 的 L3 Meta-Factory 层，用户只需一句话描述领域需求，即可自动从 6 种架构模式中选择最优方案并生成完整的 Agent 团队配置。经过严格的 A/B 实验验证，Harness 将 LLM 代码 Agent 的输出质量提升了 60%，且在越复杂的任务上效果越显著。作为 Claude Code Agent Teams 生态的基础设施级工具，Harness 代表了 AI Agent 从「个体智能」到「群体智能」的关键一步。

---

*数据来源：GitHub 仓库 (revfactory/harness)，2026 年 5 月访问*

# Council of High Intelligence 项目分析

## 项目名称

**Council of High Intelligence** — 18 位 AI 人格组成的多模型审议委员会，为重大决策提供结构化对抗性思维

- **GitHub**: [0xNyk/council-of-high-intelligence](https://github.com/0xNyk/council-of-high-intelligence)
- **许可证**: MIT

---

## 项目概述

Council of High Intelligence（高智商委员会）是一个创新的多 LLM 审议系统，由开发者 0xNyk 于 2026 年 3 月创建。它将 18 位来自不同知识领域和思维范式的 AI 人格（从亚里士多德到费曼，从孙子到图灵奖得主 Karpathy）组织成一个结构化的审议委员会，通过多轮辩论和对抗性思维来帮助用户做出更明智的重大决策。该项目目前拥有超过 1,700 个 GitHub Star，在 AI Agent 和决策工具领域引起了广泛关注。

Council 的核心理念是：一个模型的"最佳猜测"远不如 18 个独立分析视角的交叉验证可靠。单一 LLM 查询只能给出一个模型的自信输出，而 Council 强制 3-18 个独立分析从不同知识传统出发，相互质疑彼此的假设，最终合成一个充分暴露分歧而非掩盖分歧的裁决。这种结构化审议的设计灵感来源于董事会决策、科学同行评议和辩论赛中的对抗性论证机制，将人类数千年积累的决策智慧编码为可编程的 AI Agent 交互模式。

项目以 Claude Code Skill 和 Codex Skill 的形式部署，安装极为简便——一条命令即可将 18 个 Council Agent 和对应的 Skill 文件安装到用户的开发环境中。使用时只需输入 `/council` 加上问题描述，即可触发完整的多轮审议流程。Council 支持三种模式：Full（全部 18 位成员参与完整审议）、Quick（快速简化审议）和 Duo（指定 2 位成员进行对抗式辩论），灵活适配不同决策场景的时间需求。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **18 位 AI 人格** | Aristotle、Socrates、Sun Tzu、Ada Lovelace、Marcus Aurelius、Machiavelli、Lao Tzu、Feynman、Linus Torvalds、Miyamoto Musashi、Alan Watts、Andrej Karpathy、Ilya Sutskever、Daniel Kahneman、Donella Meadows、Charlie Munger、Nassim Taleb、Dieter Rams |
| **极性配对（Polarity Pairs）** | 13 对精心设计的对立配对（如 Socrates vs Feynman、Aristotle vs Lao Tzu），强制产生真实的思维张力而非表面赞同 |
| **多 LLM 提供商路由** | 跨 Claude（opus/sonnet）、GPT、Gemini、Ollama 等多个 LLM 提供商路由，确保不同人格使用不同模型的推理路径 |
| **问题重述门控（Problem Restate Gate）** | 每位成员必须先重新表述问题，如果 3+ 位成员的表述方式完全不同，说明问题本身需要重新定义 |
| **反对配额与新颖性门控** | 强制异议配额确保不同意声音被充分表达，新颖性门控确保不会过早达成表面共识 |
| **三种审议模式** | Full（18人完整审议）、Quick（快速简化）、Duo（指定双人对抗，如 `/council --duo --members torvalds,ada`） |
| **Claude Code / Codex 兼容** | 一键安装为 Claude Code Skill 或 Codex Skill，与现有开发工作流无缝集成 |
| **结构化裁决输出** | 最终裁决以 "Unresolved Questions"（未解决问题）和 "Recommended Next Steps"（建议下一步）开头，而非自信的虚假共识 |
| **反群体思维机制** | 当 >70% 成员过早达成一致时，强制两位成员 steelman（善意重构）对立观点 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要语言** | Shell（安装脚本）、YAML/Markdown（Agent 配置和 Prompt 模板） |
| **运行平台** | Claude Code（Anthropic）、Codex CLI（OpenAI） |
| **AI Agent** | 18 个独立 Agent，每个封装特定的思维范式和人格设定 |
| **LLM 路由** | 多提供商路由（Claude opus/sonnet、GPT、Gemini、Ollama 等） |
| **安装方式** | `./install.sh`（Claude Code）或 `./install.sh --codex`（Codex） |
| **许可证** | MIT（CC0 公共领域声明） |

---

## 项目亮点

### 跨学科思维的工程化实现

Council 最具创造力的设计在于将人类数千年的跨学科思维传统工程化为可编程的 Agent 交互模式。18 位成员横跨哲学（亚里士多德、苏格拉底、老子）、科学（费曼、Ada Lovelace）、军事战略（孙子、宫本武藏）、决策科学（Kahneman、Taleb）、系统思维（Donella Meadows）、工程实践（Torvalds、Rams）、投资哲学（Munger）、AI 技术（Karpathy、Sutskever）等多个领域，每位的 Prompt 都精心编码了其核心思维范式和关键偏见（Polarity）。这种"让历史上最优秀的头脑在你的问题上进行辩论"的体验，是任何单一 LLM 查询都无法提供的。

### 真正的模型多样性（非换装式）

很多多 Agent 系统只是让同一个模型扮演不同"角色"——本质上是同一种推理穿上了不同的戏服。Council 通过多提供商路由（Multi-Provider Routing）确保不同成员使用不同的底层模型（如 Aristotle 用 opus 追求深度分类、Torvalds 用 sonnet 追求快速判断），从而产生真正不同的推理路径和结论。配合极性配对的设计，这种真实的模型多样性确保了审议的对抗性是实质性的而非表演性的。

### 反群体思维的制度设计

Council 对群体思维（Groupthink）的防范达到了制度设计层面。三个关键机制协同工作：① 异议配额（Dissent Quotas）确保反对声音被分配到具体成员；② 新颖性门控（Novelty Gates）检测共识是否达成过早；③ 当 >70% 成员过快达成一致时，系统强制两位成员进行 Steelman（善意重构对立论点的最强版本）。这些机制源自真实组织决策和行为经济学的研究成果（Kahneman 的 Thinking Fast/Slow、Sunstein 的 Why Societies Need Dissent），被巧妙地编码为 AI Agent 交互规则。

### 问题重述的元认知门控

Council 的 Problem Restate Gate 是一个精妙的元认知设计：每位成员在回答之前必须先用自己的方式重新表述问题。如果 3 位或更多成员的重述方式差异显著，系统会标记"问题本身可能是错误的"。这种机制捕捉到了人类决策中最常见的失败模式——**用错误的方式回答错误的问题**——并将其自动化为 AI 系统的内建检测。

---

## 应用场景

### 重大架构决策

技术团队在面对"微服务还是单体架构？""应该自建还是采购？""使用哪种数据库？"等重大技术决策时，可以将问题提交给 Council。Council 的 18 位成员会从不同角度审视：Kahneman 会分析决策偏见和锚定效应，Taleb 会评估尾部风险和反脆弱性，Torvalds 会给出务实的工程判断，Karpathy 会从 AI/ML 角度评估可扩展性。最终裁决不仅给出建议，还会暴露所有未解决的核心分歧和建议的后续验证步骤。

### 产品策略制定

产品经理可以用 Council 来审议产品方向决策。Munger 的逆向思维（"什么会保证失败？"）和 Rams 的用户中心设计（"少而更好——用户说了算"）会形成强力对立，迫使团队同时考虑竞争劣势和用户体验。Watts 的视角重构功能可能会揭示团队正在回答一个错误的问题——这在产品方向决策中是极其常见且代价高昂的错误。

### 投资与风险评估

Council 的多位成员天然适配投资决策场景：Munger 的多模型推理和逆向思维、Taleb 的反脆弱和尾部风险分析、Kahneman 的认知偏见和前景理论、Meadows 的系统思维和反馈回路。对于"是否应该投资这个技术栈？""这个市场的长期风险是什么？"等问题，Council 能提供远超单一分析的全面视角。

### AI Agent 和开源策略决策

作为 Claude Code / Codex 的原生 Skill，Council 特别适合在开发工作流中即时使用。开发者在编写代码时遇到的策略性问题——"是否应该开源这个 Agent 框架？""应该在这里加缓存吗？"——都可以通过 `/council --quick` 快速获取多角度分析。Quick 模式在几秒内即可返回简化版的审议结果，不会打断开发流程。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 1,762 |
| **总 Forks** | 193 |
| **今日新增 Stars** | 323 |
| **许可证** | MIT |
| **主要语言** | Shell |
| **创建时间** | 2026-03-02 |

---

## 总结

Council of High Intelligence 是 **AI 时代的结构化决策辅助工具**，1.7K Stars，将 18 位跨学科 AI 人格、极性配对对抗机制、多模型路由和反群体思维制度设计融合为一个简洁的 `/council` 命令。它不是一个简单的"多 Agent 聊天室"，而是一个经过精心工程化的审议系统——借鉴了董事会决策、科学同行评议和行为经济学的研究成果，将人类最优秀的跨学科思维传统编码为可编程的 AI 交互模式。

---

*数据来源：GitHub 仓库 (0xNyk/council-of-high-intelligence)，2026 年 6 月访问*

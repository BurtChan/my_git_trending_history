# Kilo Code 项目分析

## 项目名称
**Kilo Code** — 最受欢迎的开源 AI 编程代理，一站式智能工程平台
- **GitHub**: [Kilo-Org/kilocode](https://github.com/Kilo-Org/kilocode)
- **许可证**: MIT
- **官网**: https://kilo.ai/

---

## 项目概述

Kilo Code 是一款开源 AI 编程代理，可在 VS Code、JetBrains IDE 及命令行界面中运行，为开发者提供全流程的 AI 辅助编程体验。该项目由 GitLab 联合创始人兼前 CEO Sid Sijbrandij 与 Scott Breitenother 于 2025 年 3 月联合创立，总部位于旧金山。作为 Cline 和 Roo Code 的开源超集，Kilo Code 在继承二者优秀基因的基础上，引入了编排器模式、并行代理、自动模型路由等创新功能，形成了独具特色的"Kilo 速度"开发理念。截至 2026 年 6 月，项目已获得超过 300 万开发者用户，累计处理超 30 万亿个 token，在 OpenRouter 上排名第一。

Kilo Code 的核心哲学是"模型自由"——支持 500 多个 AI 模型（包括 GPT-5.5、Claude Opus 4.7、Claude Sonnet 4.6、Gemini 3.1 Pro Preview 等前沿模型），且按提供商原价收费，零加价。开发者可以接入自己的 API 密钥（BYOK），也可以通过 Kilo Gateway 选择最优模型组合。这种模型无关的设计理念使其在 Cursor、Windsurf、GitHub Copilot 等竞品中脱颖而出，为开发者提供了真正的选择自由。

2025 年 12 月，Kilo Code 完成了 800 万美元种子轮融资，投资方包括 Cota Capital（领投）、General Catalyst、Breakers、Quiet Capital 和 Tokyo Black。团队以极快的迭代速度著称——项目创建仅 15 个月便积累了超过 23,000 次提交和 430 个发布版本，体现了其"Kilo 速度"的工程文化。43% 的 Kilo 用户据称从 Cursor 迁移而来，反映出开源社区对透明度和可定制性的强烈需求。

---

## 核心功能

- **多 IDE 支持**: 以 VS Code 扩展、JetBrains 插件和独立 CLI 三种形态运行，开发者无需更换已有编辑器即可使用
- **500+ 模型接入**: 支持 OpenAI、Anthropic、Google、Mistral 等主流模型提供商，以及开源模型，按提供商原价零加价计费
- **编排器模式 (Orchestrator Mode)**: 可将复杂任务自动分解为多个子任务，分配给不同模式（Ask、Code、Debug 等）并行执行，实现端到端自动化
- **并行代理 (Parallel Agents)**: 多个 AI 代理可同时规划、构建和审计代码，大幅提升开发效率
- **自动模型路由 (Auto Model)**: 根据任务复杂度和预算自动选择最优模型策略，无需手动切换
- **任务中模型切换**: 可在同一任务执行过程中动态切换不同模型，针对不同子任务使用最合适的模型
- **MCP 协议支持**: 支持模型上下文协议（Model Context Protocol），可扩展代理能力
- **AGENTS.md 配置**: 通过项目根目录的标准化 Markdown 文件为 AI 代理定义项目规范、编码标准和约束条件
- **自主模式 (`kilo run --auto`)**: 支持无人值守的 CI/CD 自动化执行，可集成到持续集成流程中
- **AI 代码审查**: 在 pull request 上自动执行 AI 驱动的代码审查，支持在 app.kilo.ai/code-reviews 配置
- **Cloud 云端代理**: 通过 app.kilo.ai/cloud 提供无需本地环境的云端编程体验
- **自定义代理构建**: 开发者可创建专用代理，针对特定工作流程进行优化

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | TypeScript |
| IDE 扩展 | VS Code Extension API |
| JetBrains 集成 | JetBrains Plugin SDK |
| 命令行工具 | Node.js CLI |
| 模型接入 | OpenAI API、Anthropic API、Google AI API、OpenRouter 等 |
| 扩展协议 | MCP (Model Context Protocol) |
| 许可证 | MIT |
| 代码仓库结构 | Monorepo（含 VS Code 扩展、JetBrains 插件、CLI 等子包）|
| 项目配置 | AGENTS.md 标准化配置文件 |

---

## 项目亮点

### 由 GitLab 联合创始人倾力打造

Kilo Code 的联合创始人 Sid Sijbrandij 是 GitLab 的联合创始人兼前 CEO，在开源 DevOps 领域拥有深厚的经验和广泛的行业影响力。这一背景为 Kilo Code 带来了成熟的社区运营理念和企业级产品思维，也使项目从诞生起就备受关注。CEO Scott Breitenother 提出了"我们不是在用机器人替代人类，而是在让人类变成赛博格"的理念，强调 AI 是增强而非替代开发者。凭借这支护航团队，Kilo Code 在 2025 年 12 月成功获得 800 万美元种子融资，投资方阵容包括 General Catalyst 等顶级机构。

### 模型无关的极致开放策略

Kilo Code 最大的差异化优势在于其坚定的"模型无关"立场。与 Cursor 绑定自有模型、Claude Code 仅支持 Anthropic 模型不同，Kilo Code 支持 500 多个模型，涵盖闭源和开源两大阵营。更重要的是，其计费模式为"零加价"——开发者按模型提供商的原价付费，Kilo Code 不从 token 费用中抽取利润。这种商业模式虽然在短期内放弃了 API 差价收入，但赢得了社区的深度信任。据 Vellum 评测，Kilo Code 的定价模式虽然对新手略感复杂，但对于熟悉 API 使用的开发者而言，实际成本远低于 Cursor 的 $20/月订阅制。

### 编排器模式与并行代理的工程创新

Kilo Code 引入的编排器模式是其最具技术亮点的功能。开发者只需描述一个高层目标，编排器会自动将其分解为多个子任务，并根据任务类型分配给 Ask（咨询）、Code（编码）、Debug（调试）等不同模式的代理执行。同时，并行代理功能允许多个 AI 代理同时工作——一个负责规划、一个负责编码、一个负责审计——形成类似"AI 开发团队"的协作模式。这种多代理架构在竞品中尚属罕见，代表了 AI 编程工具从"单助手"向"多代理协作"的演进方向。

### 开源生态中的"超集"定位

Kilo Code 的技术根基来自 Cline 和 Roo Code（原 Roo Code 已归档），是在二者基础上的增强超集。开源社区对此反响积极——在 Cursor 论坛上，有用户评价："Kilo 在开源、透明度和定制化方面表现出色。如果你需要更多配置选项，Kilo Code 是很好的选择。"与 Cline 的简洁相比，Kilo Code 提供了更丰富的功能集和更深的定制能力；与 Cursor 的闭源锁定相比，Kilo Code 的 MIT 许可证和完全透明的代码库让开发者对安全和隐私拥有完全控制。这种"站在巨人肩膀上"的策略使其在开源 AI 编程工具生态中快速占据了一席之地。

---

## 应用场景

### 个人开发者的日常编程加速

对于个人开发者，Kilo Code 可作为 VS Code 或 JetBrains 中的智能编程伙伴，显著提升编码效率。通过自然语言描述需求，AI 代理可自动完成代码编写、重构、调试等任务。支持任务中途切换模型的能力，使得开发者可以根据成本和效果灵活选择——简单补全使用廉价模型，复杂推理使用前沿模型。Reddit 社区有用户表示："我现在使用 VS Code + Kilo Code 扩展，体验非常好，它基本上是 Cline/Roo Code 的增强版，免费使用且可以接入任何 LLM。"

### 团队协作与 AI 代码审查

Kilo Code 提供的 AI 代码审查功能可自动在 pull request 上执行代码质量检查，为团队提供即时的代码反馈。AGENTS.md 标准化配置文件确保团队所有成员的 AI 代理遵循统一的编码规范和项目约束，形成一致的代码风格。团队成员还可以通过 Slack 集成（Kilo 的 Viktor 助手）在沟通工具中直接调用 AI 能力，将 AI 辅助编程无缝融入现有的协作工作流。

### CI/CD 自动化与自主编程

`kilo run --auto` 自主模式使 Kilo Code 可在 CI/CD 流水线中无人值守运行，自动处理代码生成、测试修复、重构等任务。这一功能面向希望将 AI 编程能力集成到自动化流程中的工程团队，代表了 AI 编程从"交互式辅助"向"自主执行"的关键跨越。结合云端代理部署能力，团队可以在无需 SSH、Docker 或 YAML 配置的情况下快速部署 24/7 运行的 AI 代理。

### 多模型策略的成本优化

对于需要控制 AI 成本的企业团队，Kilo Code 的 Auto Model 路由功能和 500+ 模型选择提供了精细化成本控制能力。团队可以根据不同任务类型配置不同的模型策略——例如日常补全使用开源模型，复杂架构设计使用 Claude Opus，快速原型使用 GPT-5.5——从而在效果和成本之间取得最优平衡。零加价的计费模式确保企业不会为中间商利润买单。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| GitHub Stars | 23,360 |
| GitHub Forks | 2,742 |
| 今日新增 Stars | 513（趋势榜数据）|
| 主要语言 | TypeScript |
| 许可证 | MIT |
| 创建时间 | 2025-03-10 |
| 总提交数 | 23,064 |
| 发布版本数 | 430 |
| 融资情况 | 800 万美元种子轮（2025 年 12 月）|
| 用户规模 | 超 300 万开发者 |
| Token 处理量 | 超 30 万亿 |
| OpenRouter 排名 | #1 |

---

## 总结

Kilo Code 是 2025-2026 年开源 AI 编程工具领域最引人注目的项目之一。凭借 GitLab 联合创始人的行业背书、坚定的模型无关开放策略、编排器与并行代理的工程创新，以及对 Cline/Roo Code 生态的成功继承与增强，它在短短 15 个月内便成长为拥有 2.3 万 Stars、300 万用户的开源编程代理标杆。在 Cursor 闭源锁定与 Claude Code 模型绑定的竞争格局中，Kilo Code 以 MIT 开源、零加价计费、500+ 模型自由的差异化策略开辟了一条独特的道路——虽然其社区支持模式和定价体系仍有改进空间，但对于重视透明度、可定制性和成本控制的开发者而言，Kilo Code 无疑是当前最值得关注的 AI 编程工具之一。

---

*数据来源：GitHub 仓库 (Kilo-Org/kilocode)，2026 年 6 月访问*

# Awesome Claude Code 项目分析

> **Claude Code 生态系统的" Awesome 清单"** -- 精心策划的 Claude Code 技能、钩子、斜杠命令、Agent 编排器、应用和插件资源合集，是探索 Claude Code 增强工具链的终极导航站。

- **GitHub**: [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)
- **语言**: Python（自动化脚本）/ Markdown
- **Stars**: 21,993
- **Forks**: 1,244
- **许可证**: Creative Commons CC BY-NC-ND 4.0（署名-非商业性使用-禁止演绎）
- **作者**: hesreallyhim

---

## 基本信息

| 项目 | 详情 |
| --- | --- |
| **项目名称** | awesome-claude-code |
| **GitHub 地址** | https://github.com/hesreallyhim/awesome-claude-code |
| **项目定位** | A curated list of awesome skills, hooks, slash-commands, agent orchestrators, applications, and plugins for Claude Code by Anthropic |
| **Stars** | 21,993（Claude Code 生态中最受关注的 Awesome List） |
| **Forks** | 1,244 |
| **Watchers** | 199 |
| **Open Issues** | 86 |
| **许可证** | CC BY-NC-ND 4.0（允许复制和再分发，但不允许修改版本或商业使用） |
| **主要语言** | Python（自动化脚本）/ Markdown |
| **创建时间** | 2025-04-19 |
| **最近更新** | 2026-01-27 |
| **创建者** | hesreallyhim |
| **仓库大小** | 17,023 KB |
| **Topics 标签** | agent-skills, agentic-coding, ai-workflows, anthropic, awesome-list, claude, claude-code, coding-agent, llm 等 |
| **特色功能** | 滚动展示精选项目、自动推荐系统、Star 增长图表 |

---

## 解决什么问题

Claude Code 自发布以来，围绕它迅速涌现了大量的社区工具、插件和工作流增强方案，但这些资源散落在 GitHub 各处，开发者面临以下痛点：

1. **资源分散，发现困难**：Claude Code 的生态工具分布在数百个独立仓库中，从技能（Skills）、钩子（Hooks）、斜杠命令（Slash Commands）到 Agent 编排器，没有统一的索引，新用户难以找到适合自己需求的工具。

2. **质量参差不齐**：社区贡献的资源质量差异巨大，有的经过生产验证、文档齐全，有的则只是一次性实验。缺乏筛选机制，用户需要逐一试用才能判断价值。

3. **分类体系缺失**：Claude Code 的扩展机制涵盖 Skills、Hooks、Slash Commands、CLAUDE.md、Status Lines、Orchestrators 等多个维度，但没有统一的分类标准，用户难以按需求快速定位。

4. **信息更新滞后**：Claude Code 功能迭代极快，每周都有新的社区项目出现，旧的项目也可能停止维护。静态博客文章或教程很容易过时。

5. **新人入门门槛高**：刚接触 Claude Code 的开发者不了解生态系统的全貌，不知道有哪些增强手段可用，也不知道最佳实践是什么。

**awesome-claude-code** 通过一个精心策划、持续更新、分类清晰的高质量资源清单来解决这些问题，堪称 Claude Code 生态的"黄页"。

---

## 核心功能

### 1. 十大分类体系

项目将 Claude Code 生态资源分为十大类别，覆盖了从底层扩展到上层应用的完整链条：

| 分类 | 图标 | 说明 | 收录项目数 |
| --- | --- | --- | --- |
| **Agent Skills（智能体技能）** | 🤖 | 模型控制的专业化配置，使 Claude Code 获得特定领域能力 | 20+ |
| **Workflows & Knowledge Guides（工作流与知识指南）** | 🧠 | 紧耦合的 Claude Code 原生资源集，覆盖 SDLC 全流程 | 30+ |
| **Tooling（工具）** | 🧰 | 基于 Claude Code 构建的完整应用程序 | 30+ |
| **Status Lines（状态栏）** | 📊 | 终端状态栏定制和增强配置 | 5+ |
| **Hooks（钩子）** | 🪝 | 在 Claude 生命周期不同节点激活命令和脚本的 API | 10+ |
| **Slash Commands（斜杠命令）** | 🔪 | 精心调优的定制化提示词，控制 Claude 执行特定任务 | 30+ |
| **CLAUDE.md Files（项目配置文件）** | 📂 | 帮助 Claude Code 理解项目的上下文指令文件范例 | 15+ |
| **Alternative Clients（替代客户端）** | 📱 | Claude Code 的替代 UI 和前端交互方式 | 4+ |
| **Official Documentation（官方文档）** | 🏛️ | Anthropic 官方文档和资源链接 | 3+ |
| **Ralph Wiggum（自主循环模式）** | - | 将 AI 编码 Agent 在自动化循环中运行直到规范满足的技术 | 6+ |

### 2. 精选资源详解

#### Agent Skills -- 让 Claude Code 获得超能力

这是清单中最核心的类别，每个收录的 Skill 都附带详细描述。代表性项目包括：

- **AgentSys** (avifenesh): 工作流自动化系统，包含插件、Agent 和技能组合，自动化任务到生产的全流程，含 PR 管理、代码清理、漂移检测和多 Agent 代码审查。
- **Trail of Bits Security Skills**: 专业安全审计技能集，包含 CodeQL 和 Semgrep 静态分析、变体分析、修复验证和差异代码审查等十余个安全领域技能。
- **Claude Scientific Skills** (K-Dense): 涵盖研究、科学、工程、分析、金融和写作的科研技能包，被评价为"GitHub 上最优秀的技能仓库之一"。
- **Superpowers** (Jesse Vincent): 软件工程核心能力包，覆盖 SDLC 大部分环节（规划、审查、测试、调试），将工程最佳实践整合为 Claude Code 可直接使用的"超能力"。
- **Fullstack Dev Skills** (jeffallan): 65 个专业技能覆盖全栈开发，9 个工作流命令集成 Jira/Confluence，创新的 `/common-ground` 命令揭示 Claude 对项目的隐藏假设。
- **Context Engineering Kit** (Vlad Goncharov): 高级上下文工程技术与模式集合，以最小 Token 开销提升 Agent 结果质量。

#### Workflows -- 端到端开发流程

收录了大量完整的工作流方案：

- **AB Method**: 规范驱动的原则性工作流，将大问题转化为聚焦的增量任务。
- **Agentic Workflow Patterns**: 来自 Anthropic 文档的 Agent 模式合集，配有 Mermaid 图和代码示例，覆盖子 Agent 编排、渐进式技能、并行工具调用、Master-Clone 架构等。
- **Claude Code Ultimate Guide**: 从入门到高级用户的完整指南，含生产就绪模板、Agent 工作流指南、测验和速查表。
- **Simone**: 不只是命令集，而是一套完整的文档、指南和流程体系来推动项目规划和执行。
- **RIPER Workflow**: 强制分离 Research、Innovate、Plan、Execute、Review 五个阶段的结构化开发工作流。

#### Tooling -- 完整工具应用

- **claude-devtools** (matt1398): 桌面应用，通过分析会话日志提供 Claude Code 会话的可观测性，包含轮次上下文数据、压缩可视化、子 Agent 执行树和自定义通知触发器。
- **Claude Squad** (smtg-ai): 终端应用，在独立工作区管理多个 Claude Code、Codex 和 Aider 实例，支持并行任务处理。
- **Container Use** (dagger): 为编码 Agent 提供开发环境，使多个 Agent 能安全独立地使用指定技术栈。
- **ccflare** / **better-ccflare**: Claude Code 使用量仪表盘，提供媲美 Tableau 的 Web UI，含全面的成本指标、Token 消耗分析。
- **VoiceMode MCP**: 为 Claude Code 带来语音对话能力，支持任何 OpenAI API 兼容的语音服务。
- **viwo-cli**: 在 Docker 容器中运行 Claude Code，使用 git worktree 作为卷挂载，支持 `--dangerously-skip-permissions` 的更安全使用。

#### Orchestrators -- Agent 编排器

- **Auto-Claude** (AndyMik90): 自主多 Agent 编码框架，集成全 SDLC，"为你规划、构建和验证软件"，含看板式 UI。
- **Ruflo** (rUv): 部署和协调多 Agent 集群的编排平台，支持自学习、自主多 Agent 集群、向量多层记忆、系统化规划和安全护栏。
- **Claude Task Master** (eyaltoledano): AI 驱动开发的任务管理系统，与 Cursor AI 无缝协作。
- **TSK** (dtormoen): Rust CLI 工具，将开发任务委托给在沙箱 Docker 环境中运行的 AI Agent，多 Agent 并行工作，返回 git 分支供人工审查。

#### Hooks -- 生命周期钩子

- **Dippy**: 使用 AST 解析自动批准安全的 Bash 命令，对破坏性操作仍提示确认，解决权限疲劳问题。
- **parry**: Claude Code 钩子的提示注入扫描器，扫描工具输入和输出中的注入攻击、密钥泄露和数据外泄。
- **TDD Guard**: 实时监控文件操作的钩子系统，阻止违反 TDD 原则的变更。
- **Britfix**: 将美国英语拼写自动转换为英国英语，智能处理代码文件（仅转换注释和文档字符串）。

### 3. 特色栏目

- **Latest Additions（最新添加）**: 每次更新在页面顶部展示最新收录的 2-3 个项目，方便回访用户快速了解新增内容。
- **Featured Claude Code Projects（精选项目滚动条）**: 使用 SVG 横幅展示精选项目。
- **Star 增长图表**: 页面底部嵌入 starchart.cc 生成的 Star 增长曲线，直观展示项目热度。

### 4. 贡献机制

项目采用自动化的推荐系统：
- 不接受直接 PR 提交资源（只有 Claude 本身被允许提交 PR）
- 用户通过 Issue 推荐新资源，自动化系统处理后续流程
- 有 CONTRIBUTING.md 和 CODE_OF_CONDUCT.md 规范

---

## 技术栈

| 组件 | 技术 |
| --- | --- |
| **清单格式** | Markdown（GitHub README） |
| **自动化脚本** | Python |
| **徽章生成** | Shields.io / 自定义 SVG |
| **Star 图表** | starchart.cc |
| **贡献系统** | GitHub Issues + 自动化处理 |
| **许可协议** | CC BY-NC-ND 4.0 |
| **托管平台** | GitHub Pages / GitHub Repository |
| **CI/CD** | GitHub Actions（自动化资源收录） |
| **项目图标** | 自定义 SVG 横幅和徽章 |

---

## 使用场景

| 场景 | 说明 | 推荐分类 |
| --- | --- | --- |
| **新用户入门** | 刚接触 Claude Code，想了解生态全貌和增强手段 | 按分类浏览全部资源 |
| **寻找特定功能** | 需要 Claude Code 执行安全审计、DevOps、科研等特定任务 | Agent Skills |
| **搭建开发工作流** | 希望构建从需求到部署的完整自动化流程 | Workflows & Knowledge Guides |
| **监控使用成本** | 追踪 Claude Code 的 Token 消耗和费用 | Tooling > Usage Monitors |
| **提升开发效率** | 通过斜杠命令快速执行常见操作 | Slash Commands |
| **配置项目规范** | 学习如何编写 CLAUDE.md 来让 Claude 更好理解项目 | CLAUDE.md Files |
| **多 Agent 协作** | 需要多个 Claude Code 实例并行工作 | Tooling > Orchestrators |
| **自动化循环** | 让 Claude Code 持续工作直到任务完成（Ralph Wiggum 模式） | Workflows > Ralph Wiggum |
| **代码安全审计** | 对代码进行安全漏洞检测和静态分析 | Agent Skills > Trail of Bits Security Skills |
| **全栈项目开发** | 需要从规划、编码到测试的完整技能包 | Agent Skills > Fullstack Dev Skills |
| **语音交互** | 希望通过语音与 Claude Code 对话 | Tooling > VoiceMode MCP |
| **Docker 隔离** | 在容器中安全运行 Claude Code | Tooling > Container Use / viwo-cli |
| **团队协作** | 多人共用 Claude Code 的配置管理 | Tooling > Config Managers |
| **学习 Claude Code 架构** | 深入理解 Claude Code 的设计原理 | Workflows > Learn Claude Code |
| **IDE 集成** | 在 VS Code / Neovim / Emacs 中使用 Claude Code | Tooling > IDE Integrations |

---

## 资源分类速查

### Agent Skills 代表性项目

| 项目 | 作者 | 核心价值 |
| --- | --- | --- |
| AgentSys | avifenesh | 工作流自动化 + PR 管理 + 多 Agent 代码审查 |
| Trail of Bits Security Skills | Trail of Bits | 专业安全审计（CodeQL/Semgrep） |
| Claude Scientific Skills | K-Dense | 科研/工程/金融/写作技能包 |
| Superpowers | Jesse Vincent | SDLC 全链路工程能力 |
| Fullstack Dev Skills | jeffallan | 65 个全栈技能 + Jira/Confluence 集成 |
| cc-devops-skills | akin-ozer | DevOps 工程师专用（IaC 代码生成） |
| Context Engineering Kit | Vlad Goncharov | 高级上下文工程（最小 Token 开销） |

### Orchestrators 代表性项目

| 项目 | 作者 | 核心价值 |
| --- | --- | --- |
| Auto-Claude | AndyMik90 | 自主多 Agent + 看板 UI + 全 SDLC |
| Claude Squad | smtg-ai | 终端多实例管理（Claude + Codex + Aider） |
| Claude Task Master | eyaltoledano | 任务管理 + Cursor AI 协作 |
| Ruflo | rUv | 多 Agent 集群 + 向量记忆 + 自学习 |
| TSK | dtormoen | Rust CLI + Docker 沙箱 + 并行 Agent |

### Usage Monitors 代表性项目

| 项目 | 作者 | 核心价值 |
| --- | --- | --- |
| ccflare / better-ccflare | snipeship / tombii | Web UI 仪表盘，全面成本分析 |
| CC Usage | ryoppippi | CLI 工具，本地日志分析 + 费用仪表盘 |
| Claudex | Kunwar Shah | 浏览器端会话历史浏览 + 全文搜索 + 本地运行 |

---

## 一句话总结

**Awesome Claude Code（21,993 Stars）是 Claude Code 生态系统中规模最大、质量最高的精选资源合集，收录了 150+ 个经过筛选的 Skills、Hooks、Slash Commands、Orchestrators、工具和 CLAUDE.md 范例，按十大类别系统化组织，并持续通过自动化机制更新，是任何 Claude Code 用户探索生态、发现工具和提升效率的必备导航站。**

---

*数据来源: [GitHub API](https://api.github.com/repos/hesreallyhim/awesome-claude-code) 及项目 README，统计截至 2026 年 4 月。*

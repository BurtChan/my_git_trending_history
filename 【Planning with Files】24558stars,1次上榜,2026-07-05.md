# Planning with Files 项目分析

## 项目名称

**Planning with Files** — 持久化文件规划系统，让 AI 编程 Agent 的计划在上下文丢失、会话清除和崩溃后依然存活

- GitHub: https://github.com/OthmanAdi/planning-with-files
- 许可证: MIT

---

## 项目概述

**Planning with Files** 是一个为 AI 编程 Agent 设计的持久化文件规划技能（Skill），灵感源自 Manus AI 的核心理念："Markdown 是我磁盘上的'工作内存'"。该项目直击当前 AI Agent 编程中最普遍的痛点——**上下文窗口是有上限的**。当对话过长、用户执行 `/clear`、或 Agent 崩溃时，之前制定的所有计划、进度和决策都会丢失，导致 Agent 从零开始，之前的工作全部白费。

项目的解决方案简洁而深刻：**将上下文窗口视为 RAM，将文件系统视为磁盘——任何重要的东西都写入磁盘。** 具体实现为经典的 3-File Pattern（三文件模式）：`task_plan.md` 跟踪阶段和进度，`findings.md` 存储研究和发现，`progress.md` 记录会话日志和测试结果。这三个文件始终存在于磁盘上，每次会话开始时通过 Hook 机制自动重新注入上下文，确保 Agent 始终知道自己"在做什么、做到哪了、下一步是什么"。

该项目由 Ahmad Othman Ammar Adi 开发，采用 SKILL.md 标准分发，兼容 60+ AI Agent（包括 Claude Code、Codex CLI、Cursor、GitHub Copilot、Gemini CLI、Kiro、OpenCode、Hermes Agent 等）。其基准测试结果令人印象深刻：在有 Skill 的情况下，30 项断言通过率高达 96.7%（29/30），而无 Skill 时仅 6.7%（2/30），盲评 A/B 对比 3/3 全胜，平均评分从 6.8/10 提升到 10.0/10。

## 核心功能

| 功能 | 说明 |
|------|------|
| 3-File Pattern（三文件模式） | task_plan.md + findings.md + progress.md 的标准化任务管理文件结构 |
| 会话恢复（Session Recovery） | 通过 `UserPromptSubmit` Hook 每次交互自动重新注入活跃计划 |
| SHA-256 哈希签名（Hash Attestation） | 对计划文件加锁，防止被篡改，Hook 检测到篡改时阻止注入 |
| 并行计划隔离（Parallel Plan Isolation） | `.planning/YYYY-MM-DD-slug/` 目录支持多会话并发，互不干扰 |
| 自治模式（Autonomous Mode） | 为强模型优化的模式，减少每次工具调用的计划重新注入开销 |
| 门控模式（Gated Mode） | 5 条件确定性完成门：仅当所有条件满足时才阻止，否则让 Agent 自由工作 |
| 运行账本（Run Ledger） | Append-only JSONL 格式替换原始 progress.md 尾部，更结构化的进度记录 |
| 停止钩子（Stop Hook） | 自动检测计划中是否有 `in_progress` 阶段，防止 Agent 过早宣布完成 |
| `/plan` 斜杠命令 | Claude Code 插件模式的完整命令集：`/plan`、`/plan:status`、`/plan-goal`、`/plan-attest` 等 |
| 多 Agent 共享状态 | 磁盘上的文件作为多个 Agent 的共享工作记忆，实现跨 Agent 的任务连续性 |
| 容错能力 | 崩溃、`/clear`、新会话后自动从磁盘恢复计划状态，无需人工干预 |

## 技术栈

| 组件 | 技术 |
|------|------|
| 分发标准 | SKILL.md（AI Agent 通用技能标准） |
| 插件模式 | Claude Code Plugin + Hooks（`UserPromptSubmit`、`Stop`） |
| 文件格式 | Markdown（计划）、JSONL（运行账本）、TOML（配置） |
| 安全机制 | SHA-256 哈希签名 + 篡改检测 |
| 会话管理 | 基于目录隔离的并行计划系统 |
| 兼容性 | 60+ AI Agent（Claude Code、Codex、Cursor、Copilot、Gemini CLI 等） |
| 安装方式 | `/plugin marketplace add`（Claude Code）、`npx skills add`（通用） |
| 基准框架 | Anthropic `skill-creator` framework（Claude Sonnet 4.6） |

## 项目亮点

### 1. 极简但极其有效的核心理念

Planning with Files 的核心思想可以用一句话概括："重要的东西不要只放在上下文里，写到磁盘上。"这个看似简单的理念解决了 AI Agent 长任务中最致命的问题——上下文丢失。项目没有引入复杂的数据库或外部状态管理服务，仅用 3 个 Markdown 文件就实现了完整的计划持久化方案。这种极简主义让它能在几乎任何 Agent 环境中运行，零依赖、零配置。

### 2. 基准测试数据极其亮眼

在 Anthropic 官方 `skill-creator` 框架下，使用 Claude Sonnet 4.6 进行的严格基准测试显示，启用该 Skill 后的通过率从 6.7% 跃升至 96.7%，平均评分从 6.8 提升到满分 10.0。盲评 A/B 对比 3/3 全胜——这意味着在不知道是否使用 Skill 的情况下，评估者一致认为使用了 Skill 的 Agent 输出质量更高。这些数据为项目的价值提供了量化证据。

### 3. 渐进式特性演进（零破坏更新）

从 v1 到 v3.2.0，项目始终坚持"opt-in, no breaking changes"的设计原则。v2 引入了哈希签名和并行隔离，v3 引入了自治模式、门控模式和运行账本——所有新特性都是可选的，老用户的 3-File Pattern 工作流完全不受影响。这种设计哲学在 AI Agent 工具生态中非常难得，确保了项目的长期可维护性。

### 4. SKILL.md 标准的典范实现

Planning with Files 是 SKILL.md 标准最成功的实践案例之一。它展示了 SKILL.md 标准的真正价值——一次编写，60+ Agent 通用。通过统一的 Hook 机制和文件接口，同一个 Skill 可以在 Claude Code、Codex CLI、Cursor、GitHub Copilot、Gemini CLI、Hermes Agent 等完全不同的环境中工作，无需为每个 Agent 单独适配。

## 应用场景

### 大规模代码重构

当需要对一个大型代码库进行跨文件、跨模块的重构时，AI Agent 需要在数百次工具调用中保持对整体重构计划的一致理解。Planning with Files 确保每次上下文刷新后，Agent 仍能准确知道重构的当前阶段、已完成步骤和剩余任务，避免重复工作或遗漏步骤。

### 多 Agent 协作编程

多个 Agent（如一个负责前端、一个负责后端、一个负责测试）通过共享磁盘上的计划文件实现状态同步。每个 Agent 在开始工作时读取最新计划，完成后更新进度，形成一种轻量级但有效的跨 Agent 协调机制，无需复杂的消息队列或 RPC 调用。

### 长时间运行的任务

对于需要持续数小时甚至数天的 Agent 任务（如完整的项目生成、大规模文档编写、自动化测试套件构建），Planning with Files 的持久化机制是不可或缺的保障。无论是因为 API 限速、网络中断还是用户手动清理上下文，任务都能从上次停止的地方继续。

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 24,558 |
| 🍴 Forks | 2,104 |
| 📅 创建时间 | 2026-01-03 |
| 📝 今日新增 | 61 stars today |
| 🖥️ 主要语言 | Python |
| 📄 许可证 | MIT |
| 🏷️ 标签 | agent-skills, agentic-ai, claude-code, coding-agent, multi-agent-systems 等 20+ |

## 总结

Planning with Files 是 AI Agent 工程化领域的一颗明珠——它用最简单的方法（3 个 Markdown 文件）解决了最核心的问题（上下文丢失），并以量化数据证明了自己的价值（96.7% 通过率 vs 6.7%）。作为 SKILL.md 标准的标杆实现，它展示了"一次编写、60+ Agent 通用"的愿景如何变为现实。对于任何在日常工作中使用 AI 编程 Agent 的开发者，这是一个几乎零成本、收益巨大的必备技能。

---

*数据来源：GitHub 仓库 (OthmanAdi/planning-with-files)，2026 年 7 月访问*

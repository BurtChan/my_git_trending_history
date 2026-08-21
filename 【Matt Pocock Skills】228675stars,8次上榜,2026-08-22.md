# Matt Pocock Skills 项目分析

## 项目名称

**Matt Pocock Skills** — 面向真实工程师的 AI 编码技能集，修复 AI 代码生成的常见问题

- **GitHub**: [mattpocock/skills](https://github.com/mattpocock/skills)
- **许可证**: MIT

---

## 项目概述

Matt Pocock Skills 是由知名 TypeScript 教育者 Matt Pocock（拥有 60,000+ 订阅者）开源的 AI Agent 技能集合。该项目包含 20+ 个精心设计的技能（Skills），旨在解决 AI 编码助手（如 Claude Code、GitHub Copilot 等）在实际工程中的常见失败模式。

项目核心理念是将**数十年软件工程经验**编码为结构化的技能文件（SKILL.md），让 AI Agent 按照经过验证的工程最佳实践工作，而非盲目生成代码。每个技能都是**小型、可组合、易于适配**的，覆盖从需求对齐、测试驱动开发、调试到架构改进的全流程。

项目凭借高质量的内容和 Matt Pocock 在 TypeScript 社区的影响力，迅速获得了 84,000+ Stars，成为 AI 编码技能领域最受欢迎的开源项目之一。技能通过 `npx skills@latest add mattpocock/skills` 一键安装，支持 Claude Code、Codex、OpenCode 等主流 AI 编码工具。

---

## 核心功能

### 工程技能（Engineering）

| 技能 | 功能描述 |
|------|----------|
| `/grill-with-docs` | 需求对齐会议，挑战你的计划，更新领域文档和架构决策记录 |
| `/tdd` | 红绿重构的测试驱动开发循环，确保代码质量 |
| `/diagnose` | 结构化调试循环：复现→最小化→假设→监控→修复→回归测试 |
| `/zoom-out` | 让 Agent 俯瞰整个系统，理解代码在全局中的位置 |
| `/improve-codebase-architecture` | 发现代码库中的深化机会，提出模块化重构建议 |
| `/build` | 按垂直切片逐步构建功能或修复 Bug |
| `/prototype` | 快速构建一次性原型验证设计方案 |

### 生产力技能（Productivity）

| 技能 | 功能描述 |
|------|----------|
| `/grill-me` | 非代码场景的需求对齐，帮助理清思路 |
| `/caveman` | 压缩通信模式，减少 75% AI Token 使用量 |
| `/handoff` | 将当前对话压缩为交接文档，方便下一个 Agent 继续 |
| `/to-prd` | 将对话上下文转化为 PRD，提交为 GitHub Issue |
| `/to-issues` | 将计划拆分为可独立抓取的 GitHub Issues |
| `/triage` | 基于标签状态机的 GitHub Issue 分类管理 |

### 辅助工具

| 技能 | 功能描述 |
|------|----------|
| `/write-a-skill` | 按标准模板创建新的 Agent 技能 |
| `/setup-matt-pocock-skills` | 初始化仓库配置（Issue 跟踪器、标签、领域文档） |
| `/git-guardrails-claude-code` | 阻止危险的 Git 命令执行 |
| `/setup-pre-commit` | 配置 Husky pre-commit 钩子 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **技能格式** | SKILL.md（Markdown + YAML frontmatter） |
| **安装方式** | npx skills@latest |
| **支持 Agent** | Claude Code、Codex、OpenCode 等 |
| **配置文件** | AGENTS.md / CLAUDE.md |
| **Issue 集成** | GitHub / GitLab / 本地 Markdown |
| **文档结构** | CONTEXT.md + docs/adr/（架构决策记录） |
| **主要语言** | Shell（技能脚本） |

---

## 项目亮点

### 解决 AI 编码核心痛点
项目精准定位了 AI 编码的三大失败模式：Agent 没按要求做（用 `/grill-me` 解决）、Agent 过于冗长（用 `/caveman` 解决）、代码不工作（用 `/tdd` 和 `/diagnose` 解决）。

### 基于真实工程经验
Matt Pocock 将多年 TypeScript 咨询和教学经验凝练为这些技能，每个技能都有明确的触发条件、执行步骤和质量检查点，不是简单的 prompt。

### 高度可组合
技能之间可以自由组合，例如先用 `/grill-with-docs` 对齐需求，再用 `/tdd` 编写代码，最后用 `/handoff` 交接——形成完整的工程工作流。

### 社区影响力巨大
84k+ Stars，529 watchers，被 Medium、Substack 等平台广泛讨论，成为 AI 编码技能的标杆项目。

---

## 应用场景

### AI 辅助编码规范化
团队使用统一的技能集来规范 AI 编码助手的行为，确保生成的代码符合工程标准，减少 "vibe coding" 的随意性。

### 测试驱动开发
使用 `/tdd` 技能让 AI Agent 严格遵循红绿重构循环，先写测试再写实现，提高代码质量。

### 复杂 Bug 诊断
使用 `/diagnose` 技能为 AI Agent 提供结构化的调试方法论，避免 AI 盲目猜测和无效修改。

### 项目交接和知识传递
使用 `/handoff` 和 `/grill-with-docs` 创建结构化的项目文档，让不同的 AI Agent 会话之间能无缝传递上下文。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 228,675 |
| **总 Forks** | 19,565 |
| **今日新增 Stars** | 1,239 |
| **许可证** | MIT |
| **主要语言** | Shell |
| **Watchers** | 529 |

---

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 6 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单（1,695 stars today）

**最新动态**：
- Matt Pocock Skills 在 2026 年 5 月首次分析时约 84K Stars，如今已飙升至 206K+，三个月内增长超 12 万，成为 AI 编码技能领域增长最迅猛的项目之一
- 作为 TypeScript 社区知名教育者 Matt Pocock 的工程技能库，项目持续扩充覆盖需求对齐、TDD、调试、架构改进等全流程的实战技能
- 技能生态全面爆发背景下，该项目与 addyosmani/agent-skills、obra/superpowers 等一起成为 AI 编码代理技能规范的主要来源

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 84,006 | 206,077 | +122,071 |
| 总 Forks | 7,283 | 17,796 | +10,513 |

**核心变化概要**：
1. Star 数从 84,006 增长至 206,077（+122,071），三个月翻倍有余
2. Forks 从 7,283 增至 17,796（+10,513），社区二次开发与传播显著加速
3. 技能库持续成为主流 AI 编码工具（Claude Code、Codex 等）的工程实践标准




### 更新 2 — 2026 年 8 月 7 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单（2,002 stars today）

**最新动态**：
- Matt Pocock Skills 连续第二日登上 Trending，Star 数从 206,077 增长至 206,879（+802），稳居 20 万 Star 俱乐部
- 项目由 TypeScript 教育家 Matt Pocock 开源其个人 `.agents` 目录中的实战技能集，覆盖规格驱动开发、代码审查、测试策略等真实工程场景，被开发者视为「来自一线工程师」的技能库标杆
- 社区持续将其技能套件移植到 Claude Code、Codex、Cursor 等主流 AI 编码工具，生态影响力不断扩大

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 206,077 | 206,879 | +802 |
| 总 Forks | 17,796 | 17,867 | +71 |

**核心变化概要**：
1. Star 数从 206,077 增长至 206,879（+802），连续两日上榜
2. Fork 数从 17,796 增至 17,867（+71），技能库复用与二次开发活跃
3. 今日新增 2,002 stars，20 万 Star 体量下仍保持高速增长

---

### 更新 3 — 2026 年 8 月 8 日（再次登上 Trending）
**更新原因**：Matt Pocock Skills 连续第三日登上 Trending，Star 数从 206,879 增长至 208,583（+1,704），正式突破 208K

**最新动态**：Matt Pocock Skills 连续第三日登榜，Star 总数突破 208K，保持 AI 编码技能领域头部位置。项目已从「Matt Pocock 个人 .agents 目录」进化为成熟分发体系：通过 Claude Code 官方 marketplace 一键安装（`claude plugins install mattpocock-skills`），更新自动推送，订阅而非 fork 的哲学与 skills.sh 的可编辑副本形成互补。420 commits 的迭代节奏稳定，技能集合强调「小而可组合、适配任何模型」，与 GSD、BMAD、Spec-Kit 等接管整个流程的框架形成差异化——用户保留控制权，bug 也更易定位。newsletter 订阅者已达约 60,000 人，社区传播持续放大。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 206,879 | 208,583 | +1,704 |
| 总 Forks | 17,867 | 18,000 | +133 |

**核心变化概要**：
- Star 总数突破 208K，连续三日登榜，日增超 1,700
- Claude Code marketplace 官方插件分发 + skills.sh 可编辑副本双路径
- 420 commits 稳定迭代，技能库持续扩充
- newsletter 订阅者约 6 万，社区影响力持续放大


### 更新 4 — 2026 年 8 月 9 日（再次登上 Trending）
**更新原因**：Matt Pocock Skills 再次登上 GitHub Trending，Star 数从 208,583 增长至 209,807（+1,224），连续多日稳居榜单。

**最新动态**：Matt Pocock 于 8 月 5 日发布 Skills v1.2.0，带来多项新技能与工具集成：新增 `/wait-what`（让 Agent 用大白话复述）、`/writing-for-agents`（面向 Agent 的写作规范）等技能，并正式支持 Claude Code Plugin 集成；同期还上线了 `/wizard`（生成引导用户完成设置的脚本）与 `/to-questionnaire`（把开放问题转成待填文档）两个新技能。v1.1 时代的 `/wayfinder`、`/to-spec`、`/to-tickets` 等规划类技能持续被社区引用，技能库已成长为 AI 编码工作流中「工程纪律」的代表性开源资产。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 208,583 | 209,807 | +1,224 |
| 总 Forks | 18,000 | 18,132 | +132 |

**核心变化概要**：
- v1.2.0 发布：新增 /wait-what、/writing-for-agents，支持 Claude Code Plugin
- 新增 /wizard、/to-questionnaire 技能，覆盖更多开发场景
- Star 逼近 21 万，连续多日占据 Trending
- 技能库从「提示词集合」演变为受治理的工程控制组件

---

---

### 更新 5 — 2026 年 8 月 20 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
- 持续作为 AI 编码技能与 Agent 工作流的高热度入口，社区关注度显著上升。
- 技能目录持续覆盖工程实践、代码审查与协作流程，适配多种编码 Agent。
- 本次 Stars 增长超过 1.3 万，显示该类可复用 Agent 技能资产仍在快速扩散。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 209,807 | 223,181 | +13,374 |
| 总 Forks | 18,132 | 19,212 | +1,080 |

**核心变化概要**：
1. 持续作为 AI 编码技能与 Agent 工作流的高热度入口，社区关注度显著上升。
2. 技能目录持续覆盖工程实践、代码审查与协作流程，适配多种编码 Agent。
3. 本次 Stars 增长超过 1.3 万，显示该类可复用 Agent 技能资产仍在快速扩散。

---

### 更新 6 — 2026 年 8 月 21 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
- Skills for Real Engineers 持续扩散：技能按「用户调用 / 模型调用」双模式组织，/grill-me、/to-prd、/diagnosing-bugs、tdd、domain-modeling 等技能已成为社区广泛引用的工程实践范本。
- GitHub Discussions 开放后社区活跃度进一步提升，大量开发者分享技能定制与 Agent 工作流集成经验。
- 今日单日新增 2,192 Stars，总星数突破 22.7 万，稳居 Agent Skills 赛道热度第一梯队。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 223,181 | 227,436 | +4,255 |
| 总 Forks | 19,212 | 19,477 | +265 |

**核心变化概要**：
1. 技能目录按用户调用/模型调用双模式重组，README 结构化程度大幅提升
2. Discussions 开放，社区围绕 Agent 工作流的讨论持续升温
3. 单日 +2,192 Stars，Agent Skills 作为可复用资产的地位进一步巩固
---

### 更新 7 — 2026 年 8 月 22 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：

- Skills for Real Engineers 热度持续发酵：连续多日上榜，总星数突破 22.8 万，稳居 Agent Skills 赛道榜首位置。
- 技能目录按「用户调用 / 模型调用」双模式组织，/grill-me、tdd、domain-modeling 等已成为社区广泛引用的工程实践范本，GitHub Discussions 中技能定制与工作流集成讨论活跃。
- 今日 Trending 页面显示单日新增 3,368 Stars（页面快照口径），API 实测 24 小时净增 1,239 Stars，20 万体量下仍保持高增长动能。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 227,436 | 228,675 | +1,239 |
| 总 Forks | 19,477 | 19,565 | +88 |

**核心变化概要**：

1. 总星数从 227,436 增至 228,675（+1,239），第 8 次登上 Trending
2. Fork 数增至 19,565，技能复用与二次开发保持活跃
3. Agent Skills 作为可复用工程资产的地位进一步巩固
---

## 总结

Matt Pocock Skills 是**AI 编码技能领域的标杆项目**，84k+ Stars。它由 TypeScript 社区知名教育者 Matt Pocock 创建，包含 20+ 个精心设计的技能，覆盖需求对齐、测试驱动开发、调试、架构改进等全流程，旨在将 AI 编码助手从 "vibe coding" 提升为真正的工程实践。技能可通过 npx 一键安装，支持主流 AI 编码工具。

---

*数据来源：GitHub 仓库 (mattpocock/skills)、ExplainX（2026 年 5 月访问）*

---

*数据来源：GitHub 仓库 (mattpocock/skills)，2026 年 8 月访问*
*首次分析：2026 年 5 月 | 最近更新：2026 年 8 月 22 日*

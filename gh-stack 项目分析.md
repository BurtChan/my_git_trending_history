# gh-stack 项目分析

## 项目名称
**gh-stack** — GitHub 官方 Stacked PR CLI 扩展，管理链式分支和拉取请求
- **GitHub**: [github/gh-stack](https://github.com/github/gh-stack)
- **许可证**: MIT

---

## 项目概述
GitHub 官方开发的 `gh` CLI 扩展，用于管理 Stacked PR（堆叠拉取请求）。Stacked PR 是一种将大型变更拆分为一系列小型、可独立审查的 PR 的工作流，每个 PR 建立在下一个之上，形成链式结构。该工具目前处于私有预览阶段，需要注册候补名单。

gh-stack 提供了完整的分支栈管理能力，包括初始化栈、添加新分支、级联 rebase、冲突解决、栈内导航等功能。它将栈元数据存储在 `.git/gh-stack` 中（不提交到仓库），并自动启用 `git rerere` 进行冲突解决记忆。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| `stack init` | 初始化新的分支栈，支持交互式和非交互式模式 |
| `stack add` | 在栈顶添加新分支，支持自动提交和命名 |
| `stack checkout` | 按栈编号、PR 编号或分支名导航 |
| `stack rebase` | 级联 rebase 整个栈，支持上下栈方向和中断恢复 |
| `stack modify` | 修改栈内分支属性 |
| AI Agent 集成 | 通过 `gh skill install` 安装，支持 AI 编码助手操作 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | Go |
| 平台 | GitHub CLI (`gh`) v2.0+ |
| 存储 | `.git/gh-stack` (本地 JSON) |
| 冲突解决 | `git rerere` |
| 许可证 | MIT |

---

## 项目亮点

### GitHub 官方出品
由 GitHub 团队直接开发维护，是与 Git 工作流深度集成的官方解决方案，代表了 GitHub 对 Stacked PR 工作流的官方支持方向。

### 级联 Rebase 引擎
支持 trunk-upward 的级联 rebase，当底层 PR 被合并时自动切换到 `--onto` 模式，大幅简化了多分支并行开发的复杂度。

### AI Agent 原生集成
通过 `gh skill install github/gh-stack` 安装为 AI 编码助手的技能，让 Claude Code 等 AI Agent 能够直接操作分支栈，是 AI 辅助开发流程的重要组成部分。

### 智能冲突处理
自动启用 `git rerere` 记住冲突解决方案，遇到重复冲突时自动应用历史解决方案，配合 `--continue`/`--abort` 提供完整的中断恢复机制。

---

## 应用场景

### 大型功能开发
当需要开发一个涉及多个模块的大型功能时，使用 Stacked PR 可以将变更拆分为逻辑独立的小 PR，方便团队逐层审查。

### AI 编码助手协作
结合 Claude Code 等 AI Agent 使用，AI 可以自动创建和管理分支栈，实现复杂功能的自动分解和逐步提交。

### 代码审查流程优化
审查者只需关注每个 PR 的增量变更，而非一个巨大的 diff，显著提高代码审查效率和质量。

### 持续集成友好
栈内的每个 PR 可以独立运行 CI，确保每一层变更都通过测试，避免集成问题积累。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 696 |
| 🍴 Forks | 32 |
| 📝 语言 | Go |
| 📅 创建时间 | 2026-02-06 |

---

## 总结
GitHub 官方的 Stacked PR CLI 工具，为大型变更的分层审查提供了原生支持，其 AI Agent 集成能力标志着 Git 工作流与 AI 辅助开发的深度融合，是现代代码协作流程的重要基础设施。

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 2 日（再次登上 Trending）

**更新原因**：项目再次登上 GitHub Trending 榜单，Star 持续增长

**最新动态**：GitHub 官方的 Stacked PR CLI 扩展持续获得社区关注，支持 `gh skill install` AI Agent 集成安装方式。工具提供完整的栈管理命令集（init、add、checkout、rebase、modify、sync、submit），其中 `stack modify` 提供交互式 TUI 进行栈重构（支持插入/删除/折叠/重排序分支），`stack sync` 实现一键 fetch→rebase→push→PR 同步全流程。目前仍处于私有预览阶段，需注册候补名单。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 696 | 769 | +73 |
| 总 Forks | 32 | 35 | +3 |

---

*数据来源：GitHub 仓库 (github/gh-stack)，2026 年 08 月访问*
*首次分析：2026 年 08 月*

# Superpowers 项目分析

> **一句话总结** -- 给 AI 编程 Agent 装上"超能力"的技能框架与开发方法论，让 Claude Code、Cursor 等 Agent 自动遵循 TDD、系统化调试、子 Agent 驱动开发的完整工作流。

- **GitHub**: [obra/superpowers](https://github.com/obra/superpowers)
- **语言**: Shell（技能描述文件，Markdown / YAML）
- **Stars**: 267,109 | **今日新增**: 931
- **Forks**: 23,868
- **作者**: @obra（Jesse Vincent），Prime Radiant 团队
- **许可证**: MIT

---

## 解决什么问题

当前 AI 编程 Agent（Claude Code、Cursor、Codex 等）虽然代码生成能力强大，但在实际软件工程中存在系统性缺陷：

1. **缺乏方法论** -- Agent 倾向于直接跳入写代码，而不是先理解需求、设计方案
2. **不写测试** -- AI 生成的代码通常缺少测试，或者先写代码后补测试（本末倒置）
3. **缺乏规划能力** -- 大任务没有拆解，容易偏离目标、遗忘上下文
4. **无系统化调试** -- 遇到 bug 靠猜测而非根因分析
5. **缺少质量关卡** -- 没有代码审查、验证环节，无法保证交付质量

Superpowers 把经过验证的软件工程最佳实践封装成一套 **可自动触发的技能系统**，让 AI Agent 从"会写代码的工具"升级为"遵循工程规范的开发者"。

---

## 核心功能

### 基本工作流（7 步自动流水线）

| 步骤 | 技能 | 触发时机 | 做什么 |
|------|------|----------|--------|
| 1 | **brainstorming** | 写代码之前 | 苏格拉底式提问，提炼需求，分段展示设计文档供确认 |
| 2 | **using-git-worktrees** | 设计确认后 | 创建隔离的 git worktree 工作空间，验证测试基线 |
| 3 | **writing-plans** | 设计通过后 | 拆解为 2-5 分钟的小任务，每个任务含精确文件路径、完整代码、验证步骤 |
| 4 | **subagent-driven-development** | 计划就绪后 | 为每个任务派发独立子 Agent，双阶段审查（规格合规 + 代码质量） |
| 5 | **test-driven-development** | 实现阶段 | 强制 RED-GREEN-REFACTOR 循环：先写失败测试，再写最小代码，测试通过后提交 |
| 6 | **requesting-code-review** | 任务之间 | 对照计划审查代码，按严重程度报告问题，关键问题阻断进度 |
| 7 | **finishing-a-development-branch** | 任务完成 | 验证测试，提供合并/PR/保留/丢弃选项，清理 worktree |

> 所有技能在 Agent 执行任何任务前自动检查并触发，是**强制工作流**而非建议。

### 技能库一览

**测试类**:
- `test-driven-development` -- RED-GREEN-REFACTOR 循环，含测试反模式参考

**调试类**:
- `systematic-debugging` -- 4 阶段根因分析（含根因追踪、纵深防御、条件等待技术）
- `verification-before-completion` -- 确认问题真正修复

**协作类**:
- `brainstorming` -- 苏格拉底式设计精炼
- `writing-plans` -- 详细实现计划
- `executing-plans` -- 带人工检查点的批量执行
- `dispatching-parallel-agents` -- 并发子 Agent 工作流
- `requesting-code-review` / `receiving-code-review` -- 代码审查与反馈响应
- `using-git-worktrees` -- 并行开发分支
- `finishing-a-development-branch` -- 合并/PR 决策
- `subagent-driven-development` -- 双阶段审查的快速迭代

**元技能**:
- `writing-skills` -- 创建新技能的最佳实践指南（含测试方法论）
- `using-superpowers` -- 技能系统入门

---

## 技术栈

| 维度 | 说明 |
|------|------|
| **核心格式** | Markdown / YAML 技能描述文件（Shell 脚本辅助） |
| **集成方式** | 各平台插件系统（Plugin Marketplace / Extensions） |
| **支持平台** | Claude Code、Cursor、Codex、OpenCode、GitHub Copilot CLI、Gemini CLI |
| **安装方式** | 插件市场一键安装或手动 fetch 安装脚本 |
| **版本管理** | 通过 `/plugin update superpowers` 自动更新 |

---

## 设计哲学

项目明确宣示四大原则：

1. **测试驱动开发** -- 永远先写测试
2. **系统化优于临时应对** -- 流程优于猜测
3. **降低复杂度** -- 简洁是首要目标（YAGNI、DRY）
4. **证据优于声明** -- 验证后再宣布成功

关键设计思想：把实现计划写得"清晰到连一个充满热情但缺乏判断力、没有项目背景、讨厌测试的初级工程师都能跟上"。这实质上是为 LLM Agent 量身定制的工作流。

---

## 使用场景

| 场景 | 说明 |
|------|------|
| **AI 自主开发** | 让 Claude 等自主工作数小时而不偏离计划，Claude 可连续自主工作 2 小时以上 |
| **大型功能开发** | 复杂需求自动拆解为小任务，子 Agent 逐个执行并审查 |
| **团队 AI 协作** | 并行派发多个子 Agent，各自在独立 worktree 中工作 |
| **严格 TDD 项目** | 强制先测试后实现，删除先写代码后补测试的做法 |
| **系统化调试** | 遇到 bug 不靠猜测，走 4 阶段根因分析流程 |
| **代码质量保障** | 自动代码审查，关键问题阻断，确保交付质量 |
| **多平台 Agent 增强** | 一套技能框架同时增强 Claude Code、Cursor、Codex、Gemini 等 6 种 AI 编程工具 |

---

## 快速安装

```bash
# Claude Code 官方市场（推荐）
/plugin install superpowers@claude-plugins-official

# Claude Code 第三方市场
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace

# Cursor -- 在 Agent chat 中搜索 "superpowers" 安装

# Gemini CLI
gemini extensions install https://github.com/obra/superpowers
gemini extensions update superpowers

# GitHub Copilot CLI
copilot plugin marketplace add obra/superpowers-marketplace
copilot plugin install superpowers@superpowers-marketplace

# Codex
# 告诉 Codex: Fetch and follow instructions from
# https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md

# 更新
/plugin update superpowers
```

---

## 项目生态

- **作者**: Jesse Vincent，Perl 社区知名开发者，Request Tracker (RT) 和 Perl 6/MojoMojo 的创建者
- **团队**: Prime Radiant
- **社区**: Discord 社区支持，GitHub Issues，Release 邮件通知
- **贡献方式**: Fork 仓库，按 `writing-skills` 技能规范创建新技能，提交 PR

---

---

## 📋 更新记录

### 更新 3 — 2026 年 8 月 6 日（再次登上 Trending）
**更新原因**：Superpowers 持续登 Trending，Star 数从 266,347 增长至 267,109（+762），日增 931 Star

**最新动态**：Superpowers 连续三日登上 Trending，Star 总数突破 267K，稳居 GitHub 全球排名前列。作为最大的 Agentic Skills 框架，其「Brainstorm → Spec → Subagent-Driven Development → Review」方法论已成为 AI 编程 Agent 生态的事实标准之一。v6.1.1 的 autoresearch loop 优化持续发酵，token 消耗降 50%、时间降 60% 的效率优势在开发者社区中口碑扩散。项目对 Claude Code、Codex、Kimi、Gemini 等多 Agent 的原生插件支持，使其生态位从「Claude Code 专属技能」扩展为「跨 Agent 工程方法论」。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 266,347 | 267,109 | +762 |
| 总 Forks | 23,814 | 23,868 | +54 |

**核心变化概要**：
- Star 总数突破 267K，全球排名稳定在前列，连续 3 日 Trending
- autoresearch loop（v6.1.1）效率优势持续传播，token 消耗降 50%、时间降 60%
- 跨 Agent 原生插件（Claude Code/Codex/Kimi/Cursor）巩固方法论标准地位

---




### 更新 1 — 2026 年 8 月 4 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单（617 stars today）

**最新动态**：
- 项目自 4 月首次分析以来 Star 数从 140K 增长至 266K，翻近一倍，成为 AI Agent 技能框架领域的绝对标杆
- 技能框架持续扩展，支持 Claude Code、Cursor、Codex、Gemini 等主流 AI 编程客户端
- 在 Trending 榜单持续活跃，多次登上每日榜单

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 140,618 | 266,088 | +125,470 |
| 总 Forks | 21,891 | 23,791 | +1,900 |

**核心变化概要**：
1. 项目自 4 月首次分析以来 Star 数从 140K 增长至 266K，翻近一倍，成为 AI Agent 技能框架领域的绝对标杆
1. 技能框架持续扩展，支持 Claude Code、Cursor、Codex、Gemini 等主流 AI 编程客户端
1. 在 Trending 榜单持续活跃，多次登上每日榜单



---

### 更新 2 — 2026 年 8 月 5 日（再次登上 Trending）
**更新原因**：Superpowers 持续登 Trending，全球 Star 排名第 14，日增 617 Star

**最新动态**：Superpowers 由 Jesse Vincent（Prime Radiant）创建，已从 2025 年 10 月的个人生产力实验成长为 GitHub 全球排名第 14 的开源项目（266K+ Stars）。作为最大的 Agentic Skills 框架，Superpowers 提供完整的软件开发生命周期方法论：Brainstorm → Spec → Subagent-Driven Development → Review。v6.1.1 于 2026 年 7 月发布，引入 autoresearch loop 自动优化构建参数，token 消耗降低 50%，wall-clock 时间减少 60%。项目已适配 Claude Code、Codex、Kimi、Gemini 等多个 AI 编码代理。新增 .claude-plugin、.codex-plugin、.kimi-plugin 和 .cursor-plugin 目录，实现跨 IDE/代理的原生插件支持。680 commits 的活跃开发节奏显示持续迭代。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 266,088 | 266,347 | +259 |
| 总 Forks | 23,786 | 23,814 | +28 |

**核心变化概要**：
- GitHub 全球排名第 14（266K+ Stars），成为最大的 Agentic Skills 框架
- v6.1.1 引入 autoresearch loop，token 消耗降 50%，时间降 60%
- 新增 Claude Code、Codex、Kimi、Cursor 原生插件支持
- 14-skill 方法论覆盖完整软件开发生命周期
- Discord 社区和发布通知系统建立，开发者生态完善

> 更新依据：GitHub Trending 2026-08-05 数据，Star 数由 GitHub API 实时获取
## 一句话总结

> Superpowers 是一个 **140k+ Stars 的 AI Agent 技能框架与软件开发方法论**，由 Jesse Vincent 和 Prime Radiant 团队创建，通过可自动触发的技能系统（头脑风暴、TDD、子 Agent 驱动开发、系统化调试、代码审查等），让 Claude Code、Cursor、Codex、Gemini 等 AI 编程 Agent 自动遵循严格的软件工程流程，实现从需求分析到代码交付的全流程质量保障。今日新增 1,926 Stars，是当前 AI 编程工具生态中最热门的 Agent 增强框架之一。

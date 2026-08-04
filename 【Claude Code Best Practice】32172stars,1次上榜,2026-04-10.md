# Claude Code Best Practice 项目分析

> **Claude Code 最佳实践的百科全书** — 社区驱动的 Claude Code 使用指南，涵盖概念、工作流、69 条技巧、编排模式与社区生态，是 Claude Code 用户必读的知识库。

- **项目名称**: Claude Code Best Practice
- **GitHub**: [shanraisshan/claude-code-best-practice](https://github.com/shanraisshan/claude-code-best-practice)
- **Stars**: 32,172 | **Forks**: 2,945
- **许可证**: MIT
- **语言**: HTML / Markdown（知识库项目）
- **作者**: shanraisshan（Claude Community Ambassador, Claude Certified Architect）
- **创建时间**: 2025-10-31
- **Slogan**: Practice makes Claude perfect

---

## 解决什么问题

Claude Code 作为 Anthropic 官方 CLI 编程工具，功能迭代极快（从 v1 到 v2.1.x 短短数月内新增大量特性），但官方文档往往滞后于实际功能。同时，社区中大量来自 Boris Cherny（Claude Code 创始人）、Thariq 等核心团队成员的最佳实践散落在 Twitter/X 推文、播客和博客中，缺乏系统整理。

本项目解决了以下痛点：

1. **概念碎片化** — Agent、Command、Skill、Hook、Workflow 等概念定义模糊，用户不知道何时用哪个
2. **最佳实践分散** — 核心团队的技巧散落在各处推文和文章中，难以系统学习
3. **开发工作流选型困难** — 社区涌现出数十种 Claude Code 开发工作流（如 Superpowers、BMAD-METHOD、oh-my-claudecode 等），缺乏横向对比
4. **新功能追踪困难** — Power-ups、Ultraplan、Claude Code Web、Computer Use 等 beta 功能更新频繁

---

## 核心内容

### 1. 概念体系（CONCEPTS）

系统梳理 Claude Code 的所有核心概念，每个概念标注了 "Best Practice" 和 "Implemented" 状态：

| 概念 | 位置 | 说明 |
|------|------|------|
| **Subagents** | `.claude/agents/<name>.md` | 在全新隔离上下文中运行的自主执行者，拥有独立工具、权限、模型和持久身份 |
| **Commands** | `.claude/commands/<name>.md` | 注入现有上下文的知识——用户通过斜杠命令调用的简单提示模板 |
| **Skills** | `.claude/skills/<name>/SKILL.md` | 注入现有上下文的知识——可配置、可预加载、可自动发现，支持上下文分叉和渐进式披露 |
| **Workflows** | `.claude/commands/weather-orchestrator.md` | Command -> Agent -> Skill 编排模式的实现 |
| **Hooks** | `.claude/hooks/` | 在 Agent 循环之外运行的用户定义处理器（脚本、HTTP、提示），响应特定事件 |
| **MCP Servers** | `.claude/settings.json` / `.mcp.json` | Model Context Protocol 连接外部工具、数据库和 API |
| **Plugins** | 可分发包 | 技能、子 Agent、Hook、MCP Server 和 LSP Server 的打包集合 |
| **Settings** | `.claude/settings.json` | 分层配置系统：权限、模型、输出样式、沙箱、快捷键、快速模式 |
| **Memory** | `CLAUDE.md` / `.claude/rules/` | 通过 CLAUDE.md 文件和 `@path` 导入实现持久上下文 |
| **Checkpointing** | 自动（基于 git） | 自动跟踪文件编辑，支持回退（Esc Esc 或 `/rewind`） |

### 2. 编排工作流（Orchestration Workflow）

项目提出了一个清晰的编排架构模式：

```
Command（触发）-> Agent（执行）-> Skill（知识注入）
```

以天气查询编排器（weather-orchestrator）为完整示例，展示了如何将 Command 作为入口、Agent 处理逻辑、Skill 提供领域知识的协作模式。

### 3. 69 条技巧（Tips and Tricks）

按 12 个类别组织的社区最佳实践，每条标注来源（Boris Cherny、Thariq、社区等）：

- **Prompting（3 条）** — 挑战 Claude、"scrap this and implement the elegant solution"、让 Claude 自己修 bug
- **Planning/Specs（6 条）** — 总是从 plan mode 开始、用 AskUserQuestion 让 Claude 采访你、原型 > PRD
- **CLAUDE.md（7 条）** — 控制在 200 行以内、用 `<important if="...">` 标签、用 settings.json 替代 CLAUDE.md 中的硬性规则
- **Agents（4 条）** — 按功能划分子 Agent、用子 Agent 保持主上下文清洁、test time compute
- **Commands（3 条）** — 用 Command 而非子 Agent 做工作流、一天做多次的事就变成斜杠命令
- **Skills（9 条）** — 用 context:fork 隔离执行、Skills 是文件夹不是文件、构建 Gotchas 部分、描述写给模型看
- **Hooks（5 条）** — 用 PostToolUse 自动格式化、用 Stop hook 让 Claude 继续或验证
- **Workflows（7 条）** — 50% 上下文时手动 /compact、用 Opus 规划用 Sonnet 写码、用 ultrathink 关键词
- **Workflows Advanced（6 条）** — ASCII 图理解架构、用 /loop 和 /schedule 做定时任务、投资验证技能
- **Git / PR（5 条）** — PR 保持小而聚焦、always squash merge、每小时至少提交一次
- **Debugging（7 条）** — 截图分享给 Claude、让 Claude 跑后台看日志、/doctor 诊断问题
- **Utilities（5 条）** — 用终端而非 IDE、/voice 语音提示提效 10x、用好 status line
- **Daily（2 条）** — 每日更新 Claude Code、每天先读 changelog

### 4. 开发工作流横向对比

收录并对比了 10 个主流 Claude Code 开发工作流：

| 工作流 | Stars | 独特之处 |
|--------|-------|----------|
| Everything Claude Code | 137k | Instinct 评分、AgentShield、多语言规则 |
| Superpowers | 135k | TDD-first、Iron Laws、全计划审查 |
| Spec Kit | 85k | Spec 驱动、Constitution、22+ 工具 |
| gstack | 64k | 角色人设、/codex review、并行冲刺 |
| Get Shit Done | 48k | 全新 200K 上下文、Wave 执行、XML 计划 |
| BMAD-METHOD | 44k | 完整 SDLC、Agent 人设、22+ 平台 |
| OpenSpec | 37k | Delta Specs、棕地项目、Artifact DAG |
| oh-my-claudecode | 24k | 团队编排、tmux workers、技能自动注入 |
| Compound Engineering | 13k | Compound Learning、多平台 CLI、插件市场 |
| HumanLayer | 10k | RPI、上下文工程、300k+ LOC |

### 5. 热门新功能（Hot Features）

追踪 Claude Code 最新 beta 和实验性功能：

| 功能 | 说明 |
|------|------|
| **Power-ups** | 交互式教学课程，用动画演示教你 Claude Code 特性 |
| **Ultraplan** | 云端计划草稿，支持浏览器审阅和行内评论 |
| **Claude Code Web** | 云端运行任务，支持长时任务和并行会话 |
| **Computer Use** | 让 Claude 控制屏幕——打开应用、点击、输入 |
| **Auto Mode** | 后台安全分类器替代手动权限确认 |
| **Channels** | 从 Telegram/Discord/Webhook 推送事件到运行中的会话 |
| **Voice Dictation** | 20 种语言的按键说话语音输入 |
| **Agent Teams** | 多 Agent 并行处理同一代码库 |
| **Scheduled Tasks** | /loop 本地循环 + /schedule 云端定时 |

### 6. 深度报告

项目还产出了一系列专题对比报告：

- Agent SDK vs CLI 对比
- Browser Automation MCP 分析
- Global vs Project Settings 对比
- Skills in Monorepos 指南
- Agent Memory 分析
- Advanced Tool Use 报告
- Usage & Rate Limits 指南
- Agents vs Commands vs Skills 对比
- LLM Degradation 分析

### 7. 创始人内容索引

系统整理了 Claude Code 创始人 Boris Cherny 和核心团队成员的内容：

- **视频/播客** — Pragmatic Engineer、Lenny's Podcast、Y Combinator 等 6 个深度访谈
- **推文/文章** — 从 2025 年 12 月到 2026 年 3 月的 14 篇核心内容

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **内容格式** | Markdown / HTML / SVG |
| **Agent 定义** | `.claude/agents/*.md` |
| **Command 定义** | `.claude/commands/*.md` |
| **Skill 定义** | `.claude/skills/*/SKILL.md` |
| **Hook 脚本** | Shell / Python |
| **配置** | `.claude/settings.json`、`.mcp.json` |
| **项目维护** | Claude Code 自身（v2.1.92）自动更新 |

---

## 使用场景

| 场景 | 说明 |
|------|------|
| **Claude Code 入门学习** | 按概念表顺序阅读，理解 Agent、Command、Skill、Hook 的区别和用法 |
| **构建自己的 Claude Code 工作流** | 参考编排模式和 69 条技巧，搭建适合自己团队的开发流程 |
| **工作流选型** | 通过 10 大工作流横向对比表，选择适合项目规模和需求的工作流 |
| **解决具体问题** | 在 Tips and Tricks 中查找特定场景的解决方案（如上下文管理、调试、PR 管理） |
| **追踪新功能** | Hot 板块跟踪最新 beta 功能和实验性特性 |
| **团队知识共享** | 作为团队 Claude Code 使用的标准参考文档 |

---

## 如何使用

```
1. 像读课程一样阅读本仓库，先理解 Agent、Command、Skill、Hook 的概念
2. 克隆仓库，动手实验——运行 /weather-orchestrator、听 hook 音效、试 Agent Teams
3. 回到自己的项目，让 Claude 参考本仓库建议该采用哪些最佳实践
```

---

## 相关项目

作者维护的系列项目：

- **claude-code-hooks** — Claude Code 的 Hook 集合
- **codex-cli-best-practice** — OpenAI Codex CLI 的最佳实践
- **codex-cli-hooks** — Codex CLI 的 Hook 集合

---

## 一句话总结

> Claude Code Best Practice 是一个**社区驱动的 Claude Code 百科全书式知识库**（32k+ Stars），由 Claude Community Ambassador shanraisshan 维护，系统整理了核心概念定义、69 条来自创始团队的实用技巧、10 大开发工作流横向对比、编排架构模式、beta 功能追踪和深度专题报告，是 Claude Code 用户从入门到精通的必备参考资料。

# wshobson/agents 项目分析

## 项目名称
**Agents（wshobson/agents）** — 跨 7 大 AI 编码工具的多 harness 智能体插件市场
- **GitHub**: [wshobson/agents](https://github.com/wshobson/agents)
- **许可证**: MIT

---

## 项目概述

Agents 是目前规模最大的 AI 编码助手插件市场之一，维护着 **94 个插件**（92 个本地 + 2 个外部条目），内含 **202 个 agents、185 个 skills、105 个 commands**。它的核心卖点是「一次维护、多端复用」：同一套 Markdown 源组件可以安装到 Claude Code、OpenAI Codex CLI、Cursor、OpenCode、Antigravity CLI、GitHub Copilot 和 Pi 七种 harness（编码工具）上，安装与能力适配由各 harness 的适配层自动完成。

项目采用源组件共享架构——所有 agents/skills/commands 以统一 Markdown 源编写，再按目标工具生成对应格式的制品（如 Codex 的 TOML agents、Copilot 的 agent profiles）。超大 skill 正文会自动拆分为参考文件以适配 8 KB 预算限制。质量保障方面提供了 plugin-eval 评估框架（含 LLM judge 与 Monte Carlo 实验层），可用 `uv run` 对单个 skill 打分。插件覆盖 Python/JavaScript 开发、代码审查、测试、基础设施、安全扫描等工程全场景，由 619 次提交持续维护，是 agentic 编码生态事实上的「组件分发基础设施」。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 多 harness 支持 | 一套组件适配 Claude Code / Codex CLI / Cursor / OpenCode / Antigravity / Copilot / Pi，各有专门安装路由 |
| 插件市场 | 94 个插件按领域分组：python-development、javascript-typescript、developer-essentials、security-scanning 等 |
| Skills-only 安装 | `gh skill`（需 GitHub CLI 2.90+）或 `npx skills` 单独安装技能，无需克隆仓库、不带 hooks |
| 质量评估 | plugin-eval 框架：`score --depth quick` 快速评估 skill，LLM judge / Monte Carlo 为实验层 |
| 能力矩阵文档 | docs/harnesses.md 详列各 harness 的模型映射、工具权限、hooks 与安装差异 |
| 外部市场集成 | 可挂载外部 marketplace 条目（如 Pensyve 自托管运行时） |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 组件源格式 | Markdown（agents / skills / commands 共享源） |
| 适配生成 | 各 harness 专用 manifest（Claude plugin、Codex TOML、Copilot profiles 等） |
| 安装工具链 | Makefile + uv（Python 3.12+）+ GitHub CLI |
| 评估框架 | plugin-eval（启发式 + LLM judge + Monte Carlo，可选 llm 依赖） |
| 语言统计 | Python（脚本与工具链） |

---

## 项目亮点

### 规模最大的开源 agentic 组件库
202 agents + 185 skills + 105 commands 的体量远超同类项目，且全部经过统一 authoring conventions 约束，质量一致性有保障。

### 真正的「write once, run in 7 harnesses」
不是简单的格式转换，而是针对每个 harness 的能力差异做了完整适配：工具权限翻译、hooks/MCP 配置差异、8 KB skill 预算的正文拆分都有专门处理。

### 工程化质量闭环
从架构文档（ARCHITECTURE.md）、贡献规范、CLI 往返验证（round-trip-results.md）到 plugin-eval 评分框架，形成了组件生产→验证→分发的完整流水线。

---

## 应用场景

### 多工具用户统一配置
同时使用 Claude Code 和 Cursor/Codex 的开发者，只需维护一份组件集，所有工具获得一致的 agent/skill 体验。

### 团队标准化工程实践
通过 security-scanning、developer-essentials 等插件，团队可以把代码审查规范、测试模式、安全基线一键分发到每个成员的 AI 编码工具中。

### Skill 生态研究
185 个 skills 的源 Markdown 是研究「如何写出高质量 agent skill」的最佳参考语料，配套的 authoring conventions 文档可直接作为团队内部规范。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 41,264 |
| 总 Forks | 4,393 |
| 今日新增 | +93 |
| Open Issues | 5 |
| 创建时间 | 2025-07-24 |

---

## 总结

wshobson/agents 用一套共享 Markdown 源 + 七种 harness 适配层的设计，解决了 AI 编码组件碎片化的核心痛点，以 4.1 万 Star 成为当前 agentic 编码生态中覆盖面最广、工程化最成熟的插件分发基础设施。

---

*数据来源：GitHub 仓库 (wshobson/agents)，2026 年 10 月 21 日访问*
*首次分析：见文件头部 | 最近更新：2026 年 10 月 21 日*

# Agentic Awesome Skills (AAS Core) 项目分析

## 项目名称
**Agentic Awesome Skills** — 2,715+ 个可安装 SKILL.md 技能的智能体技能目录与选配工具
- **GitHub**: [sickn33/agentic-awesome-skills](https://github.com/sickn33/agentic-awesome-skills)
- **许可证**: MIT
- **语言**: JavaScript / Markdown（技能本体为 SKILL.md）

---

## 项目概述

Agentic Awesome Skills（AAS）是一个超大型的智能体技能（Skills）目录项目，收录了 **2,715+ 个可安装的 SKILL.md 技能剧本**，覆盖编码、调试、文档、媒体生成等各类任务场景。其核心组件 AAS Core 帮助 Codex 或 Claude 等智能体检索完整本地技能目录、记录智能体选择的技能、并在修改目标项目前输出可审查的选配计划（plan preview）。

项目的定位强调「可审查与可复用」：AAS Core 本身不做技能排名或推荐，而是让智能体基于项目实际需要自主选择技能集，通过只读的 `compose_stack` 工具在内存中校验所选技能的结构与身份，持久化为 `aas-stack.json` 清单（技术上限 128 个技能），再经 `aas stack validate` 校验、`aas stack plan` 生成不可变预览供人工审查后安装。应用（apply）与恢复（recovery）环节仍属实验性功能，需显式 opt-in。

当前版本 V19.11.0，迭代速度极快。项目为独立社区项目，与 Google 无隶属关系（Antigravity、Gemini 等名称仅描述兼容目标），已获 Vercel OSS Program、Snyk、BrowserStack、Atlas Cloud 等厂商赞助支持，总 Star 达 4.8 万。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **2,715+ 技能目录** | 覆盖开发、调试、文档、媒体等场景的可安装 SKILL.md 剧本库 |
| **AAS Core 智能选配** | 智能体检查项目后自主选择精确技能集，只读 compose_stack 校验结构 |
| **计划预览（plan preview）** | 安装前输出不可变预览，人工审查后才落地，核心路径不改目标 |
| **栈清单与校验** | aas-stack.json（上限 128 技能）+ `aas stack validate` 结构校验 |
| **直接安装器** | 已知技能 ID 时 `agentic-awesome-skills --skills a,b --dry-run` 预览后直装 |
| **多宿主适配** | Claude Code、Codex CLI、Cursor、Gemini CLI、Kiro、Copilot、OpenCode、Antigravity 等 |
| **Workbench 浏览器审查** | aaskills.tech/workbench 在浏览器内存中审查栈与计划，不触本地文件系统 |
| **稳定技能清单 v1** | 标准化技能清单格式，保证跨版本可追溯 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 分发形态 | npm 包（agentic-awesome-skills）+ MCP 本地服务器 |
| 技能格式 | SKILL.md（Markdown 剧本） |
| 核心工具 | compose_stack（只读校验）/ aas CLI（validate/plan/install-preview） |
| 宿主支持 | Codex CLI、Claude Code、Cursor、Gemini CLI、Kiro、Copilot、OpenCode、Antigravity、Autohand Code |
| 托管目录 | aaskills.tech（hosted catalog）+ Workbench（浏览器端审查） |

---

## 项目亮点

### 1. 「人审最后一步」的信任边界设计
与直接自动安装技能的方案不同，AAS Core 把技能选择权交给智能体、把落地权留给人：所有安装路径（plan preview / dry-run）都先产出可审查的产物，apply 必须显式 opt-in，信任边界在文档中写得非常明确。

### 2. 超大规模与高迭代节奏
2,715+ 技能的规模在同类项目中居首，README 头部的 registry-sync 元数据显示版本已到 19.11.0 且每日同步，目录维护活跃度极高。

### 3. 中立目录定位
Core 明确「不排名、不推荐」，只做结构校验与计划预览，避免目录方对技能质量的背书责任，同时通过 hosted catalog 与 Workbench 提供发现与审查界面。

---

## 应用场景

### 1. 智能体项目脚手架
新项目启动时让 Codex/Claude 扫描代码库，从目录中选出精确技能集，经人工审查后一次性装齐开发所需技能。

### 2. 团队技能标准化
通过 aas-stack.json 清单固化团队认可的技能组合，`aas stack validate` 保证成员环境一致性。

### 3. 技能生态研究
2,715+ 个 SKILL.md 是研究社区提示词工程与技能设计模式的绝佳语料库。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 48,113 |
| 总 Forks | 7,021 |
| 今日新增 | +125 |
| 当前版本 | V19.11.0 |
| 主要语言 | JavaScript / Markdown |
| 许可证 | MIT |

## 📋 更新记录

### 更新 1 — 2026 年 10 月 21 日（再次登上 Trending）

**更新原因**：Agentic Awesome Skills 连续第二天登上 GitHub Trending（第 2 次上榜），总 Stars 从 47,988 增至 48,113（**+125**，API 口径）。

**最新动态**：

- 连续多日稳定在 Trending 榜单尾部，今日增量 +125 stars、Forks +13（7,008 → 7,021），增速较首榜（+58/日）有所放缓但仍为正增长。
- 版本迭代持续推进（当前 V19.11.x），2,600+ 技能目录与 AAS Core 控制面（CLI、本地 MCP、目录、插件、Workbench）保持活跃维护。
- README 强调其作为「本地、智能体优先的控制平面」定位：完整目录发现、智能体自有选择、栈校验与规划，与同类项目（如 wshobson/agents 多 harness 插件市场）形成生态互补。

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 47,988 | 48,113 | +125 |
| 总 Forks | 7,008 | 7,021 | +13 |
| 今日新增 | +58 | +125 | +67 |

---

## 总结

Agentic Awesome Skills 以 2,715+ 技能的目录规模和「智能体选、人来批」的信任边界设计，成为 AI Agent 技能生态中规模最大、工程化程度最高的技能分发基础设施之一——它不生产技能价值，但把技能的发现、校验、审查与安装流程标准化了。

---

*数据来源：GitHub 仓库 (sickn33/agentic-awesome-skills)，2026 年 10 月 20 日访问*
*首次分析：见文件头部 | 最近更新：2026 年 10 月 21 日*

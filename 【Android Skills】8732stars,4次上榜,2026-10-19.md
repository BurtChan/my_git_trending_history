# Android Skills 项目分析

## 项目名称

**Android Skills** — Google 官方 Android 开发 AI Agent 技能库

- **GitHub**: [android/skills](https://github.com/android/skills)
- **许可证**: Apache-2.0

---

## 项目概述

Android Skills 是 Google Android 官方团队推出的 AI Agent 技能（Skills）仓库，提供一组「AI 优化的模块化指令与资源」，帮助 AI 编码 Agent 更好地理解和执行符合 developer.android.com 最佳实践的 Android 开发任务。技能以开放标准（agentskills.io）的 SKILL.md Markdown 文件形式发布，为 LLM 提供专业领域与工作流的技术规格锚定。

项目最值得关注的设计哲学是「只补短板」：Google 明确表示技能开发聚焦于「评估显示 LLM 表现不佳」的用例与工作流，而不去覆盖 LLM 已经熟练的成熟领域（如基础 Jetpack Compose 最佳实践）。这是一种评估驱动的技能建设思路，让每个技能都有明确的增量价值。

仓库配套 Android CLI 工具链，一条命令即可把技能安装到 Gemini、Antigravity、Claude Code、Codex 等各类 Agent 的技能目录，标志着 Android 官方开发工具链正式向 Agentic AI 工作流开放。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 官方技能库 | 覆盖 Android 开发中 LLM 表现不佳的领域（如 R8 混淆分析 r8-analyzer、Wear OS Compose M3 等） |
| 开放标准格式 | 遵循 agentskills.io 开放标准的 SKILL.md 文件，可被主流 Agent 自动发现与激活 |
| Android CLI 集成 | `android skills add/update` 一条命令安装/更新技能到当前项目或所有检测到的 Agent |
| 多 Agent 适配 | 支持 Claude Code（plugin marketplace）、Codex、Gemini、Antigravity 等多种 Agent 安装方式 |
| 自动激活 | Agent 根据任务自动匹配技能，如「Make my app UI edge-to-edge」即触发对应技能 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 技能格式 | SKILL.md（agentskills.io 开放标准） |
| 安装工具 | Android CLI（android skills add/update） |
| 支持平台 | Gemini / Antigravity（默认 ~/.gemini/antigravity/skills）、Claude Code、Codex |
| 维护方 | Google Android 官方团队（不接受公开 PR，经 GitHub Issue 反馈） |

---

## 项目亮点

### 官方权威 + 评估驱动

这是 Android 官方（android 组织）在 Agent Skills 标准上的第一个重大动作。技能选题完全由 LLM 评估数据驱动——只在模型确实做不好的领域投入，避免了「官方技能库沦为文档搬运」的常见问题，每个技能都有可验证的增量价值。

### Agentic Android 开发的官方入口

配合 developer.android.com 上的 Android skills / Android CLI / Android Studio (Gemini skills) 文档体系，Google 正在把「AI Agent 写 Android 应用」从社区实践升级为官方支持的一等公民工作流。

### 一次安装、全 Agent 生效

`android skills add --all` 会自动检测本机所有 Agent 目录并安装，技能更新也由 CLI 统一管理，解决了技能在多 Agent 间散装维护的痛点。

---

## 应用场景

### AI 辅助 Android 开发

在日常 Android 项目中使用 Claude Code / Gemini / Codex 开发时安装对应技能，让 Agent 在 R8 优化、边缘到边缘 UI、Wear OS 等容易出错的领域输出符合官方最佳实践的代码。

### 团队工程规范落地

团队可以把技能作为「可执行的开发规范」分发：新成员的 Agent 装上同一套技能，产出代码自动对齐团队与官方标准。

### Agent 技能生态研究

作为 Google 官方对 agentskills.io 开放标准的落地样本，是研究「官方厂商如何构建 Agent 技能生态」的绝佳参考。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 8,732 |
| 总 Forks | 567 |
| 今日新增 | 140 |
| 许可证 | Apache-2.0 |
| 主要语言 | Markdown (SKILL.md) |


## 📋 更新记录

### 更新 1 — 2026年10月17日（连续第二日在榜）

**更新原因**：Android Skills 连续第二日登上 GitHub Trending（第 2 次上榜），API 口径总 Stars 从 7,860 增至 7,987（+127），Forks 从 523 增至 530（+7）。

**最新动态**：

Android Skills 回榜次日继续在榜，单日 +127，总星逼近 8 千。Google 官方保持约两日一 bump 的更新节奏：v1.0.15（10/14）与 v1.0.14（10/12）接连同步技能库内容并更新 Claude 插件清单（#234、#230），评估驱动补短板的技能集持续扩充。在 Skills 生态集体在榜（Superpowers、Context Mode、ECC 等同榜）的背景下，Google 官方入场为 Android 开发 Agent 化提供的背书效应继续放大。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 7,860 | 7,987 | +127 |
| 总 Forks | 523 | 530 | +7 |
| 今日新增 | 35 | 127 | — |

**核心变化概要**：

- Stars 7,860 → 7,987（+127），连续第二日在榜，累计 2 次上榜，逼近 8 千
- Forks 523 → 530（+7）
- v1.0.15（10/14）/ v1.0.14（10/12）接连更新，官方约两日一 bump 节奏延续

---

### 更新 2 — 2026年10月18日（连续第三日在榜）

**更新原因**：Android Skills 连续第三日登上 GitHub Trending（第 3 次上榜），API 口径总 Stars 从 7,987 增至 8,592（+605），单日增量较昨日（+127）明显放大，突破 8 千关口。

**最新动态**：

Android Skills 回榜第三日增速显著抬升，单日 +605（前两日分别为 +35、+127），总星正式突破 8 千。仓库保持高更新频率：latest release 仍为 v1.0.15（10/14），技能目录覆盖 build-system、camera、device-ai、jetpack-compose、media、navigation、performance、play、security、testing、tv、wear、xr 等 20+ 个 Android 开发领域，Forks 同步增至 560。在 Skills 生态多项目同榜的格局下，Google 官方 Android 技能库已成为开发者安装 Agent 技能的确定性入口之一。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 7,987 | 8,592 | +605 |
| 总 Forks | 530 | 560 | +30 |
| 今日新增 | 127 | 605 | — |

**核心变化概要**：

- Stars 7,987 → 8,592（+605），连续第三日在榜，累计 3 次上榜，突破 8 千
- Forks 530 → 560（+30）
- 单日增量 +605 为上榜以来最大，评估驱动补短板的官方技能集需求持续放量

---

### 更新 3 — 2026年10月19日（连续第四日在榜）

**更新原因**：Android Skills 连续第四日登上 GitHub Trending（第 4 次上榜），API 口径总 Stars 从 8,592 增至 8,732（+140），单日增量较昨日（+605）明显回落，进入稳定放量阶段。

**最新动态**：

Android Skills 回榜第四日增速回落至 +140，属于连续在榜后段的自然衰减。仓库保持活跃迭代：提交数增至 76 commits，技能目录在既有 build-system、camera、device-ai、jetpack-compose、media、navigation、performance、play、security、testing、tv、wear、xr 等领域之外，新增 identity（身份认证）、system/edge-to-edge（沉浸式 UI）、profilers/android-profiler（性能剖析）等目录，覆盖面继续扩展。Forks 同步增至 567。README 中的安装路径显示，无既有 Agent 目录时技能默认安装给 Gemini 与 Antigravity（~/.gemini/antigravity/skills），反映出 Google 在自家 Agent 生态与第三方 Agent（Claude Code、Codex）之间双向兼容的定位。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 8,592 | 8,732 | +140 |
| 总 Forks | 560 | 567 | +7 |
| 今日新增 | 605 | 140 | — |

**核心变化概要**：

- Stars 8,592 → 8,732（+140），连续第四日在榜，累计 4 次上榜
- Forks 560 → 567（+7）
- 技能目录新增 identity、system/edge-to-edge、profilers/android-profiler 等领域，提交数增至 76


## 总结

Android Skills 是 Google 官方进军 Agent 技能生态的标志性项目：以评估驱动只补 LLM 短板、一次安装覆盖全部主流 Agent，标志着 Android 开发工具链正式拥抱 Agentic AI 工作流。

---

*数据来源：GitHub 仓库 (android/skills)，2026 年 10 月访问*
*首次分析：见文件头部 | 最近更新：2026 年 10 月 19 日*

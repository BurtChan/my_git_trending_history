# Expo Skills 项目分析

## 项目名称

**Expo Skills** — Expo 官方出品的 AI Agent 技能库，让 AI 编程助手正确使用 Expo/EAS 构建 React Native 应用
- **GitHub**: [expo/skills](https://github.com/expo/skills)
- **许可证**: MIT
- **语言**: Shell（技能定义文件）
- **创建时间**: 2025-11-30
- **官网**: https://docs.expo.dev/skills/

---

## 项目概述

Expo Skills 是 React Native 开发框架 Expo 官方团队推出的 AI Agent 技能（Skills）集合。它把 Expo 团队积累的框架知识与工程经验封装成一组结构化的 SKILL.md 文件，供 Claude Code、Codex、Cursor、GitHub Copilot、Windsurf、Gemini CLI 等主流 AI 编程代理按需加载——当开发者让 AI「建一个带 Tab 导航的 Expo Router 页面」或「创建 EAS 构建工作流」时，Agent 会根据任务上下文自动选用正确的技能，避免凭训练数据里的过时知识瞎编 API。

技能分为三组：框架组（免费开源，涵盖项目结构、Router 导航、动画、原生 UI、设计系统、数据请求、原生模块、Brownfield 集成、SDK 升级等 16 项）；服务组（围绕付费的 EAS 云服务，涵盖应用商店提交、EAS Hosting、CI/CD Workflow、OTA 更新、崩溃监控、云模拟器等 7 项，每项开头标注费用/套餐限制）；实验组（未定稿 API 的迁移技能）。

该项目是 2025 年底兴起的「Agent Skills」生态在官方框架厂商侧的标杆落地：与 Anthropic 的 Claude Skills、Vercel 的 skills 一样走 SKILL.md 想象力路线，但由框架官方维护意味着知识永远跟随 SDK 版本更新，这是社区技能库难以做到的。上线近一年已获 3,796 stars，再次以单日 +369 stars 登上 Trending。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 25+ 官方技能 | 覆盖 Expo Router、动画、设计系统、数据请求、原生模块、SDK 升级等全开发周期 |
| 多 Agent 通用 | 一个 `npx skills@latest add` 命令安装到 Cursor/Copilot/Windsurf/Gemini/Cline 等任意 Agent |
| 插件市场直装 | Claude Code 与 Codex 走官方插件市场（expo@claude-plugins-official / expo@openai-curated），自动更新 |
| 免费/付费边界清晰 | 框架技能全免费；EAS 服务技能明确标注 costs/plan-limits，避免 Agent 乱调付费服务 |
| Expo MCP Server 联动 | 技能教 Agent「怎么做」，MCP Server 给 Agent 实操能力（装依赖、触发构建、拉崩溃数据、截屏模拟器） |
| 反馈闭环 | 每个技能内置 `@expo/agent-cli feedback` 指令，可直接从 Agent 提交反馈 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 技能格式 | SKILL.md（Markdown 结构化知识文件） |
| 分发渠道 | skills.sh CLI、Claude Code 插件市场、Codex 插件市场 |
| 目标平台 | iOS / Android / Web（React Native + Expo SDK + EAS） |
| 配套设施 | Expo MCP Server（文档检索、构建触发、运行时调试） |
| 许可证 | MIT |

---

## 项目亮点

### 框架官方维护的「活文档」

社区技能库最大的痛点是随 SDK 演进快速过时。Expo Skills 由官方团队随 SDK 一起更新，技能内容明确声明「Expo 文档、Expo CLI、EAS CLI 才是唯一真相源，技能教 Agent 如何正确应用它们」——定位是文档的 Agent 适配层而非替代品，这个边界感设计值得所有框架厂商借鉴。

### 免费与付费服务的隔离设计

每个 EAS 服务技能开头强制携带费用/套餐限制说明，且技能描述自带分组标签。这防止了 AI Agent 在用户不知情的情况下触发付费构建或云服务——对成本敏感的个人开发者与小团队是实打实的保护。

### 一条命令覆盖全部主流 Agent

`npx skills@latest add expo/skills --skill '*'` 一条命令即可安装到十余种 AI 编程工具，Agent 侧零绑定。技能安装后通过各 Agent 的 SKILL.md 发现机制自动生效，无需逐家适配。

---

## 应用场景

### Expo/React Native 全栈开发

日常用 Cursor 或 Claude Code 开发 Expo 应用的团队，装上后 Agent 在路由、动画、原生模块、升级等场景直接给出符合当前 SDK 版本的最佳实践，减少「AI 生成的代码用了已废弃 API」的返工。

### Web 应用迁移原生 App

`expo-web-to-native` 与 `expo-brownfield` 技能专门覆盖 Next.js/Vite/CRA 应用迁移为原生应用、以及在现有原生 App 中嵌入 React Native 的高难度场景。

### CI/CD 与发布自动化

eas-workflows（CI/CD YAML）、eas-update（OTA 发布与回滚）、eas-observe（发布健康监控）等技能让 Agent 具备搭建完整移动端交付流水线的能力。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 3,796 |
| 总 Forks | 241 |
| 今日新增 | +369 stars |
| Open Issues | 101 |
| 创建时间 | 2025-11-30 |

---

## 📋 更新记录

### 更新 1 — 2026 年 10 月 30 日（再次登上 Trending）

**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：

Expo Skills 连续第二日登上 Trending，Star 从 3,427 增长至 3,796（+369），Fork 从 219 增至 241（+22）。工程侧保持高频迭代：10 月 28 日移除各技能 SKILL.md frontmatter 中的 per-skill version 字段（#266），简化技能元数据维护；eas-observe 技能新增 Expo MCP Server observe 工具文档，并补充 Expo Image 与 Reanimated 集成说明（#249/#252）；插件侧完成 Codex 向 Agent Plugins manifest 的迁移（#139），移除独立的 feedback 技能改由 agent CLI 承接。官方随 SDK 同步维护技能的策略持续兑现，覆盖的技能组与 Agent 平台（Claude Code、Codex 等）兼容面进一步扩大。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 3,427 | 3,796 | +369 |
| 总 Forks | 219 | 241 | +22 |

**核心变化概要**：
- Star 从 3,427 增长至 3,796（+369），连续第二日在榜
- SKILL.md frontmatter 移除 per-skill version 字段，元数据简化（#266）
- eas-observe 技能补充 Expo MCP Server observe 工具、Expo Image 与 Reanimated 集成文档
- Codex 插件完成向 Agent Plugins manifest 的迁移，独立 feedback 技能由 agent CLI 替代


## 总结

Expo 官方把框架知识封装成 25+ 个跨 Agent 通用的 AI 技能并随 SDK 同步维护，是「官方框架 × Agent Skills 生态」目前完成度最高的落地样本——用 React Native/Expo 开发的人几乎应该无脑安装。

---

*数据来源：GitHub 仓库 (expo/skills)，2026 年 10 月 30 日访问*

*首次分析：见文件头部 | 最近更新：2026 年 10 月 30 日*

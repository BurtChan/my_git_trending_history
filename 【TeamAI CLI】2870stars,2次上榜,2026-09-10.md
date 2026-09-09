# TeamAI CLI 项目分析

## 项目名称
**TeamAI CLI（teamai-cli）** — 腾讯开源的团队级 AI 代理 Harness 管理工具：「The team harness for AI agents」
- **GitHub**: [Tencent/teamai-cli](https://github.com/Tencent/teamai-cli)
- **许可证**: MIT
- **语言**: TypeScript（Node.js，npm 全局安装）

---

## 项目概述

TeamAI CLI 是腾讯开源的团队 AI 协作基础设施，核心理念是「Make Every Team AI Native」——把团队在 AI 编码代理上的最佳实践（技能、规则、文档、hooks、MCP 配置、环境变量、知识库）沉淀到一个共享 Git 仓库中，再通过 CLI 自动分发给每个成员本地的 AI 工具。无论团队用 Claude Code、Codex、Cursor、CodeBuddy、OpenCode 还是腾讯自家的 WorkBuddy，成员只需 `teamai init` 一次，之后每次会话启动时自动 `teamai pull` 拉取最新配置，实现「管理员配置一次、全团队自动同步」。

项目解决的是 AI 编码代理普及后的新痛点：每个开发者的 skills/rules/MCP 配置散落在各自机器上，团队最佳实践无法沉淀和复用。TeamAI 用 Git-native 的方式把「AI 工作流配置」变成团队资产——通过 `teamai push`（创建分支 + MR → 评审合并）与 `teamai pull`（SessionStart hook 自动触发）的闭环，让 Harness 的演进像代码一样走评审流程。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 多代理 Harness 管理 | 统一管理 skills / rules / docs / env / agents / hooks / MCP，支持 Claude Code、Codex、Cursor、CodeBuddy、OpenCode、WorkBuddy、OpenClaw、Hermes 等 8+ 工具 |
| Git-native 分发 | `teamai push` 开 MR 评审，合并后成员 `teamai pull` 自动同步；支持 GitHub / GitLab / GitCode / CNB / TGit / 私有 Git |
| 角色与标签 | `teamai roles` 定义角色→命名空间映射；`teamai tags` 按标签订阅技能，成员只同步所需资源 |
| 技能订阅源 | `teamai source` 订阅其他团队或组织共享仓库的技能，pull 时自动同步 |
| 知识库闭环 | `teamai session save` 记录脱敏会话摘要，`teamai digest` 生成每周团队使用报告（token 用量、会话量、干预率） |
| 团队仪表盘 | `teamai dashboard` 展示成员实时编码会话状态、干预次数、token 用量及 KB Health 知识库健康度 |
| CI 集成 | `teamai ci extract-mr` 从 MR 提取知识、评论、合并后写入知识库 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| CLI 主体 | TypeScript + Node.js（tsup 构建） |
| 测试 | Vitest（单测 + e2e） |
| 分发 | npm（`npm install -g teamai-cli`） |
| 配置 | hooks.yaml / mcp.yaml 声明式配置 |

---

## 项目亮点

### 覆盖最全的代理矩阵
支持矩阵横跨 8+ 主流 AI 编码工具，连 Hermes、DeepSeek Harness 等新生态也纳入兼容范围，是国内大厂中覆盖面最广的团队级 Harness 方案。

### 「push → 评审 → pull」的工程化治理
技能和规则变更走 MR 评审流程，杜绝个人随意改动影响全团队；重复 push 会更新既有 PR 而非新建，工程细节考虑周全。

### 用量分析与知识库健康度
不止分发配置，还闭环度量：周报 digest、会话摘要、KB Health 页面报告知识库覆盖率/召回趋势/沉默条目，让「团队 AI 资产」可运营、可维护。

---

## 应用场景

### 企业研发团队标准化
数十人团队统一 AI 编码规范：管理员维护技能库，新成员 init 一次即获得与团队一致的最佳实践配置。

### 跨团队技能共享
通过 source 订阅机制，组织内公共技能仓库一次维护、多团队复用。

### AI 工具治理与度量
管理者通过 dashboard 掌握团队真实 AI 使用情况（干预率、token 消耗），为工具选型和流程改进提供数据依据。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 2,870 |
| 总 Forks | 180 |
| 今日新增 | +258 |
| 创建时间 | 2026-04-27 |

---

## 📋 更新记录

### 更新 1 — 2026 年 9 月 10 日

**更新原因**：连续第二天登上 GitHub Trending 榜单（今日 +258 Stars，API 精确数据）

**最新动态**：

- Star 从 2,612 增至 2,870（+258），Forks 从 168 增至 180（+12），上榜第二天热度延续。
- 腾讯官方团队持续维护，团队 AI 工作流配置即代码的定位在国内大厂开源项目中独树一帜。
- Git 评审式分发 + 角色标签管控 + 使用度量闭环的「团队 AI 治理」方案继续吸引企业开发者关注。

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|---------|---------|------|
| 总 Stars | 2,612 | 2,870 | +258 |
| 总 Forks | 168 | 180 | +12 |
| 今日新增 | — | 258 stars | — |

**核心变化概要**：

- 连续第二天在榜，+258 Stars
- 大厂背书的团队 AI 治理方案关注度提升
- Fork 增长 12 个，企业试用迹象初显

---

## 总结

腾讯 TeamAI CLI 把「团队 AI 工作流配置」当成代码资产来管理：Git 评审式分发 + 角色标签精细管控 + 使用度量闭环，是国内大厂对「AI 代理团队化治理」这一新命题给出的最完整开源答案，首日上榜即 +1,083 Star 说明切中了团队标准化痛点。

---

*数据来源：GitHub 仓库 (Tencent/teamai-cli)，2026 年 9 月 10 日访问*
*首次分析：2026 年 9 月 9 日 | 最近更新：2026 年 9 月 10 日*

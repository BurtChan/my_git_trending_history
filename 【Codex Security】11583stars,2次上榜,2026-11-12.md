# Codex Security 项目分析

## 项目名称
**Codex Security** — OpenAI 出品的安全漏洞发现、验证与修复 CLI/SDK
- **GitHub**: [openai/codex-security](https://github.com/openai/codex-security)
- **许可证**: Apache-2.0

---

## 项目概述

Codex Security 是 OpenAI 官方推出的应用安全工具链，提供安全工作流的 CLI（`cs` / `codex-security` 命令）与 TypeScript SDK，用于在代码中发现（find）、调查（investigate）和修复（fix）安全漏洞。它既可以嵌入 Codex Agent 会话中使用（安全工作流插件），也可以在终端独立运行扫描，还能通过 GitHub Action 和 SDK 嵌入 CI/自动化管道。

项目定位是「AI 原生的安全扫描器」：与传统 SAST 工具不同，Codex Security 的扫描由大模型驱动，能进行深度调查（Deep Scan，可设 15 分钟标准调查时限）、对候选发现做二次验证排除误报、生成补丁并验证既有修复。扫描结果本地保存为 Markdown 报告（含源码证据与覆盖范围说明），也可发布到 Codex Security Cloud 集中管理。

从 README 的功能广度看，这是一个覆盖安全开发全生命周期的产品：扫描（全库/指定路径/Git diff）→ 验证与修复 → 报告治理（去重、按自定义评级标准评严重度、从源码与 Git 历史建议 owner）→ 第三方扫描器结果导入 → 与 Linear/Jira/GitHub 工单联动 → SARIF/JSON/CSV 导出 → 容器化批量扫描。7 月创建至今 11.4K Star，是 OpenAI 在 DevSecOps 方向的重要落子。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 多粒度扫描 | 全库、指定路径、Git 变更区间（base→HEAD）；Deep Scan 在标准扫描基础上重复扫描并去重 |
| 发现验证与修复 | 验证候选发现、生成补丁、验证已有修复是否有效 |
| 安全治理文档 | 起草 SECURITY.md 策略、保存威胁模型供后续评审 |
| 报告管理 | 浏览已保存扫描、识别重复、按自定义评级评估严重度、从源码/Git 历史建议责任人 |
| 第三方扫描器导入 | 预览外部扫描器发现、本地保存或发布到 Codex Security Cloud |
| 工单集成 | Linear、Jira、GitHub 跟踪发现；导出 SARIF/JSON/CSV |
| CI 自动化 | GitHub Action + SDK，支持跨仓库/组件的容器化批量扫描（Docker Compose） |
| 多模型后端 | 支持 OpenAI、Amazon Bedrock（AWS 凭证直连）、OpenRouter、Fireworks AI 等 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| CLI/SDK | TypeScript（npm: @openai/codex-security） |
| 运行环境 | Node.js 22.13+/24/26，Python 3.10+（辅助） |
| 包管理 | pnpm；Bun 亦在工具链中 |
| 部署形态 | CLI 全局安装 / npx / GitHub Action / Docker Compose 容器化批量 |
| 结果格式 | Markdown 报告 + SARIF/JSON/CSV 导出 |
| 许可证 | Apache-2.0 |

---

## 项目亮点

### 证据驱动的扫描报告
每次扫描产出 Markdown 报告，包含源码证据（source evidence）与排除项（exclusions）说明——发现不是一句警告，而是带上下文的调查结论，便于人工复核与后续修复。

### AI 验证消除误报
传统扫描器误报率高是运维最大痛点。Codex Security 的 validate 环节对候选发现做二次验证，patch 环节可直接生成并验证修复，把「发现→确认→修复」闭环压缩到一个工具内。

### 从单机到流水线的完整自动化路径
本地 `cs scan` 起步，`--max-time 15` 控制调查成本上限；CI 中用环境变量注入 API Key；批量场景用 Docker Compose 保持结果与认证状态跨运行复用；workflow runner 把单个 CLI 阶段容器化并可对接独立部署的 findings 服务。

### 开放的发现身份与互操作
提供 scanner-imports 的 schema 指南，定义导入发现的身份与证据标准；支持 `publish scan --to custom` 与显式 `--findings-url` 对接自建端点，避免厂商锁定。

---

## 应用场景

### DevSecOps CI 门禁
在 GitHub Actions 中对每次 PR 运行安全扫描，发现自动建单（Linear/Jira），SARIF 导出可接入 GitHub Security tab，形成持续安全基线。

### 遗留系统安全体检
对存量仓库跑 Deep Scan，AI 驱动的调查能覆盖传统规则引擎难以表达的漏洞模式（如业务逻辑缺陷），验证环节过滤误报后由人工确认修复。

### 安全团队报告整合
把多个第三方扫描器的结果导入统一平台，去重、按组织自定义的严重度评级标准打分、自动建议 owner，再发布到云端集中跟踪。

### 开源项目安全托管
维护者可用它起草 SECURITY.md、跑社区贡献代码的扫描、验证修复 PR 是否真正消除了漏洞。

---

## Star 数据

| 指标 | 数据 |
|------|------|
| **总 Stars** | 11,583 |
| **总 Forks** | 920 |
| **今日新增 Stars** | +204 |
| **许可证** | Apache-2.0 |
| **创建时间** | 2026-07-13 |

---

## 📋 更新记录

### 更新 1 — 2026 年 11 月 12 日

**更新原因**：再次登上 GitHub Trending，Star 数从 11,379 增长至 11,583（+204）

**最新动态**：开发节奏极快（11 月 11 日单日 4 个合并）：workbench findings 通过共享 Cloud transport 发布版本化结果（#2603）、SDK 修复网络等待期间扫描中断问题（#2411）、CLI 修复 JSON 错误与 token 窗口保留（#2593）、finding 导入简化与导出文件保护（#2595）。产品在「发现→修复→治理」闭环上快速迭代。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 11,379 | 11,583 | +204 |
| 总 Forks | 914 | 920 | +6 |

**核心变化概要**：
- Star 数 11,379 → 11,583（+204），Forks 914 → 920（+6）
- 第二次上榜（首次 11 月 11 日）
- 11 月 11 日单日 4 个合并：Cloud transport 版本化 findings（#2603）、扫描网络韧性（#2411）等

## 总结

Codex Security 把大模型的调查推理能力注入应用安全全流程：扫描带证据、验证去误报、修复有补丁、治理可集成，是 OpenAI 在 AI 驱动 DevSecOps 赛道的旗舰级开源布局。

---

*数据来源：GitHub 仓库 (openai/codex-security)，2026 年 11 月访问*
*首次分析：见文件头部 | 最近更新：2026 年 11 月 12 日*

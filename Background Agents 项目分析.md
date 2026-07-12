# Background Agents 项目分析

## 项目名称
**Background Agents (Open-Inspect)** — 开源后台 AI 编程代理系统，支持多客户端接入和多人协作
- **GitHub**: [ColeMurray/background-agents](https://github.com/ColeMurray/background-agents)
- **许可证**: MIT

---

## 项目概述
Background Agents（Open-Inspect）是一个受 Ramp 公司 Inspect 系统启发的开源后台 AI 编程代理系统。它提供了一个托管式后台编码代理，可以在用户处理其他工作时自主完成编码任务。系统支持多种接入方式——Web UI、Slack、GitHub PR、Linear 工单、Webhook 等，用户可以从任何地方发起编码任务。

Open-Inspect 的核心架构采用控制平面（Cloudflare Workers + Durable Objects）和数据平面（Sandbox 后端）的分离设计。控制平面负责会话管理、WebSocket 通信、GitHub 集成和事件流；数据平面提供完整的开发环境（Node.js、Python、git、浏览器自动化、VS Code）。每个会话在独立的沙盒中运行，支持并行子任务在独立沙盒中同时工作。

系统支持 Anthropic Claude、OpenAI Codex（通过 ChatGPT 订阅）和 OpenCode Zen 等多种 AI 模型，提供多人实时协作的"多人游戏"模式。项目采用单租户安全模型设计，适合组织内部部署——所有用户共享同一 GitHub App 凭证，部署在组织 SSO/VPN 之后。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 后台自主编码 | AI 代理在后台独立完成编码任务，用户无需实时监控 |
| 多客户端接入 | 支持 Web UI、Slack、GitHub PR、Linear、Webhook 多种接入方式 |
| 多人协作 | 多人实时协作同一编码会话，支持并行子任务在独立沙盒运行 |
| 完整开发环境 | 沙盒内置 Node.js、Python、git、浏览器自动化、VS Code |
| 定时任务 | 支持 cron 定时任务、Sentry 告警触发、Webhook 触发自动化 |
| PR 归属 | 创建 PR 时使用正确的 commit 归属，归因到发起任务的用户 |
| 多模型支持 | 支持 Claude、OpenAI Codex、OpenCode Zen 等模型 |
| Cloudflare 原生 | 控制平面基于 Cloudflare Workers + Durable Objects，无服务器架构 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 控制平面 | Cloudflare Workers + Durable Objects + D1 |
| Web 客户端 | Next.js |
| 后端 | TypeScript |
| 基础设施 | Modal / Daytona / OpenComputer |
| 集成 | GitHub App、Slack Bot、Linear Bot |

---

## 项目亮点

### 控制平面与数据平面分离架构
Open-Inspect 采用创新的架构设计：轻量级控制平面运行在 Cloudflare Workers 上（按请求计费、自动扩展），而重量的沙盒环境作为数据平面独立部署。这种分离使得系统可以根据实际负载独立扩展两个平面，控制成本的同时保证性能。

### 多人协作的"多人游戏"模式
系统支持多人实时协作同一编码会话，类似游戏中的"多人模式"。多个开发者可以同时观察和指导 AI 代理的工作，甚至可以创建并行子任务在不同的沙盒中同时处理不同问题。这种协作模式在开源编码代理系统中非常罕见。

### 从 Slack 到 PR 的全链路自动化
用户可以直接在 Slack 消息中发起编码任务，AI 代理完成后自动创建 GitHub PR 并归因到正确的用户。Linear 工单也可以自动触发编码会话。这种从任务管理到代码交付的全链路自动化，大大简化了团队的工作流程。

---

## 应用场景

### 团队异步编码工作流
开发团队使用 Open-Inspect 处理异步编码任务——团队成员在 Slack 或 Linear 中创建任务后即可切换到其他工作，AI 代理在后台完成编码并创建 PR。团队在 PR Review 环节汇合，实现高效的异步协作。

### 自动化 Bug 修复和代码维护
将 Sentry 告警等监控系统的通知接入 Webhook，当 Bug 触发时自动启动编码会话修复问题并创建 PR。这实现了从 Bug 发现到修复的全自动化流程。

### 开源项目维护
开源项目维护者可以使用 GitHub PR 集成，让 AI 代理自动处理简单的 PR（如格式化、lint 修复、文档更新等），释放维护者的时间专注于更重要的技术决策。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 2,171 |
| 总 Forks | 336 |
| 今日新增 | 9 |
| 主要语言 | TypeScript |
| 创建时间 | 2026-01-25 |

---

## 总结
Background Agents 是一个架构精巧的开源后台编码代理系统，以控制平面与数据平面分离的设计实现弹性扩展，多客户端接入和多人协作模式为企业级 AI 辅助编码提供了完整的解决方案。

---

*数据来源：GitHub 仓库 (ColeMurray/background-agents)，2026 年 7 月访问*

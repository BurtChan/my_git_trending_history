# Weave Router 项目分析

## 项目名称
**Weave Router** — 面向 Agent 系统的模型路由器，50ms 内把每个 prompt 路由到最合适的模型，端点一换立省 40-70% 成本
- **GitHub**: [workweave/router](https://github.com/workweave/router)
- **许可证**: ELv2（Elastic License 2.0，API 标注 NOASSERTION）
- **背后团队**: Weave（workweave.ai，工程智能平台，Robinhood/PostHog/Reducto 等在用）

---

## 项目概述

Weave Router 是一个 drop-in 代理：把 Claude Code、Codex、Cursor 或自有应用的 API 端点指向 localhost:8080，它就接管每个请求的模型选择——不是按 prompt 关键词瞎猜，而是用机载微型嵌入器（on-box embedder）+ 源自 arXiv 论文 Avengers-Pro（2508.12631）的聚类评分器，按「动作」粒度（而非回合粒度）为每一次上游 API 调用挑选当时最优的模型。兼容 Anthropic Messages、OpenAI Chat Completions、Gemini 原生三种 API 形态（含流式、工具调用、视觉），通过 OpenRouter 也认识 DeepSeek/Kimi/GLM/Qwen/Llama/Mistral 等 OSS 模型。BYOK 默认：密钥留本机静态加密。OTLP trace 开箱即用，路由决策可导出为 NDJSON 进自有数仓。Go 1.25 编写，800 commits，测试齐全。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 每动作路由 | 聚类评分器按 action 粒度选模型，官方宣称降本 40-70% |
| 三协议兼容 | Anthropic / OpenAI / Gemini 端点全覆盖，流式+工具+视觉 |
| 一行接入 | `npx @workweave/router` 自动改写 Claude Code/Codex/opencode/pi 配置 |
| 自托管完整栈 | Docker Compose：Postgres + 路由器 + 仪表盘，rk_ 路由密钥体系 |
| 可观测 | OTLP trace + /v1/analytics 路由决策 NDJSON 导出 |
| 健康探针 | /health 存活、/readyz 依赖就绪（等 sidecar 策略模型）、/validate 密钥校验 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | Go 1.25 |
| 存储 | PostgreSQL（路由决策与密钥） |
| 路由核心 | 机载嵌入器 + Avengers-Pro 聚类评分（sidecars/hmm 策略进程） |
| 前端 | 自带路由仪表盘（frontend/） |
| 部署 | Docker Compose / npm 安装器 / 托管版 |

---

## 项目亮点

### 学术方法落地为基础设施
把 2025 年路由研究（Avengers-Pro）工程化为可自托管的生产代理，论文→产品路径清晰，SEMANTICS.md 明确定义 session/round/turn/action/step 术语，工程沟通严谨。

### 动作粒度的成本手术
Agent 工作流中大量「读文件/格式化」类动作用便宜模型、「推理/写码」用旗舰模型，按动作而非回合路由是降本 40-70% 的关键，契合 agentic coding 的真实成本结构。

### BYOK + 可审计
密钥不出本机、决策全量可导出，对安全敏感企业比 SaaS 路由器（OpenRouter 等）更可控。

---

## 应用场景

### Claude Code / Codex 重度用户降本
端点一改，同一工作流里自动混用强弱模型，月账单直接砍半。

### 企业 Agent 平台的模型治理层
统一入口管理多供应商密钥与路由策略，OTLP 对接既有观测体系。

### 模型评测与成本分析
/v1/route 只返回决策不调上游，配合分析导出做 A/B 与成本归因。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 2,662 |
| 总 Forks | 77 |
| 今日新增 | +284 |
| 主要语言 | Go |

---

## 总结

把「该用哪个模型」从人工配置变成 50ms 内的自动决策，Weave Router 是 agentic coding 降本赛道上方法论最扎实的新选手。

---

*数据来源：GitHub 仓库 (workweave/router)，2026 年 8 月 30 日访问*

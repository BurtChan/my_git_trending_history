# AgentMemory 项目分析

## 项目名称

**AgentMemory** — AI 编码 Agent 的持久化记忆引擎，基于学术基准测试排名第一

- **GitHub**: [rohitg00/agentmemory](https://github.com/rohitg00/agentmemory)
- **官网**: https://agent-memory.dev
- **许可证**: Apache License 2.0

---

## 项目概述

AgentMemory 是专为 AI 编码 Agent 设计的持久化记忆引擎，解决了一个根本性问题：Claude Code、Cursor、Gemini CLI、Codex CLI 等编码 Agent 在会话结束后会丢失所有上下文，迫使开发者每次都要重新解释代码库、偏好和历史决策。AgentMemory 提供了一个自包含的记忆层，捕获每次交互、工具使用和观察，并通过语义搜索实现跨会话的即时检索。

系统在 LongMemEval-S（ICLR 2025 学术基准测试，用于评估聊天助手的长期记忆能力）上实现了 **95.2% 的检索准确率（R@5）**，显著优于仅使用 BM25 的 86.2%。与其他记忆方案相比，它还能节省 **高达 92% 的 token 消耗**——每年约 170K tokens，而 LLM 摘要方案需要约 650K tokens。这种高效性来源于其三流检索管道（BM25 + 向量 + 知识图谱）和每小时一次的合并清理机制，将原始观察压缩为语义记忆，自动合并重复项并审计一致性。

基于 **iii 引擎**（Worker/Function/Trigger 原语）构建，AgentMemory 以单进程方式运行，使用 SQLite 作为内部数据库，零外部依赖。它提供 12 个自动捕获钩子对接所有主流编码 Agent、51 个 MCP 工具和 121 个 REST 端点，还配备端口 3113 上的实时可视化查看器和 OpenTelemetry 可观测性集成。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **零外部数据库** | 自包含单进程运行，使用 SQLite 内嵌数据库，无外部依赖 |
| **12 个自动捕获钩子** | 对接 Claude Code、Cursor、Gemini CLI、Codex CLI、OpenCode 等所有主流 Agent |
| **三流检索** | BM25 + 向量嵌入 + 知识图谱搜索，精确语义召回（P50 < 20ms） |
| **记忆合并** | 每小时自动压缩原始观察为语义记忆，合并重复项并审计一致性 |
| **记忆生命周期** | 版本管理、替代关系和关系图谱 |
| **团队记忆** | 命名空间的共享与私有记忆，支持跨团队成员协作 |
| **隐私设计** | 存储前自动剥离密钥和 API Key 等敏感信息 |
| **自我修复** | 熔断器和 Provider 回退链，确保高可用性 |
| **引用溯源** | 每条记忆可追溯至其原始观察来源 |
| **Git 快照** | 记忆状态的版本管理、回滚和差异比较 |
| **会话回放** | JSONL 会话导入，完整重建历史会话 |
| **联邦同步** | 跨认证 HTTPS 的点对点记忆同步 |
| **MCP 支持** | 51 个 MCP 工具和 121 个 REST 端点（端口 3111） |
| **实时查看器** | 端口 3113 上的 Web 可视化界面，展示钩子、会话、记忆和图谱 |
| **OTEL 可观测性** | OpenTelemetry 集成，支持追踪和日志 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | TypeScript |
| **运行时** | Node.js |
| **核心引擎** | iii engine（iii-hq/iii）— Worker/Function/Trigger 原语 |
| **数据库** | SQLite（内嵌，零外部依赖） |
| **搜索** | BM25 + 向量嵌入 + 知识图谱 |
| **协议** | MCP（模型上下文协议）、REST API（121 端点） |
| **LLM Provider** | Anthropic（Claude）、Gemini、MiniMax、OpenRouter（环境变量自动检测） |
| **可观测性** | OpenTelemetry（OTEL） |
| **安装** | `npx -y @agentmemory/mcp`（一行命令） |
| **基准测试** | LongMemEval-S（ICLR 2025） |

---

## 项目亮点

### 基准测试领先的性能
95.2% 的检索准确率（R@5）在 LongMemEval-S（ICLR 2025）上排名第一，优于 BM25-only 方案（86.2%），并节省 92% token 消耗（~170K vs ~650K tokens/年）。

### 零摩擦部署
60 秒内启动，无需任何配置；一行 npm install 即可运行。无外部数据库，无框架开销。

### 全 Agent 兼容
适用于 Claude Code、Cursor、Gemini CLI、Codex CLI、OpenCode、OpenClaw、Hermes 等所有支持 MCP/REST/Hook 的 Agent，所有 Agent 共享同一记忆服务器。

### 亚毫秒级召回
P50 延迟低于 20ms，三流检索（BM25 + 向量 + 知识图谱）兼顾精度与速度。

---

## 应用场景

### AI 辅助软件开发
使用 AI 编码 Agent（Claude Code、Cursor 等）的开发者可以跨会话保持持久上下文，无需每次重新解释代码库、架构决策和编码偏好。

### 团队知识管理
命名空间的共享/私有记忆让开发团队能构建集体知识库，所有 AI Agent 都可从中获取信息，确保团队成员间的一致性。

### 企业 AI Agent 基础设施
自我修复架构（熔断器、回退链）、隐私设计（敏感信息剥离）和 OTEL 可观测性使其适合对可靠性和安全性有严格要求的企业部署。

### 会话审计与合规
引用溯源、Git 快照和审计追踪使组织能够将 AI Agent 的决策追溯至原始观察来源，支持合规和调试工作流。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | ~3,090 |
| **总 Forks** | ~319 |
| **许可证** | Apache License 2.0 |
| **主要语言** | TypeScript |
| **基准测试** | LongMemEval-S R@5: 95.2%（ICLR 2025） |
| **检索延迟** | P50 < 20ms |

---

## 总结

AgentMemory 是**专为 AI 编码 Agent 打造的持久化记忆引擎**，约 3,090 Stars。项目以 TypeScript 构建，基于 iii 引擎运行，使用 SQLite 内嵌数据库实现零外部依赖。其三流检索管道（BM25 + 向量 + 知识图谱）在 LongMemEval-S（ICLR 2025）基准上达到 95.2% 准确率，同时节省 92% 的 token 消耗。提供 12 个自动捕获钩子兼容所有主流编码 Agent，51 个 MCP 工具和 121 个 REST 端点，是 AI Agent 长期记忆领域的技术领先方案。

---

*数据来源：GitHub 仓库 (rohitg00/agentmemory)、agent-memory.dev，2026 年 5 月访问*

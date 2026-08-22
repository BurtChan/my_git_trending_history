# Apache Maka 项目分析

## 项目名称
**Apache Maka (Incubating)** — 本地优先的 AI Agent 桌面工作台
- **GitHub**: [apache/maka](https://github.com/apache/maka)
- **许可证**: Apache-2.0（Apache 孵化器项目）

---

## 项目概述
Maka 是一个进入 Apache 孵化器的本地优先（local-first）AI Agent 工作台：不只是聊天助手，而是在受控权限下检查项目、执行工具、产出 Artifact，并把模型消息、工具调用、工具结果、权限决策和终止事件全部记录为**只追加日志（append-only log）**。桌面版、终端 TUI、非交互 CLI 和评测主体都经由统一的 Runtime Host 执行。

项目 2026 年 5 月底创建，8 月 22 日首次登上 Trending（总 2,018 stars，单日 +148）。当前 macOS Apple Silicon 桌面版为早期公开发布，数据格式与 CLI 仍可能变化。仓库 3,593 commits，迭代极快，且提供了完整的中英双语 README/架构文档。

---

## 核心功能
| 功能 | 描述 |
|------|------|
| Agent Runtime | 多模型连接、流式输出、thinking、用量核算、provider 错误归一化 |
| 本地工具 | Read / Write / Edit / Bash / Glob / Grep，带 schema 校验与权限策略 |
| Runtime Event Log | 模型消息、Tool Call/Result、终止事实全量落日志；会话与恢复都是日志的投影 |
| 上下文管理 | Tool Result 修剪 + LLM 压缩改变下次推理所见，但不丢弃已记录证据 |
| 桌面工作台 | 会话分支/重试/搜索/重命名、Artifact 预览、权限与模型设置（Electron + React） |
| TUI/CLI | `maka` / `maka run`，与桌面版共享工作区和模型连接 |
| 评测 | `maka eval run`，声明式多臂实验，不可变 per-cell 尝试 |
| 备份恢复 | SQLite 在线备份 API + SHA-256 清单绑定的 Artifact 备份/校验/恢复 |

---

## 技术栈
| 组件 | 技术 |
|------|------|
| 语言 | TypeScript（monorepo packages/） |
| 桌面 | Electron + React |
| 存储 | SQLite（会话/Artifact 权威存储） |
| 工程化 | biome、knip、coderabbit、pr_agent、完整 e2e/smoke 测试 |

---

## 项目亮点
### "日志即运行时"架构
会话、UI、模型上下文、崩溃恢复全部是 append-only 事件日志之上的投影——把数据库领域 event sourcing 的思想引入 Agent 运行时，可审计、可回放。

### 上下文 ≠ 历史
Tool Result 修剪与压缩只影响"模型看到什么"，不删除"已发生什么"，为 Agent 可靠性提供了记录层与推理层的清晰分离。

### Apache 治理 + 双语文档
进入 ASF 孵化器意味着 vendor-neutral 的社区治理路线；中英文架构/贡献文档齐全，对中国开发者参与友好。

---

## 应用场景
### 本地敏感代码库的 AI 助手
数据默认留在本机，模型连接自选（云 API/本地模型/网关），适合不能上云的工程团队。
### Agent 行为审计与回放
全量事件日志使每次工具调用可追溯，满足合规/复盘需求。
### Agent 评测实验
声明式多臂评测设计，把 Maka 与外部竞品 Agent 放在同一基准下复现实验。

---

## Star 数据
| 指标 | 数值 |
|------|------|
| 总 Stars | 2,018 |
| 总 Forks | 240 |
| 今日新增 | +148 |
| 创建时间 | 2026-05-27 |

---

## 总结
Apache 孵化器里的本地优先 Agent 工作台，以"append-only 事件日志为运行时核心"的架构设计在同质化的 Agent 桌面应用中独树一帜，值得持续关注其孵化进展。

---

*数据来源：GitHub 仓库 (apache/maka)，2026 年 8 月访问*

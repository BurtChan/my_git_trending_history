# Beads 项目分析

## 项目名称

**Beads** — 为 AI 编码 Agent 提供记忆升级的分布式图谱 Issue 追踪器

- **GitHub**: [gastownhall/beads](https://github.com/gastownhall/beads)
- **许可证**: MIT

---

## 项目概述

Beads 是由知名工程师 Steve Yegge（Gas Town Hall 组织）发起的开源项目，旨在解决 AI 编码 Agent（如 Claude Code、Cursor、Windsurf 等）在长周期开发中丢失上下文和任务状态的痛点。传统的 AI Agent 通常依赖 Markdown 文件（如 TODO.md、PLAN.md）来记录任务计划，但这种方式在 Agent 重新启动或崩溃后会导致记忆丢失，且多 Agent 并行工作时容易产生 Git 冲突。Beads 通过构建一个基于版本化数据库的结构化 Issue 追踪系统，让 Agent 拥有了"持久记忆"。

项目采用 Dolt（一个支持 Git 式版本控制的 SQL 数据库）作为底层存储，所有任务和依赖关系以图谱形式组织，支持分支、合并和远程同步。这意味着 Agent 的任务状态可以像代码一样进行版本管理，多个 Agent 在不同分支上工作时也不会产生冲突。Beads 的核心理念是"Agent 优先"——所有的输出格式、API 设计都针对大语言模型的消费习惯进行了优化，而非面向人类 UI。

Beads 可以独立于 Git 运行（纯本地模式），也可以与 Git 深度集成。项目已发布至 v0.44.0，社区活跃，已有多个第三方集成工具（如 opencode-beads、Copilot 集成等），形成了围绕 Agent 记忆管理的生态雏形。

---

## 核心功能

- **持久化任务记忆**：Agent 的任务状态在重启和崩溃后依然保留
- **依赖感知图谱**：任务间通过 `relates_to`、`duplicates`、`supersedes`、`replies_to` 等关系链接，形成有向无环图
- **自动就绪检测**：`bd ready` 命令自动识别所有依赖已满足、可以立即执行的任务
- **零冲突合并**：基于哈希 ID 的设计确保多 Agent / 多分支并行工作无合并冲突
- **语义压缩（Compaction）**：对已关闭的旧任务进行语义摘要，节省上下文窗口
- **Issue 消息系统**：支持线程式消息、临时生命周期和邮件委托
- **JSON 输出模式**：所有命令支持 `--json` 输出，便于 Agent 直接解析
- **隐身模式（Stealth Mode）**：本地使用时不产生 Git 提交
- **嵌入式 / 服务器模式**：默认嵌入式运行（无需外部服务），也支持连接远程 Dolt 服务器
- **联邦支持（Federation）**：跨项目、跨 Agent 的任务协调能力

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Go |
| **数据库** | Dolt（版本化 SQL 数据库，支持单元格级合并和 Git 式分支） |
| **缓存** | SQLite（读取模型缓存） |
| **日志格式** | JSONL（任务日志） |
| **版本控制** | Git（可选集成） |
| **本地通信** | Unix Socket（bd.sock） |
| **npm 包** | `@beads/bd` |
| **安装方式** | Homebrew（macOS/Linux） |

---

## 项目亮点

### Agent-First 设计哲学
所有 API 输出专为 LLM 消费优化，而非人类 UI，大幅减少 Agent 的上下文消耗和理解负担。

### Git 即数据库
巧妙利用 Dolt 的 Git 式版本控制能力，将任务状态像代码一样管理，实现异步协作和状态追踪。

### 零冲突多 Agent 协作
哈希 ID + Dolt 单元格级合并，彻底解决多 Agent 并行工作时的冲突问题。

### "记忆衰减"机制
语义压缩功能自动摘要旧任务，模拟人类记忆的自然遗忘过程，有效管理有限的上下文窗口。

---

## 应用场景

### AI 编码 Agent 的持久记忆层
为 Claude Code、Cursor、Windsurf 等 AI 编码工具提供跨会话的任务记忆。

### 多 Agent 协作编排
在 Gas Town 等多 Agent 框架中，作为跨 Agent 的任务协调和状态共享平台。

### 大型项目任务分解与追踪
将复杂项目拆解为 Epic → Task 的层次结构，通过依赖图谱管理开发顺序。

### CI/CD 门控集成
通过 `bd gate` 命令与 GitHub Actions 等 CI/CD 系统集成，实现任务级别的流程控制。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 21,474 |
| **总 Forks** | 1,435 |
| **今日新增 Stars** | Trending 日榜上榜 |
| **许可证** | MIT |
| **创建时间** | 2025 年 |
| **主要语言** | Go |

---

## 总结

Beads 是当前 AI 编码 Agent 生态中最具创新性的基础设施项目之一，它以"给 AI 金鱼装上记忆"为核心理念，基于 Dolt 版本化数据库构建了一个 Agent 优先的分布式图谱 Issue 追踪系统，解决了 AI Agent 长周期开发中上下文丢失、多 Agent 协作冲突、任务依赖管理混乱等关键痛点，短短半年内即获得超过 21,000 Stars，成为 GitHub 上增长最快的 AI 开发工具之一，为 AI 编程时代的工程管理提供了一种全新的范式。

---

*数据来源：GitHub 仓库 (gastownhall/beads)，2026 年 4 月访问*

# TencentDB Agent Memory 项目分析

## 项目名称
**TencentDB Agent Memory** — 面向 AI Agent 的完全本地化长期记忆系统

- **GitHub**: [TencentCloud/TencentDB-Agent-Memory](https://github.com/TencentCloud/TencentDB-Agent-Memory)
- **许可证**: Custom（开源）

---

## 项目概述

TencentDB Agent Memory 是腾讯云开源的一个面向 AI Agent 的**完全本地化长期记忆系统**，通过四层渐进式记忆管线（4-tier progressive pipeline）实现从短期工作记忆到长期个性化记忆的完整覆盖，**零外部 API 依赖**，所有计算和存储均在本地完成。

该项目解决了当前 AI Agent 领域的一个核心痛点：Agent 缺乏跨会话的记忆能力，导致用户需要反复重复相同的信息和偏好。传统方案要么采用暴力式的历史累积（导致 token 爆炸），要么采用不可逆的有损摘要（丢失关键细节）。TencentDB Agent Memory 拒绝这两种极端，而是设计了一套**分层记忆架构**——符号记忆（Symbolic Memory）解决任务内信息过载，记忆分层（Memory Layering）解决跨会话经验传递。

项目的核心理念是："Memory is not about hoarding everything in the AI — it is about sparing humans from having to repeat themselves."（记忆不是在 AI 中囤积一切——而是让人免于重复自己。）在基准测试中，该项目表现出了显著的效果提升：WideSearch 任务成功率提升 51.52%，SWE-bench 成功率提升 9.93%，同时 token 消耗大幅降低（最高减少 61.38%）。

---

## 核心功能

### 1. 记忆分层（Memory Layering）——渐进式异构存储
- **短期上下文分层**：底层为原始工具输出（refs/*.md），中层为步骤级摘要（jsonl），顶层为轻量级 Mermaid 画布（仅此层保留在上下文中）
- **长期个性化分层（语义金字塔）**：L0 对话原文 → L1 原子事实 → L2 场景块 → L3 用户画像
- **技能生成分层**：执行轨迹 → 解决方案模式 → 可复用技能/SOP

### 2. 符号记忆（Symbolic Memory）——Mermaid 画布
将冗长的日志卸载到外部文件，仅保留轻量级 Mermaid 任务图在上下文中。Agent 通过 `node_id` 按需钻取完整内容，将上下文占用从数十万 token 压缩到几百 token。

### 3. 多平台支持
支持 OpenClaw 和 Hermes 两大 Agent 框架的即插即用集成，支持 Docker 一键部署。

### 4. 零外部 API 依赖
所有计算和存储完全本地化，无需连接任何外部 API，保障数据隐私和离线可用性。

### 5. 短期压缩引擎
基于可卸载（offload）机制，自动将冗余的中间工具输出压缩并外存，显著降低 token 消耗。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | TypeScript (84.2%), Python (7.5%), Shell (7.0%) |
| 向量存储 | SQLite + sqlite-vec |
| 可视化 | Mermaid 图表 |
| Agent 框架 | OpenClaw, Hermes |
| 部署方式 | Docker, 本地插件 |

---

## 项目亮点

### 显著的性能提升
在多项基准测试中，记忆插件带来了成功率的大幅提升和 token 消耗的大幅降低。WideSearch 成功率提升 51.52%，token 消耗减少 61.38%；长期记忆 PersonaMem 测试中成功率从 48% 跃升至 76%。这些结果是在**连续长会话**中测量的，而非孤立的单轮对话，更贴近真实使用场景。

### 创新的分层记忆架构
不同于传统的扁平向量存储方案，TencentDB Agent Memory 设计了一套三层异构存储体系——底层用数据库做全文检索（保存证据），顶层用人类可读的 Markdown 文件（保存结构）。这种设计在性能和可解释性之间取得了优秀的平衡。

### 完全本地化的隐私保护
零外部 API 依赖意味着所有用户数据（对话历史、用户画像、技能库）都存储在本地，不会泄露到任何第三方服务。这对于企业级部署和隐私敏感场景尤为重要。

### 渐进式披露（Progressive Disclosure）
Agent 只在上下文中保留最顶层的摘要画布（几百 token），通过 `node_id` 按需钻取下层细节。这种设计既保证了信息的完整性，又控制了上下文窗口的占用。

---

## 应用场景

### AI 编程助手的长程记忆
当开发者使用 Claude Code、Codex 等编程 Agent 时，Agent 可以跨会话记住项目结构、编码偏好、历史决策，避免重复解释相同的上下文。特别是在 SWE-bench 等代码任务中，记忆系统帮助 Agent 保持了更清晰的问题解决思路。

### 企业知识管理
企业可以将 Agent 作为知识助手使用，记忆系统自动从日常交互中提炼用户画像和技能库，形成可复用的组织知识资产。所有数据本地存储，满足企业合规要求。

### 个性化 AI 助手
长期记忆系统使 AI 助手能够记住用户的偏好、习惯和过往交互，从"每次都是全新开始"进化为"越用越了解你"的个性化体验。语义金字塔的四层结构确保了从原始对话到用户画像的信息无损提炼。

### 复杂多步骤任务
对于需要长时间连续工作的 AI Agent（如自动化运维、数据分析流程），短期记忆分层机制可以管理中间步骤的大量输出，防止上下文溢出，同时保持关键信息的可追溯性。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 7,355 |
| 🍴 Forks | 688 |
| 📝 今日新增 | 610 |
| 💻 主要语言 | TypeScript |
| 📅 创建时间 | 2026-04-07 |
| 📜 许可证 | Custom |

---

## 总结

TencentDB Agent Memory 是一个设计精良的 AI Agent 记忆系统，通过分层记忆架构和符号记忆机制，在性能提升（成功率最高 +51.52%）和成本降低（token 消耗最高 -61.38%）两个维度都取得了显著成果。其完全本地化的设计理念和对零外部 API 依赖的坚持，使其成为隐私敏感场景下的理想选择。作为腾讯云开源项目，它在企业级 AI Agent 基础设施方面提供了有价值的参考实现。

---

*数据来源：GitHub 仓库 (TencentCloud/TencentDB-Agent-Memory)，2026 年 7 月访问*

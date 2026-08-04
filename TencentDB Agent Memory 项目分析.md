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
| ⭐ Stars | 11,266 |
| 🍴 Forks | 972 |
| 📝 今日新增 | 250 |
| 💻 主要语言 | TypeScript |
| 📅 创建时间 | 2026-04-07 |
| 📜 许可证 | Custom |

---

## 总结

TencentDB Agent Memory 是一个设计精良的 AI Agent 记忆系统，通过分层记忆架构和符号记忆机制，在性能提升（成功率最高 +51.52%）和成本降低（token 消耗最高 -61.38%）两个维度都取得了显著成果。其完全本地化的设计理念和对零外部 API 依赖的坚持，使其成为隐私敏感场景下的理想选择。作为腾讯云开源项目，它在企业级 AI Agent 基础设施方面提供了有价值的参考实现。

---

*数据来源：GitHub 仓库 (TencentCloud/TencentDB-Agent-Memory)，2026 年 7 月访问*

---

## 📋 更新记录

### Update 1 — 2026-08-02

**更新原因**：Star 数显著增长，从 7.3k 增至 10k+，社区活跃度大幅提升。

**最新动态**：
- v2.0+ 大版本迭代发布，包含数据迁移工具等重要更新
- Agent Loadout 装备系统上线，支持为 Agent 配置记忆装备
- 四类记忆资产体系完善：Chat Memory（L0-L3 分层蒸馏）、Skill（可执行专家知识）、Wiki（带链接图的结构化知识）、CodeGraph（代码符号索引）
- 冷启动导入能力：支持从现有代码库导入 → CodeGraph，文档导入 → Wiki，对话导入 → Skills/Chat Memory
- 访问控制体系：支持 private/team/restricted/agent 四级权限
- 一人公司模式（one-person company model）支持

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 7,355 | 10,091 | +2,736 |
| 总 Forks | 688 | 972 | +284 |

---

## 更新 2 — 2026年8月3日

**更新原因**：单日新增 604 Star，总 Star 突破万级继续攀升至 10,786，OpenClaw 与 Hermes 集成引发广泛关注。

**最新 Star 数据**：

| 总 Stars | 10,091 | 10,786 | +695 |

**更新亮点**：
- 最近集成 OpenClaw 和 Hermes 支持，扩展了 Agent 生态兼容性
- 发布 Hub 资产路由系统，提升记忆资产的分发与管理效率
- 支持 PostgreSQL Protocol 和 REST API 访问，降低接入门槛，便于与现有数据基础设施整合
|- Forks 增至 1,023，社区参与度持续走高

---

## 更新 3 — 2026年8月3日（晚间数据）

**更新原因**：晚间再次确认 Trending 数据，Star 从 10,786 继续攀升至 11,266，单日累计增长突破 1,174 星，四层记忆架构和 OpenClaw 集成持续吸引关注

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 10,786 | 11,266 | +480 |
| 总 Forks | ~1,023 | 1,065 | +42 |

**更新亮点**：
- 单日 Star 增长持续加速，晚间数据再增 480 颗，累计今日 +1,174
- 四层记忆管道（工作记忆→情景记忆→语义记忆→长期记忆）架构设计持续获得认可
- 与 OpenClaw、Hermes 等 Agent 框架的集成效果显著，SWE-bench 成功率从 58.4% 提升至 64.2%
- PostgreSQL Protocol 和 REST API 双接入模式降低使用门槛
|- 完全本地化部署零外部 API 调用的隐私优势在 Agent 生态中差异化明显

---

## 更新 4 — 2026年8月4日

**更新原因**：连续第二天登上 Trending，今日 +602 星（Trending 页面数据），总星数从 10,786 增至 11,432，Agent 记忆赛道持续升温

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 10,786 | 11,432 | +646 |
| 总 Forks | 1,065 | 1,079 | +14 |

**更新亮点**：
- 连续登上 Trending，总 Star 数从 10,786 增长至 11,432（+646），单日增速保持稳定
- 四类记忆资产体系（Chat Memory、Skill Library、Wiki、CodeGraph）获得社区广泛认可
- L0-L3 分层记忆管道（会话→原子事实→情景→人格）架构设计持续引领行业方向
- 与 OpenClaw、Hermes 等主流 Agent 框架的集成生态持续扩展
- Agent Memory 赛道 2026 年持续升温（mem0 报告显示架构成熟度显著提升），TencentDB 凭借完全本地化零外部 API 的差异化定位脱颖而出

---

## 更新 5 — 2026年8月4日（晚间数据）

**更新原因**：连续多日 Trending，晚间数据确认 Star 从 11,432 增长至 11,999（+567），Agent 记忆赛道热度不减

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 11,432 | 11,999 | +567 |
| 总 Forks | 1,079 | 1,136 | +57 |

**更新亮点**：
- 连续多日 Trending 推动 Star 突破 11,900，累计从 7,355 增长至 11,999（+4,644，增长 63%）
- v1.0.1 版本已发布，OpenClaw 插件集成 `@tencentdb-agent-memory/memory-tencentdb` 支持一键安装配置
- 四类记忆资产体系（Chat Memory L0-L3、Skill Library、Wiki、CodeGraph）在 Agent 社区持续获得验证
- PostgreSQL Protocol 和 REST API 双接入模式，便于与现有数据基础设施整合
- 作为 Agent Memory 赛道的完全本地化方案，隐私零外部 API 调用的差异化定位持续吸引企业用户

### 更新 — 2026年8月4日（晚间更新）

**更新原因**：项目再次登上 GitHub Trending 榜单，Star 数从 11,999 增长至 12,093（+94），日增 1,090 颗 Star

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 11,999 | 12,093 | +94 |
| 总 Forks | 1,136 | 1,144 | +8 |

**更新亮点**：
- 连续多日 Trending 推动 Star 突破 12,000 里程碑，累计从 7,355 增长至 12,093（+4,738，增长 64%）
- 日增 1,090 颗 Star 排名 Trending Top 5，Agent Memory 赛道热度不减
- v1.0.1 版本已发布，OpenClaw 插件集成 `@tencentdb-agent-memory/memory-tencentdb` 支持一键安装配置
- 四类记忆资产体系（Chat Memory L0-L3、Skill Library、Wiki、CodeGraph）在 Agent 社区持续获得验证
- 作为 Agent Memory 赛道的完全本地化方案，隐私零外部 API 调用的差异化定位持续吸引企业用户

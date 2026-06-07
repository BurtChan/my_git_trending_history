# pg_durable — PostgreSQL 原生持久化执行引擎

## 概述

**pg_durable** 是微软开源的 PostgreSQL 扩展，在数据库内部原生实现持久化执行（Durable Execution）。它基于 Rust 和 pgrx 框架构建，将传统上需要 Temporal、AWS Step Functions 等外部编排服务的容错工作流能力，直接带入了 PostgreSQL。

项目的核心理念是：**你只需编写 SQL，pg_durable 负责其余一切**——队列管理、状态追踪、崩溃恢复、步骤协调、自动重试，全部在数据库内自动完成。无需 Redis、无需 Kubernetes、无需外部编排集群，仅作为 PostgreSQL 扩展运行，通过后台工作进程（Background Worker）驱动执行。

该项目源自微软 Azure HorizonDB（基于 PostgreSQL 的云数据库服务）的 Durable Functions 能力，现已作为独立开源扩展面向社区发布，当前处于 **Preview** 阶段。开源首日即在 Hacker News 获得 265+ 热度，社区反响强烈。

**项目地址：** https://github.com/microsoft/pg_durable
**官方文档：** https://microsoft.github.io/pg_durable/
**许可证：** PostgreSQL License

## 核心功能

### SQL 原生 DSL — 用操作符编排工作流

pg_durable 提供了一套极简的 SQL DSL，通过可组合的操作符定义函数图：

- **`~>` 顺序链接**：将多个步骤串联执行，上一步输出自动传递到下一步
- **`|=>` 变量绑定**：将步骤输出绑定到命名变量，供后续步骤引用（如 `$batch`、`$embeddings`）
- **`&` 并行扇出**：多个步骤并行执行
- **`df.start()`**：初始化并启动工作流
- **`df.join()`**：显式并行汇合
- **`df.if()`**：条件分支
- **`df.loop()`**：扇出/循环控制
- **`df.http()`**：从 SQL 直接调用 HTTPS 端点（白名单机制）
- **`df.result()`**：查询工作流执行结果

### 持久化与容错 — 默认持久

每个步骤的执行状态都作为检查点（Checkpoint）写入 PostgreSQL 专用 `duroxide.*` Schema。当数据库崩溃、重启或某步骤失败时，工作流会从**最后一个成功检查点**自动恢复，而非从头重跑——避免了重复工作、资金浪费和潜在的数据不一致。

### 自动重试 — 精准恢复

内置重试逻辑，步骤失败时**仅重试该步骤**，其余工作流继续推进，不会因为单个失败导致整体回滚。

### SQL 原生可观测性

所有工作流状态均存储在 PostgreSQL 表中，可通过标准 SQL 查询执行历史、检查步骤输出、调试失败原因——无需外部监控面板或仪表盘。

### 调度与定时任务

支持 Cron 调度，定时轮询 API、归档记录、同步数据等场景。循环工作流在数据库重启后自动恢复执行。

## 技术栈

| 技术组件 | 说明 |
|---------|------|
| **语言** | Rust |
| **扩展框架** | pgrx（PostgreSQL Rust 扩展开发框架） |
| **运行时引擎** | duroxide（Rust 持久化任务框架，处理确定性重放和检查点） |
| **状态存储** | duroxide-pg（PostgreSQL 状态提供者，持久化至 `duroxide.*` Schema） |
| **执行模型** | PostgreSQL Background Worker（后台工作进程） |
| **支持版本** | PostgreSQL 17、PostgreSQL 18 |
| **分发方式** | .deb 包（Debian/Ubuntu）+ Docker 支持 |
| **托管平台** | Azure HorizonDB（内置 pg_durable 的托管 PostgreSQL 云服务） |
| **许可证** | PostgreSQL License |

## 亮点

### 1. 架构范式的革新 — "数据库即工作流引擎"

传统方案中，构建容错工作流需要引入外部编排服务（Temporal、AWS Step Functions、Azure Durable Functions、Restate 等），这意味着额外的集群运维、网络通信和数据一致性挑战。pg_durable 直接将持久化执行嵌入数据库，**架构复杂度趋近于零**——你的 PostgreSQL 既是数据存储，也是工作流引擎，两者合二为一。

### 2. SQL DSL 的优雅设计

嵌入流水线的完整示例仅需数行 SQL：

```sql
SELECT df.start(
  'SELECT id, content FROM documents WHERE embedded = false LIMIT 500'
  |=> 'batch'
  ~> 'SELECT call_embedding_api($batch)'
  |=> 'embeddings'
  ~> 'INSERT INTO document_embeddings SELECT unnest FROM unnest($embeddings::vector[])'
  ~> 'UPDATE documents SET embedded = true WHERE id IN (SELECT id FROM jsonb_array_elements($batch))'
);
```

对比传统方案需要 300+ 行的队列管理、轮询函数、手动重试、步骤依赖追踪等样板代码，pg_durable 的 DSL 将复杂度压缩了两个数量级。变量通过 `$var_name` 自动在步骤间流动，开发者只需关注业务 SQL。

### 3. 原子化备份 — 相比外部编排器的关键优势

使用 `pg_basebackup` 或 PITR（时间点恢复）时，**工作流状态与业务数据原子化备份**。传统方案中，Temporal 等外部编排器的状态与数据库数据分别备份，恢复后可能出现两者不一致的情况。pg_durable 消除了这一根本性难题。

### 4. 微软在 PostgreSQL 生态的战略投入

pg_durable 是微软持续加大对 PostgreSQL 投入的最新体现。通过 Azure HorizonDB，微软将 pg_durable 与企业级能力（128TB 弹性存储、3072 vCore 扩展、Microsoft Defender 威胁检测、Entra ID 身份管理、DiskANN 向量搜索等）深度集成，打造了差异化的 PostgreSQL 云服务。项目本身完全开源，无供应商锁定。

### 5. AI 时代的数据库原生编排

在 AI 工作流（向量嵌入、数据摄取、RAG 流水线）蓬勃发展的背景下，pg_durable 的"数据不动、计算就数据"理念尤为契合——嵌入 API 调用与数据库写入在同一事务上下文中编排，天然避免数据在不同系统间搬运的复杂性和延迟。项目还内置了 `pg-durable-sql` Agent 技能，让 GitHub Copilot 等 AI 助手能直接生成正确的持久化函数 SQL。

## 典型场景

### 场景一：AI 向量嵌入流水线

批量读取未嵌入文档 → 调用外部嵌入 API → 将向量写入嵌入表 → 标记完成。整个链路持久化，API 调用失败时仅重试失败步骤，数据库崩溃后从断点恢复。

### 场景二：多数据源 ETL 流水线

串联 "数据清理 → 格式转换 → 质量校验 → 加载入库"，每步检查点化。支持条件分支——校验失败时走告警流程，成功时继续加载。

### 场景三：并行聚合与仪表盘刷新

使用 `&` 操作符同时执行多个聚合查询（用户数、订单数、交易额），全部完成后自动刷新仪表盘，一步到位。

### 场景四：扇出-聚合模式（Fan-out/Fan-in）

将大批量任务拆分为多个并行工作单元，全部完成后汇总结果。适用于批量邮件发送、分布式数据处理等场景。

### 场景五：外部 API 工作流 + 人工审批

自动化审批常规操作，高风险操作暂停等待人工审批后继续执行——工作流状态在等待期间持久化存储，审批通过后无缝恢复。

### 场景六：数据库维护自动化

自动检测 autovacuum 阻塞、表膨胀、事务号回卷风险等，触发告警或等待 DBA 审批后自动修复，全程持久化保障。

## Star 数据

| 指标 | 数据 |
|------|------|
| **总 Star 数** | ⭐ 1,338 |
| **总 Fork 数** | 🍴 27 |
| **今日新增 Star** | 📈 +314 |
| **主要语言** | Rust |
| **创建时间** | 2026-02-13 |
| **项目状态** | Preview（API 可能变更） |
| **开源协议** | PostgreSQL License |

## 总结

pg_durable 是微软在 PostgreSQL 生态中的一次极具创新性的尝试。它将持久化执行——这一传统上需要独立编排服务才能实现的企业级能力——以 PostgreSQL 扩展的形式内嵌到数据库中，开创了"数据库即工作流引擎"的新范式。

其核心价值在于：

1. **架构简化**：消除对外部编排服务（Temporal、Step Functions 等）的依赖，运维复杂度大幅降低
2. **开发效率**：SQL DSL 将 300+ 行样板代码压缩为数行，变量自动流动，开发者专注业务逻辑
3. **数据一致性**：工作流状态与业务数据原子化备份，从根本上解决恢复一致性问题
4. **AI 友好**：天然适配 AI 流水线场景，"数据不动、计算就数据"的理念契合现代数据工程实践

当然，项目当前仍处于 Preview 阶段，存在一定局限性：缺乏 Web UI 和内置监控面板、测试体系尚不成熟、多主（Multi-master）扩展方案尚未就绪、且更适合以 SQL 为中心的工作流而非跨服务编排场景。对于需要语言 SDK（Python/TypeScript）或复杂可观测性的团队，Temporal 和 DBOS 仍是更成熟的选择。

但随着 PostgreSQL 持续"吞噬"传统中间件能力（时序、向量、队列，如今又加上工作流编排），pg_durable 代表了一个值得关注的趋势：**未来越来越多的基础设施能力将以扩展的形式直接嵌入数据库，而非作为独立服务运行。** 对于已经在 PostgreSQL 上构建应用的数据和 AI 团队，pg_durable 值得持续关注和早期试用。

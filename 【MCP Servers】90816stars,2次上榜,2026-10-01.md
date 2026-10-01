# MCP Servers 项目分析

## 项目名称

**MCP Servers** — Model Context Protocol 官方参考服务器集合（Anthropic 主导）

- **GitHub**: [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)
- **许可证**: Apache-2.0（新贡献）/ MIT（既有代码）
- **开发语言**: TypeScript（部分 Python）
- **Star 数**: 90,712（Trending 当日 +48）

---

## 项目概述

MCP（Model Context Protocol，模型上下文协议）是 Anthropic 于 2024 年底提出的开放标准，被誉为「AI 界的 USB-C」：它为 LLM 应用与外部数据源、工具之间定义了统一的连接协议。本仓库是 MCP 官方组织维护的**参考实现集合**，包含由 MCP 指导小组直接维护的一小组参考服务器，以及通往社区生态的资源入口，累计提交超过 4,100 次，90K+ Stars 使其成为 AI 工具生态中最具标志性的仓库之一。

仓库当前包含 7 个活跃参考服务器：**Everything**（协议全特性测试）、**Fetch**（网页抓取与 LLM 友好转换）、**Filesystem**（受控文件操作）、**Git**（仓库读取/搜索/操作）、**Memory**（基于知识图谱的持久记忆）、**Sequential Thinking**（结构化反思式推理）、**Time**（时区转换）。早期的一批服务器（GitHub、GitLab、Google Drive、PostgreSQL、Puppeteer、Slack、SQLite 等）已归档至 `servers-archived` 仓库，官方定位收缩为「教学示例」而非生产方案——生产环境的服务器目录职责已移交 **MCP Registry**（registry.modelcontextprotocol.io）。

需要强调的是：这些服务器是演示 MCP 特性与 SDK 用法的**参考实现**，官方明确提示开发者按自身威胁模型评估安全要求，而非直接当生产件使用。

---

## 核心功能

| 服务器 | 能力 |
|------|------|
| **Everything** | 覆盖 prompts/resources/tools 全特性的参考与测试服务器 |
| **Fetch** | 抓取网页内容并转换为高效适配 LLM 的格式 |
| **Filesystem** | 带可配置访问控制的安全文件读写 |
| **Git** | 读取、搜索与操作 Git 仓库 |
| **Memory** | 基于知识图谱的跨会话持久记忆 |
| **Sequential Thinking** | 通过思维序列实现动态反思式问题求解 |
| **Time** | 时间与时区转换 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | TypeScript（npx 分发）、Python（uvx/pip 分发） |
| 协议 | Model Context Protocol（JSON-RPC 2.0 基础） |
| 官方 SDK | C#/Go/Java/Kotlin/PHP/Python/Ruby/Rust/Swift/TypeScript 十门语言 SDK |
| 发布 | OIDC 可信发布（CI 直发 npm，无需 registry token） |

---

## 项目亮点

### 十门语言官方 SDK 矩阵
MCP 官方同时维护 C#、Go、Java、Kotlin、PHP、Python、Ruby、Rust、Swift、TypeScript 十个 SDK，本仓库的服务器即是各 SDK 的示范用法——协议标准的「参考实现 + SDK 文档」双重角色。

### 从大杂烩到注册表化的生态治理
早期仓库收录数十个第三方服务器导致维护与安全压力，官方果断将归档服务器迁移至 `servers-archived`、把生态目录职责交给 MCP Registry，本仓库只保留指导小组维护的少量参考件——这是开源项目「做减法」的典型案例。

### 教学定位的安全自觉
README 显著位置警告参考实现非生产就绪，提示开发者自行实现安全防线；配合 SECURITY.md 与 OIDC 可信发布流程，安全工程贯穿始终。

---

## 应用场景

### 学习 MCP 协议开发
通过阅读 Filesystem/Git 等参考服务器源码，快速掌握 resources、tools、prompts 三类原语的实现方式。

### 为 AI 助手配备标准工具
用 `npx -y @modelcontextprotocol/server-memory` 一行命令即可给 Claude Desktop 等 MCP 客户端挂上持久记忆或 Git 操作能力。

### 构建自有服务器的前置调研
基于 Everything 服务器做协议一致性测试，再参照 Fetch 的 LLM 友好转换模式构建领域专用服务器。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ 总 Stars | 90,816 |
| 🍴 Forks | 11,723 |
| 📈 Trending 当日新增 | +104 |
| 历史提交数 | 4,189 |

> 注：MCP 已被 OpenAI、Google 等主要 AI 厂商采纳为事实标准，本仓库作为协议「源头仓库」长期处于高位 Star、低日增的稳态，本次上榜属协议生态热度回升的反映。

---

## 📋 更新记录

### 更新 1 — 2026 年 10 月 1 日（连续第二日登上 Trending）

**更新原因**：连续第二日登上 Trending，Star 90,712 → 90,816（+104，API 口径），协议源头仓库热度回升延续。

**最新动态**：
- 官方 Registry（registry.modelcontextprotocol.io）保持每日数十款服务器上新的节奏，9 月 30 日单日即有 GitLab MCP、IDE for agents 等多款新服务器入库，生态供给侧持续繁荣。
- 2026-07-28 版规范持续落地：Tasks 移入 `io.modelcontextprotocol/tasks` 扩展、动态客户端注册（DCR）正式弃用转向 CIMD、确立十二个月最低弃用窗口，协议治理走向成熟。
- 企业侧对注册表、审批与审计层的需求上升，「registry 化治理」与本仓库从大而全服务器合集转向参考实现 + 注册表分发的历史方向互相印证。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 90,712 | 90,816 | +104 |
| 总 Forks | 11,717 | 11,723 | +6 |

**核心变化概要**：
- Star 90,712 → 90,816（+104），连续两日在榜，协议热度回升
- 官方 Registry 每日数十款服务器上新，供给侧繁荣
- 2026-07-28 规范（Tasks 扩展化、DCR→CIMD）推动生态标准化

## 总结

MCP Servers 是 AI 工具调用协议标准化的源头仓库——它以 7 个精炼的参考服务器和十门语言 SDK，定义了 LLM 连接外部世界的「官方姿势」；其从大而全转向注册表化治理的历程，本身就是 AI 开源生态走向成熟的缩影。

---

*数据来源：GitHub 仓库 (modelcontextprotocol/servers)，2026 年 10 月 1 日访问*
*首次分析：2026 年 9 月 30 日 | 最近更新：2026 年 10 月 1 日*

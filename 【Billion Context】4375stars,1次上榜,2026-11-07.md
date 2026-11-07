# Billion Context 项目分析

## 项目名称
**Billion Context** — 让 AI 编码会话跑一个月、吞吐数十亿 token 的上下文压缩插件
- **GitHub**: [ranxianglei/billion-context](https://github.com/ranxianglei/billion-context)
- **许可证**: MIT + 附加署名条款（产品化使用须在官网/文档标注并回链）

---

## 项目概述

Billion Context（bili）是一个上下文压缩插件，宣称「billion-context is all you need」：让单次 AI 会话持续一个月、累计处理数十亿 token，同时把 100K 的小上下文窗口用出大窗口的效果，整体 token 消耗省 5 倍。它瞄准的是当前 AI 编码工作流中最现实的矛盾——长会话、大仓库与有限的上下文窗口/高昂的 token 成本之间的落差。

项目以插件形式接入多种 Agent 客户端：内置 Claude Code 插件（.claude-plugin）、Codex 插件、Hermes 插件（hermes-plugin/ 目录）、pi/omp/opencode 客户端侧插件，以及独立的 billion-context-pi 与 opencode-acp 发行形态。核心压缩内核在 kernel/ 与 src/ 中实现，配有 paper/（方法论论文）、proof/ 与 verif/（验证材料）、500+ 通过的 mock 测试套件。

工程完成度颇有野心：提供统一存储（unified store，shadow/full 两级）、会话文件生命周期管理（可选 GC、归档/恢复 CLI）、CC content store、面板 HTTP 端点（存储 gc/restore）、完善的配置文档（中英双语 README/CONFIGURATION/TECHNICAL-NOTES）与审计日志。项目直言当前仍处早期——协议与压缩逻辑已过 mock 测试，真机集成测试是下一里程碑。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 月级单会话 | 单会话跨月持续工作，累计数十亿 token 不丢上下文 |
| 小窗口等效 | 100K 上下文窗口即可获得接近大窗口的工作记忆 |
| 省 5 倍 token | 压缩后整体 token 消耗约为原始的 1/5 |
| 多客户端插件 | Claude Code / Codex / Hermes / pi / omp / opencode 全覆盖 |
| 统一存储与 GC | 会话文件 opt-in 清理（BILI_SESSION_GC，默认关闭，双重条件才删+审计日志） |
| 存储维护 CLI | `archive` / `restore` / `gc` 本地直接维护 sessions 目录，支持 --dry-run 与 --json |
| 中英双语文档 | README、配置、技术笔记、会话/消息身份规范均有中文版 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | TypeScript（Node.js） |
| 形态 | Agent 客户端压缩插件（dsh-plugin 生态）+ 协议代理（cooperative-proxy） |
| 存储 | 统一存储（index.db + sessions 目录 + archive.jsonl，shadow/full 模式） |
| 质量 | 500+ mock 测试、proof/verif 验证材料、advisories 安全公告流程 |
| 发行 | npm、Docker、客户端内置插件（dist/agent/*.js） |

---

## 项目亮点

### 直击 Agent 长会话的最大痛点
上下文窗口与 token 成本是所有 AI 编码工作流的硬约束。与其等待模型厂商把窗口做大，Billion Context 选择在客户端侧做分层压缩——思路与「上下文工程」趋势完全同频，且给出了可量化的收益承诺（100K 窗口够用、省 5 倍）。

### 生态覆盖罕见的广度
同时适配 Claude Code、Codex、Hermes、pi、omp、opencode 六种客户端，并提供统一压缩内核。这意味着用户换 Agent 工具不用换压缩方案，长会话资产（会话文件、压缩缓存）可以跨客户端延续。

### 工程纪律大于营销话术
默认不删任何用户数据（GC opt-in）、压缩会话永不删除、每次删除审计留痕、删除条件双校验（超期且从未压缩或请求体极小）；配套 advisory 流程、dry-run 维护命令、中英完整文档。对一个「帮你压缩记忆」的项目来说，数据安全立场是关键加分项。

### 开源 + 署名条款的可持续模式
MIT 加一条署名附加条款：产品化的使用者须在可见位置标注使用了 billion-context 并回链仓库。这既保持了开源自由度，又为项目争取应有的可见度——对依赖口碑传播的基础设施项目是聪明的取舍。

---

## 应用场景

### 长周期复杂项目开发
跨数周的大重构、多模块迁移：单会话连续工作一个月，模型始终保有完整任务记忆，不必反复「重新理解项目」。

### Token 成本敏感的日常编码
API 按量付费的个人开发者与小团队，用 5 倍 token 压缩显著降低 Claude Code/Codex 日常开销。

### 大仓库代码问答与巡检
在上下文装不下的大代码库里做持续导航、审查与自动化巡检，压缩层把关键上下文保持在 100K 窗口内。

### 多客户端工作流统一
同时使用多个 Agent CLI 的用户，用同一压缩底座获得一致的长会话体验与可迁移的会话存储。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 4,375 |
| 🍴 Forks | 357 |
| 📈 今日新增 | 185 |
| 💻 主要语言 | TypeScript |
| 📄 许可证 | MIT + 附加署名条款 |
| 📅 创建时间 | 2026-08-06 |

---

## 总结

Billion Context 用客户端侧压缩把「小窗口跑月级会话」变成可落地的工作流，是上下文工程赛道里工程完成度和生态覆盖都突出的选手；3 个月 4,300+ Stars 的增长说明「省 token + 长记忆」正是 AI 编码用户的刚需，值得使用 Claude Code/Codex 重度工作流的团队试用观察。

---

*数据来源：GitHub 仓库 (ranxianglei/billion-context)，2026 年 11 月访问*

# Reverse Skill 项目分析

## 项目名称
**Reverse Skill** — AI 驱动的逆向工程与安全研究技能路由包
- **GitHub**: [zhaoxuya520/reverse-skill](https://github.com/zhaoxuya520/reverse-skill)
- **许可证**: MIT（主项目）、CTF-Sandbox-Orchestrator 使用 GPL-3.0

---

## 项目概述
Reverse Skill 是一个面向 AI 代码代理（Claude Code、Codex CLI、Cursor、Cline、Kiro 等）的逆向工程、授权渗透测试和安全研究技能路由包。它通过智能路由机制，将 AI 代理自动引导到正确的方法论、工具链和工作流，覆盖 APK 逆向、二进制分析、前端 JS 加密、CTF 挑战、漏洞利用开发等 20 余种安全场景。

项目的核心价值在于解决了一个普遍痛点：AI 代码代理在面对逆向工程任务时，往往不知道该使用 jadx、apktool、Frida、IDA 还是 BurpSuite 等工具。Reverse Skill 通过规则引擎和场景路由矩阵，让 AI 代理像经验丰富的安全研究员一样选择正确的工具链和操作流程，同时通过自动进化知识库积累经验、避免重复犯错。

---

## 核心功能

| 功能模块 | 描述 |
|----------|------|
| **智能路由引擎** | MASTER-ROUTING / master-route.ps1 根据任务类型自动分发到对应安全场景技能 |
| **20+ 安全场景覆盖** | APK 逆向、iOS 逆向、二进制分析、JS 逆向、恶意软件分析、渗透测试、CTF、固件安全等 |
| **工具链自动引导** | 自动检测本地已安装的安全工具（jadx、Frida、IDA、radare2、nmap 等）并按需自举 |
| **知识库自进化** | 通过 field-journal 记录每次操作的经验，形成可复用的安全研究知识库 |
| **案件管理流程** | case-init 初始化案件目录，包含 scope 定义、时间线、证据链和工作项 |
| **CTF 沙箱编排** | CTF-Sandbox-Orchestrator 包含 40+ 子技能，自动编排 CTF 解题流程 |
| **报告生成** | 自动生成 Evidence → Finding → Path 结构化分析报告 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心分析 | IDA Pro、radare2、Ghidra |
| 脚本语言 | Python、PowerShell、Bash、Node.js |
| 移动逆向 | Java/JDK（jadx、apktool）、Frida |
| 容器化 | Docker |
| 平台支持 | Windows、Linux、macOS、Kali Linux |
| 协议分析 | MCP Server 集成 |

---

## 项目亮点

### 场景全覆盖的技能路由
Reverse Skill 覆盖了从 APK 逆向到 EDR 绕过、从 OLLVM 去混淆到供应链安全分析的 20 余种场景，每种场景都有独立的技能目录和工具链配置。这种全面性在开源安全工具中极为罕见——通常安全工具只专注于某一领域，而 Reverse Skill 提供了一站式的 AI 辅助安全研究平台。

### 多平台工具链自动检测
项目内置 refresh-tool-index 脚本（支持 Windows PowerShell 和 Linux Bash），可自动扫描本机已安装的安全工具并生成 tool-index.md 状态文件。AI 代理据此知道哪些工具可用，避免尝试调用未安装的工具导致失败。

### 案件全生命周期管理
从 case-init 创建案件目录（含 scope.md 定义授权范围和网络配置），到 ops/ 目录下的证据链管理和角色分工，再到 timeline 工作项追踪，Reverse Skill 将安全研究的最佳实践融入 AI 代理的工作流中，确保操作规范性和可追溯性。

---

## 应用场景

### AI 辅助安全研究
安全研究员使用 Claude Code 或 Cursor 时，Reverse Skill 让 AI 自动选择正确的逆向工具链（如分析 APK 时引导到 jadx + Frida 流程），大幅降低 AI 在安全领域的误操作率。

### CTF 竞赛辅助
CTF-Sandbox-Orchestrator 包含 40+ 子技能，可自动编排 CTF 解题流程，从逆向到利用开发一站式覆盖。

### 企业安全审计
通过 scope.md 定义授权范围和网络配置，结合证据链管理和结构化报告生成，适用于企业级的授权渗透测试场景。

### 安全工具学习和教学
内置 Python Lab 和详细的场景文档，安全初学者可以借助 AI 代理学习各种逆向工程和渗透测试工具的使用方法。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 11,584 |
| 🍴 Forks | 1,759 |
| 📝 语言 | PowerShell |
| 📄 许可证 | MIT |
| 📅 创建时间 | 2025 年 |

---

## 总结
Reverse Skill 是目前最全面的 AI 辅助安全研究工具集，通过智能路由将 AI 代码代理的安全能力提升到专业水平。它不仅覆盖了逆向工程和渗透测试的各个领域，还通过案件管理、知识进化、报告生成等功能构建了完整的安全研究工作流，是 AI 时代安全工具链的一次重要创新。

---

*数据来源：GitHub 仓库 (zhaoxuya520/reverse-skill)，2026 年 8 月 2 日访问*

---

## 更新记录

### 更新 1 — 2026 年 8 月 1 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
- Reverse Skill 于 2026 年 7 月 18 日正式发布 v1.0.0 版本，标志着首个正式版的发布里程碑
- 社区活跃度显著提升，新增多个 field-journal 实战案例（包括 Electron Bytenode 特权更新链分析、Windows 24H2 逆向环境兼容性测试等）
- 近期 PR 活跃：新增 P0 scope 安全门控、Burp MCP 集成、Codex frontmatter 支持等改进
- 新增 PRIMARY bash 对等实现和安装渠道优化，改善跨平台兼容性
- 支持场景已扩展至 20+，覆盖 APK 逆向、二进制分析、CTF 竞赛、固件渗透、供应链安全等

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 10,113 | 11,089 | +976 |
| 总 Forks | 1,594 | 1,594 | — |

**核心变化概要**：
- 正式发布 v1.0.0，从实验项目转为稳定可用
- 社区贡献活跃，新增安全门控和 Burp MCP 集成
- 实战案例持续积累，覆盖更多逆向场景

### 更新 2 — 2026 年 8 月 2 日（连续 Trending）
**更新原因**：连续登上 Trending，单日新增 1,360 星，社区增长势头强劲

**最新动态**：
- 连续两天登上 GitHub Trending 榜单，单日星增 1,360 创近期新高
- v1.0.0 正式版后社区活跃度持续攀升，总星数突破 11.5k
- 20+ 场景技能矩阵进一步完善，涵盖 APK 逆向、IDA、radare2、JS 逆向、.NET、固件渗透、CTF、pwn chain、EDR 绕过、LLM 安全、供应链安全等
- MASTER-ROUTING.md + master-route.ps1 作为 PRIMARY 快速路由入口，提升技能分发效率
- case-init 工具链和 field-journal 知识闭环持续优化
- Ops contracts 完善：Scope/授权门控、Evidence→Finding→Path 证据链、角色分工、时间线追踪
- CTF-Sandbox-Orchestrator 集成 40+ 子技能，覆盖主流 CTF 赛题类型
- 跨平台支持：Windows 主力平台，Linux/macOS/Kali 支持路径已打通

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 11,089 | 11,584 | +495 |
| 总 Forks | 1,594 | 1,759 | +165 |

**核心变化概要**：
- 连续 Trending 驱动社区爆发式增长，单日 1,360 星增量创项目新高
- Fork 增长加速（+165），反映开发者参与和二次开发热情高涨
- 场景技能矩阵和工具链引导体系日趋成熟

### 更新 3 — 2026 年 8 月 3 日（连续 Trending）
**更新原因**：连续第三天登上 GitHub Trending，单日新增 1,145 星，社区增长势头持续强劲

**最新动态**：
- 连续第三天登上 GitHub Trending 榜单，单日星增 1,145 维持高位
- 三天内累计新增约 1,767 星（从 11,089 到 12,856），增长 16%
- Fork 数从 1,759 增至 1,930（+171），开发者参与度持续攀升
- 项目作为 AI Agent 安全技能路由的定位获得社区广泛认可，在 Claude Code、Codex CLI、Cursor 等 AI 代理生态中的集成案例持续增长
- MASTER-ROUTING 快速路由入口和 case-init 案件管理工作流在安全研究社区中口碑良好

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 11,584 | 12,856 | +1,272 |
| 总 Forks | 1,759 | 1,930 | +171 |

**核心变化概要**：
- 连续第三天 Trending，三天累计增星 1,767，增长 16%
- Fork 加速增长（+171），反映开发者参与和二次开发热情持续高涨
- AI 代理安全技能路由的差异化定位日趋巩固

### 更新 4 — 2026年8月3日（晚间数据）

**更新原因**：连续多日登上 Trending，晚间数据显示 Star 持续增长至 14,725，较上次记录增长 1,869 星，网络安全 AI 技能路由赛道爆发式增长

**最新动态**：
- Star 数从 12,856 暴增至 14,725（+1,869），单日增速创项目历史新高
- Fork 数从 1,930 增至 2,172（+242），开发者参与度同步爆发
- 连续多日 Trending 驱动下，四天累计增星超 3,600 颗，增长 32%
- 20+ 场景技能矩阵（APK 逆向、IDA、radare2、JS 逆向、.NET、固件渗透、CTF、pwn chain、EDR 绕过、LLM 安全、供应链安全等）在 AI 代理生态中的集成度持续深化
- MASTER-ROUTING 快速路由入口和 case-init 案件管理工作流成为安全研究社区标准参考方案
- 跨平台支持完善（Windows/Linux/macOS/Kali），社区贡献活跃

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 12,856 | 14,725 | +1,869 |
| 总 Forks | 1,930 | 2,172 | +242 |

**核心变化概要**：
- 连续多日 Trending 驱动 Star 暴增 1,869，创项目单日增长纪录
- Fork 同步增长 242，反映安全研究社区的大规模参与
- AI 代理安全技能路由器的差异化定位获得市场验证，在 Claude Code、Cursor 等主流 AI 代理中的集成案例持续增长

### 更新 5 — 2026 年 8 月 4 日（再次登上 Trending）
**更新原因**：连续多日登上 Trending，网络安全 AI 技能路由赛道持续爆发式增长

**最新动态**：
- Star 数从 14,725 增至 15,242（+517），连续多日维持日均 500+ 高增速
- Fork 数从 2,172 增至 2,241（+69），开发者参与度持续攀升
- **20+ 场景技能矩阵**全面覆盖：APK 逆向、IDA、radare2、JS 逆向、.NET、固件渗透、CTF（40+ 子技能）、pwn chain、EDR 绕过、LLM 安全、供应链安全
- 支持 **5 大 AI 客户端**：Claude Code、Kiro、Cursor、Cline、Codex CLI，跨平台覆盖 Windows/Linux/macOS/Kali
- MIT 许可（主项目）+ GPLv3（CTF 模块），MASTER-ROUTING 快速路由入口、case-init 案件管理工作流和 field-journal 知识库体系成熟完善

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 14,725 | 15,242 | +517 |
| 总 Forks | 2,172 | 2,241 | +69 |

**核心变化概要**：
- 连续多日 Trending 驱动 Star 稳步增长 517，累计增星超 4,100 颗（从首次记录 11,089 算起）
- 20+ 场景技能矩阵 + 40+ CTF 子技能构建了最全面的 AI 辅助安全研究工具集
- 5 大 AI 客户端支持（Claude Code/Kiro/Cursor/Cline/Codex CLI）覆盖主流 AI 编码代理生态
- case-init + field-journal + MASTER-ROUTING 三大核心工作流形成完整的安全研究闭环

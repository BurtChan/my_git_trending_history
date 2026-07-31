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
| ⭐ Stars | 10,113 |
| 🍴 Forks | 1,557 |
| 📝 语言 | Python、PowerShell、Bash |
| 📅 创建时间 | 2025 年 |

---

## 总结
Reverse Skill 是目前最全面的 AI 辅助安全研究工具集，通过智能路由将 AI 代码代理的安全能力提升到专业水平。它不仅覆盖了逆向工程和渗透测试的各个领域，还通过案件管理、知识进化、报告生成等功能构建了完整的安全研究工作流，是 AI 时代安全工具链的一次重要创新。

---

*数据来源：GitHub 仓库 (zhaoxuya520/reverse-skill)，2026 年 7 月访问*

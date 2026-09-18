# BrowserSkill 项目分析

## 项目名称
**BrowserSkill** — 让 AI 智能体使用你真实登录态的浏览器，且不打断你的工作
- **GitHub**: [Tencent/BrowserSkill](https://github.com/Tencent/BrowserSkill)
- **许可证**: MIT

---

## 项目概述

BrowserSkill 是腾讯开源的浏览器自动化桥接工具，定位解决 AI Agent 浏览器操作的一个核心痛点：**如何让 Agent 复用用户已登录的真实浏览器环境，同时不干扰用户正在进行的操作**。

传统方案要么要求 Agent 使用独立的无状态浏览器实例（没有登录态，需要单独维护测试账号），要么直接接管用户的浏览器窗口（打断用户工作）。BrowserSkill 的创新在于引入「借还制」：Agent 需要操作某个已打开的标签页时必须显式「借用」，任务完成后归还，其余浏览器窗口完全不受影响。浏览器任务运行在独立可见的 Agent Window 中，用户可以继续使用自己的浏览器。

项目 2026 年 6 月底创建，不到三个月即登上 GitHub Trending（单日 +1,350 stars），增长速度在浏览器自动化赛道非常突出。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 复用真实登录态 | Agent 直接操作用户已登录的站点，无需测试账号 |
| Agent Window 隔离 | 浏览器任务在独立可见窗口运行，不打断用户 |
| 任意 Agent 接入 | 任何能调用 shell 的 Agent 都可通过 `bsk` CLI 使用，无框架锁定 |
| 内置 Human-in-loop | 遇到验证码/登录/确认对话框时，Agent 可请求人类接管后继续 |
| 一键技能安装 | `bsk install-skill` 支持 Cursor/Claude Code/Codex/OpenClaw 等 8+ harness |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| CLI/守护进程 | Rust（crates/bsk-cli、bsk-protocol） |
| 浏览器扩展 | TypeScript（Chrome/Edge，Firefox 规划中） |
| 通信 | 本地 IPC + WebSocket (127.0.0.1) |
| 构建 | Cargo + pnpm workspace |
| 平台 | macOS / Linux / Windows 全平台 |

---

## 项目亮点

### 架构上的「最小信任」设计
Agent 从不直接接触浏览器，所有请求经 `bsk` CLI → 本地 daemon → 浏览器扩展三层路由，扩展在 Agent Window 中执行。DeepSeek Harness 走专用插件路径（注入原生 `browser_*` 工具），同样复用该链路。

### 明确的「借还」边界语义
「借用标签页」是显式动作、有明确归还点，这与「静默抓取整个浏览器控制权」的产品形成本质区别，对企业和个人用户的安全边界更友好。

### 面向 harness 生态的分发策略
提供 AGENT_INSTALL.md 的一句话安装流（把安装指令直接发给你的 Agent 即可完成部署），并内置针对 8 个主流 Agent harness 的 skill 安装器，把「被 Agent 采用」做成了产品能力本身。

---

## 应用场景

### 已登录站点的信息采集与操作
让 Agent 查询已登录的内部系统、后台数据、订单状态，无需为其单独配置账号和凭证。

### 跨 Agent 的浏览器自动化标准件
团队内不同成员使用 Cursor、Claude Code、Codex 等不同工具，均可用同一套 `bsk` CLI 获得一致的浏览器能力。

### 需要人工介入的半自动流程
涉及验证码、二次确认、敏感操作的流程中，Agent 可在关键节点交还人类，随后自动继续。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 5,054 |
| 总 Forks | 354 |
| 今日新增 | +1,078 |
| 创建时间 | 2026-06-22 |

## 📋 更新记录

### 更新 1 — 2026 年 9 月 18 日（连续第二日在榜）

**更新原因**：连续第二日登上 GitHub Trending，单日新增 443 Stars（API 精确数据）

BrowserSkill 次日继续在榜：总 Stars 从 3,533 增至 3,976（+443，+12.5%），Forks 从 248 增至 282（+34）。腾讯出品的这个「借还制 + Agent Window 隔离」浏览器技能框架处于快速上升期，Rust CLI + 扩展的本地架构与多 harness 分发策略持续吸引 Agent 开发者关注，单日 12.5% 的增速在新上榜项目中表现突出。

**Star 数据**：

| 总 Stars | 3,533 | 3,976 | +443 |
| 总 Forks | 248 | 282 | +34 |

- 总 Stars 3,533 → 3,976（+443，+12.5%），连续两日在榜（第 2 次上榜）
- Forks 248 → 282（+34）
- 借还制浏览器技能框架获 Agent 社区认可，上升期增速突出

---

### 更新 2 — 2026 年 9 月 19 日（连续第三日在榜）

**更新原因**：连续第三日登上 GitHub Trending，单日新增 1,078 Stars（API 精确数据），总量突破 5K。

BrowserSkill 第三日继续在榜：总 Stars 从 3,976 增至 5,054（+1,078，+27.1%），Forks 从 282 增至 354（+72）。腾讯出品的「借还制 + Agent Window 隔离」浏览器技能框架热度加速上升，第三日单日增量较昨日（+443）翻倍以上，Rust CLI + 扩展的本地架构与多 harness 分发策略持续吸引 Agent 开发者，三日从 3.5K 冲上 5K。

**Star 数据**：

| 总 Stars | 3,976 | 5,054 | +1,078 |
| 总 Forks | 282 | 354 | +72 |

- 总 Stars 3,976 → 5,054（+1,078，+27.1%），连续三日在榜（第 3 次上榜）
- Forks 282 → 354（+72），集成生态扩张明显

---

## 总结

BrowserSkill 用「借还制 + Agent Window 隔离」重新定义了 Agent 与真实浏览器的安全交互边界，是腾讯在 AI Agent 基础设施方向上小而精准的一击，Rust CLI + 扩展的本地架构和多 harness 分发策略使其极有可能成为浏览器技能的标准组件。

---

*数据来源：GitHub 仓库 (Tencent/BrowserSkill)，2026 年 9 月访问*
*首次分析：2026-09-17 | 最近更新：2026-09-19*

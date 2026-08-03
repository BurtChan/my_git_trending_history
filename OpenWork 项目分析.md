# OpenWork 项目分析

## 项目名称
**OpenWork** — Claude Cowork 的开源替代品，AI 工作流共享平台

- **GitHub**: [different-ai/openwork](https://github.com/different-ai/openwork)
- **许可证**: 自定义（见 LICENSE 文件）

---

## 项目概述

OpenWork 是一个免费开源的桌面应用程序，专注于 AI 工作流的共享与复用。它被定位为 Claude Cowork 和 Codex 的开源替代品，支持 macOS、Windows 和 Linux 三大平台。核心理念是通过一个 OpenWork MCP（Model Context Protocol）连接器，让用户在 Codex、Claude Code、Cursor 等不同 AI 编码工具中复用相同的技能（Skills）、MCP 服务和已连接的服务。

项目采用 Electron + Vite + pnpm workspaces + Turbo monorepo 架构，提供了完整的桌面应用体验，但桌面应用本身是可选的——用户完全可以仅通过现有 AI 代理使用 OpenWork 的全部功能。OpenWork 还提供 Den（组织管理控制面），支持团队级的推理资源调配、策略管理、技能/插件发布以及 Anthropic 兼容插件的导入。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **MCP 集成** | 通过两个工具（search_capabilities + execute_capability）暴露功能 |
| **跨工具复用** | 同一套 Skills/MCPs 可在 Codex、Claude Code、Cursor 等多工具间共享 |
| **团队协作** | Den 控制面支持团队成员邀请、团队管理和访问控制 |
| **推理资源管理** | 统一调配团队成员的模型使用，控制每个成员/团队可用的模型提供商 |
| **技能市场** | 支持通过市场发布技能，并按组织/团队/个人维度分配 |
| **插件导入** | 支持导入 Anthropic 兼容的插件，将其技能和远程 MCP 通过 OpenWork MCP 暴露 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 框架 | Electron |
| 构建工具 | Vite |
| 包管理 | pnpm workspaces |
| Monorepo | Turbo |
| 运行时 | Node.js |
| 协议 | MCP（Model Context Protocol） |
| 远程 API | `https://api.openworklabs.com/mcp/agent` |

---

## 项目亮点

### AI 编码工具的「通用适配器」
OpenWork 通过标准化的 MCP 协议，解决了不同 AI 编码工具之间技能和工作流无法互通的痛点，一次配置即可在多个工具中使用。

### 桌面应用可选
不强制安装桌面应用——通过添加一个远程 MCP URL 即可使用全部功能，降低了使用门槛。

### 企业级团队管理
Den 控制面提供了推理资源调配、桌面策略管控、技能发布等企业级功能，使 OpenWork 不仅适用于个人开发者，也能满足团队协作需求。

### 完善的开发者工具链
支持多 git worktree 同时开发、自动 CDP 端口分配、独立 dev profile 隔离等高级开发功能，展现了工程化的项目管理水平。

---

## 应用场景

### 跨 AI 工具工作流共享
开发者编写的 AI 技能和工作流可在 Claude Code、Codex、Cursor 等工具间无缝复用，避免重复配置。

### 团队 AI 能力标准化
团队管理者可通过 Den 统一发布标准技能包，确保所有成员使用一致的 AI 工作流和最佳实践。

### AI 代理生态接入
通过插件导入功能，可以将现有的 Anthropic 兼容插件生态接入 OpenWork，扩展可用能力。

### 本地优先的 AI 开发
桌面应用在本地运行，支持 AI 编码工具直接调用本地服务，保持数据私密性。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 20,437 |
| 🍴 Forks | 2,095 |
| 👀 Watchers | 75 |
| 📝 Commits | 4,091 |

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 1 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：OpenWork 作为 Claude Cowork 的开源替代方案持续受到关注，今日新增 796 Stars，总 Star 数突破 20,200。该项目基于 opencode 构建，为开发者提供开源的 AI 协作工作空间，无需依赖商业产品即可获得类似体验。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 19,955 | 20,242 | +287 |
| 总 Forks | 1,998 | 1,998 | — |

**核心变化概要**：
- 持续登上 Trending，开源协作工具需求旺盛
- 作为 Claude Cowork 的免费替代，降低 AI 协作门槛
- 社区贡献活跃，Fork 数接近 2,000
- Star 增长稳定，从 19,955 增至 20,242

---

## 总结

OpenWork 是 AI 编码工具生态中一个重要的基础设施项目，通过 MCP 协议标准化和开源开放的模式，打破了不同 AI 工具之间的壁垒。其 18K+ Stars 的高人气反映了开发者对跨工具工作流互通的强烈需求。

---

*数据来源：GitHub 仓库 (different-ai/openwork)，2026 年 7 月访问*

---

## 2026-07-31 更新 1

### Star 数据更新
| 指标 | 数值 | 备注 |
|------|------|------|
| 总 Stars | 19,070 | +210（较上次记录 18,860） |
| 今日 Star 增长 | 915 | 强劲增长 |
| 总 Forks | 1,935 | |
| License | MIT | |

### 最新动态
- **Claude Cowork 开源替代定位明确**：OpenWork 持续强化作为 Claude Cowork 免费开源替代品的品牌形象，吸引大量寻求低成本 AI 工作流方案的开发者。
- **MCP 协议标准化推进**：通过 OpenWork MCP 连接器，用户可将同一套 Skills/MCPs 接入 Codex、Claude Code、Cursor 等多个 AI 编码工具，实现真正的跨工具能力复用。
- **跨平台桌面应用覆盖**：支持 macOS、Windows 和 Linux 三大平台，桌面应用为可选组件，通过远程 MCP URL 即可使用全部功能，降低使用门槛。
- **团队管理功能完善（OpenWork Den）**：提供推理配置、团队成员管理、桌面策略管控、技能市场发布及 Anthropic 兼容插件导入等企业级能力。
- **社区活跃度高**：项目累计 4,091+ 次提交，今日单日 Star 增长 915，反映出快速迭代的开发节奏和强烈的社区关注。

### 趋势分析
OpenWork 今日以 +915 的单日 Star 增长登上 GitHub Trending，核心驱动力在于其精准切中了 AI 编码工具生态中"工作流互通"的痛点。随着 Claude Code、Codex、Cursor 等 AI 编码工具的普及，开发者对跨工具复用 Skills/MCPs 的需求急剧上升，而 OpenWork 以开源免费的方式提供了这一能力，直接与 Anthropic 的 Claude Cowork 形成竞争。高增长也表明社区对 MCP 协议标准化方向的认可，OpenWork 正成为 AI 代理生态中重要的基础设施层。

---

## 更新记录

### 更新 1 — 2026年7月31日

| 指标 | 数值 |
|------|------|
| 上次记录 | 19,070 Stars |
| 总 Stars | 19,955 |
| 新增 | +885 |
| 今日 Trending | +796 stars |

---

### 更新 2 — 2026年8月3日

**更新原因**：Star 日增 280，总星突破 20,000 后继续稳步攀升至 20,437，再次登上 GitHub Trending

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 19,955 | 20,437 | +482 |
| 总 Forks | ~2,000 | 2,095 | +95 |

**更新亮点**：
- 再次登上 GitHub Trending，总 Star 数稳步逼近 20,500
- 作为 Claude Cowork 的开源替代方案，MCP 协议标准化持续吸引开发者关注
- OpenWork 生态扩展，Skills/MCPs 共享工作流互通能力持续增强
- 社区持续活跃，自托管 AI 协作工具赛道热度不减

---

### 更新 3 — 2026年8月4日

**更新原因**：连续两天登上 GitHub Trending，今日 +280 星（Trending 页面数据），总星数从 19,955 增至 20,505，AI 工作流共享赛道热度不减

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 19,955 | 20,505 | +550 |
| 总 Forks | ~2,000 | 2,102 | +102 |

**更新亮点**：
- 连续登上 Trending，总 Star 数从 19,955 增长至 20,505（+550），稳步突破 20,500
- 作为 Claude Cowork 免费开源替代方案的定位持续吸引大量开发者，据 cubed.run 报道该项目曾迫使 Anthropic 重新考虑 AI 定价策略
- MCP 协议标准化推进，OpenWork MCP 连接器支持 Codex、Claude Code、Cursor 等主流 AI 工具跨平台复用
- OpenWork Den 团队控制面板功能持续完善，企业级推理配置、策略管控、技能市场发布能力日趋成熟
- 跨平台桌面应用（macOS/Windows/Linux）+ 远程 MCP URL 双模式降低使用门槛
- 社区活跃度高，累计 4,111+ 次提交反映快速迭代的开发节奏

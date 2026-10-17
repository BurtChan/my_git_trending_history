# CLI-Anything 项目分析

## 项目名称

**CLI-Anything** — 让所有软件变为 Agent 原生，通过自动生成 CLI 实现智能体对任意软件的操控

- **GitHub**: [HKUDS/CLI-Anything](https://github.com/HKUDS/CLI-Anything)
- **许可证**: Apache License 2.0

---

## 项目概述

CLI-Anything 是由香港大学数据科学实验室（HKUDS）开发的开源项目，其核心愿景是让世界上所有软件都能被 AI 智能体直接控制。在当前的 AI Agent 生态中，操控桌面软件通常依赖脆弱的屏幕点击自动化或不完善的 API 封装，而 CLI-Anything 通过为任意软件自动生成结构化的命令行接口（CLI），从根本上解决了这一问题。

项目采用 7 阶段自动化流水线，涵盖代码库分析、架构设计、实现、测试规划、测试编写和文档生成，能够为任何拥有代码库的软件快速生成生产级的 CLI 接口。生成的 CLI 以结构化 JSON 输出为特点，消除了复杂的解析需求，确保了确定性和可靠的结果。

CLI-Anything 还提供了 CLI-Hub 注册中心，用户可以通过 `pip install cli-anything-hub` 一键浏览、安装和管理社区构建的所有 CLI 工具。目前项目已支持 Claude Code、OpenCode、Goose、Codex、GitHub Copilot CLI 等多种主流智能体平台，并且已经为 Blender、Obsidian、Godot Engine、Kdenlive 等数十款主流软件生成了可用的 CLI 线束（harness）。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **自动化 CLI 生成** | 通过 7 阶段流水线自动为任意软件生成生产级 CLI |
| **CLI-Hub 注册中心** | 浏览、安装、管理社区贡献的所有 CLI 工具 |
| **SKILL.md 集成** | 为 AI 智能体提供标准化的技能描述文件，支持自主发现与安装 |
| **多平台兼容** | 支持 Claude Code、OpenCode、Goose、Codex、OpenClaw 等多种 Agent 平台 |
| **结构化 JSON 输出** | 所有 CLI 输出均为结构化格式，便于智能体解析和处理 |
| **插件系统** | 支持社区开发新的 CLI 线束和扩展 |
| **浏览器自动化** | 提供 DOMShell MCP 和 Accessibility Tree 支持 |
| **一键安装** | `npx skills add` 或 `pip install` 即可完成部署 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要语言** | Python |
| **包管理** | pip / npx |
| **Agent 协议** | SKILL.md 标准 |
| **CLI 生成** | 7 阶段自动化流水线 |
| **浏览器自动化** | DOMShell MCP + Accessibility Tree |
| **注册中心** | CLI-Hub (clianything.cc) |
| **测试** | 单元测试 + 端到端测试 + 后端验证 |

---

## 项目亮点

1. **革命性理念**：提出"Agent 原生软件"概念，让任何软件无需 API 或 GUI 即可被 AI 智能体控制
2. **高度自动化**：7 阶段流水线从代码分析到文档生成全自动完成，极大降低了 CLI 开发成本
3. **社区驱动生态**：CLI-Hub 注册中心汇聚社区力量，已有数十款软件的 CLI 线束可供安装使用
4. **广泛兼容性**：支持几乎所有主流 AI Agent 平台，真正做到平台无关的通用解决方案

---

## 应用场景

1. **AI Agent 自动化办公**：让智能体通过 CLI 操控 Obsidian、Blender、Godot Engine 等桌面软件完成复杂任务
2. **DevOps 流程自动化**：通过生成的 CLI 接口实现跨软件的自动化部署和运维
3. **AI 编程助手增强**：为 Claude Code、Copilot 等编程助手扩展操控外部软件的能力
4. **科研与工程自动化**：利用 CLI 线束实现 CAD 建模、3D 渲染、数据处理等任务的自动化流水线

---

## Star 数据

| 指标 | 数据 |
|------|------|
| **总 Stars** | 53,937 |
| **Forks** | 4,896 |
| **今日新增 Stars** | +203 |
| **许可证** | Apache License 2.0 |
| **主要语言** | Python |

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 15 日（再次登上 Trending）

**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：时隔 3 个月，CLI-Anything 再次登上 GitHub Trending，Star 数从 35,273 增长至 47,160（+11,887），Forks 增至 4,382。这个由 HKUDS 团队打造的「让所有软件 Agent-Native」项目，通过 CLI-Hub（clianything.cc）将命令行工具接入 AI Agent 生态，近 3 个月增长迅猛，说明 AI Agent 调用 CLI 工具的需求正在爆发。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 35,273 | 47,160 | +11,887 |
| 总 Forks | 3,465 | 4,382 | +917 |

**核心变化概要**：
- Star 突破 47K，3 个月净增超 1.1 万
- CLI-Hub 持续扩充可接入的工具库，Agent-Native 生态加速成型
- 与 AI Agent 工作流深度整合的定位获得开发者广泛认可
---

### 更新 2 — 2026 年 8 月 16 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
CLI-Anything 连续第 3 天登上 GitHub Trending，Star 数从 47,160 增至 47,361（+201），Forks 增至 4,392。这个由 HKUDS 团队打造的「让所有软件 Agent-Native」项目学术影响力持续发酵：团队发表 arXiv 论文《CLI-Anything: Towards Agent-Native Computer Use》（2606.03854），系统阐述 CLI-Hub 作为 Agent 与命令行工具之间的能力发现、安装与交互基础设施；当前已为 CLI 配套 61 个 SKILL.md 技能文件，并在 18 个高复杂度应用上完成生产级测试，覆盖创意、生产力、AI 图像生成、本地 LLM 推理等此前 AI Agent 难以涉足的领域。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 47,160 | 47,361 | +201 |
| 总 Forks | 4,382 | 4,392 | +10 |

**核心变化概要**：
- Star 从 47.2K 增至 47.4K（+201），连续第 3 天登上 Trending
- arXiv 论文发布，Agent-Native Computer Use 理论体系成型
- 61 个配套 CLI 技能 + 18 个生产级应用测试，生态持续完善

### 更新 3 — 2026 年 9 月 23 日（时隔 5 周再次登上 Trending）

**更新原因**：时隔 5 周（8/16 后）再次登上 GitHub Trending，Star 从 47,361 增至 49,721（+2,360），Forks 从 4,392 增至 4,591（+199）。

**最新动态**：
CLI-Anything（CLI-Hub）作为「Agent-Native 软件」范式的基础设施，近 5 周保持周均 +470 的稳定增长。随着多 Agent 系统对传统软件调用能力的依赖加深，把命令行工具自动封装为 Agent 可调用接口的 CLI-Hub 路线，正获得越来越多 Agent 框架的接入。

同榜的 strands-agents/harness-sdk（AWS 系 Agent SDK）、BuilderIO/agent-native 等项目均指向同一趋势：Agent 与既有软件生态的桥接层是当前 infra 热点。

**Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|:---:|:---:|:---:|:---:|
| 总 Stars | 47,361 | 49,721 | +2,360 |
| 总 Forks | 4,392 | 4,591 | +199 |

**核心变化概要**：
- Star 从 47,361 增至 49,721（+2,360），周均 +470 稳步增长
- Forks 从 4,392 增至 4,591（+199），生态接入持续
- Agent-Native 软件范式与同榜 harness 类项目形成趋势共振
### 更新 4 — 2026 年 9 月 24 日（连续第二日登上 Trending）

**更新原因**：连续第二日登上 GitHub Trending 榜单（今日 +440 Stars，API 精确数据）

- Star 从 49,721 增至 50,161（+440），Forks 从 4,591 增至 4,609（+18），昨日回榜后热度延续。
- 「Agent-Native 软件范式」议题持续发酵，与同榜 Agent harness/编排类项目形成趋势共振。
- 第 5 次上榜，CLI-Hub 工具生态与主流 Agent 平台接入面继续扩大。

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 49,721 | 50,161 | +440 |
| 总 Forks | 4,591 | 4,609 | +18 |



---


## 总结

CLI-Anything 是一个极具前瞻性的开源项目，由香港大学数据科学实验室打造，旨在通过自动生成 CLI 接口的方式让 AI 智能体能够操控任意软件。项目采用 7 阶段自动化流水线，从代码分析到文档生成全程自动化，并配合 CLI-Hub 注册中心构建了活跃的社区生态。凭借 50,000+ 的 Stars 和对主流 Agent 平台的广泛支持，CLI-Anything 正在引领"Agent 原生软件"的新范式，有望成为 AI Agent 生态中不可或缺的基础设施。

### 更新 5 — 2026 年 9 月 25 日（连续第三日登上 Trending）

**更新原因**：连续第三天登上 GitHub Trending（SnailDev 9/23+9/24 归档 + 今日 HTML 确认在榜），streak 豁免 500 阈值。

**最新动态**：连续第三天在榜，过去一天 Star +86、Fork +5，总量突破 5 万后进入平稳增长区间。学术驱动（arXiv 论文）+ CLI-Hub 生态扩张的双引擎仍在发挥作用。

CLI-Hub 收录的 CLI 工具与 SKILL.md 技能文件持续增加，Agent-Native Computer Use 的定位在 Claude/Agent 生态爆发的背景下持续获得曝光。

**Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 50,161 | 50,247 | +86 |
| 总 Forks | 4,609 | 4,614 | +5 |

**核心变化**：

- Star 数：50,161 → **50,247**（+86）
- Forks：4,609 → 4,614（+5）
- 上榜情况：2026 年 9 月 25 日（连续第三日登上 Trending）
- 数据来源：GitHub API（2026-09-25）
---

### 更新 6 — 2026 年 10 月 14 日（时隔 19 天再次登上 Trending）

**更新原因**：时隔 19 天再次登上 GitHub Trending，离榜期间 Star 累计 +1,912（API 精确数据）

**最新动态**：离榜近三周后重返 Trending，总 Stars 从 50,247 增至 52,159（+1,912），Forks 从 4,614 增至 4,756（+142）。CLI-Hub（clianything.cc）生态持续扩张，Agent-Native Computer Use 定位在 Agent 工具链爆发背景下保持曝光；仓库现有 893 commits、115 contributors，社区贡献活跃。

**Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 50,247 | 52,159 | +1,912 |
| 总 Forks | 4,614 | 4,756 | +142 |

**核心变化**：

- Star 数：50,247 → **52,159**（+1,912，离榜期间累计）
- Forks：4,614 → 4,756（+142）
- 上榜情况：2026 年 10 月 14 日（时隔 19 天再次登上 Trending）
- 数据来源：GitHub API（2026-10-14）



### 更新 7 — 2026 年 10 月 16 日（连续多日稳居 Trending）

**更新原因**：时隔两天再次登上 GitHub Trending，Star 52,159 → 53,174（+1,015，API 精确数据）

**最新动态**：CLI-Anything 10 月 14 日回榜后持续在榜，总 Stars 突破 5.3 万（52,159 → 53,174，+1,015），Forks 从 4,756 增至 4,821（+65）。项目当前主打「18 个专业软件 Demo + 2,280 项通过测试」的工程化叙事，arXiv 论文（2606.03854）「CLI-Anything: Towards Agent-Native Computer Use」持续为 Agent-Native Computer Use 定位背书；CLI-Hub（clianything.cc）作为 Agent 与 CLI 工具的注册中心，生态聚合效应逐步显现。两日 +1,015 的增速显示回榜热度仍在延续。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 52,159 | 53,174 | +1,015 |
| 总 Forks | 4,756 | 4,821 | +65 |

**核心变化**：

- Star 数：52,159 → **53,174**（+1,015，两日）
- Forks：4,756 → 4,821（+65）
- 上榜情况：2026 年 10 月 16 日（回榜后连续在榜）
- 数据来源：GitHub API（2026-10-16）



---

*数据来源：GitHub 仓库 (HKUDS/CLI-Anything)，2026 年 10 月访问*
*首次分析：见文件头部 | 最近更新：2026 年 10 月 18 日*
### 更新 8 — 2026 年 10 月 17 日（连续多日在榜）

**更新原因**：连续多日稳居 GitHub Trending，总 Stars 从 53,174 增长至 53,734（+560），今日单日新增 +281 Stars，「让所有软件 Agent 原生」的方法论叙事保持热度。

**最新动态**：
- CLI-Hub（clianything.cc）作为 Agent 与 CLI 工具注册中心持续扩充，仓库内 agent-harness 覆盖 Blender、GIMP、Godot、QGIS、FreeCAD 等数十款专业软件，3MF/agent-harness 等新领域 harness 持续合入
- 工程指标升级：「18 个专业软件 Demo + 2,280 项通过测试」的基准叙事延续，arXiv 技术报告（2606.03854）为 Agent-Native Computer Use 定位提供学术背书
- 多 Agent 框架适配扩展：除 Claude Code 插件外，新增 Cursor 插件、Codex skill、pi-extension 与 Hermes skill 等接入方式

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 53,174 | 53,734 | +560 |
| 总 Forks | 4,821 | 4,880 | +59 |
| 今日新增 | — | +281 | — |

**核心变化概要**：
- 总 Stars 达 53,734（+560），连续多日在榜、日均增速稳定在数百量级
- CLI-Hub 生态聚合 + 多框架插件（Cursor/Codex/Hermes）扩展是本轮主要进展
- 方法论型项目（非单一工具）的长尾热度罕见地持续超过两周

---

### 更新 9 — 2026 年 10 月 18 日（连续多日在榜）

**更新原因**：连续多日稳居 GitHub Trending，总 Stars 从 53,734 增长至 53,937（+203），今日单日新增 +203 Stars，方法论型项目的长尾热度持续。

**最新动态**：
- 仓库进入稳态期：主分支最近提交仍为 9 月下旬 README 维护，最新 release 仍为 v0.4.0，热度由 CLI-Hub（clianything.cc）生态与多框架插件（Claude Code/Cursor/Codex/Hermes）持续承接
- agent-harness 矩阵继续横跨 Blender、GIMP、Godot、QGIS、FreeCAD 等数十款专业软件，「18 个专业软件 Demo + 2,280 项通过测试」的基准叙事保持
- arXiv 技术报告（2606.03854）的 Agent-Native Computer Use 定位继续为项目提供学术背书

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 53,734 | 53,937 | +203 |
| 总 Forks | 4,880 | 4,896 | +16 |
| 今日新增 | +281 | +203 | — |

**核心变化概要**：
- 总 Stars 达 53,937（+203），连续多日在榜，增速稳定在数百量级
- 稳态期：无新提交/新版本，生态叙事承接热度
- 方法论型项目长尾热度持续超过两周

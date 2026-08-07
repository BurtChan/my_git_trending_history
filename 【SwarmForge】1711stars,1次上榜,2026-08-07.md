# SwarmForge 项目分析

## 项目名称
**SwarmForge** — 基于 tmux 的纪律化多智能体编排平台（Robert C. Martin 出品）
- **GitHub**: [unclebob/swarm-forge](https://github.com/unclebob/swarm-forge)
- **许可证**: 未声明（README 显示为自定义项目）

---

## 项目概述
SwarmForge 是"鲍勃大叔"（Robert C. Martin，敏捷/清洁代码之父）推出的多智能体协作编排工具，定位是"把一群 AI 智能体变成可靠、专业的软件工程师"。与市面上追求自动化的 agent 框架不同，SwarmForge 强调**纪律**（disciplined）：它用 tmux 会话 + git worktree 把多个智能体组织成可观察、可干预的工作流。

系统设计非常"Uncle Bob"：每个智能体有明确的角色分工（coder、cleaner、spec 作者、QA 等），遵循 TDD、Gherkin 规格、CRAP/DRY 审查、架构审查等软件工程纪律。`main` 分支承载共享脚本与默认"宪法"（constitution）条款，可运行的工作流分支（如 two-pack、four-pack）各自定义角色提示词与本地宪法。

项目创建于 2026 年 4 月，今日 +85 Star 首次登上 Trending。README 特别警告不要购买任何声称相关的 SWARM 代币——这是防诈骗声明，也说明项目热度已引来仿冒。

---

## 核心功能
| 功能 | 说明 |
|------|------|
| tmux 多会话编排 | 每个 agent 一个 tmux 窗口/会话，可实时观察 |
| git worktree 隔离 | 智能体在不同 worktree 中工作，互不踩踏 |
| 角色化提示词 | coder / cleaner / QA / spec 等角色分工 |
| 宪法条款 | 共享与分支级的约束规则（constitution） |
| 工作流分支 | two-pack（快速后端）/ four-pack（规格驱动）等 |
| 看门狗恢复 | 窗口异常时自动重建并恢复会话状态 |

---

## 技术栈
| 组件 | 技术 |
|------|------|
| 语言 | Clojure（脚本）、Shell |
| 编排 | tmux + git worktree |
| 工具 | bb.edn（babashka）、swarm 包装脚本 |
| 流程 | TDD、Gherkin、CRAP/DRY 审查 |

---

## 项目亮点

### 把软件工程纪律注入 Agent 协作
多数 agent 框架追求"全自动"，SwarmForge 反其道而行：用 TDD、规格驱动、架构审查等传统工程纪律约束智能体，产出更接近"可维护的代码"而非"能跑的代码"。

### 可观察性优先
每个 agent 都在独立 tmux 窗口中运行，人类可以随时查看、介入、恢复——这不是黑盒自动化，而是人机协作的"车间"。

### 大师级设计理念
Uncle Bob 亲自操刀，分支设计（two-pack/four-pack）对应不同项目复杂度，体现了他对软件工程流程的深刻理解。

---

## 应用场景

### 小型后端功能开发
two-pack 工作流：coder 按 TDD 实现 → cleaner 做重构与架构审查，适合快速迭代。

### 规格驱动的中型项目
four-pack 工作流引入 Gherkin 规格与验收测试角色，适合需要可追溯需求的模块。

### 教学与流程研究
对"AI 时代软件工程流程"感兴趣的人，可以观察大师如何组织多 agent 协作。

---

## Star 数据
| 指标 | 数值 |
|------|------|
| ⭐ 总 Stars | 1,711 |
| 🍴 总 Forks | 190 |
| 今日新增 | +85 |

---

## 总结
SwarmForge 是 Robert C. Martin 用 tmux + git worktree 构建的纪律化多智能体编排平台，把 TDD 与工程审查流程嵌入 agent 协作，为"AI 写代码"提供了可观察、可控制、讲纪律的另一种答案。

---

*数据来源：GitHub 仓库 (unclebob/swarm-forge)，2026 年 8 月访问*

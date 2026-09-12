# Worktrunk 项目分析

## 项目名称
**Worktrunk** — 为并行 AI Agent 工作流设计的 Git Worktree 管理 CLI
- **GitHub**: [max-sixty/worktrunk](https://github.com/max-sixty/worktrunk)
- **许可证**: 未标注（NOASSERTION）

---

## 项目概述
Worktrunk 是 Rust 编写的 Git worktree 命令行管理器，由 Maximilian Roos（max-sixty）开发，2025 年 12 月 30 日发布。它瞄准的核心痛点是：当开发者并行运行多个 AI 编程代理（Claude Code、Gemini CLI 等）时，原生 git worktree 的用户体验非常繁琐——每个 agent 需要独立的目录和分支，手动 `git worktree add` + `cd` + 建分支 + 事后清理，步骤冗长且易错。

Worktrunk 把这整套流程压缩为 `wt switch -c -x claude feat` 一条命令：创建 worktree、切过去、顺手启动 Claude。发布推文获得 9.75 万次浏览，迅速成为「多 agent 并行开发」工作流的热门基础设施，7,000 Star 见证了 AI 编程时代对 Git 工作流重构的真实需求。

---

## 核心功能

| 命令 | 作用 | 等价原生操作 |
|------|------|--------------|
| `wt switch [-c] [-x claude] feat` | 切换/创建 worktree，可选直接启动 agent | `git worktree add -b feat ../repo.feat && cd ../repo.feat && claude` |
| `wt list` | 带状态面板的 worktree 列表（分支/变更/agent） | `git worktree list`（仅路径） |
| `wt merge main` | 自动生成 commit message、合并回 main、后台清理 worktree 与分支 | 手动 commit + merge + remove 三连 |
| `wt remove` | 清理 worktree，已合并则删分支 | `git worktree remove` + `git branch -d` |
| `wt step` | 逐步推进工作流 | — |

---

## 技术栈
| 组件 | 技术 |
|------|------|
| 语言 | Rust（cargo install worktrunk） |
| 分发 | Homebrew / crates.io / Winget / Nix（flake） |
| 构建 | cargo-dist（dist-workspace.toml）、Taskfile |
| 集成 | Claude Code、Gemini CLI（gemini-extension.json）、Zellij 标签页工作流 |
| Shell 集成 | `wt config shell install` |

---

## 项目亮点

### 面向 Agent 的完整生命周期管理
不只是创建 worktree——从 `switch` 启动 agent，到 `list` 监控各 agent 状态，到 `merge` 自动写 commit message 并回主分支，再到后台自动清理，覆盖「并行开发-合并-收尾」全链路。

### 极致简化的一等命令
`wt switch feat` 替代五条原生命令的组合；merge 阶段自动判断是否需要 rebase/squash，输出清晰的 diff 摘要。

### 跨平台细节
Windows 上因与 Windows Terminal 的 `wt` 冲突，默认以 `git-wt` 名称安装；支持 Grove 式 bare clone 工作流（Laurent Kempé 等博主实测推荐）。

---

## 应用场景

### 多 Claude Code/Gemini 并行开发
每个 agent 独占一个 worktree + 分支，Zellij 多标签页各跑一个，互不冲突地并行完成不同特性。

### 人类的多分支并行工作
即使不用 AI，多特性并行、热修隔离、多版本测试、代码审查等场景同样受益于简化的 worktree 流。

### AI 编程团队的标准化工作流
以 CLI 形式固化「每个任务一个隔离环境」的实践，降低团队引入并行 agent 的门槛。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ 总 Stars | 7,159 |
| 🍴 总 Forks | 255 |
| 📈 今日新增 | 159 |
| 创建时间 | 2025-10-17 |
| 主要语言 | Rust |
| Open Issues | 39 |

## 📋 更新记录

### 更新 1 — 2026年9月13日（连续第二天登上 Trending）

连续第二天登上 Trending，Star 从 7,000 增至 7,159（+159），Fork 从 248 增至 255，日增速较昨日的 +44 明显放大，多 agent 并行开发工作流的刚需属性得到验证。

`wt switch -c -x claude feat` 一条命令完成建 worktree + 切换 + 拉起 agent 的核心卖点未变，Rust 实现的轻量定位使其在 Claude Code / Gemini CLI 并行场景中持续被推荐。

**Star 数据**

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|------|------|------|
| 总 Stars | 7,000 | 7,159 | +159 |
| 总 Forks | 248 | 255 | +7 |
| 今日新增 | — | 159 | — |

**核心变化**

- Star 7,000 → 7,159（+159，日均 +159）
- Fork 248 → 255（+7）
- 连续在榜第二日，增长稳健，暂无异常波动信号

---

## 总结
Worktrunk 用 Rust 把 Git worktree 的繁琐操作压缩成面向 AI Agent 并行工作流的一等命令，从启动、监控到合并清理的全生命周期覆盖，是「多代理并行编程」时代 Git 工作流重构的代表工具。

---

*数据来源：GitHub 仓库 (max-sixty/worktrunk)，2026 年 9 月访问*
*首次分析：见文件头部 | 最近更新：2026 年 9 月 13 日*

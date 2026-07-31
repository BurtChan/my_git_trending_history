# Tuicr 项目分析

## 项目名称
**Tuicr** — 基于 Vim 键绑定的终端代码审查工具（发音 "tweaker"）

- **GitHub**: [agavra/tuicr](https://github.com/agavra/tuicr)
- **许可证**: MIT

---

## 项目概述

Tuicr 是一个用 Rust 编写的终端代码审查工具，以 Vim 键绑定为核心交互方式，提供类似 GitHub 的连续 diff 视图、PR 风格的多级评论系统和完整的审查会话持久化功能。它以单一静态二进制分发，无需运行时依赖，支持审查未提交变更、提交范围、GitHub PR 和 GitLab MR 等多种目标。

Tuicr 的独特之处在于将代码审查从浏览器带到了终端——开发者可以在熟悉的 Vim 操作模式下完成全部审查工作，并通过 `:submit` 命令直接将行内评论推送到 GitHub/GitLab。此外，它还支持将审查结果导出为结构化 Markdown（方便 Claude、Codex 等 AI 编码代理消费），提供了连接人类审查和 AI 辅助审查的桥梁。

项目支持 git、jujutsu（jj）和 Mercurial 三种版本控制系统，内置 24 种终端主题（含 catppuccin、ayu、github 等流行配色），并提供了 Rust 库 API 供程序化集成。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **连续 diff 流** | 所有变更文件在一个视图中连续滚动查看 |
| **多级评论** | 支持行级、范围级、文件级和审查级四种评论粒度 |
| **审查追踪** | 按文件或 hunk 粒度追踪审查进度，跨会话持久化 |
| **VCS 支持** | Git、Jujutsu（jj）、Mercurial |
| **审查目标** | 未提交变更、提交范围、GitHub PR、GitLab MR |
| **GitHub/GitLab 推送** | 行内评论直接作为 PR Review 推送到远端 |
| **AI 代理导出** | 结构化 Markdown 导出，含编号评论和文件/行锚点 |
| **主题系统** | 24 种内置终端主题 |
| **单一二进制** | 零运行时依赖，支持 Cargo/Homebrew/Mise/Nix 安装 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | Rust |
| 终端 UI | 自研 TUI 框架（Vim 键绑定） |
| 分发 | 单一静态二进制 |
| 安装方式 | Cargo、Homebrew、Mise、Nix |
| 配置 | TOML（`~/.config/tuicr/config.toml`） |
| 外部依赖 | `gh`（GitHub CLI）、`glab`（GitLab CLI） |

---

## 项目亮点

### 真正的 Vim 体验
完整支持 Vim 键绑定（包括 visual mode、`{N}G`、Ctrl-d/u 等），不像其他竞品仅支持基础的 j/k 上下移动。

### AI 代理友好的审查导出
结构化 Markdown 导出包含编号评论和精确的文件/行锚点，专为 Claude、Codex 等 AI 编码代理设计，实现「人类审查 + AI 修复」的高效工作流。

### 智能会话恢复
重新打开 PR/MR 时自动选择上次审查之后的新提交，已覆盖的提交显示 `✓` 标记，避免重复审查。

### 多 VCS 和多平台支持
同时支持 Git、Jujutsu 和 Mercurial 三种版本控制系统，覆盖 Linux、macOS 和 Windows 三大平台。

---

## 应用场景

### 终端原生代码审查
为习惯在终端工作的开发者提供浏览器级的代码审查体验，无需切换到 GitHub/GitLab Web 界面。

### AI 辅助代码审查工作流
将审查导出为结构化 Markdown 后喂给 AI 编码代理（Claude、Codex），让 AI 根据审查意见直接修复代码。

### 大型 PR/MR 审查
连续 diff 流视图和 hunk 粒度的审查追踪，特别适合处理包含大量文件变更的 Pull Request。

### 多版本控制项目
在同时使用 Git、Jujutsu 或 Mercurial 的团队中，Tuicr 提供统一的审查体验。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 1,903 |
| 🍴 Forks | 163 |
| 📜 许可证 | MIT |

---

## 总结

Tuicr 用 Rust 重新定义了终端代码审查体验，将 GitHub 风格的 diff 浏览和评论系统完整搬到了终端中。其真正的 Vim 键绑定支持和 AI 代理友好的审查导出功能，使其在同类工具（hunk、lumen 等）中脱颖而出，是终端工作流中代码审查环节的优秀解决方案。

---

*数据来源：GitHub 仓库 (agavra/tuicr)，2026 年 7 月访问*

# OpenClaude 项目分析

## 项目名称
**OpenClaude** — 开源的多后端 AI 编码代理终端（Open terminal for any LLM）
- **GitHub**: [Gitlawb/openclaude](https://github.com/Gitlawb/openclaude)
- **许可证**: MIT（社区修改部分）+ Anthropic 原始 Claude Code 许可（衍生部分）
- **主页**: https://openclaude.gitlawb.com

---

## 项目概述

OpenClaude 是一个开源的编码代理 CLI 工具，源自 Anthropic 的 Claude Code 代码库并做了大量社区化改造。其核心卖点是「runs anywhere, uses anything」——一个终端统一接入云端与本地模型后端：OpenAI 兼容 API、Gemini、GitHub Models、Codex OAuth、Ollama、Atomic Chat 等均可作为推理后端，同时保留完整的终端优先工作流：提示、工具调用、子代理、MCP、斜杠命令与流式输出。

项目于 2026 年 4 月创建，短短五个月即收获 30,900+ Star 与 8,900+ Fork，增长速度极为惊人，是「Claude Code 开源替代」赛道中最受关注的项目之一。仓库存有 1,172 个提交，包含 Docker 部署、VS Code 扩展、Android 安装指南等完整工程化配套。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 多后端接入 | OpenAI 兼容 API / Gemini / GitHub Models / Codex OAuth / Ollama 等统一到一个 CLI |
| `/provider` 引导配置 | 交互式后端设置，配置档案保存在 `.openclaude-profile.json` |
| 编码代理工作流 | bash、文件工具、grep、glob、子代理、任务、MCP、Web 工具一站集成 |
| 会话恢复与分叉 | 按 session ID 恢复对话，`--fork-session` 支持对话历史分支 |
| 后台会话 | 长任务脱离终端后台运行，本地子进程模式（无守护进程、无网络服务） |
| VS Code 扩展 | 内置官方扩展，支持启动集成与主题 |
| 像素风伴侣 | 按 Enter 时射箭的像素艺术小角色（项目特色彩蛋） |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | TypeScript |
| 运行时 | Node.js ≥22（npm 安装）/ Bun（源码构建） |
| 桌面集成 | VS Code Extension |
| 部署 | Docker / npm 全局安装 / AUR（Arch Linux） |
| 发布 | release-please 自动化 |

---

## 项目亮点

### 彻底的后端中立性
与 Claude Code 锁定 Anthropic API 不同，OpenClaude 把「模型后端」抽象成可插拔配置，本地 Ollama 与云端 API 可以在同一工作流中无缝切换，对成本敏感和隐私敏感的用户都是刚需。

### 干净的配置切割
OpenClaude 使用独立的 `~/.openclaude` 配置目录，不读取 `~/.claude` 或 Claude Code 凭证，从架构上避免了与原版工具的配置冲突和数据混淆，迁移路径清晰。

### 工程成熟度高
1,172 个提交、PR 检查 CI、安全策略、CodeRabbit 代码审查、发布自动化一应俱全；还有 GitLawb 去中心化镜像，社区运营（Discord/Discussions/X）完整。

### 合规边界清晰
README 明确声明项目与 Anthropic 无关联，「Claude」商标归 Anthropic 所有，社区修改以 MIT 发布、衍生部分保留原许可——在开源分叉商业产品方面提供了合规范本。

---

## 应用场景

### 本地模型开发者
用 Ollama 跑本地模型却想要 Claude Code 级别代理体验的用户，OpenClaude 是目前最完整的开源选择。

### 多云成本优化团队
同一 CLI 在 OpenAI / Gemini / GitHub Models 间切换，按任务复杂度选后端，控制 API 成本。

### 编码代理研究者
想研究 Claude Code 架构（工具调用、MCP、子代理编排）的开发者可以直接阅读和改造这个开源代码库。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 31,826 |
| 总 Forks | 8,945 |
| 今日新增 Stars | +646 |
| 创建时间 | 2026-04-01 |
| 主要语言 | TypeScript |

## 📋 更新记录

### 更新 1 — 2026 年 9 月 2 日（再次登上 Trending）
**更新原因**：连续第二日登上 GitHub Trending 榜单

**最新动态**：OpenClaude 在首日冲榜后热度延续，次日继续在榜。Star 突破 3.1 万，Fork 逼近 9 千，社区围绕「Claude Code 开源替代」的讨论持续升温。项目保持后端中立定位，支持任意模型供应商接入的卖点继续吸引被 API 定价困扰的开发者。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 30,948 | 31,180 | +232 |
| 总 Forks | 8,924 | 8,943 | +19 |

**核心变化概要**：
- 连续第二日在榜，Star +232、Fork +19
- Star 总量突破 3.1 万，五个月增长曲线依然陡峭
- 「Claude Code 开源化」赛道头部地位巩固


---

### 更新 2 — 2026 年 9 月 3 日（连续第 3 日登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：OpenClaude 连续第三日登上 Trending，单日 +646 星（昨日仅 +232），增长显著提速，总星数达到 3.18 万。「Claude Code 开源替代」赛道的关注度持续升温，社区对其开放实现与生态兼容能力的讨论热度上升。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 31,180 | 31,826 | +646 |
| 总 Forks | 8,924 | 8,945 | +21 |

**核心变化概要**：
- 连续第 3 日在榜，单日 +646，较昨日（+232）大幅提速
- Star 总量达 3.18 万
- 「Claude Code 开源化」赛道头部地位继续巩固

---

## 总结

OpenClaude 是「Claude Code 开源化」浪潮中的旗舰项目：它把 Anthropic 封闭的编码代理体验改造成后端中立的开放工具，五个月 30K+ Star 的增速印证了市场需求。对于被 API 定价和供应商锁定困扰的开发者，这是目前工程完成度最高的替代方案。

---

*数据来源：GitHub 仓库 (Gitlawb/openclaude)，2026 年 9 月访问*

*首次分析：见文件头部 | 最近更新：2026 年 9 月 3 日*

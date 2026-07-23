# Ego Lite 项目分析

## 项目名称

**Ego Lite** — 人与 AI Agent 并行工作的浏览器

- **GitHub**: [citrolabs/ego-lite](https://github.com/citrolabs/ego-lite)
- **许可证**: MIT

---

## 项目概述

Ego Lite 是一款专为人类和 AI Agent 并行协作设计的浏览器。与 Browser-Use、Vercel agent-browser 等浏览器自动化框架不同，Ego Lite 不是在现有浏览器之外驱动另一个浏览器实例，而是从零构建了一个人类和 Agent 共享的浏览器环境——Agent 在自己的「Space」中执行任务，而用户的标签页完全不受干扰。

Ego Lite 的核心创新在于「代码驱动而非命令驱动」的设计理念。传统浏览器自动化工具（如 Browser-Use）要求 Agent 通过一系列 CLI 命令与浏览器交互（打开页面→查看→点击→再查看），形成低效的来回循环。Ego Lite 将浏览器能力封装为 JavaScript 函数，Agent 可以直接编写代码组合多步操作，在单次输出中完成整个工作流。实测表明，复杂任务下 Ego Lite 比竞品快 2.5 倍，且消耗的 Token 数更少。

另一个关键差异化是「继承 Chrome 数据」的能力。用户首次启动时可以选择迁移 Chrome 的登录信息、Cookie、扩展和书签，这意味着 Agent 可以直接使用用户已登录的网站账号执行任务，无需重新配置。Ego Lite 通过 `ego-browser` 技能层兼容 Claude Code、Codex、Cursor 等主流 Agent CLI，无需针对不同 Agent 做适配。

---

## 核心功能

1. **Agent 独立 Space**：每个 Agent 在完全隔离的 Space 中运行，用户可以随时查看哪个 Space 有 Agent 正在执行任务，并随时接管或停止。多个 Space 支持完全并行，例如 Claude Code 同时在 10 个 Space 中处理 10 个潜在客户，Codex 在另外 5 个 Space 中爬取网站。

2. **代码驱动的工作流**：浏览器能力封装为 JavaScript 函数（snapshot、fill、click、wait、navigate、capture），Agent 编写 JS 代码片段一次性完成多步操作，而非通过 CLI 命令逐步驱动。复杂任务效率提升达 2.5 倍。

3. **Chrome 数据继承**：首次启动时可迁移 Chrome 的登录状态、Cookie、扩展和书签，Agent 可直接使用用户已登录的网站账号，消除登录摩擦和配置成本。

4. **高质量页面快照**：内核级别的自定义生成页面快照，文本模型可准确「看到」并操作网页内容，可靠处理深度嵌套的 iframe——这是其他方案经常失败的场景。

5. **通用 Agent 兼容**：通过 `ego-browser` 连接层，支持任何 Agent CLI（Claude Code、Codex、Cursor 及自定义方案），不绑定特定 Agent 供应商。

6. **本地数据隐私**：所有浏览数据存储在用户本地设备上，Ego Lite 仅记录用户是否选择迁移 Chrome 数据的设置信息，不收集任何浏览行为数据。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 浏览器核心 | JavaScript（58.5%） + TypeScript（40.6%） |
| Agent 技能层 | ego-browser（JavaScript 模块） |
| 安装方式 | macOS 原生应用 / npx skills add |
| Agent 集成 | Claude Code、Codex、Cursor、自定义 CLI |
| 技能标准 | Agent Skills（.claude-plugin / .codex-plugin） |

---

## 项目亮点

### 与现有方案的定位差异

Ego Lite 的市场定位非常清晰：它既不是 Browser-Use 那样的自动化框架（需要单独的浏览器，登录状态无法迁移），也不是 ChatGPT Atlas/Perplexity Comet 那样的 AI 浏览器（内置 Agent，用户无法替换）。Ego Lite 是「一个浏览器，人类和任何 Agent 共享」——用户可以随时接入自己的 Claude Code、Codex 或 Cursor 来驱动浏览器任务，同时保持日常浏览体验不受干扰。

### 性能优势显著

在 Vercel agent-browser 的四项复杂浏览器自动化基准测试中，Ego Lite 每项任务均以最高 2.5 倍的速度优势胜出，且消耗的 Token 数量大幅减少。更值得注意的是，任务越复杂，Ego Lite 的优势越明显——这得益于其「代码驱动」的架构设计，避免了 CLI 命令式交互的来回往返开销。

---

## 应用场景

### AI Agent 批量网页操作

营销团队可以使用 Ego Lite 让 Claude Code 在 10 个并行 Space 中同时处理潜在客户资料——访问 LinkedIn 页面、提取关键信息、填写 CRM 表单。每个 Space 完全隔离，不存在标签页冲突或会话污染，用户可在自己的标签页中正常工作。

### 网站测试与爬取

开发者可以让 Codex 在多个 Space 中同时爬取不同网站的数据，或并行执行端到端测试。由于继承了 Chrome 的登录状态，Agent 可以直接访问需要认证的内部系统和付费 API，无需额外配置测试账号。

### 日常浏览 + AI 辅助并行

用户在浏览网页时，可以让 Agent 在后台 Space 中执行耗时任务（如批量下载、数据整理、表单填写），两者互不干扰。这是传统浏览器自动化工具无法实现的使用模式——因为它们要么独占浏览器，要么需要启动独立的浏览器实例。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 1,496 |
| 总 Forks | 86 |
| 主要语言 | JavaScript |
| 创建时间 | 2026-04-16 |
| 今日新增 Stars | 219 |

---

## 总结

Ego Lite 重新定义了「AI 浏览器」这一品类——不是为 AI 造一个专用浏览器，而是让人类日常使用的浏览器原生支持 AI Agent 并行工作。其代码驱动架构、Chrome 数据继承和通用 Agent 兼容性，使其在浏览器自动化赛道中形成了独特的差异化优势。

---

*数据来源：GitHub 仓库 (citrolabs/ego-lite)，2026 年 7 月访问*
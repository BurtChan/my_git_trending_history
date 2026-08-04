# Code Review Graph 项目分析

## 项目名称
**Code Review Graph** — 本地优先的代码智能图谱，为 AI 编码工具大幅减少上下文消耗
- **GitHub**: [tirth8205/code-review-graph](https://github.com/tirth8205/code-review-graph)
- **许可证**: MIT
- **官网**: https://code-review-graph.com

---

## 项目概述

Code Review Graph 是一个面向 AI 编码工具的本地优先代码智能图谱系统，通过构建代码库的持久化依赖关系图，帮助 AI 在代码审查时只读取真正相关的文件，而非盲目扫描整个项目。项目的核心理念是"Stop burning tokens. Start reviewing smarter."（停止浪费 token，开始更智能地审查）——它利用 Tree-sitter 将代码解析为 AST（抽象语法树），然后构建包含函数、类、导入等节点以及调用、继承、测试覆盖等边的图谱，在审查时查询图谱计算出 AI 需要读取的最小文件集合。

项目在 token 效率方面表现极为出色：在 FastAPI 仓库上实现了 528 倍的 token 缩减（从 951,071 tokens 降至 2,169 tokens），中位数约为 82 倍缩减。这意味着 AI 编码工具的上下文窗口可以更专注于真正相关的代码，大幅提升审查质量和响应速度。对于拥有数千甚至数万文件的大型代码库（monorepo），这一优势尤为显著——项目展示了在 27,700+ 文件的 monorepo 中，将 208,821 tokens 的原始语料缩减至约 2,495 tokens（93 倍缩减）的能力。

Code Review Graph 支持广泛的编程语言（Python、JS/TS/TSX、Go、Rust、Java、C/C++、C#、Ruby、Kotlin、Swift、PHP 等 30+ 种），并可通过 `code-review-graph install` 一条命令自动检测并配置用户已有的 AI 编码工具（Codex、Claude Code、Cursor、Windsurf、Zed、Continue、OpenCode、GitHub Copilot 等）。项目采用增量更新机制，文件保存和提交钩子触发的增量更新在 2 秒内即可完成（2,900 文件项目），确保图谱始终与代码库保持同步。

## 核心功能

| 功能 | 说明 |
|------|------|
| 代码 AST 解析 | 使用 Tree-sitter 将代码解析为 AST，提取函数、类、导入等节点 |
| 依赖关系图谱 | 构建节点（函数/类/导入）和边（调用/继承/测试覆盖）的持久化图谱 |
| 爆炸半径分析 | 文件变更时追踪所有调用者、依赖方和受影响的测试文件 |
| 增量更新 | 文件保存和提交钩子触发增量更新，仅重新解析变更文件，2,900 文件 < 2 秒 |
| 一键安装 | 自动检测 AI 编码工具并配置 MCP/Skills/Hooks（支持 15+ 工具） |
| Monorepo 支持 | 27,700+ 文件项目中排除无关文件，仅读取约 15 个相关文件 |
| 语义搜索 | 可选的嵌入向量搜索（支持 sentence-transformers、Gemini、MiniMax、OpenAI） |
| 交互式可视化 | D3.js 力导向图可视化，直观展示代码依赖关系 |
| Hub 与 Bridge 检测 | 识别代码库中连接度最高的"枢纽"节点和跨模块"桥梁"节点 |
| 自定义语言支持 | 通过 `.code-review-graph/languages.toml` 添加 Tree-sitter 尚未支持的语言 |

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | Python (91.6%) |
| 代码解析 | Tree-sitter（多语言 AST 解析器） |
| AI 工具集成 | MCP（Model Context Protocol）、Claude Code Skills、Git Hooks |
| 可视化 | D3.js（力导向图） |
| 嵌入向量 | sentence-transformers、Gemini、MiniMax、OpenAI 兼容端点 |
| 依赖管理 | uv（推荐）/ pip |
| 许可证 | MIT |

## 项目亮点

### 极致 Token 效率：中位数 82 倍缩减

Code Review Graph 最引人注目的成果是其 token 效率的数量级级提升。在 6 个主流开源项目的基准测试中，实现了 38 倍至 528 倍的 token 缩减，中位数约为 82 倍。这意味着 AI 编码工具不再需要将整个代码库塞入上下文窗口，而是通过图谱查询精确获取与变更相关的代码片段。对于 token 成本高昂的大型语言模型调用场景，这直接转化为显著的成本节省和质量提升——更少的不相关代码意味着更少的干扰和更精准的审查。

### 增量更新机制：毫秒级响应

传统代码索引工具在每次查询时都需要全量重建索引，耗时可能达到数十秒甚至数分钟。Code Review Graph 采用增量更新机制，在文件保存和代码提交时自动触发图谱差分更新——通过 SHA-256 哈希检查识别变更文件，仅重新解析受影响的部分。实测中，2,900 文件项目的增量更新在 2 秒内完成，使得图谱始终与代码库保持近乎实时的同步。这种"随时可用"的特性对于持续编码工作流至关重要。

### 一键安装，零配置接入

Code Review Graph 的 `code-review-graph install` 命令可以自动检测用户系统中已安装的 AI 编码工具（目前支持 Codex、Claude Code、Cursor、Windsurf、Zed、Continue、OpenCode、Antigravity、Gemini CLI、Qwen、Qoder、Kiro、GitHub Copilot 等 15+ 工具），并自动写入正确的 MCP 配置、安装钩子/技能、注入图谱感知指令。用户无需手动编辑配置文件或理解 MCP 协议细节，一行命令即可完成全部配置。这种"开箱即用"的设计大大降低了使用门槛。

### 30+ 种编程语言支持

得益于 Tree-sitter 的多语言解析能力，Code Review Graph 支持 Python、JavaScript/TypeScript/TSX、Go、Rust、Java、C/C++、C#、Ruby、Kotlin、Swift、PHP、Scala、Solidity、Dart、R、Perl、Lua、Objective-C、Shell、Elixir、Zig、PowerShell、Julia、ReScript、GDScript、Nix、Verilog/SystemVerilog、SQL、Vue/Svelte SFC、Astro、Jupyter Notebook 等 30+ 种语言。对于 Tree-sitter 尚未覆盖的语言，用户还可以通过 `.code-review-graph/languages.toml` 自定义添加，无需 fork 项目。

## 应用场景

### 大型代码库的 AI 辅助代码审查

在拥有数千甚至数万文件的大型代码库中，AI 编码工具的上下文窗口往往无法容纳整个项目，导致审查遗漏关键依赖关系。Code Review Graph 通过爆炸半径分析，精确识别代码变更影响的函数、类和文件，使 AI 只需关注真正相关的代码。这在 enterprise monorepo（企业单体仓库）场景中尤为有价值——项目展示了在 27,700+ 文件中仅读取约 15 个文件的能力。

### 多 AI 编码工具的统一图谱层

Code Review Graph 支持与 15+ 种主流 AI 编码工具集成，提供了一个统一的代码智能图谱层。这意味着无论团队使用 Claude Code、Cursor、Windsurf 还是 Codex，都可以共享同一个代码依赖图谱，确保不同工具在审查同一代码库时有一致的上下文理解。对于使用多种 AI 工具的团队，这避免了每种工具各自维护独立索引的冗余。

### 持续集成中的智能变更分析

Code Review Graph 的增量更新和爆炸半径分析能力使其非常适合集成到 CI/CD 流水线中。在代码提交触发 CI 时，图谱可以自动计算变更的影响范围，智能决定需要运行哪些测试——而非运行全部测试套件。结合 git hooks 的实时更新机制，可以在代码提交前就为开发者提供变更影响的即时反馈。

### 代码架构健康度可视化

项目内置的 D3.js 交互式可视化功能可以生成代码依赖关系的力导向图，直观展示代码库中的"枢纽"（hub，连接度最高的节点）和"桥梁"（bridge，跨模块连接节点）。这些可视化结果可以帮助架构师识别代码耦合热点、评估模块化程度、发现潜在的架构债务。对于大型团队的代码健康度监控具有实用价值。

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 19,613 |
| 🍴 Forks | 2,100 |
| 📅 创建时间 | 2026-02-26 |
| 🌐 语言 | Python |
| 📜 许可证 | MIT |
| 🔑 主题标签 | ai-coding、claude-code、code-review、mcp、tree-sitter、knowledge-graph、graphrag |



---

## 📋 更新记录

### 更新 2 — 2026 年 7 月 21 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：Code Review Graph（CRG）持续巩固其在 AI 辅助代码审查领域的核心地位。v2.3.4 版本正式兼容 MCP 1.0 标准，为 AI 编码工具提供标准化的代码上下文接口。新增对 Kiro 和 GitHub Copilot CLI 平台的原生支持，至此已覆盖 Claude Code、Cursor、Copilot、Codex、Gemini CLI 等所有主流 AI 编码工具。CRG 通过 Tree-sitter 构建代码的结构化图谱（函数、调用、导入、测试覆盖），在代码审查时计算最小文件集，实现 8.2 倍的上下文减少。Star 数即将突破 20K 里程碑，社区贡献和讨论活跃。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 19,613 | 19,988 | +375 |
| 总 Forks | 2,088 | ~2,113 | +25 |

**核心变化概要**：
- v2.3.4 发布，正式兼容 MCP 1.0 标准
- 新增 Kiro 和 GitHub Copilot CLI 平台支持，覆盖主流 AI 编码工具
- Star 数突破 20K 里程碑，社区活跃度持续攀升

---

## 📋 更新记录

### 更新 1 — 2026 年 7 月 22 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
- 自上次更新（7 月 20 日）以来，Star 数从约 20K 增长至 26,255，两日内新增超 6,200 Stars，增长势头极为迅猛
- 项目已发布 v2.3.4，正式兼容 MCP 1.0 标准，成为首批适配 MCP 1.0 的代码智能工具之一
- 新增 VS Code 扩展（code-review-graph-vscode），在 IDE 内直接提供代码图谱可视化和上下文查询
- 持续扩展 AI 编码工具支持：新增 Kiro、GitHub Copilot CLI、CodeBuddy 等平台集成，覆盖主流 AI 编码工具达 15+ 种
- 官方文档站点上线（code-review-graph.com），提供完整的安装指南、功能说明和基准测试数据

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 19,988 | 26,255 | +6,267 |
| 总 Forks | 2,200 | 2,340 | +140 |

**核心变化概要**：
- 两日内 Star 增长超 6,200（+31%），总 Star 突破 26K
- v2.3.4 发布，正式兼容 MCP 1.0 标准
- 新增 VS Code 扩展，支持 IDE 内直接使用
- AI 编码工具支持扩展至 15+ 种（含 Kiro、Copilot CLI、CodeBuddy）
- 官方文档站点 code-review-graph.com 上线

## 总结

Code Review Graph 是一个创新的本地优先代码智能图谱工具，通过 Tree-sitter AST 解析构建代码依赖关系图，实现了 AI 编码工具上下文的数量级级缩减（中位数 82 倍）。它支持 30+ 种编程语言、15+ 种 AI 编码工具的一键集成，增量更新机制确保图谱与代码库实时同步。对于任何面临大型代码库 AI 辅助审查挑战的开发团队来说，Code Review Graph 都是一个极具实用价值的工具——它让 AI 不再需要"读完整个代码库"，而是"只读真正需要的部分"。

---

*数据来源：GitHub 仓库 (tirth8205/code-review-graph)，2026 年 07 月访问*
*首次分析：见文件创建时间 | 最近更新：2026年07月22日*

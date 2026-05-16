# CodeGraph 项目分析

## 项目名称

**CodeGraph** — 为 Claude Code 提供预索引代码知识图谱，减少 94% 工具调用

- **GitHub**: [colbymchenry/codegraph](https://github.com/colbymchenry/codegraph)
- **许可证**: MIT

---

## 项目概述

**CodeGraph** 是一个为 AI 编码助手（特别是 Claude Code）设计的本地代码知识图谱系统，由拥有 15 年以上软件开发经验的 Colby McHenry 创建。项目的核心理念是：当 Claude Code 探索一个新的代码库时，它需要反复使用 grep、glob、Read 等工具调用来理解代码结构，这些"探索税"浪费了大量 token 和时间。CodeGraph 通过预先构建代码的语义知识图谱，让 AI 代理直接查询代码的符号关系、调用图和结构信息，从根本上解决了这个问题。

项目使用 TypeScript 开发，采用 SQLite 作为图数据库后端，实现 100% 本地运行。它通过 MCP（Model Context Protocol）协议与 Claude Code 集成，提供符号搜索、调用者追踪、上下文查询、影响分析等多种强大的代码导航工具。基准测试显示，使用 CodeGraph 后可以减少 92%-94% 的工具调用，探索速度提升 71%-77%。

CodeGraph 支持 19 种以上编程语言，包括 TypeScript、JavaScript、Python、Go、Rust、Java、C#、PHP、Ruby、C、C++、Swift、Kotlin、Dart、Svelte 等。即使是 VS Code 这样的大型项目，也能在十余秒内完成代码图谱构建。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **预索引代码图谱** | 自动分析代码库，构建包含符号定义、引用关系、调用图的语义知识图谱，存储在本地 SQLite 数据库中 |
| **MCP 服务器集成** | 通过 Model Context Protocol 与 Claude Code、Cursor、OpenAI Agents 等 AI 编码工具无缝集成 |
| **符号搜索 (codegraph_search)** | 快速搜索代码中的符号定义和引用，替代传统的 grep/ripgrep 扫描 |
| **调用者追踪 (codegraph_callers)** | 追踪函数/方法的调用链，快速了解"谁在调用这个函数" |
| **上下文查询 (codegraph_context)** | 获取符号的完整上下文信息，包括定义位置、类型签名、相关代码片段 |
| **影响分析 (codegraph_affected)** | 基于 diff 分析变更的影响范围，追踪依赖链，辅助代码审查和重构决策 |
| **流式代码片段** | 按需流式传输代码片段给 AI 代理，精确控制 token 消耗 |
| **交互式安装器** | 提供交互式安装程序，自动配置 Claude Code 的 MCP 设置和 CLAUDE.md 指令 |
| **19+ 语言支持** | 支持 TypeScript、JavaScript、Python、Go、Rust、Java、C#、PHP、Ruby、C/C++、Swift、Kotlin、Dart、Svelte 等 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | TypeScript |
| 图数据库 | SQLite |
| 集成协议 | MCP (Model Context Protocol) |
| 目标工具 | Claude Code、Cursor、OpenAI Agents |
| 配置方式 | .codegraph/config.json + CLAUDE.md |
| 许可证 | MIT |

---

## 项目亮点

1. **大幅降低 AI 编码成本**：基准测试显示 CodeGraph 可减少 92%-94% 的工具调用次数，探索速度提升 71%-77%，显著降低 API token 消耗和编码时间成本。

2. **100% 本地运行，隐私安全**：所有代码分析在本地完成，代码库内容不会发送到任何外部服务器，SQLite 数据库存储在本地 `.codegraph/` 目录，确保代码隐私安全。

3. **MCP 原生集成**：通过 MCP 协议与 Claude Code 深度集成，安装器自动配置 MCP 服务器和 CLAUDE.md 指令，用户几乎零配置即可使用。

4. **广泛的语言支持**：支持 19 种以上编程语言，覆盖主流后端、前端、移动端和系统编程语言，适用于几乎所有技术栈的代码库。

---

## 应用场景

1. **大型代码库开发**：在拥有数十万行代码的大型项目中，使用 CodeGraph 让 Claude Code 快速理解代码结构，无需逐文件扫描，大幅提升 AI 辅助编码效率。

2. **代码重构与影响分析**：进行大规模重构时，使用 CodeGraph 的 `affected` 功能分析变更影响范围，追踪依赖链，确保不遗漏任何需要修改的下游代码。

3. **代码审查辅助**：在 PR 审查中，CodeGraph 帮助 AI 代理快速理解变更的上下文和影响范围，提供更精准的审查建议。

4. **新人代码库上手**：新加入团队的成员可以通过 AI 代理 + CodeGraph 快速探索和理解代码库架构，大幅缩短上手时间。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ 总 Stars | 2,143 |
| 🍴 Forks | 191 |
| 📈 今日新增 | 397 |
| 📜 许可证 | MIT |
| 💻 主要语言 | TypeScript |

---

## 总结

CodeGraph 是 AI 编码工具生态中的一个关键基础设施项目，它通过预先构建代码知识图谱来解决 AI 代理在代码探索中的效率瓶颈。项目由经验丰富的开发者 Colby McHenry 创建，使用 TypeScript 和 SQLite 实现 100% 本地运行，通过 MCP 协议与 Claude Code 等主流 AI 编码工具无缝集成。基准测试证明它能减少 92% 以上的工具调用，显著降低 API 成本并提升编码速度。支持 19 种以上编程语言，适用于从个人项目到企业级代码库的各种场景，是提升 AI 辅助开发效率的重要工具。

# Everything Claude Code 项目分析

## 项目名称

**Everything Claude Code (ECC)** — AI 编码智能体的性能优化系统

- **GitHub**: [affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code)
- **许可证**: MIT
- **作者**: Affaan Mustafa（Anthropic 黑客马拉松获奖者）

---

## 项目概述

Everything Claude Code（ECC）是目前 GitHub 上最受欢迎的 AI 编码智能体配置系统，由 Anthropic 黑客马拉松获奖者 Affaan Mustafa 创建。项目汇集了 48 个智能体（Agent）、183 个技能（Skill）、规则集、钩子（Hook）和安全扫描工具，形成了一套完整的 AI 编码工作流优化方案。

ECC 的核心理念是**将 AI 编码智能体的最佳实践系统化、可移植化**。当开发团队开始认真使用 Claude Code、Cursor、Codex 等编码工具时，面临的共同挑战是：默认配置过于通用、项目间配置不共享、优化经验无法积累。ECC 将这些最佳实践打包为一套可版本控制、跨工具共享的配置系统，使团队能够在 Claude Code 和 Cursor 等不同工具间保持一致的 TDD 工作流、安全扫描和代码审查标准。

截至 2026 年 5 月，ECC 已获得 163K+ Stars、25.3K+ Forks、170+ 贡献者，覆盖 12+ 语言生态系统，是 GitHub 上增长最快的开发者工具仓库之一。ECC v2.0.0-rc.1 引入了跨智能体架构（Cross-Harness Architecture）和 Hermes 操作器故事，进一步扩展了对多种 AI 编码工具的支持。

---

## 核心功能

### 1. 48+ 编码智能体（Agents）
包括代码审查器、安全审计员（AgentShield）、构建修复器、C++/Go/Flutter/Rust 等语言专用智能体，覆盖完整的开发生命周期。

### 2. 183+ 技能（Skills）
技能是主要工作流界面，涵盖代码生成、测试驱动开发、性能优化、安全审计、文档生成等场景，支持跨项目复用。

### 3. 规则集（Rules）
模块化规则目录，按需复制到 `~/.claude/rules/ecc/`，覆盖代码风格、安全策略、架构约束等方面。

### 4. 钩子系统（Hooks）
Git 提交前自动触发安全扫描、代码质量检查等，确保每次提交符合团队标准。

### 5. 多模型命令
支持 `/multi-plan`、`/multi-execute`、`/multi-backend`、`/multi-frontend` 等多模型编排命令。

### 6. 安全审计（AgentShield）
内置安全扫描智能体，自动检测代码中的安全漏洞和合规问题。

### 7. 仪表盘 GUI
桌面仪表盘可可视化浏览 ECC 的所有组件、智能体和技能。

### 8. Claude Code 插件
支持作为 Claude Code 插件一键安装：`/plugin marketplace add` + `/plugin install`。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 配置格式 | Markdown（规则、技能、智能体） |
| 包管理 | npm / Claude Code Plugin |
| 钩子实现 | JSON 配置 |
| 脚本语言 | JavaScript / TypeScript / Python |
| 支持工具 | Claude Code、Cursor、Codex、OpenCode、Gemini |
| 操作系统 | Windows、macOS、Linux |
| 许可证 | MIT |

---

## 项目亮点

1. **163K+ Stars 的社区认可**：GitHub 上最热门的 AI 编码工具配置仓库，社区活跃度极高，170+ 贡献者持续贡献
2. **跨工具统一配置**：同一套配置可在 Claude Code、Cursor、Codex、OpenCode 等多种 AI 编码工具间共享，消除工具切换成本
3. **生产级工作流**：不仅提供配置，更提供完整的 TDD 工作流、安全扫描和代码审查自动化，来自 10+ 个月真实产品开发经验的沉淀
4. **模块化设计**：规则、技能、智能体完全解耦，用户可按需选择安装，不影响现有工作流

---

## 应用场景

1. **团队 AI 编码标准化**：为团队建立统一的 AI 编码规范和工作流，确保所有成员使用一致的代码质量标准
2. **个人 AI 编码效率提升**：一键安装 Claude Code 插件，获得预配置的代码审查、安全扫描和 TDD 工作流
3. **多语言项目开发**：覆盖 C++、Go、Flutter、Rust、Python、JS/TS 等 12+ 语言生态的专用智能体
4. **安全合规开发**：内置 AgentShield 安全审计，在代码提交阶段自动拦截安全问题

---

## Star 数据

| 指标 | 数据 |
|------|------|
| 总 Stars | ⭐ 163,000+ |
| 总 Forks | 🍴 25,300+ |
| 今日新增 | 📈 Trending Daily |
| 许可证 | MIT |
| 主要语言 | Markdown / JavaScript |
| 贡献者 | 170+ |
| 覆盖语言 | 12+ 生态系统 |

---

## 总结

Everything Claude Code 是 AI 编码智能体领域的"配置即基础设施"方案，将 Anthropic 黑客马拉松获奖者的 10+ 个月实战经验沉淀为一套可共享、可版本控制的智能体配置系统。163K+ Stars 的成绩证明了开发者社区对统一 AI 编码工作流的强烈需求。对于任何认真使用 Claude Code、Cursor 等 AI 编码工具的开发者或团队来说，ECC 都是值得安装和学习的标杆项目。

# Cline 项目分析

## 项目名称

**Cline** — 开源的自主编程 AI 智能体，直接运行在开发者的 IDE 中

- **GitHub**: [cline/cline](https://github.com/cline/cline)
- **许可证**: Apache License 2.0

---

## 项目概述

Cline（原名 Claude Dev）是一个**完全开源的自主编程智能体**，直接运行在开发者的编辑器中。它能创建和编辑文件、执行终端命令、使用浏览器等，且**每一步操作都需要用户许可**，在自主执行和人类监督之间取得独特平衡。

Cline 最初源自一次黑客松项目（未获奖），但随后迅速成长为 **GitHub 2025 年增长最快的 AI 开源项目**——根据 GitHub Octoverse 2025 报告，贡献者年增长率高达 **4,704%**。截至目前，Cline 在 VS Code Marketplace 的安装量已超过 **380 万次**。

Cline 的核心设计理念是**模型无关 + 人在环路**：支持 OpenAI、Anthropic、Google Gemini、AWS Bedrock、Azure、本地模型（Ollama 等）等任意 AI 模型，用户自带 API Key（BYOK）；同时每步操作都需要用户审批确认。2026 年 4 月，虽然 OpenAI 雇佣了部分 Cline 核心工程师，但项目仍在持续运营和迭代，当前版本为 **3.79.0**。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **Plan & Act 双模式** | Plan 模式用于规划分析，Act 模式用于自主执行；可针对不同模式使用不同模型以节省成本 |
| **文件创建与编辑** | 直接在编辑器中创建/编辑文件，提供 diff 视图展示更改内容 |
| **终端命令执行** | 在终端中直接执行命令，实时监控 linter/编译器错误并自动修复 |
| **浏览器自动化** | 启动无头浏览器进行网页开发和测试，支持点击、输入、滚动、截图和控制台日志捕获 |
| **MCP 协议支持** | 通过 Model Context Protocol 创建自定义工具扩展能力，如获取 Jira 工单、管理 AWS EC2 等 |
| **工作区快照与回滚** | 每一步自动拍摄工作区快照，可对比并恢复到之前的任意状态 |
| **上下文管理** | 添加 URL、文件、文件夹为任务提供丰富的上下文信息 |
| **Token 与成本追踪** | 实时追踪 Token 使用量和 API 调用成本，帮助预算管理 |
| **多模型 API 支持** | 支持 OpenAI、Anthropic、Google Gemini、AWS Bedrock、Azure、Ollama 等多种模型 API |
| **子智能体研究模式** | 可触发研究型子智能体进行深度分析和调研 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要语言** | TypeScript（100%） |
| **平台** | VS Code Extension（引擎要求 ^1.84.0）、JetBrains 插件、CLI |
| **AI 模型集成** | OpenAI API、Anthropic API、AWS Bedrock、Azure OpenAI、Google Vertex AI、Ollama |
| **构建工具** | npm scripts、npm-run-all |
| **测试框架** | Chai |
| **许可证** | Apache License 2.0 |
| **当前版本** | 3.79.0 |
| **发布者** | Cline Bot Inc.（创始人 saoudrizwan） |

---

## 项目亮点

### GitHub 2025 年增长最快的 AI 开源项目
被 GitHub Octoverse 2025 报告认可，贡献者年增长率 **4,704%**，超越所有其他 AI 项目，被评为定义 GitHub 的前 100 个项目之一。

### 真正的"人在环路"自主编程
与 Cursor/Copilot 的建议式交互不同，Cline 强调每步审批控制，AI 可以自主执行复杂多步骤任务，但每个关键操作都在人类监督之下。

### 模型无关的开源架构
唯一完全开源（Apache 2.0）、编辑器原生、支持任意 AI 模型的编程智能体，不受任何单一 AI 厂商绑定。

### 从设计图到应用的端到端能力
能将 UI 设计稿转换为功能完整的应用代码，结合浏览器自动化实现从开发到测试的完整闭环。

---

## 应用场景

### 功能开发与代码重构
开发者描述需求后，Cline 自主完成多文件编辑、代码重构和功能实现，适合日常代码库维护工作。

### Bug 修复与调试
Cline 能分析错误日志、定位问题、编写修复代码并运行测试验证，特别适合 Web 应用的端到端调试。

### 设计稿转应用（Mockup → App）
将 UI 设计图转换为功能性前端应用，利用浏览器自动化进行视觉验证，快速实现产品原型。

### 代码库学习与开源贡献
帮助开发者快速理解陌生代码库结构，降低开源贡献门槛，有实际案例显示开发者使用 Cline 首次成功贡献代码。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 60,671+ |
| **总 Forks** | 6,240+ |
| **今日新增 Stars** | 持续强劲增长 |
| **许可证** | Apache License 2.0 |
| **创建时间** | 2024 年 7 月 6 日 |
| **主要语言** | TypeScript |
| **VS Code 安装量** | 380 万+ |
| **支持平台** | VS Code、JetBrains、CLI |

---

## 总结

Cline 是**增长最快的开源 AI 编程智能体**，60k+ Stars、380 万安装量。它用 TypeScript 编写，作为 VS Code/JetBrains 插件运行，支持任意 AI 模型（OpenAI、Anthropic、本地模型等），通过 Plan & Act 双模式、浏览器自动化和 MCP 协议实现从设计到部署的端到端编程辅助。项目以 Apache 2.0 协议开源，被 GitHub Octoverse 2025 评为增长最快的 AI 项目，与 Cursor、GitHub Copilot、Claude Code 并列为顶级 AI 编程工具。

---

*数据来源：GitHub 仓库 (cline/cline)、GitHub Octoverse 2025 报告、Cline 官方博客（2026 年 4 月访问）*

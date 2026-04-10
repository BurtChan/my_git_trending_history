# Goose 项目分析

## 一句话总结

**Goose 是由 Linux 基金会旗下 Agentic AI Foundation (AAIF) 主导的开源通用 AI Agent，以 Rust 构建，提供桌面应用、CLI 和 API 三种使用形态，支持 15+ LLM 提供商和 70+ MCP 扩展，覆盖代码开发、自动化工作流、数据分析等广泛场景。**

---

## 基本信息

| 项目 | 详情 |
|------|------|
| **项目名称** | Goose |
| **GitHub 地址** | https://github.com/aaif-goose/goose |
| **组织** | Agentic AI Foundation (AAIF) @ Linux Foundation（原 Block 公司项目） |
| **许可证** | Apache 2.0 |
| **主要语言** | Rust (58.3%)、TypeScript (34.1%) |
| **Stars** | 38,465+ |
| **Forks** | 3,740+ |
| **贡献者** | 400+ |
| **当前版本** | v1.29.1（2026 年 4 月 3 日发布） |
| **跨平台** | macOS / Windows / Linux |

---

## 解决什么问题

现有的 AI 编码助手大多局限于代码补全和建议，缺乏真正的执行能力。Goose 的核心定位是"超越代码建议"——它是一个能在本地机器上**安装、执行、编辑和测试**的通用 AI Agent。用户不仅可以用它写代码，还能完成研究、写作、自动化、数据分析等任务。项目支持多种 LLM 后端和 MCP 扩展标准，解决了 Agent 工具被供应商锁定的问题。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **桌面应用** | 原生桌面客户端，支持 macOS、Linux、Windows |
| **CLI 命令行** | 完整的终端工作流支持，一条命令安装使用 |
| **API 接口** | 可嵌入任意应用的 API，便于二次开发 |
| **多 LLM 支持** | 支持 Anthropic、OpenAI、Google、Ollama、OpenRouter、Azure、Bedrock 等 15+ 提供商 |
| **ACP 订阅接入** | 可直接使用现有的 Claude、ChatGPT、Gemini 订阅，无需额外 API Key |
| **MCP 扩展生态** | 基于 Model Context Protocol 开放标准，支持 70+ 扩展连接工具和数据源 |
| **ACP 服务端** | 可作为 ACP Server，从 Zed、JetBrains、VS Code 等 IDE 接入 |
| **Recipes 工作流** | 将工作流捕获为可移植的 YAML 配置，支持团队共享和 CI 集成 |
| **MCP Apps** | 扩展可在桌面端渲染交互式 UI（按钮、表单、可视化） |
| **子 Agent（Subagents）** | 可生成独立子 Agent 并行处理任务（代码审查、研究、文件处理等） |
| **安全机制** | 提示注入检测、工具权限控制、沙箱模式、对手审查器 |

---

## 技术栈

| 技术 | 用途 |
|------|------|
| **Rust** | 核心引擎，提供高性能和跨平台能力 |
| **TypeScript** | 桌面应用 UI 和扩展开发 |
| **Model Context Protocol (MCP)** | 开放标准，连接 AI Agent 与工具/数据源 |
| **Agent Client Protocol (ACP)** | Agent 间通信标准，支持 IDE 集成 |
| **YAML (Recipes)** | 工作流配置与共享 |
| **V8 引擎** | 内嵌 JavaScript 运行时（用于扩展） |

---

## 典型使用场景

| 场景 | 说明 |
|------|------|
| **代码开发** | 代码生成、编辑、调试、测试，端到端的开发辅助 |
| **自动化工作流** | 通过 Recipes 定义和复用重复性任务流程，支持团队协作和 CI |
| **研究与写作** | 利用 LLM 能力进行资料研究、文档撰写、内容生成 |
| **数据分析** | 读取和处理数据文件，生成分析报告 |
| **IDE 集成** | 作为 ACP Server 从 Zed、VS Code、JetBrains 等编辑器调用 |
| **自定义 Agent 构建** | 通过 Custom Distributions 构建预配置的品牌化 Agent 分发版 |

---

## 项目特点

- **社区治理**：项目已从 Block 公司捐赠给 Linux 基金会的 Agentic AI Foundation (AAIF)，确保供应商中立和长期开放
- **开放标准优先**：深度集成 MCP 和 ACP 两大开放协议，强调互操作性
- **高性能原生应用**：Rust 构建，非 Electron 套壳，性能和资源占用表现优异
- **灵活接入**：既支持 API Key 调用，也支持现有订阅（Claude/ChatGPT/Gemini）直接接入

---

*数据来源：GitHub 仓库 README、goose-docs.ai 官方文档（2026 年 4 月访问）*

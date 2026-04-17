# Craft Agents 项目分析

## 项目名称

**Craft Agents** — 以文档为中心的开源 AI Agent 桌面客户端

- **GitHub**: [lukilabs/craft-agents-oss](https://github.com/lukilabs/craft-agents-oss)
- **许可证**: Apache License 2.0

---

## 项目概述

Craft Agents 是由知名笔记应用 Craft 的开发团队 Lukilabs 推出的一款开源 AI Agent 桌面客户端，其设计理念是"以文档为中心"而非以代码为中心。它基于 Claude Agent SDK 和 Pi SDK 构建，为用户提供直观的多任务处理、API 连接、会话共享以及高度可定制的用户界面。项目遵循 Agent 原生软件（Agent-Native Software）设计原则，通过描述性提示词让 AI 自主判断执行动作，而非通过繁琐的手动配置。

该项目的核心价值在于将多种 LLM 提供商（Anthropic Claude、OpenAI Codex、GitHub Copilot、OpenRouter、Ollama 等）整合到统一的桌面体验中，并原生支持 MCP（Model Context Protocol）协议来连接外部数据源（如 GitHub、Slack、Linear 等）。用户可以在一个应用内管理多个 AI 会话、连接多种 API 数据源，并通过自动化功能实现事件驱动的任务编排。

此外，Craft Agents 还支持无头远程服务器模式（Headless Server）和 CLI 客户端，使其不仅限于桌面 GUI 使用场景，还能在服务器端进行长时间运行的会话、CI/CD 管道集成和命令行交互。项目具备完善的安全机制，包括 AES-256-GCM 凭证加密存储和本地 MCP 服务器隔离，有效防止凭证泄露。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 多会话收件箱 | 支持会话归档、标记、状态管理和命名持久化 |
| 多 LLM 连接 | 支持 Anthropic Claude、OpenAI、GitHub Copilot、OpenRouter、Ollama 及自定义端点 |
| MCP 数据源集成 | 通过 MCP 协议连接 GitHub、Slack、Linear 等外部工具与服务 |
| REST API 和本地文件源 | 支持 REST API、本地文件作为数据源 |
| 三级权限模式 | 提供 safe、ask、allow-all 三种工具执行权限级别 |
| 后台任务执行 | 支持在后台运行长时间任务 |
| 多文件 Diff 对比 | 查看和对比多个文件的代码变更 |
| Skills 技能系统 | 可定义和复用的 AI 技能，支持 requiredSources 和 icon 元数据 |
| 自动化工作流 | 基于事件驱动的自动化任务，包括定时任务和标签变更触发 |
| 无头远程服务器模式 | 可在远程服务器上无界面运行 |
| CLI 客户端 | 支持命令行交互，适用于脚本和 CI/CD |
| 多语言国际化 | 支持匈牙利语、德语、波兰语等多语言翻译 |
| 一键安装 | macOS/Linux/Windows 均支持一行命令安装 |

---

## 技术栈

| 类别 | 技术 |
|------|------|
| 主要语言 | TypeScript |
| 运行时 | Bun（JavaScript/TypeScript 运行时） |
| AI SDK | Claude Agent SDK、Pi SDK |
| 桌面框架 | Electron |
| 前端框架 | React |
| UI 组件 | shadcn/ui |
| CSS 框架 | Tailwind CSS |
| 构建工具 | esbuild、Vite |
| 安全 | AES-256-GCM 加密存储 |
| 包管理 | Bun Workspaces（Monorepo 架构） |

---

## 项目亮点

1. **以文档为中心的 Agent 范式**：区别于传统以代码为中心的开发工具，Craft Agents 首创以文档为核心的工作流，让 AI Agent 更贴近知识工作者的使用习惯。
2. **多提供商无缝切换**：一个应用内支持 Anthropic、OpenAI、Copilot、OpenRouter、Ollama 等多种 LLM 后端，且 MCP 数据源可在所有提供商间通用代理，实现真正的"一次配置，处处可用"。
3. **安全至上设计**：采用 AES-256-GCM 加密凭证存储、本地 MCP 服务器隔离（过滤敏感环境变量防止凭证泄露）、Web-fetch SSRF 防护等多层安全机制。
4. **灵活部署模式**：同时支持桌面 GUI（Electron）、无头服务器和 CLI 三种运行模式，覆盖从日常使用到服务器端自动化部署的全场景。

---

## 应用场景

1. **多 Agent 协作办公**：团队成员可通过多会话管理和会话共享功能，在同一平台上与不同 AI Agent 协作完成文档编写、代码审查等任务。
2. **企业 AI 工具集成**：通过 MCP 协议连接 GitHub、Slack、Linear 等企业工具，将 AI Agent 无缝嵌入现有工作流，实现自动化项目管理。
3. **服务器端自动化**：利用无头服务器模式和 CLI 客户端，在 CI/CD 管道中集成 AI Agent，自动化代码审查、文档生成等流程。
4. **本地隐私敏感开发**：支持 Ollama 等本地模型提供商，开发者可在完全本地环境中运行 AI Agent，保障代码和数据隐私。

---

## Star 数据

| 指标 | 数据 |
|------|------|
| 总 Stars | ⭐ 4,200+ |
| 总 Forks | 🍴 622 |
| 主要语言 | TypeScript |
| 许可证 | Apache License 2.0 |
| 最新版本 | v0.8.9 |

---

## 总结

**Craft Agents（lukilabs/craft-agents-oss）** 是一款以文档为中心的开源 AI Agent 桌面客户端，由知名笔记应用 Craft 的开发团队 Lukilabs 推出。它将 Anthropic Claude、OpenAI、GitHub Copilot、Ollama 等多种 LLM 后端统一整合到一个美观流畅的桌面体验中，并原生支持 MCP 协议连接 GitHub、Slack 等外部工具。项目基于 TypeScript + Electron + React + Bun 技术栈构建，采用 Apache 2.0 许可证开源，当前已获得超过 4,200 个 GitHub Stars，是一个快速成长的 Agent 基础设施项目，适合从个人开发者到企业团队的多种 AI 工作流场景。

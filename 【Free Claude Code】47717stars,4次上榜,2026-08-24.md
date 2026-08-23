# Free Claude Code 项目分析

## 项目名称

**Free Claude Code** — 免费使用 Claude Code 的 API 代理服务器，将请求路由到免费或本地 LLM

- **GitHub**: [Alishahryar1/free-claude-code](https://github.com/Alishahryar1/free-claude-code)
- **许可证**: MIT License

---

## 项目概述

free-claude-code 是一个轻量级的 API 代理服务器，它拦截 Claude Code 的 API 请求，并将其路由到免费的或本地的 LLM 提供商（如 NVIDIA NIM、OpenRouter、LM Studio、llama.cpp 等），使用户无需 Anthropic API Key 即可免费使用 Claude Code CLI 和 VSCode 扩展。

该项目的核心理念是作为 Claude Code 的**即插即用替代品（Drop-in Replacement）**，只需设置 2 个环境变量即可使用，无需修改 Claude Code 本身的任何代码。此外，它还创新性地支持通过 Discord 或 Telegram 机器人远程控制 Claude Code 进行编程，甚至支持语音消息输入。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **零成本使用** | 通过 NVIDIA NIM（40 请求/分钟）、OpenRouter 等免费额度实现免费使用 |
| **即插即用** | 无需修改 Claude Code，直接作为代理替换，仅需 2 个环境变量 |
| **多提供商支持** | 支持 NVIDIA NIM、OpenRouter、DeepSeek、LM Studio、llama.cpp 五大后端 |
| **按模型映射** | 可将特定的 Claude 模型路由到不同的提供商 |
| **思维链支持** | 解析 `<thinking>` 标签，支持 Claude 的思考块输出 |
| **智能限流** | 智能节流机制防止 API 过度使用 |
| **Discord/Telegram 机器人** | 通过消息平台远程编程，支持会话持久化和实时进度显示 |
| **语音笔记** | 支持语音消息，自动转录并作为常规提示处理 |
| **子代理控制** | 防止子代理失控 |
| **高度可扩展** | 可轻松添加自定义提供商和消息平台 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **Web 框架** | FastAPI（uvicorn ASGI 服务器） |
| **AI SDK** | OpenAI Python SDK |
| **消息平台** | discord.py + python-telegram-bot |
| **语音处理** | Whisper（语音转文字） |
| **包管理** | uv（现代 Python 包管理工具） |
| **主要语言** | Python（99.5%）+ Shell（0.5%） |

---

## 项目亮点

1. **零门槛入门** — 仅需 2 个环境变量配置，极大降低了使用门槛
2. **多后端冗余** — 支持多个免费 LLM 后端提供商，确保可用性和灵活性
3. **本地运行能力** — 通过 LM Studio 和 llama.cpp 支持完全离线/本地运行
4. **远程编程能力** — 通过 Discord/Telegram 可随时随地使用 Claude Code

---

## 应用场景

1. **个人开发者免费使用 Claude Code**：无需 Anthropic API Key 即可体验 Claude Code 编程辅助
2. **本地隐私开发**：通过 LM Studio/llama.cpp 本地部署，完全离线 AI 编程助手
3. **远程编程协作**：通过 Discord/Telegram 机器人随时随地发起编程任务
4. **多模型对比测试**：利用不同提供商的模型进行对比测试，选择最优方案

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | ~47,717 |
| **Forks** | ~740 |
| **今日新增** | 持续保持增长态势，日均增长数十至上百 Star |
| **许可证** | MIT License |
| **主要语言** | Python |

---

## 总结

free-claude-code 是一个巧妙的开源项目，通过代理机制让开发者无需 Anthropic API Key 即可免费使用 Claude Code。项目基于 FastAPI 构建轻量级代理服务，支持 NVIDIA NIM、OpenRouter、LM Studio 等多个后端，还集成了 Discord/Telegram 远程控制和语音输入等特色功能。凭借 MIT 协议、极低的使用门槛和丰富的功能，在短时间内吸引了近 4,000 Star，是 AI 编程工具领域值得关注的开源项目。
---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 3 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单，Star 数出现爆发式增长

**最新动态**：
free-claude-code 自首次分析以来实现了惊人的 **10 倍以上增长**，Star 数从约 3,900 飙升至 **43,847**（+39,947）。这一爆发式增长与 2025-2026 年 AI 编程工具的浪潮高度吻合——Claude Code 成为最受开发者欢迎的 AI 编程助手之一，而 free-claude-code 作为零成本使用 Claude Code 的唯一可行方案，自然成为社区关注的焦点。项目持续支持 NVIDIA NIM、OpenRouter、LM Studio、llama.cpp 等后端，Discord/Telegram 远程编程功能也持续迭代。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | ~3,900 | 43,847 | +39,947 |

**核心变化概要**：
- Star 数从约 3,900 增长至 43,847，增幅超 **10 倍**，进入 GitHub 4 万 Star 俱乐部
- AI 编程工具（特别是 Claude Code）在 2025-2026 年成为主流开发方式，免费代理需求井喷
- 项目作为「零成本使用 Claude Code」的唯一可行方案，持续获得社区高度关注
- 多后端支持（NVIDIA NIM、OpenRouter、DeepSeek、LM Studio、llama.cpp）确保了灵活性和可用性

### 更新 2 — 2026 年 8 月 4 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
- 项目已支持 **30+ 提供商**，包括 Claude Code、Codex CLI、Pi 等主流 AI 编码代理，生态覆盖面持续扩大
- 技术栈升级至 **Python 3.14**，采用 uv 包管理和 Pytest 测试框架，累计提交达 871 次
- 新增 **Claude Code 分层路由**（Fable/Opus/Sonnet/Haiku），支持根据任务复杂度智能选择模型层级
- 支持语音输入，集成**桌面系统集成**（系统托盘/菜单栏），管理后台可通过 localhost:8082 访问

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 43,847 | 43,913 | +66 |
| 总 Forks | — | 7,247 | — |

**核心变化概要**：
- Star 数从 43,847 增至 43,913（+66），增长趋于平稳，进入成熟期
- 提供商数量从 5 大后端扩展至 30+，覆盖几乎所有主流 AI 编码代理
- Claude Code 分层路由（Fable/Opus/Sonnet/Haiku）实现精细化成本控制
- 桌面集成和管理后台使项目从 CLI 工具升级为完整的桌面应用方案

### 更新 3 — 2026年8月4日（再次登上 Trending）

**最新 Star 数据**：

| 总 Stars | 43,913 | 44,169 | +256 |

- Star 数从 43,913 增至 44,169（+256），日增 278 颗 Star

**更新原因**：项目再次登上 GitHub Trending 榜单，Star 数从 43,913 增长至 44,169（+256），日增 278 颗 Star

Star 增长 256 颗，日增 278 颗（Trending）。Use Claude Code, Codex and Pi for free from your terminal, app, IDE, or phone like OpenClaw (voice supported)

> 更新依据：GitHub Trending 2026-08-04 数据，Star 数由 GitHub API 实时获取

---

### 更新 4 — 2026 年 8 月 24 日（再次登上 Trending）
**更新原因**：项目时隔 20 天再次登上 GitHub Trending 榜单，Star 持续高速增长

**最新动态**：
- Star 数从 44,169 增至 47,717（+3,548），今日单日新增 1,040 Stars，免费使用 Claude Code 的需求持续旺盛。
- 项目已支持从终端、App、IDE、手机多种入口免费使用 Claude Code / Codex / Pi，并支持类 OpenClaw 的语音输入。
- Fork 数增至 7,852，社区围绕多后端（NVIDIA NIM、OpenRouter、LM Studio、llama.cpp）的部署与定制活跃。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 44,169 | 47,717 | +3,548 |
| 总 Forks | 7,247 | 7,852 | +605 |

**核心变化概要**：
1. Star 从 44,169 增至 47,717（+3,548），第 4 次登上 Trending
2. 支持终端/App/IDE/手机多入口 + 语音输入
3. Fork 增至 7,852，多后端部署生态活跃

---

*数据来源：GitHub 仓库 (Alishahryar1/free-claude-code)，2026 年 8 月访问*
*首次分析：2026 年 8 月 | 最近更新：2026 年 8 月 24 日*

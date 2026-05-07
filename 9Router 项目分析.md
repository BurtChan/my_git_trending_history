# 9Router 项目分析

## 项目名称

**9Router** — 免费 AI 路由器，连接所有 AI 编码工具到 40+ 提供商，节省 Token

- **GitHub**: [decolua/9router](https://github.com/decolua/9router)
- **许可证**: MIT

---

## 项目概述

9Router 是一款**免费开源的 AI 模型路由器**，专为 AI 编码工具用户设计。它充当中间代理层，将 Claude Code、Codex、Cursor、Cline、Copilot、Antigravity、OpenCode、OpenClaw 等主流 AI 编码工具统一连接到 40 多个 AI 提供商和 100 多个模型，实现智能路由、自动降级和 Token 节省。

9Router 的核心价值在于解决 AI 编码工具的三大痛点：**成本高昂、模型单一、配额耗尽导致工作中断**。通过 RTK（Runtime Token Kompression）技术，9Router 能在每次请求中自动压缩工具输出，节省 20-40% 的 Token 消耗；通过智能三级降级机制（订阅 → 低价 → 免费），确保编码工作永不中断。

项目基于 Node.js 开发，通过 `npm install -g 9router` 即可全局安装，支持 localhost、VPS、Docker 和 Cloudflare Workers 等多种部署方式。对于拥有 Claude Pro、OpenAI 订阅的开发者，9Router 能最大化利用订阅配额；对于零预算用户，则可通过 Kiro AI、OpenCode Free、Vertex AI 等免费提供商实现完全免费的 AI 编码体验。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **RTK Token 节省** | 自动压缩工具结果后再发送给 LLM，每次请求节省 20-40% Token |
| **智能三级降级** | 自动在订阅模型、低价模型、免费模型之间切换，避免中断 |
| **实时配额追踪** | 监控所有提供商的 Token 用量和重置倒计时 |
| **格式翻译** | 无缝转换 OpenAI、Claude、Gemini、Cursor、Kiro、Vertex 等不同 API 格式 |
| **多账户支持** | 同一提供商支持多账户轮询或优先级路由 |
| **自动 Token 刷新** | OAuth 令牌到期前自动刷新 |
| **自定义组合** | 创建和管理无限数量的模型组合 |
| **请求日志** | 调试模式下记录完整的请求/响应日志 |
| **云端同步** | 跨设备同步配置 |
| **使用分析** | 追踪 Token 用量、成本和趋势 |
| **随处部署** | 支持 localhost、VPS、Docker、Cloudflare Workers |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | JavaScript |
| **运行时** | Node.js |
| **安装方式** | npm 全局安装 (`npm install -g 9router`) |
| **支持工具** | Claude Code、Codex、Cursor、Cline、Copilot、Antigravity、OpenCode、OpenClaw 等 |
| **支持提供商** | 40+ 提供商（Claude、OpenAI、Gemini、DeepSeek、GLM、Kimi、MiniMax、Groq 等） |
| **部署方式** | localhost / VPS / Docker / Cloudflare Workers |
| **许可证** | MIT |

---

## 项目亮点

### 极致的成本优化
RTK 技术通过压缩工具输出实现 20-40% 的 Token 节省，加上智能降级到免费模型的能力，让开发者可以大幅降低 AI 编码的成本，甚至实现零成本使用。

### 40+ 提供商的统一接入
一个路由器统一管理 Claude、GPT、Gemini、DeepSeek、GLM、MiniMax 等 40 多个 AI 提供商，配合 100+ 模型选择，开发者不再被单一提供商锁定。

### 永不中断的编码体验
三级降级机制确保当主力模型配额耗尽时，自动切换到备用模型，实现 7×24 小时不间断的 AI 编码辅助。

### 灵活的部署选项
从本地 localhost 到 Cloudflare Workers 全球边缘网络，9Router 支持各种部署场景，个人开发者和小团队都能找到适合的方案。

---

## 应用场景

### 订阅最大化利用
拥有 Claude Pro 或 ChatGPT Plus 订阅的开发者，通过 9Router 确保每一分订阅费都被充分利用，配额重置前自动降级到免费模型。

### 零成本 AI 编码
利用 Kiro AI（Claude 4.5 + GLM-5 + MiniMax）、OpenCode Free、Vertex AI（新用户 $300 额度）等免费提供商，实现完全免费的 AI 编码体验。

### 团队协作 AI 编码
多账户轮询功能让团队成员共享多个 AI 提供商账户，配合使用分析追踪团队成本。

### 聊天机器人免费 AI
通过 OpenClaw 集成，将免费 AI 模型接入 WhatsApp、Telegram、Slack 等聊天平台，实现零成本的 AI 助手。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **今日新增 Stars** | ~130 |
| **许可证** | MIT |
| **主要语言** | JavaScript |
| **支持工具数** | 10+ AI 编码工具 |
| **支持提供商数** | 40+ AI 提供商 |

---

## 总结

9Router 是一款面向 AI 编码工具用户的**智能模型路由器和成本优化工具**。它基于 Node.js 开发，支持 Claude Code、Cursor、Codex 等 10+ 编码工具连接到 40+ AI 提供商的 100+ 模型，通过 RTK 技术节省 20-40% Token，通过智能三级降级确保编码永不中断。项目采用 MIT 许可证，支持多种部署方式，适合追求成本优化和无缝编码体验的开发者。

---

*数据来源：GitHub 仓库 (decolua/9router)（2026 年 5 月访问）*

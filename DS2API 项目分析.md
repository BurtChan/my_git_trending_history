# DS2API 项目分析

## 项目名称

**DS2API** — DeepSeek 客户端协议转通用 API 全栈中间件工具

- **GitHub**: [CJackHwang/ds2api](https://github.com/CJackHwang/ds2api)
- **许可证**: AGPL-3.0

---

## 项目概述

DS2API 是一款轻量、高性能的全栈中间件工具，能够将 DeepSeek Web 端的对话能力转换为兼容 OpenAI、Claude 和 Gemini 的标准 API 接口。项目由开发者 CJackHwang 于 2026 年 1 月创建，完全使用 Go 语言编写后端，搭配 React 构建的前端 WebUI 管理控制台，旨在为用户提供一个零成本接入 DeepSeek 大模型的统一 API 网关。

DS2API 的核心设计理念是**协议桥接**：通过逆向分析 DeepSeek Web 客户端的通信协议，将非标准的客户端对话协议翻译为业界通用的 OpenAI Chat Completions、Anthropic Messages 和 Google Gemini API 格式。这意味着任何已经接入 OpenAI API 的应用——包括 Claude Code、OpenCode、Roo Code 等编码工具，以及各类 AI 应用——都可以零修改地切换到 DeepSeek 后端。

项目支持多种部署方式：预编译二进制文件（支持多平台）、Docker 容器、Vercel Serverless 函数以及 Zeabur 平台一键部署。同时内置了完善的 WebUI 管理控制台，支持账号池管理、运行时配置、代理管理、会话记录查看等功能，提供了完整的运维体验。

---

## 核心功能

### 1. 多协议 API 兼容
完整兼容 OpenAI、Claude（Anthropic）和 Gemini 三大 API 格式，包括 Chat Completions、Embeddings、Responses、Models 等接口，客户端无需任何修改即可接入。

### 2. 多账号轮询与池管理
支持配置多个 DeepSeek 账号进行轮询负载均衡，自动处理 Token 刷新、邮箱/手机双登录模式，支持账号并发限制（In-flight）和等待队列。

### 3. DeepSeek PoW 纯 Go 实现
高性能的 Proof-of-Work 算法纯 Go 语言实现，用于 DeepSeek 客户端认证，相比其他语言实现性能更优。

### 4. Tool Calling 智能适配
针对 DeepSeek 客户端的 Tool Calling 行为进行特殊处理，包括防泄露检测、增量输出、XML/Markup 解析以及协议格式转换，确保工具调用在不同 API 格式间正确传递。

### 5. WebUI 管理控制台
基于 React 构建的完整管理后台，支持多语言切换和暗色模式，提供配置管理、账号管理、代理管理、服务端会话记录查看等功能。

### 6. Admin API 管理接口
提供完整的 RESTful 管理接口（JWT 鉴权），支持运行时配置修改、账号测试、会话清理、配置导入导出等运维操作。

### 7. 多平台部署
- **二进制文件**: GitHub Actions 自动构建多平台预编译包
- **Docker**: 支持 docker-compose 一键启动
- **Vercel**: Serverless 部署，适合已有 Vercel 基础设施的用户
- **Zeabur**: 平台一键部署
- **本地源码**: Go 1.26+ 和 Node.js 20.19+ 环境

### 8. 流式响应支持
完整的 SSE（Server-Sent Events）流式输出支持，兼容各协议的流式调用模式。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 后端语言 | Go (Golang) |
| 前端框架 | React |
| 部署容器 | Docker / Vercel Serverless |
| 认证方式 | Bearer Token / API Key / JWT (Admin) |
| 配置管理 | config.json / 环境变量 |
| CI/CD | GitHub Actions |
| 许可证 | AGPL-3.0 |

---

## 项目亮点

1. **三大 API 协议统一桥接**: 同时兼容 OpenAI、Claude、Gemini 三种 API 格式，一个服务覆盖所有主流 AI 客户端，极大降低了接入成本。

2. **纯 Go 高性能实现**: 后端完全使用 Go 语言编写，包括 DeepSeek PoW 算法的原生实现，相比基于 Node.js 或 Python 的方案具有显著的性能优势，适合高并发场景。

3. **完善的管理体系**: 内置 WebUI 管理控制台和 Admin API，提供从账号池管理到运行时监控的完整运维能力，而非简单的协议转发代理。

4. **灵活的多平台部署**: 从二进制文件到 Serverless 函数，从 Docker 到 Vercel，覆盖了从个人开发到团队使用的各种部署场景，上手门槛极低。

---

## 应用场景

1. **AI 编码工具接入**: 将 Claude Code、OpenCode、Roo Code 等 AI 编码工具的后端从 OpenAI/Claude API 切换为 DeepSeek，利用 DeepSeek 的性价比优势降低使用成本。

2. **AI 应用统一网关**: 为企业内部多个 AI 应用提供统一的 DeepSeek API 接入层，通过账号池轮询实现负载均衡和高可用。

3. **API 兼容性测试**: 开发者可以使用 DS2API 快速验证自己的应用在不同 API 协议（OpenAI/Claude/Gemini）下的兼容性表现。

4. **个人学习与研究**: 作为学习 API 协议转换、逆向工程、Go 语言 Web 开发的参考项目，项目文档完善，代码结构清晰。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | ⭐ 1,310 |
| 总 Forks | 🍴 436 |
| 主要语言 | Go |
| 许可证 | AGPL-3.0 |
| 创建时间 | 2026-01-21 |
| 开放 Issues | 12 |

---

## 总结

DS2API 是一款实用的 DeepSeek API 桥接中间件，通过协议转换技术将 DeepSeek Web 客户端能力暴露为标准 API 接口，同时兼容 OpenAI、Claude 和 Gemini 三大格式。项目以 Go 语言为核心，具备高性能、轻量级的特点，配合完善的 WebUI 管理控制台和多平台部署支持，为希望利用 DeepSeek 模型能力的开发者和团队提供了便捷的接入方案。该项目特别适合需要将现有 AI 应用快速迁移到 DeepSeek 后端、或希望以低成本使用高质量大模型能力的用户群体。

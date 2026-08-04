# OpenConnector 项目分析

## 项目名称

**OpenConnector** — 开源认证网关，连接 1000+ SaaS 提供商到 AI Agent

- **GitHub**: [oomol-lab/open-connector](https://github.com/oomol-lab/open-connector)
- **许可证**: Apache License 2.0

---

## 项目概述

OpenConnector 是由 OOMOL Lab 开发的开源认证网关，定位为 Composio 的开源替代品。它的核心能力是让 AI Agent 通过统一的接口安全地访问和操作上千个 SaaS 服务（GitHub、Gmail、Notion、Slack、BigQuery、Airtable 等），无需每个服务单独集成。项目创建于 2025 年 6 月底，在短短一个月内已获得超过 3600 Stars，增长势头强劲。

项目的核心设计理念是将「认证与授权」从 Agent 逻辑中完全解耦。Agent 不直接持有任何 API 密钥或 OAuth Token，而是通过 SDK/CLI/MCP/HTTP 等标准接口调用网关，由网关在安全边界内处理凭证管理、Token 刷新、权限范围控制和操作审计。这种架构让 Agent 开发者只需关注业务逻辑，认证复杂性由网关统一承担。

项目提供了完整的开发者工具链：TypeScript SDK 用于编程集成，oo CLI 用于本地调试，MCP 协议支持直接对接各类 Agent 宿主（如 Claude Desktop），HTTP/OpenAPI 接口支持任意语言调用。部署方式灵活——支持本地 Docker 自托管、Fly.io 云托管、Cloudflare Workers 轻量部署，以及 OOMOL 官方托管服务（含预配置 OAuth 应用）。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **连接器目录** | 内置 1000+ SaaS 提供商连接器，涵盖 GitHub、Gmail、Notion、Slack、BigQuery、Supabase 等 |
| **凭证管理** | 支持 API Key、OAuth2、自定义凭证和无认证四种模式，Token 自动刷新 |
| **Action 合约** | 每个 Action 提供 request/response Schema、所需权限范围，支持懒加载执行器 |
| **运行时控制** | 连接身份管理、权限范围控制、Action 白名单/黑名单、临时文件中转、脱敏运行日志 |
| **多部署目标** | 本地 Docker/Node.js、Fly.io（SQLite）、Cloudflare Workers（D1/R2）、OOMOL 托管 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要语言** | TypeScript |
| **框架** | Node.js 22+、Docker、Cloudflare Workers |
| **许可证** | Apache License 2.0 |
| **接口协议** | MCP、HTTP/REST、OpenAPI、SDK |
| **数据存储** | SQLite（本地/Fly.io）、Cloudflare D1（Workers） |
| **容器镜像** | ghcr.io/oomol-lab/open-connector |

---

## 项目亮点

### 统一认证边界
Agent 永远不接触原始凭证，所有 API 密钥和 OAuth Token 严格停留在网关运行时边界内。Agent 只接收元数据、安全的账户标签和执行结果，从根本上降低了凭证泄露风险。

### 多协议接入
同一套连接器目录通过 SDK（编程集成）、CLI（本地调试）、MCP（Agent 宿主对接）、HTTP/OpenAPI（任意语言调用）四种方式暴露，开发者可以按需选择最合适的集成路径。

### 灵活部署策略
从完全自控的本地 Docker 部署，到零运维的 Cloudflare Workers 边缘部署，再到开箱即用的 OOMOL 托管服务（预配 OAuth 应用），覆盖了从个人开发到生产环境的完整部署需求。

### Action 可检视性
每个 Action 提供完整的请求/响应 Schema 和所需权限范围，开发者可以在调用前精确了解数据流向和权限需求，实现安全审计前置。

---

## 应用场景

### AI Agent SaaS 集成
让 AI Agent 安全地操作用户的 SaaS 服务——读取 Gmail 邮件、管理 Notion 页面、查询 BigQuery 数据等，无需每个服务单独开发认证模块。

### MCP 工具扩展
为支持 MCP 协议的 Agent 宿主（如 Claude Desktop）快速扩展上千个 SaaS 工具能力，通过 `http://localhost:3000/mcp` 即可接入。

### 企业内部自动化
作为企业内部 AI 系统的统一 API 网关，集中管理所有 SaaS 连接的认证、授权和审计日志。

### 开发者工具链集成
通过 OpenAPI 规范自动生成客户端代码，或将连接器目录嵌入 CI/CD 流水线，实现自动化运维。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 3,624 |
| **总 Forks** | 288 |
| **今日新增 Stars** | ~100+（Trending 日） |
| **许可证** | Apache License 2.0 |
| **主要语言** | TypeScript |
| **创建时间** | 2025-06-29 |
| **Open Issues** | 7 |

---

## 总结

OpenConnector 是 **面向 AI Agent 的开源 SaaS 集成网关**，3.6K Stars。它通过统一的认证边界和 Action 目录，让 Agent 安全地连接 1000+ SaaS 服务，提供了 SDK、CLI、MCP、HTTP 四种接入方式，支持从本地 Docker 到 Cloudflare Workers 的多种部署方案。作为 Composio 的开源替代，项目在一个月内快速获得社区认可，技术架构清晰，实用性强，是 AI Agent 基础设施领域值得关注的项目。

---

*数据来源：GitHub 仓库 (oomol-lab/open-connector)，2025 年 7 月访问*

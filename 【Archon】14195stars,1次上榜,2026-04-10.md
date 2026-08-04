> Archon 是 AI 编程助手的「指挥中心」——通过 MCP 协议将自定义知识库和任务管理系统直接接入 Claude Code、Cursor 等工具，让 AI 真正理解你的项目上下文。

---

## 基本信息

| 项目 | 信息 |
| --- | --- |
| 名称 | Archon (Archon OS) |
| GitHub URL | https://github.com/coleam00/Archon |
| Stars | ~14,195 (+138 today) |
| Forks | Trendshift 排名前列 |
| 许可证 | Archon Community License (ACL) v1.2（免费使用、可 Fork，但不得作为服务转售） |
| 主要语言 | Python (后端)、TypeScript/React (前端) |
| 作者 | coleam00 (Dynamous AI Mastery 社区) |
| 当前状态 | Beta 阶段，活跃开发中 |

---

## 解决什么问题

当前 AI 编程助手（如 Claude Code、Cursor、Windsurf 等）面临一个核心痛点：**上下文缺失**。它们不知道你的项目文档、技术规范、任务进度等关键信息，导致生成的代码常常偏离实际需求。

Archon 解决的问题包括：

1. **知识孤岛**：项目文档散落在各处（网站、PDF、Markdown），AI 助手无法统一检索
2. **上下文断裂**：每次对话都要重新描述项目背景，AI 无法持久化理解项目全貌
3. **任务脱节**：AI 助手与项目任务管理系统完全割裂，无法感知开发进度和优先级
4. **工具隔离**：不同 AI 编程工具之间无法共享同一套知识库和任务上下文

Archon 的核心理念是：**人机共用同一套知识库和任务系统**。你通过 Web 界面管理知识与任务，AI 编程助手通过 MCP 协议读取同一份数据，实现真正的上下文协作。

---

## 核心功能

### 1. 智能知识管理
- **网站自动爬取**：输入文档 URL，自动检测并爬取整站文档（支持 sitemap、单页、全站）
- **多格式文档处理**：上传 PDF、Word、Markdown、纯文本文件，智能分块索引
- **代码示例提取**：自动识别文档中的代码片段并单独建立索引
- **向量语义搜索**：基于 PGVector 的高级语义搜索，支持上下文嵌入
- **来源管理**：按来源、类型、标签组织和过滤知识条目

### 2. MCP 协议集成
- **Model Context Protocol 服务端**：作为 MCP Server 运行，兼容 Claude Code、Cursor、Kiro、Windsurf、Claude Desktop 等所有 MCP 客户端
- **MCP 工具集**：提供 RAG 查询、任务管理、项目操作等完整工具集
- **实时流式响应**：AI Agent 响应支持实时流式输出和进度追踪
- **多 LLM 支持**：兼容 OpenAI、Ollama、Google Gemini 模型

### 3. 项目与任务管理
- **层级化项目结构**：项目 -> 功能 -> 任务的三级组织体系
- **AI 辅助创建**：通过内置 AI Agent 自动生成项目需求和任务拆解
- **文档版本管理**：支持文档版本控制和协作编辑
- **进度追踪**：实时更新任务状态，人机同步可见

### 4. 高级 RAG 策略
- **混合搜索**：结合关键词和语义向量的混合检索
- **上下文嵌入**：更精准的上下文感知 embedding
- **结果重排序 (Reranking)**：对检索结果二次排序，提升回答质量

### 5. 实时协作
- **WebSocket 实时更新**：爬取、处理、AI 操作全程实时进度追踪
- **多用户支持**：团队协作构建知识库和管理项目
- **后台异步处理**：不阻塞界面的异步操作机制
- **健康监控**：内置服务健康检查和自动重连

---

## 技术栈

### 后端
| 组件 | 技术 |
| --- | --- |
| API 服务 | FastAPI + SocketIO |
| MCP 服务端 | 轻量 HTTP Wrapper (Python) |
| AI Agent 服务 | PydanticAI |
| 数据库 | Supabase (PostgreSQL + PGVector) |
| 容器化 | Docker Compose 微服务架构 |

### 前端
| 组件 | 技术 |
| --- | --- |
| 框架 | React + Vite |
| 语言 | TypeScript |
| 样式 | TailwindCSS |
| 实时通信 | Socket.IO Client |

### 架构特点
- **真微服务架构**：Server、MCP Server、Agents Service、UI 四个独立服务，无共享代码依赖
- **HTTP 服务间通信**：所有服务间通信基于 HTTP API
- **独立扩展**：每个服务可独立扩容
- **开发模式灵活**：支持混合开发（后端 Docker + 前端本地热重载）和全 Docker 模式

---

## 使用场景

### 1. 企业级 AI 辅助开发
团队将内部技术文档、架构设计、API 规范等上传至 Archon，所有开发者通过 Cursor 或 Claude Code 编码时自动获取企业知识上下文，代码生成质量显著提升。

### 2. 开源项目贡献
贡献者爬取项目官方文档至 Archon，AI 编程助手在编码时直接检索最新 API 用法和最佳实践，减少因文档过时导致的错误。

### 3. 技术学习与研究
学习新技术时，将官方文档、教程 PDF、博客文章等统一归档到 Archon，通过 AI 助手基于知识库进行问答，获得精准的上下文感知回答。

### 4. 跨工具统一上下文
在 Claude Code 写后端、Cursor 写前端、Windsurf 做调试时，所有工具共享同一套知识库和任务上下文，保持开发一致性。

### 5. Agent 工作流自动化
通过 Agent Work Orders 服务（可选），自动化执行 Claude Code CLI 工作流，结合知识库实现端到端的任务执行。

---

## 快速上手

1. **前置条件**：Docker Desktop、Supabase 账户、OpenAI API Key
2. **克隆仓库**：`git clone -b stable https://github.com/coleam00/archon.git`
3. **配置环境**：复制 `.env.example` 为 `.env`，填入 Supabase 凭证
4. **初始化数据库**：在 Supabase SQL 编辑器执行 `migration/complete_setup.sql`
5. **启动服务**：`docker compose up --build -d`
6. **访问界面**：打开 http://localhost:3737 完成 API Key 配置
7. **连接 AI 工具**：在 MCP Dashboard 复制配置连接你的 AI 编程助手

---

## 项目定位与意义

Archon 的前身是一个「构建 AI Agent 的 AI Agent」（the agenteer），后来转型为更通用的 AI 编程助手知识中枢。这个转型非常精准——在 AI 编程工具百花齐放的 2025-2026 年，**上下文工程 (Context Engineering)** 正在成为决定 AI 编程质量的关键因素。

Archon 不是又一个 AI 编程工具，而是**所有 AI 编程工具的「大脑」**——它让各种 AI 编程助手共享同一份项目知识，理解同一个任务上下文，真正做到「人机协作」而非「人机对话」。

---

> Archon = AI 编程助手的共享大脑。MCP 协议让它与任何兼容工具无缝连接，知识库 + 任务管理让它成为项目上下文的唯一真相来源。

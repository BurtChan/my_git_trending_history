# PentAGI 项目分析

## 项目名称
**PentAGI** — 全自主 AI 多智能体渗透测试系统
- **GitHub**: [vxcontrol/pentagi](https://github.com/vxcontrol/pentagi)
- **许可证**: MIT

---

## 项目概述
PentAGI（Penetration Testing Artificial General Intelligence）是一款全自主的 AI 多智能体渗透测试平台，专为安全专业人士、研究人员和爱好者设计。该系统采用多智能体架构，通过专业化的 AI Agent 团队自主确定并执行渗透测试步骤，在安全的 Docker 沙箱环境中完成从侦察到漏洞利用的完整渗透测试流程。

PentAGI 的核心创新在于将大语言模型（LLM）与专业渗透测试工具链深度融合。系统内置 20 多种专业安全工具（nmap、metasploit、sqlmap 等），并通过智能任务规划系统将复杂的渗透测试目标自动分解为可执行的子任务，分配给不同角色的 Agent 执行。Agent 团队包含研究员、开发者、执行者、搜索者、代码编写者等 13 种专业角色，每种角色负责渗透测试流程中的特定环节。

该系统采用微服务架构，支持水平扩展，集成了完整的监控栈（Grafana、Prometheus、OpenTelemetry、Jaeger、Loki）和持久化存储（PostgreSQL + pgvector）。支持 10 多种 LLM 提供商（OpenAI、Anthropic、Gemini、Ollama、DeepSeek、GLM 等），并兼容 OpenAI 兼容端点。PentAGI 提供了现代化的 React + TypeScript 前端界面和完整的 REST + GraphQL API，能够生成详细的漏洞报告（Web/Markdown/PDF 格式）。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 全自主渗透测试 | AI Agent 自主规划和执行渗透测试步骤，无需人工干预 |
| Docker 沙箱隔离 | 所有操作在安全隔离的 Docker 容器中执行，防止对生产环境影响 |
| 20+ 专业工具集成 | 内置 nmap、metasploit、sqlmap、nikto 等主流渗透测试工具 |
| 13 种专业 Agent 角色 | 研究员、开发者、执行者、搜索者、代码编写者、安装者、渗透测试者等 |
| 智能记忆系统 | 长期记忆存储研究成果和成功攻击路径，支持向量检索和知识图谱 |
| 7 种搜索集成 | Tavily、Traversaal、Perplexity、DuckDuckGo、Google、Sploitus、Searxng |
| 知识图谱 | 基于 Graphiti + Neo4j 的语义关系追踪（Beta） |
| 详细报告生成 | 支持 Web、Markdown、PDF 格式的漏洞报告，含利用指南 |
| 10+ LLM 提供商支持 | OpenAI、Anthropic、Gemini、Bedrock、Ollama、DeepSeek、GLM 等 |
| 完整监控栈 | Grafana、Prometheus、OpenTelemetry、Jaeger、Loki |
| REST + GraphQL API | 完整的 API 支持，Bearer Token 认证 |
| 水平扩展 | 微服务架构，支持容器编排和水平扩展 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 后端 API | Go（REST + GraphQL） |
| 前端 UI | React + TypeScript |
| 数据库 | PostgreSQL + pgvector 扩展 |
| 知识图谱 | Graphiti API + Neo4j |
| 监控 | Grafana、Prometheus、VictoriaMetrics、OpenTelemetry、Jaeger、Loki |
| 分析 | Langfuse、ClickHouse、Redis、MinIO |
| 安全工具 | nmap、metasploit、sqlmap 等 20+ 工具 |
| 容器化 | Docker + Docker Compose |
| LLM 集成 | 10+ 提供商（OpenAI、Anthropic、Gemini、Ollama 等） |
| 许可证 | MIT |

---

## 项目亮点

### 多智能体协同的专业渗透测试
PentAGI 的 13 种 Agent 角色设计是其核心竞争力。系统不是用单一 LLM 完成所有渗透测试任务，而是模拟真实安全团队的工作方式——研究员 Agent 负责收集情报和漏洞信息，开发者 Agent 编写定制化攻击脚本，执行者 Agent 在沙箱中运行工具，搜索者 Agent 在互联网上寻找已知漏洞和利用方法。这种专业化的分工使每个 Agent 专注于自己擅长的领域，整体渗透测试质量远超单一 Agent 方案。

### 四层记忆系统的智能知识管理
PentAGI 实现了完整的四层记忆架构：长期记忆（向量存储嵌入 + 知识库 + 工具知识库）、工作记忆（当前上下文、活跃目标、系统状态）、情景记忆（历史操作、结果、成功模式）以及链摘要（通过选择性摘要管理上下文增长）。这套记忆系统使 PentAGI 能够从过去的渗透测试经验中学习，避免重复失败的攻击路径，积累有效的攻击知识。

### 生产级的安全基础设施
与概念验证项目不同，PentAGI 具备生产级系统的完整特征：微服务架构支持水平扩展、完整的可观测性栈（从指标到日志到分布式追踪）、知识图谱支持语义关系推理、多种 LLM 提供商的灵活切换。系统的执行监控和智能任务规划功能（虽然目前处于 Beta 阶段）可根据模型能力自动调整策略——对小参数模型（< 32B）推荐启用执行监控和任务规划以获得 2 倍质量提升。

---

## 应用场景

### 企业安全评估
安全团队可以使用 PentAGI 对内部系统进行自动化的渗透测试，快速发现常见漏洞和配置缺陷，作为人工安全评估的高效补充。

### 安全研究与教育
安全研究人员和学生可以利用 PentAGI 学习渗透测试方法论和工具使用，系统会自动记录每一步操作和决策过程，便于学习和分析。

### CTF 竞赛训练
PentAGI 的自主渗透能力可以用于 CTF（Capture The Flag）比赛的训练场景，AI Agent 自动分析目标、发现漏洞、获取 Flag。

### DevSecOps 集成
将 PentAGI 集成到 CI/CD 流水线中，在部署前自动对新系统进行安全评估，实现安全左移。

### 安全意识演示
企业安全团队可以使用 PentAGI 演示攻击路径和漏洞影响，帮助管理层和非技术人员理解安全风险。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | ⭐ 19,194 |
| 总 Forks | 🍴 2,607 |
| 今日新增 | 🌟 454 stars today |
| 主要语言 | Go |
| 许可证 | MIT |
| 最新版本 | v2.1.0 |

---

## 总结
PentAGI 是当前最成熟的全自主 AI 渗透测试平台之一，通过 13 种专业化 Agent 角色的协同工作、四层记忆系统的智能知识管理和生产级的基础设施架构，将 LLM 与专业安全工具链深度融合。近 2 万 Star 和活跃的社区（Discord + Telegram）表明其在安全社区中的广泛认可，是 AI 赋能网络安全领域的标杆项目。

---

*数据来源：GitHub 仓库 (vxcontrol/pentagi)，2026 年 7 月访问*

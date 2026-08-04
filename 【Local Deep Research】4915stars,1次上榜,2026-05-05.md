# Local Deep Research 项目分析

## 项目名称

**Local Deep Research** — 本地运行的 AI 深度研究助手，支持多 LLM 和多搜索引擎

- **GitHub**: [LearningCircuit/local-deep-research](https://github.com/LearningCircuit/local-deep-research)
- **许可证**: MIT

---

## 项目概述

Local Deep Research 是一款完全本地运行的 AI 研究助手，旨在为用户提供深度、自主的研究能力，同时保证数据隐私和安全。与 Perplexity、ChatGPT 等云端 AI 研究工具不同，Local Deep Research 的所有数据处理、模型推理和知识库构建都在用户本地完成，零遥测、零追踪、零外部数据传输。

项目的核心能力是**深度代理式研究（Agentic Deep Research）**——它不仅能执行简单的搜索和摘要，还支持 20+ 种研究策略，包括快速事实查询、深度分析、学术研究等。最新引入的 LangGraph Agent Strategy 让 LLM 自主决定搜索内容、选择专业搜索引擎（arXiv、PubMed、Semantic Scholar 等），并在适当时机综合研究结果，实现了真正的自主研究循环。

在性能方面，Local Deep Research 在 SimpleQA 基准测试中达到了约 95% 的准确率（使用 Qwen 3.6-27B 在 RTX 3090 上测试），展现了本地模型在研究任务上的强大潜力。项目支持 Ollama、llama.cpp 等本地推理后端，以及 Google、Anthropic、OpenAI 等云端 LLM，为用户提供了灵活的模型选择。集成的 10+ 搜索引擎覆盖了通用搜索、学术论文、医疗文献等不同领域。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 多策略研究 | 20+ 种研究策略，支持快速查询、深度分析、学术研究等不同场景 |
| LangGraph Agent | 自主代理研究模式，LLM 自主决定搜索方向和工具选择 |
| 多 LLM 支持 | 兼容 Ollama、llama.cpp、Google、Anthropic、OpenAI 等推理后端 |
| 多搜索引擎 | 集成 SearXNG、arXiv、PubMed、Semantic Scholar 等 10+ 搜索源 |
| 本地知识库 | 可构建和搜索本地知识库，导入并索引多种来源的文档 |
| AES-256 加密 | 全端加密的知识库，确保研究数据的隐私安全 |
| Docker 部署 | 支持 Docker Compose 一键部署，包含 GPU 加速支持 |
| 分析仪表盘 | 追踪研究成本、性能指标和使用统计 |

---

## 技术栈

| 类别 | 技术 |
|------|------|
| 主要语言 | Python |
| Agent 框架 | LangGraph |
| 本地推理 | Ollama、llama.cpp |
| 云端 LLM | Google Gemini、Anthropic Claude、OpenAI GPT |
| 搜索引擎 | SearXNG、Brave Search、arXiv、PubMed、Semantic Scholar |
| 加密方案 | AES-256、SQLCipher |
| 容器安全 | Cosign 签名、SLSA 来源认证、SBOM 生成 |
| 安全扫描 | Gitleaks、OSV-Scanner、npm-audit、Retire.js |
| 部署方式 | Docker Compose、pip、Unraid |

---

## 项目亮点

1. **真正的本地优先**：所有数据处理完全在本地完成，零遥测零追踪，通过 AES-256 加密和 SQLCipher 保护知识库安全。供应链安全方面采用 Cosign 签名、SLSA 来源认证和 SBOM，在开源 AI 工具中属于安全实践的标杆。
2. **卓越的研究性能**：在 SimpleQA 基准上达到 ~95% 准确率，这一成绩使用本地模型（Qwen 3.6-27B + RTX 3090）即可达成，证明本地 AI 研究工具已可媲美云端方案。
3. **LangGraph Agent 自主研究**：最新的 LangGraph Agent Strategy 实现了真正的自主研究——LLM 自主规划研究路径、选择专业搜索引擎、判断何时综合结论，模拟了人类研究者的思维过程。
4. **生产级安全体系**：项目集成了 8+ 种安全扫描工具（Gitleaks、OSV-Scanner、Dockle、Hadolint、Checkov 等），Docker 镜像包含完整的安全认证链，远超一般开源项目的安全标准。

---

## 应用场景

1. **学术研究辅助**：集成 arXiv、PubMed、Semantic Scholar 等学术搜索引擎，帮助研究人员快速进行文献调研和综述撰写。
2. **隐私敏感研究**：适用于医疗、法律、金融等对数据隐私有严格要求的行业，所有研究数据完全保留在本地。
3. **个人知识管理**：构建本地可搜索的知识库，长期积累和检索研究成果，形成个人或团队的知识资产。
4. **深度技术调研**：使用深度分析策略进行技术选型、竞品分析、市场研究等需要多轮搜索和综合分析的复杂研究任务。

---

## Star 数据

| 指标 | 数据 |
|------|------|
| ⭐ 总 Stars | 4,915 |
| 🍴 Forks | 461 |
| 📈 今日新增 | 171 |
| 📄 许可证 | MIT |
| 💻 主要语言 | Python |

---

## 总结

Local Deep Research 是一款定位明确的本地优先 AI 研究助手，在数据隐私和 AI 能力之间找到了优秀的平衡点。它通过支持 20+ 种研究策略、10+ 搜索引擎和多 LLM 后端，为用户提供了灵活而强大的深度研究能力。LangGraph Agent Strategy 的引入让研究过程更加自主化，而 SimpleQA 95% 的准确率则证明了本地模型的实际可用性。项目在生产级安全实践方面的投入尤为突出，使其成为隐私敏感场景下 AI 研究工具的首选。

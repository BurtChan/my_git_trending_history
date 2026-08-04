# QMD 项目分析

- **项目名称**: QMD (Query Markup Documents)
- **项目地址**: [https://github.com/tobi/qmd](https://github.com/tobi/qmd)
- **作者**: @tobi（Shopify 创始人 Tobias Lütke）
- **许可证**: MIT License

---

## 项目概述

QMD 是一个完全本地运行的命令行搜索引擎，专为索引和搜索 Markdown 文档、知识库、会议记录等各类文本内容而设计。它由 Shopify 创始人 Tobias Lütke 开发，融合了当前搜索领域的 SOTA（State of the Art）方法，包括 BM25 全文检索、向量语义搜索和 LLM 重排序，所有计算均在本地设备上完成，无需联网。

QMD 不仅是一个独立的 CLI 搜索工具，还提供 MCP（Model Context Protocol）服务器和 Node.js SDK，可以与 Claude Code、Claude Desktop 等 AI 工具深度集成，为 Agentic 工作流提供高质量的文档检索能力。

---

## 核心功能

### 1. 三级搜索模式

| 命令 | 搜索方式 | 说明 |
|------|----------|------|
| `qmd search` | BM25 全文检索 | 基于 SQLite FTS5 的关键词搜索，速度最快 |
| `qmd vsearch` | 向量语义搜索 | 基于 embedding 模型的语义相似度搜索 |
| `qmd query` | 混合搜索 + 重排序 | 结合 FTS + 向量 + 查询扩展 + LLM 重排序，质量最高 |

### 2. 智能文档分块（Smart Chunking）

QMD 使用评分算法在 Markdown 文档中寻找自然断点，而非简单的硬切割。分块大小约为 900 个 token，重叠率 15%。

- **标题级别分块**: H1 得分 100、H2 得分 90、H3 得分 80，依次递减
- **代码块保护**: 代码围栏内的断点会被忽略，保持代码完整性
- **AST 感知分块**: 对 TS/JS/Python/Go/Rust 等代码文件，使用 tree-sitter 在函数、类、接口等语法边界处切割

### 3. 混合搜索流水线（Hybrid Search Pipeline）

`query` 命令的搜索流程：
1. **查询扩展**: 原始查询（x2 权重）+ LLM 生成 1 个变体
2. **并行检索**: 每个查询同时走 FTS 和向量索引
3. **RRF 融合**: 使用 Reciprocal Rank Fusion（k=60）合并结果，Top-1 额外 +0.05 加分
4. **LLM 重排序**: 使用 qwen3-reranker 对 Top 30 候选文档打分
5. **位置感知混合**: Rank 1-3 取 75% RRF / 25% 重排序；Rank 4-10 取 60%/40%；Rank 11+ 取 40%/60%

### 4. 上下文系统（Context）

用户可以为集合和路径添加描述性元数据，搜索结果会附带返回这些上下文信息，帮助 LLM 做出更好的文档选择。

### 5. MCP 服务器

提供标准的 MCP 协议接口，暴露 `query`、`get`、`multi_get`、`status` 四个工具，支持 stdio 和 HTTP 两种传输方式。HTTP 模式下 LLM 模型常驻 VRAM，避免重复加载。

### 6. Node.js SDK

可作为库在 Node.js/Bun 应用中直接使用，支持 `createStore()` 创建存储实例，提供 `search()`、`searchLex()`、`searchVector()`、`expandQuery()` 等完整的编程接口。

---

## 技术栈

| 技术 | 用途 |
|------|------|
| **TypeScript** | 核心开发语言 |
| **Node.js / Bun** | 运行时（需要 Node.js >= 22 或 Bun >= 1.0） |
| **SQLite FTS5** | 全文索引引擎 |
| **sqlite-vec** | 向量索引存储 |
| **node-llama-cpp** | 本地 LLM 推理（加载 GGUF 格式模型） |
| **tree-sitter** | 代码文件的 AST 解析分块 |
| **HuggingFace** | 模型下载和缓存 |

### 本地模型（首次使用自动下载）

| 模型 | 用途 | 大小 |
|------|------|------|
| `embeddinggemma-300M-Q8_0` | 向量嵌入（默认） | ~300MB |
| `qwen3-reranker-0.6b-q8_0` | 重排序 | ~640MB |
| `qmd-query-expansion-1.7B-q4_k_m` | 查询扩展（微调） | ~1.1GB |

支持通过 `QMD_EMBED_MODEL` 环境变量切换嵌入模型，例如使用 `Qwen3-Embedding-0.6B` 以支持中文等 119 种语言的语义搜索。

---

## 项目亮点

1. **完全本地运行**: 所有搜索、嵌入、重排序均在本地完成，数据不离开设备，保护隐私
2. **SOTA 搜索方法**: 融合 BM25 + 向量搜索 + LLM 重排序的混合流水线，追踪当前最优搜索技术
3. **Shopify 创始人出品**: 由 Tobias Lütke 亲自开发和维护，代码质量和工程水准极高
4. **MCP 原生支持**: 可作为 Claude Code 插件安装，也可作为独立 MCP 服务器运行
5. **智能分块策略**: 基于 Markdown 结构和代码 AST 的语义分块，保证搜索质量
6. **多语言支持**: 可切换嵌入模型以支持中文、日文、韩文等 119 种语言

---

## 应用场景

### 个人知识管理
索引 Obsidian 笔记库、Markdown 日记、阅读笔记等，用自然语言快速查找信息。例如 `qmd query "上次讨论的架构方案"`。

### AI Agent 集成
通过 MCP 服务器让 Claude Code、Claude Desktop 等 AI 助手直接搜索你的文档库，为 Agentic 工作流提供上下文。例如在 Claude Desktop 中配置 QMD MCP 服务器后，AI 可以自动检索相关笔记。

### 团队知识库搜索
为团队的内部文档、Wiki、会议记录建立索引，团队成员通过 CLI 快速检索。

### 开发者文档检索
索引项目文档和 API 文档，结合 AST 感知分块，精准搜索代码和文档内容。

### SDK 嵌入式搜索
将 QMD 作为库集成到自己的 Node.js 应用中，构建定制化的文档搜索功能。

---

## 安装和使用方法

### 安装

```bash
# 全局安装（npm）
npm install -g @tobilu/qmd

# 或使用 Bun
bun install -g @tobilu/qmd

# 或直接运行
npx @tobilu/qmd ...
```

### 快速上手

```bash
# 1. 添加文档集合
qmd collection add ~/notes --name notes
qmd collection add ~/Documents/meetings --name meetings

# 2. 添加上下文描述
qmd context add qmd://notes "个人笔记和想法"
qmd context add qmd://meetings "会议记录"

# 3. 生成向量嵌入
qmd embed

# 4. 搜索
qmd search "项目时间线"            # 关键词搜索
qmd vsearch "如何部署"             # 语义搜索
qmd query "季度规划流程"           # 混合搜索（最佳质量）
```

### 配置 MCP 服务器（Claude Code）

```bash
# 插件方式安装（推荐）
claude plugin marketplace add tobi/qmd
claude plugin install qmd@qmd
```

### 配置 MCP 服务器（Claude Desktop）

在 `~/Library/Application Support/Claude/claude_desktop_config.json` 中添加：

```json
{
  "mcpServers": {
    "qmd": {
      "command": "qmd",
      "args": ["mcp"]
    }
  }
}
```

---

## 与其他搜索工具的对比

| 维度 | QMD | ripgrep / grep | Meilisearch | Elasticsearch |
|------|-----|----------------|-------------|---------------|
| 搜索方式 | BM25 + 向量 + LLM 重排序 | 纯文本匹配 | 全文搜索 | 全文 + 向量 |
| 语义理解 | 支持（向量搜索 + LLM） | 不支持 | 有限 | 需插件 |
| 本地运行 | 完全本地 | 完全本地 | 需服务器 | 需服务器 |
| 安装复杂度 | npm 一行命令 | 简单 | 需部署 | 需部署 |
| AI 集成 | MCP 原生支持 | 无 | 无 | 无 |
| 适用场景 | 文档/知识库 | 代码搜索 | 网站/应用搜索 | 企业级搜索 |

---

## Star 数据

| 指标 | 数据 |
|------|------|
| **总 Star 数** | 21,214 |
| **Fork 数** | 1,308 |
| **Watch 数** | 82 |
| **Open Issues** | 295 |
| **创建时间** | 2025-12-08 |
| **最近更新** | 2026-04-13 |
| **许可证** | MIT |

---

## 总结

QMD 是 Shopify 创始人 Tobias Lütke 打造的本地文档搜索引擎，将 BM25 全文检索、向量语义搜索和 LLM 重排序三大 SOTA 方法融合在一个轻量的 CLI 工具中。项目 21k+ Stars，核心亮点在于完全本地运行保护隐私、智能 Markdown/AST 感知分块、以及原生 MCP 服务器支持。无论是个人笔记搜索、团队知识管理还是 AI Agent 集成，QMD 都提供了一个简洁而强大的解决方案。对于注重隐私、需要在本地高效检索大量文档的用户，QMD 是当前最值得关注的工具之一。

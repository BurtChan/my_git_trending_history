# MinerU 项目分析

## 项目名称
**MinerU** — 将复杂文档智能转换为 LLM 可用 Markdown/JSON 的开源解析引擎
- **GitHub**: [opendatalab/MinerU](https://github.com/opendatalab/MinerU)
- **许可证**: Apache 2.0

---

## 项目概述

MinerU 是由 OpenDataLab 团队开源的智能文档解析工具，专注于将 PDF、图片及各类 Office 文档（DOCX、PPTX、XLSX）高质量地转换为结构化的 Markdown 和 JSON 格式，为 AI 大模型的训练和推理提供高质量的文本语料。该项目起源于 InternLM 大模型预训练过程中的实际需求——团队在处理海量科学文献时发现，传统的 PDF 解析工具在公式、表格、图表等复杂元素的提取上表现不佳，严重影响了模型训练数据的质量。为解决这一痛点，MinerU 应运而生，并逐步发展为一个功能全面、精度领先的文档智能解析平台。

在技术实现上，MinerU 提供了三种灵活的部署引擎以适应不同场景需求：**Pipeline 引擎**（快速稳定，支持 CPU/GPU，准确率 85.75%，适合大批量处理）、**VLM 引擎**（基于视觉语言模型的高精度模式，准确率达 95.39%，需 GPU 支持）以及 **Hybrid 引擎**（兼顾高精度与原生文本提取，准确率 95.30%，最新 v3.3 版本引入 effort 参数支持 medium/high 精度调节）。这种多引擎架构使用户能够在处理速度和解析精度之间灵活权衡。

MinerU 已成长为 GitHub 上最受关注的人工智能文档处理项目之一，拥有超过 69,100 个 Star 和近 5,900 个 Fork。项目在 v3.1 版本中将许可证从 AGPLv3 更改为 Apache 2.0，显著降低了企业用户的商用门槛。此外，MinerU 支持昇腾、寒武纪等国产 AI 芯片，集成选项极为丰富——包括 MCP Server（支持 Cursor/Claude Desktop）、RAG 框架（LangChain/LlamaIndex）、多语言 SDK（Python/Go/TypeScript）、CLI、REST API、Docker 和 WebUI，几乎覆盖了所有主流的使用方式。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| PDF 智能解析 | 精确提取 PDF 中的文本、公式、表格、图片、标题层级等元素，转换为结构化 Markdown |
| Office 文档转换 | 支持 DOCX、PPTX、XLSX 等 Office 格式文档的解析与转换 |
| OCR 文字识别 | 集成 OCR 引擎，可处理扫描件和图片中的文字内容 |
| 版面分析 | 智能识别文档版面布局，区分正文、标题、脚注、页眉页脚、图表区域等 |
| 公式识别与转换 | 专门针对科学文献中的数学公式进行精确识别，支持 LaTeX 格式输出 |
| 表格结构化提取 | 识别表格结构并转换为 Markdown 表格或 JSON 格式，保留行列关系 |
| 多引擎部署 | 提供 Pipeline、VLM、Hybrid 三种引擎，适配不同精度和性能需求 |
| 批量处理 | 支持大规模文档批量解析，适合企业级数据处理场景 |
| MCP Server 集成 | 作为 MCP（Model Context Protocol）服务端，可直接接入 Cursor、Claude Desktop 等 AI 编程工具 |
| RAG 框架兼容 | 提供 LangChain 和 LlamaIndex 集成，无缝融入 RAG（检索增强生成）工作流 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 主要语言 | Python |
| 视觉模型引擎 | VLM（Vision Language Model） |
| OCR 引擎 | 内置 OCR 识别 |
| 版面分析 | 深度学习模型 |
| 部署方式 | Docker、CLI、REST API、WebUI |
| SDK 支持 | Python、Go、TypeScript |
| AI 框架集成 | LangChain、LlamaIndex |
| MCP 协议 | Model Context Protocol（Cursor/Claude Desktop） |
| 硬件加速 | GPU（CUDA）、国产 AI 芯片（昇腾、寒武纪等） |
| 最低配置 | 16GB RAM，推荐 32GB+ |
| 技术报告 | MinerU / MinerU2.5 / MinerU2.5 Pro（arXiv） |

---

## 项目亮点

### 三引擎架构，精度与效率的完美平衡
MinerU 独创的三引擎架构（Pipeline / VLM / Hybrid）是其核心竞争力。Pipeline 引擎以 85.75% 的准确率实现快速稳定的批量处理，适合大规模文档场景；VLM 引擎借助视觉语言模型将准确率提升至 95.39%，满足高精度需求；Hybrid 引擎则巧妙结合两者优势，在保持 95.30% 高精度的同时优先提取原生文本。用户可根据实际需求灵活选择，这一设计在同类工具中独具特色。

### 专为科学文献优化的公式与表格解析
MinerU 的研发初衷即为解决 InternLM 预训练中科学文献的解析难题，因此对公式和表格的识别能力尤为突出。数学公式可精确转换为 LaTeX 格式，复杂表格能完整保留结构关系，这对于学术论文、技术报告等专业文档的处理具有不可替代的价值。项目还发布了多篇 arXiv 技术报告（MinerU、MinerU2.5、MinerU2.5 Pro），体现了扎实的学术基础。

### 极致的集成生态
MinerU 在集成能力上做到了行业领先——不仅提供传统的 CLI、REST API、Docker 和 WebUI，还率先支持了 MCP Server 协议，可直连 Cursor 和 Claude Desktop 等 AI 编程助手，将文档解析能力无缝嵌入 AI 工作流。同时支持 LangChain 和 LlamaIndex 两大 RAG 框架，以及 Python、Go、TypeScript 三语言 SDK，几乎覆盖了开发者的所有使用习惯。

### 商用友好的 Apache 2.0 许可证
在 v3.1 版本中，MinerU 将许可证从 AGPLv3 更改为 Apache 2.0，这一决策极大地降低了企业用户的采用门槛。Apache 2.0 许可证允许商业使用、修改和分发而不强制开源衍生作品，使 MinerU 成为企业在构建文档处理管线时的首选开源方案之一。

---

## 应用场景

### 大模型预训练数据准备
MinerU 最初即为 InternLM 预训练而生，天然适合作为 LLM 训练语料的文档解析管线。通过批量处理海量 PDF 文献、技术报告、书籍等，将其转换为高质量的 Markdown/JSON 格式文本，为模型训练提供干净、结构化的输入数据，显著提升预训练语料质量。

### RAG 知识库构建
在企业知识管理和智能问答场景中，MinerU 可将内部文档（PDF 报告、PPT 演示文稿、Excel 数据表）解析为结构化文本，结合 LangChain/LlamaIndex 框架构建向量知识库，实现基于企业私有文档的精准问答与信息检索。

### Agentic 工作流文档处理
通过 MCP Server 协议，MinerU 可直接接入 Claude Desktop、Cursor 等 AI Agent 工具，让 AI 助手能够实时读取和理解用户本地的 PDF/Office 文档。这一能力在合同审核、文档摘要、学术文献分析等 Agent 工作流中具有极高的实用价值。

### 学术研究与文献分析
针对科研人员的论文阅读与分析需求，MinerU 能精确提取论文中的公式、表格、参考文献等结构化元素，配合高精度的 VLM 引擎，可显著提升文献整理、综述撰写、数据提取等研究工作的效率。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| GitHub Stars | 69,150 |
| GitHub Forks | 5,842 |
| 主要语言 | Python |
| 许可证 | Apache 2.0 |
| 创建时间 | 2024-02-29 |
| 今日新增 Stars | 524 |

---

## 总结

MinerU 是当前开源社区中最领先的智能文档解析工具，凭借独创的三引擎架构、业界顶尖的解析精度（最高 95.39%）、专为科学文献优化的公式表格识别能力，以及覆盖几乎所有主流集成方式的丰富生态，已成为大模型训练数据准备和 RAG 知识库构建不可或缺的基础设施组件。从 AGPL 到 Apache 2.0 的许可证变更进一步释放了其商业价值，使其在企业级应用中拥有广阔前景。

---

*数据来源：GitHub 仓库 (opendatalab/MinerU)，2026 年 6 月访问*

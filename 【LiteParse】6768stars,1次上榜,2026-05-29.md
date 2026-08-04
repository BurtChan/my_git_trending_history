# LiteParse 项目分析

## 项目名称

**LiteParse** — LlamaIndex 团队开源的快速、轻量、纯本地文档解析工具，专为 AI Agent 和数据管线设计

- **GitHub**: [run-llama/liteparse](https://github.com/run-llama/liteparse)
- **许可证**: Apache License 2.0

---

## 项目概述

LiteParse 是由 LlamaIndex 团队开源的一款快速、轻量、纯本地的文档解析工具，专为 AI Agent 和实时数据管线设计，无需云服务或 LLM 依赖即可从 PDF、Office 文档和图片中提取布局感知的文本。它是 LlamaIndex 团队在多年构建 LlamaParse（业界领先的云端文档解析服务）过程中，将核心解析引擎开源后推出的独立工具。

项目的核心理念是"保留布局而非检测结构"——不尝试将表格转换为 Markdown 等结构化格式，而是将文本投射到空间网格上，保留原始排版的空间关系，让 LLM 利用自身的空间推理能力来"阅读"文档。据官方数据，LiteParse 可以在约 2 秒内处理 500 页文档，处理速度随 CPU 核心数线性扩展。

当前 AI Agent 和 RAG 系统的数据摄取管线已成为主要瓶颈。传统工具如 pypdf、pdfplumber 虽然速度快但会破坏文档布局、丢失空间上下文；而云端解析服务虽然准确度高，但存在隐私、成本和网络延迟问题。LiteParse 恰好填补了这一空白——它能在毫秒级内完成文档解析，输出带边界框的空间文本，同时完全在本地运行，无需 API Key、无需发送任何数据到云端。此外，它采用 TypeScript/Rust 构建，零 Python 依赖，这在以 Python 为主导的 AI 生态中是一个大胆且务实的选择。

---

## 核心功能

### 1. 空间文本解析
从 PDF 中提取带有边界框（bounding boxes）的布局感知文本，保留文本在页面上的空间位置关系，输出为结构化 JSON，每个文本元素都标注了坐标和位置信息。

### 2. OCR 文字识别
内置 Tesseract OCR 支持，对扫描件或图片型 PDF 自动启用 OCR；支持自定义 Tesseract 训练数据路径、多语言识别、以及 HTTP OCR 服务器对接以获得更高精度。

### 3. 批量文档解析
支持对整个目录进行批量解析（`lit batch-parse`），自动遍历所有文件并输出结构化结果，适合大规模文档处理管线。

### 4. 页面截图生成
可为文档任意页面生成 PNG 截图（`lit screenshot`），支持指定页面范围和 DPI，用于多模态推理和更深入的文档分析。

### 5. 多格式输入支持
支持 PDF、DOCX、PPTX、XLSX、图片等 50+ 种文档格式的自动检测和解析，Office 文档和图片会自动转换为 PDF 后再进行解析。

### 6. CLI 命令行工具
提供统一的 `lit` 命令行界面，支持解析、批量解析、截图三大核心操作，可配置 OCR 语言、最大页数、目标页面、DPI、密码保护文档等参数。

### 7. 浏览器端运行（WASM）
提供 WebAssembly 版本（`@llamaindex/liteparse-wasm`），可在浏览器中直接解析 PDF，基于 PDF.js 和 Tesseract.js 实现，无需后端服务。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心引擎** | Rust（高性能文档解析核心） |
| **主要语言绑定** | TypeScript / Node.js |
| **Python 绑定** | Python（`pip install liteparse`） |
| **浏览器运行时** | WebAssembly（WASM），基于 PDF.js + Tesseract.js |
| **OCR 引擎** | Tesseract（默认）+ 可插拔 HTTP OCR 服务器 |
| **Office 文档转换** | LibreOffice（自动转换 DOC/DOCX/PPT 等） |
| **图片处理** | ImageMagick（图片转 PDF） |
| **CLI 工具** | `lit` 命令行工具 |
| **所属生态** | LlamaIndex 生态系统 |
| **许可证** | Apache License 2.0 |

---

## 项目亮点

### 极速本地解析，零云依赖
LiteParse 完全在本地运行，无需 API Key、无需云服务、无需消耗 LLM Token。据官方测试，约 2 秒即可处理 500 页文档，处理速度随 CPU 核心数线性扩展。这种设计消除了网络延迟、隐私泄露和云服务成本三大痛点。

### "保留布局而非检测结构"的独特理念
与传统解析工具试图将表格检测并转换为 Markdown 不同，LiteParse 采用空间文本投影技术，通过缩进和空白保留文档的原始视觉布局。这种设计哲学认为 LLM 自身具备空间推理能力，无需工具预先"翻译"文档结构。

### 多语言、多平台、多运行时支持
LiteParse 提供了罕见的全平台覆盖：Rust 核心 + Node.js/TypeScript 原生库 + Python 绑定 + 浏览器 WASM 版本。所有版本共享同一套 `lit` CLI，能无缝融入任何技术栈。

### 原生 Agent 技能设计
LiteParse 从设计之初就面向 AI Agent 使用场景，内置了 Agent Skill（`SKILL.md`）支持，可与 Claude Code 等 AI 编程助手直接集成，让 Agent 可以直接调用 `lit` 命令进行文档读取和截图提取。

---

## 应用场景

### RAG（检索增强生成）数据摄取管线
在构建 RAG 系统时，数据摄取管线往往是最大的性能瓶颈。LiteParse 可作为文档摄取的第一层，快速将 PDF、Office 文档转换为带空间信息的结构化文本，供下游向量化和检索使用。

### AI 编程助手与自主 Agent 工具链
Claude Code、Cursor 等 AI 编程助手经常需要读取 PDF 规格文档、技术手册等。LiteParse 作为 Agent Skill 直接嵌入 Agent 工具链，让 Agent 无需每次手写解析代码即可快速读取文档内容。

### 企业文档自动化处理
在保险、金融、制造、医疗等行业，大量文档（发票、合同、报表）需要自动化处理。LiteParse 支持 50+ 种文档格式，可批量解析整个目录的文档，输出结构化 JSON，且数据全程本地处理，满足合规要求。

### 浏览器端文档解析应用
借助 WASM 版本，开发者可以构建完全在浏览器端运行的 PDF 解析应用，无需后端服务，适合需要离线文档处理的 Web 应用。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 6,768 |
| **总 Forks** | 425 |
| **今日新增 Stars** | +932 |
| **许可证** | Apache License 2.0 |
| **发布时间** | 2026 年 3 月 |
| **主要语言** | Rust / TypeScript |

---

## 总结

LiteParse 是 LlamaIndex 团队将多年文档解析经验凝聚而成的开源力作，以"快速、轻量、本地优先"为核心定位，通过独特的空间文本保留理念和多平台全语言支持，为 AI Agent 时代提供了一款实用的文档解析基础设施。今日新增 932 Stars 的高增长态势表明社区对其设计理念的高度认可。

---

*数据来源：GitHub 仓库 (run-llama/liteparse)，2026 年 5 月访问*

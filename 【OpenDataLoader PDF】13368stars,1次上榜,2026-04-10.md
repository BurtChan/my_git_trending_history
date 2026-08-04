# OpenDataLoader PDF 项目分析

> **面向 AI 数据准备的 PDF 解析器 — 在 200+ 份真实 PDF 基准测试中排名第一（0.907 总分），将任意 PDF 转换为结构化 Markdown/JSON/HTML，同时是首个端到端生成 Tagged PDF 的开源工具。**

- **GitHub**: [opendataloader-project/opendataloader-pdf](https://github.com/opendataloader-project/opendataloader-pdf)
- **语言**: Java（核心引擎）+ Python / Node.js / Java SDK
- **Stars**: 13,368（+1,012 今日） | **Forks**: 数据持续增长中
- **许可证**: Apache License 2.0（2.0 之前版本为 MPL 2.0）
- **作者**: opendataloader-project（与 PDF Association 及 Dual Lab / veraPDF 团队合作）
- **支持语言**: Python 3.10+、Node.js、Java 11+
- **包管理**: PyPI (`opendataloader-pdf`)、npm (`@opendataloader/pdf`)、Maven Central

---

## 项目定位

OpenDataLoader PDF 是一款**面向 AI 数据准备的 PDF 解析与可访问性自动化工具**，13k+ Stars。它在 200 份真实 PDF 文档的基准测试中以 0.907 的综合得分排名第一，能将任意 PDF 高精度转换为结构化 Markdown、JSON（含边界框坐标）和 HTML。同时，它是业界首个能够在 Apache 2.0 开源许可下端到端生成 Tagged PDF（带标签 PDF）的工具，为全球 PDF 无障碍合规提供了可扩展的自动化方案。

---

## 解决什么问题

### 1. PDF 解析精度不足
传统 PDF 解析器在处理复杂布局时面临严重问题：
- **阅读顺序错乱** — 多栏排版、侧边栏、混合布局中的文字顺序混乱
- **表格结构丢失** — 边框缺失、合并单元格、嵌套表格无法正确还原
- **元素坐标缺失** — 无法定位内容在原始页面中的位置，RAG 引用无据可依
- **复杂内容无法处理** — 数学公式、图表、扫描件、手写体等需要 AI 级别理解

### 2. PDF 无障碍合规成本高昂
- 欧洲无障碍法案（EAA）要求 2025 年 6 月前所有数字产品具备可访问性
- ADA 及 Section 508（美国）、韩国数字包容法案均已生效
- 人工 PDF 修复成本每份文档 $50-$200，且无法规模化
- 现有开源工具均无法端到端生成 Tagged PDF，大多依赖专有 SDK

---

## 核心功能

| 功能 | 说明 | 状态 |
|------|------|------|
| **文本提取（正确阅读顺序）** | XY-Cut++ 算法确保多栏、侧边栏、混合布局的正确阅读顺序 | 已发布 |
| **边界框坐标** | 每个元素（标题、段落、表格、图片）均提供精确的页面坐标 | 已发布 |
| **表格提取** | 简单有框表格（本地模式）+ 复杂/无框表格（混合模式，准确率 0.928） | 已发布 |
| **标题层级检测** | 自动识别标题级别（H1+），保留文档结构 | 已发布 |
| **列表检测** | 支持有序、无序、嵌套列表的识别 | 已发布 |
| **图片提取（含坐标）** | 提取图片并保留其在页面中的位置信息 | 已发布 |
| **OCR 扫描件识别** | 内置 OCR，支持 80+ 语言，处理 300 DPI+ 低质量扫描件 | 已发布（混合模式） |
| **数学公式提取** | 从科学 PDF 中提取公式并转换为 LaTeX | 已发布（混合模式） |
| **图表/图片 AI 描述** | 使用 SmolVLM（256M 轻量视觉模型）生成图表和图片的文字描述 | 已发布（混合模式） |
| **Tagged PDF 结构提取** | 读取并利用 PDF 原生结构标签，还原作者意图 | 已发布 |
| **AI 安全过滤** | 自动检测并过滤隐藏文本、透明字体、零字号字体、页面外内容等提示注入攻击 | 已发布 |
| **页眉/页脚/水印过滤** | 自动识别并过滤页面装饰元素 | 已发布 |
| **敏感数据脱敏** | 可选功能，将邮件、URL、电话号码替换为占位符 | 已发布 |
| **自动标签化 → Tagged PDF** | 为无标签 PDF 自动生成结构标签 | 2026 Q2 |
| **PDF/UA 导出** | 转换为 PDF/UA-1 或 PDF/UA-2 合规文件 | 企业版 |
| **无障碍编辑器** | 可视化标签审查与修复工具 | 企业版 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心引擎** | Java 11+（确定性本地 PDF 处理） |
| **Python SDK** | Python 3.10+（通过 JVM 桥接调用核心引擎） |
| **Node.js SDK** | TypeScript / JavaScript |
| **Java SDK** | 原生 Java（Maven Central 分发） |
| **阅读顺序算法** | XY-Cut++（改进的递归版面分析算法） |
| **混合模式 AI 后端** | 本地部署，结合规则引擎与 AI 模型 |
| **OCR 引擎** | 内置于混合模式，支持 80+ 语言 |
| **公式识别** | 混合模式中的 LaTeX 转换 |
| **视觉描述模型** | SmolVLM（256M 参数轻量视觉模型） |
| **LangChain 集成** | `langchain-opendataloader-pdf` 官方包 |
| **验证工具** | veraPDF（PDF Association 与 Dual Lab 开发） |
| **无障碍规范** | Well-Tagged PDF（PDF Association 制定的标签规范） |
| **包分发** | PyPI、npm、Maven Central |

---

## 基准测试表现

在 200 份真实世界 PDF（含多栏排版、科学论文）的综合基准测试中：

| 引擎 | 总分 | 阅读顺序 | 表格 | 标题 | 速度（秒/页） |
|------|------|----------|------|------|---------------|
| **OpenDataLoader [hybrid]** | **0.907** | **0.934** | **0.928** | 0.821 | 0.463 |
| docling | 0.882 | 0.898 | 0.887 | **0.824** | 0.762 |
| nutrient | 0.880 | 0.924 | 0.662 | 0.811 | 0.230 |
| marker | 0.861 | 0.890 | 0.808 | 0.796 | 53.932 |
| unstructured [hi_res] | 0.841 | 0.904 | 0.588 | 0.749 | 3.008 |
| OpenDataLoader (本地) | 0.831 | 0.902 | 0.489 | 0.739 | **0.015** |

> 分数归一化至 [0, 1]，越高越好；速度越低越好。本地模式处理速度达 60+ 页/秒（CPU），无需 GPU。

---

## 输出格式

| 格式 | 适用场景 |
|------|----------|
| **JSON** | 结构化数据，含边界框坐标和语义类型标注 |
| **Markdown** | 纯净文本，适合 LLM 上下文输入和 RAG 分块 |
| **HTML** | 带样式的网页展示 |
| **Annotated PDF** | 可视化调试 — 在原始 PDF 上标注检测到的结构 |
| **Text** | 纯文本提取 |

---

## 快速上手

### Python

```bash
pip install -U opendataloader-pdf
```

```python
import opendataloader_pdf

opendataloader_pdf.convert(
    input_path=["file1.pdf", "file2.pdf", "folder/"],
    output_dir="output/",
    format="markdown,json"
)
```

### Node.js

```bash
npm install @opendataloader/pdf
```

```javascript
import { convert } from '@opendataloader/pdf';

await convert(['file1.pdf', 'file2.pdf', 'folder/'], {
  outputDir: 'output/',
  format: 'markdown,json'
});
```

### 混合模式（复杂文档）

```bash
pip install -U "opendataloader-pdf[hybrid]"

# 终端 1 — 启动后端
opendataloader-pdf-hybrid --port 5002

# 终端 2 — 处理 PDF
opendataloader-pdf --hybrid docling-fast file1.pdf file2.pdf folder/
```

### LangChain 集成

```bash
pip install -U langchain-opendataloader-pdf
```

```python
from langchain_opendataloader_pdf import OpenDataLoaderPDFLoader

loader = OpenDataLoaderPDFLoader(
    file_path=["file1.pdf", "file2.pdf"],
    format="text"
)
documents = loader.load()
```

---

## 使用场景

| 场景 | 说明 |
|------|------|
| **RAG（检索增强生成）** | 将 PDF 转换为结构化 Markdown 用于语义分块，JSON 输出含边界框支持"点击溯源"交互 |
| **企业文档处理** | 批量解析合同、报告、财务报表中的表格和结构化数据 |
| **科学文献挖掘** | 提取论文中的公式（LaTeX）、图表描述、多栏排版内容 |
| **扫描件数字化** | OCR 处理历史档案、扫描发票、手写文档（80+ 语言） |
| **PDF 无障碍合规** | 自动为无标签 PDF 生成结构标签，满足 EAA / ADA / Section 508 法规要求 |
| **AI 训练数据准备** | 大规模 PDF 到高质量 Markdown/JSON 的转换管线 |
| **内容管理系统** | 自动提取文档结构，建立可搜索的结构化知识库 |
| **法律与医疗** | 100% 本地处理，敏感文档无需上传云端 |

---

## PDF 无障碍合规管线

OpenDataLoader 提供端到端的 PDF 无障碍合规工作流：

```
无标签 PDF
    |
    v
1. 审计（检查现有标签） → 2. 自动标签化（生成 Tagged PDF） → 3. PDF/UA 导出 → 4. 可视化编辑器
    (已发布)               (2026 Q2, Apache 2.0)               (企业版)          (企业版)
```

- 与 **PDF Association** 和 **Dual Lab**（veraPDF 开发者）合作开发
- 遵循 **Well-Tagged PDF** 规范
- 使用 **veraPDF** 进行自动化合规验证
- 自动标签化功能在 Apache 2.0 下完全免费

---

## 项目亮点

- 13k+ Stars，GitHub 上增长最快的 PDF 解析开源项目
- 基准测试综合排名第一（0.907），表格准确率最高（0.928）
- 本地模式 CPU 处理速度 60+ 页/秒（0.015s/页），无需 GPU
- 100% 本地运行，数据不出机器，适合法律/医疗/金融等敏感场景
- 首个端到端开源 Tagged PDF 生成工具（Apache 2.0）
- 同时提供 Python、Node.js、Java 三种 SDK
- 内置 AI 安全过滤，防御 PDF 提示注入攻击
- 官方 LangChain 集成支持
- 从 MPL 2.0 更改为 Apache 2.0，对企业更友好

---

## 一句话总结

> OpenDataLoader PDF 是一款**面向 AI 数据准备的 PDF 解析与无障碍自动化工具**，13k+ Stars，以 Java 为核心引擎提供 Python/Node.js/Java SDK，在 200+ 份真实 PDF 基准测试中排名第一（0.907 总分），本地模式 CPU 速度 60+ 页/秒，混合模式处理复杂表格/OCR/公式/图表，100% 本地运行无需云端，同时是首个端到端生成 Tagged PDF 的开源工具（Apache 2.0），为 RAG 管线和 PDF 无障碍合规提供了完整的解决方案。

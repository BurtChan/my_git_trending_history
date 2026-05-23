# Presenton 项目分析

## 项目名称

**Presenton** — 开源 AI 演示文稿生成器，Gamma / Beautiful AI 的开源替代方案

- **GitHub**: [presenton/presenton](https://github.com/presenton/presenton)
- **官网**: https://presenton.ai
- **许可证**: Apache License 2.0

---

## 项目概述

Presenton 是一个开源的 AI 演示文稿（PPT）生成器与 API 平台，定位为 **Gamma、Beautiful AI、Decktopus** 等商业产品的开源替代方案。用户可以通过自然语言提示词或上传文档，让 AI 自动生成完整的专业演示文稿，支持导出为可编辑的 PPTX 和 PDF 格式。

项目强调**隐私优先、数据自主、可自托管**的核心设计理念。通过 Docker 一键部署即可在本地运行完整服务，数据完全不出用户设备。同时支持通过 Ollama 接入本地 LLM，实现 100% 离线使用，满足 GDPR 等数据合规要求。

项目拥有完善的生态系统，提供 REST API、JavaScript SDK、Python SDK、Electron 桌面客户端等全套工具链，支持 OpenAI、Gemini、Azure OpenAI、Claude、Ollama 等多种 LLM 后端，不绑定单一 AI 提供商。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **Prompt → 演示文稿** | 输入一句话提示词，AI 自动生成完整幻灯片 |
| **文档 → 演示文稿** | 上传 PDF/Word 等文档，AI 提取内容生成演示文稿 |
| **可编辑 PPTX 导出** | 生成标准 PowerPoint 文件，可在 MS PowerPoint/Google Slides 中编辑 |
| **PDF 导出** | 支持导出为 PDF 格式，专业排版 |
| **自定义模板系统** | 基于 HTML + Tailwind CSS 创建无限自定义模板，保留品牌 DNA |
| **AI 模板转换器** | 将现有 PPT 文件转换为可复用的 AI 模板 |
| **自托管部署** | 支持 Docker 一键部署，数据完全本地化 |
| **桌面应用** | 提供 macOS / Windows / Linux 原生 Electron 桌面客户端 |
| **REST API** | 提供完整的 API 接口，可编程生成/编辑演示文稿 |
| **BYOK 自带密钥** | 支持用户自带 LLM API Key |
| **Ollama 离线支持** | 支持本地运行 Ollama 模型，完全离线使用 |
| **多 LLM 支持** | 兼容 OpenAI、Gemini、Vertex AI、Azure OpenAI、Claude 等 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要编程语言** | JavaScript |
| **后端** | Python (FastAPI)、Node.js |
| **前端** | HTML、Tailwind CSS |
| **桌面端** | Electron (TypeScript) |
| **包管理** | npm (Node.js)、uv (Python) |
| **容器化** | Docker、Docker Compose |
| **镜像仓库** | GitHub Container Registry (ghcr.io) |
| **LLM 集成** | OpenAI API、Azure OpenAI、Gemini、Vertex AI、Ollama |
| **OCR** | Tesseract |
| **API 规范** | REST API，HTTP Basic Auth |

---

## 项目亮点

### 真正的开源替代
对标 Gamma、Beautiful AI、Decktopus 等付费 SaaS 产品，提供完全开源免费的替代方案，Apache 2.0 许可证允许商业使用。

### 隐私至上 + 离线可用
支持 100% 本地运行，通过 Ollama 实现完全离线使用，数据不离开用户设备，符合 GDPR 数据保护规范。

### API 优先设计
提供完整的 RESTful API 和 SDK（JavaScript / Python），便于开发者将 AI 演示文稿生成功能嵌入自有产品。

### 品牌一致性
自定义模板系统基于 HTML + Tailwind CSS，可保留企业品牌 DNA，提供全局主题系统统一管理品牌风格。

---

## 应用场景

### 企业团队协作
自托管部署确保敏感数据不出内网，合规可控，适合金融、医疗、法律等行业。

### SaaS 产品集成
白标集成，将 AI 演示文稿生成功能嵌入自有产品，通过 API 编程控制。

### 个人与教育
免费、本地、私密地生成演示文稿，学生可将笔记/文档快速转为专业 PPT。

### 营销与咨询
一键生成客户提案、营销演示，支持自定义品牌模板确保视觉一致性。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 5,471+ |
| **总 Forks** | 1,027+ |
| **今日新增 Stars** | 趋势上升中 |
| **许可证** | Apache License 2.0 |
| **主要语言** | JavaScript |
| **创建时间** | 约 2025 年 |

---

## 总结

Presenton 是一个成熟度较高的开源 AI 演示文稿生成平台，5,400+ Stars，以 Apache-2.0 许可证发布。项目采用 JavaScript + Python + TypeScript 全栈架构，支持多种 LLM 后端和图片生成方案，提供 Docker 一键部署和跨平台桌面客户端。其核心价值在于**将商业 AI PPT 工具的能力开源化、本地化、API 化**，是从个人到企业的多层次使用场景的理想选择。

---

*数据来源：GitHub 仓库 (presenton/presenton)、presenton.ai 官网（2026 年 5 月访问）*

# Qiaomu Anything to NotebookLM 项目分析

## 项目名称

**Qiaomu Anything to NotebookLM** — 多源内容智能处理器，支持 15+ 种内容源自动上传 NotebookLM 生成播客/PPT/思维导图

- **GitHub**: [joeseesun/qiaomu-anything-to-notebooklm](https://github.com/joeseesun/qiaomu-anything-to-notebooklm)
- **许可证**: MIT

---

## 项目概述

Qiaomu Anything to NotebookLM 是一个 Claude Code Skill，充当**多源内容到 Google NotebookLM 的智能桥梁**。它能够自动从微信公众号、YouTube、播客（小宇宙/喜马拉雅）、网页、PDF、Markdown 等 15+ 种内容源获取内容，上传到 NotebookLM，并根据自然语言指令生成播客、PPT、思维导图、Quiz 等多种格式。

项目的核心价值在于将**内容获取、格式转换、AI 生成**三个步骤自动化。用户只需用自然语言描述需求（如"把这篇微信文章生成播客"），工具会自动识别内容类型、获取内容、上传 NotebookLM 并生成指定格式的输出。此外，项目还支持自动检测和绕过 300+ 媒体网站的付费墙。

项目最初名为 `weixin-to-notebooklm`，仅支持微信公众号文章。随着功能扩展到 15+ 种内容源，更名为 `anything-to-notebooklm` 以更准确反映其能力。项目支持深度分析模式（三轮渐进式策略）和飞书文档自动创建，适合内容创作者和知识工作者使用。

---

## 核心功能

### 1. 多源内容获取（15+ 种）

| 内容源 | 处理方式 |
|--------|----------|
| 微信公众号文章 | MCP 工具抓取 |
| YouTube 视频 | 直接传递给 NotebookLM |
| 播客（小宇宙/喜马拉雅） | 自动转录为文本 |
| 网页（含付费网站） | 自动抓取 + 付费墙绕过 |
| PDF / EPUB / TXT | markitdown 转 Markdown |
| Word / PowerPoint / Excel | markitdown 转 Markdown |
| Markdown | 直接上传 |
| 图片 / 音频 / ZIP | 自动识别处理 |
| Twitter/X | 脚本抓取 |
| 飞书文档 | 飞书 MCP 服务器 |

### 2. 多格式 AI 生成

| 输出格式 | 说明 |
|----------|------|
| 🎙️ 播客 | AI 生成 8+ 分钟播客音频 |
| 📊 PPT | 自动生成演示文稿 |
| 🗺️ 思维导图 | 可视化知识结构 |
| 📝 Quiz | 互动测验题 |
| 🎬 视频 | 视频内容 |
| 📄 报告 | 文本报告 |
| 📈 信息图 | 可视化图表 |
| 📋 闪卡 | 学习闪卡 |

### 3. 付费墙绕过
自动检测并绕过 300+ 媒体网站的付费墙（如 NYT、WSJ 等），获取完整内容。

### 4. 深度分析模式
三轮渐进式深度分析策略，逐步深入理解内容。

### 5. 飞书集成
支持自动创建飞书文档，方便团队协作和知识分享。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心框架** | Claude Code Skill（SKILL.md） |
| **主程序** | Python（main.py） |
| **内容抓取** | MCP Server（微信/飞书） |
| **格式转换** | markitdown |
| **播客转录** | 自定义 Python 脚本 |
| **AI 生成** | Google NotebookLM API |
| **安装脚本** | Bash（install.sh） |
| **许可证** | MIT |

---

## 项目亮点

### 15+ 种内容源全覆盖
从微信公众号到 YouTube、播客到 PDF、EPUB 到飞书文档，几乎覆盖了中文互联网和常见文档格式的所有主流内容源，实现"万物皆可 NotebookLM"。

### 自然语言驱动
用户只需用中文自然语言描述需求，工具自动识别内容类型并选择正确的处理管道。例如"把这篇微信文章生成播客"、"这本EPUB做成思维导图"。

### 付费墙智能绕过
内置 300+ 媒体网站付费墙绕过能力，用户无需手动处理付费内容，直接获取完整文章。

### 中文生态深度适配
项目针对中文互联网生态（微信公众号、小宇宙播客、喜马拉雅、飞书）做了深度适配，是中文用户使用 NotebookLM 的最佳工具。

---

## 应用场景

### 微信公众号内容转化
将感兴趣的微信文章一键转为播客，在通勤时收听；或转为思维导图，快速掌握文章要点。

### 学术论文和文档整理
将 PDF 论文、EPUB 电子书上传 NotebookLM，生成 Quiz 和闪卡辅助学习和复习。

### 播客内容再利用
将小宇宙或喜马拉雅播客自动转录后生成 PPT 或报告，用于会议分享和知识存档。

### 付费文章深度阅读
绕过付费墙获取完整文章，利用 NotebookLM 的 AI 能力进行深度分析和摘要。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 2,422 |
| **总 Forks** | 254 |
| **今日新增 Stars** | 465 |
| **许可证** | MIT |
| **主要语言** | Python |
| **最新版本** | v1.0.1 |

---

## 总结

Qiaomu Anything to NotebookLM 是**面向中文用户的多源内容智能处理器**，2,400+ Stars。它作为 Claude Code Skill 运行，支持微信公众号、YouTube、播客、PDF、EPUB 等 15+ 种内容源，自动上传到 NotebookLM 并生成播客、PPT、思维导图、Quiz 等 8 种输出格式。项目深度适配中文互联网生态，内置付费墙绕过功能，是中文知识工作者利用 NotebookLM 的利器。

---

*数据来源：GitHub 仓库 (joeseesun/qiaomu-anything-to-notebooklm)（2026 年 5 月访问）*

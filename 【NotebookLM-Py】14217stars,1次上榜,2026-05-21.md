# NotebookLM-Py 项目分析

## 项目名称

**NotebookLM-Py** — 非官方 Google NotebookLM Python API 与智能代理技能

- **GitHub**: [teng-lin/notebooklm-py](https://github.com/teng-lin/notebooklm-py)
- **许可证**: MIT

---

## 项目概述

NotebookLM-Py 是一个非官方的 Python 库，通过 Python、CLI 和 AI 代理集成（Claude Code、Codex、OpenClaw）提供对 Google NotebookLM 的完整编程访问能力。它封装了 Google 未公开的 API，暴露了甚至官方 NotebookLM Web UI 都不具备的功能，例如批量下载、测验/闪卡导出、思维导图数据提取等。

该库支持三种主要使用模式：用于应用集成的 Python 异步 API、用于 Shell 脚本和自动化的 CLI，以及让 LLM 编码代理直接与 NotebookLM 交互的 Agent 技能集成。用户可以创建笔记本、添加来源（URL、YouTube、PDF、音频、视频、图片、EPUB）、与内容对话、生成所有类型的工件（音频概述/播客、视频、幻灯片、测验、闪卡、思维导图），并以多种格式下载结果。同时还支持多账户配置、浏览器 Cookie 认证和导出到 Google Docs/Sheets。

该项目依赖 Google 未公开的 API，因此最适合用于原型开发、研究和个人项目。项目积极维护中，已于 2026 年 1 月发布 v0.4.0 版本，支持 macOS、Linux 和 Windows。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **Python 异步 API** | 通过异步 Python 接口完整访问 Google NotebookLM 所有功能 |
| **CLI 命令行工具** | 用于 Shell 脚本、快速任务和 CI/CD 自动化 |
| **AI 代理集成** | 作为 Claude Code、Codex、OpenClaw 的技能安装，实现代理自主操作 |
| **批量来源导入** | 支持 URL、YouTube、PDF、音频、视频、图片、EPUB 等多种格式 |
| **内容生成** | 音频概述、播客、视频、幻灯片、测验、闪卡、思维导图 |
| **批量下载与多格式导出** | 导出到 Google Docs、Sheets、JSON 等多种格式 |
| **多账户支持** | 支持多账户配置和浏览器 Cookie 认证 |
| **跨平台** | 支持 macOS、Linux、Windows |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Python（async/await） |
| **API** | Google NotebookLM 未公开 API |
| **CLI** | Click/Argparse |
| **代理技能** | SKILL.md 技能框架 |
| **平台** | macOS / Linux / Windows |

---

## 项目亮点

### 超越官方 Web UI 的功能
暴露了 Google NotebookLM 官方 Web 界面不具备的能力，如批量下载、测验导出、思维导图数据提取等。

### 无缝 AI 代理集成
一条命令即可安装为 Claude Code 和 Codex 的技能，实现 LLM 编码代理自主管理 NotebookLM。

### 活跃开发与丰富文档
频繁发布新版本，文档完善，支持 EPUB 来源、Edge SSO 登录、多账户配置等新特性。

### 三种使用模式
Python API、CLI、Agent 技能三种模式灵活切换，满足不同场景需求。

---

## 应用场景

### 研究自动化
批量导入研究资料并编程提取洞察，自动化文献综述和研究笔记整理。

### 内容生成流水线
自动化创建播客、测验、演示文稿等多媒体内容，用于教学和培训。

### AI 代理工作流
让 Claude Code 或 Codex 代理自主管理 NotebookLM 笔记本，实现端到端的知识管理自动化。

### 个人知识管理
与策划好的文档集合进行对话和查询，构建个人知识库和问答系统。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 14,217 |
| **总 Forks** | 1,979 |
| **今日新增 Stars** | 182 |
| **许可证** | MIT |
| **主要语言** | Python |

---

## 总结

NotebookLM-Py 是一个强大的非官方 Python 库，通过编程接口解锁了 Google NotebookLM 的全部潜力。支持 Python API、CLI 和 AI 代理三种使用模式，实现了超越官方 Web UI 的自动化研究工作流、内容生成和知识管理。活跃的开发、完善的功能和跨平台支持使其成为将 NotebookLM 集成到开发或研究流水线中的首选工具。

---

*数据来源：GitHub 仓库 (teng-lin/notebooklm-py)，2026 年 5 月访问*

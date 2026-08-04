# Browserbase Skills 项目分析

## 项目名称

**Browserbase Skills** — 为 Claude Code 等 AI 编码助手提供 Browserbase 浏览器自动化能力的技能集

- **GitHub**: [browserbase/skills](https://github.com/browserbase/skills)
- **许可证**: 未明确标注（Browserbase 商业项目）

---

## 项目概述

Browserbase Skills 是由 Browserbase 官方开发的一套 AI Agent 技能集，旨在让 Claude Code 等 AI 编码助手能够通过 Browserbase 云端浏览器基础设施进行 Web 自动化操作。Browserbase 是一个云端无头浏览器自动化平台，提供生产级的浏览器基础设施，支持远程会话、验证码自动解决、住宅代理 IP 等高级功能。

该项目是 Browserbase 生态的重要组成部分，通过标准化的技能（Skills）格式，将复杂的浏览器自动化能力封装为 AI Agent 可直接调用的指令集。开发者只需在 Claude Code 中安装对应插件，即可让 AI Agent 执行网页导航、数据提取、表单填写、截图、多标签管理等浏览器操作。这大大降低了将浏览器自动化集成到 AI 工作流中的门槛。

Browserbase Skills 包含多个专项技能：`browser`（浏览器自动化）、`browserbase-cli`（bb CLI 工作流）、`functions`（无服务器浏览器自动化部署）、`site-debugger`（自动化调试诊断）等。每个技能都是独立可安装的模块，开发者可以根据需求选择性安装。项目采用 Vercel Skills CLI 标准格式，兼容 Claude Code、Cursor、Codex 等多种 AI 编码助手。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **browser 技能** | 通过 browse CLI 实现浏览器自动化，支持网页导航、DOM 元素交互、数据提取、截图等 |
| **browserbase-cli 技能** | 教会 AI Agent 使用官方 bb CLI 管理浏览器基础设施（会话、项目、上下文、扩展等） |
| **functions 技能** | 将浏览器自动化部署为 Browserbase 云端无服务器函数，支持 `bb functions init` 快速初始化 |
| **site-debugger 技能** | 诊断和修复失败的浏览器自动化脚本，帮助调试复杂的 Web 交互问题 |
| **远程浏览器会话** | 通过 Browserbase 云端运行浏览器，无需本地安装 Chrome，支持多标签和持久化状态 |
| **验证码自动解决** | 内置 CAPTCHA 自动解决能力，处理 reCAPTCHA、hCaptcha 等常见验证码 |
| **住宅代理 IP** | 使用住宅代理 IP 绕过反爬虫检测，适合大规模数据采集场景 |
| **bb fetch** | 通过 Browserbase 代理获取网页内容，支持重定向控制和 JSON 输出 |
| **bb search** | 通过 Browserbase Search API 进行网页搜索 |
| **本地环境支持** | 支持 `browse env local` 在本地 Chrome 中运行自动化脚本进行调试 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | JavaScript |
| **技能格式** | Vercel Skills CLI（SKILL.md） |
| **浏览器引擎** | Browserbase 云端浏览器（基于 Chromium） |
| **CLI 工具** | bb CLI（Browserbase 官方命令行工具） |
| **浏览自动化** | browse CLI |
| **兼容平台** | Claude Code、Cursor、Codex 等 AI 编码助手 |
| **插件安装** | Claude Code Plugin Marketplace |
| **运行环境** | Browserbase 云端 / 本地 Chrome |

---

## 项目亮点

### 云端浏览器基础设施
Browserbase 提供生产级的云端浏览器环境，开发者无需维护本地浏览器实例，直接在云端运行自动化任务，支持大规模并发和持久化会话。

### 反检测能力
内置住宅代理 IP 和 CAPTCHA 自动解决，有效绕过网站的反爬虫机制，适合需要采集受保护网站数据的场景。

### 无服务器函数部署
通过 `bb functions` 可以将浏览器自动化脚本部署为无服务器函数，按需运行，无需管理服务器，适合间歇性或事件驱动的自动化任务。

### 多 AI Agent 兼容
采用 Vercel Skills CLI 标准格式，兼容 Claude Code、Cursor、Codex 等多种 AI 编码助手，一套技能可在多个 AI 平台使用。

---

## 应用场景

### Web 数据采集
让 AI Agent 自动访问目标网站，提取结构化数据（价格、新闻、产品信息等），用于市场分析、竞品监控或研究用途。

### 自动化测试
通过 site-debugger 技能诊断和修复浏览器自动化脚本中的问题，提升 Web 应用测试效率。

### AI 驱动的 Web 操作
让 AI Agent 在 Claude Code 中直接执行网页操作，如填写表单、下载文件、查询信息等，将浏览器作为 AI 工作流的一部分。

### 爬虫开发与调试
开发者使用 browse CLI 在本地 Chrome 中快速迭代和调试爬虫脚本，确认无误后部署到 Browserbase 云端运行。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 676+ |
| **总 Forks** | 54+ |
| **今日新增 Stars** | ~54 |
| **许可证** | 未明确标注 |
| **创建时间** | 2025 年 |
| **主要语言** | JavaScript |

---

## 总结

Browserbase Skills 是 Browserbase 官方为 AI 编码助手打造的浏览器自动化技能集，676+ Stars。它通过标准化的 Skills 格式将 Browserbase 云端浏览器基础设施（远程会话、CAPTCHA 解决、住宅代理、无服务器部署）封装为 Claude Code、Cursor 等 AI Agent 可直接调用的指令模块。项目包含 browser、browserbase-cli、functions、site-debugger 等多个专项技能，让 AI Agent 能够在编码工作流中无缝执行 Web 自动化任务，是 AI Agent 与浏览器交互的重要桥梁。

---

*数据来源：GitHub 仓库 (browserbase/skills)、docs.browserbase.com 官方文档（2026 年 4 月访问）*

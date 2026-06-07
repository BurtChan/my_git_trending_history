# Open Design 项目分析

## 项目名称
**Open Design** — 本地优先、开源的 Claude Design 替代方案，将 AI Agent 变身设计引擎
- **GitHub**: [nexu-io/open-design](https://github.com/nexu-io/open-design)
- **许可证**: Apache-2.0

---

## 项目概述

Open Design 是由 nexu-io 团队于 2026 年 4 月 28 日推出的开源项目，定位为 Anthropic Claude Design 的本地优先、完全开源替代方案。项目诞生仅 11 天后便登上了 GitHub 趋势榜，并迅速积累了超过 6 万颗 Star，成为 2026 年上半年最受关注的 AI 设计工具项目之一。其核心理念是将 Anthropic 封闭的 Claude Design 工作流——发现需求、锁定方向、流式生成 artifact、评审、交付——转化为开放的技能文件系统、设计系统和插件生态，使任何编程 Agent 都能读取、编写和混搭。

从架构上看，Open Design 采用 Web 应用 + 本地守护进程（daemon）的架构，原生桌面应用支持 macOS 和 Windows。它能自动检测用户 PATH 中已安装的 21+ 种编程 Agent CLI（包括 Claude Code、Codex、Cursor Agent、Gemini CLI、OpenCode、Qwen、GitHub Copilot CLI、Hermes Agent、Kimi CLI 等），并将这些 CLI 作为设计引擎驱动，通过可组合的 Skills 和品牌级 Design Systems 来生成高质量的设计产物。BYOK（Bring Your Own Key）策略贯穿每一层——模型、Agent、技能——用户完全掌控自己的数据和密钥。

项目的愿景不止于"克隆" Claude Design，而是构建一个开放的设计生态系统。v0.9.0 版本引入了内置 Model Router，实现了零配置启动；v0.6.0 版本曾在一个 Sprint 内合入 136 个 PR，展现了惊人的迭代速度。团队还推出了 Open Design Fellow 计划，为贡献者提供每 MR $1,000 的报酬加免费模型额度，积极建设开源社区。

---

## 核心功能

### 技能系统（Skills）
Open Design 内置 259+ 个可组合技能，每个技能遵循 Claude Code 的 `SKILL.md` 约定，以文件夹形式组织，包含 `od:` frontmatter 元数据。技能覆盖从需求发现、视觉方向选择、流式 artifact 生成到评审交付的完整设计工作流。所有技能均为可读可编辑的 TypeScript 模块，用户可以自由添加自定义技能——只需将文件夹放入指定目录，重启守护进程即可在界面中使用。

### 设计系统（Design Systems）
项目提供 150+ 套品牌级设计系统，每套遵循统一的 9 段式 Markdown Schema：颜色、字体、间距、布局、组件、动效、语调、品牌规范和反模式。这些设计系统覆盖 AI/ML、开发工具、生产力、金融科技、电商、媒体、汽车等众多行业，模拟了 Linear、Stripe、Vercel、Notion、Apple 等知名品牌的视觉语言。这种"确定性调色板库+清单文化"的设计，让 AI Agent 能够像资深设计师一样系统化地产出设计。

### 插件生态（Plugins）
261+ 个官方插件构成可移植的 Agent-Skill 文件夹，涵盖场景模板、图片模板、视频模板、设计系统扩展、原子组件、示例项目等。插件市场的设计使得生态可以快速扩展，社区贡献者也能轻松发布自己的插件。

### 多格式输出
- **原型（Web · Desktop · Mobile）**：生成单页 HTML artifact，在沙箱 iframe 中实时预览，支持响应式布局
- **实时 Artifact 和仪表盘**：可编辑的 KPI 面板，支持数据驱动的动态展示
- **幻灯片**：15 种模板 × 36 种主题，支持导出为 HTML、PDF、PPTX、ZIP、Markdown 等多种格式
- **图片**：93 个可复制的 prompt 模板，适用于各类视觉场景
- **视频 & HyperFrames**：通过 HTML+CSS+GSAP 动画引擎生成 MP4 视频，支持逐帧动画和运动图形

### MCP Server 集成
通过 MCP（Model Context Protocol）Server，Open Design 支持与 21+ 种编程 Agent 的深度集成。这意味着用户无需离开现有的 Agent 工作流，即可调用 Open Design 的全部设计能力。内置 BYOK Proxy 支持接入任意 LLM，真正做到"你的 CLI、你的密钥"。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | TypeScript |
| 桌面应用框架 | 原生桌面应用（macOS / Windows） |
| 架构模式 | Web 应用 + 本地守护进程（daemon） |
| 设计输出 | 单页 HTML artifact（真实 CSS + 字体 + 组件） |
| 动画引擎 | GSAP（用于视频/HyperFrames 生成） |
| Agent 通信协议 | MCP（Model Context Protocol）Server |
| 视频渲染 | HTML + CSS + GSAP → MP4 |
| 导出格式 | HTML / PDF / PPTX / ZIP / Markdown / MP4 |
| 模型路由 | 内置 Model Router（v0.9.0+，零配置） |
| LLM 支持 | BYOK Proxy（Claude / GPT / Gemini / Qwen / 本地模型等） |
| 设计系统格式 | 9 段式 Markdown Schema（DESIGN.md） |
| 技能格式 | SKILL.md 约定 + TypeScript 模块 |
| 许可证 | Apache-2.0 |

---

## 项目亮点

### Agent 原生的设计工作流
Open Design 并非传统的"AI 设计工具"，而是将设计能力直接嵌入编程 Agent 的工作流中。它自动检测用户已有的 CLI 工具（Claude Code、Codex、Cursor 等），将这些 Agent 作为设计引擎，通过结构化的 prompt stack 驱动——包含需求发现问卷、视觉方向选择器、实时 Todo 进度追踪、沙箱 iframe 预览和多格式导出。这种"Agent 即设计师"的模式开创了 AI 设计工具的新范式。

### 极度开放的文件系统架构
与传统 SaaS 设计工具（如 Figma、Claude Design）不同，Open Design 的每一个技能、每一套设计系统、每一个插件都是一个可读可编辑的文件。设计系统的 9 段式 Markdown Schema 让设计师和开发者都能直接理解和修改。这种文件系统级别的开放性，意味着用户拥有完全的控制权——可以 fork、定制、混搭，不受任何平台锁定。正如项目所言："停止封闭，变为文件系统中的技能、设计系统和插件。"

### 惊人的生态扩张速度
项目从 2026 年 4 月 28 日创建到 6 月初，短短一个多月内便从 31 个技能、72 个设计系统扩张至 259+ 个技能、150+ 个设计系统、261+ 个插件。v0.6.0 版本曾在一个 Sprint（约 2 天）内合入 136 个 PR，涵盖 Cloudflare Pages 部署、外部 MCP 客户端、矢量 PDF 导出、新增多语言支持等大量功能。这种迭代速度在开源社区中相当罕见。

### 零配置的模型路由
v0.9.0 引入的内置 Model Router 是一大技术亮点。用户无需任何配置即可开始使用，系统自动处理模型选择和 API 调用。结合 BYOK Proxy 的全层支持，用户可以使用 Claude、GPT、Gemini、Qwen 甚至本地 Ollama 模型，真正实现了"一个工具，所有模型"的灵活性。

---

## 应用场景

### 初创企业快速原型设计
对于资源有限的初创团队，Open Design 可以在没有专业设计师的情况下快速生成高质量的产品原型、融资路演幻灯片和营销物料。150+ 套品牌级设计系统确保了输出质量，而"Agent 即设计师"的模式让产品经理或开发者直接用自然语言即可完成设计工作。一套 seed round 融资演示文稿从需求描述到最终交付仅需几分钟。

### 设计系统标准化与品牌一致性
企业的设计团队可以利用 Open Design 的 9 段式 Design Systems Schema 来标准化内部设计规范。每个设计系统涵盖颜色、字体、间距、布局、组件、动效、语调、品牌和反模式，形成完整的设计语言文档。通过 Agent 驱动，新项目可以自动遵循已有设计规范，确保品牌一致性。已有的 Linear、Stripe、Vercel 等知名品牌风格的设计系统也可作为参考起点。

### 前端开发者辅助设计
前端开发者可以利用 Open Design 快速将设计概念转化为可运行的 HTML/CSS 代码。生成的 artifact 使用真实 CSS、字体和组件（而非像素级画布操作），输出的代码可直接用于开发。结合现有的 UI 库，开发者可以获得更高精度的设计产出。这种从"设计到代码"的无缝衔接大大缩短了开发周期。

### 内容创作者的多媒体生产
Open Design 的多格式输出能力（HTML/PDF/PPTX/MP4）使其成为内容创作者的利器。93 个图片 prompt 模板、15×36 种幻灯片模板主题、HyperFrames 动态图形能力，覆盖了从社交媒体图片到企业宣传片、从技术博客插图到教学演示的广泛需求。视频功能通过 HTML+CSS+GSAP 直接生成 MP4，无需专业的视频编辑软件。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| GitHub Stars | 60,870 |
| Forks | 6,837 |
| 主要语言 | TypeScript |
| 许可证 | Apache-2.0 |
| 创建时间 | 2026-04-28 |
| 内置技能数 | 259+ |
| 设计系统数 | 150+ |
| 官方插件数 | 261+ |
| 支持的 Agent 数 | 21+ |
| 媒体提供商数 | 14 |
| HN 讨论热度 | 232 points / 92 comments |
| 数据采集时间 | 2026-06-08 |

---

## 总结

Open Design 是 2026 年 AI 设计领域最具野心的开源项目之一——它不仅仅是一个 Claude Design 的平替，更是一个以文件系统为核心的开放设计生态系统，将"Agent 即设计师"的理念推向了极致，通过 259+ 技能、150+ 设计系统和 261+ 插件构建了一个前所未有的 AI 原生设计工作流。

---

*数据来源：GitHub 仓库 (nexu-io/open-design)，2026 年 06 月访问*

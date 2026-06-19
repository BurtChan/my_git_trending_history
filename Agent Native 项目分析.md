# Agent Native 项目分析

## 项目名称
**Agent Native** — 构建智能体原生应用的开源框架
- **GitHub**: [BuilderIO/agent-native](https://github.com/BuilderIO/agent-native)
- **许可证**: MIT

---

## 项目概述

Agent Native 是由 Builder.io 团队打造的开源框架，其核心理念是将 AI 智能体（Agent）与用户界面（UI）视为"同等公民"——每一个操作都可以双向触发：既可以点击按钮执行，也可以通过对话指令完成。传统应用往往在 UI 和 AI 之间做出取舍，而 Agent Native 让每一个应用同时具备精致的用户界面和强大的自主智能体能力，两者深度融合而非简单叠加。

该框架提供了一套完整的产品级构建原语（Primitives），包括共享动作定义（`defineAction`）、SQL 驱动的状态管理、身份认证体系、工具与技能系统、任务调度与可观测性等。开发者无需在智能体合约和 UI 之间反复切换——只需选择 UI 的深度级别，底层智能体协议保持不变。这种设计哲学代表了应用开发从"AI 增强型"向"智能体原生"的范式跃迁。

框架采用完全开放策略，后端技术栈高度解耦：数据库兼容 Drizzle ORM 支持的任意 SQL 数据库，部署兼容 Nitro 支持的任意平台，模型栈可自由选择。这种零供应商锁定的设计使其在当前 AI 开发工具生态中独具竞争力。项目已有 12 个完整的应用模板可供直接使用，覆盖日历、邮件、内容管理、幻灯片、数据分析等核心场景。

---

## 核心功能

### 三种产品形态
Agent Native 提供三种递进的产品形态，共享相同的底层原语，开发者可根据需求灵活选择：
- **Headless（无头模式）**：通过代码、CLI、HTTP、MCP 或 A2A 协议直接调用智能体与操作，适合将 AI 能力嵌入到已有系统中，无需额外 UI 层。
- **Rich Chat（富聊天模式）**：独立的或可嵌入的聊天界面，原生支持表格、图表、审批流程、设置向导和工具结果渲染，提供远超普通聊天窗口的交互体验。
- **Whole App（完整应用模式）**：完整的 SaaS 产品级 UI，聊天从中心位置启动后可移至侧边栏，始终与应用状态实时同步，适合构建面向终端用户的全功能产品。

### 多协议原生支持
框架内置了业界最全面的 AI 协议支持，并非作为额外集成插件存在，而是核心架构的一部分。支持的协议包括 A2A（Agent-to-Agent 智能体间通信）、MCP（Model Context Protocol 模型上下文协议）、MCP Apps 与 MCP OAuth（MCP 应用与认证）、AG-UI（自定义智能体运行时适配器路径）、A2UI（声明式 UI 格式，新兴标准）、ACP（编码智能体与编辑器互操作协议）、HTTP/CLI 动作调用以及深度链接。

### 技能系统（Skills）
提供无需脚手架即可使用的智能体技能扩展机制。目前核心技能包括 `/visual-plan`（可视化规划：在编码前生成结构化、可审阅的计划，包含内联图表、UI 线框图、原型、逐文件实现映射和批注）和 `/visual-recap`（可视化回顾：将 PR 和 Git Diff 转化为视觉化回顾，以变更前后对比块展示 Schema、API 和文件变化，支持生成可分享的审阅链接）。这些技能兼容 Claude Code、Codex、Cursor、OpenCode、GitHub Copilot/VS Code 等主流编码智能体。

### 单体仓库与跨应用协作
默认采用 pnpm monorepo 的多应用工作空间结构，所有应用共享认证会话和零配置的跨应用 A2A 通信。例如，在日历应用的智能体聊天中标记 `@mail` 即可直接触发邮件应用的操作，无需 JWT 签名或 CORS 配置。这为构建多应用平台提供了开箱即用的基础设施。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | TypeScript |
| 包管理器 | pnpm（monorepo 工作空间） |
| ORM | Drizzle（支持任意 SQL 数据库） |
| 部署引擎 | Nitro（支持任意部署目标） |
| 前端 | React（模板基于 React 构建） |
| CSS 框架 | Tailwind CSS |
| AI 协议 | A2A、MCP、AG-UI、A2UI、ACP |
| 智能体兼容 | Claude Code、ChatGPT、Codex、Cursor、OpenCode、GitHub Copilot/VS Code |
| 许可证 | MIT |

---

## 项目亮点

### 开创性的"智能体即公民"架构
Agent Native 首次在框架层面将智能体和 UI 置于完全对等的地位。传统方案要么是"有精美 UI 但 AI 是外挂"的 SaaS 工具，要么是"功能强大但没有 UI"的原始 AI 智能体。Agent Native 的双向操作模型让点击和对话成为同一条操作路径的两端，智能体可以直接修改应用代码和 UI，而非仅限于执行预设指令。

### 12 个完整的生产级模板
项目提供了 12 个可直接 fork 和定制的完整 SaaS 应用模板，每一个都不是简单的脚手架，而是功能完备、可直接部署的产品。包括 Calendar（对标 Google Calendar/Calendly）、Content（对标 Obsidian/Notion）、Slides（对标 Google Slides/Pitch）、Analytics（对标 Amplitude/Mixpanel）、Mail（对标 Superhuman/Gmail）、Forms（对标 Typeform）、Clips（对标 Loom）、Brain（团队知识库）、Assets（品牌资产管理）、Design（设计原型）、Dispatch（智能体任务调度中心）和 Plans（编码智能体可视化规划）。这意味着开发者可以基于这些模板快速构建自己的 AI 原生产品，无需从零开始。

### 极致的零锁定设计
框架在后端数据库（Drizzle 支持的任意 SQL）、部署平台（Nitro 支持的任意目标）、AI 模型提供商等方面均不设锁定。与其他可能绑定特定云服务或模型的 AI 框架不同，Agent Native 真正做到了"你的代码你拥有"。配合 MIT 开源许可证，企业可以完全自主地部署和定制。

### A2A 智能体间协作的工程化实践
Agent Native 不仅支持 A2A 协议，更在单体仓库层面实现了零配置的跨应用智能体通信。在多应用工作空间中，不同应用之间的智能体可以自然地相互调用和协作，共享认证上下文，无需复杂的集成配置。这代表了从"单一智能体"到"智能体生态系统"的重要一步。

---

## 应用场景

### 企业内部工具平台化
企业可以使用 Agent Native 的工作空间架构快速构建内部工具套件（邮件、日历、表单、知识库等），各应用共享统一认证和智能体能力，员工既可以通过传统 UI 操作，也可以通过自然语言让智能体代为执行，极大提升跨应用工作效率。

### SaaS 产品 AI 原生化改造
对于现有 SaaS 产品团队，Agent Native 提供了一条从"AI 增强型"向"智能体原生"演进的路径。可以从 Headless 模式开始，将 AI 能力集成到现有系统中，逐步过渡到 Rich Chat 和 Whole App 模式，最终实现 AI 深度融入产品每一个交互的场景。

### 编码智能体的可视化能力扩展
开发团队可以利用 `/visual-plan` 和 `/visual-recap` 等技能，为 Claude Code、Codex、Cursor 等编码智能体添加结构化可视化和审阅能力。编码前生成可评审的视觉化计划，编码后生成变更回顾，显著提升 AI 辅助代码开发的可控性和可审查性。

### 替代付费 SaaS 工具
Agent Native 的 12 个模板可以直接替代 Google Calendar、Obsidian、Google Slides、Amplitude、Loom、Superhuman 等主流付费 SaaS 产品，且完全开源、可自定义、数据自主可控。对于注重数据主权和成本控制的团队而言，这提供了极具吸引力的替代方案。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 902 |
| 🍴 Forks | 108 |
| 📝 主要语言 | TypeScript |
| 📄 许可证 | MIT |
| 🏠 官网 | agent-native.com |

---

## 总结

Agent Native 是一个具有前瞻性的开源框架，它重新定义了 AI 智能体与用户界面之间的关系——不再是"AI 辅助 UI"或"UI 包装 AI"，而是让两者成为同构系统中真正对等的组成部分。凭借全面的协议支持（A2A、MCP、AG-UI、ACP 等）、12 个生产级应用模板、零供应商锁定的技术架构以及活跃的社区生态（902 Stars、108 Forks），Agent Native 正在成为构建下一代智能体原生应用的首选框架。对于希望在 AI 时代构建差异化产品的开发者和企业而言，这是一个值得关注和投入的高潜力项目。

---

*数据来源：GitHub 仓库 (BuilderIO/agent-native)，2026 年 6 月访问*

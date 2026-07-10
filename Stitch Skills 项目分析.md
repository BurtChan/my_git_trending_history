# Stitch Skills 项目分析

## 项目名称
**Stitch Skills** — Google 实验室的 AI 编码代理技能库，遵循 Agent Skills 开放标准

- **GitHub**: [google-labs-code/stitch-skills](https://github.com/google-labs-code/stitch-skills)
- **许可证**: Apache-2.0

---

## 项目概述

Stitch Skills 是 Google Labs Code 团队开发的一套 AI 编码代理技能和插件库，设计用于与 Google Stitch MCP 服务器配合工作。每个技能遵循 [Agent Skills](https://agentskills.io) 开放标准，确保与多种编码代理兼容，包括 Codex、Antigravity、Gemini CLI、Claude Code 和 Cursor。

该项目于 2026 年 1 月创建，分为三大类插件/技能集合：**Design**（设计工作流）、**Build**（代码生成和框架集成）、**Utilities**（辅助工具）。这些技能使 AI 编码代理能够完成从前端代码到设计系统的转换、设计稿到 React 组件的生成、多页面网站的创建等高级任务。

值得注意的是，该项目明确声明**不是 Google 官方支持的产品**，也不属于 Google 开源软件漏洞奖励计划的范围。

---

## 核心功能

### Design（设计技能）
| 技能 | 描述 |
|------|------|
| `code-to-design` | 将前端代码（React、Vue 等）转换为 Stitch Design |
| `generate-design` | 从文本/图像生成新设计页面，编辑现有页面 |
| `manage-design-system` | 管理设计系统——上传 DESIGN.md 并应用主题 |
| `extract-design-md` | 从前端源代码提取 DESIGN.md 设计系统规范 |
| `extract-static-html` | 从运行中的 Web 应用提取自包含静态 HTML |
| `upload-to-stitch` | 将本地资源上传到 Stitch 项目 |

### Build（构建技能）
| 技能 | 描述 |
|------|------|
| `react-components` | 将 Stitch 设计转换为 React 组件系统 |
| `react-native` | 将 Stitch 设计转换为 React Native 组件 |
| `remotion` | 从 Stitch 项目生成 Remotion 演示视频 |
| `shadcn-ui` | shadcn/ui 组件集成和构建指导 |

### Utilities（工具技能）
| 技能 | 描述 |
|------|------|
| `design-md` | 分析 Stitch 项目生成 DESIGN.md 文件 |
| `enhance-prompt` | 将模糊 UI 想法优化为 Stitch 专用提示词 |
| `stitch-loop` | 从单个提示词生成完整多页面网站 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | TypeScript |
| 标准 | Agent Skills 开放标准 |
| 服务器 | Stitch MCP Server |
| 兼容代理 | Claude Code、Cursor、Codex、Gemini CLI、Antigravity |
| 构建系统 | 插件市场安装或选择性安装 |

---

## 项目亮点

### 1. 遵循 Agent Skills 开放标准
Stitch Skills 的最大价值在于对 Agent Skills 开放标准的遵循。这意味着这些技能不仅限于 Google Stitch 生态，任何兼容该标准的编码代理（如 Claude Code、Cursor）都可以使用，具备良好的跨平台互操作性。

### 2. 全链路设计到代码转换
提供从前端代码→设计系统→设计稿→React 组件的完整双向转换能力。开发者可以从现有代码提取设计系统，也可以从设计稿生成代码，形成完整的设计-开发闭环。

### 3. 模块化插件架构
技能按功能分为 Design、Build、Utilities 三大类，每类独立安装。开发者可根据需要选择性安装，避免引入不必要的依赖。

### 4. 演示视频自动生成
`remotion` 技能能从设计稿自动生成带过渡动画和缩放效果的产品演示视频，为设计展示和产品发布提供了全新的自动化方式。

---

## 应用场景

### 1. 前端代码迁移到设计系统
将已有的 React/Vue 前端代码逆向提取为 DESIGN.md 设计系统规范，便于在 Stitch 设计工具中可视化管理。

### 2. 设计稿到生产代码
设计师在 Stitch 中完成设计后，通过 Stitch Skills 自动转换为 React/React Native 组件，大幅缩短设计到开发的时间。

### 3. AI 辅助 UI 开发
配合 Claude Code 或 Cursor 等 AI 编码代理，Stitch Skills 赋予 AI 理解设计系统和生成一致 UI 组件的能力。

### 4. 产品展示和文档
利用 `remotion` 技能从设计项目自动生成演示视频，用于产品发布、内部汇报和用户文档。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| Stars | 6,583 |
| Forks | 914 |
| 今日新增 | 101 |
| 创建时间 | 2026-01-16 |

---

## 总结

Stitch Skills 代表了 AI 编码代理技能生态的前沿探索——通过标准化的技能接口将设计工具、构建工具和编码代理串联起来，形成从设计到生产的全链路 AI 辅助工作流。

---

*数据来源：GitHub 仓库 (google-labs-code/stitch-skills)，2026 年 7 月访问*

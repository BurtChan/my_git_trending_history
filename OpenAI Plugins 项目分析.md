# OpenAI Plugins 项目分析

## 项目名称
**OpenAI Plugins** — OpenAI Codex 插件官方示例集合

- **GitHub**: [openai/plugins](https://github.com/openai/plugins)
- **许可证**: 无统一仓库许可证（各插件独立声明，多数为 MIT，部分如 Figma 使用 LicenseRef-Figma-Developer-Terms）

---

## 项目概述

OpenAI Plugins 是 OpenAI 官方维护的 Codex 插件示例仓库，为开发者展示了如何扩展 Codex CLI 和 Codex 桌面应用的能力。仓库包含 **100+ 个插件实现**，每个插件通过标准的 `.codex-plugin/plugin.json` 清单文件定义，配合 skills、MCP 服务器、agents、commands 等配套资源，构建出完整的 AI 编码工作流增强方案。

该仓库是 OpenAI 推动 AI 编码工具生态建设的核心举措。随着 Codex CLI 和 Codex 桌面应用的发布，OpenAI 需要向社区展示插件体系的最佳实践，并提供可直接使用的官方和第三方插件。仓库中的插件涵盖了设计工具（Figma、Canva）、协作平台（Notion、Linear）、多平台应用构建（iOS/macOS/Web）、前端框架（Expo）、部署平台（Netlify、Cloudflare）、动画工具（Remotion）、CRM（HubSpot）、金融数据（Alpaca、Binance）、搜索引擎、项目管理等多个领域，充分展现了 Codex 插件系统的灵活性和广度。

Codex 插件是一个**可安装的工作流捆绑包**，而非单一提示词。每个插件由三层架构组成：**Skill（技能）** 定义 Codex 应如何完成任务，**App（应用）** 连接外部工具和服务，**MCP Server（模型上下文协议服务器）** 提供专门能力。这三层设计使得单个插件能够同时在 Codex 桌面应用、CLI 和 IDE 扩展中运行。

---

## Star 数据统计

| 指标 | 数值 |
|------|------|
| 总 Star 数 | 1,643 |
| 总 Fork 数 | 252 |
| 今日新增 Star | 49 |
| 贡献者数量 | 54 |
| 总提交数 | 252 |
| 创建时间 | 2026-03-04 |
| 主要语言 | JavaScript |
| 仓库许可证 | 未统一（各插件独立声明） |

仓库自 2026 年 3 月创建以来，在短短三个月内即获得超过 1,600 颗 Star，日均新增约 18 颗 Star，反映出开发者社区对 Codex 插件生态的强烈兴趣。54 位贡献者中既包含 OpenAI 内部工程师（如 @cching-openai、@ashwinm-oai、@vb-openai 等），也包含来自 Figma、Netlify、Expo、Remotion 等合作公司的开发者，体现了跨企业协作的开源生态模式。

---

## 核心功能详解

### 插件体系架构

Codex 插件的核心是标准化的目录结构和声明式配置。每个插件遵循统一的组织规范：

| 组件 | 路径 | 说明 |
|------|------|------|
| 清单文件 | `.codex-plugin/plugin.json` | 必需，定义插件元数据、版本、描述、作者、许可证、关键词等 |
| 技能目录 | `skills/` | 包含 SKILL.md 和 references/，定义 Codex 执行特定任务的知识和规则 |
| 应用配置 | `.app.json` | 可选，定义与外部服务的连接配置 |
| MCP 服务器 | `.mcp.json` | 可选，配置模型上下文协议服务器，提供工具调用能力 |
| Agent 定义 | `agents/` | 可选，插件级别的 Agent 配置（如 openai.yaml） |
| 命令定义 | `commands/` | 可选，定义可由用户触发的自定义命令 |
| 钩子配置 | `hooks.json` | 可选，定义工作流中的生命周期钩子 |
| 资源文件 | `assets/` | 包含图标、logo、截图等 UI 资源 |
| 构建脚本 | `scripts/` | 可选，包含自动化脚本（如 build_and_run.sh） |

### plugin.json 清单结构

每个插件的 `plugin.json` 清单文件包含完整的元信息定义，以 Figma 插件为例：

```json
{
  "name": "figma",
  "version": "2.0.8",
  "description": "Figma workflows for design implementation...",
  "author": { "name": "Figma", "url": "https://www.figma.com" },
  "license": "LicenseRef-Figma-Developer-Terms",
  "skills": "./skills/",
  "apps": "./.app.json",
  "interface": {
    "displayName": "Figma",
    "category": "Design",
    "capabilities": ["Interactive", "Read", "Write"],
    "defaultPrompt": ["Inspect a Figma design and implement it in code"],
    "brandColor": "#1ABCFE"
  }
}
```

关键字段包括 `capabilities`（定义交互模式：Interactive/Read/Write）、`category`（分类标签）、`defaultPrompt`（默认使用提示）、`brandColor`（品牌色）等，这些元数据在 Codex 插件市场中用于展示和检索。

### 插件创建机制

仓库根目录的 `.agents/skills/plugin-creator/` 内置了 `$plugin-creator` 技能，这是一个自举式工具——用 Codex 插件体系本身来创建新插件。开发者只需描述需求，`$plugin-creator` 即可自动脚手架生成 `.codex-plugin/plugin.json` 清单及配套文件结构，大幅降低插件开发门槛。

---

## 主要技术栈

| 技术领域 | 涉及技术/平台 |
|----------|---------------|
| 插件核心 | plugin.json 清单、SKILL.md、.mcp.json、.app.json |
| iOS 开发 | SwiftUI、App Intents、Xcode、XcodeBuildMCP、SwiftUI Previews |
| macOS 开发 | Swift、SwiftUI、AppKit、SwiftPM、codesign、notarytool、lldb |
| Web 开发 | React、shadcn/ui、Supabase、Postgres、Stripe |
| 跨平台移动 | Expo、React Native、Expo Router、EAS Build、Native Modules |
| 部署运维 | Netlify、Cloudflare、CircleCI、GitHub Actions |
| 设计工具 | Figma、Canva、Code Connect、Design System |
| 动画视频 | Remotion、React、FFmpeg、Three.js |
| 协作文档 | Notion、Google Slides、Google Drive |
| 项目管理 | Linear、Asana、ClickUp、Monday.com |
| CRM/销售 | HubSpot、Close、Attio、Carta CRM |
| 数据分析 | Amplitude、Mixpanel、Datadog、Metabase、MotherDuck |
| 金融交易 | Alpaca、Binance、Brex、FactSet、Morningstar |
| AI/ML | Hugging Face、Fal AI、OpenAI API |
| 通信支持 | Gmail、Intercom、Help Scout、Fireflies |

---

## 重点插件分析

### 开发构建类插件

| 插件名称 | 版本 | 核心能力 | 关键技术 |
|----------|------|----------|----------|
| build-ios-apps | 0.1.1 | iOS 应用构建与调试 | SwiftUI、App Intents、XcodeBuildMCP、Simulator、性能分析、内存泄漏检测 |
| build-macos-apps | — | macOS 原生应用开发 | Swift、AppKit 互操作、SwiftPM、签名公证、窗口管理、Liquid Glass |
| build-web-apps | 0.1.1 | Web 前端应用构建 | shadcn/ui、Stripe 支付、Supabase 数据库、浏览器测试 |
| expo | 1.0.1 | 跨平台移动应用开发 | Expo Router、EAS Build、OTA 升级、TestFlight/App Store 部署 |

**build-ios-apps** 是功能最为丰富的开发插件之一。它涵盖了从 App Intents 和 App Shortcuts 设计到 SwiftUI UI 构建的全流程，支持在 Codex 内置浏览器中渲染 SwiftUI 预览，支持 Liquid Glass 等现代 iOS 设计模式，还提供 ETTrace 性能分析和内存泄漏检测等调试工具。插件通过 `.mcp.json` 配置了 XcodeBuildMCP 服务器，实现了与 Xcode 构建系统的深度集成。

**build-macos-apps** 采用了与 iOS 插件不同的策略——纯 Shell 优先模式。核心执行依赖 `xcodebuild`、`swift`、`open`、`lldb`、`codesign`、`spctl` 等命令行工具，不假设模拟器或触控式 UI 检查。插件包含 12 个子技能：build-run-debug、test-triage、signing-entitlements、swiftpm-macos、packaging-notarization、swiftui-patterns、liquid-glass、window-management、appkit-interop、view-refactor、telemetry 等，覆盖了 macOS 应用开发的全生命周期。

**expo** 插件由 Expo 团队官方编写（author 为 "Expo Team"，email 为 support@expo.dev），体现了 OpenAI 与开源框架团队的深度合作。该插件提供 Expo Router UI 构建、API 路由编写、数据获取与样式配置、Native Modules 开发、Dev Client 创建、SDK 升级以及 EAS 部署工作流（包括 TestFlight、App Store、Play Store）等完整能力。

### 设计与创意类插件

| 插件名称 | 版本 | 核心能力 | 能力模式 |
|----------|------|----------|----------|
| figma | 2.0.8 | 设计到代码转换、Code Connect 模板 | Interactive, Read, Write |
| canva | — | Canva 设计集成 | — |
| remotion | 1.0.1 | 基于React的程序化视频创作 | Read, Write |

**figma** 是仓库中版本号最高（v2.0.8）且最成熟的插件之一，由 Figma 团队直接维护。它实现了三大核心工作流：设计稿到代码实现（Design-to-Code）、Code Connect 模板生成（用于 Figma 组件的代码关联）、以及项目特定设计系统规则生成。插件使用 Figma 自定义许可证（LicenseRef-Figma-Developer-Terms），而非 MIT。其默认提示词包括"检查 Figma 设计并用代码实现"、"为组件创建 Code Connect 模板"、"在 Figma 中构建或更新屏幕"等。

**remotion** 由 Remotion 团队官方贡献，支持动画、时间轴、音频、字幕、3D、转场、图表、文字特效等程序化视频创作能力。通过 React 声明式语法定义视频内容，结合 FFmpeg 渲染，是创意工作者的强大工具。

### 部署与基础设施插件

| 插件名称 | 版本 | 核心能力 |
|----------|------|----------|
| netlify | 1.1.1 | 项目部署、预览与生产环境管理 |
| cloudflare | — | CDN 和基础设施管理 |
| circleci | — | CI/CD 流水线配置与管理 |
| github | — | Git 仓库操作与 GitHub 集成 |

**netlify** 插件由 Netlify 官方维护（author.name 为 "Netlify"），提供部署状态检查、站点管理和预览/生产环境工作流。插件通过 `.app.json` 配置与 Netlify 平台的连接，品牌色为 Netlify 标志性的 `#00AD9F`。

### 协作与效率类插件

| 插件名称 | 核心能力 |
|----------|----------|
| notion | 实现规划、研究综合、会议准备、知识捕获 |
| linear | 项目管理与Issue追踪 |
| google-slides | 演示文稿创建与编辑 |
| gmail | 邮件读取与发送 |
| calendly / google-calendar | 日程管理 |

**notion** 插件将规格文档转化为实施计划、将研究综合为结构化文档、准备会议材料并捕获决策到知识页面，是 AI 驱动知识管理的典型应用。

### 数据与金融类插件

仓库中数据分析和金融类插件数量庞大，体现了 Codex 在非传统编码领域的扩展能力：

- **数据分析**：Amplitude、Mixpanel（含 headless 版本）、Datadog、Metabase、Cube、Deepnote、MotherDuck 等
- **金融交易**：Alpaca（美股交易API）、Binance（加密货币）、Brex（企业金融）、FactSet（金融数据）、LSEG（伦敦证券交易所）、Morningstar（投资研究）
- **企业情报**：CB Insights、HG Insights、D&B Finance Analytics、Channel99 等

这些插件将 Codex 的能力从纯粹的代码编写扩展到数据分析、金融建模和商业智能领域，大幅拓宽了 AI 编码工具的应用边界。

### 其他特色插件

| 插件名称 | 领域 | 特色 |
|----------|------|------|
| hugging-face | AI/ML | Hugging Face 模型和数据集访问 |
| fal | AI 推理 | AI 模型托管和推理 |
| coderabbit | 代码审查 | AI 驱动的代码审查 |
| codex-security | 安全扫描 | 安全漏洞检测 |
| lovable | 应用构建 | 无代码/低代码应用构建 |
| convex | 后端平台 | 实时后端服务 |
| game-studio | 游戏开发 | 游戏制作工作流 |

---

## 项目亮点

### 跨企业协作的开源生态

仓库的独特之处在于它不仅包含 OpenAI 自身编写的插件（如 notion、build-ios-apps、build-web-apps），还直接收录了合作伙伴官方维护的插件——Figma 团队编写了 figma 插件，Netlify 团队编写了 netlify 插件，Expo 团队编写了 expo 插件，Remotion 团队编写了 remotion 插件。这种多方参与的开放模式打破了传统官方示例库的单一来源限制，使得仓库成为真正的行业标准参考。

### 自举式插件创建工具

`.agents/skills/plugin-creator` 是一个精妙的设计——用插件体系本身来创建新插件。开发者无需手动了解复杂的清单格式和目录结构，只需通过 `$plugin-creator` 技能描述需求即可自动生成标准化的插件骨架。这种"吃自己的狗粮"（dogfooding）实践证明了 Codex 插件体系的表达力。

### 多层次工作流抽象

Codex 插件不是简单的 API 封装，而是真正的多层次工作流抽象：
1. **Skill 层**：定义 Codex 执行任务的规则和最佳实践（通过 SKILL.md）
2. **App 层**：连接外部服务和工具（通过 .app.json）
3. **MCP 层**：提供专门的工具调用能力（通过 .mcp.json）
4. **Agent 层**：定义插件级别的智能代理（通过 agents/）
5. **Command 层**：定义用户可触发的命令（通过 commands/）
6. **Hook 层**：定义工作流生命周期钩子（通过 hooks.json）

这种分层设计使得插件既能提供简单的知识增强，也能实现复杂的自动化工作流。

### 覆盖面极广的领域

从传统的软件开发工具（GitHub、CircleCI）到创意设计（Figma、Canva、Remotion），从项目管理（Linear、Asana）到金融分析（Binance、Morningstar），从企业搜索（Coveo、Hebbia）到法律合规（Docket），插件覆盖了企业级工作流的几乎所有关键环节。100+ 插件的覆盖面在同类 AI 编码工具中首屈一指。

---

## 应用场景

### 场景一：全栈应用快速原型开发

开发者可以同时启用 **build-web-apps**（前端构建）、**netlify**（部署）、**github**（版本控制）、**convex**（后端）等插件，让 Codex CLI 自动完成从设计到部署的完整流程。加上 **stripe** 集成，甚至可以快速搭建一个具备支付功能的 SaaS 产品原型。

### 场景二：设计到代码的自动化转换

UI/UX 设计师和前端开发者可以通过 **figma** 插件，将 Figma 设计稿自动转化为可运行的代码。配合 **build-web-apps** 的 shadcn/ui 组件库和浏览器测试能力，实现设计到代码的高效落地。Code Connect 模板功能确保 Figma 组件与代码组件的双向同步。

### 场景三：跨平台移动应用开发

使用 **expo** 插件可以快速启动 React Native 项目，配置 Expo Router 路由、编写 API 路由、管理 Native Modules、处理 OTA 更新，并最终通过 EAS Build 部署到 TestFlight 和应用商店。整个流程由 Codex 的 AI 能力驱动，大幅降低移动开发的入门门槛。

### 场景四：企业知识管理与自动化

结合 **notion**（知识库）、**linear**（任务管理）、**google-calendar**（日程）、**gmail**（邮件）、**slack**（协作，如已集成）等插件，Codex 可以充当企业的 AI 助理，自动整理会议纪要、跟踪项目进度、生成报告并同步到相关平台。

### 场景五：数据驱动决策支持

**amplitude**、**mixpanel**、**metabase**、**motherduck** 等数据分析插件，配合 **alpaca**、**binance** 等金融插件，使得 Codex 可以成为数据分析师的助手——自动查询数据、生成可视化图表、编写分析报告，甚至执行交易策略。

---

## 总结

OpenAI Plugins 仓库是 Codex 插件生态的官方"食谱集"和参考实现库。它在短短三个月内聚集了 100+ 插件、54 位贡献者和 1,600+ Star，已成为 AI 编码工具生态建设的重要基础设施。仓库的价值不仅在于提供了可直接使用的插件，更在于建立了一套标准化的插件架构规范（plugin.json 清单 + 分层目录结构），为整个 Codex 生态的繁荣奠定了基础。

从技术角度看，该仓库展示了 Codex 插件体系的核心设计哲学：通过声明式配置（plugin.json）定义插件身份和元数据，通过 Skill 定义知识增强，通过 MCP 定义工具扩展，通过 Agent 定义智能行为。这种分层解耦的设计使得插件既能保持简洁（仅需 plugin.json 即可构成最小插件），也能表达复杂的工作流（全组件组合）。

对于开发者而言，该仓库既是学习 Codex 插件开发的最佳起点，也是获取现成工作流增强的实用资源库。无论你是想构建 iOS/macOS/Web 应用、管理 Notion 文档、部署到 Netlify、创建 Remotion 动画视频，还是进行金融数据分析，都能在这里找到对应的插件实现作为参考。

---

*数据来源：2026 年 6 月访问 [GitHub - openai/plugins](https://github.com/openai/plugins)，数据截至 2026 年 6 月 6 日。*

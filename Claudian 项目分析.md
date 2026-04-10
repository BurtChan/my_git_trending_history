# Claudian 项目分析

> **Obsidian 内的 AI 编码 Agent** -- 将 Claude Code 和 Codex 嵌入 Obsidian 知识库，让 Vault 成为 Agent 的原生工作目录，实现文件读写、搜索、终端和多步骤工作流的一体化协作。

- **GitHub**: [YishenTu/claudian](https://github.com/YishenTu/claudian)
- **语言**: TypeScript
- **Stars**: 6,623+（日增长 +174）
- **许可证**: MIT
- **作者**: YishenTu (@YishenTu)

---

## 基本信息

| 项目 | 详情 |
| --- | --- |
| **项目名称** | Claudian |
| **GitHub 地址** | https://github.com/YishenTu/claudian |
| **项目定位** | An Obsidian plugin that embeds AI coding agents (Claude Code, Codex) in your vault |
| **Stars** | 6,623+（日增长 +174，快速增长中） |
| **Forks** | 持续增长中 |
| **许可证** | MIT |
| **主要语言** | TypeScript |
| **创建者** | YishenTu (@YishenTu) |
| **运行平台** | macOS / Linux / Windows（仅桌面端） |
| **最低要求** | Obsidian v1.4.5+、Claude Code CLI 或 Codex CLI |
| **支持的 AI 提供商** | Anthropic Claude（默认）、OpenAI Codex、Openrouter、Kimi 等 |

---

## 解决什么问题

Obsidian 是一款强大的知识管理工具，但缺乏与 AI 编码 Agent 的深度集成。用户在 Obsidian 中撰写笔记、管理项目文档时，若想利用 AI 编码能力，通常需要在多个应用之间来回切换，存在以下痛点：

1. **上下文割裂**：在 Obsidian 中写文档，在终端中跑 Claude Code，两者之间无法共享文件系统和知识库上下文，信息流转效率低。
2. **无法就地编辑**：传统 AI 聊天工具与笔记内容分离，无法直接在笔记中选中文字让 AI 就地进行修改和优化。
3. **缺乏文件级协作**：AI Agent 无法直接读取和操作 Vault 中的笔记文件，无法进行多步骤的文件搜索、编辑、创建工作流。
4. **多工具管理复杂**：Claude Code、Codex 等 AI 工具各有自己的配置和界面，缺乏统一的集成入口。
5. **对话与知识脱节**：AI 对话记录散落在系统各处，无法与 Obsidian 知识库中的笔记形成有机联系。

Claudian 通过将 Claude Code 和 Codex 直接嵌入 Obsidian 插件中，让 Vault 目录成为 Agent 的原生工作空间，从根本上解决了 AI 编码 Agent 与知识管理工具之间的协作鸿沟。

---

## 核心功能

### 侧边栏聊天（Chat Sidebar）

从 Obsidian 的功能区图标或命令面板打开聊天侧边栏，与 AI Agent 进行自然语言交互。Agent 可以直接读取、写入、编辑和搜索 Vault 中的文件，就像在终端中使用 Claude Code 一样。

### 内联编辑（Inline Edit）

选中笔记中的文字（或从光标位置开始），通过快捷键触发内联编辑。Agent 直接在笔记中进行修改，并提供**逐词差异预览**（word-level diff），让每次修改清晰可见。

### 斜杠命令与技能（Slash Commands & Skills）

在聊天输入框中输入 `/` 或 `$` 即可调用可复用的提示模板或技能（Skills），支持用户级和 Vault 级两个作用域，实现"一次定义，到处使用"。

### @提及系统（@mention）

输入 `@` 即可提及 Agent 需要操作的任何对象：
- **Vault 文件**：直接引用知识库中的笔记
- **子 Agent（Subagent）**：调用专业化的子任务处理器
- **MCP 服务器**：连接外部工具服务
- **外部目录文件**：引用 Vault 之外的文件资源

### 计划模式（Plan Mode）

通过 `Shift+Tab` 切换。Agent 在实施之前先探索和设计，生成详细的执行计划供用户审核批准，避免盲目操作。

### 指令模式（Instruction Mode `#`）

在聊天输入中通过 `#` 添加精细化的自定义指令，对 Agent 的行为进行精确控制。

### MCP 服务器集成

通过 Model Context Protocol（支持 stdio、SSE、HTTP 三种传输方式）连接外部工具和服务：
- **Claude 提供商**：在应用内管理 Vault 的 MCP 配置
- **Codex 提供商**：使用 Codex CLI 自身的 MCP 配置

### 多标签与对话管理

- 支持多个聊天标签页，同时处理多个任务
- 完整的对话历史管理
- 支持**分叉（Fork）**、**恢复（Resume）**和**压缩（Compact）**对话

### 多 AI 提供商支持

| 提供商 | 说明 |
| --- | --- |
| **Claude（默认）** | 通过 Claude Code CLI，支持 Claude 订阅、API 或兼容提供商（Openrouter、Kimi 等） |
| **Codex（可选）** | 通过 Codex CLI，OpenAI 的编码 Agent |

---

## 技术栈

| 层次 | 技术 |
| --- | --- |
| **插件框架** | Obsidian Plugin API |
| **主要语言** | TypeScript |
| **构建工具** | npm（标准 Node.js 工具链） |
| **Claude 集成** | Claude Agent SDK（@anthropic-ai/claude-code） |
| **Codex 集成** | Codex app-server（JSON-RPC 传输、JSONL 历史记录） |
| **协议支持** | Model Context Protocol（MCP）-- stdio / SSE / HTTP |
| **国际化** | 自建 i18n 模块，支持 10 种语言 |
| **UI 组件** | Obsidian 原生 UI + 自定义模块化 CSS |
| **安全模型** | 本地审批机制（Approval Utilities） |

### 项目架构

```
src/
├── main.ts                  # 插件入口
├── app/                     # 共享默认值和插件级存储
├── core/                    # 提供商无关的运行时、注册表和类型契约
│   ├── runtime/             # ChatRuntime 接口和审批类型
│   ├── providers/           # 提供商注册表和工作区服务
│   ├── security/            # 审批工具
│   └── ...                  # commands, mcp, prompt, storage, tools, types
├── providers/
│   ├── claude/              # Claude SDK 适配器、提示编码、存储、MCP、插件
│   └── codex/               # Codex app-server 适配器、JSON-RPC 传输、JSONL 历史
├── features/
│   ├── chat/                # 侧边栏聊天：标签、控制器、渲染器
│   ├── inline-edit/         # 内联编辑模态框和提供商支持
│   └── settings/            # 设置面板（含提供商标签页）
├── shared/                  # 可复用 UI 组件和模态框
├── i18n/                    # 国际化（10 种语言）
├── utils/                   # 跨领域工具函数
└── style/                   # 模块化 CSS
```

架构设计上的亮点：
- **core/ 层提供商无关**：运行时接口、类型契约、命令系统均为通用设计，方便扩展新的 AI 提供商
- **providers/ 层可插拔**：Claude 和 Codex 作为独立适配器实现，互不干扰
- **features/ 层功能解耦**：聊天、内联编辑、设置三大功能模块独立，便于维护和扩展

---

## 使用场景

### 知识工作者：AI 辅助笔记与写作
- 在 Obsidian 笔记中选中段落，让 AI 就地润色、翻译、扩写
- 利用 Plan Mode 让 AI 先分析笔记结构再提出修改建议
- 通过 @mention 引用多篇笔记让 AI 进行交叉分析和综合总结

### 开发者：Vault 内编码工作流
- 将项目代码库放在 Vault 中（或通过 @mention 引用外部目录），直接在 Obsidian 内完成代码编写、调试、重构
- 利用多标签同时处理多个编码任务，对话历史与项目文档共存一处
- 通过 MCP 连接外部开发工具（数据库、API 测试等），构建完整的开发环境

### 研究人员：文献处理与知识提取
- 将 PDF、笔记导入 Vault，让 AI Agent 阅读并生成摘要、提取关键信息
- 利用 Slash Commands 创建标准化的分析模板，批量处理研究材料
- 通过内联编辑在原始笔记上叠加 AI 生成的批注和分析

### 团队协作：共享知识库 + AI 增强
- 团队共享的 Obsidian Vault 中安装 Claudian，所有成员获得一致的 AI 辅助体验
- 利用 Vault 级 Skills 定义团队标准化的工作流程
- 通过指令模式（#）确保 AI 输出符合团队的格式和质量要求

### 多模型协作场景
- 同时配置 Claude 和 Codex 提供商，在不同任务中选择最合适的模型
- 利用子 Agent（Subagent）机制，将子任务分派给不同模型处理

---

## 隐私与数据安全

| 数据类型 | 存储位置 |
| --- | --- |
| **发送至 API 的数据** | 用户输入、附件、图片、工具调用输出（默认发送至 Anthropic/OpenAI，可通过环境变量配置） |
| **本地存储** | Vault 内 `.claudian/` 目录（设置和会话元数据）、`.claude/` 目录（Claude 提供商文件） |
| **对话记录** | `~/.claude/projects/`（Claude）、`~/.codex/sessions/`（Codex） |
| **遥测** | 无 -- 除配置的 API 提供商外，不进行任何数据追踪 |

---

> **Claudian 是目前将 AI 编码 Agent 与 Obsidian 知识库深度融合的最成熟方案，凭借原生工作目录集成、内联差异编辑、多提供商支持和 MCP 扩展能力，让 Obsidian 从个人知识管理工具升级为 AI 驱动的智能工作空间。**

---

*分析日期：2026-04-10 | Stars: 6,623+ | 来源: [GitHub - YishenTu/claudian](https://github.com/YishenTu/claudian)*

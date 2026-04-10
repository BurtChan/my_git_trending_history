# Oh-My-ClaudeCode 项目分析

> **Claude Code 的多 Agent 编排引擎** -- 零学习曲线的团队优先多智能体协作框架，让 Claude Code 从单兵作战进化为团队协同。

- **GitHub**: [Yeachan-Heo/oh-my-claudecode](https://github.com/Yeachan-Heo/oh-my-claudecode)
- **npm 包名**: `oh-my-claude-sisyphus`
- **语言**: TypeScript / JavaScript
- **Stars**: 11,000+
- **许可证**: MIT
- **作者**: Yeachan Heo (@Yeachan-Heo)

---

## 基本信息

| 项目 | 详情 |
| --- | --- |
| **项目名称** | oh-my-claudecode (OMC) |
| **GitHub 地址** | https://github.com/Yeachan-Heo/oh-my-claudecode |
| **项目定位** | Teams-first Multi-agent orchestration for Claude Code |
| **Stars** | 11,000+（GitHub 上最热门的 Claude Code 增强项目之一） |
| **许可证** | MIT |
| **主要语言** | TypeScript / JavaScript |
| **npm 包名** | oh-my-claude-sisyphus |
| **创建者** | Yeachan Heo (@Yeachan-Heo) |
| **核心维护者** | Yeachan Heo、HaD0Yun (@HaD0Yun) |
| **文档语言** | English / 한국어 / 中文 / 日本語 / Español / Tiếng Việt / Português |
| **最低要求** | Claude Code CLI + Claude Max/Pro 订阅或 Anthropic API Key |

---

## 解决什么问题

Claude Code 本身是一个强大的单 Agent 编程工具，但在面对**复杂的多步骤任务**时存在明显局限：

1. **缺乏团队协作机制**：单个 Claude 实例无法同时处理架构设计、代码编写、测试验证等并行工作，导致大型任务串行执行，效率低下。
2. **没有编排策略**：用户需要手动拆解任务、逐个指示 Claude Code 执行，无法通过自然语言描述复杂目标后自动完成全流程。
3. **Token 消耗不优化**：所有任务都使用同一模型等级，简单任务浪费 Opus 级别的 Token，复杂任务又可能用 Haiku 处理导致质量不足。
4. **经验无法复用**：每次解决同类问题时需要重复相同的调试过程，缺乏从经验中学习和模式提取的机制。
5. **缺乏跨模型协作**：无法利用 Codex（代码审查）、Gemini（UI/设计、100 万 Token 上下文）等不同模型的互补优势。

OMC 通过提供一个**团队优先的多 Agent 编排层**来解决这些问题，在 Claude Code 之上构建了完整的任务分配、并行执行、质量验证和经验学习机制。

---

## 核心功能

### 编排模式（8 种策略）

| 模式 | 说明 | 适用场景 |
| --- | --- | --- |
| **Team（推荐）** | 规范化阶段流水线：team-plan -> team-prd -> team-exec -> team-verify -> team-fix | 多个 Claude Agent 协作完成共享任务清单 |
| **omc team（CLI）** | tmux CLI 工作进程，真实的 claude/codex/gemini 进程在分屏面板中运行 | Codex/Gemini CLI 任务；按需生成，完成任务后销毁 |
| **ccg** | 三模型顾问：通过 /ask codex + /ask gemini 咨询，Claude 综合分析 | 需要同时利用 Codex 和 Gemini 的混合后端+UI 工作 |
| **Autopilot** | 自主执行模式（单主 Agent） | 端到端功能开发，最小化人工干预 |
| **Ultrawork** | 最大并行度（非 Team 模式） | 突发并行修复/重构，无需 Team 模式时使用 |
| **Ralph** | 持久模式，带验证/修复循环 | 必须完整完成的任务（不留部分结果） |
| **Pipeline** | 顺序阶段处理 | 严格排序的多步骤转换 |
| **Ultrapilot** | 已弃用的兼容模式（autopilot pipeline 别名） | 旧版工作流兼容 |

### 19 个专业化 Agent

OMC 内置 19 个专业化 Agent（含分层变体），涵盖：
- **架构 Agent**：系统设计和架构决策
- **研究 Agent**：代码库搜索和技术调研
- **设计 Agent**：UI/UX 设计相关任务
- **执行 Agent**：代码编写和实现
- **测试 Agent**：测试编写和验证
- **数据科学 Agent**：数据分析和机器学习相关任务

### 智能模型路由

根据任务复杂度自动选择合适的模型等级，节省 30-50% 的 Token 消耗：
- **Haiku**：简单查找、快速任务
- **Sonnet**：标准任务
- **Opus**：架构设计、深度分析

### 自定义技能系统（Skill）

"学一次，用一世"的可复用知识提取机制：

| 作用域 | 路径 | 共享范围 | 优先级 |
| --- | --- | --- | --- |
| 项目级 | `.omc/skills/` | 团队共享（可版本控制） | 高（覆盖用户级） |
| 用户级 | `~/.omc/skills/` | 所有项目共享 | 低（兜底） |

支持自动学习和自动注入：OMC 从会话中提取可复用的调试知识，生成便携式技能文件，当匹配到相关上下文时自动加载。

### 开发者体验

- **魔法关键词**：`ralph`、`ulw`、`ralplan`、`autopilot`、`ccg`、`deepsearch` 等快捷触发
- **HUD 状态栏**：实时显示编排指标和当前状态
- **分析与成本追踪**：跨会话 Token 使用分析
- **通知集成**：支持 Telegram / Discord / Slack 回调通知

### 多 AI 协作

OMC 可选地编排外部 AI 提供商，实现跨模型验证：

| 提供商 | 安装方式 | 功能 |
| --- | --- | --- |
| Gemini CLI | `npm install -g @google/gemini-cli` | 设计审查、UI 一致性（100 万 Token 上下文） |
| Codex CLI | `npm install -g @openai/codex` | 架构验证、代码审查交叉检验 |

三套 Pro 计划（Claude + Gemini + ChatGPT）约 $60/月即可覆盖全部功能。

---

## 技术栈

| 组件 | 技术 |
| --- | --- |
| **核心语言** | TypeScript / JavaScript |
| **运行时** | Node.js（npm 包分发） |
| **包名** | oh-my-claude-sisyphus（npm） |
| **安装方式** | npm CLI / Claude Code Plugin Marketplace |
| **多路复用** | tmux / psmux（Windows 原生） |
| **Agent 通信** | tmux 分屏面板 + JSONL |
| **状态持久化** | `.omc/state/`、`.omc/sessions/`、`.omc/plans/` |
| **技能存储** | `.omc/skills/`（项目级）、`~/.omc/skills/`（用户级） |
| **通知** | Telegram Bot API / Discord Webhook / Slack Webhook |
| **外部集成** | OpenClaw Gateway、Codex CLI、Gemini CLI |
| **CI/CD** | Claude Code Plugin Marketplace |
| **平台支持** | macOS / Linux / Windows（psmux 原生 tmux）/ WSL2 |

---

## 使用场景

| 场景 | 说明 | 推荐模式 |
| --- | --- | --- |
| **全栈功能开发** | 从需求到代码到测试的端到端自动化 | Autopilot / Team |
| **大规模代码重构** | 多文件并行修改，自动验证不破坏现有功能 | Ultrawork / Ralph |
| **Bug 批量修复** | 一次性修复所有 TypeScript 错误或 lint 警告 | Team（多 executor） |
| **需求澄清** | 对模糊想法进行苏格拉底式提问，明确需求后再开发 | deep-interview |
| **跨模型代码审查** | 同时用 Codex 审查架构、Gemini 审查 UI，Claude 综合 | ccg / omc team |
| **持续验证任务** | 必须确保完全通过验证的关键任务（部署前检查等） | Ralph |
| **技能沉淀** | 将团队调试经验提取为可复用的技能文件 | /learner |
| **多步骤流水线** | 严格顺序的多阶段数据处理或文档生成 | Pipeline |
| **架构深度思考** | 需要深度推理的架构设计和技术决策 | ultrathink |
| **代码库全局搜索** | 快速在大型代码库中定位特定模式或中间件 | deepsearch |

---

## 快速开始

```bash
# 方式一：Plugin Marketplace 安装（推荐）
/plugin marketplace add https://github.com/Yeachan-Heo/oh-my-claudecode
/plugin install oh-my-claudecode

# 方式二：npm 全局安装
npm i -g oh-my-claude-sisyphus@latest

# 运行 Setup
/setup

# 立即使用 -- 自主构建
autopilot: build a REST API for managing tasks

# 不确定从哪里开始？用深度访谈澄清需求
/deep-interview "I want to build a task management app"

# Team 模式 -- 多 Agent 协作
/team 3:executor "fix all TypeScript errors"

# CLI 多模型协作
omc team 2:codex "review auth module for security issues"
omc team 2:gemini "redesign UI components for accessibility"

# 三模型综合分析
/ccg Review this PR — architecture (Codex) and UI components (Gemini)
```

---

## 魔法关键词速查

| 关键词 | 效果 | 示例 |
| --- | --- | --- |
| `team` | Team 编排 | `/team 3:executor "fix all TS errors"` |
| `omc team` | tmux CLI 工作进程 | `omc team 2:codex "security review"` |
| `ccg` | 三模型综合 | `/ccg review this PR` |
| `autopilot` | 自主执行 | `autopilot: build a todo app` |
| `ralph` | 持久验证模式 | `ralph: refactor auth` |
| `ulw` | 最大并行 | `ulw fix all errors` |
| `ralplan` | 迭代规划共识 | `ralplan this feature` |
| `deep-interview` | 苏格拉底需求澄清 | `deep-interview "vague idea"` |
| `deepsearch` | 代码库搜索 | `deepsearch for auth middleware` |
| `ultrathink` | 深度推理 | `ultrathink about this architecture` |
| `cancelomc` / `stopomc` | 停止活跃 OMC 模式 | `stopomc` |

---

## 适用人群

| 角色 | 收获 |
| --- | --- |
| **Claude Code 日常用户** | 将 Claude Code 从单 Agent 升级为多 Agent 协作系统，大幅提升生产力 |
| **全栈开发者** | 一条命令驱动多 Agent 完成从架构到测试的全流程 |
| **团队技术负责人** | 利用 Team 模式协调多个 Agent 并行处理代码审查、重构等任务 |
| **AI 工程师** | 学习多 Agent 编排的设计模式和实践经验 |
| **追求效率的开发者** | 通过智能模型路由节省 30-50% Token 成本 |
| **多模型用户** | 统一管理 Claude + Codex + Gemini 三模型的协作工作流 |

---

## 一句话总结

**Oh-My-ClaudeCode（OMC）是一个团队优先的 Claude Code 多 Agent 编排框架，11k+ Stars，提供 8 种编排策略、19 个专业化 Agent、智能模型路由（节省 30-50% Token）、可复用技能系统和跨模型协作（Claude + Codex + Gemini），通过自然语言驱动将 Claude Code 从单兵工具升级为自动化团队。**

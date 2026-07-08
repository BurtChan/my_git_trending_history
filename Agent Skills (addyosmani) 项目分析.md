# Agent Skills (addyosmani) 项目分析

## 项目名称
**Agent Skills** — 面向 AI 编码代理的生产级工程技能库
- **GitHub**: [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills)
- **许可证**: MIT

---

## 项目概述

Agent Skills 是由 Google Chrome 团队核心开发者 Addy Osmani 创建的开源项目，旨在为 AI 编码代理（如 Claude Code、Codex、Cursor 等）提供**生产级别的工程技能规范**。该项目将资深工程师在软件开发各阶段所遵循的工作流、质量门禁和最佳实践进行标准化封装，使 AI 代理能够在每个开发阶段中一致性地执行高质量工程任务。

项目核心理念是将软件开发拆解为六个阶段：**定义（DEFINE）→ 规划（PLAN）→ 构建（BUILD）→ 验证（VERIFY）→ 审查（REVIEW）→ 交付（SHIP）**，每个阶段都有对应的斜杠命令和技能集合。这种结构化的方法确保 AI 代理不是盲目生成代码，而是遵循经过验证的工程方法论，从需求澄清到最终交付的完整生命周期管理。

与 `agentskills/agentskills`（Agent Skills 标准规范）不同，Addy Osmani 的这个仓库是**技能的具体实现版本**，提供了可直接在 Claude Code、Cursor、Copilot 等 AI 编码工具中使用的完整技能集。它不仅定义了技能的标准格式，还包含了 24 个经过精心设计的具体技能，覆盖从需求访谈到代码简化的全流程。

---

## 核心功能

### 8 个斜杠命令

| 命令 | 用途 | 核心原则 |
|------|------|----------|
| `/spec` | 定义要构建什么 | 先写规格再写代码 |
| `/plan` | 规划如何构建 | 小而原子化的任务 |
| `/build` | 增量式构建 | 一次实现一个切片 |
| `/test` | 验证代码正确性 | 测试是代码正确的证明 |
| `/review` | 合并前审查 | 提升代码健康度 |
| `/webperf` | Web 性能审计 | 先度量再优化 |
| `/code-simplify` | 简化代码 | 清晰胜过技巧 |
| `/ship` | 发布到生产环境 | 更快的发布更安全 |

### 自主模式

`/build auto` 命令可一次性生成计划并自主实现所有任务——用户只需审批一次计划，后续自动运行。每个任务仍保持测试驱动和独立提交，遇到失败或高风险操作时自动暂停。

### 24 个完整技能

项目包含 24 个精细设计的技能，按开发阶段分为六大类：

**定义阶段**：`interview-me`（需求访谈）、`idea-refine`（创意提炼）、`spec-driven-development`（规格驱动开发）

**规划阶段**：`planning-and-task-breakdown`（任务分解）

**构建阶段**：`incremental-implementation`（增量实现）、`test-driven-development`（测试驱动开发）、`context-engineering`（上下文工程）、`source-driven-development`（源码驱动开发）、`doubt-driven-development`（质疑驱动开发）、`frontend-ui-engineering`（前端 UI 工程）、`api-and-interface-design`（API 设计）

**验证阶段**：`browser-testing-with-devtools`（浏览器调试）、`debugging-and-error-recovery`（调试与恢复）

**审查阶段**：`code-review-and-quality`（代码审查）、`code-simplification`（代码简化）

**交付阶段**：`ship-it`（发布）、`webperf`（性能审计）、`changelog-generation`（变更日志）

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 技能定义 | Markdown（遵循 Agent Skills 标准） |
| 兼容代理 | Claude Code、Cursor、Copilot CLI、Codex CLI |
| 上下文集成 | MCP（Model Context Protocol） |
| 浏览器调试 | Chrome DevTools MCP |
| 许可证 | MIT |

---

## 项目亮点

### 质疑驱动开发（Doubt-Driven Development）

这是项目中最独特的技能之一。当面临高风险场景（生产部署、安全相关、不可逆操作）或不熟悉的代码时，该技能采用"主张→提取→质疑→调和→停止"的五步对抗式审查流程，可选跨模型升级验证。这种将批判性思维系统化嵌入 AI 工作流的方式，显著提升了 AI 生成代码的可靠性。

### 上下文工程（Context Engineering）

专门解决 AI 代理在不同任务间切换时信息丢失的问题。通过规则文件、上下文打包和 MCP 集成，在正确的时间向代理提供正确的信息，确保输出质量的一致性。这是 AI 编码工具实际使用中常见的痛点，该技能提供了系统化的解决方案。

### 规格驱动开发（Spec-Driven Development）

在编写任何代码之前，先生成包含目标、命令、结构、代码风格、测试策略和边界条件的 PRD（产品需求文档）。这种方法将传统的"先想后做"理念编码为 AI 可执行的流程，有效减少因需求不明确导致的返工。

### 自动技能激活

技能可根据上下文自动激活——例如 API 设计工作触发 `api-and-interface-design`，UI 工作触发 `frontend-ui-engineering`。用户无需手动选择技能，系统会根据当前工作内容智能匹配最合适的工作流。

---

## 应用场景

### AI 辅助的工程团队

对于使用 Claude Code、Cursor 等 AI 编码工具的开发团队，Agent Skills 提供了一套即插即用的工程标准。团队可以基于这些技能定制自己的工作流规范，确保 AI 代理在代码质量、测试覆盖率、安全性等方面达到与资深工程师一致的水平。

### 个人开发者的 AI 编码伴侣

独立开发者使用 AI 编码工具时，往往缺乏系统性的质量保障机制。Agent Skills 通过 8 个斜杠命令和 24 个技能，将软件工程的完整方法论嵌入到 AI 交互中，让个人开发者也能享受"AI + 工程规范"的双重优势。

### 代码质量审查自动化

`code-review-and-quality` 技能实现了五轴代码审查（变更大小控制在约 100 行、严重性标签分类、审查速度规范等），可作为 CI/CD 流水线中的自动化质量门禁，在代码合并前确保一致性。

### 企业级 AI 编码标准化

大型组织引入 AI 编码工具时面临标准化挑战。Agent Skills 提供了遵循 Agent Skills 标准的技能集，可作为企业自定义技能的开发参考和基础模板，加速 AI 编码工具的企业级部署。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ 总 Stars | 72,147 |
| 🍴 总 Forks | 7,815 |
| 📈 今日新增 | 1,317 stars today |
| 🗓️ 创建时间 | 2026-02-15 |
| 🏷️ 主要话题 | agent-skills, claude-code, codex, cursor |
| 💻 主要语言 | JavaScript |

---

## 总结

Agent Skills 是目前 AI 编码代理生态中**最全面、最成熟的工程技能库**之一，由业界知名开发者 Addy Osmani 主导。项目将传统软件工程的精华——从规格驱动开发到质疑驱动审查——系统性地转化为 AI 可执行的技能规范，填补了 AI 编码工具"会写代码但不懂工程"的关键空白。72K+ 的 Stars 和 1,300+ 的今日新增充分说明了开发社区对 AI 编码质量标准化的强烈需求。

---

*数据来源：GitHub 仓库 (addyosmani/agent-skills)，2026 年 7 月访问*

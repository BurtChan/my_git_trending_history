# Ralph 项目分析

## 1. 项目名称与地址

**Ralph** -- 自主 AI Agent 循环工具

**项目地址**：https://github.com/snarktank/ralph

## 2. 项目概述

Ralph 是一个自主 AI Agent 循环工具，由开发者 snarktank 创建并维护，基于 Geoffrey Huntley 提出的 Ralph 模式构建。它能够反复运行 AI 编码工具（Amp CLI 或 Claude Code），自动执行直到产品需求文档（PRD）中的所有用户故事全部完成。每次迭代都会生成一个全新的 AI 实例，拥有干净的上下文窗口，而记忆通过 git 历史记录、`progress.txt` 和 `prd.json` 三个文件持久化保存。

Ralph 的核心设计哲学是"小步快跑"——不追求单次完美的长上下文处理，而是将复杂任务拆分为小的用户故事，每次迭代只处理一个，通过多次干净上下文的迭代来累积完成复杂项目。这种方式有效规避了大语言模型上下文窗口溢出导致代码质量下降的问题。

项目同时支持 Amp CLI 和 Claude Code 作为底层 AI 编码引擎，并提供 Skill 系统（PRD 生成 + JSON 转换）实现从需求到代码的全链路自动化。

## 3. 核心功能

- **自主循环执行**：持续运行 AI 编码实例，自动按优先级完成 PRD 中的用户故事。当所有故事的 `passes` 状态为 `true` 时，Ralph 输出 `<promise>COMPLETE</promise>` 信号并退出循环。
- **每次迭代全新上下文**：每个迭代生成新的 AI 实例（Amp 或 Claude Code），彻底避免上下文窗口溢出问题。迭代间的记忆仅通过三个文件维持：git 历史、`progress.txt` 和 `prd.json`。
- **PRD 驱动开发**：从自然语言的产品需求自动生成结构化的 Markdown PRD，再转换为 JSON 任务列表（prd.json），每个用户故事包含 id、title、priority、passes 等字段。
- **进度持久化**：通过 git 历史（代码变更）、`progress.txt`（经验教训）和 `prd.json`（任务完成状态）三个维度维持跨迭代的完整记忆。
- **自动质量检查**：每次迭代自动运行类型检查（typecheck）和测试（tests），全部通过后才提交代码，确保代码质量不会跨迭代累积退化。
- **AGENTS.md 自动更新**：每个迭代后自动更新 `AGENTS.md` 文件，记录发现的模式、注意事项和代码约定，让后续迭代和人类开发者都受益。
- **双工具支持**：同时支持 Amp CLI（默认）和 Claude Code 作为底层 AI 编码引擎，通过 `--tool amp` 或 `--tool claude` 参数切换。
- **自动归档**：切换到不同功能分支（不同 `branchName`）时，自动将之前运行的配置归档到 `archive/YYYY-MM-DD-feature-name/` 目录。
- **PRD Skill 和 Ralph Skill**：提供两个独立的 Skill 组件，分别用于生成 PRD 和将 PRD 转换为 JSON 格式，支持 Amp Skills 和 Claude Code Skills 两种安装方式。
- **Claude Code 插件市场**：通过 `/plugin marketplace add snarktank/ralph` 安装，提供 `/prd` 和 `/ralph` 两个命令。
- **浏览器验证**：前端故事可在验收标准中包含"Verify in browser using dev-browser skill"，Ralph 会自动使用浏览器技能验证 UI 变更。
- **交互式流程图**：项目内置 `flowchart/` 目录，提供 Ralph 工作流程的可视化交互展示。

## 4. 技术栈

- **核心脚本**：Bash（`ralph.sh`，整个循环的驱动脚本）
- **AI 编码工具**：
  - Amp CLI（默认引擎）
  - Claude Code（`npm install -g @anthropic-ai/claude-code`）
- **任务格式**：JSON（`prd.json`，包含用户故事列表及完成状态）
- **进度记录**：纯文本（`progress.txt`，追加式写入）
- **辅助工具**：
  - `jq`（JSON 解析和处理，macOS 可通过 `brew install jq` 安装）
  - `git`（版本控制、分支管理、变更记忆载体）
- **Prompt 模板**：
  - `prompt.md`（Amp 的提示词模板）
  - `CLAUDE.md`（Claude Code 的提示词模板）
- **Skill 系统**：
  - `skills/prd/`（PRD 生成技能）
  - `skills/ralph/`（PRD 转 JSON 技能）
  - 兼容 Amp Skills 和 Claude Code Skills
- **Claude Code 插件**：`.claude-plugin/` 目录（插件市场清单）
- **可视化**：`flowchart/` 目录（基于 npm + Web 的交互式流程图）
- **版本管理**：git，功能分支由 PRD 中的 `branchName` 字段决定

## 5. 项目亮点

- **解决 LLM 上下文溢出核心痛点**：大任务是 LLM 编码的主要挑战——上下文窗口耗尽后代码质量急剧下降。Ralph 通过"每次迭代一个故事 + 全新上下文"的策略，从根本上解决了这一问题。
- **反馈循环保障质量**：强制要求类型检查和测试全部通过才提交，确保代码质量不会随迭代次数增加而退化。项目明确指出："Ralph only works if there are feedback loops"。
- **AGENTS.md 知识沉淀机制**：这是 Ralph 区别于其他 AI Agent 工具的关键设计。每次迭代后自动更新 `AGENTS.md`，记录发现的模式（"this codebase uses X for Y"）、陷阱（"do not forget to update Z when changing W"）和有用上下文（"the settings panel is in component X"），让后续迭代和人类开发者持续受益。
- **极简依赖设计**：只需 Bash、jq 和一个 AI 编码工具即可运行，无需额外框架或运行时环境。
- **全链路自动化**：从自然语言需求 -> PRD 文档 -> JSON 任务 -> 自主编码执行 -> 质量验证 -> 提交，形成完整的自动化闭环。
- **任务粒度指导**：项目提供了清晰的任务粒度指南，帮助用户区分"合适大小的故事"（添加数据库列和迁移、添加 UI 组件、更新服务器逻辑）和"过大的任务"（构建整个仪表盘、添加认证、重构 API）。

### 工作流程详解：PRD -> JSON -> 迭代循环

**第一步：创建 PRD（产品需求文档）**
```
Load the prd skill and create a PRD for [功能描述]
```
AI 会提出澄清问题，最终将输出保存到 `tasks/prd-[feature-name].md`。

**第二步：将 PRD 转换为 Ralph JSON 格式**
```
Load the ralph skill and convert tasks/prd-[feature-name].md to prd.json
```
生成 `prd.json` 文件，包含结构化的用户故事列表，每个故事带有 id、title、priority、passes 等字段。

**第三步：运行 Ralph 循环**
```bash
# 使用 Amp（默认）
./scripts/ralph/ralph.sh [max_iterations]

# 使用 Claude Code
./scripts/ralph/ralph.sh --tool claude [max_iterations]
```
默认最大迭代次数为 10 次。Ralph 在每次迭代中：
1. 根据 PRD 的 `branchName` 创建功能分支
2. 选取优先级最高且 `passes: false` 的故事
3. 实现该单个故事
4. 运行质量检查（类型检查、测试）
5. 检查通过则提交代码
6. 更新 `prd.json` 将故事标记为 `passes: true`
7. 将经验教训追加到 `progress.txt`
8. 重复直到所有故事完成或达到最大迭代次数

## 6. 应用场景

- **功能开发自动化**：将完整的产品需求拆分为小的用户故事，让 AI 自主逐个实现。适合新功能从零到一的开发流程。
- **代码重构**：将大型重构任务拆分为安全的增量步骤自动执行，每步都有测试保障。
- **测试覆盖补充**：自动为代码库中的模块逐个添加测试，可按模块粒度生成 PRD。
- **技术债务清理**：按照优先级自动处理技术债务清单，每次处理一个债务项。
- **多模块项目开发**：在大项目中按模块逐步推进，每次迭代专注一个模块的变更。
- **前端 UI 开发**：结合 dev-browser 技能自动验证浏览器中的 UI 变更效果。

## 7. Star 数据

- 总 Star 数：15,938
- Fork 数：1,589
- 今日增长：+463

## 8. 总结

Ralph 代表了一种务实的 AI 自主编码方法论。它不追求单次完美的长上下文处理，而是通过"小步快跑"的策略，用多次干净上下文的迭代来累积完成复杂任务。这种设计哲学既避免了 LLM 上下文窗口的限制，又通过质量检查和 AGENTS.md 机制保证了代码质量。

项目的安装和使用门槛极低：三种安装方式（项目内复制、全局 Skills 安装、Claude Code 插件市场），核心依赖仅需 Bash 和 jq。AGENTS.md 的自动更新机制是整个设计中最具价值的创新——它不仅服务于 AI 的后续迭代，也为人类开发者提供了持续积累的项目知识库。

对于已经在使用 Amp 或 Claude Code 但希望进一步提升自动化程度的开发者，Ralph 提供了一个优雅且低风险的解决方案。项目的关键前提是：必须有类型检查和测试作为反馈循环，否则 Ralph 的质量保障机制将无法发挥作用。

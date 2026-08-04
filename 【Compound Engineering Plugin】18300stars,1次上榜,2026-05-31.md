# Compound Engineering Plugin 项目分析

## 项目名称

**Compound Engineering Plugin** — AI 原生复合工程哲学插件，让每次工程工作都比上一次更轻松

- **GitHub**: [EveryInc/compound-engineering-plugin](https://github.com/EveryInc/compound-engineering-plugin)
- **许可证**: MIT

---

## 项目概述

Compound Engineering Plugin 是由 Every 公司开发的一款官方插件，旨在将「复合工程」（Compound Engineering）哲学注入 AI 编码代理中。其核心理念源自 Every 团队在构建 AI 首席参谋产品 Cora 的过程中积累的经验——每次工程单元的产出应当使后续工作变得更容易，而非更困难。该插件通过结构化的规划、审查和知识沉淀机制，打破了传统 AI 辅助编码中「提示→编码→交付→遗忘」的事务性循环。

该插件提供超过 50 个专业化子代理和 38 个斜杠命令，覆盖从策略制定、需求头脑风暴、代码规划到代码审查、调试、知识复合等完整的工程工作流。它支持 Claude Code、OpenAI Codex、Cursor、GitHub Copilot、Gemini、Qwen Code、Windsurf、Kiro 等 10 余种主流 AI 编码工具，实现了跨平台统一的工程规范和协作标准。

复合工程方法论强调将 80% 的精力投入在规划和审查阶段，仅 20% 用于实际编码执行。通过持续捕获每次编码会话中的经验教训并反馈到系统中，团队的知识和 AI 代理的能力得以不断累积和提升。这种「学习循环」使得代码库不会随时间增长而变得难以维护，反而会随着迭代变得更加清晰和高效。

---

## 核心功能

| 命令 | 描述 |
|------|------|
| /ce-strategy | 定义产品目标、方法和关键指标，建立 STRATEGY.md 作为项目北极星 |
| /ce-ideate | 生成、评估和路由创意想法，从发散思维到收敛决策 |
| /ce-brainstorm | 结构化头脑风暴，生成功能需求并支持概念图输出 |
| /ce-plan | 基于契约驱动的详细开发计划，自动综合需求并内联到 SKILL.md |
| /ce-code-review | 多代理并行代码审查，含置信度门控、去重和主题分组 |
| /ce-doc-review | 文档、架构和产品计划的一致性与可行性审查 |
| /ce-work | 执行计划中的工作项，支持自动修复和深度选择器 |
| /ce-debug | 系统化调试流程，精准定位和修复问题 |
| /ce-compound | 捕获会话学习成果并沉淀为结构化知识，供未来会话复用 |
| /ce-compound-refresh | 刷新和更新已沉淀的知识库，确保信息时效性 |
| /ce-commit-push-pr | 自动创建特性分支、生成含核心原则的 PR 描述 |
| /ce-product-pulse | 生成产品使用和性能报告，辅助策略迭代 |
| /ce-sessions | AI 代理会话发现与解析，跨会话知识管理 |
| /ce-setup | 一站式环境诊断、工具安装和项目配置 |
| /lfg | 全自动工程工作流，一键启动完整的复合工程循环 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | TypeScript |
| 插件格式 | SKILL.md（Markdown 约定） |
| 代理系统 | 50+ 专业化子代理（Reviewer、Strategist、Architect 等） |
| 斜杠命令 | 38+ 个结构化工作流命令 |
| 支持平台 | Claude Code、Codex、Cursor、Copilot、Gemini、Qwen、Windsurf、Droid、OpenCode、Pi、Kiro |
| CLI 工具 | @every-env/compound-plugin（bunx 安装适配器） |
| 知识管理 | STRATEGY.md、SKILL.md、CHANGELOG.md 结构化文档 |
| 输出格式 | Markdown、HTML（可选）、JSON（headless 模式） |
| 图像生成 | Google Gemini API 集成 |
| 许可证 | MIT License |

---

## 项目亮点

1. **跨平台统一标准**：同一套代理配置可无缝运行于 Claude Code、Codex、Cursor 等 10 余种 AI 编码工具，消除工具间碎片化
2. **复合学习循环**：每次编码会话的经验自动沉淀为结构化知识，AI 代理越用越聪明，代码库越迭代越清晰
3. **50+ 专业化代理**：涵盖代码审查、架构策略、API 契约、设计还原、数据完整性等维度的并行审查，确保代码质量
4. **活跃社区与快速迭代**：18.3k+ Stars、66+ 贡献者，每周持续更新，版本已迭代至 3.9.x

---

## 应用场景

1. **AI 原生产品全流程开发**：从产品策略定义、需求头脑风暴、开发规划到代码实现、审查、部署的端到端 AI 辅助工程
2. **多 AI 工具团队的统一工程规范**：跨 Claude Code、Cursor、Copilot 等不同 AI 工具的团队建立统一的工程工作流和质量标准
3. **大型代码库的知识管理**：通过持续的知识沉淀和代码简化审查，防止代码库随时间退化，实现正向累积效应
4. **代码审查自动化**：利用多代理并行审查机制替代传统人工 code review，提升审查效率并覆盖更多维度

---

## Star 数据

| 指标 | 数据 |
|------|------|
| 总 Stars | 18,300+ |
| 总 Forks | 1,400+ |
| 今日新增 | ~128（本周新增） |
| 许可证 | MIT |
| 主要语言 | TypeScript |

---

## 总结

Compound Engineering Plugin 是 Every 公司开源的 AI 编码工程哲学实践工具，以「让每次工程工作都比上一次更轻松」为核心理念，通过 50+ 专业化代理和 38+ 结构化命令覆盖了从策略到交付的完整软件开发生命周期。它打破了 AI 编码的事务性模式，建立了持续学习和知识复用的复合循环，支持 10 余种主流 AI 编码平台，以 MIT 许可证开源，已获得 18.3k+ Stars，成为 AI 辅助开发领域最具影响力的工作流插件之一。

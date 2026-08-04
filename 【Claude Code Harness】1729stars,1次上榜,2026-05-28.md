# Claude Code Harness 项目分析

## 项目名称

**Claude Code Harness** — 为 Claude Code 打造的规范化开发框架，通过「计划→执行→评审」循环实现高质量软件开发

- **GitHub**: [Chachamaru127/claude-code-harness](https://github.com/Chachamaru127/claude-code-harness)
- **许可证**: MIT

---

## 项目概述

Claude Code Harness 是一款专为 AI 编程助手 Claude Code 设计的「纪律性交付循环」（Disciplined Delivery Loop）工具，同时为 Codex 和 OpenCode 提供有界路径支持。项目创始团队指出——Claude Code 很强大，但原始的 Agent 工作容易漂移：计划停留在聊天中，测试变成可选项，评审来得太晚，发布证据靠记忆重建。

Harness 的核心价值在于将这种无序的 AI 辅助开发过程转化为一条**可重复、可审计的操作路径**。项目提供了规范的六阶段工作流：Investigate（调查）→ Plan（计划）→ Work（执行）→ Review（评审）→ PR（提交）→ Release（发布），覆盖完整开发周期。

项目以轻量级 Shell 脚本为核心，提供 macOS、Linux、Windows 的预编译二进制文件，30 秒即可完成安装。用户的核心职责不是手写计划，而是在执行继续之前批准或纠正 AI 生成的契约。

---

## 核心功能

| 命令/功能 | 说明 |
|---|---|
| `/harness-setup` | 初始化项目，安装指导文件、命令接口、钩子和检查项 |
| `/harness-plan` | 将用户意图转化为 `spec.md` 和 `Plans.md` 规范文档 |
| `/harness-work` | 执行已批准的任务或任务范围，包含验证环节 |
| `/harness-review` | 对实现结果进行独立评审 |
| `/harness-release` | 检查发布就绪状态 |
| `bin/harness doctor --migration-report` | 对现有配置进行迁移兼容性检查 |
| **Breezing** | 面向更大任务列表的团队级执行模式 |
| **Codex Companion Review** | 基于 Schema 的第二意见评审（用于 Codex） |
| **OpenCode Bootstrap** | 将 Harness 指导镜像到 OpenCode 中 |
| **harness-mem** | 项目级别的记忆与召回系统 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要编程语言** | Shell（Bash 脚本） |
| **配置文件** | YAML（配置）、JSON（Schema 定义） |
| **跨平台二进制** | macOS (amd64/arm64)、Linux (amd64)、Windows (amd64) |
| **兼容工具** | Claude Code、Codex CLI、OpenCode、Cursor、GitHub Copilot CLI |
| **文档体系** | Markdown（架构、证据、示例、入职指南等完整文档） |

---

## 项目亮点

### 30 秒极速安装
通过 `/harness-plan` 即可开始使用，上手门槛极低。

### 规范的六阶段工作流
覆盖从调查到发布的完整开发周期，确保每一步都有明确的输出和验证。

### 人类在环（Human-in-the-loop）
强调用户审批而非自动化替代，用户负责审批或纠正 AI 生成的契约。

### 多工具兼容
不局限于 Claude Code，还支持 Codex、OpenCode、Cursor、GitHub Copilot 等多种 AI 编程助手。

---

## 应用场景

### 个人开发者使用 Claude Code
需要结构化工作流避免 AI 编码漂移，提高代码质量和可审计性。

### 团队协同开发
通过 Breezing 模式协同处理大型任务列表，统一团队工作流。

### CI/CD 集成
利用 Review 和 Release 命令确保代码质量门槛，规范化发布流程。

### 多 Agent 工作流统一
在 Claude Code、Codex、OpenCode 等多个 AI 编程工具间统一工作流标准。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 1,729+ |
| **总 Forks** | 191+ |
| **今日新增 Stars** | ~50+ |
| **许可证** | MIT |
| **创建时间** | 2025 年 12 月 |
| **主要语言** | Shell |

---

## 总结

Claude Code Harness 是一个**AI 辅助开发纪律性工具**，1.7k+ Stars。它为 Claude Code 等 AI 编程助手提供规范的六阶段工作流（调查→计划→执行→评审→提交→发布），将无序的 AI 编码过程转化为可重复、可审计的操作路径。项目以轻量级 Shell 脚本为核心，30 秒安装，兼容多种 AI 编程工具，适合希望提升 AI 辅助开发质量的个人和团队使用。

---

*数据来源：GitHub 仓库 (Chachamaru127/claude-code-harness)，2026 年 5 月访问*

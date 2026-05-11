# React Doctor 项目分析

## 项目名称

**React Doctor** — AI 生成 React 代码的健康检测工具

- **GitHub**: [millionco/react-doctor](https://github.com/millionco/react-doctor)
- **许可证**: MIT

---

## 项目概述

React Doctor 是一个专为检测 AI 编码助手（如 Cursor、Copilot 等）生成的 React 代码质量问题而设计的 CLI 工具和 GitHub Action。它能扫描整个 React 代码库并输出 0-100 分的健康评分，附带可操作的诊断报告，帮助开发者捕获 AI Agent 写出的反模式、性能问题和安全漏洞。

React Doctor 的诞生源于一个日益普遍的问题：AI 编码助手虽然大幅提升了开发效率，但经常生成存在微妙 Bug 和反模式的 React 代码——不必要的 `useEffect`、不当的状态管理、可访问性违规、安全漏洞等。React Doctor 作为自动化的质量门禁，填补了 AI 生成代码与生产级质量之间的差距。

项目支持 Next.js、Vite、React Native 和 TanStack Start 等主流框架，提供 CLI、GitHub Action、Node.js API 和 ESLint/oxlint 插件等多种使用方式。其规则覆盖状态与副作用、性能、安全、可访问性、架构和死代码检测六大类别，并附带公共排行榜展示高分 React 代码库。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **健康评分（0-100）** | 一条命令扫描整个代码库，输出健康评分和可操作诊断（75+ 优秀，50-74 需改进，<50 危急） |
| **多框架支持** | 支持 Next.js、Vite、React Native、TanStack Start |
| **状态与副作用检测** | 捕获不必要的 useEffect、派生状态、链式状态更新、事件处理函数误用 |
| **性能分析** | 识别不必要的重渲染、缺失 memoization |
| **安全扫描** | 检测常见安全漏洞 |
| **可访问性检查** | 发现 a11y 违规 |
| **架构审查** | 高亮架构层面的问题 |
| **死代码检测** | 识别未使用的代码 |
| **框架特定规则** | Next.js（元数据缺失、Suspense 缺失等）、React Native（推荐 Reanimated/Pressable 等） |
| **GitHub Action** | CI/CD 集成，支持 PR 评论自动反馈 |
| **灵活配置** | react-doctor.config.json 支持规则静默、文件忽略、自定义规则 |
| **内联抑制** | 代码内抑制特定规则 |
| **公共排行榜** | 展示高分 React 代码库排名 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | TypeScript |
| **Lint 引擎** | oxlint（主要）、ESLint（辅助） |
| **包管理** | npm（npx 运行 CLI） |
| **CI 集成** | GitHub Actions |
| **项目结构** | Monorepo（packages/react-doctor/） |
| **配置格式** | JSON（react-doctor.config.json） |
| **NPM 包** | react-doctor |

---

## 项目亮点

### 精准定位 AI 代码问题
专门针对 AI 编码助手生成代码的常见问题设计，在 AI 辅助开发日益普及的当下具有极高的实用价值。

### 多种集成方式
CLI、GitHub Action、Node.js API、ESLint/oxlint 插件四种使用方式，覆盖本地开发、CI/CD 和 IDE 等多种场景。

### 框架深度适配
针对 Next.js、React Native、TanStack Start 等框架提供特定规则，而非泛泛的通用检查。

### 单一评分可视化
0-100 的健康评分让代码质量一目了然，配合公共排行榜增加社区参与度。

---

## 应用场景

### AI 编码质量门禁
在 CI/CD 流水线中集成 React Doctor，作为 AI 生成代码的自动质量门禁，防止有问题的代码合入主分支。

### 代码审查辅助
在 PR Review 中使用 React Doctor 自动检测问题，减轻人工审查负担。

### 代码库健康监控
定期扫描代码库获取健康评分，跟踪代码质量变化趋势。

### AI Agent 工作流集成
作为编码 Agent 的技能（如 ui-skills.com），在 Agent 完成代码编写后自动运行质量检查。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | ~7,700 |
| **总 Forks** | ~242 |
| **今日新增 Stars** | 312 |
| **许可证** | MIT |
| **主要语言** | TypeScript |

---

## 总结

React Doctor 是一个专为 AI 生成 React 代码设计的**健康检测工具**，7.7k Stars。它用 TypeScript 构建，基于 oxlint 引擎，通过 0-100 健康评分覆盖状态副作用、性能、安全、可访问性、架构六大类检查，支持 Next.js/React Native/TanStack Start 等主流框架。在 AI 辅助编码日益普及的今天，React Doctor 填补了 AI 生成代码与生产级质量之间的关键缺口。

---

*数据来源：GitHub 仓库 (millionco/react-doctor)、GitHub Marketplace（2026 年 5 月访问）*

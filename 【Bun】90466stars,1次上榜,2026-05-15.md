# Bun 项目分析

## 项目名称

**Bun** — 极速 JavaScript/TypeScript 全能工具链，Node.js 的直接替代品

- **GitHub**: [oven-sh/bun](https://github.com/oven-sh/bun)
- **许可证**: MIT（部分组件使用 LGPL-2）

---

## 项目概述

Bun 是一个集 JavaScript 运行时、打包器、测试运行器和包管理器于一体的全能工具链，由 Jarred Sumner 创建。项目以单个可执行文件（`bun`）的形式发布，旨在作为 Node.js 的**直接替代品**（drop-in replacement），在保持兼容性的同时大幅提升性能。

Bun 的核心是高性能 JavaScript 运行时，基于 Safari 的 **JavaScriptCore** 引擎（而非 Node.js 和 Deno 使用的 V8 引擎）。Bun 使用 Zig 语言编写，从底层优化了启动时间和内存使用，其内置工具（包管理器、测试运行器、打包器）均显著快于现有方案。

2025 年 12 月，Bun 被 **Anthropic** 收购，Bun 团队加入 Anthropic 以支持 Claude Code 和 Claude Agent SDK 的开发。截至 2026 年 5 月，Bun 最新版本为 v1.3.13，支持 Linux（x64 & arm64）、macOS（x64 & Apple Silicon）和 Windows（x64 & arm64）全平台。

---

## 核心功能

### 1. 极速 JavaScript 运行时
`bun run` 命令可直接执行 JavaScript 和 TypeScript 文件，启动速度和内存占用远优于 Node.js，兼容 Node.js API 生态。

### 2. 内置包管理器
提供 `bun install`、`bun add`、`bun remove`、`bun update` 等命令，兼容 package.json 和 npm 生态，安装速度比 npm/yarn/pnpm 快数倍。

### 3. 内置测试运行器
`bun test` 提供 Jest 兼容的测试框架，开箱即用，无需额外配置，测试执行速度极快。

### 4. 内置打包器
`Bun.build()` API 可将 JavaScript/TypeScript 项目打包为单个文件，适用于构建部署产物。

### 5. 脚本运行器
`bun run <script>` 执行 package.json 中定义的脚本，比 npm run 快约 30 倍。

### 6. 包执行器
`bunx <package>` 类似 npx，可直接运行 npm 包中的命令，无需全局安装。

### 7. Node.js 兼容性
持续运行 Node.js 测试套件以确保兼容性，支持 Node.js API、npm 包、node_modules 等。

### 8. 全平台支持
支持 Linux（x64/arm64）、macOS（x64/Apple Silicon）、Windows（x64/arm64），并提供 Docker 镜像。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Zig |
| **JavaScript 引擎** | JavaScriptCore（WebKit/Safari 引擎） |
| **运行时平台** | Linux / macOS / Windows |
| **API 兼容** | Node.js API |
| **包管理** | npm 兼容（package.json / node_modules） |
| **测试框架** | Jest 兼容 |
| **打包器** | 内置 Bun.build() |
| **容器化** | Docker（oven/bun） |
| **安装方式** | curl、Homebrew、PowerShell、npm |

---

## 项目亮点

### 极致性能
Bun 在启动时间、包安装、测试执行等各个方面都显著优于 Node.js 生态的现有工具。包安装速度比 npm 快约 30 倍，脚本执行快约 30 倍，测试运行快数倍。

### 单一可执行文件
所有功能（运行时、包管理、测试、打包）集成在一个 `bun` 二进制文件中，无需安装多个工具，极简部署。

### Anthropic 收购
2025 年 12 月被 Anthropic 收购后，Bun 成为 Claude Code 和 Claude Agent SDK 的底层运行时支持，获得更强的人力和资源投入。

### 持续迭代的 Canary 构建
每次提交到 main 分支都会自动发布 Canary 版本，社区可以即时测试最新功能和修复。

---

## 应用场景

### Node.js 项目加速迁移
现有 Node.js 项目可几乎零修改地切换到 Bun，获得更快的开发体验——更快的包安装、更快的测试运行、更快的脚本执行。

### 全栈 Web 开发
使用 Bun 的内置 HTTP 服务器、WebSocket 支持、文件 API 等构建高性能 Web 应用，单个工具覆盖开发全流程。

### CI/CD 流水线优化
在 CI/CD 中使用 Bun 替代 Node.js，可大幅减少依赖安装和测试运行时间，降低构建成本。

### 边缘计算和 Serverless
Bun 的快速启动和低内存占用使其非常适合边缘计算和 Serverless 场景，冷启动时间远低于 Node.js。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 90,466 |
| **总 Forks** | 4,496 |
| **今日新增 Stars** | 289 |
| **许可证** | MIT（含 LGPL-2 组件） |
| **主要语言** | Zig / Rust |
| **创建时间** | 2021 年 |
| **最新版本** | v1.3.13（2026 年 4 月） |

---

## 总结

Bun 是一个**全能 JavaScript/TypeScript 工具链**，90k+ Stars。它用 Zig 语言编写，基于 JavaScriptCore 引擎，将运行时、包管理器、测试运行器和打包器集成在单个二进制文件中，作为 Node.js 的直接替代品提供数倍的性能提升。2025 年底被 Anthropic 收购后，Bun 正在成为 Claude Code 等产品的核心基础设施，拥有强劲的发展势头。

---

*数据来源：GitHub 仓库 (oven-sh/bun)、Wikipedia（2026 年 5 月访问）*

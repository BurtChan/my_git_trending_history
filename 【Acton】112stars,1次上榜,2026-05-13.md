# Acton 项目分析

## 项目名称

**Acton** — TON 区块链智能合约一体化开发工具链

- **GitHub**: [ton-blockchain/acton](https://github.com/ton-blockchain/acton)
- **许可证**: Apache-2.0 / MIT 双许可证

---

## 项目概述

Acton 是由 TON 官方团队（ton-blockchain）打造的统一智能合约开发工具链，完全围绕 TON 的新一代智能合约语言 **Tolk** 构建。它将项目脚手架、编译构建、测试、调试、脚本编写、钱包管理、部署与验证等诸多功能整合为单一 CLI 工具，旨在为 TON 开发者提供端到端的开发体验。Acton 使用 Rust 编写，性能优异且以单文件无依赖可执行文件形式分发，支持 macOS（ARM64 / x86_64）和 Linux（x86_64 / ARM64）等主流平台。

Acton 不仅是面向人类开发者的工具，还特别优化了对 AI Agent 的友好性，内置技能描述和使用手册，使 AI 编程助手可以将其作为运行时来执行开发任务。它还支持从传统 FunC + Blueprint 项目到 Tolk + Acton 的完整迁移路径，帮助开发者平滑过渡到新一代开发范式。

项目创建于 2025 年 10 月 17 日，目前处于活跃开发阶段，已有 22 个开放 Issue，社区参与度持续增长。

---

## 核心功能

### 项目脚手架（Scaffolding）
一键创建 TON 智能合约项目，包含标准化项目结构和配置。

### 编译构建（Build）
集成 Tolk 编译器，直接在 CLI 中完成智能合约编译。

### 原生 Tolk 测试（Native Tests）
使用 Tolk 语言本身编写单元测试、事务流测试和跨合约交互测试，速度比 TypeScript + JS 沙盒快 50 倍。

### 调试器（Debugger）
精确定位异常（如 exit code 9），支持查看调用栈、局部变量、延迟字段等，适用于完全优化的生产合约，兼容所有主流 IDE。

### dApp 集成（TypeScript Wrapper 生成）
自动生成 TypeScript 包装器，支持 TON Connect + React 前端集成。

### 水龙头与部署（Faucet & Deployment）
内置测试网水龙头充值、钱包管理、合约部署与链上验证。

### 链上脚本（On-chain Scripting）
使用 Tolk 编写部署脚本和链上交互脚本。

### 代码覆盖率（Coverage Reports）
支持行级和分支级覆盖率追踪，可视化报告，可导出 LCOV 格式。

### 变异测试（Mutation Testing）
通过翻转运算符、值和分支来检测薄弱的测试用例。

### 分叉测试（Fork Testing）
基于真实主网状态运行测试，自动拉取已部署账户到本地模拟器。

### Gas 分析（Gas Profiling）
快照事务链 Gas 用量，对比基线，在部署前捕获费用回归。

### 模糊测试（Fuzz Testing）
支持参数化测试、自动生成输入、可复现种子。

### IDE 集成（LSP 支持）
内置 Linter 和 Formatter，支持 VS Code、JetBrains、Cursor、Zed 等 LSP 编辑器。

### CI/CD 集成
开箱即用的 GitHub Actions 和 GitLab CI 支持。

### FunC → Tolk 迁移工具（func2tolk）
端到端迁移现有 FunC 项目，包括合约和测试用例的转换。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Rust |
| **智能合约语言** | Tolk（TON 新一代合约语言） |
| **包管理 / 构建** | Cargo（Rust Workspace） |
| **编译器集成** | tolk-compiler |
| **链上模拟** | ton-emulator |
| **前端集成** | TypeScript（自动生成 Wrapper）、React、TON Connect |
| **CI/CD** | GitHub Actions、GitLab CI |
| **IDE 支持** | LSP（VS Code、JetBrains、Cursor、Zed） |
| **分发方式** | 单文件可执行文件、Docker 镜像 |
| **许可证** | Apache-2.0 / MIT 双许可 |

---

## 项目亮点

### 一站式开发工具链
将脚手架、编译、测试、调试、部署、验证等全流程整合为单一 CLI 工具，开发者无需在多个工具间切换，极大提升了开发效率。原生测试比传统 TypeScript 测试快 **50 倍**。

### AI Agent 友好设计
内置技能描述和使用手册，专为 AI 编程助手（如 Codex、Claude 等）优化。Acton 可以作为 AI Agent 的运行时，实现自动化智能合约开发和部署流程。

### 企业级测试深度
提供变异测试、分叉测试（基于真实主网状态）、Gas 分析与回归检测、模糊测试和代码覆盖率追踪等多维度质量保障手段，确保合约安全性和性能。

### 平滑迁移路径
提供从 FunC + Blueprint 到 Tolk + Acton 的端到端迁移工具，不仅转换合约代码，还将 TypeScript 测试转换为原生 Tolk 测试，帮助开发者无缝升级到新一代开发范式。

---

## 应用场景

### TON 智能合约全流程开发
从零创建 TON 链上项目，编写、测试、调试和部署智能合约，适用于 DeFi 协议、NFT 市场、DAO 治理等 TON 生态应用开发。

### dApp 前后端一体化开发
通过自动生成 TypeScript 包装器，配合 TON Connect 和 React，快速搭建去中心化应用的前后端完整方案。

### 合约安全审计与质量保障
利用变异测试、Gas 分析、分叉测试等高级测试功能，对已部署或即将部署的合约进行深度安全审计和性能优化。

### CI/CD 自动化流水线
在 GitHub Actions 或 GitLab CI 中集成 Acton，实现自动化构建、测试、覆盖率检查和合约部署，适合团队协作开发和持续交付场景。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | ~112 |
| **总 Forks** | ~19 |
| **开放 Issue** | 22 |
| **创建时间** | 2025-10-17 |
| **最近更新** | 2026-05-13 |
| **主要语言** | Rust |
| **许可证** | Apache-2.0 / MIT 双许可 |

---

## 总结

Acton 是 TON 官方团队推出的新一代智能合约开发工具链，以 Rust 编写、围绕 Tolk 语言构建，将项目创建、编译、测试、调试、部署、验证等全生命周期功能统一在单一 CLI 中。它不仅在性能上远超传统方案（原生测试速度提升 50 倍），还创新性地优化了 AI Agent 集成体验，并提供了企业级的测试深度（变异测试、分叉测试、Gas 分析等）。作为 TON 生态从 FunC 向 Tolk 过渡的关键基础设施，Acton 正在成为 TON 智能合约开发的事实标准工具链。

---

*数据来源：GitHub 仓库 (ton-blockchain/acton)，数据截至 2026 年 5 月 13 日*

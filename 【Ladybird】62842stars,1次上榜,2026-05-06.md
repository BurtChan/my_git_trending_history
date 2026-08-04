# Ladybird 项目分析

## 项目名称

**Ladybird** — 从零构建的真正独立网页浏览器

- **GitHub**: [LadybirdBrowser/ladybird](https://github.com/LadybirdBrowser/ladybird)
- **许可证**: BSD 2-Clause

---

## 项目概述

Ladybird 是一款真正独立的网页浏览器，采用基于 Web 标准的全新引擎从零构建。项目目前处于 pre-alpha（预发布）阶段，仅适合开发者使用。

Ladybird 最初源于 SerenityOS 操作系统内置浏览器，由创始人 Andreas Kling 创建。2024 年从 SerenityOS 独立，成立了 Ladybird Browser Initiative——一个美国 501(c)(3) 非营利组织，由 GitHub 联合创始人 Chris Wanstrath 捐赠 100 万美元启动。项目的核心使命是**打破当前浏览器市场由 Chromium（Google）垄断的局面，为互联网提供一个真正独立、不依赖广告驱动的开源浏览器引擎**。

项目包含完整的 HTML 解析器、CSS 引擎、JavaScript 引擎、布局引擎和图形渲染，采用多进程架构和沙盒隔离设计。2026 年 2 月，创始人使用 Claude Code 和 OpenAI Codex 将 LibJS 从 C++ 移植到 Rust，仅用两周时间完成，成为 AI 辅助大规模代码迁移的标志性案例。

---

## 核心功能

### 1. 完全独立的浏览器引擎
不使用任何其他浏览器引擎的代码——不是 Chromium 壳、不是 WebKit 移植、不是 Firefox 分支，所有组件均从零编写。

### 2. 多进程架构
包含主 UI 进程、多个 WebContent 渲染进程、ImageDecoder 图像解码进程、RequestServer 网络请求进程。

### 3. 沙盒隔离
每个标签页在独立的渲染进程中运行，与系统其余部分隔离，提升安全性。

### 4. 自研核心库
| 库名 | 功能 |
|------|------|
| **LibWeb** | Web 渲染引擎（HTML、DOM、CSS） |
| **LibJS** | JavaScript 引擎 |
| **LibWasm** | WebAssembly 支持 |
| **LibGfx** | 图形渲染（2D 绘图、字体、图像解码） |
| **LibCore** | 事件循环和操作系统抽象层 |
| **LibIPC** | 进程间通信 |
| **LibURL** | URL 解析 |
| **LibHTTP** | HTTP 协议实现 |
| **LibTLS** | TLS/SSL 支持 |
| **LibRegex** | 正则表达式 |

### 5. 跨平台支持
支持 Linux、macOS、Windows（WSL2）、多种 *Nix 系统，Android（实验性）。

### 6. 无用户变现
不接受搜索交易或用户数据变现，资金完全来自捐赠和赞助。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | C++（主力，逐步引入 Rust） |
| **新增语言** | Rust（2026 年 2 月宣布采用） |
| **测试/工具** | JavaScript |
| **GUI 框架** | Qt6（Linux）、AppKit（macOS） |
| **构建系统** | CMake |
| **编译器** | Clang/LLVM |
| **许可证** | BSD 2-Clause "Simplified" License |

---

## 项目亮点

### 互联网第四大独立浏览器引擎
当前全球浏览器引擎市场几乎被 Chromium（Blink）和 WebKit（Safari）垄断，Firefox（Gecko）市场份额不断缩小。Ladybird 是近二十年来第一个从零构建的全新浏览器引擎项目。

### AI 辅助 Rust 迁移的里程碑实践
2026 年 2 月，创始人 Andreas Kling 使用 Claude Code 和 OpenAI Codex 将 LibJS（约 25,000 行代码）从 C++ 移植到 Rust，仅用两周时间完成通常需要数月的手工移植，实现了逐字节完全一致的输出，52,898 个 test262 测试零回归。

### 强大的非营利支持体系
获得 Cloudflare（铂金级，10 万美元）、Shopify、FUTO、JetBrains、Human Rights Foundation、37signals 等 18 家赞助商支持，加上 GitHub 联合创始人的 100 万美元初始捐赠。

### 清晰的产品路线图
- **2026 年**：面向开发者的 Alpha 版本（Linux/macOS）
- **2027 年**：面向用户的 Beta 版本（可下载应用）
- **2028 年**：稳定版本（通用发布）

---

## 应用场景

### 打破浏览器垄断
为互联网生态提供独立于 Google Chromium 的第三选择，防止 Web 标准被单一厂商控制，维护 Web 开放性。

### 隐私优先浏览
无广告驱动、无用户数据变现、无搜索交易，适合对隐私和数字主权有高要求的用户和组织。

### 嵌入式 Web 渲染
独立引擎可被第三方应用集成使用，无需依赖 Chromium 或 WebKit。

### Web 标准研究/教育
完整从零实现的浏览器引擎是学习 Web 标准和浏览器工作原理的绝佳教材，已被多所高校用于教学。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 62,842+ |
| **总 Forks** | 2,990+ |
| **今日新增 Stars** | ~20-50 |
| **许可证** | BSD 2-Clause |
| **创建时间** | 2024 年 5 月 30 日 |
| **主要语言** | C++（逐步引入 Rust） |
| **全球排名** | GitHub #274 |

---

## 总结

Ladybird 是近二十年来第一个从零构建的全新浏览器引擎项目，62,800+ Stars。项目由 SerenityOS 独立而来，成立了美国 501(c)(3) 非营利组织运营，获得 GitHub 联合创始人 100 万美元启动资金和 18 家企业赞助。2026 年 2 月使用 Claude Code 完成 LibJS 从 C++ 到 Rust 的里程碑式迁移，成为 AI 辅助大规模代码迁移的标志性案例。项目计划 2026 年发布 Alpha、2027 年 Beta、2028 年稳定版，旨在打破 Chromium 垄断，维护 Web 开放生态。

---

*数据来源：GitHub 仓库 (LadybirdBrowser/ladybird)（2026 年 5 月 6 日访问）*

# Android Reverse Engineering Skill 项目分析

## 项目名称

**Android Reverse Engineering Skill** — Claude Code 的 Android 应用逆向工程插件，支持 APK 反编译与 HTTP API 提取

- **GitHub**: [SimoneAvogadro/android-reverse-engineering-skill](https://github.com/SimoneAvogadro/android-reverse-engineering-skill)
- **许可证**: Apache-2.0

---

## 项目概述

Android Reverse Engineering Skill 是一个专为 **Claude Code** 设计的技能插件，旨在让 AI 辅助完成 Android 应用的逆向工程工作。该项目由 Simone Avogadro 开发，核心能力是反编译 Android APK/XAPK/JAR/AAR 文件，并从中提取应用使用的 HTTP API 信息，包括 Retrofit 端点、OkHttp 调用、硬编码 URL 以及认证模式等。

项目的诞生源于开发者的实际需求——在逆向分析 Android 应用时（尤其是提取未公开的 API），传统方式需要手动操作 jadx、grep 搜索代码等繁琐步骤。通过将这一流程封装为 Claude Code 技能，用户只需一条 `/decompile` 命令或自然语言描述，AI 即可自动完成反编译、API 提取和文档生成。这意味着以往需要数周才能完成的逆向工程任务，现在可以缩短到一个周末搞定。

该工具底层集成了行业标准的反编译工具链（jadx + FernFlower），并通过精心设计的 Shell 脚本实现自动化流水线。从安装依赖、反编译 APK、到提取 API 调用模式，整个过程高度自动化，非常适合安全研究人员、API 开发者和逆向工程爱好者使用。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **APK/XAPK/JAR/AAR 反编译** | 支持 Android 主流包格式的反编译，基于 jadx + FernFlower 引擎 |
| **HTTP API 提取** | 自动识别并提取 Retrofit 端点、OkHttp 调用、硬编码 URL 和认证模式 |
| **斜杠命令调用** | 通过 `/decompile path/to/app.apk` 一键触发完整反编译流程 |
| **自然语言激活** | 支持用自然语言描述需求，Claude Code 自动识别并调用技能 |
| **依赖自动管理** | 提供 `check-deps.sh` 和 `install-deps.sh` 自动检测和安装所需工具 |
| **调用流程分析** | 通过 `api-extraction-patterns.md` 和 `call-flow-analysis.md` 参考，精确提取 API 调用链 |
| **文档生成** | 反编译后自动生成可读的 API 文档，方便理解应用的网络通信逻辑 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Shell Script |
| **反编译引擎** | jadx（DEX → Java）、FernFlower（Java 字节码反编译） |
| **运行平台** | Claude Code 技能框架 |
| **安装方式** | Claude Code Plugin Marketplace / 本地克隆 |
| **许可证** | Apache-2.0 |

---

## 项目亮点

### AI + 逆向工程的创新结合
将 AI 辅助引入 Android 逆向工程领域，利用 Claude Code 的代码理解能力自动分析反编译后的代码，显著降低逆向工程的技术门槛。社区反馈表明，Claude Code 在 APK 逆向工程方面"令人惊叹地出色"。

### 开箱即用的完整工具链
从依赖检测（`check-deps.sh`）到安装（`install-deps.sh`）、反编译（`decompile.sh`）和 API 提取（`find-api-calls.sh`），提供完整的自动化流水线，用户无需手动配置任何工具。

### 精准的 API 提取能力
不仅能反编译代码，还能智能识别 Retrofit 注解、OkHttp 构建器模式、硬编码 URL 等多种 API 定义方式，并提取完整的端点路径、请求方法和认证信息，生成结构化的 API 文档。

### 双模式交互设计
同时支持精确的斜杠命令（`/decompile`）和灵活的自然语言描述两种调用方式，满足不同使用习惯的用户需求。

---

## 应用场景

### 安全研究与漏洞分析
安全研究人员可以使用该工具快速反编译目标 Android 应用，提取其 API 端点和认证机制，分析潜在的安全漏洞。

### 第三方 API 集成开发
开发者需要对接没有公开 API 文档的服务时，可通过反编译其官方 Android 应用提取 API 信息，实现非官方客户端或网关开发。

### 应用行为审计
企业安全团队可以审计员工使用的第三方应用，了解其网络通信行为和数据传输模式，评估数据泄露风险。

### 逆向工程学习
对 Android 逆向工程感兴趣的学习者可以借助 AI 辅助理解反编译代码，加速学习曲线，从实践中掌握逆向分析技术。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 2,070+ |
| **总 Forks** | 236 |
| **今日新增 Stars** | ~200+（GitHub Trending 上榜） |
| **许可证** | Apache-2.0 |
| **创建时间** | 2026 年 2 月 |
| **主要语言** | Shell |

---

## 总结

Android Reverse Engineering Skill 是一个将 **AI 能力引入 Android 逆向工程** 的创新项目，2,070+ Stars。它作为 Claude Code 的技能插件，基于 jadx 和 FernFlower 反编译引擎，实现了 APK/XAPK/JAR/AAR 文件的一键反编译和 HTTP API 自动提取。项目提供了完整的自动化工具链（从依赖安装到 API 文档生成），支持斜杠命令和自然语言两种调用方式，将传统逆向工程从数周缩短到一个周末的工作量，特别适合安全研究人员、API 开发者和逆向工程学习者使用。

---

*数据来源：GitHub 仓库 (SimoneAvogadro/android-reverse-engineering-skill)、Reddit r/ClaudeAI、XDA Forums（2026 年 4 月访问）*

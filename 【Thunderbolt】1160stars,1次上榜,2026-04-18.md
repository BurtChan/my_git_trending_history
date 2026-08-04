# Thunderbolt 项目分析

## 项目名称

**Thunderbolt** — 由 Thunderbird 团队打造的开源、可自主托管的 AI 客户端

- **GitHub**: [thunderbird/thunderbolt](https://github.com/thunderbird/thunderbolt)
- **官网**: https://thunderbolt.io
- **许可证**: Mozilla Public License 2.0 (MPL-2.0)

---

## 项目概述

Thunderbolt 是由 MZLA Technologies Corporation（Mozilla 基金会子公司，即 Thunderbird 邮件客户端背后的同一组织）开发的一款**开源、可自主托管的 AI 客户端**。项目核心理念是让用户掌控自己的 AI 体验：选择自己的模型，拥有自己的数据，消除供应商锁定。

Thunderbolt 与 Thunderbird 邮件客户端是**独立的产品**，虽然同属 MZLA Technologies，但并非 Thunderbird 现有产品线的一部分。该项目资金来源于 Mozilla 的资助，体现了 Mozilla 一贯的"互联网为公众利益服务"的理念在 AI 时代的延续。

项目基于 deepset 的 **Haystack** 开源 AI 框架构建，采用 **TypeScript + Rust + Tauri** 技术栈，实现了跨 Web、桌面和移动端六大平台（macOS、Linux、Windows、Android、iOS）的全面覆盖。Thunderbolt 支持接入前沿模型（OpenAI、Anthropic、Google 等）、本地模型（Ollama、llama.cpp）和自托管模型，用户可自由选择和切换，真正实现了零供应商锁定。

---

## 核心功能

| 功能 | 状态 |
|------|------|
| **聊天模式** | ✅ 已完成 |
| **搜索模式** | ✅ 已完成 |
| **聊天小组件** | ✅ 已完成 |
| **自定义模型/提供商** | ✅ 已完成 |
| **Ollama 兼容** | ✅ 已完成 |
| **Google 集成** | ✅ 已完成 |
| **Microsoft 集成** | ✅ 已完成 |
| **OIDC 身份认证** | ✅ 已完成 |
| **研究模式** | 🔍 预览版 |
| **MCP 支持** | 🔍 预览版 |
| **可选端到端加密 (E2EE)** | 🔍 预览版 |
| **跨设备云同步** | 🔍 预览版 |
| **ACP 协议** | 🔧 开发中 |
| **Agent 记忆与技能** | 📋 计划中 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主语言** | TypeScript + Rust |
| **前端框架** | React + Vite |
| **桌面端框架** | Tauri（Rust 跨平台桌面应用框架）|
| **运行时/包管理** | Bun |
| **AI 框架** | Haystack（deepset 开源 AI 框架）|
| **后端部署** | Docker Compose / Kubernetes |
| **本地推理** | Ollama、llama.cpp |

---

## 项目亮点

1. **数据主权与隐私保护**：完全自托管部署，数据不离开组织基础设施，支持可选的端到端加密（E2EE），正在接受安全审计
2. **零供应商锁定**：支持前沿模型、本地模型、自托管模型，用户可自由选择和切换 AI 提供商
3. **全平台覆盖**：一套代码覆盖 Web、桌面（macOS/Linux/Windows）和移动端（Android/iOS）六大平台
4. **Thunderbird 血统**：由 Mozilla 旗下 MZLA Technologies 开发，继承了 Thunderbird 品牌的可信度和开源精神

---

## 应用场景

1. **企业内部 AI 平台**：组织可在自有基础设施上部署 Thunderbolt，为员工提供 AI 工具，确保敏感数据不外泄
2. **合规敏感行业**：金融、医疗、政府等需要严格数据管控的行业，通过自托管满足合规要求
3. **多模型统一管理**：在一个界面中管理多种 AI 模型（OpenAI、Anthropic、本地 Ollama 等）的团队
4. **个人/小型团队私有 AI 助手**：技术爱好者在本地运行 AI 模型并通过统一客户端交互

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | ~1,160 |
| **Forks** | 58 |
| **今日新增** | 📈 Trending |
| **许可证** | MPL-2.0 |
| **主要语言** | TypeScript / Rust |

---

## 总结

Thunderbolt 是 Thunderbird 团队从邮件客户端向 AI 客户端领域的重要延伸，以"用户掌控 AI"为核心理念，打造了一个开源、可自托管、跨平台的 AI 客户端。项目凭借 Mozilla 的品牌背书、Haystack 的成熟 AI 框架基础和 Tauri 的跨平台能力，正在为追求数据主权和隐私保护的用户提供 TeamViewer 级别的 AI 体验。虽然项目仍处于早期阶段，但其清晰的定位和强大的背景使其值得持续关注。

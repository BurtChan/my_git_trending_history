# FluidVoice 项目分析

## 项目名称
**FluidVoice** — macOS 平台上最快的离线 AI 语音转文字听写应用
- **GitHub**: [altic-dev/FluidVoice](https://github.com/altic-dev/FluidVoice)
- **许可证**: GPL-3.0

---

## 项目概述

FluidVoice 是一款专为 macOS 设计的全开源、完全本地运行的语音转文字听写应用，由 Altic 团队开发。该项目于 2025 年 9 月创建，以"永不收费、永远开源"为理念，致力于让每一位 Mac 用户都能享受高速、精准、隐私安全的语音输入体验。与需要订阅付费的云端语音转写服务不同，FluidVoice 将所有语音模型部署在用户本地设备上，确保语音数据不会上传至任何云端服务器。

该项目支持多种业界领先的语音识别模型，包括 NVIDIA Nemotron Speech 3.5、Parakeet TDT v3、Whisper、Cohere Transcribe 以及 Apple Speech 原生模型，覆盖约 40 种语言。FluidVoice 是首批支持 Nemotron Speech 3.5 流式转录能力的 macOS 听写应用之一，将 NVIDIA 最新语音模型无缝集成到原生 Apple Silicon 工作流中。当前版本为 1.6.0，已上架 Homebrew，安装便捷。

FluidVoice 不仅仅是一款听写工具，它还提供"命令模式"（Command Mode）允许用户通过语音控制 Mac 执行各种操作，以及"写作模式"（Write Mode）可在任何应用的文本框中直接语音输入或改写内容。该应用深度集成了 macOS 原生体验，支持全局快捷键触发、实时预览悬浮窗和自动输入到当前应用，是目前 macOS 生态中最具竞争力的开源语音输入方案之一。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 离线语音转文字 | 完全本地运行，语音数据不上传云端，保障用户隐私安全 |
| 多模型支持 | 支持 Nemotron Speech 3.5、Parakeet TDT v3、Whisper、Cohere Transcribe、Apple Speech 等多种模型 |
| 流式实时转录 | 基于 Nemotron Speech 3.5 Ultra Fast Low Latency 模型，支持低延迟流式语音转录 |
| 命令模式（Command Mode） | 通过语音控制 Mac 执行各种操作，实现免提电脑操控 |
| 写作模式（Write Mode） | 在任何应用（Notes、Slack、Cursor、Gmail 等）的文本框中直接语音输入文字 |
| AI 文本增强 | 可接入 OpenAI、Groq 等 AI 模型，对转录文本进行润色和改写 |
| 多语言支持 | 支持约 40 种语言的自动检测与转录，覆盖主流语种 |
| 历史记录 | 记录所有语音转录历史，方便回溯和复用 |
| 全局快捷键 | 通过快捷键随时启动语音输入，无缝融入现有工作流 |
| 实时预览 | 语音转录过程中显示悬浮预览窗口，转录完成自动输入当前应用 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 编程语言 | Swift |
| 目标平台 | macOS（Apple Silicon 芯片） |
| 系统要求 | macOS 14.0 及以上 |
| 语音模型引擎 | FluidAudio（自研本地转录引擎） |
| ASR 模型 | NVIDIA Nemotron Speech 3.5、Parakeet TDT v3、Whisper、Cohere Transcribe |
| 系统语音 | Apple Speech（macOS 原生语音识别） |
| AI 增强 | OpenAI、Groq 等云端 AI 模型（可选） |
| 安全存储 | macOS Keychain（存储 AI 密钥） |
| 分发渠道 | Homebrew Cask（`brew install --cask fluidvoice`） |
| 开源许可证 | GPL-3.0（2026 年 2 月从 Apache-2.0 更改） |

---

## 项目亮点

### 🏆 首批支持 NVIDIA Nemotron Speech 3.5 的 macOS 应用

FluidVoice 实现了对 NVIDIA 最新 Nemotron Speech 3.5 模型的 Day-0 支持，成为首批将该模型集成到 macOS 原生工作流中的听写应用。该模型具备流式转录能力，支持约 40 种语言，延迟可控制在 80ms 至 1 秒之间，为用户带来近乎实时的语音输入体验。这一特性使 FluidVoice 在同类开源项目中脱颖而出。

### 🔒 完全本地运行，隐私零泄露

FluidVoice 采用本地优先架构，所有语音模型均在用户设备上运行，语音数据绝不会上传至任何云端服务器。对于注重隐私保护的用户来说，这是一个极具吸引力的特性。可选的 AI 增强功能（如文本润色）使用的 API 密钥也通过 macOS Keychain 安全存储，确保信息安全。

### 🎯 双模式设计：听写 + 电脑控制

FluidVoice 创新性地提供了"写作模式"和"命令模式"两种工作模式。写作模式专注于语音输入文字，适用于文档编辑、消息发送等场景；命令模式则允许用户通过语音执行 macOS 操作，实现免提电脑控制。这种双模式设计使其不仅是一款听写工具，更是一个语音驱动的 Mac 操作助手。

### 📦 开箱即用的 Homebrew 安装体验

FluidVoice 已上架 Homebrew Cask，用户只需一条命令 `brew install --cask fluidvoice` 即可完成安装。搭配 Parakeet TDT v3 默认模型（约 500MB），首次使用即可获得快速的语音转录体验，无需复杂配置。项目完全开源且永久免费，社区活跃度高，更新迭代迅速。

---

## 应用场景

### 📝 高效文档写作与编辑

对于经常需要撰写文档、邮件、报告的用户，FluidVoice 可以在任何文本输入框（包括 Notes、Pages、Google Docs、Cursor 编辑器等）中直接语音输入文字，大幅提升输入效率。据官方估算，以每天输入 500 字计算，大约可节省 9 分钟，同时保持心流状态。

### 💻 编程开发辅助

开发者在编写代码时可以使用 FluidVoice 进行注释撰写、代码文档编写，甚至通过 AI 增强功能对转录内容进行格式化和润色。在 Cursor、VS Code 等代码编辑器中直接语音输入，双手可以继续操作键盘和鼠标，显著提升开发效率。

### 🌍 多语言办公场景

支持约 40 种语言的自动检测和转录，FluidVoice 非常适合需要在不同语言间切换的国际化办公场景。无论是中文、英文、日文还是欧洲语言，都能自动识别并准确转录，消除语言障碍。

### ♿ 无障碍与免提操作

对于有打字困难的用户或需要免提操作的场景（如厨房烹饪、驾车等），FluidVoice 的命令模式允许通过语音控制 Mac 执行各种操作，写作模式则能替代键盘输入，为无障碍使用提供强大支持。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Star 数 | 9,683 |
| 总 Fork 数 | 653 |
| 今日新增 Star | 83 |
| 主要编程语言 | Swift |
| 创建时间 | 2025-09-21 |
| 开源 issues | 74 |
| 当前版本 | 1.6.0 |
| 许可证 | GPL-3.0 |
| 项目主页 | https://altic.dev/fluid |

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 13 日（再次登上 Trending）

**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：FluidVoice 时隔一个多月再次登上 GitHub Trending，Star 数从 6 月末的 3,657 爆发式增长至 9,683（+6,026），Forks 从 234 增至 653。这款 macOS 离线语音转文字应用凭借完全本地运行、无隐私上传的架构持续吸粉，对 NVIDIA Nemotron Speech 等前沿语音模型的快速跟进与双模式设计（写作 + 命令）获得大量好评，社区口碑驱动了这轮显著增长。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 3,657 | 9,683 | +6,026 |
| 总 Forks | 234 | 653 | +419 |

**核心变化概要**：
- Star 数较 6 月末增长逾 160%，突破 9.6K
- 离线隐私语音识别的差异化定位持续获得认可
- Forks 近 3 倍增长，社区参与度显著提升


---

## 总结

FluidVoice 是一款在 macOS 生态中极具竞争力的开源离线语音转文字应用，凭借其完全本地运行的隐私保护架构、对 NVIDIA Nemotron Speech 3.5 等前沿模型的快速集成支持、创新的双模式设计（写作 + 命令），以及开箱即用的 Homebrew 安装体验，在短短 9 个月内获得了超过 3,600 颗 Star 和近 500 颗单日 Star 增长，展现了强大的社区认可度。该项目以"永远免费、永远开源"为承诺，持续快速迭代，已从单纯的听写工具进化为集语音输入、电脑控制、AI 文本增强于一体的综合语音助手，是 macOS 用户值得高度关注的开源项目。

---

*数据来源：GitHub 仓库 (altic-dev/FluidVoice)，2026 年 6 月访问*
*首次分析：见文件头部 | 最近更新：2026 年 8 月 13 日*

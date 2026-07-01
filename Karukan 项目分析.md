# Karukan 项目分析

## 项目名称
**Karukan** — 基于 llama.cpp 神经网络的跨平台日语输入法系统

- **GitHub**: [togatoga/karukan](https://github.com/togatoga/karukan)
- **许可证**: MIT OR Apache-2.0（双重许可，第三方数据使用 BSD 3-Clause）

---

## 项目概述

Karukan 是一个面向 Linux 和 macOS 平台的现代日语输入法系统（IME），其核心亮点在于采用基于 **llama.cpp** 的神经网络引擎实现假名到汉字（Kana-Kanji）的智能转换。该项目由日本开发者 Hitoshi Togasaki（@togatoga）于 2024 年 8 月创建，以 Rust 语言为主要开发语言，使用 Cargo 工作区管理多个子 crate，并辅以 Swift 开发 macOS 原生前端。项目名称「かるかん」源自日语词汇，体现了轻量、灵活的设计理念。

与传统日语输入法依赖规则匹配和统计模型的方案不同，Karukan 采用了 **GPT-2 架构的神经网络模型**（项目代号 jinen）进行假名汉字转换，训练部分在独立的 Python 项目 `karukan-jinen` 中完成，输出 GGUF 格式的量化模型文件供 karukan-engine 加载推理。首次启动时，系统会自动从 Hugging Face 下载预训练模型，后续使用本地缓存，无需重复下载。这种设计将前沿的 NLP 技术引入了日常输入法场景，代表了日语 IME 领域的一次技术革新。

项目采用模块化的 monorepo 架构，分为五个核心模块：`karukan-engine`（核心引擎库）、`karukan-im`（共享 IME 引擎）、`karukan-fcitx5`（Linux fcitx5 前端）、`karukan-macos`（macOS Swift 前端）和 `karukan-cli`（命令行工具集）。这种分层设计使得核心转换逻辑与平台 UI 完全解耦，便于跨平台复用和独立迭代。项目还内置了基于 **Sudachi** 形态素分析器的系统词典支持，以及学习缓存机制（基于使用频率的 TSV 记录），能够随使用不断优化转换精度。

---

## 核心功能

### 神经网络假名汉字转换
Karukan 的核心能力是利用 GPT-2 神经网络模型进行假名到汉字的转换，通过 llama.cpp 在本地高效推理。支持两种转换策略：默认策略同时使用轻量和标准模型以获得最佳效果，`light` 策略仅使用轻量模型以降低内存占用，适合低配 PC。转换过程采用 beam search 算法，配合分块（chunk）机制和左上下文（left context）理解，能够准确处理长句和歧义场景。

### 实时预编辑转换（Live Conversion）
支持实时转换模式，用户输入假名的同时系统即时显示汉字转换结果，无需按空格键触发转换。该功能通过 `Ctrl+Shift+L` 快捷键切换，默认开启。实时转换大幅提升了输入流畅度，使体验接近智能手机上的日语输入。

### Emoji 与颜文字快捷输入
内置丰富的 Emoji 和颜文字快捷触发支持。用户可通过 `:trigger`、`:smile`、`:halo` 等简短触发词快速插入对应的表情符号，也可通过 `ぴえん`（哭泣表情）、`きんにく`（肌肉表情）等日语关键词触发相关 Emoji，为日常聊天和社交场景提供便捷输入。

### 罗马字到假名转换
`karukan-engine` 内置完整的罗马字（Romaji）到平假名（Hiragana）的转换引擎，使用 Trie 数据结构和规则系统实现高效的按键序列匹配，支持标准罗马字输入方案，是日语 IME 输入管线的基础环节。

### 系统词典与用户词典
基于 **Sudachi** 日语形态素分析器构建系统词典，支持从 Sudachi CSV 文件生成二进制词典。同时支持用户自定义词典（`user_dicts/` 目录）和基于使用频率的学习缓存（`learning.tsv`），采用 `recency * 10.0 + ln(1 + frequency)` 的评分公式对候选词排序，实现越用越准的自适应体验。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Rust（Cargo workspace monorepo） |
| **macOS 前端** | Swift / InputMethodKit |
| **Linux 前端** | C++ addon（fcitx5）+ C FFI 桥接 |
| **推理引擎** | llama.cpp（神经网络模型本地推理） |
| **模型格式** | GGUF（量化格式，支持 Q5 等级别） |
| **模型架构** | GPT-2（训练项目：karukan-jinen，Python） |
| **形态素分析** | Sudachi（日语分词与词典） |
| **词典数据** | SudachiDict + Google Mozc（BSD 3-Clause） |
| **模型分发** | Hugging Face（自动下载与缓存） |
| **进程间通信（macOS）** | JSON-RPC（karukan-imserver 子进程） |
| **HTTP 服务** | karukan-server（Web UI + REST API） |
| **基准测试** | AJIMEE-Bench（Exact Match Rate + CER） |
| **平台支持** | Linux（fcitx5）/ macOS |
| **许可证** | MIT OR Apache-2.0（主体）、BSD 3-Clause（Mozc 数据） |

---

## 项目亮点

### 神经网络驱动的 IME 创新
将 GPT-2 大语言模型技术应用于日语输入法的假名汉字转换，突破了传统统计模型和规则系统的精度天花板。通过 llama.cpp 实现本地高效推理，在保证隐私的同时提供高质量的转换结果，是 NLP 技术在桌面输入法领域的前沿实践。

### 精致的模块化架构
项目采用清晰的五层模块设计：engine（核心推理）→ im（共享引擎逻辑）→ fcitx5/macos（平台前端）→ cli（工具链）。核心引擎与 UI 完全解耦，macOS 前端通过 JSON-RPC 与独立子进程通信，Linux 前端通过 C FFI 桥接，体现了高水平的跨平台工程设计能力。

### 完善的开发工具链
`karukan-cli` 提供了丰富的命令行工具：`karukan-dict` 用于词典构建与浏览（支持 Web UI），`sudachi-dict` 用于 Sudachi 词典转换（支持模型 NLL 评分），`karukan-server` 提供 HTTP API 服务，`ajimee-bench` 用于标准化精度评估。这套工具链覆盖了从词典构建、模型评估到服务部署的完整开发流程。

### 自适应学习机制
内置基于使用频率的学习缓存系统，通过 `learning.tsv` 记录用户的选择偏好，结合近因加权的评分算法（`recency * 10.0 + ln(1 + frequency)`），使输入法能够根据个人使用习惯不断优化候选词排序，实现越用越精准的个性化体验。

---

## 应用场景

### Linux 日语输入
为 Linux 用户提供基于 fcitx5 框架的高质量日语输入体验。在传统日语 IME（如 Mozc、Anthy）之外，提供了一个基于神经网络的新选择，特别适合追求转换精度和现代输入体验的用户。

### macOS 日语输入
为 macOS 用户提供原生 Swift 输入法方案，通过 InputMethodKit 深度集成系统输入体验。适合需要在 Mac 上进行日语写作、学习或日常沟通的用户，可与 Karabiner 等工具配合实现灵活的输入模式切换。

### 日语 NLP 研究与评估
项目内置 AJIMEE-Bench 评估工具，支持对假名汉字转换模型的 Exact Match Rate 和 Character Error Rate 进行标准化评估，为日语 IME 领域的学术研究和模型对比提供了便捷的基准测试平台。

### 嵌入式与服务端日语转换
通过 `karukan-server` 提供的 HTTP API（`/api/convert`、`/api/kanji/convert` 等端点），可将神经网络假名汉字转换能力集成到 Web 应用、聊天系统或其他需要日语输入处理的服务中，实现输入法引擎的服务化部署。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 531 |
| **总 Forks** | 30 |
| **Open Issues** | 11 |
| **许可证** | MIT OR Apache-2.0 |
| **创建时间** | 2024-08-11 |
| **主要语言** | Rust |
| **总 Commits** | 26（main 分支） |

---

## 总结

Karukan 是一个将神经网络技术引入日语输入法领域的前沿开源项目，531 Stars。它以 Rust 为核心语言，通过 llama.cpp 本地推理 GPT-2 模型实现高质量的假名汉字转换，并采用精致的五模块 monorepo 架构支持 Linux（fcitx5）和 macOS（Swift）双平台。项目集成了 Sudachi 词典、自适应学习缓存、实时转换、Emoji 快捷输入等完整功能，同时提供丰富的 CLI 工具链和 HTTP 服务，既是实用的日语输入解决方案，也是 NLP 技术在 IME 领域的创新实验平台。

---

*数据来源：GitHub 仓库 (togatoga/karukan)，2026 年 7 月访问*

# LiteRT-LM 项目分析

> Google 面向边缘设备的大语言模型高性能推理框架，已在 Chrome、Pixel Watch 等产品中投入生产使用。

---

## 基本信息

| 项目 | 详情 |
| :--- | :--- |
| **项目名称** | LiteRT-LM |
| **GitHub 地址** | https://github.com/google-ai-edge/LiteRT-LM |
| **产品官网** | https://ai.google.dev/edge/litert-lm |
| **所属组织** | Google AI Edge (google-ai-edge) |
| **Stars** | ~2,017 |
| **Forks** | ~212 |
| **开源协议** | Apache License 2.0 |
| **主要语言** | C++ |
| **创建时间** | 2025-04-14 |
| **最新版本** | v0.10.1 |

---

## 项目简介

LiteRT-LM 是 Google 推出的**生产级、高性能、开源推理框架**，专为在边缘设备上部署大语言模型 (LLM) 而设计。它已实际应用于 Chrome 浏览器、Chromebook Plus、Pixel Watch 等 Google 核心产品中，提供端侧生成式 AI 体验。

---

## 解决的核心问题

在移动端和物联网设备上运行大语言模型面临三大挑战：

1. **算力受限** — 边缘设备的 CPU/GPU/NPU 性能远低于服务器
2. **内存有限** — 设备内存不足以直接加载完整大模型
3. **生态碎片化** — 不同平台（Android、iOS、Web、桌面、IoT）差异巨大

LiteRT-LM 通过硬件加速、模型量化和统一的跨平台 API 体系，让 LLM 能够在资源受限的边缘设备上高效运行。

---

## 核心特性

### 跨平台支持
覆盖 Android、iOS、Web、桌面（Linux/macOS/Windows WSL）和 IoT 设备（如 Raspberry Pi）。

### 硬件加速
通过 GPU 和 NPU 加速器榨取硬件峰值性能，最新版本支持 NPU 加速（Gemma 模型）和桌面 GPU。

### 多模态输入
支持视觉（图像）和音频输入，不限于纯文本推理。

### 工具调用 (Tool Use)
内置 Function Calling 支持，可用于构建 Agentic 工作流，让端侧模型具备调用外部工具的能力。

### 广泛的模型支持
兼容 Gemma（含最新 Gemma 4）、Llama、Phi-4、Qwen 等主流开源模型家族。

### CLI 工具
提供 `litert-lm` 命令行工具，无需编写代码即可在终端快速体验模型推理。

---

## 技术栈

| 层级 | 技术 |
| :--- | :--- |
| **核心引擎** | C++ |
| **Android API** | Kotlin (Stable) |
| **脚本/原型** | Python (Stable) |
| **高性能原生** | C++ (Stable) |
| **iOS/macOS** | Swift (开发中) |
| **模型格式** | LiteRT 自有格式 (.litertlm) |
| **模型来源** | Hugging Face 仓库 |
| **构建系统** | 支持从源码编译 |
| **部署工具** | `uv` / `litert-lm` CLI |

---

## 应用场景

- **移动端智能助手** — 在 Android/iOS 应用中集成端侧 LLM，无需联网即可对话
- **浏览器内 AI** — Chrome 中直接运行生成式 AI 功能（已生产使用）
- **可穿戴设备** — Pixel Watch 等智能手表上的端侧 AI 推理
- **离线 AI 应用** — 无网络环境下的文本生成、翻译、摘要
- **IoT 智能网关** — 在 Raspberry Pi 等设备上部署轻量 LLM
- **Agentic 工作流** — 利用 Function Calling 构建可调用工具的端侧智能体
- **多模态分析** — 端侧图像理解、语音处理

---

## 版本演进

| 版本 | 关键更新 |
| :--- | :--- |
| **v0.10.1** | Gemma 4 支持，引入 LiteRT-LM CLI |
| **v0.9.0** | Function Calling 能力增强，性能稳定性提升 |
| **v0.8.0** | 桌面 GPU 支持，多模态输入 |
| **v0.7.0** | NPU 加速（Gemma 模型） |

---

## 快速上手示例

```bash
# 安装 CLI
uv tool install litert-lm

# 一行命令运行 Gemma 3n 模型
litert-lm run \
  --from-huggingface-repo=google/gemma-3n-E2B-it-litert-lm \
  gemma-3n-E2B-it-int4 \
  --prompt="What is the capital of France?"

# 运行最新的 Gemma 4 模型
litert-lm run \
  --from-huggingface-repo=litert-community/gemma-4-E2B-it-litert-lm \
  gemma-4-E2B-it.litertlm \
  --prompt="What is the capital of France?"
```

---

## 相关资源

- [技术概览（含性能基准）](https://ai.google.dev/edge/litert-lm/overview)
- [CLI 使用指南](https://ai.google.dev/edge/litert-lm/cli)
- [Android (Kotlin) 指南](https://ai.google.dev/edge/litert-lm/android)
- [Python 指南](https://ai.google.dev/edge/litert-lm/python)
- [C++ 指南](https://ai.google.dev/edge/litert-lm/cpp)
- [Google AI Edge Gallery App](https://github.com/google-ai-edge/gallery)
- [从源码编译](https://github.com/google-ai-edge/LiteRT-LM/blob/main/docs/getting-started/build-and-run.md)

---

## 一句话总结

> LiteRT-LM 是 Google 出品的生产级端侧 LLM 推理框架，通过硬件加速和跨平台 API 让大语言模型在手机、浏览器、手表、IoT 等边缘设备上高效运行，已在 Chrome 和 Pixel Watch 等产品中落地。

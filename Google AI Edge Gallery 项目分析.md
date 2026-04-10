# Google AI Edge Gallery 项目分析

> **设备端生成式 AI 体验平台** — Google 出品的移动端 AI 模型运行与评测应用，让最强开源 LLM 在手机上完全离线运行。

- **GitHub**: [google-ai-edge/gallery](https://github.com/google-ai-edge/gallery)
- **许可证**: Apache 2.0
- **状态**: 实验性 Beta
- **系统要求**: Android 12+ / iOS 17+
- **下载**: [Google Play](https://play.google.com/store/apps/details?id=com.google.ai.edge.gallery) / [App Store](https://apps.apple.com/app/ai-edge-gallery) / [APK 直装](https://github.com/google-ai-edge/gallery/releases)

---

## 项目定位

Google AI Edge Gallery 是一个移动端应用，核心目标是将开源大语言模型（LLM）带到手机本地运行。所有推理在设备端完成，**无需联网，完全离线**，保障用户隐私。最新版已支持 **Gemma 4** 模型家族。

---

## 核心功能

### 1. Agent Skills（智能体技能）

将 LLM 从纯对话助手升级为**主动式助手**。通过模块化技能扩展模型能力：
- Wikipedia 事实核查
- 交互式地图
- 富文本摘要卡片
- 支持从 URL 加载自定义技能
- 可浏览 GitHub Discussions 上的社区贡献

### 2. AI Chat with Thinking Mode（AI 对话 + 思维模式）

- 多轮流畅对话
- **Thinking Mode**：开启后可查看模型的**逐步推理过程**，理解复杂问题如何被解决
- 目前支持 Gemma 4 系列模型

### 3. Ask Image（图像问答）

多模态能力，支持：
- 物体识别
- 视觉谜题解答
- 使用摄像头或相册图片获取详细描述

### 4. Audio Scribe（语音转录）

- 实时语音转文字
- 语音翻译
- 使用高效设备端语言模型

### 5. Prompt Lab（提示词实验室）

- 测试不同提示词和单轮用例的专用工作区
- 细粒度控制模型参数（temperature、top-k 等）

### 6. Mobile Actions（移动端操作）

- 离线设备控制与自动化任务
- 基于 FunctionGemma 270m 微调模型驱动

### 7. Tiny Garden（迷你花园）

- 实验性小游戏
- 使用自然语言种植和收获虚拟花园
- 同样基于 FunctionGemma 270m 微调

### 8. 模型管理与基准测试

- 灵活的模型沙盒，支持多种开源模型
- 从列表下载或加载自定义模型
- 管理模型库
- 运行基准测试，了解模型在**你的硬件**上的实际表现

---

## 技术栈

| 技术 | 说明 |
|------|------|
| **Google AI Edge** | 设备端 ML 的核心 API 和工具 |
| **LiteRT** | 轻量级运行时，优化模型执行（即 TensorFlow Lite 的新品牌） |
| **Hugging Face 集成** | 模型发现与下载 |
| **Gemma 4** | 最新支持的模型家族，具备高级推理与创作能力 |
| **FunctionGemma 270m** | 专为设备端功能调用微调的小模型 |

---

## 亮点特性

### 100% 设备端隐私

所有模型推理直接在设备硬件上运行，不需要网络连接。用户的提示词、图片和敏感数据**永不离开设备**。

### 思维模式（Thinking Mode）

这是区别于其他本地 AI 应用的杀手级功能。开启后可以看到模型如何一步步推理，对于理解复杂问题解决过程非常有价值。目前支持 Gemma 4 系列。

### 模块化技能系统

通过 Agent Skills 机制，可以像安装插件一样扩展模型能力。支持社区贡献和自定义 URL 加载。

---

## 适用场景

| 场景 | 说明 |
|------|------|
| **隐私优先** | 需要完全离线的 AI 对话，数据不离开设备 |
| **模型评测** | 在真实移动硬件上基准测试不同 LLM 的表现 |
| **提示词工程** | 在 Prompt Lab 中调试和优化提示词 |
| **边缘 AI 开发** | 了解和学习设备端 AI 的实现方式 |
| **日常 AI 使用** | 随时随地使用 AI，不受网络限制 |

---

## 与同类项目对比

| 特性 | AI Edge Gallery | 其他本地 AI 应用 |
|------|----------------|-----------------|
| **Google 官方** | ✅ | ❌ |
| **Android + iOS** | ✅ | 多数仅 Android |
| **思维模式** | ✅ | ❌ |
| **Agent 技能扩展** | ✅ | 少数支持 |
| **基准测试工具** | ✅ | 少数支持 |
| **多模态** | ✅（图像 + 语音） | 部分支持 |
| **Hugging Face 集成** | ✅ | 部分支持 |

---

## 快速开始

1. 确认设备满足系统要求（Android 12+ / iOS 17+）
2. 从应用商店下载安装
3. 打开应用，选择并下载模型
4. 开始使用各项 AI 功能，全程无需联网

---

## 一句话总结

> Google AI Edge Gallery 是 Google 官方推出的**设备端 AI 体验中心**——让开源 LLM 在手机上离线运行，支持对话、图像问答、语音转录、提示词实验、模型评测等功能，所有推理在本地完成，隐私零泄露。

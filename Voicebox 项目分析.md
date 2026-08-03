# Voicebox 项目分析

**项目地址**：https://github.com/jamiepine/voicebox

## 项目概述

Voicebox 是一个开源的本地化语音合成工作室，定位为 ElevenLabs 的免费开源替代品。它能够从几秒钟的音频中克隆声音，支持 5 个 TTS 引擎、23 种语言的语音生成，并提供后处理效果和多轨时间线编辑器。项目由 Jamie Pine 开发，采用 Tauri (Rust) 构建桌面应用，所有模型和语音数据都在本地运行，确保完全隐私。

- **作者**：Jamie Pine (@jamiepine)
- **许可证**：MIT
- **官网**：voicebox.sh
- **技术定位**：本地优先的语音克隆与合成工具

## 核心功能

### 多引擎语音克隆
项目内置 5 个 TTS 引擎，每个引擎有不同的优势：

| 引擎 | 语言数 | 特点 |
|------|--------|------|
| Qwen3-TTS (0.6B/1.7B) | 10 | 高质量多语言克隆，支持语速/语气指令（"慢一点说"、"低语"） |
| LuxTTS | 英语 | 轻量（约 1GB VRAM），48kHz 输出，CPU 上 150 倍实时速度 |
| Chatterbox Multilingual | 23 | 最广语言覆盖——阿拉伯语、芬兰语、希伯来语、斯瓦希里语等 |
| Chatterbox Turbo | 英语 | 快速 350M 模型，支持副语言情感标签 |
| TADA (1B/3B) | 10 | HumeAI 语音语言模型，支持 700 秒以上连贯音频 |

### 情感与副语言标签
在文本输入中输入 `/` 可插入情感标签（Chatterbox Turbo 引擎）：
- `[laugh]` `[chuckle]` `[gasp]` `[cough]` `[sigh]` `[groan]` `[sniff]` `[shush]` `[clear throat]`

### 后处理效果（8 种）
基于 Spotify 的 `pedalboard` 库，支持实时预览：
- 变调（Pitch Shift，±12 半音）
- 混响（Reverb）
- 延迟（Delay/Echo）
- 合唱/镶边（Chorus/Flanger）
- 压缩器（Compressor）
- 增益（Gain，-40 ~ +40 dB）
- 高通滤波器
- 低通滤波器

内置 4 个预设（机器人、广播、回声室、低沉嗓音），支持自定义预设。

### 无限长度生成
- 自动在句子边界切分文本，逐块生成后交叉淡入淡出
- 可配置自动分块上限（100–5,000 字符）
- 交叉淡入淡出滑块（0–200ms）
- 最大文本长度：50,000 字符
- 智能切分：尊重缩写、中日韩标点和 `[标签]`

### Stories 编辑器
多轨时间线编辑器，适用于对话、播客和叙事场景：
- 多轨合成，支持拖放
- 内联音频裁剪和拆分
- 自动回放与同步播放头
- 每个轨道片段支持版本锁定

### 语音档案管理
- 从音频文件创建档案或直接在应用内录音
- 导入/导出档案以备份或分享
- 多样本支持，提高克隆质量
- 每个档案可设置默认效果链

### REST API
完整的 REST API，用于将语音合成集成到自己的应用中：
- `POST /generate` — 生成语音
- `GET /profiles` — 列出语音档案
- `POST /profiles` — 创建语音档案
- API 文档：`http://localhost:17493/docs`

### 录音与转录
- 应用内录音，带波形可视化
- 系统音频捕获（macOS 和 Windows）
- 自动转录（Whisper / Whisper Turbo）

## 技术栈

| 层面 | 技术 |
|------|------|
| 桌面应用 | Tauri (Rust)，非 Electron |
| 前端 | React + TypeScript + Tailwind CSS |
| 状态管理 | Zustand + React Query |
| 后端 | FastAPI (Python) |
| TTS 引擎 | Qwen3-TTS, LuxTTS, Chatterbox, Chatterbox Turbo, TADA |
| 音效处理 | Pedalboard (Spotify) |
| 语音转录 | Whisper / Whisper Turbo (PyTorch 或 MLX) |
| 推理后端 | MLX (Apple Silicon) / PyTorch (CUDA/ROCm/XPU/CPU) |
| 数据库 | SQLite |
| 音频处理 | WaveSurfer.js, librosa |

### GPU 支持矩阵

| 平台 | 后端 | 备注 |
|------|------|------|
| macOS (Apple Silicon) | MLX (Metal) | 通过 Neural Engine 快 4-5 倍 |
| Windows/Linux (NVIDIA) | PyTorch (CUDA) | 自动下载 CUDA 二进制 |
| Linux (AMD) | PyTorch (ROCm) | 自动配置 HSA_OVERRIDE_GFX_VERSION |
| Windows (任意 GPU) | DirectML | 通用 Windows GPU 支持 |
| Intel Arc | IPEX/XPU | Intel 独立显卡加速 |
| 任意 | CPU | 通用兼容，但较慢 |

## 项目亮点

- **本地优先，完全隐私**：所有模型和数据都在本机运行，零数据外泄
- **5 个 TTS 引擎可切换**：不同引擎适配不同场景，按需选择最优方案
- **23 种语言覆盖**：从英语到阿拉伯语、日语、印地语、斯瓦希里语
- **情感标签系统**：支持 `[laugh]` `[sigh]` `[gasp]` 等副语言表达
- **原生性能**：使用 Tauri (Rust) 而非 Electron，轻量高效
- **全平台 GPU 支持**：Apple Silicon MLX、NVIDIA CUDA、AMD ROCm、Intel Arc、DirectML
- **MIT 开源许可**：完全免费，无商业限制
- **内置 REST API**：方便开发者集成到自己的项目中
- **Stories 多轨编辑器**：类似视频编辑的时间线界面，支持多角色对话

## 应用场景

- **播客制作**：使用多语音克隆和 Stories 编辑器制作多角色播客
- **游戏开发**：通过 REST API 为游戏角色生成对话语音
- **视频配音**：将脚本转换为高质量语音，支持多种情感和语气
- **无障碍辅助**：为视障用户提供文本转语音服务
- **有声书制作**：支持无限长度文本生成，适合长篇有声读物
- **内容本地化**：23 种语言支持，轻松生成多语言版本
- **语音助手开发**：通过 API 集成到自定义语音助手应用
- **教育内容**：为教学视频和课件生成旁白

## Star 数据

- 总 Star 数：16,302
- Fork 数：1,940
- 今日增长：+512
- 贡献者：jamiepine, tomasmach, selop, pandego 等


---

## 📋 更新记录

### 更新 1 — 2026 年 7 月 23 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：

Voicebox 自首次分析以来实现了从「语音克隆工作室」到「完整 AI 语音工作室」的蜕变。项目发布了 **v0.5.0** 大版本（2026 年 4 月），这是迄今为止最重要的更新，将 Voicebox 从单纯的 TTS 工具升级为完整的语音输入/输出平台。TTS 引擎从最初 5 个扩展至 **7 个**（新增 Qwen3-TTS 0.6B/1.7B、Qwen CustomVoice、LuxTTS、TADA），语言覆盖从 23 种保持不变但质量大幅提升。

v0.5.0 的核心新功能包括：系统级全局听写（通过可配置的键盘快捷键，可向任何应用输入文本）、MCP 集成的 AI 代理语音输出（Claude Code、Cursor、Windsurf 等可直接用用户克隆的声音朗读回复）、Stories 多轨对话编辑器、8 种后处理效果（基于 Spotify Pedalboard）。项目累计发布了 **25 个版本**，从 v0.1.0（2026 年 1 月）到 v0.5.0，开发节奏极为活跃。技术媒体 TechTimes 专门撰文评价其 3 秒零样本语音克隆能力，AI Toolly 也将其列为 GitHub Trending 热门项目。Stars 从约 16K 飙升至 45K+，增幅近 3 倍，反映了社区对本地化、隐私友好的开源语音工具的强烈需求。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 16,302 | 45,768 | +29,466 |
| 总 Forks | — | 5,587 | — |

**核心变化概要**：
- 今日新增 557 个 Stars，持续登上 Trending 榜单

### 更新 2 — 2026 年 8 月 3 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
Voicebox 持续稳定增长，Star 数从 45,768 增长至 **48,404**（+2,636）。作为本地优先的语音合成工作室，项目在 AI 语音工具领域持续保持热度。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 45,768 | 48,404 | +2,636 |

**核心变化概要**：
- Star 数从 45.8K 增长至 48.4K，即将突破 5 万 Star 里程碑
- 作为 ElevenLabs 开源替代品的定位持续获得社区认可

---

## 总结

Voicebox 是语音合成领域的一颗新星。它以"本地优先 + 多引擎 + 全平台 GPU"的组合拳，为 ElevenLabs 等商业服务提供了一个强有力的开源替代方案。5 个 TTS 引擎的灵活切换、23 种语言的广泛覆盖、8 种后处理效果以及 Stories 多轨编辑器，构成了一个功能完整的语音创作工具链。MIT 许可证和 REST API 的开放设计使其对个人创作者和商业团队都极具吸引力。16K+ 的 Star 数证明了市场对本地化、隐私友好的语音合成工具的强烈需求。

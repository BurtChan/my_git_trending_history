# MOSS-Transcribe-Diarize 项目分析

## 项目名称

**MOSS-Transcribe-Diarize** — 开源端到端多说话人语音转写与说话人分离模型

- **GitHub**: [OpenMOSS/MOSS-Transcribe-Diarize](https://github.com/OpenMOSS/MOSS-Transcribe-Diarize)
- **许可证**: Apache-2.0

---

## 项目概述

MOSS-Transcribe-Diarize 是由 **OpenMOSS 团队**（上海创新研究院 SII，与复旦大学和 MOSI.AI 紧密合作）推出的**开源端到端音频理解模型**。该模型以仅 0.9B 参数实现了长音频、多说话人的统一建模，一次性完成自动语音识别（ASR）、说话人分离（Diarization）、时间戳预测和声学事件感知四项任务，无需拼接独立的 ASR 和 Diarization 系统。

传统方案通常需要将 ASR 模型和说话人分离模型级联使用，存在对齐困难、误差传播等问题。MOSS-Transcribe-Diarize 采用端到端设计，接收原始音频输入，直接输出带说话人标签和时间戳的结构化转录文本，格式为 `[起始时间][说话人编号]转写文本[结束时间]`，如 `[0.48][S01]Welcome everyone[1.66][12.26][S02]The new pipeline is ready[13.81]`。

项目在多项基准测试中击败了 Doubao、ElevenLabs、Gemini 2.5 Pro 等商业模型，并获得了 **INTERSPEECH 2026 第二届 MLC-SLM Challenge 冠军**（14 种语言赛道）。同时提供 Pro 版本（更高性能，API 访问），社区反馈该模型实际支持的语言范围远超官方声明的中英文，在电话语音等场景也有良好表现。

---

## 核心功能

### 1. 端到端多说话人转写
将 ASR 和说话人分离统一在一个模型内完成，避免传统级联方案的误差传播和对齐问题，支持两个及以上说话人的对话场景。

### 2. 精确时间戳预测
每段转写文本均附带起止时间戳（秒级精度），输出格式 `[start][Sxx]text[end]`，可直接用于字幕生成、会议记录等下游任务。

### 3. 50+ 种语言支持
支持中文、英语、日语、韩语等全球 50 余种语言，实际测试显示支持范围可能更广，包括电话语音、方言等非标准场景。

### 4. 长音频处理
可处理长达 90 分钟的音频片段，在单次推理中完成完整转写，适合会议、播客、访谈等长音频场景。

### 5. 声学事件感知
除了语音转写外，模型还能感知声学事件（如笑声、掌声、沉默等），提供更丰富的音频理解能力。

### 6. OpenAI 兼容 API
通过 SGLang Omni 后端部署时，提供与 OpenAI `/v1/audio/transcriptions` 完全兼容的 API 接口，方便集成到现有系统中。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Python |
| **音频编码器** | Whisper-Medium 风格卷积-Transformer 编码器 |
| **文本解码器** | Qwen3-0.6B 风格因果语言模型 |
| **音频前端** | WhisperFeatureExtractor，16kHz，80 mel bins，30s 分块 |
| **音文桥接** | 4× 时间步合并 + MLP 适配器 |
| **融合方式** | masked_scatter 将音频特征替换 `<|audio_pad|>` 嵌入 |
| **推理后端** | Transformers / SGLang Omni（推荐，OpenAI 兼容） |
| **模型规模** | 0.9B（开源）/ Pro（API） |
| **支持语言** | 50+ |
| **许可证** | Apache-2.0 |

---

## 项目亮点

### 小模型大能力
仅 0.9B 参数，但在 AISHELL-4、Alimeeting、Podcast、Movies 等多项基准上取得 SOTA 或接近 SOTA 的成绩，整体性能超越 Doubao、ElevenLabs、Gemini 2.5 Pro 等参数量大得多的模型。

### 端到端统一建模
打破传统 ASR + Diarization 级联方案的局限，通过单一模型联合优化语音转写和说话人分离，消除了级联误差传播和对齐问题，cpCER 和 Δcp 指标显著优于传统方案。

### 学术竞赛冠军验证
INTERSPEECH 2026 第二届 MLC-SLM Challenge 14 语言赛道冠军，学术认可度高，论文已发表。

### 生产级部署支持
SGLang Omni 后端在单张 H100 上可实现 16 并发、RTF 低至 0.061，提供 OpenAI 兼容 API，支持 `response_format=json/verbose_json/text`，可直接替代现有 Whisper 服务。

---

## 应用场景

### 会议记录与字幕生成
自动将会议录音转写为带说话人标签和时间戳的文本，直接生成结构化会议纪要或字幕文件。

### 播客与访谈内容处理
对播客、访谈节目等长音频进行高效转写，自动区分不同嘉宾的发言，便于内容检索和二次创作。

### 客服对话质检
将客服通话录音自动转写并标注不同说话人，用于服务质量监控、合规审查和对话分析。

### 多语言媒体内容处理
利用 50+ 语言支持处理全球化媒体内容，实现跨语言的音频转写和理解。

### 法律/医疗录音转写
对法庭庭审录音、医患对话录音等专业场景进行结构化转写，提供带时间戳的精确记录。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 427+ |
| **总 Forks** | 50+ |
| **许可证** | Apache-2.0 |
| **主要语言** | Python |
| **首次发布** | 2026 年 5 月 |

---

## 总结

MOSS-Transcribe-Diarize 是 OpenMOSS 团队继 MOSS-TTS 之后在语音领域的又一力作，也是当前**开源端到端多说话人语音转写领域的 SOTA 模型**。仅 0.9B 参数即实现了 ASR + 说话人分离 + 时间戳预测的统一建模，在多项基准上击败了 Doubao、ElevenLabs、Gemini 等商业模型，并获得 INTERSPEECH 2026 竞赛冠军。项目提供 OpenAI 兼容 API，SGLang Omni 后端性能优异，可直接集成到现有语音处理流水线中，是会议转写、播客处理、客服质检等场景的优秀选择。

---

*数据来源：GitHub 仓库 (OpenMOSS/MOSS-Transcribe-Diarize)、Reddit r/speechtech 社区反馈、Emergent Mind（2026 年 7 月访问）*

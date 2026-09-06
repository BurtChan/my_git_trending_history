# OpenWhispr 项目分析

## 项目名称
**OpenWhispr** — WisprFlow / Granola 的开源免费替代：隐私优先的语音转文字听写工具，集成 AI 智能体、会议转录与笔记，跨 macOS/Windows/Linux
- **GitHub**: [OpenWhispr/openwhispr](https://github.com/OpenWhispr/openwhispr)
- **许可证**: MIT

---

## 项目概述
OpenWhispr 是一款桌面端语音听写（voice-to-text dictation）应用：按热键、说话、文字立刻出现在光标处。它把自己定位为 WisprFlow 和 Granola 这两款热门商业语音效率工具的开源免费替代品，核心卖点是「隐私优先」——支持完全离线的本地语音识别（本地 Whisper、NVIDIA Parakeet），音频永远不离开设备；也支持 BYOK（自带 API Key）云端模式换取速度。无数据收集、无遥测、完全开源。

除了基础听写，它还提供 AI 文本处理（本地 llama.cpp 推理）、会议转录（含原生 AEC 回声消除辅助模块）与笔记生成，正在从单一听写工具扩展为「语音输入 + 会议记录 + AI 笔记」的完整语音生产力套件。项目已有 2,119 次提交、release 频繁，被 Neon 赞助，社区活跃度高，近期登上 Trending 反映出语音 AI 生产力工具从尝鲜走向日常、用户开始追求开源可控替代方案的趋势。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 全局热键听写 | 任意应用内按热键说话，文字出现在光标处 |
| 本地离线转录 | Whisper / NVIDIA Parakeet 本地引擎（whisper.cpp + sherpa-onnx），音频不出设备 |
| 云端 BYOK | 自带 API Key 使用云端模型，速度优先 |
| 会议转录 | meeting-aec-helper 原生回声消除模块辅助会议场景 |
| AI 智能体与笔记 | 基于 llama.cpp 本地 LLM 的文本后处理与笔记生成 |
| MCP 集成 | 内置 MCP server，可被其他 AI 工具调用 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 桌面框架 | Electron 41 |
| 前端 | React 19、TypeScript、Tailwind CSS v4、shadcn/ui |
| 本地存储 | better-sqlite3 |
| 语音引擎 | whisper.cpp、sherpa-onnx（Parakeet 推理） |
| 本地 LLM | llama.cpp |
| 打包 | electron-builder（含未签名 Windows 变体）、Nix flake |

---

## 项目亮点

### 「音频永不离开设备」的隐私承诺
在几乎所有语音工具都默认云端处理的背景下，OpenWhispr 把本地 Whisper/Parakeet 转录作为一等公民，配合零遥测承诺，满足律师、医生、企业员工等对语音数据敏感人群的真实合规需求。

### 完整的自托管技术闭环
从 whisper.cpp 语音推理、sherpa-onnx 运行时、llama.cpp 本地 LLM 到 better-sqlite3 本地存储，整条链路不依赖任何强制云服务，甚至提供 custom-asr-shim 示例支持任意自托管 ASR API——技术上是最彻底的「去云化」语音工具。

### 针对商业产品的正面竞争姿态
README 直接对标 WisprFlow/Granola，文档站（docs.openwhispr.com）覆盖快速入门、平台指南、API、MCP、故障排查，成熟度按商业产品标准打造，而非玩具项目。

---

## 应用场景

### 日常文字输入提效
写邮件、聊天、填表时用语音代替打字，本地转录零延迟零成本，适合每天大量文字输入的写作者与客服。

### 会议记录与纪要
会议转录 + AI 笔记生成，全程本地处理，适合对外部会议录音敏感的企业内部使用。

### 无障碍与多语言输入
跨平台（含 Linux）+ Whisper 多语言能力，为打字不便人群与多语言工作者提供低成本语音输入方案。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ 总 Stars | 7,109 |
| 🍴 总 Forks | 924 |
| 📈 今日新增 | 274 stars |
| 许可证 | MIT |
| 主要语言 | TypeScript |

---

## 总结
OpenWhispr 是语音生产力赛道「开源替代商业 SaaS」的代表作：用 whisper.cpp + llama.cpp + 全本地链路实现了 WisprFlow 级体验且音频不出设备，对隐私敏感用户而言是目前最完整的免费选择。

---

*数据来源：GitHub 仓库 (OpenWhispr/openwhispr)，2026 年 9 月访问*

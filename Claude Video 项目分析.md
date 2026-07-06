# Claude Video 项目分析

## 项目名称

**Claude Video** — 为 Claude AI 赋予视频观看能力

- GitHub 仓库：[bradautomates/claude-video](https://github.com/bradautomates/claude-video)
- 许可证：MIT
- 开发语言：Python

---

## 项目概述

Claude Video 是一个专为 Claude AI 编程助手设计的技能插件，通过 `/watch` 命令让 Claude 具备"观看"视频的能力。Claude 原生只能处理文本和图像输入，无法直接理解视频内容。这个插件填补了这一能力空白——用户只需提供一个视频链接或本地文件路径，Claude Video 会自动下载视频、提取关键帧、生成时间戳转录文本，然后将所有帧作为图像交给 Claude 分析，使 Claude 能够"看到"视频画面、"听到"音频内容。

该项目的核心技术架构基于 FFmpeg 和 yt-dlp 两大工具链。FFmpeg 负责视频下载后的帧提取和音视频处理，yt-dlp 负责从 YouTube、TikTok、Vimeo 等主流平台下载视频。通过智能帧预算系统，Claude Video 根据视频时长自动调整提取密度——30 秒以内的视频密集采样约 30 帧，而超过 10 分钟的长视频则限制在 100 帧以内，避免 token 消耗失控。同时内置了基于亮度阈值的帧去重机制，能够识别慢速淡入淡出和静态画面，避免重复帧浪费 token。

Claude Video 提供了四种细节模式：`transcript`（仅字幕，4.5 秒完成，零图像 token）、`efficient`（关键帧提取，约 50 帧）、`balanced`（场景切换检测，约 100 帧，默认模式）和 `token-burner`（不限帧数，最高保真）。对于 49 分钟的 720p 视频，`balanced` 模式约 21 秒完成处理，消耗约 19,700 图像 token。这种灵活的精度-成本权衡机制使开发者可以根据具体需求选择合适的处理深度。

项目自 2026 年 4 月创建以来迅速获得关注，目前在 GitHub 上已有超过 3,800 Star。它不仅支持 Claude Code，还兼容 Codex、Cursor、Copilot、Gemini CLI 等 50+ AI 编程助手，通过统一的 skills 安装机制实现跨平台部署。

---

## 核心功能

### 视频下载与提取

支持 YouTube、TikTok、Vimeo 等主流视频平台的 URL 输入，以及本地视频文件路径。通过 yt-dlp 自动处理各种平台的反爬和认证机制，支持仅下载所需片段（`--start`/`--end` 参数），减少不必要的数据传输。

### 多级帧提取引擎

提供四种细节模式，对应不同的帧提取策略：关键帧模式（`-skip_frame nokey`）、场景切换检测模式、以及不限帧数的高保真模式。每种模式在处理速度、token 成本和视觉保真度之间做了不同的权衡。

### 自动帧去重

使用 FFmpeg 对比亮度阈值（2.0），将每个候选帧与上一个**保留帧**（而非前一个候选帧）比较，有效捕获慢速淡入淡出、终端滚动等渐变场景中的冗余帧。实测在静态画面为主的视频中可减少约 50% 的帧数。

### 时间戳转录

自动提取视频内嵌字幕或生成语音转录文本，与帧提取并行处理。转录文本带有精确时间戳，使 Claude 能够将视觉帧与音频内容关联分析。

### 首次运行自动配置

首次使用时自动检测并安装 FFmpeg 和 yt-dlp 依赖：macOS 通过 Homebrew 自动安装，Linux/Windows 打印精确安装命令。后续运行预检查在 100ms 内完成。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 视频处理 | FFmpeg |
| 视频下载 | yt-dlp |
| 开发语言 | Python |
| 插件标准 | AI Agent Skills |
| 目标平台 | Claude Code, Codex, Cursor, Copilot, Gemini CLI 等 |

---

## 项目亮点

### 跨平台兼容性

Claude Video 不仅支持 Claude Code 的原生插件安装（`/plugin marketplace add`），还通过 `npx skills add` 命令兼容 Codex、Cursor、Copilot、Gemini CLI 等 50+ AI 编程助手。这种广泛的兼容性使其成为一个通用的"AI 视频理解"能力增强插件，而非局限于单一平台。

### 智能帧预算系统

根据视频时长自动调整采样密度，确保短视频获得密集采样（30 秒视频约 30 帧），长视频则合理控制帧数避免 token 爆炸。结合 `--start`/`--end` 参数的聚焦模式，可以针对特定时间段进行更高密度的帧提取（最高 2 fps），实现精确定位分析。

### 精细的 Token 成本控制

每帧的 token 消耗公式为 `(width × height) / 750`，用户可通过 `--resolution` 参数调整输出分辨率来精确控制成本。帧去重机制进一步减少了无效帧的 token 开销。四种细节模式为不同预算场景提供了明确的成本预期。

### 多格式输入支持

支持 YouTube、TikTok、Vimeo 等 URL 链接输入，也支持本地 MP4、MOV 等文件路径。对于本地录屏场景（如 Bug 复现、UI 测试），可以直接传入本地文件进行分析，无需上传到任何平台。

---

## 应用场景

### Bug 复现与 UI 分析

开发者在屏幕录制中复现了某个 Bug，可以运行 `/watch bug-repro.mov what's going wrong?`，Claude 会逐帧分析 UI 状态变化，精准定位问题出现的时刻和原因。比截图描述更直观、比文字描述更精确。

### 技术视频内容提取

观看技术教程或产品发布会时，使用 `/watch https://youtu.be/<video> summarize this` 快速获取要点摘要。Claude 能同时分析画面内容和演讲文本，提供比纯文本摘要更全面的理解。

### 内容创作分析

营销团队可以使用 `/watch https://youtu.be/<viral-video> what hook did they open with?` 分析热门视频的开场钩子、叙事结构和视觉策略。帧级分析能力让 AI 能识别到传统文本分析无法捕捉的视觉叙事技巧。

### 会议录像审查

对于重要的线上会议录像，Claude Video 可以提取每一页 PPT 的截图、演讲者的发言内容，并生成带有时间戳的结构化笔记，大幅提升会后回顾的效率。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| GitHub Stars | 3,812 |
| Forks | 571 |
| 今日新增 Stars | 368 |
| 开发语言 | Python |
| 许可证 | MIT |
| 创建时间 | 2026-04-24 |

---

## 总结

Claude Video 是一个精巧实用的 AI 能力扩展插件，通过帧提取+转录的双通道处理架构，为 Claude 等 AI 编程助手补齐了视频理解这一重要能力短板。其智能帧预算系统和四级细节模式在视觉保真度与 token 成本之间提供了灵活的权衡空间，使开发者可以根据实际需求精确控制分析深度和成本。

---

*数据来源：GitHub 仓库 (bradautomates/claude-video)，2026 年 7 月访问*

# ffmpeg-skill 项目分析

## 项目名称
**ffmpeg-skill** — 给编程 Agent 的本地视频编辑器：42 个 FFmpeg 工具 + 机器可读契约 + MCP 服务器
- **GitHub**: [kajisho5/ffmpeg-skill](https://github.com/kajisho5/ffmpeg-skill)
- **许可证**: MIT

---

## 项目概述

ffmpeg-skill 的口号是「Give your coding agent a video editor」：让 Claude Code、Cursor、Codex 或任何 MCP 客户端能够用本地 FFmpeg 剪辑你的视频素材，并且自己校验输出结果。它把 42 个常用视频编辑操作（剪切、字幕、重构图、响度归一化、平台导出等）封装成带机器可读契约的工具集，Agent 调用后可以自动 probe 验证产物参数（时长、分辨率、帧率），形成「执行—检查」闭环，而不是盲跑命令碰运气。

项目主打零云依赖：无云服务、无 API Key、纯 Python 标准库实现，本地 FFmpeg 完成全部处理，隐私与成本都可控。安装只需 `npx ffmpeg-skill`，同时提供 MCP 服务器模式供各类 MCP 客户端接入。工程规范同样出色：CI 中对 FFmpeg 6.1/7.1/8/9 四个版本做兼容性测试，通过 OpenSSF Scorecard 安全评估，发布 npm 包。

2026 年 9 月创建，两个月内累计 6,100+ Stars 并持续登上 Trending，正好踩中了「Agent 技能生态（Agent Skills）」与「视频内容生产自动化」两条热线的交点：短视频创作者、课程制作者和 Agent 工作流开发者都需要一个能让 AI 可靠操作视频的本地工具。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 42 个 FFmpeg 编辑工具 | 剪切(cut)、适配重构图(fit)、字幕(caption)、静音移除(silence)、响度归一(loudness)等 |
| 机器可读契约 | 每个工具带结构化参数契约，Agent 可靠调用不出格式错 |
| 自校验输出 | Agent 自动 probe 产物：时长/分辨率/帧率量化验证（如 59.98s、1080×1920、30fps）|
| 动态字幕 | karaoke 高亮、pop 动画等字幕样式，caption.py 参数化生成 |
| 平台导出预设 | 16:9 → 9:16 竖屏重构图、各平台规格一键导出 |
| MCP 服务器 | 标准 MCP 协议接入，Claude Code/Cursor/Codex/Gemini CLI 通吃 |
| 零云零密钥 | 本地 FFmpeg 处理，纯 Python 标准库，隐私安全零 API 成本 |
| npm 分发 | `npx ffmpeg-skill` 一条命令安装 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | Python（纯标准库，零第三方依赖）|
| 视频引擎 | FFmpeg 6.1 / 7.1 / 8 / 9（CI 四版本兼容测试）|
| 分发 | npm 包 + npx，MCP Server 模式 |
| 质量与安全 | GitHub Actions CI、OpenSSF Scorecard |
| 字幕/语音 | 可配合 Whisper 做语音转字幕 |
| 许可证 | MIT |

---

## 项目亮点

### 1. 「契约 + 自校验」的 Agent 工具设计范式
不满足于把命令包一层：每个工具带机器可读契约让 Agent 参数不跑偏，执行后 probe 输出物量化校验让 Agent 自己发现错误——这是 Agent 工具设计的教科书式实现。

### 2. 真正的本地优先
无云、无 API Key、纯标准库——视频素材不出本机，对隐私敏感的创作者和企业场景极友好，同时零运行成本。

### 3. 生态卡位精准
同时以 Agent Skill（Claude Code/Cursor/Codex）和 MCP Server 两种形态接入主流编程 Agent，踩中 Agent Skills 生态爆发的风口。

### 4. 工程质量在同类技能项目中居前
FFmpeg 四版本 CI 兼容矩阵、OpenSSF Scorecard、demo 全部可由脚本复现（含逐帧 before/after 对照）——可信度建设远超平均水准。

---

## 应用场景

### 1. 短视频批量加工
Agent 批量执行裁剪、竖屏重构图、加字幕、响度归一、平台导出，一条对话完成整季短视频后期。

### 2. 课程/播客后期自动化
静音段落自动移除、Whisper 转字幕、karaoke 动态字幕、响度标准化（-14 LUFS）全流程交给 Agent。

### 3. Agent 工作流的视频节点
在自动化内容流水线（抓取→生成→剪辑→发布）中作为可靠的视频处理节点接入 MCP。

### 4. 隐私敏感的专业剪辑
素材不能上云的场合（法务、医疗、企业内部内容），本地 FFmpeg 全程处理，合规无忧。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Star 数 | ⭐ 6,154 |
| 总 Fork 数 | 🍴 543 |
| 今日新增 Star | 📈 +331 |
| 主要语言 | Python |
| 开源协议 | MIT |
| 创建时间 | 2026-09-03 |
| Open Issues | 32 |

---

## 总结

ffmpeg-skill 用「机器可读契约 + 输出自校验 + 本地零依赖」的组合拳，把 FFmpeg 这个命令行猛兽驯化成了编程 Agent 可靠驾驭的视频编辑器——42 个工具覆盖短视频后期全流程，是 Agent Skills 生态中工程质量与实用价值兼备的标杆项目。

---

*数据来源：GitHub 仓库 (kajisho5/ffmpeg-skill)，2026 年 11 月 16 日访问*

# Douyin Downloader 项目分析

## 项目名称
**Douyin Downloader** — 实用的抖音批量下载工具：去水印、视频/图集/合集/音乐/直播全覆盖，SQLite 去重 + 浏览器回退
- **GitHub**: [jiji262/douyin-downloader](https://github.com/jiji262/douyin-downloader)
- **许可证**: MIT

---

## 项目概述

Douyin Downloader（V2.0）是一个 Python 编写的抖音内容批量下载工具，支持单条视频/图集/合集/音乐下载，也支持按创作者主页批量抓取（作品/喜欢/合集/音乐四种模式），自动优先选择无水印源并从码率阶梯中挑最高画质。项目以「工程实用性」见长：进度条、指数退避重试、限速、SQLite+本地文件双重去重、增量下载、下载完整性校验（Content-Length 验证、残缺文件自动清理）一应俱全，翻页被风控拦截时还能自动回退到 Playwright 浏览器模式（支持人工过验证码）。

V2 版本的功能扩展明显超出普通下载器：直播流录制（FLV/HLS）、评论区采集（含回复，存 JSON）、抖音热搜榜与关键词搜索（JSONL 导出）、REST API 服务器模式（`--serve`）、Bark/Telegram/Webhook 下载完成通知，甚至集成了 OpenAI Transcriptions API 的视频转写。作者还推出了桌面端 Douzy（闭测中），同一后端支持抖音、TikTok、YouTube 三平台工作区与账号内容同步。

该项目由国内开发者维护（提供完整中文文档与 QQ 群），2023 年创建至今 11K+ Stars，是中文数据自管理工具出海 GitHub Trending 的代表。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 单条下载 | 视频 `/video/{id}`、图集 `/note|gallery/{id}`、合集 `/collection|mix/{id}`、音乐 `/music/{id}` |
| 主页批量 | `/user/{sec_uid}` + post/like/mix/music 四种模式 |
| 无水印+高画质 | 自动选无水印源，从 `video.bit_rate` 梯队挑最高码率 |
| 直播录制 | `live.douyin.com/{room_id}` → FLV/HLS，断流保留部分数据 |
| 评论/热搜采集 | 逐条评论+回复存 JSON；`--hot-board`/`--search` 导出 JSONL |
| 服务器模式 | `--serve` 起 REST API（fastapi+uvicorn 可选） |
| 通知推送 | Bark / Telegram / Webhook |
| 工程可靠性 | SQLite 去重、增量下载、时间过滤、完整性校验、退避重试 |
| 浏览器回退 | Playwright 兜底翻页，支持人工 CAPTCHA |
| 桌面端 Douzy | 抖音/TikTok/YouTube 三平台 GUI（闭测） |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | Python 3.8+ |
| 配置 | YAML（config.example.yml） |
| 存储 | SQLite 去重库 |
| 浏览器回退 | Playwright (Chromium) |
| 进度/并发 | Rich 进度条、可配置并发（默认 5）、限速 2 req/s |
| 服务化 | FastAPI + Uvicorn（可选） |
| 部署 | Dockerfile、GitHub Actions CI |

---

## 项目亮点

### 工程完成度远超同类
去重、增量、退避、限速、完整性校验、静默日志模式——把一个「爬虫脚本」做成了有测试、有 CI、有配置体系的正规工程项目（62 commits 但功能密度极高）。

### 从下载器到数据管理平台
直播录制、评论采集、热搜监控、REST API、视频转写，覆盖「个人数据自管理」全链路，不只是存视频，而是存元数据、存社交图谱。

### 浏览器回退是杀手锏
平台风控升级导致 API 翻页失效是所有 downloader 的死穴，该项目用 Playwright 回退 + 人工过码的设计大幅延长了工具可用寿命。

---

## 应用场景

### 个人内容备份
把自己或关注的创作者作品、图集、音乐无水印归档本地，配合增量模式长期同步。

### 内容创作者素材管理
批量采集对标账号作品与评论区反馈，辅助选题与竞品分析（注意项目声明仅供技术研究与个人数据管理）。

### 数据管道组件
REST API 服务器模式 + JSONL 导出，可以嵌入更大的数据采集流水线。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 11,183 |
| 总 Forks | 1,732 |
| 今日新增 | +473 |
| 主要语言 | Python |
| 许可证 | MIT |
| 创建时间 | 2023-05-25 |

---

## 总结

Douyin Downloader 用严肃的工程质量（去重/重试/回退/校验）把抖音批量下载做成了「个人数据自管理」平台，直播录制、评论采集与桌面端 Douzy 让它成为中文内容工具开源化的标杆项目。

---

*数据来源：GitHub 仓库 (jiji262/douyin-downloader)，2026 年 9 月访问*

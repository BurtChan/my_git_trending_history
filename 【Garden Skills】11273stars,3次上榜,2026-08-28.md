# Garden Skills 项目分析

## 项目名称
**Garden Skills** — ConardLi（code秘密花园）出品的生产级 Agent Skills 合集
- **GitHub**: [ConardLi/garden-skills](https://github.com/ConardLi/garden-skills)
- **许可证**: MIT

---

## 项目概述
Garden Skills 是知名前端技术博主 ConardLi（code秘密花园，公众号/B站/X 全平台技术创作者）开源的 Agent Skills 合集，面向 Claude Code、Cursor、Codex 等 AI 编码代理，收录 5 个生产级 Skill：网页视频演示、Web 设计工程、GPT Image 2 图像生成、本地知识库检索、美文排版。项目 142 commits，中/英/日三语文档，已进入 Claude Code plugin marketplace。

它的定位不是玩具 demo，而是每个 Skill 都带完整工作流、硬性检查点、独立版本发布（如 web-design-engineer v1.3.0）的工程化作品。凭借作者在国内前端社区的影响力（B站 47 万粉级别账号矩阵）和 Skill 生态的热度，上线以来增长迅速。

---

## 核心功能
| Skill | 用途 |
|------|------|
| web-video-presentation | 把脚本/文章/课程转成可录屏的 16:9 网页演示（1920×1080 固定舞台，23 套主题，可插拔 TTS） |
| web-design-engineer | 把 AI 生成的网页从"能用"打磨到"惊艳"：五维设计读数、六大设计流派顾问、25 个锚定风格配方（Linear/Aesop/Bloomberg 等） |
| gpt-image-2 | GPT Image 2 图像生成提示词工程：18 个视觉类目、79 个结构化模板、160+ 公开案例库 |
| kb-retriever | 本地知识库渐进式检索：先导航索引再搜内容，PDF/Excel 先学后处理，最多 5 轮约束 |
| beautiful-article | 任意来源（URL/PDF/截图/笔记）→ 精美可分享文章：10 种文章类型带内容保留率，Reacticle 组件协议 |

---

## 技术栈
| 组件 | 技术 |
|------|------|
| Skill 规范 | Agent Skills（SKILL.md）标准，agentskills.io 认证 |
| 分发 | npx skills CLI / Claude Code plugin marketplace / Releases .zip / git submodule |
| 演示/设计 | Vite + React + TypeScript，主题 token 架构 |
| 图像 | GPT Image 2 及 OpenAI 兼容图像 API |
| 检索 | grep / pdftotext / pdfplumber / pandas 工作流 |

---

## 项目亮点
### 单 Skill 深度即产品
web-design-engineer 内置 25 个锚定风格配方，每个配方带具体色板、字体、签名动作与反模式清单，还有"反 AI 俗套黑名单"，工程化程度远超一般 prompt 合集。

### 硬检查点人机协作
各 Skill 在关键决策点（脚本、主题、大纲、实现模式、音频）强制暂停等用户确认，避免 agent 一口气跑偏，这是对 agent 可控性设计的成熟理解。

### 中文创作者生态红利
作者是国内头部前端博主，B站/公众号/小红书全平台矩阵推广，加上中文文档优先，该项目是国内 Agent Skill 生态的代表作，传播路径与海外项目截然不同。

### 案例库驱动
gpt-image-2 带 160+ 在线案例库，web-video-presentation 有 23 主题画廊，所见即所得降低了采纳门槛。

---

## 应用场景
### 内容创作者工作流
文章 → 演示视频（web-video-presentation）→ 配图（gpt-image-2）→ 精美排版（beautiful-article），一套 Skill 覆盖技术内容生产全链路。

### 前端原型质量提升
让 Cursor/Claude Code 写出的页面过一遍 web-design-engineer，从"AI 味"界面升级为有设计系统的作品，适合 landing page、dashboard 场景。

### 团队本地知识问答
kb-retriever 的渐进式检索 + 引用溯源，适合内部文档目录的问答场景，不淹没上下文。

### 博主/讲师课程制作
把课程文稿转成可分步演示的 16:9 舞台，配 TTS 旁白直接录制成教学视频。

---

## Star 数据
| 指标 | 数值 |
|------|------|
| 总 Stars | 11,273 |
| 总 Forks | 1,406 |
| 今日新增 Star | 381 |

## 📋 更新记录

### 更新 1 — 2026年8月27日（再次登上 Trending）

**更新原因**：连续第二日登上 GitHub Trending，Star 数持续增长

**最新动态**：Garden Skills 在首日爆发（+5,000+）后进入稳步增长期，今日再增 131 Star 突破 10.8K。该项目昨日新建分析后保持连续在榜，反映国内技术社区对 Agent Skills 工程化实践的关注持续升温。仓库本身近期无新 commit（最后推送 2026-07-12），本轮增长主要由 Trending 榜单曝光与 GPT Image 2 生态热度带动——同榜单上游项目 awesome-gpt-image-2（21K Star）今日 +4,044，形成生态联动效应。web-design 与 gpt-image 相关 Skill 是主要引流入口。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 10,761 | 10,892 | +131 |
| 总 Forks | 1,382 | 1,387 | +5 |

**核心变化概要**：
- 连续第二日在榜，Star 突破 10.8K，增速从爆发期回落至稳定增长
- 与 awesome-gpt-image-2 同榜联动，GPT Image 2 生态热度持续外溢
- 仓库无新 commit，增长纯粹由曝光与生态热度驱动

---

### 更新 2 — 2026年8月28日（连续第三日登上 Trending）
**更新原因**：项目连续第三日登上 GitHub Trending 榜单（8/26-8/28，SnailDev 归档验证），今日新增 +381 Stars

**最新动态**：Garden Skills 连续三日在榜，Star 从 10,892 增至 11,273。作为国内头部前端博主 ConardLi 的开源 Agent Skills 合集（网页设计、知识检索、图像生成等五个 Skill），其增长动能来自 GPT Image 2 / Claude Skills 生态热度的持续外溢——同榜的 awesome-gpt-image-2 已连续多日霸榜。Forks 从 1,387 增至 1,406，增速与 Star 保持同步，说明有相当比例的用户在真正使用和改造这些 Skill 而非仅围观收藏。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 10,892 | 11,273 | +381 |
| 总 Forks | 1,387 | 1,406 | +19 |

**核心变化概要**：
- 连续第三日在榜（8/26-8/28），Star 突破 1.1 万
- 增长由 GPT Image 2 / Claude Skills 生态热度持续外溢驱动
- Forks 同步增长 19，用户实际使用与改造比例健康
- 单个 Skill 的「小产品」深度仍是其区别于普通 awesome 列表的核心竞争力

---

## 总结
Garden Skills 是国内头部前端博主交出的 Agent Skills 工程化答卷：五个 Skill 各自达到"小产品"深度，硬检查点与案例库设计体现成熟的 agent 可控性理念，也是观察中文技术社区如何切入 Skill 生态的样本。

---

*数据来源：GitHub 仓库 (ConardLi/garden-skills)，2026 年 8 月 27 日访问*
*首次分析：2026 年 8 月 | 最近更新：2026 年 8 月 28 日*

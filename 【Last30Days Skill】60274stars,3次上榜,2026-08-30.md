# Last30Days Skill 项目分析

## 项目名称
**Last30Days Skill** — AI Agent 技能插件，跨 14+ 平台并行研究任意主题，以真人参与度（点赞、评论、真金白银）评分并综合生成深度摘要

- **GitHub**: [mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill)
- **许可证**: MIT

---

## 项目概述

Last30Days Skill 是一款由开发者 mvanhorn 创建的 **AI Agent 技能插件**，其核心使命是"搜索人，而非聚合编辑器"。它能够同时搜索 Reddit、X/Twitter、YouTube、TikTok、Instagram、Hacker News、Polymarket、GitHub、Threads、Pinterest、Bluesky、Perplexity 等 **14+ 个平台**，然后以**真人参与度信号**（upvotes、likes、评论数、真金白银的投注金额）对搜索结果进行评分排序，最终由 AI Agent 综合生成一份有据可查的研究简报。

该项目的设计哲学直击当前 AI 搜索的核心痛点：**单一 AI 无法访问所有信息源**。Google 搜索无法触及 Reddit 评论和 X 帖子，ChatGPT 有 Reddit 合作但无法搜索 X 和 TikTok，Perplexity 依赖爬虫且缺乏社区信号。Last30Days 通过在 Claude Code 等 AI Agent 内部同时搜索多个平台，利用每个平台独特的参与度信号（如 Reddit 的 upvotes、Polymarket 的真金投注、Hacker News 的 points），让 AI 能够综合来自各个"围墙花园"的信息，生成真正有参考价值的研究摘要。

Last30Days 于 2026 年 1 月 23 日创建，凭借其独特的跨平台研究能力和出色的产品设计，在短时间内获得了超过 27,000 Star，2026 年 6 月 4 日单日新增 173 Star。项目拥有 1,012 个测试用例，代码质量极高，显示出工程严谨性与创新思维的完美结合。

---

## 核心功能

### 1. 跨 14+ 平台并行搜索
| 平台 | 信号类型 | 成本 |
|------|----------|------|
| Reddit | 无过滤的用户观点，评论 upvotes | 免费 |
| X/Twitter | 行业热点、专家长文、突发反应 | 免费（浏览器登录） |
| YouTube | 深度视频完整转录搜索 | 免费（需 yt-dlp） |
| TikTok | 创作者触达率、互动指标 | ScrapeCreators Key |
| Instagram Reels | 网红转录、视觉文化 | ScrapeCreators Key |
| Hacker News | 开发者共识、point/comment 计数 | 免费 |
| Polymarket | 真金白银的投注赔率 | 免费 |
| GitHub | PR 速度、stars、releases、issues | 免费 |
| Digg | AI 1000 排行榜聚类（无需 X 认证） | 免费 |
| Threads/Pinterest/Bluesky | 社交层信号 | 免费 |
| Perplexity | 带引用的网络搜索 | OpenRouter Key |
| Web | 编辑报道、博客 | Brave Search Key |

### 2. 智能搜索（Killer Feature）
引擎在搜索前会**自动解析搜索意图和目标定位**。例如搜索"OpenClaw"时，会自动解析出 @steipete、r/openclaw、r/ClaudeCode 等相关社区和渠道。支持双向映射：人物↔公司、产品↔创始人、名称↔GitHub Profile。

### 3. 可分享的 HTML 简报
`/last30days 主题 --emit=html` 命令可生成自包含的暗色模式 HTML 简报，无需 JS 依赖、内联 CSS、可离线查看，适合打印和分享。

### 4. 跨平台聚类合并
相同故事在 Reddit/X/YouTube 上出现时，自动合并为单一聚类，避免信息重复，确保摘要的简洁性。

### 5. 自动竞争对手发现
`/last30days OpenAI --competitors` 可自动发现竞争对手，并行运行多个研究管线进行对比分析。

### 6. GitHub 人物模式
`/last30days 开发者 --github-user=username` 显示该开发者的 PR 速度、合并率、发布节奏等 GitHub 活动数据。

### 7. 趋势监控
支持 `--store` 持久化到 SQLite，`scripts/watchlist.py` 定时运行 + Slack/webhook 通知，`scripts/briefing.py` 生成日/周报。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | Python |
| AI Agent 集成 | Claude Code / Codex CLI / Gemini CLI 等 50+ Agent |
| 安装方式 | `/plugin marketplace add mvanhorn/last30days-skill` |
| 通用安装 | `npx skills add mvanhorn/last30days-skill -g` |
| 数据存储 | SQLite（持久化模式） |
| 测试覆盖 | 1,012 个测试用例 |
| 搜索后端 | 多平台并行搜索 + Brave Search |

---

## 项目亮点

### 1. "搜索人而非编辑器"的独特定位
Last30Days 的核心理念——以真人参与度信号而非编辑器选择来排序信息——是对传统搜索引擎和 AI 搜索工具的根本性反思。Polymarket 的真金白银投注、Reddit 社区的 upvotes、GitHub 的 stars 和 merge rate，这些信号反映的是**真实人群的真实行为**，比任何算法编辑都更能反映"什么真正重要"。

### 2. 打破平台围墙花园的信息聚合
当前互联网正朝着"围墙花园"方向发展——每个平台都有独特的内容，但没有单一搜索引擎能覆盖所有平台。Last30Days 通过在 AI Agent 内部并行搜索多个平台，打破了这一限制。它不是替代搜索引擎，而是在搜索引擎之上叠加了一层跨平台的社区信号分析。

### 3. 极致的 Agent 技能设计
1,012 个测试用例、50+ AI Agent 平台兼容、30 秒零配置向导——Last30Days 展示了"AI Agent 技能"这一新兴软件形态的最佳实践。它证明了 AI Agent 技能可以是一个高质量、可维护、可扩展的软件产品，而非简单的提示词模板。

### 4. 从搜索到洞察的完整链条
Last30Days 不仅仅是"搜索多个平台"，它的价值在于将搜索结果转化为有洞察力的综合摘要。通过跨平台聚类、参与度排序、AI Agent 综合评估，用户获得的是经过验证的、有据可查的深度研究简报，而非原始搜索结果的堆砌。

---

## 应用场景

### 1. 技术趋势追踪
开发者可以用 `/last30days Claude Code vs Cursor` 快速了解两个工具在社区中的口碑对比——不是看厂商宣传，而是看真实用户在 Reddit、HN、X 上说了什么、投了多少票。

### 2. 人物/公司调研
投资者和猎头可以用 `/last30days Peter Steinberger` 了解一个人的近期活动——GitHub 提交频率、社区讨论热度、行业评价等，全部基于真实的参与度信号。

### 3. 产品竞争分析
产品经理可以用 `/last30days OpenAI --competitors` 了解竞争对手的社区动态，发现潜在竞争者和市场机会。

### 4. 事件研究与事实核查
记者和研究员可以用 `/last30days 特定事件` 快速收集多个平台上的相关信息，以参与度信号判断信息的可信度和热度，辅助事实核查和深度报道。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Star 数 | ⭐ 60,274 |
| 总 Fork 数 | 🍴 5,285 |
| 今日新增 Star | 📈 +272 |
| 主要语言 | Python |
| 开源协议 | MIT |
| 创建时间 | 2026-01-23 |
| Open Issues | 92 |

---

## 总结

Last30Days Skill 是 AI Agent 技能生态中最出色的项目之一。它以"搜索人而非编辑器"的独特理念，打破了互联网平台围墙花园的信息壁垒，通过 14+ 平台并行搜索和真人参与度信号排序，为用户提供了一种全新的深度研究方式。1,012 个测试用例展示了极高的工程标准，50+ Agent 平台的兼容性体现了出色的设计前瞻性。对于需要快速了解"真实世界里真正发生着什么"的研究者、投资者和产品决策者，Last30Days 是一个不可或缺的工具。

---

*数据来源：GitHub 仓库 (mvanhorn/last30days-skill)，2026 年 6 月访问*

---

## 更新记录

### 更新 1 — 2026年7月31日

| 指标 | 数值 |
|------|------|
| 上次记录 | 27,288 Stars |
| 总 Stars | 56,559 |
| 新增 | +29,271 |
| 今日 Trending | +660 stars |

---

### 更新 2 — 2026年8月30日（再次登上 Trending）
**更新原因**：一个月增长 3,715 Stars 回归 Trending，v3.11.x 社区贡献活跃

**最新动态**：自 7 月 31 日更新以来，项目从 v3.3 推进到 v3.11.1（7 月时点已合并 175 个 PR，其中 122 个来自 52 位社区贡献者），引擎持续打磨引用规则与渲染分层。8 月下旬随 Agent Skills 生态整体升温再度登上 Trending。
60K Star 量级使其稳居最热门 Agent 技能之列；安装渠道已覆盖 Claude Code 插件市场、Codex、Cursor、Gemini CLI、Grok 原生插件市场等 50+ Agent 平台，「搜索人而非编辑器」的实时信号研究定位在研究者和决策者群体中口碑持续积累。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 56,559 | 60,274 | +3,715 |
| 总 Forks | 5,285 | 5,285 | +0 |

**核心变化概要**：
- 一个月增长 3,715 Stars 回归 Trending，v3.11.x 社区贡献活跃
- Forks 5,285 → 5,285（+0），社区使用与二次开发持续活跃
- 长期增长动能充足，开发者生态位稳固

---


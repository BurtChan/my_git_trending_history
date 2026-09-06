# Marketing Skills 项目分析

## 项目名称

**Marketing Skills** — 面向 AI 代理的营销技能集合，43+ 种结构化营销专业知识与工作流

- **GitHub**: [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills)
- **许可证**: MIT License

---

## 项目概述

Marketing Skills for AI Agents 是一个面向 AI 代理的营销技能集合，专为技术营销人员和创始人打造。该项目为 Claude Code、OpenAI Codex、Cursor、Windsurf 等遵循 Agent Skills 规范的 AI 编码代理提供结构化的营销专业知识与工作流。

核心理念是将营销最佳实践以 Markdown 文件的形式封装为"技能（Skills）"，让 AI 代理能够像专业营销团队一样执行各类营销任务，包括转化率优化（CRO）、文案撰写、SEO、分析和增长工程等。项目由 Corey Haines（Conversion Factory 创始人、Swipe Files 创建者）主导开发。

v2.0 版本从 `.claude/` 目录迁移到通用的 `.agents/` 目录，增强了跨平台兼容性。项目在极短时间内获得 23,000+ Star 和 3,700+ Fork，证明了"AI + 营销"赛道的巨大市场潜力。

---

## 核心功能

| 技能类别 | 包含技能 |
|---------|---------|
| **转化率优化** | page-cro（页面转化）、form-cro（表单转化）、onboarding-cro（引导转化）、signup-cro（注册转化） |
| **内容与文案** | copywriting（文案撰写）、copy-editing（文案编辑）、email-sequence（邮件序列）、social-content（社交内容） |
| **SEO 与发现** | ai-seo（AI 搜索优化）、seo-audit（SEO 审计）、competitor-alternatives（竞品对比）、aso-audit（应用商店优化） |
| **付费与分发** | ad-creative（广告创意）、landing-page（落地页） |
| **分析与测试** | analytics-tracking（分析追踪）、ab-test-setup（A/B 测试） |
| **增长工程** | free-tool-strategy（免费工具策略）、referral-program（推荐计划）、community-marketing（社区营销）、churn-prevention（流失预防） |
| **策略与变现** | product-marketing-context（产品营销上下文）、launch-strategy（发布策略）、pricing-strategy（定价策略）、content-strategy（内容策略） |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **技能文件格式** | Markdown |
| **主要语言** | JavaScript（CLI 工具和安装脚本） |
| **包管理** | Node.js / npx |
| **技能规范** | Agent Skills 开放规范 |
| **兼容平台** | Claude Code、OpenAI Codex、Cursor、Windsurf |

---

## 项目亮点

1. **结构化营销知识体系** — 每个技能都是精心构建的 Markdown 文件，包含经过验证的营销框架
2. **技能互联** — 技能之间相互引用，以 `product-marketing-context` 为基础构建共享上下文
3. **多平台兼容** — 不仅限于 Claude Code，还支持 Codex、Cursor、Windsurf 等多种 AI 代理
4. **多种安装方式** — 支持 CLI（`npx skills`）、Claude Code 插件、Git 克隆、Submodule、Fork 等 6 种方式

---

## 应用场景

1. **SaaS 创始人**：使用 AI 代理快速生成和优化产品营销策略
2. **技术营销团队**：让 AI 编码助手执行专业营销任务
3. **独立开发者**：使用免费工具策略规划增长，设置 GA4 追踪
4. **增长工程师**：构建自动化营销工作流，创建邮件序列

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 47,342 |
| **Forks** | 7,379 |
| **今日新增** | 172 stars |
| **许可证** | MIT License |
| **主要语言** | JavaScript |

---

## 📋 更新记录

### 更新 1 — 2026 年 9 月 7 日（再次登上 Trending）

**更新原因**：时隔 4 个多月再次登上 GitHub Trending 榜单，Star 翻倍增长至 4.7 万（API 口径）

**最新动态**：
- Marketing Skills 时隔四个多月重回 Trending，Star 从 4 月的约 23,200 翻倍增长至 47,342（+24,142），完成 2 倍跃迁，正式逼近 5 万 Star 俱乐部。
- Forks 从约 3,700 翻倍至 7,379，469 次提交显示项目持续高频迭代；技能库已扩展至覆盖 CRO、SEO/AI-SEO、付费广告、留存、Growth Engineering、RevOps 等营销全链路 40+ 技能，并引入「product-marketing 基础技能 + 其他技能交叉引用」的网状架构。
- 商业化探索值得关注：Verified Partners（如 Converly 转化归因）以披露式赞助接入工具推荐，配套 Conversion Factory 咨询与 Magister AI CMO 产品形成商业闭环，是 Skills 生态中商业模型最清晰的项目之一。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | ~23,200 | 47,342 | +24,142 |
| 总 Forks | ~3,700 | 7,379 | +3,679 |

**核心变化概要**：
- 时隔 4 个月重回 Trending，Star 约 23,200 → 47,342（+24,142，翻倍）
- Forks 约 3,700 → 7,379（翻倍），469 次提交高频迭代
- 技能网络化：product-marketing 基础技能 + 40+ 营销技能交叉引用
- Verified Partners 披露式赞助 + 咨询/AI CMO 产品形成商业闭环

---

## 总结

coreyhaines31/marketingskills 是一个现象级的开源项目，创造性地将营销专业知识系统化为 AI 代理可以理解的"技能"文件。项目采用 MIT 许可证，提供 43+ 种覆盖营销全链路的技能，兼容主流 AI 编码代理平台，短时间内获得 23,000+ Star 和 3,700+ Fork。它代表了 AI 驱动的营销自动化的前沿方向，是技术营销人员和 AI 从业者都值得关注的标杆项目。

---

*数据来源：GitHub 仓库 (coreyhaines31/marketingskills)，2026 年 9 月访问*
*首次分析：2026 年 4 月 | 最近更新：2026 年 9 月 7 日*

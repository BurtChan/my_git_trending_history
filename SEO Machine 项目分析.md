# SEO Machine 项目分析

> **一句话总结** -- 基于 Claude Code 的 SEO 长文内容创作工作空间，集研究、撰写、分析、优化于一体，帮助企业批量生产搜索引擎友好的高质量博客内容。

- **GitHub**: [TheCraigHewitt/seomachine](https://github.com/TheCraigHewitt/seomachine)
- **语言**: Python
- **Stars**: 3,574 | **Forks**: 629
- **许可证**: MIT License (Copyright 2025 Castos)
- **作者**: Craig Hewitt -- 播客托管 SaaS 平台 [Castos](https://castos.com) 创始人，108 位 GitHub 关注者

---

## 解决什么问题

企业和内容团队面临的核心痛点是：**SEO 内容生产流程碎片化**。从关键词研究、竞品分析、撰写初稿、SEO 优化到最终发布，通常需要在多个工具之间反复切换，且 AI 生成的内容往往缺乏品牌一致性、SEO 规范难以统一落地。

SEO Machine 将整个 SEO 内容生命周期（研究 -> 撰写 -> 分析 -> 优化 -> 发布）整合到一个 Claude Code 工作空间中，通过自定义命令、专业化 Agent 和上下文文件系统，让 AI 在充分理解品牌调性、SEO 规范和竞品态势的前提下，产出结构完整、搜索引擎友好的长篇博客文章。

---

## 核心功能

### 1. 自定义命令系统（20+ 条 Slash Command）

| 命令 | 用途 |
|------|------|
| `/research [topic]` | 关键词研究 + Top 10 竞品分析 + 内容空白识别 |
| `/write [topic]` | 生成 2,000-3,000+ 字的 SEO 优化文章 |
| `/rewrite [topic]` | 基于分析结果更新已有内容 |
| `/analyze-existing [URL/file]` | 分析现有文章的 SEO 表现，给出健康评分 (0-100) |
| `/optimize [file]` | 最终 SEO 审计与优化 |
| `/scrub [file]` | 去除 AI 痕迹（破折号、填充短语、机械式表达） |
| `/publish-draft [file]` | 通过 WordPress REST API + Yoast SEO 发布 |
| `/priorities` | 基于分析数据的内容优先级矩阵 |
| `/landing-write/audit/research` | 着陆页创建与 CRO 审计系列命令 |
| `/research-serp/gaps/trending/...` | 细分研究命令（SERP 分析、内容缺口、趋势发现等） |

### 2. 专业化 Agent 体系（10 个）

- **Content Analyzer** -- 五大模块联动（搜索意图、关键词密度、内容长度对比、可读性、SEO 质量），输出出版就绪评估
- **SEO Optimizer** -- 页面 SEO 分析，0-100 评分
- **Meta Creator** -- 生成 5 组 Meta Title + Description 变体，附带 SERP 预览
- **Internal Linker** -- 基于 `internal-links-map.md` 的战略性内链建议
- **Keyword Mapper** -- 关键词分布热力图、密度分析、LSI 关键词覆盖
- **Editor** -- 人性化编辑，检测"机器人腔"并给出修改建议（人性化评分 0-100）
- **Performance** -- 整合 GA4/GSC/DataForSEO 数据，生成内容优先级队列
- **Headline Generator** -- 10+ 标题变体 + A/B 测试建议
- **CRO Analyst** -- 着陆页转化率优化分析
- **Landing Page Optimizer** -- 着陆页全面优化（首屏、CTA、信任信号、结构）

### 3. 26 个营销 Skills

覆盖文案撰写、CRO（着陆页/表单/注册流程/弹窗/付费墙）、营销策略、邮件序列、社交媒体、付费广告、SEO 审计、Schema 标记、程序化 SEO、竞品替代页、分析追踪、A/B 测试、推荐计划、免费工具策略、营销心理学等。

### 4. 高级 SEO 分析模块（Python）

五个独立的 Python 分析引擎：

| 模块 | 功能 |
|------|------|
| `search_intent_analyzer.py` | 搜索意图分类（信息型/导航型/交易型/商业型） |
| `keyword_analyzer.py` | TF-IDF + K-means 主题聚类、关键词密度与分布热力图、关键词堆砌风险检测 |
| `content_length_comparator.py` | 抓取 Top 10-20 SERP 竞品词数，计算中位数/75 分位/推荐长度 |
| `readability_scorer.py` | Flesch Reading Ease、Flesch-Kincaid Grade Level、被动语态比例、复杂词识别 |
| `seo_quality_rater.py` | 0-100 综合评分（内容/关键词/Meta/结构/链接/可读性六维度） |

### 5. 数据集成

- **Google Analytics 4** -- 流量、参与度、转化、趋势
- **Google Search Console** -- 关键词排名、展示/点击、CTR
- **DataForSEO** -- 竞品排名、SERP 特性、关键词指标

### 6. WordPress 发布集成

通过自定义 MU-Plugin 暴露 Yoast SEO 字段，支持直接从工作空间发布文章到 WordPress 站点。

### 7. 上下文驱动的内容生成

8 个上下文文件（品牌调性、写作范例、风格指南、SEO 规范、目标关键词、内链地图、竞品分析、CRO 最佳实践）确保 AI 输出与品牌高度一致。项目附带 Castos 播客托管 SaaS 的完整示例，方便用户参考。

---

## 技术栈

| 层面 | 技术 |
|------|------|
| **AI 引擎** | Claude Code (Anthropic) |
| **编程语言** | Python（分析模块、数据源集成、研究脚本） |
| **NLP 库** | NLTK、textstat、scikit-learn（TF-IDF、K-means） |
| **数据采集** | BeautifulSoup4（网页抓取）、DataForSEO API |
| **分析平台** | Google Analytics 4 API、Google Search Console API |
| **CMS 集成** | WordPress REST API + Yoast SEO（PHP MU-Plugin） |
| **项目结构** | Claude Code Commands/Agents/Skills 三层架构 |
| **配置** | JSON 竞品配置模板、环境变量 `.env` 管理 API 凭证 |

---

## 使用场景

1. **SaaS 企业内容营销团队** -- 批量生产 SEO 优化的技术博客，配合产品关键词集群系统化占领搜索排名
2. **独立站/个人博客运营者** -- 用 AI 加速内容产出，同时保证 SEO 规范和品牌一致性
3. **SEO 代理机构** -- 为多个客户配置不同上下文文件，高效交付 SEO 内容
4. **已有内容库的优化** -- 通过 `/analyze-existing` + `/rewrite` 工作流系统化刷新旧文章
5. **着陆页 CRO** -- 创建和审计转化率优化的着陆页，而不仅仅是博客
6. **播客/媒体公司内容再利用** -- 项目源自 Castos（播客托管平台），天然适配将播客内容转化为 SEO 文章的场景

---

## 项目亮点与洞察

1. **非传统"工具"，而是"工作空间"** -- SEO Machine 不是独立的 SaaS 产品，而是 Claude Code 的定制化配置集合。它的价值在于将 Claude Code 的通用能力通过命令、Agent、上下文文件塑造成 SEO 内容专家。

2. **"上下文即护城河"设计哲学** -- AI 生成内容的质量上限取决于你输入的上下文质量。项目要求用户填充 8 个上下文文件，本质上是在建立一个"品牌知识库"，让 AI 不再泛泛而谈。

3. **从 Castos 内部工具到开源项目** -- 项目最初为 Castos（播客托管 SaaS）内部使用而开发，后来开源。`examples/castos/` 目录保留了完整的真实示例，这让项目具有很强的实用性参考价值。

4. **Agent 自动触发机制** -- 执行 `/write` 后，SEO Optimizer、Meta Creator、Internal Linker、Keyword Mapper 四个 Agent 会自动串行分析内容，无需手动调用，形成"写后即审"的工作流。

5. **反 AI 痕迹设计** -- `/scrub` 命令专门用于去除 AI 写作的水印特征（破折号、填充短语、机械模式），Editor Agent 也提供"人性化评分"，反映了对 AI 内容质量日益增长的关注。

6. **数据驱动的内容策略** -- 通过 GA4、GSC、DataForSEO 的实时数据集成，`/priorities` 和 Performance Agent 能够基于真实流量和排名数据指导内容优先级，而非凭直觉。

---

## 一句话总结

> SEO Machine 是一个将 Claude Code 打造成 SEO 内容工厂的开源工作空间 -- 通过 20+ 自定义命令、10 个专业化 Agent、26 个营销 Skill 和 Python 分析引擎，在品牌上下文的约束下，实现从关键词研究到 WordPress 发布的 SEO 内容全流程自动化。

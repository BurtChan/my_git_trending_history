# AI Design Skills 项目分析

## 项目名称
**AI Design Skills** — 面向 AI 编码工具的设计技能集合，让 Claude Code / Cursor / Codex 等工具按专业设计规范产出高转化落地页
- **GitHub**: [elayadesign/ai-design-skills](https://github.com/elayadesign/ai-design-skills)
- **许可证**: MIT

---

## 项目概述

AI Design Skills 是一个仍在快速成长的设计技能（skills）合集，专门解决一个普遍痛点：AI 编码工具写出的页面「能用但难看、能跑但没转化」。每个 skill 是一个自包含的文件夹，内含一份结构化的 SKILL.md 规则文件，可被任何读取 markdown 规则的 AI 工具消费——Claude Code、Cursor、Codex、Windsurf、Cline，甚至 Claude.ai 网页版（把文件上传到 Project 即可）。

核心 skill `landing-page-design` 把「落地页设计」拆成两大体系：**Part A 策略与结构**（intake 提问清单 → 页面结构 → 布局选型 → 转化规则 → 文案公式 → 构建顺序 → SEO/AEO），**Part B 视觉系统**（字体、间距、圆角、背景、Hero、图标、动效、内容真实感、交互状态、上线检查清单、强制的 tagline reveal 区块）。它不是一个泛泛的「设计建议」，而是一套可直接执行的强约束规则——例如字体只能用 Geist/Manrope/Poppins、禁用 Inter/Roboto、禁用斜体和 900 字重、所有字号必须对齐 Tailwind 字号阶梯、动效必须用 `cubic-bezier(0.22,1,0.36,1)` 曲线且只动画 transform/opacity。

项目创建于 2026 年 7 月底， README 中明确「More on the way」——它是 elayadesign 设计技能生态的入口仓库，姊妹项目 `redesign-skill`（面向存量站点改版）单独成库。三个月内积累 9,000+ stars，单日新增近 1,400，是「AI 工具 + 专业领域方法论」这一赛道（继 awesome-claude-skills 之后）的最新代表。

---

## 核心功能

| 功能 | 描述 |
|---|---|
| Intake 提问清单 | 一次批量收集目的/受众/证据/约束，缺什么就合理假设一行声明并继续，不阻塞构建 |
| 页面结构模板 | 首屏（标题+副标题+CTA+证明+视觉）、中部论证（问题→方案、收益、三步流程、社会证明）、底部（FAQ 6-12 问、风险逆转、最终 CTA） |
| 布局选型 | 四种布局（经典 Hero / 长文故事 / 极简转化页 / 对比页）按流量意图选择并说明理由 |
| 转化与文案规则 | 一 offer 一受众一动作、收益优先、具体数字替代空话（"4 小时降到 15 分钟"而非"省时提效"）、标题公式库 |
| 严格视觉系统 | 批准字体清单 + 禁用清单、Tailwind 字号/间距强制对表、嵌套圆角公式、禁止渐变背景和单侧卡片描边 |
| 动效规范 | 统一减速曲线、仅动画 transform/opacity、导航浮岛式设计、滚动 reveal 用 IntersectionObserver、尊重 prefers-reduced-motion |
| 内容真实感 | 禁止占位拉丁文和"revolutionize/supercharge"式填充词，要求真实文案、可信人名数字、行业化品牌名 |
| 交付检查清单 | hover/active/focus/loading/empty/error 全状态、404、法务链接、表单校验、favicon、og:image 等上线必备项 |

---

## 技术栈

| 组件 | 技术 |
|---|---|
| 载体形式 | 纯 Markdown SKILL.md（无代码依赖），每 skill 一个自包含文件夹 |
| 目标工具 | Claude Code（.claude/skills/）、Cursor（.cursor/rules/）、Codex（AGENTS.md）、Windsurf、Cline、Claude.ai Projects |
| 视觉基准 | Tailwind CSS 默认字号/间距阶梯 |
| 字体体系 | Geist、Manrope、Poppins（正文）+ Geist Mono（代码/数据） |
| 图标库 | Phosphor、Solar、Iconamoon |
| 动效实现 | IntersectionObserver / Framer Motion whileInView，cubic-bezier(0.22,1,0.36,1) 基准曲线 |

---

## 项目亮点

### 把「设计品味」编码成可执行规则
多数 AI 生成页面的失败不是能力问题而是约束缺失——模型默认产出 Inter 字体、紫色渐变、居中卡片的「AI 味」页面。该 skill 用批准/禁用清单 + 数值化规则表（字号必须落在 Tailwind 阶梯、间距查表、圆角按公式嵌套）把专业设计决策压缩成模型可直接遵循的硬约束，输出稳定性远高于「请设计得好看点」式提示。

### Part A/Part B 分层：先想清楚再动手
强制先完成策略层（一个 offer、一个受众、一个主动作；intake 提问；布局选型说明理由）再进入视觉层，杜绝 AI「上来就写代码」的通病。还规定按 Hero→收益→流程→证明→FAQ→CTA 的顺序逐 section 构建，保持每次迭代 diff 可审查。

### 跨工具通用 + 零成本定制
安装只需复制一个文件夹到对应工具的规则目录；所有设计价值观（字体/颜色/间距/动效）集中在文件尾部一个 section，fork 后改一处即全局生效。MIT 许可、无署名要求，可商用。

### 内容真实感规则是稀缺品
市面上设计规范很少覆盖「示例内容可信度」：要求真实草拟文案（禁止 Lorem ipsum）、避免可疑的整数定价、确认消息具体平静（"Invoice sent to Dana"）、报错说清原因和下一步——这些细节正是「模板感」与「产品感」的分界线。

---

## 应用场景

### 独立开发者快速上线营销页
用 Claude Code/Cursor 建 landing page 时挂载此 skill，从文案到视觉系统一步到位，避免「工程师审美」页面拉低转化。intake 清单还能反向帮开发者理清定位。

### 设计系统团队给 AI 协作立规矩
把团队自己的字体/间距/动效规范替换进 skill 的 values section，让 AI 生成的代码天然符合团队规范，减少 review 摩擦。

### AI 编码课程与教程配套
「教 AI 做设计」本身就是极佳的教学素材——规则文件逐条解释了为什么禁用某字体、为什么动效只动画 transform，适合作为 prompt engineering / AI 辅助开发的案例教材。

### 页面改版与设计 review
即使不新建页面，skill 的 Quick checklist（三组共 30+ 检查项）可直接用于存量页面的设计审计；姊妹仓库 redesign-skill 专注存量站点改版场景。

---

## Star 数据

| 指标 | 数值 |
|---|---|
| 总 Stars | 9,157 |
| 总 Forks | 660 |
| 今日新增 | +1,395 stars today |
| Open Issues | 5 |
| 创建时间 | 2026-07-29 |
| 许可证 | MIT |

---

## 总结

把专业落地页设计与转化方法论编码成跨工具通用的 AI 技能规则文件，是「Claude Skills 生态」向垂直专业领域深化的代表项目。

---

*数据来源：GitHub 仓库 (elayadesign/ai-design-skills)，2026 年 10 月 28 日访问*
*首次分析：2026 年 10 月 28 日 | 最近更新：2026 年 10 月 28 日*

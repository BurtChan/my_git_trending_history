# Diagram Design 项目分析

## 项目名称
**Diagram Design** — 让 AI 生成设计师不讨厌的编辑级图表
- **GitHub**: [cathrynlavery/diagram-design](https://github.com/cathrynlavery/diagram-design)
- **许可证**: MIT

---

## 项目概述
Diagram Design 是一个面向 Claude Code 等 AI 编码工具的图表生成 Skill，由 BestSelf.co 创始人 Cathryn Lavery 打造。项目的核心主张是「编辑级图表（Editorial diagrams）——你的设计师不会讨厌的那种」：提供 29 种图表类型，全部输出自包含的 HTML + SVG，无需 Figma、无需构建步骤、无需 JS、无需外部图片，浏览器直接打开即可使用。

项目的出发点是作者本人的痛点：每次需要架构草图、流程图或金字塔图时，让 Claude 生成的都是千篇一律的圆角框示意图，与网站的编辑风格格格不入。要么花 30 分钟在 Figma 里手动调整，要么干脆放弃图表。于是她构建了这个 Skill 库，让 AI 直接产出符合编辑设计规范（统一字体、克制的强调色、精准的间距网格）的高质量图表，并且通过读取你的网站，在 60 秒内把品牌配色和字体映射到每一张图上。

## 核心功能
| 功能 | 描述 |
|------|------|
| 29 种图表类型 | Architecture、Flowchart、Sequence、State machine、ER、Timeline、Swimlane、Quadrant、Nested、Tree、Org chart、Venn、Layers、Pyramid、Consultant 2×2、Radar、Loop、IT current-state、High-Level、Bar/Line chart、Gantt、Scatter plot、Process、Medallion、Data flow、DP integration、DP security matrix 等 |
| 三种变体 | 每种图表都提供 minimal light、minimal dark、full-editorial 三种样式，直接浏览器打开 |
| 品牌化 Onboarding | 读取网站主页提取主色调、字体栈，映射为 paper/ink/muted/accent 语义 token，写入 style-guide.md，60 秒完成品牌适配 |
| 对比度自动检查 | 生成图表时自动做色彩对比度检查，保证可读性 |
| 自包含输出 | 纯 HTML + SVG，无构建步骤、无 JS、无外部图片，截图即用 |
| 多 Agent 生态 | 同一份代码树同时支持 Claude Code（skill + plugin）、Claude Cowork、Codex（npx skills add）三种安装路径 |
| 手绘/终端风格 | SVG turbulence + displacement map 实现手绘变体；terminal/CLI 窗口风格用于技术文档 |
| 图标库 | 55 个单色 IT/云图标（Docker、K8s、AWS、Azure、Postgres 等），currentColor 继承品牌色 |

## 技术栈
| 组件 | 技术 |
|------|------|
| 输出格式 | 自包含 HTML + SVG |
| Skill 框架 | Claude Code Skills（SKILL.md + references 分层加载） |
| 设计系统 | Instrument Serif（标题）+ Geist sans（节点名）+ Geist Mono（技术标注），1px hairline 边框，无阴影，max border-radius 10px |
| 布局规范 | 所有坐标/宽度/间距整除 4（"非卖品"规则，防止 AI 生成感） |
| 图标来源 | Tabler Icons（MIT）+ Simple Icons（CC0），脚本 `scripts/build-icons.py` 重新生成 |
| 手绘效果 | SVG turbulence + displacement map filter |

## 项目亮点
### 分层引用，按需加载
每种图表类型对应一个独立 reference 文件（如 `primitive-sequence.md`），Claude 只读取当前任务需要的那个类型定义，而不是整个技能库。新增图表类型不会影响已有类型的性能，上下文占用被严格限制。

### 设计系统即规范
项目把「不像 AI 生成」变成了一组可执行的硬性规则：单一强调色、每张图最多 1-2 个焦点元素、1px hairline 边框、无阴影、最大圆角 10px、所有尺寸整除 4。珊瑚色焦点节点把读者视线引向最重要的 1-2 个元素，密度目标控制在 4/10——"每个节点都要挣得自己的位置"。

### 品牌即模板
最独特的差异化：不是让用户手动配 30 个变量，而是直接读取网站——背景色变成 paper token、CTA 色变成 accent token、正文字体栈变成节点字体。语义化映射（paper/ink/muted/accent/link）让品牌适配从「调色」升级为「注入设计意图」。

### 克制哲学
README 明确列出何时不该用这个技能：推文用的 unicode 图、任何列表、before/after 对比、单框"图"——画图之前先问"读者从这张图中学到的是否多于一段好文字？" 这种克制让产出质量始终高于平均水平。

## 应用场景
### 技术文档与架构图
架构草图、流程图、时序图、状态机、ER 模型，直接生成符合编辑规范的自包含 HTML，插入文档或截图即用，替代 Mermaid 的"slop"风格。

### 产品与咨询展示
Consultant 2×2 场景矩阵、Pyramid 漏斗、Quadrant 定位图、Org chart 组织架构——面向客户汇报时输出编辑级视觉，而非通用模板感。

### 数据呈现
Bar/Line chart、Gantt、Scatter plot、Radar 蜘蛛图，纯 SVG 无依赖，适合需要嵌入网页或文档的轻量可视化。

### 数据平台治理
Medallion 多层数据存储、Data flow 角色化管道、DP integration 源→核心→消费链路、DP security matrix 按角色权限矩阵——数据工程与合规场景专用图表类型。

## Star 数据
| 指标 | 数值 |
|------|------|
| 总 Stars | 9,620 |
| 总 Forks | 624 |
| 许可证 | MIT |
| 主要语言 | HTML |
| 创建时间 | 2026 年 4 月 |

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 13 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：Diagram Design 热度爆发式增长，Star 数从 6,405 飙升至 9,620（+3,215），Forks 从 420 增至 624（+204），单日增量创历史新高。项目发布 v2.0，新增标志性图型「The Loop」——带共享内存中枢的飞轮图（flywheel），虚线表示写回路径；图型类型从 13 种扩展至 27 种（架构、流程图、时序、ER、泳道、时间线、维恩、组织架构等），并扩展支持 Claude Code、Codex、Pi 三款工具。品牌注入（Brand Onboarding）流程更完善：skill 自动抓取网站主页、提取主色板与字体栈、映射到语义角色（paper/ink/muted/accent/link）、展示 diff 后写入 style-guide.md，后续所有图表自动套用品牌视觉规范；同时支持导入 draw.io 文件并按目标格式/尺寸/细节重绘，产品化程度明显提升。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 6,405 | 9,620 | +3,215 |
| 总 Forks | 420 | 624 | +204 |

**核心变化概要**：
- Star 数 6,405 → 9,620（+3,215），单日涨幅惊人
- v2.0 新增 The Loop 飞轮图 + 共享内存中枢
- 图型类型扩展至 27 种，覆盖 Claude Code / Codex / Pi
- 品牌注入 + draw.io 重绘流程完善，产品化雏形显现


## 总结
Diagram Design 把「编辑级设计规范」编译成 AI 可执行的图表生成规则，用品牌注入 + 严格设计系统解决了 AI 图表"能用但丑"的普遍痛点，是 AI 原生设计工具赛道中思路最清晰的 Skill 项目之一。

---

*数据来源：GitHub 仓库 (cathrynlavery/diagram-design)，2026 年 8 月访问*
*首次分析：2026 年 8 月 | 最近更新：2026 年 8 月 13 日*

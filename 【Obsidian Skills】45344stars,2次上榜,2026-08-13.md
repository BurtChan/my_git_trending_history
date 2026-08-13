# Obsidian Skills 项目分析

- **项目名称**: Obsidian Skills
- **项目地址**: [https://github.com/kepano/obsidian-skills](https://github.com/kepano/obsidian-skills)
- **作者**: @kepano（Obsidian CEO Steph Ango）
- **许可证**: MIT License

---

## 项目概述

Obsidian Skills 是 Obsidian 官方推出的 **AI Agent 技能包**，遵循 Agent Skills 规范，让 AI 编程助手（如 Claude Code、Codex CLI、OpenCode 等）能够正确理解和操作 Obsidian 笔记库的核心格式和功能。它由 Obsidian CEO Steph Ango（@kepano）亲自维护，作为 `.claude-plugin` 格式的插件发布。

项目包含五个独立技能，分别覆盖 Obsidian 的 Markdown 语法、Bases 数据库、JSON Canvas 画布、CLI 命令行操作以及 Defuddle 网页内容提取。每个技能以 `SKILL.md` 文件的形式定义，包含 YAML 元数据头和详细的 Markdown 技能说明文档，可被任何兼容 Agent Skills 规范的 AI 工具自动发现和加载。

---

## 核心功能

### 技能 1: obsidian-markdown（Obsidian 风味 Markdown）

教会 AI 正确创建和编辑 Obsidian 增强的 Markdown 文件（`.md`）。

**覆盖的语法特性：**
- **Wikilinks**: `[[Note Name]]`、`[[Note Name|Display Text]]`、`[[Note Name#Heading]]`、`[[Note Name#^block-id]]`
- **嵌入**: `![[Note Name]]`、`![[image.png|300]]`、`![[document.pdf#page=3]]`
- **Callouts**: `> [!note]`、`> [!warning] Title`、可折叠（`+`/`-`）
- **属性/Frontmatter**: YAML 头部的 `tags`、`aliases`、`cssclasses` 等
- **标签**: `#tag`、`#nested/tag` 层级标签
- **注释**: `%%隐藏文本%%`
- **高亮**: `==高亮文本==`
- **数学公式**: 行内 `$e^{i\pi}$` 和块级 `$$...$$`
- **Mermaid 图表**: 代码块中的 Mermaid 语法
- **脚注**: `[^1]` 和 `^[行内脚注]`

### 技能 2: obsidian-bases（Obsidian 数据库）

教会 AI 创建和编辑 Obsidian Bases 文件（`.base`），这是 Obsidian 的结构化数据视图功能。

**覆盖的功能：**
- **四种视图类型**: table（表格）、cards（卡片）、list（列表）、map（地图）
- **过滤器**: 支持 `==`、`!=`、`>`、`<` 等操作符，支持 `and`/`or`/`not` 逻辑嵌套
- **公式**: 条件逻辑 `if()`、数学运算、日期计算、字符串处理
- **函数库**: 全局函数（`now()`、`today()`、`date()`）、字符串函数（`contains()`、`startsWith()`）、列表函数（`filter()`、`map()`、`reduce()`）、文件函数（`hasTag()`、`inFolder()`）
- **汇总**: 内置 Average、Sum、Min、Max、Median、Stddev、Earliest、Latest 等
- **分组**: `groupBy` 按属性分组，支持 ASC/DESC 排序

### 技能 3: json-canvas（JSON 画布）

教会 AI 创建和编辑 JSON Canvas 文件（`.canvas`），遵循 [JSON Canvas Spec 1.0](https://jsoncanvas.org/spec/1.0/) 开放规范。

**覆盖的元素：**
- **四种节点类型**: `text`（文本+Markdown）、`file`（文件引用）、`link`（外部URL）、`group`（分组容器）
- **边（Edges）**: 连接节点的线条，支持方向（`fromSide`/`toSide`）、端点形状（`arrow`/`none`）、标签和颜色
- **颜色系统**: 6 个预设颜色（`"1"` 到 `"6"`）+ 自定义十六进制颜色（`"#FF0000"`）
- **分组**: 带标签和背景图的容器节点，支持 `cover`/`ratio`/`repeat` 三种背景样式
- **布局规范**: Z-index 排序、推荐尺寸、间距建议、16 字符十六进制 ID 格式

### 技能 4: obsidian-cli（Obsidian 命令行）

教会 AI 通过 `obsidian` CLI 与运行中的 Obsidian 实例交互。

**覆盖的命令：**
- **文件操作**: `read`、`create`、`append`、`search`、`daily:read`、`daily:append`
- **属性管理**: `property:set` 设置笔记属性
- **任务管理**: `tasks daily todo` 管理任务
- **搜索**: `search query="关键词"` 全文搜索
- **标签**: `tags sort=count counts` 统计标签
- **反向链接**: `backlinks file="Note"` 查看反向链接
- **插件开发**: `plugin:reload` 重载插件、`dev:errors` 检查错误、`dev:screenshot` 截图、`dev:dom` 检查 DOM、`eval` 执行 JavaScript

### 技能 5: defuddle（网页内容提取）

教会 AI 使用 Defuddle CLI 从网页中提取干净的 Markdown 内容，去除导航、广告等干扰元素，节省 token 消耗。

**覆盖的功能：**
- `defuddle parse <url> --md` 提取 Markdown
- `defuddle parse <url> -p title` 提取特定元数据
- `defuddle parse <url> --md -o content.md` 保存到文件

---

## 技术栈

| 技术 | 用途 |
|------|------|
| **Markdown** | 技能内容描述文件（SKILL.md） |
| **YAML** | 技能元数据头（name、version、description） |
| **Agent Skills 规范** | 标准化的技能发现和加载协议 |
| **.claude-plugin** | Claude Code 插件分发格式（plugin.json + skills/） |
| **JSON Canvas Spec 1.0** | 开放的画布文件格式规范 |

---

## 安装和加载说明

### 方式 1: Claude Code 插件市场（推荐）

```bash
# 从插件市场添加并安装
/plugin marketplace add kepano/obsidian-skills
/plugin install obsidian@obsidian-skills
```

### 方式 2: npx skills

```bash
npx skills add git@github.com:kepano/obsidian-skills.git
```

### 方式 3: 手动安装 -- Claude Code

将仓库内容添加到 Obsidian 笔记库根目录下的 `.claude` 文件夹中。

### 方式 4: 手动安装 -- Codex CLI

将 `skills/` 目录复制到 Codex 技能路径（通常为 `~/.codex/skills`）。

### 方式 5: 手动安装 -- OpenCode

克隆整个仓库到 OpenCode 技能目录：

```bash
git clone https://github.com/kepano/obsidian-skills.git ~/.opencode/skills/obsidian-skills
```

目录结构应为 `~/.opencode/skills/obsidian-skills/skills/<skill-name>/SKILL.md`。OpenCode 会自动发现所有 `SKILL.md` 文件，无需额外配置。

---

## 技能文件的具体结构和格式

每个技能遵循标准的目录结构：

```
obsidian-skills/
├── .claude-plugin/
│   └── plugin.json          # 插件元数据
├── skills/
│   ├── obsidian-markdown/
│   │   ├── SKILL.md          # 技能主文件
│   │   └── references/       # 参考文档
│   │       ├── CALLOUTS.md
│   │       ├── EMBEDS.md
│   │       └── PROPERTIES.md
│   ├── obsidian-bases/
│   │   └── SKILL.md
│   ├── json-canvas/
│   │   └── SKILL.md
│   ├── obsidian-cli/
│   │   └── SKILL.md
│   └── defuddle/
│       └── SKILL.md
├── LICENSE
└── README.md
```

每个 `SKILL.md` 文件格式如下：

```markdown
---
name: skill-name
version: "1.0.0"
description: 技能描述和使用触发条件
---

# 技能标题

技能的详细说明文档，包含语法参考、
代码示例、验证规则等完整内容。
```

YAML 头部的 `name` 是技能标识符，`description` 用于 AI 决定何时激活该技能。

---

## 与 Claude Code 技能系统的关系

Obsidian Skills 是 Claude Code **Agent Skills 规范** 的官方示范实现：

1. **规范兼容**: 遵循 Agent Skills 标准格式（`skills/<name>/SKILL.md`），可被任何兼容规范的 AI 工具加载
2. **多工具支持**: 不仅限于 Claude Code，还支持 Codex CLI、OpenCode、ClawdBot、OpenClaw 等工具
3. **插件分发**: 通过 `.claude-plugin/plugin.json` 作为 Claude Code 插件分发，支持 `/plugin marketplace add` 一键安装
4. **自动发现**: AI 工具根据 `SKILL.md` 中的 `description` 字段自动判断何时激活对应技能
5. **引用系统**: `obsidian-markdown` 技能通过 `references/` 子目录组织补充文档（CALLOUTS.md、EMBEDS.md、PROPERTIES.md），展示技能文件的模块化组织方式

---

## 项目亮点

1. **Obsidian 官方出品**: 由 CEO Steph Ango 亲自维护，确保技能内容与 Obsidian 功能完全同步
2. **规范示范**: 作为 Agent Skills 规范的参考实现，展示了技能文件的标准结构和最佳实践
3. **五个核心技能全覆盖**: Markdown 语法、Bases 数据库、Canvas 画布、CLI 命令行、网页内容提取
4. **多工具兼容**: 支持任何兼容 Agent Skills 规范的 AI 工具，不绑定单一平台
5. **极简无依赖**: 纯 Markdown/YAML 文件，无代码执行，无外部依赖，安全可靠

---

## 应用场景

### AI 辅助笔记管理
让 AI 正确创建和编辑 Obsidian 笔记，使用正确的 wikilink 语法、属性格式和嵌入语法，避免格式错误导致的功能异常。

### 知识库自动化
用 AI Agent 批量整理和管理笔记库。例如批量添加标签、更新属性、重组文件夹结构，所有操作都遵循 Obsidian 规范。

### Canvas 画布操作
让 AI 生成思维导图、流程图、项目看板等画布文件。AI 知道正确的 JSON Canvas 格式，生成的 `.canvas` 文件可以直接在 Obsidian 中打开使用。

### 数据库视图创建
让 AI 创建 Bases 数据库视图，用于任务追踪、阅读清单、项目笔记索引等场景。AI 掌握完整的过滤器、公式和函数语法。

### 插件开发调试
通过 obsidian-cli 技能，AI 可以直接与运行中的 Obsidian 交互，执行插件重载、错误检查、DOM 检查等开发调试操作。

---

## Star 数据

| 指标 | 数据 |
|------|------|
| **总 Star 数** | 45,344 |
| **Fork 数** | 3,280 |
| **Watch 数** | 34 |
| **Open Issues** | 6 |
| **创建时间** | 2026-01-02 |
| **最近更新** | 2026-01-10 |
| **许可证** | MIT |
| **提交数** | 37 |

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 13 日（再次登上 Trending）

**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：kepano/obsidian-skills 时隔四个月再次登上 GitHub Trending，Star 数从 4 月的 4,188 暴增至 45,344（+41,156），Fork 数从 178 增至 3,280。作为 Obsidian CEO Steph Ango 亲自维护的官方 Agent 技能包，该项目在 2026 年 Agent Skills 浪潮中成为标杆——五个核心技能（Markdown 语法、Bases、JSON Canvas、CLI、Defuddle）自发布起就遵循标准 SKILL.md 规范，在 Claude Code、Codex CLI、OpenCode 等 Agent 工具中自动发现与加载，社区涌现大量二次开发与教程。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 4,188 | 45,344 | +41,156 |
| 总 Forks | 178 | 3,280 | +3,102 |

**核心变化概要**：
- Star 数增长逾 10 倍，突破 45K，成为技能生态顶流项目
- 官方 Agent 技能规范标杆地位确立，生态大量跟进
- 与 Claude Code、Codex 等工具的集成路径成为社区标配


---

## 总结

Obsidian Skills 是 Obsidian 官方推出的 AI Agent 技能包，由 CEO Steph Ango 亲自维护。它包含五个核心技能，分别覆盖 Obsidian 的 Markdown 语法、Bases 数据库、JSON Canvas 画布、CLI 命令行操作和 Defuddle 网页内容提取。项目遵循 Agent Skills 规范，以标准化的 `SKILL.md` 文件格式组织，支持 Claude Code、Codex CLI、OpenCode 等多种 AI 工具自动发现和加载。每个技能文件都包含完整的语法参考、代码示例和验证规则，确保 AI 能正确理解和操作 Obsidian 的所有核心功能。对于使用 Obsidian 并希望借助 AI 辅助管理笔记库的用户，这是一个必不可少的技能包。

*数据来源：GitHub 仓库 (kepano/obsidian-skills)，2026 年 8 月访问*
*首次分析：见文件头部 | 最近更新：2026 年 8 月 13 日*

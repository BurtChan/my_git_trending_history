# Obsidian Skills 项目分析

> **Obsidian 的 Agent 技能系统** — 教 AI Agent 使用 Markdown、Bases、JSON Canvas 和 CLI 的技能包。

- **GitHub**: [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills)
- **Stars**: 20,545 | **今日新增**: 429
- **Forks**: 1,273
- **作者**: @kepano（Obsidian CEO Steph Ango）

---

## 项目定位

Obsidian Skills 是 Obsidian 官方推出的 **AI Agent 技能系统**，让 AI 编程助手（如 Claude Code、Cursor 等）能更好地理解和操作 Obsidian 笔记库。它教会 AI Agent 如何正确使用 Obsidian 的核心格式和功能。

---

## 解决什么问题

AI Agent 在处理 Obsidian 笔记库时，不了解 Obsidian 特有的格式和约定：
- **Markdown 扩展**: Obsidian 的链接语法 `[[wikilink]]`、标签、属性等
- **Bases**: Obsidian 的数据库功能
- **JSON Canvas**: Obsidian 的画布文件格式
- **CLI 操作**: 命令行交互方式

Obsidian Skills 作为"技能包"注入 AI Agent，让它们成为 Obsidian 专家。

---

## 核心技能

| 技能 | 说明 |
|------|------|
| **Markdown** | Obsidian 增强的 Markdown 语法（wikilink、callout、属性等） |
| **Bases** | Obsidian 数据库/表格功能的正确使用 |
| **JSON Canvas** | 画布文件（.canvas）的读写和操作 |
| **CLI** | 通过命令行与 Obsidian 交互 |

---

## 技术栈

- **格式**: 技能描述文件（Markdown / YAML）
- **集成方式**: Agent Skills 规范，可被 Claude Code、Cursor 等 AI 工具加载
- **作者**: Obsidian CEO 亲自维护

---

## 适用场景

| 场景 | 说明 |
|------|------|
| **AI 辅助笔记** | 让 AI 正确创建和编辑 Obsidian 笔记 |
| **知识库自动化** | 用 AI Agent 批量整理和管理笔记库 |
| **Canvas 操作** | AI 生成和修改画布文件 |
| **数据管理** | AI 操作 Bases 数据库 |

---

## 一句话总结

> Obsidian Skills 是 Obsidian 官方推出的 **AI Agent 技能包**，20k+ Stars，由 CEO 亲自维护，教会 AI 助手正确使用 Markdown、Bases、JSON Canvas 等 Obsidian 核心功能。

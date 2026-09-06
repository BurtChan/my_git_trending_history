# OpenAI Skills 项目分析

## 项目名称
**OpenAI Skills** — OpenAI 官方的 Codex 技能（Agent Skills）目录仓库：以「文件夹即技能」的形式为 AI 智能体打包可复用能力，一次编写、处处可用
- **GitHub**: [openai/skills](https://github.com/openai/skills)
- **许可证**: 各技能目录内含独立 LICENSE.txt（仓库级无统一许可证）

---

## 项目概述
openai/skills 是 OpenAI 官方维护的 **Skills Catalog for Codex**——Codex 智能体的技能目录仓库。所谓 Agent Skills，是指令（instructions）、脚本（scripts）与资源（resources）组成的文件夹，AI 智能体可以自动发现并调用它们去完成特定任务，实现「一次编写、处处使用」（write once, use everywhere）。这一机制遵循 agentskills.io 的开放标准，是 2025 年以来 Agent Skills 生态（Anthropic、Google、社区技能库先后爆发）在 OpenAI 阵营的官方落子。

仓库创建于 2025 年 11 月，共 114 次提交。技能按三层目录组织：`.system`（Codex 最新版自动内置）、`.curated`（官方精选，可按名安装）、`.experimental`（实验性技能，需指定目录安装）。安装方式统一通过 Codex 内置的 `$skill-installer` 命令完成，支持按名安装、按目录安装或直接给 GitHub 目录 URL 安装，安装后重启 Codex 即生效。

值得注意的是，仓库首页已标注 **deprecated（已弃用）**：当前 Codex 技能与插件示例已迁移至 openai/plugins 仓库，自定义技能请按官方 Build plugins 指南构建 skill-only 插件。因此本项目更接近一个「历史里程碑 + 生态引爆点」——它是 Agent Skills 浪潮中 OpenAI 的起点仓库，即便已宣布弃用仍在持续吸星（当前 25.5K stars、1.7K forks，今日 +44），说明社区对官方技能目录的高度关注。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 技能目录 | `.system`（自动内置）、`.curated`（官方精选）、`.experimental`（实验性）三层组织 |
| $skill-installer | Codex 内置安装器，支持按名/按目录/按 GitHub URL 三种安装方式 |
| gh-address-comments 等精选技能 | 官方精选技能可 `$skill-installer gh-address-comments` 一键安装 |
| create-plan 等实验技能 | 实验性技能从 `.experimental` 文件夹指定安装 |
| 开放标准对齐 | 遵循 agentskills.io 的 Agent Skills 开放标准 |
| 贡献机制 | contributing.md 规范社区技能提交流程 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 技能载体 | Markdown 指令 + 脚本 + 资源的文件夹结构 |
| 运行环境 | OpenAI Codex CLI / IDE 集成 |
| 安装通道 | $skill-installer（Codex 内置） |
| 标准协议 | agentskills.io Agent Skills 开放标准 |
| 语言 | Python（主语言） |

---

## 项目亮点

### 官方背书的技能生态起点
作为 OpenAI 官方仓库，它是 Codex 技能生态的规范制定者与首发目录。虽然已宣布迁移到 openai/plugins，但其三层目录结构（system/curated/experimental）与安装器交互范式被后续生态广泛沿用。

### 「文件夹即技能」的极简哲学
技能不需要注册中心、不需要包管理器，就是一个含指令与脚本的文件夹——这与 Claude Skills、agentskills.io 开放标准完全同构，跨厂商通用。

### 弃用后仍在增长的星标曲线
25.5K stars / 1.7K forks / 138 watchers，即便 README 顶部挂着 deprecated 警告仍在吸星，反映出 Agent Skills 是当前 AI 工具生态最热的赛道之一，官方动作天然自带流量。

---

## 应用场景

### Codex 用户扩展智能体能力
安装官方精选技能（如 gh-address-comments）让 Codex 获得处理 PR 评论、规划任务等专项能力，无需自行编写提示词工程。

### 技能开发者学习官方范式
研究 `.curated` 与 `.experimental` 目录中官方技能的写法（指令组织、脚本封装、LICENSE 规范），是开发自定义 skill-only 插件的最佳参考。

### 跨生态技能标准研究者
对齐 agentskills.io 开放标准，可与 Anthropic Skills、Google Skills 等横向对比，理解「技能」作为 Agent 生态通用原语的演进路径。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 25,548 |
| 🍴 Forks | 1,726 |
| 📈 今日新增 | 44 stars |
| 💬 主要语言 | Python |
| 📅 创建时间 | 2025-11-25 |

---

## 总结
OpenAI 官方 Codex 技能目录仓库，Agent Skills 浪潮在 OpenAI 阵营的起点；虽已宣布迁移至 openai/plugins，仍是理解官方技能组织范式与生态演进的关键样本。

---

*数据来源：GitHub 仓库 (openai/skills)，2026 年 9 月访问*

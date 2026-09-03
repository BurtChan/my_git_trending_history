# Prompts.chat 项目分析

## 项目名称
**Prompts.chat** — 全球最大的开源 AI Prompt 库（前身为 Awesome ChatGPT Prompts），社区共建、可自托管
- **GitHub**: [f/prompts.chat](https://github.com/f/prompts.chat)
- **许可证**: 双许可（代码 MIT / Prompt 内容 CC0 1.0 公共领域）
- **网站**: [prompts.chat](https://prompts.chat)

---

## 项目概述
prompts.chat 是由 Fatih Kadir Akın（f）维护的社区 Prompt 库，前身为广为人知的 Awesome ChatGPT Prompts——ChatGPT 爆发初期（2023 年）最著名的提示词集合，曾登上 GitHub Trending 榜首并被 Forbes 报道、Harvard 与 Columbia 的 AI 指南引用，Google Scholar 收录 40+ 学术引用，其数据集是 Hugging Face 上最多点赞的数据集之一。

项目如今已从「一个 README 列表」进化为完整的 Web 平台 + 生态：用户可以在 prompts.chat 网站上浏览、搜索、发现和收藏适用于 ChatGPT、Claude、Gemini、Llama、Mistral 等主流模型的 Prompt；支持组织级自托管（Docker Compose 一键部署，数据完全私有）；提供 MCP Server（远程 URL 或本地 npx 两种接入方式），可以把整个 Prompt 库作为工具接入任意支持 MCP 的 AI 客户端；还发布了配套电子书《The Art of ChatGPT Prompting》。

仓库技术栈为 Next.js + Prisma + TypeScript 的全栈 Monorepo，Prompt 数据以 prompts.csv / PROMPTS.md 双格式维护，贡献者通过标准 PR 流程提交。今日新增 198 星（总量 168,681），作为运营三年多的「常青树」项目仍保持活跃社区输入。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| Prompt 浏览与搜索 | prompts.chat 网站按角色/场景分类浏览，支持多模型通用 |
| 社区共建 | 8,100+ commits、数千贡献者通过 PR 提交新 Prompt |
| 自托管 | Docker Compose 部署，组织内部私有使用，零数据外泄 |
| MCP Server | 远程（https://prompts.chat/api/mcp）或本地（npx prompts.chat mcp）接入 AI 工具 |
| 数据集下载 | Hugging Face 数据集（fka/prompts.chat）+ CSV/Markdown 原始格式 |
| Claude 插件 | 内置 .claude-plugin 与 .windsurf/skills 适配 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 前端/全栈 | Next.js + TypeScript + MDX |
| 数据层 | Prisma ORM |
| 部署 | Docker Compose / Vercel |
| 监控 | Sentry（edge/server 双配置） |
| 测试 | Vitest |
| 许可证 | 代码 MIT + 内容 CC0 双许可 |

---

## 项目亮点

### 常青树级社区资产
三年多历史、167K+ Stars、21.6K Forks、8,100+ commits，是被学术引用和媒体引用最多的 Prompt 资源，几乎见证了整个 Prompt Engineering 学科的发展史。

### 从列表到平台的演进
多数 awesome-list 停留在 README 形态，prompts.chat 完成了产品化： searchable Web 平台、自托管、MCP 协议接入、Claude/Windsurf 插件适配，持续跟进 AI 工具生态的每个新标准。

### 内容彻底开放
Prompt 内容以 CC0 1.0 公共领域发布，无任何使用限制；代码 MIT，商用与二次分发均无障碍。

---

## 应用场景

### Prompt 工程学习入门
通过分类角色 Prompt（翻译、面试官、写作助手等）快速理解提示词结构与角色设定模式。

### 组织内部 Prompt 资产库
企业自托管后作为团队共享的 Prompt 知识库，沉淀业务提示词且不经过第三方云。

### AI 工具的 Prompt 数据源
通过 MCP Server 把整个库接入 Claude Code、Cursor 等工具，让 Agent 按需检索社区验证过的 Prompt。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 168,883 |
| 总 Forks | 21,758 |
| 今日新增 | 201 stars |
| 提交数 | 8,165 |

---

## 总结
prompts.chat 是 Prompt Engineering 领域的奠基级开源资产——从 Awesome ChatGPT Prompts 进化为带自托管与 MCP 接入的完整平台，168K Stars 的社区规模与 CC0 内容许可使其成为该领域事实上的标准参考库。

---

## 📋 更新记录

### 更新 1 — 2026 年 9 月 4 日（再次登上 Trending）

**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：Prompts.chat（原 Awesome ChatGPT Prompts）连续第二日登上 Trending，单日 +202 星，总星数达到 16.89 万。作为运营三年多的常青树项目，其从静态清单进化为带自托管与 MCP 接入的完整 Prompt 平台后热度不减，社区 PR 输入保持活跃（pushed 2026-09-03），CC0 许可的开放内容生态仍是核心护城河。

**最新 Star 数据**：

| 总 Stars | 168,681 | 168,883 | +202 |
| 总 Forks | 21,600 | 21,758 | +158 |

**核心变化概要**：
- Star 数 168,681 → 168,883（+202），连续第 2 日在榜
- Forks 21,600 → 21,758（+158），社区贡献活跃
- 常青树项目平台化转型后热度延续
- CC0 开放许可 + MCP 接入构成核心护城河


*数据来源：GitHub 仓库 (f/prompts.chat)，2026 年 9 月访问*
*首次分析：见文件头部 | 最近更新：2026 年 9 月 4 日*

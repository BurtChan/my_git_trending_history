# Generative AI for Beginners 项目分析

## 项目名称
**Generative AI for Beginners** — 微软出品 21 课生成式 AI 入门课程，从零开始构建 AI 应用
- **GitHub**: [microsoft/generative-ai-for-beginners](https://github.com/microsoft/generative-ai-for-beginners)
- **许可证**: MIT

---

## 项目概述
微软云倡导者团队打造的生成式 AI 入门课程，第三版共 21 节课，覆盖从 LLM 基本原理到 RAG、智能体、微调、小语言模型等前沿话题。课程分为「学习」和「构建」两种类型，每节课均提供 Python 和 TypeScript 双语言代码示例，支持 Azure OpenAI、OpenAI API、Microsoft Foundry Models 和完全离线的 Foundry Local 四种平台。

该项目是微软 for Beginners 系列课程中人气最高的一个，全球超过 11 万颗 Star，GitHub 官方推荐的 AI 学习资源之一。课程内容持续更新，已涵盖 Mistral 和 Meta 模型家族的使用方法。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 21 节完整课程 | 从 LLM 入门到 Agent 框架、微调、SLM 全流程 |
| 双语言代码示例 | 每节课均提供 Python + TypeScript 实践 |
| 多平台支持 | Azure OpenAI、OpenAI API、Foundry Models、离线 Foundry Local |
| 50+ 语言翻译 | 通过 GitHub Actions 自动翻译，覆盖中英日韩等主流语言 |
| RAG 与向量数据库 | 第 15 课深入讲解 RAG 框架与向量嵌入 |
| AI Agent 开发 | 第 17 课手把手构建 AI Agent 应用 |
| 提示工程进阶 | 第 4-5 课从基础到高级提示词技巧 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | Python, TypeScript |
| AI 平台 | Azure OpenAI, OpenAI API, Microsoft Foundry |
| LLM | GPT 系列, Mistral, Meta LLaMA |
| 向量数据库 | 多种（RAG 课中演示） |
| 嵌入模型 | Hugging Face 开源模型 |
| 离线运行 | Foundry Local |

---

## 项目亮点

### 微软官方权威课程
由微软云倡导者团队精心编写，内容质量高且紧跟 AI 技术发展前沿。课程结构从理论到实践循序渐进，适合零基础开发者快速入门。

### 多平台灵活切换
不绑定单一云服务商，开发者可以根据自身情况选择 Azure OpenAI、OpenAI API 或完全离线的 Foundry Local，降低学习门槛。

### 超大规模社区
11 万+ Star 和 6 万+ Fork，GitHub Actions 自动化翻译支持 50+ 语言，形成了一个活跃的全球学习社区。

### 完整的 AI 应用开发生命周期
从提示工程、文本生成、聊天应用、图像生成、RAG 到 AI Agent 和模型微调，覆盖了生成式 AI 应用开发的完整链路。

---

## 应用场景

### 开发者 AI 入门
适合有基础编程能力但尚未接触 AI 的开发者，21 节课构成完整学习路径，学完即可独立开发 AI 应用。

### 企业内部培训
企业可 fork 仓库作为内部 AI 培训教材，MIT 许可证允许自由修改和分发。

### 教学参考
高校和培训机构可将课程作为 AI 课程的教学大纲参考，每节课的代码示例可直接用于实验课。

### 技术栈选型参考
课程涵盖多种 AI 平台和工具的对比，帮助开发团队做出合理的技术选型决策。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 113,915 |
| 🍴 Forks | 61,175 |
| 📝 语言 | Jupyter Notebook |
| 📅 创建时间 | 2023-06-19 |

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 2 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单，Stars 从 113,915 增长至 114,160（+245）

**最新动态**：
微软 Generative AI for Beginners（Version 3）课程在 2026 年 7 月持续活跃，提供 21 节课的生成式 AI 应用开发教学。课程内容涵盖 LLM 介绍、Prompt 工程、文本/图像生成、向量数据库与 RAG、AI Agents、模型微调、小语言模型（SLM）以及 Mistral 和 Meta 模型等前沿主题。每节课都提供 Python 和 TypeScript 双语言代码示例。

2026 年 7 月，微软在 AI 平台层面推出多项重要更新：Azure OpenAI 支持Anthropic Claude 模型（包括 Claude Fable 5），GitHub Models 将于 2026 年 7 月底退役并迁移到 Microsoft Foundry Models，Foundry Local 支持完全离线运行模型。课程已相应更新 API 配置指引，引导学习者使用 Foundry Models 替代即将退役的 GitHub Models。微软还发布了 MAI thinking one（35B 活跃参数的 MoE 推理模型）和 MAI image 2.5 图像生成模型，这些新模型均可通过 Foundry 平台使用。

课程已翻译为 50+ 语言，通过 GitHub Actions 自动化保持同步更新。近 7 天新增 245 颗星，总星标已突破 114,000，稳居 GitHub 全站最受关注的教育类仓库之一。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 113,915 | 114,160 | +245 |
| 总 Forks | 61,211 | 61,211 | +0 |

**核心变化概要**：
- 课程更新 API 配置指引，适配 GitHub Models 迁移至 Foundry Models
- Azure OpenAI 新增 Anthropic Claude 模型支持
- Foundry Local 支持完全离线运行，降低学习门槛
- 21 节课覆盖 RAG、AI Agents、微调、SLM 等前沿主题
- 50+ 语言翻译通过 GitHub Actions 自动化同步

### 更新 5 — 2026年8月4日（再次登上 Trending）

**最新 Star 数据**：

| 总 Stars | 115,494 | 115,829 | +335 |

- Star 数从 115,494 增至 115,829（+335），日增 775 颗 Star

**更新原因**：项目再次登上 GitHub Trending 榜单，Star 数从 115,494 增长至 115,829（+335），日增 775 颗 Star

Star 增长 335 颗，日增 775 颗（Trending）。21 Lessons, Get Started Building with Generative AI 

> 更新依据：GitHub Trending 2026-08-04 数据，Star 数由 GitHub API 实时获取

---

### 更新 2 — 2026 年 8 月 3 日（第三次登上 Trending）

**更新原因**：Star 日增 588，连续两天登上 Trending 榜单，暑期 AI 学习热度持续攀升，社区关注度稳步上升。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 114,160 | 114,656 | +496 |
| 总 Forks | 61,211 | 61,275 | +64 |

**更新亮点**：
- 连续两天登上 Trending 榜单，日增 Star 从 245 提升至 588，增长势头明显加速
- Generative AI for Beginners .NET Version 2 近期发布，基于 .NET 10 和 Microsoft.Extensions.AI 全面重构
- GitHub Models 已正式退役，课程完全迁移至 Microsoft Foundry Models 平台
- Foundry Local 离线模型支持降低学习门槛，推动更多开发者参与
- 课程持续覆盖 AI Agents、MAI 推理模型等前沿主题，保持内容时效性


### 更新 3 — 2026年8月3日（晚间数据）

**更新原因**：连续 Trending，Star 数从 114,656 增长至 115,164（+508），生成式 AI 入门课程赛道持续火热

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 114,656 | 115,164 | +508 |
| 总 Forks | 61,275 | 61,371 | +96 |

**更新亮点**：
- 连续 Trending 推动 Star 突破 115,000 大关，累计增星超 2,000（从 113,000 到 115,164）
- 课程持续覆盖 AI Agents、MAI 推理模型等前沿主题，保持内容时效性
- GitHub Models 已正式退役，课程完全迁移至 Microsoft Foundry Models 平台
- Generative AI for Beginners .NET Edition 基于 .NET 10 持续更新
- 21 节课完整结构（Learn + Build 双模式）+ Python/TypeScript 双语言代码示例

---

---

## 总结
微软出品的生成式 AI 入门旗舰课程，以 21 节课的完整结构和双语言代码示例，为开发者提供了从理论到实践的全方位学习路径，全球 11 万+ Star 证明了其作为 AI 学习首选资源的地位。

---

*数据来源：GitHub 仓库 (microsoft/generative-ai-for-beginners)，2026 年 08 月访问*
*首次分析：2026 年 08 月*

### 更新 4 — 2026年8月4日（连续上榜）

**更新原因**：项目再次登上 GitHub Trending 榜单，Star 数从 115,164 增长至 115,436（+272），日增 776 颗 Star

| 总 Stars | 115,164 | 115,436 | +272 |

**更新亮点**：
Star 增长 272 颗，日增 776 颗（Trending Top3），连续三日上榜。微软生成式 AI 入门课程 V3 持续更新，新增 Foundry Models 平台支持（取代即将退役的 GitHub Models），涵盖 RAG、向量数据库、AI Agents、微调等前沿主题。21 节课程、60+ 语言翻译、Python/TypeScript 双代码示例，是 GitHub 上最受欢迎的 AI 学习资源之一（115K+ Stars）。

> 更新依据：GitHub Trending 2026-08-04 数据，Star 数由 GitHub API 实时获取

---

## 更新 5 — 2026年8月4日（晚间数据）

**更新原因**：连续多日 Trending，晚间数据确认 Star 从 115,436 增长至 115,494（+58），生成式 AI 入门课程赛道持续火热

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 115,436 | 115,494 | +58 |
| 总 Forks | 61,371 | 61,430 | +59 |

**更新亮点**：
- 连续多日 Trending 推动 Star 突破 115,490，累计从 113,915 增长至 115,494（+1,579）
- GitHub Models 已正式退役，课程完全迁移至 Microsoft Foundry Models 平台
- 21 节课完整结构（Learn + Build 双模式）+ Python/TypeScript 双语言代码示例
- Foundry Local 离线模型支持降低学习门槛，推动更多开发者参与
- 60+ 语言翻译通过 GitHub Actions 自动化同步，全球影响力持续扩大

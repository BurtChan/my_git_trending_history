# AI Engineering From Scratch 项目分析

## 项目名称

**AI Engineering From Scratch** — 从零到生产级 AI 工程的完整免费课程体系

- **GitHub**: [rohitg00/ai-engineering-from-scratch](https://github.com/rohitg00/ai-engineering-from-scratch)
- **许可证**: MIT

---

## 项目概述

AI Engineering From Scratch 是一个**全面、免费、开源的 AI 工程课程**，由 AI 基础设施工程师 Rohit Ghumare 创建。项目的核心理念是 **"Build, Don't Import"（构建而非引入）**——从原始数学开始实现每一个算法，不依赖任何魔法封装库。学生需要自己手写反向传播、分词器和注意力机制。

项目包含 **428 节动手实践课程**，跨越 **20 个阶段**，总时长约 **290-320 小时**。课程从数学基础（微积分、线性代数、概率论）一路覆盖到机器学习、深度学习、Transformer、大语言模型、Agent 工程、多智能体系统，直到最终的生产级部署。每节课都产出可复用的成果物：一个 prompt、一个 skill、一个 agent 或一个 MCP 服务器。

项目的数据令人深思："84% 的学生已经在使用 AI 工具，但只有 18% 觉得自己准备好在专业环境中使用它们。这个课程就是来弥合这个鸿沟的。"

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **428 节动手课程** | 覆盖 AI 工程全链路，从数学到生产部署 |
| **20 个结构化阶段** | 线性递进式学习，每阶段聚焦一个领域 |
| **4 种编程语言** | Python、TypeScript、Rust、Julia |
| **从零实现** | 每个算法从原始数学开始，先手写后引入生产库 |
| **可复用成果物** | 每节课产出可实际使用的工具或组件 |
| **内置评估工具** | `/find-your-level` 和 `/check-understanding` 自测工具 |
| **AI 术语表** | 解释行业术语——"人们说的 vs 实际含义" |
| **毕业项目** | 第 18/19 阶段：构建完整的生产级 AI 系统 |
| **SkillKit 集成** | 兼容 Claude、Cursor、Codex、Copilot 等 40+ 工具 |
| **完全免费开源** | 无付费墙、无需注册、无门槛限制 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要语言** | Python、TypeScript、Rust、Julia |
| **深度学习** | PyTorch |
| **机器学习** | scikit-learn |
| **多智能体** | CrewAI |
| **LLM 接入** | Claude、OpenAI CUA、Gemini |
| **容器编排** | Kubernetes（通过 kubectl-mcp-server） |
| **协议** | MCP（Model Context Protocol）、A2A（Agent-to-Agent） |
| **模型库** | Hugging Face Transformers |

---

## 项目亮点

### 1. "构建而非引入"哲学
每个算法从原始数学推导开始实现，先理解原理再引入生产级库。Reddit 社区评价："有一种学 AI 的方式是 import transformers，调用 .fit()，然后觉得自己很高效。然后还有这种方式。"

### 2. 业界最全面的免费 AI 课程之一
428 节课、320 小时内容、20 个结构化阶段，从零数学基础到构建生产级 AI 系统，覆盖范围极其广泛。

### 3. Agent 工程深度覆盖
仅 Agent 工程一个阶段就有 42 节课，涵盖 Reflexion、Voyager、CrewAI、Computer Use、A2A Protocol、运行时反馈循环等前沿话题。

### 4. 多语言支持
不局限于 Python，同时涵盖 TypeScript、Rust 和 Julia，让学习者具备多语言 AI 开发能力。

---

## 应用场景

### 自学 AI 工程
适合想从数学基础到生产部署全链路系统学习 AI 工程的自学者，结构化的 20 阶段路径提供清晰的学习路线图。

### 学生技能提升
帮助学生弥合"使用 AI 工具"和"专业 AI 开发能力"之间的鸿沟，从理论到实践全面覆盖。

### 开发者转型 AI 领域
为想从传统开发转型 AI 工程的程序员提供深度学习路径，不只是调 API，而是真正理解底层原理。

### 团队培训与企业内训
企业可用于 AI 团队的能力建设，内置的评估工具方便追踪学习进度。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 48,752 |
| **总 Forks** | 8,545 |
| **今日新增 Stars** | +688/日 |
| **许可证** | MIT |
| **创建时间** | 2025 年 |
| **主要语言** | Python、TypeScript、Rust、Julia |

---


---

## 📋 更新记录

### 更新 1 — 2026 年 7 月 23 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：

AI Engineering From Scratch 在过去数月经历了爆发式增长，Stars 从约 8,000 飙升至 42,000+（增长超过 5 倍），成为 GitHub 上最受欢迎的免费 AI 教程项目之一。课程内容从最初的 428 节大幅扩展至 **503 节**，新增了多个重要阶段：Phase 15（Autonomous Systems，自主系统 22 节课）和 Phase 16（Multi-Agent & Swarms，多智能体与群体智能 25 节课）等前沿内容。官网 aiengineeringfromscratch.com 月活读者突破 15 万，页面浏览量超 24 万（截至 2026 年 6 月数据）。

项目在 Claude Code 和 Cursor 生态中获得了广泛采用——每节课都产出可复用的 Skill 成果物，可通过 `npx skills add rohitg00/ai-engineering-from-scratch` 一键安装为 Claude Code / Cursor / Codex 的 Skills。这种「课程即工具链」的设计使学习者不仅获得知识，还构建了完整的 AI 工程工具库。Prism Labs 等技术媒体专门制作了视频介绍，进一步推动了项目的传播。课程的核心统计数据也从 428 节/290 小时更新为 **503 节/~320 小时**，覆盖范围从数学基础延伸到生产级 AI 系统部署的全链路。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 8,000 | 42,265 | +34,265 |
| 总 Forks | — | 7,041 | — |

**核心变化概要**：
- 今日新增 652 个 Stars，持续登上 Trending 榜单
---

### 更新 2 — 2026 年 8 月 24 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
- 自 7 月 23 日上次更新以来，Star 从 42,265 增长至 48,064（+5,799），一个月增长 13.7%，教学类项目中增速稳定。
- 课程主题版图完整浮现：AI agents、MCP、强化学习、计算机视觉、transformers、群体智能、深度学习与机器学习基础全覆盖，配合 Python + Rust + TypeScript 多语言实战路线（官方口号「Learn it. Build it. Ship it for others.」）。
- 仓库保持每周更新节奏（最近推送 2026-08-23），MIT 许可证，适合作为系统化 AI 工程学习的主线教材。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 42,265 | 48,064 | +5,799 |
| 总 Forks | 7,041 | 8,476 | +1,435 |

**核心变化概要**：
- Star 从 42,265 增至 48,064（+5,799），一个月增长 13.7%
- 课程覆盖面进一步明确：agents、MCP、强化学习、计算机视觉、transformers、群体智能全栈主题
- Python + Rust + TypeScript 多语言实战路线，教学仓库保持每周更新节奏

---

### 更新 3 — 2026 年 8 月 26 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：AI Engineering From Scratch 连续第三天在榜，Star 单日 +688（48,064 → 48,752）。428 节动手课程 + 20 个结构化阶段的「Build, Don't Import」免费课程持续被自学者收藏，9 月开学/秋招季前夕学习型仓库需求上行，该课程已成本轮 AI 工程自学浪潮的标杆资源之一。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 48,064 | 48,752 | +688 |
| 总 Forks | 8,545 | 8,545 | +0 |

**核心变化概要**：
- Star 单日 +688，逼近 4.9 万
- 连续第三日在榜，学习型仓库需求上行
- 主表历史估算值（8,000+）已修正为精确值


---

## 总结

AI Engineering From Scratch 是**目前最全面的免费 AI 工程开源课程之一**，8k+ Stars。它由 Rohit Ghumare 创建，包含 428 节动手课程和 20 个结构化阶段，从数学基础到生产级 AI 系统部署全程覆盖。项目坚持"Build, Don't Import"理念，要求学习者从原始数学开始实现每个算法，确保对底层原理的深度理解。支持 Python、TypeScript、Rust、Julia 四种语言，并内置评估工具和 SkillKit 集成，是自学者和转型开发者进入 AI 工程领域的优质资源。

---

*数据来源：GitHub 仓库 (rohitg00/ai-engineering-from-scratch)、项目官网 (aiengineeringfromscratch.com)、Reddit、Trendshift（2026 年 5 月访问）*

*首次分析：2026 年 5 月 | 最近更新：2026 年 8 月 26 日*

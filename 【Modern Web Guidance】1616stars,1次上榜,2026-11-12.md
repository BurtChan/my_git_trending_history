# Modern Web Guidance 项目分析

## 项目名称
**Modern Web Guidance (src)** — Google Chrome 官方出品的「现代 Web 平台专业知识注入器」，把 217 项现代 Web 特性指南、最佳实践与浏览器兼容性数据直接嵌入你的 AI 编码代理

- **GitHub**: [GoogleChrome/modern-web-guidance-src](https://github.com/GoogleChrome/modern-web-guidance-src)
- **许可证**: Apache-2.0（代码）+ CC-BY 4.0（指南内容）
- **官网**: [goo.gle/modern-web-guidance](https://goo.gle/modern-web-guidance)

---

## 项目概述

这是 Google Chrome 团队联合 Microsoft Edge 团队和 Web 开发社区推出的 Agent Skill 项目（本仓库为其**源仓库**，发布的 skill 产物在 [GoogleChrome/modern-web-guidance](https://github.com/GoogleChrome/modern-web-guidance)）。它解决的核心问题是：AI 编码代理的训练数据中充满了大量遗留代码，导致模型在生成前端代码时倾向于使用过时的模式——为原生已有方案的任务生成臃肿的 JavaScript，或用重量级 polyfill/旧库替代本可由浏览器原生优化的平台 API。

Modern Web Guidance 通过 Agent Skill 的 CLI 把**针对性的、专家策展的指南**直接注入代理的上下文窗口，聚焦三类引导：① **现代浏览器 API**——帮助模型正确构造它们经常误用的 API；② **性能与无障碍**——优先选择浏览器可优化的平台级 API（自带无障碍能力）；③ **负责任的降级**——引导模型使用轻量降级方案而非重型 polyfill 或旧库。

项目最具工程含金量的设计是**校准与评估闭环**：指南被刻意做成 token 高效（核心 pack 仅约 234 tokens），团队运行 eval 来剪掉「模型已经知道」的最低公分母内容。README 中的实测数据非常亮眼——claude_code (sonnet-5-5) 在 eval 通过率上从 54-58% 提升到 89%，antigravity_cli (gemini-3.8-flash) 从 60-63% 提升到 91-93%，codex_cli (gpt-6.1-sol) 提升 19-35 个百分点。这是「给 Agent 注入领域知识」赛道里少有的、用硬 eval 数字证明价值的项目。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **217 项现代 Web 特性指南** | 覆盖 CSS & Layout（123 项）、Forms & UI、Performance、Accessibility、Built-in AI 等核心领域，从近几年的成熟特性一直覆盖到 cutting edge |
| **CLI 即取即用** | `npx modern-web-guidance@latest install` 交互式安装；也可按 guide ID 精确检索（如 `animate-to-from-top-layer`）或语义搜索 |
| **两个 Skill Pack** | `modern-web-guidance`（~234 tokens，浏览器 API/布局/性能综合指南）+ `chrome-extensions`（~181 tokens，Manifest V3/扩展 API/上架指引），可用 `--choose` 自定义组合 |
| **Eval 驱动的内容校准** | 源仓库包含指南编写、校准和评估的完整基础设施（`.agents/skills`、`features/`、eval cases），用真实模型评测剪除冗余内容 |
| **隐私友好遥测** | 仅匿名收集安装数、调用代理名、guide 检索 ID，不收集原始 prompt，可用 `DISABLE_TELEMETRY=1` 退出 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | TypeScript（CLI 与构建工具链） |
| 内容格式 | Markdown 指南（guides/），源自 MDN/W3C/WHATWG/IETF 规范 |
| 分发 | npm（npx 安装向导），产物为标准 Agent Skill |
| 质量工具 | oxlint、CodeQL、Playwright 风格 eval 基础设施 |
| 许可 | Apache-2.0（代码）+ CC-BY 4.0（指南内容） |

---

## 项目亮点

### 1. 大厂背书的 Agent Skill 标杆样本
由 Google Chrome 团队主导、Microsoft Edge 团队支持，内容派生自 MDN 和 W3C/WHATWG/IETF 官方规范——这是「用 Skill 给 Agent 补领域知识」模式迄今规格最高的官方实践，对整个 Agent Skill 生态有示范意义。

### 2. 用 eval 数字说话的内容工程
不满足于「写一堆指南塞给模型」，而是为每批内容跑多模型 eval（Claude/Gemini/GPT 三个家族），量化证明注入后通过率提升 19-35 个百分点，并据此剪枝——「token 高效」不是口号而是被测量的结果。

### 3. 精准解决 LLM 时代前端的「遗产代码偏见」
模型会写 React 但写不好现代 CSS（container queries、`subgrid`、`oklch`、View Transitions、Popover API、Anchor Positioning）的痛点被行业普遍感知，这个项目给出了系统性的解法。

### 4. 源仓库与发布仓库分离的工程治理
`-src` 仓库承载指南源码、校准与 eval 基础设施，发布仓库只做干净的 skill 安装目标——内容生产与分发解耦，欢迎社区贡献指南、eval 用例和 eval 基础设施。

---

## 应用场景

### 1. AI 辅助前端开发的质检增强
团队用 Claude Code / Codex / Gemini CLI 等代理写前端代码时，安装此 skill 后代理生成的是现代原生方案（如用 `scrollbar-color` 而非自造样式代码），减少代码评审中「为什么不用原生 API」的往返。

### 2. 浏览器扩展开发
`chrome-extensions` pack 专注 Manifest V3、background workers、扩展 API 和 Chrome Web Store 上架——扩展开发者在 AI 辅助开发中可直接受益。

### 3. Agent Skill 内容工程的参考实现
想为自己的领域（如电力交易、机器视觉）构建领域知识 Skill 的团队，可参考其「指南编写 → eval 校准 → 剪枝发布」的完整方法论与基础设施。

### 4. Web 平台推广的落地管道
对 Google 而言，这是把现代 Web 特性（View Transitions、Scheduler.yield、内置 AI API 等）推动到实际生产代码的低摩擦管道——开发者无需主动学习，代理会自动带路。

---

## Star 数据

| 指标 | 数据 |
|------|------|
| **总 Stars** | 1,616 |
| **总 Forks** | 135 |
| **今日新增 Stars** | +133 |
| **Open Issues** | 364 |
| **许可证** | Apache-2.0 |
| **主要语言** | TypeScript |

---

## 总结

Modern Web Guidance 是 Google Chrome 官方对「Agent 缺现代 Web 知识」这一真实痛点的工程化回应：217 项特性指南 + eval 校准闭环 + 三个模型家族 19-35 个百分点的实测提升，既是前端开发者的实用工具，更是 Agent Skill 内容工程的教科书级参考实现。

---

*数据来源：GitHub 仓库 (GoogleChrome/modern-web-guidance-src)，2026 年 11 月访问*
*首次分析：2026 年 11 月 12 日*

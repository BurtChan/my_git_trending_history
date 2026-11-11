# Modern Web Guidance 项目分析

## 项目名称
**Modern Web Guidance** — Google 出品：把现代 Web 平台专家知识注入编码 Agent 的技能包
- **GitHub**: [GoogleChrome/modern-web-guidance-src](https://github.com/GoogleChrome/modern-web-guidance-src)
- **许可证**: Apache-2.0（代码）/ CC-BY 4.0（指南内容）

---

## 项目概述

Modern Web Guidance 是 Google Chrome 团队（联合 Microsoft Edge 团队与 Web 社区）推出的编码 Agent 技能集，解决的问题直击当前 AI 编码的普遍痛点：**LLM 训练数据中充斥着大量遗留代码，导致 Agent 默认生成过时的 Web 模式**——为有原生平台方案的任务写出臃肿的 JavaScript、滥用重型 polyfill 与遗留库。它把 Web 平台专业知识、最佳实践与浏览器兼容性数据直接嵌入 Agent 上下文，引导模型走向现代、高性能、可访问性内建的解决方案。

项目覆盖 Web 平台近年新特性的 217 项功能指南（CSS 与布局 123 项、UX、性能、表单与 UI、可访问性、内置 AI 六大类别），从 View Transitions、容器查询、Anchor Positioning 到 `scheduler.yield`、本地翻译/摘要 API。指南按 token 效率设计：团队运行评测（eval）裁剪「模型已经知道的最低公分母内容」，只保留模型缺乏的生产级实现密度。

技术形态是一个带 CLI 的 Agent Skill：`npx modern-web-guidance@latest install` 交互式安装后，Agent 可通过命令检索相关指南（如「animate a dialog modal backdrop」）或按 ID 精确获取（如 `animate-to-from-top-layer`）。发布仓库（modern-web-guidance）是纯安装目标，本仓库（-src）包含创作、校准与评测的全部源码。评测数据非常有说服力：主流编码 Agent 使用后，任务正确率普遍提升 20-35 个百分点（如 claude_code 从 54% 升至 89%）。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 217 项现代 Web 特性指南 | CSS 布局 123 项 + UX 动效、性能、表单 UI、可访问性、内置 AI 五类核心学科 |
| CLI 指南检索 | Agent 按任务语义搜索指南，或按 ID 精确获取，结果直接进入上下文窗口 |
| Token 高效设计 | eval 驱动的内容裁剪，核心包仅 ~234 tokens |
| 可选技能包 | `--choose` 选择安装：完整包或 Chrome 扩展专项包（Manifest V3 等，~181 tokens） |
| 评测基础设施 | 源仓库包含指南创作、校准、eval 案例与评测基础设施 |
| 隐私可控 | 匿名遥测可开关（DISABLE_TELEMETRY=1），不收集原始 prompt |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | TypeScript（src/ + bin/） |
| 分发 | npm 包（npx modern-web-guidance） |
| 形式 | Agent Skill（.agents/skills/） |
| 内容许可 | CC-BY 4.0（指南），部分源自 MDN/W3C/WHATWG 规范 |
| 质量保障 | oxlint、eval 评测流水线 |
| 许可证 | Apache-2.0 |

---

## 项目亮点

### 直击 LLM 遗留代码偏置
模型即使知道新 API 存在，也往往缺乏生产级现代实现模式的密度。该项目不是教模型认 API，而是把「浏览器厂商认证的最佳实践」按需注入上下文——这是只有平台厂商才能做的高质量供给侧。

### eval 驱动的 token 经济
指南不是文档搬运，而是经过评测裁剪：凡模型已稳定掌握的内容被剪掉，只保留能显著改变行为的高密度知识。核心包 234 tokens 的成本几乎可以忽略，收益却是 20-35pp 的正确率提升。

### 负责任的回退策略
不仅推荐现代 API，还指导模型使用轻量合理的回退方案，而非重型 polyfill 或遗留库——这是实际生产中兼容性处理的关键区分。

### 顶级背书与开放共建
Chrome 团队 + Microsoft Edge 团队联合支持，源仓库开放指南、eval 案例、评测基础设施的贡献，内容部分衍生自 MDN，权威性与可持续性兼备。

---

## 应用场景

### AI 编码工具的前端知识增强
为 Cursor/Claude Code/Codex 等任何支持 Agent Skills 的工具安装后，前端代码生成质量即时提升——动画、布局、表单等高频场景直接受益。

### 前端团队规范落地
团队可以把「现代 Web 标准」从口头约定变成 Agent 强制行为：写 dialog 用 Popover API、布局用容器查询、动效用 View Transitions，新代码天然符合平台演进方向。

### Chrome 扩展开发
专项技能包覆盖 Manifest V3、background workers、扩展 API 与商店发布全流程，是扩展开发者接 AI 辅助的精准工具。

### Web 平台教学与推广
217 项特性的结构化指南本身就是极佳的现代 Web 平台学习地图，配套 web-features-explorer 链接可深入每个特性的兼容性数据。

---

## Star 数据

| 指标 | 数据 |
|------|------|
| **总 Stars** | 1,389 |
| **总 Forks** | 126 |
| **今日新增 Stars** | +133 |
| **许可证** | Apache-2.0 / CC-BY 4.0 |
| **创建时间** | 2026-01-27 |

---

## 总结

Modern Web Guidance 用「厂商认证 + eval 裁剪 + 极小 token 成本」的组合拳，把 Web 平台的现代最佳实践变成了编码 Agent 的即插即用知识包，是 Agent Skills 生态中基础设施级的项目。

---

*数据来源：GitHub 仓库 (GoogleChrome/modern-web-guidance-src)，2026 年 11 月访问*

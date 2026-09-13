# Agent Skills (Tech Leads Club) 项目分析

## 项目名称
**Agent Skills** — 面向专业 AI 编码代理的「安全、经过验证」的技能注册表
- **GitHub**: [tech-leads-club/agent-skills](https://github.com/tech-leads-club/agent-skills)
- **许可证**: 自定义（要求署名 Tech Leads Club）

---

## 项目概述

Agent Skills 是 Tech Leads Club 社区推出的 AI 编码代理技能（Skills）库，定位直击当前 Agent 生态的信任危机：Snyk 的报告显示市场上超过 13%（精确数字 13.4%）的技能市场条目包含严重漏洞。该项目以此为卖点，把自己塑造成「经过验证、经过测试、安全」的技能目录——100% 开源无二进制、CI/CD 静态分析、lockfile + 内容哈希保证不可变完整性、人工策划的提示词，每个技能发布前都经过 Snyk Agent Scan 扫描。

技能（Skills）即「AI 助手的插件」：打包的指令与资源教会 Agent 新的工作流、模式与领域知识。该注册表通过 npm CLI（`npx @tech-leads-club/agent-skills`）以交互式向导分发，技能从 CDN 按需拉取（目录约 45KB），可安装到 Claude Code、Cursor、GitHub Copilot、Cline、Windsurf、OpenAI Codex、Antigravity、Gemini CLI 等十余个主流 Agent，分 Tier 1（流行）/ Tier 2（上升）/ Tier 3（企业）三档支持。

安全设计上 CLI 采用纵深防御：输入消毒、路径隔离、符号链接守卫、原子 lockfile、审计日志。2026 年 1 月创建即快速冲上 5.3K Stars，反映了「Agent 技能供应链安全」正在成为新的刚需赛道。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 安全技能目录 | 全开源、CI 静态分析、内容哈希、Snyk Agent Scan 逐项扫描 |
| 多 Agent 安装 | npx 向导式安装到 15+ 主流 AI 编码代理 |
| 技能目录 | 按分类组织的 SKILL.md + templates + references 结构 |
| 精选技能 | tlc-spec-driven（规格驱动开发）、aws-advisor、playwright-skill、figma、security-best-practices 等 |
| CLI 防御 | 消毒、路径隔离、symlink 守卫、原子 lockfile、审计日志 |
| 安装方式 | 复制（推荐）或符号链接，全局或项目级 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | TypeScript 100% |
| 构建 | Nx monorepo + semantic-release |
| 分发 | npm（@tech-leads-club/agent-skills），CDN 按需拉取 |
| 安全扫描 | Snyk Agent Scan（前 mcp-scan） |

---

## 项目亮点

### 「13.4% 技能有严重漏洞」的精准卡位
不做大而全的市场，而做「经过验证的安全子集」，把供应链安全作为核心竞争力，差异化清晰。

### 一个目录适配所有 Agent
安装向导把同一技能写入 Claude Code / Cursor / Copilot / Codex 等各家目录格式，解决技能生态碎片化。

### 工程化程度高
Nx monorepo、semantic-release、完整 CHANGELOG 与 CONTRIBUTING，1,181 次提交、月更节奏，社区运营（Tech Leads Club）背书。

---

## 应用场景

### 企业 Agent 技能治理
企业内部允许开发者使用 AI 编码代理时，用经过扫描的技能库替代野生市场，降低提示注入与恶意技能风险。

### 团队标准化工作流
tlc-spec-driven（Specify→Design→Tasks→Implement 四阶段）这类技能可以统一团队的规格驱动开发流程。

### 技能作者发布渠道
为技能作者提供带安全扫描与完整性保证的分发渠道，署名要求明确。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 5,377 |
| 总 Forks | 486 |
| 今日新增 | +215 |
| 主要语言 | TypeScript |
| 许可证 | 自定义（需署名） |
| 创建时间 | 2026-01-19 |

---

## 总结

Agent Skills 用「13.4% 的市场技能有严重漏洞」的行业痛点切入，以全开源 + 静态分析 + 逐项扫描 + 一键装到 15+ Agent 的组合，把 AI 技能供应链安全做成了产品，是 Agent 工具生态走向治理阶段的标志性项目。

---

*数据来源：GitHub 仓库 (tech-leads-club/agent-skills)，2026 年 9 月访问*

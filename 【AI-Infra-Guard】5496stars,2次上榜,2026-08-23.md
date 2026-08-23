# AI-Infra-Guard 项目分析

## 项目名称
**AI-Infra-Guard** — 腾讯开源的全栈 AI 红队（Red Teaming）平台
- **GitHub**: [Tencent/AI-Infra-Guard](https://github.com/Tencent/AI-Infra-Guard)
- **许可证**: Apache-2.0

---

## 项目概述
AI-Infra-Guard 是腾讯开源的 AI 生态安全防护平台，覆盖 AI 系统的完整攻击面：**Agent Scan**（智能体扫描）、**Skills Scan**（技能扫描）、**MCP Scan**（MCP 服务器扫描）、**AI Infra Scan**（AI 基础设施扫描）以及 **LLM 越狱评估**（jailbreak evaluation）。

随着企业大量引入 LLM Agent、MCP 工具链与外挂技能，供应链与提示注入风险急剧上升——AI-Infra-Guard 正是针对这一新战场的一站式红队工具：既能在攻击视角发现 Agent 与 MCP 生态的漏洞，也能对模型自身的越狱抵抗力做系统评估。

仓库含 1,795 commits，目录包括 agent-scan、AIG-PromptSecurity、Research 等模块，研发投入持续且深入。目前 5.1K Stars，今日 +50 温和上榜，属于安全领域的实力型项目。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| Agent Scan | 检测 AI Agent 的攻击面与安全缺陷 |
| Skills Scan | 扫描外挂技能（Skills）的供应链风险 |
| MCP Scan | 对 MCP 服务器做安全配置与漏洞扫描 |
| AI Infra Scan | 扫描 AI 基础设施组件的暴露面 |
| 越狱评估 | 系统化评测 LLM 的越狱防御能力 |
| AIG-PromptSecurity | 提示词安全专项模块 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 许可证 | Apache-2.0 |
| 架构 | 多扫描器引擎 + 评估模块 + 研究目录 |
| 背景 | 腾讯安全团队维护 |

---

## 项目亮点

### 覆盖 AI 供应链全链条
从 Agent、Skills、MCP 到底层 Infra，是目前少数把「AI 生态攻击面」做成统一平台的红队工具。

### 大厂安全团队背书
腾讯安全持续投入（1,795 commits + Research 目录），规则库与越狱用例的更新能力有保障。

### 切中 MCP 时代新风险
MCP 与 Agent Skills 爆发后，工具链投毒、恶意 MCP 服务成为 2026 年最热的安全议题，项目卡位精准。

---

## 应用场景

### 企业 AI 上线前安全评估
对内部 Agent 与 MCP 工具链做上线前红队扫描。

### 红队/渗透测试团队
AI 目标的攻击面枚举与漏洞验证工具箱。

### LLM 防御能力评测
用标准化越狱用例评估自研/采购模型的抵抗能力。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ 总 Stars | 5,496 |
| 🍴 总 Forks | 518 |
| 📈 今日新增 | 150 stars |
| 📝 Commits | 1,795 |
| 📅 许可证 | Apache-2.0 |

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 23 日（连续第 3 天登上 Trending）

**更新原因**：项目持续登上 GitHub Trending（8/21 首次上榜、8/22、8/23 连续在榜）

**最新动态**：
- 发布 v4.5.2（8 月 17 日）：Skill-Scan 新增 `.pyc` 字节码绕过检测与字符集走私防御；MCP-Scan 动态模式增加工具白名单防 RCE；漏洞库扩充至 2000+ CVE 规则；新增 SkillJack 研究项目。
- 此前 v4.5.1（7 月 30 日）加入 4 种多轮越狱攻击（Many-Shot、PAIR、GOAT、ActorAttack），Agent-Scan 扩展至 10 个检测技能（含 5 个 OWASP 技能 + Web 外泄检测）。
- v5.0.0 变异引擎重构进行中（workflow-attack 并入 mutation-attack），研发节奏活跃。
- 社区认可度持续上升：Stars 从 4,345（7 月 31 日）→ 5,107（8 月 21 日）→ 5,496，三周增长约 26%。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 5,107 | 5,496 | +389 |
| 总 Forks | 495 | 518 | +23 |

**核心变化概要**：
- 漏洞规则库从 1,888 条扩至 2,000+ 条，覆盖组件从 130 个继续增加
- Skill-Scan 补上 `.pyc` 字节码绕过这一新兴攻击面，MCP-Scan 增加白名单防 RCE 机制
- 越狱评估从单轮扩展到多轮攻击（Many-Shot/PAIR/GOAT/ActorAttack），对齐前沿攻击研究
- 持续在榜三天，AI 供应链安全赛道关注度上升（LiteLLM 供应链投毒等事件推高需求）

---

## 总结
AI-Infra-Guard 是大厂对「AI 生态安全」这一新战场的系统性回答——扫描面覆盖 Agent/Skills/MCP/Infra 全链条，是 AI 安全世界里工程完成度领先的红队平台。

---

*数据来源：GitHub 仓库 (Tencent/AI-Infra-Guard)，2026 年 8 月访问*

*首次分析：2026 年 8 月 | 最近更新：2026 年 8 月*

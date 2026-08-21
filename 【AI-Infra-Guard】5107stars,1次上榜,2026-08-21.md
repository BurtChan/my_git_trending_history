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
| ⭐ 总 Stars | 5,107 |
| 🍴 总 Forks | 495 |
| 📈 今日新增 | 50 stars |
| 📝 Commits | 1,795 |
| 📅 许可证 | Apache-2.0 |

---

## 总结
AI-Infra-Guard 是大厂对「AI 生态安全」这一新战场的系统性回答——扫描面覆盖 Agent/Skills/MCP/Infra 全链条，是 AI 安全世界里工程完成度领先的红队平台。

---

*数据来源：GitHub 仓库 (Tencent/AI-Infra-Guard)，2026 年 8 月访问*

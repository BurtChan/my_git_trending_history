# Claude-Red 项目分析

## 项目名称
**Claude-Red** — 面向 Claude Skills 体系的进攻性安全技能库
- **GitHub**: [SnailSploit/Claude-Red](https://github.com/SnailSploit/Claude-Red)
- **许可证**: MIT

---

## 项目概述
Claude-Red 是一个精心策划的进攻性安全（offensive security）技能库，专门为 Claude 的 Skills 系统设计。每个技能都是一个结构化的 SKILL.md 文件，通过 frontmatter 元数据和专家级方法论文本，将 Claude「调教」为特定攻击领域的资深专家——从 SQL 注入到 shellcode 编写，从 EDR 绕过到漏洞利用开发。

项目由安全社区 SnailSploit 维护，2026 年 3 月创建后快速迭代，从最初 38 个技能扩展到 58 个、再到当前 100+ 技能规模（目标约 130 个技能、23+ 分类），是 Claude Skills 生态在安全攻防领域最系统的扩展库之一。它的出现代表了 AI 安全工作流的一个新范式：不再是「人用工具」，而是「AI Agent 按技能卡片的专家方法论自主执行侦察、利用、后渗透全流程」。

需要注意的是，该项目定位为专业红队/渗透测试人员的效率倍增器，技能内容按 MITCK ATT&CK 战术编号组织（如 TA0001 初始访问），强调合法授权测试场景。

---

## 核心功能

| 分类 | 代表技能 | 覆盖内容 |
|------|----------|----------|
| 初始访问 | `offensive-initial-access` | 钓鱼载荷、drive-by 投递、供应链投毒向量（TA0001） |
| 红队全链 | `offensive-advanced-redteam` | C2 基础设施、OPSEC、横向移动、持久化 |
| EDR 绕过 | `offensive-edr-evasion` | 用户态 unhooking、间接系统调用、PPID 欺骗 |
| Shellcode | `offensive-shellcode` | 编写、编码、注入技术、位置无关代码 |
| 无线攻防 | `offensive-wifi` 系列 | 802.11 侦察、WPA2-PSK 握手捕获/PMKID、WPA3-SAE Dragonblood、802.1X/EAP 凭据中继 |
| 移动安全 | `offensive-mobile` | 移动端攻击面方法论 |

---

## 技术栈
| 组件 | 技术 |
|------|------|
| 技能格式 | SKILL.md（frontmatter 元数据 + Markdown 方法论正文） |
| 目标平台 | Claude Code / Claude Skills 体系 |
| 组织标准 | MITCK ATT&CK 战术分类 |
| 语言 | Python（辅助脚本） |

---

## 项目亮点

### 专家方法论的「技能化」
每个 SKILL.md 不是简单提示词，而是一套完整的攻击方法论卡片：包含前置知识、工具链选择、分步流程、常见坑点。Claude 加载技能后即具备该领域的专家级推理路径，大幅降低红队工程师在多攻击面之间切换的认知成本。

### 覆盖面系统化
从 Web（SQLi）、二进制（shellcode）、终端对抗（EDR evasion）到无线（WiFi 全家族）和移动端，按 ATT&CK 战术编号组织，可按杀伤链阶段组合使用，形成「初始访问→横向移动→持久化」的完整技能流水线。

### 社区驱动的快速演进
从 38 → 58 → 100+ 技能的扩张速度，加上明确的贡献规范（单一攻击面技能优先于大而全概览），保证了技能库的深度与颗粒度持续提升。

---

## 应用场景

### 红队与渗透测试自动化
授权渗透测试中，让 Claude Code 加载对应技能后辅助生成载荷、分析侦察数据、规划攻击路径，测试人员聚焦决策。

### 蓝队反向训练
防御方研读进攻方法论技能卡，理解攻击者视角，用于制定检测规则与加固策略（项目在 r/blueteamsec 亦有讨论）。

### AI 安全研究
作为研究「LLM + 结构化攻击知识」能力的标本，观察技能化知识注入对模型行为的影响。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ 总 Stars | 3,326 |
| 🍴 总 Forks | 532 |
| 📈 今日新增 | 99 |
| 创建时间 | 2026-03-04 |
| 主要语言 | Python |
| 许可证 | MIT |

---

## 总结
Claude-Red 把进攻性安全知识以 Claude Skills 的标准格式「技能化」，100+ 专家级方法论卡片覆盖从钓鱼到 EDR 绕过的完整杀伤链，是 AI Agent 深度参与红队工作流这一新范式的代表性项目。

---

*数据来源：GitHub 仓库 (SnailSploit/Claude-Red)，2026 年 9 月访问*

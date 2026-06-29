# VulnClaw 项目分析

## 项目名称

**VulnClaw** — 基于 AI Agent 的智能渗透测试 CLI 工具，实现自然语言驱动的全自动漏洞发现与利用

- **GitHub**: [Unclecheng-li/VulnClaw](https://github.com/Unclecheng-li/VulnClaw)
- **许可证**: MIT
- **版本**: v0.3.2（PyPI）

---

## 项目概述

VulnClaw（龙虾）是一款由 AI 驱动的渗透测试 CLI 工具，由安全研究员 Unclecheng-li 于 2026 年 4 月创建并开源。它采用 LLM Agent + MCP 工具链 + 渗透 Skill 编排的创新架构，将复杂的渗透测试流程自动化为"自然语言输入 → 自动执行"的极简交互模式。用户只需用自然语言描述目标，VulnClaw 即可自动完成从信息收集、漏洞发现、漏洞利用到报告生成的完整渗透测试周期，被誉为"说人话，打漏洞"的安全利器。

VulnClaw 的核心技术亮点是其 **Goal-Driven Solving Engine（目标驱动求解引擎）**。与传统固定轮次的渗透测试工具不同，VulnClaw 采用 Blackboard 状态空间搜索模型，将渗透测试建模为从"起点"到"目标"的搜索过程。系统维护两种状态原语：Fact（已通过真实工具输出确认的事实）和 Intent（待执行的探索方向）。每次推理（Reason）阶段读取完整状态图谱判断目标是否达成或提出新方向，每次探索（Explore）阶段执行具体工具操作并将确认结论写入 Fact。一旦某个方向被探索完毕就标记为 `concluded` 或 `abandoned`，**从根本上杜绝了循环重复**——这是传统 AI Agent 在长任务中最常见的失败模式。

在反幻觉方面，VulnClaw 实现了 **Evidence-Level Anti-Hallucination Gate（证据级反幻觉门控）**。系统要求所有结论必须 verbatim（逐字）出现在真实工具输出中，任何 LLM 虚构的"发现"都会被标记为 `[未验证]` 并丢弃。Completion Gate 在系统声称目标达成时进行二次验证——如果输出中没有实际证据标记的 flag，则拒绝完成并继续执行。这种严格的证据校验机制确保了测试结果的真实性和可审计性。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **目标驱动求解引擎** | 基于 Blackboard 状态空间搜索的 OODA 循环，自动根据目标调整策略，目标达成、探索穷尽或安全预算耗尽时终止 |
| **证据级反幻觉门控** | 结论必须 verbatim 出现在真实工具输出中，虚构发现被丢弃并标记 `[未验证]`，完成门控二次验证目标达成 |
| **自适应反射引擎** | 自动分类失败原因，L0→L4 逐级升级绕过策略（URL编码→双重写入→Unicode/Hex→多层混淆→攻击面切换） |
| **13 家 LLM 提供商支持** | 兼容 OpenAI、MiniMax、DeepSeek、智谱、Moonshot、千问、SiliconFlow、豆包、百川、阶跃星辰、商汤、零一万物等 |
| **4 个 MCP 服务** | fetch（网络请求）、memory（本地记忆）、chrome-devtools（浏览器控制）、burp（Burp Suite 集成） |
| **21 个渗透 Skill** | 7 个核心 Skill + 14 个专业 Skill（CTF Web/Crypto/Misc、OSINT 侦察、安全知识），内含 180 份参考文档 |
| **29 种编解码操作** | Base64、Hex、URL、AES、JWT、Morse 等编解码，LLM 精确调用无需猜测 |
| **持久化渗透** | 每周期 100 轮 × 10 个周期 = 最多 1000 轮深度测试，每个周期自动生成报告 |
| **Web UI 模式** | `vulnclaw web` 启动 Web 界面（127.0.0.1:7788），支持浏览器图形化操作 |
| **漏洞插件系统** | 低耦合运行时插件架构 + 内置只读 Web 插件，可扩展自定义漏洞检测规则 |
| **Python 代码执行** | 内置 `python_execute` 用于 Payload 构造和漏洞验证 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要语言** | Python 3.10+ |
| **AI Agent 框架** | LLM Agent（大语言模型驱动的智能体） |
| **工具协议** | MCP（Model Context Protocol）工具链 |
| **渗透引擎** | Blackboard 状态空间搜索 + OODA 循环 |
| **LLM 交互** | OpenAI API 兼容格式（兼容 13 家提供商） |
| **用户界面** | CLI/REPL、TUI（终端 UI）、Web UI |
| **安装方式** | PyPI（`pip install vulnclaw`）、Docker |
| **许可证** | MIT |

---

## 项目亮点

### 目标驱动的 Blackboard 求解引擎

VulnClaw 的核心创新在于将渗透测试从传统的"固定 N 轮执行"升级为"目标驱动的智能搜索"。Blackboard 架构将所有已确认的发现存储为 Fact，所有待探索的方向存储为 Intent，系统通过 Reason-Explore 循环自动规划最优攻击路径。这种架构解决了传统 AI 渗透工具的两大顽疾：循环重复（同一操作反复执行）和方向迷失（忘记之前发现了什么）。Fact 的不可变性确保了每个发现只被处理一次，Intent 的有向搜索确保了攻击路径的系统性覆盖。

### 证据级反幻觉机制

在 AI 安全工具中，LLM 的幻觉问题是致命的——虚构的"已发现漏洞"可能导致错误的安全评估报告。VulnClaw 的 Evidence-Level Anti-Hallucination Gate 通过逐字比对工具输出和 LLM 结论来验证每个声明的真实性。Completion Gate 在系统宣称"目标达成"时进行终审——只有在真实输出中确实存在证据标记的 flag 时才允许完成。这种双重门控机制在安全审计场景中具有极高的实用价值，确保测试报告中的每一个发现都有据可查。

### MCP 工具链与 Skill 编排架构

VulnClaw 采用 MCP（Model Context Protocol）作为工具集成标准，将渗透测试所需的各类工具（网络请求、浏览器控制、Burp Suite 集成等）封装为标准化服务。21 个渗透 Skill 按功能分层组织——核心 Skill 覆盖通用渗透测试流程，专业 Skill 针对 CTF 竞赛（Web/Crypto/Misc）、OSINT 侦察、安全知识查询等场景优化。每个 Skill 内含详细的参考文档（共 180 份），相当于为 LLM 提供了一个结构化的安全知识库，使其能够做出更精准的工具选择和 Payload 构造。

### 极低门槛的交互设计

VulnClaw 的设计哲学是"说人话，打漏洞"。用户无需了解 Nmap 语法、SQL 注入 Payload 模板或 CSRF 攻击链的构造方式——只需用自然语言描述测试目标（如"帮我对 http://target.example.com 进行渗透测试"），VulnClaw 会自动判断测试阶段、选择合适的工具和 Skill、构造攻击载荷并生成结构化报告。这使安全测试从需要专业渗透测试工程师的操作，降维为任何安全意识的使用者都可以进行的自动化评估。

---

## 应用场景

### 授权渗透测试

安全团队和渗透测试工程师可以使用 VulnClaw 对授权目标进行自动化安全评估。VulnClaw 的目标驱动引擎能自动探索攻击面、发现漏洞并生成详细报告，大幅提升测试效率。对于常见的 Web 漏洞（SQL 注入、XSS、CSRF、文件上传等），VulnClaw 内置的专业 Skill 已积累了丰富的检测规则和绕过策略，覆盖 L0-L4 五个递进层次。

### CTF 竞赛

VulnClaw 内置的 CTF 专业 Skill（Web、Crypto、Misc）使其成为 CTF 竞赛的强力助手。面对 CTF 题目，参赛者只需将目标 URL 输入 VulnClaw，系统会自动分析题目类型、选择对应的解题策略（如 Web 题的信息收集+漏洞利用、Crypto 题的编解码+数学分析、Misc 题的取证+隐写分析），并持续尝试直到找到 flag。持久化渗透模式（1000 轮上限）确保了复杂题目的充分探索。

### 安全教学与培训

VulnClaw 的自然语言交互和自动化执行使其成为安全培训的理想教学工具。学员可以通过观察 VulnClaw 的 Reason-Explore 决策过程来学习渗透测试的思路和方法——系统何时选择 SQL 注入、何时切换到文件包含、何时升级绕过策略，这些决策过程本身就是最好的渗透测试教学案例。

### 企业安全评估

企业安全团队可以将 VulnClaw 集成到 DevSecOps 流程中，对内部应用进行持续的安全评估。通过 Web UI 模式，安全分析师可以在浏览器中直观地监控测试进度和发现结果。VulnClaw 的结构化报告输出可以直接导入到企业的漏洞管理系统中，形成从发现到修复的完整闭环。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 1,082 |
| **总 Forks** | 165 |
| **今日新增 Stars** | 105 |
| **许可证** | MIT |
| **主要语言** | Python |
| **创建时间** | 2026-04-18 |

---

## 总结

VulnClaw 是 **AI 驱动的下一代渗透测试工具**，1K Stars，以目标驱动的 Blackboard 求解引擎和证据级反幻觉门控为核心创新，将复杂的渗透测试流程自动化为自然语言交互的极简体验。其 MCP 工具链 + Skill 编排架构、13 家 LLM 提供商兼容性、以及从信息收集到报告生成的全链路自动化，使其在授权渗透测试、CTF 竞赛、安全教学和企业安全评估等场景中都展现出强大的实用价值。

---

*数据来源：GitHub 仓库 (Unclecheng-li/VulnClaw)，2026 年 6 月访问*

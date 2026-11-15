# Claude BugHunter 项目分析

## 项目名称
**Claude-BugHunter** — 面向漏洞挖掘与外部红队工作的 Claude Code 技能包
- **GitHub**: [elementalsouls/Claude-BugHunter](https://github.com/elementalsouls/Claude-BugHunter)
- **许可证**: MIT（代码）+ CC BY 4.0（内容）双许可
- **主页**: [elementalsouls.github.io/Claude-BugHunter](https://elementalsouls.github.io/Claude-BugHunter)

---

## 项目概述

Claude-BugHunter 是一个为 Claude Code 技能系统打造的自包含技能包，安装后 Claude Code 不再只是聊天机器人，而会表现得像一名资深漏洞挖掘研究员或红队操作员：它掌握 24 类核心漏洞的检测模式、攻击链模板、VRT 严重性映射、企业平台 CVE 链，并且始终保持在授权范围内作业。

技能包规模可观：**83 个技能 + 15 个斜杠命令 + 681 个已公开披露报告模式**（其中 433 个已单独标注来源、可审计），覆盖 Web 漏洞挖掘与企业身份/基础设施攻击矩阵两大方向。全部内容从 HackerOne 公开披露报告精选策展而来，由 Bug Hunting 与 GenAI 安全研究者 Sachin Sharma 构建，并已在授权红队、漏洞赏金项目和 DVWA、OWASP Juice Shop、Hacker101 等公开训练平台上实战验证。

技能按主题自动触发——用自然语言描述正在测试的内容，相关技能自动加载，无需按名称调用。这对安全从业者意味着：一个能检索 681 个真实漏洞披露案例模式的 AI 助手，将渗透测试的信息收集与模式匹配环节效率提升一个量级。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 四层技能栈 | Think（方法论/红队思维）→ Hunt（58 个 hunt-* Web 漏洞技能）→ Perimeter（企业平台攻击链）→ Ship（报告与证据卫生） |
| 24 类漏洞检测模式 | 每类含 payload、绕过表、攻击链模板 |
| 企业平台攻击矩阵 | M365/Entra、Okta、vCenter、SSL-VPN、SharePoint、云 IAM 的 2024-2026 CVE 链 |
| 7-Question Gate | 交付前的七问验证门槛 + VRT 感知严重性评级 |
| 证据卫生 | PII 脱敏、范围外（OOS）反驳模板 |
| Burp MCP 集成 | 与 PortSwigger Burp Suite 联动 |
| engagement 脚手架 | `hunt` 命令一键创建委托项目文件夹结构 |
| cbh CLI | 终端原生运行器，可独立 pipx 安装 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 形态 | Claude Code 技能包 / 插件（.claude-plugin） |
| 辅助工具 | ProjectDiscovery（subfinder/dnsx/httpx/katana/nuclei）、SecLists、Assetnote Wordlists |
| 分发 | Claude 插件市场 / 复制安装到 ~/.claude/ |
| 内容来源 | 681 个 HackerOne 公开披露报告策展 |

---

## 项目亮点

### 从披露报告到可执行技能的规模化策展
681 个真实漏洞报告被提炼为 24 类漏洞的检测模式库，且 433 个模式带单独引用可审计——不是泛泛的「AI 安全助手」，而是有据可查的实战知识库。

### 范围纪律内建
授权边界（scope）意识内建于方法论层：7-Question Gate、OOS 反驳模板、PII 脱敏流程确保 AI 辅助的红队工作不会越界，这是安全技能包区别于普通渗透工具集的关键设计。

### 完整交付闭环
从侦察、漏洞利用到报告产出（VRT 严重性映射、红队交付物模板）形成完整工作流，覆盖漏洞赏金猎人的全部日常环节。

---

## 应用场景

### 漏洞赏金（Bug Bounty）
 hunters 在 HackerOne/Bugcrowd 平台的日常作业：按漏洞类别自动加载对应的检测模式与 payload 库。

### 授权红队评估
企业外部红队委托：企业身份体系（M365/Okta）与基础设施（vCenter/VPN）的 CVE 攻击链执行 + 标准化交付物产出。

### 安全学习与训练
配合 DVWA、OWASP Juice Shop、Hacker101 等训练平台，是学习 Web 安全实战方法论的高效路径。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 6,024 |
| 总 Forks | 919 |
| 今日新增 | +124 |
| Open Issues | 5 |
| 创建时间 | 2026-05-05 |
| 语言 | Python（辅助脚本） |
| 许可证 | MIT + CC BY 4.0 |

---

## 总结

Claude-BugHunter 把 681 个真实漏洞披露报告提炼成 83 个可自动触发的 Claude Code 技能，以「方法论 + 模式库 + 范围纪律」三件套将 AI 编码代理改造成有据可查、不越界的漏洞挖掘操作员——是 2026 年 Claude Skills 生态在安全垂直领域最完整的作品。

---

*数据来源：GitHub 仓库 (elementalsouls/Claude-BugHunter)，2026 年 11 月访问*

# Anthropic Cybersecurity Skills 项目分析

## 项目名称

**Anthropic-Cybersecurity-Skills** — 面向 AI 代理的最大开源网络安全技能库

- **GitHub**: [mukul975/Anthropic-Cybersecurity-Skills](https://github.com/mukul975/Anthropic-Cybersecurity-Skills)
- **许可证**: Apache License 2.0

---

## 项目概述

Anthropic-Cybersecurity-Skills 是目前**最大的面向 AI 代理的开源网络安全技能库**，由开发者 Mahipal (mukul975) 创建并维护。该仓库包含 **754 个生产级网络安全技能**，覆盖 **26 个安全领域**，所有技能均遵循 **agentskills.io 开放标准**，并映射到 **五大行业框架**：MITRE ATT&CK、NIST CSF 2.0、MITRE ATLAS、MITRE D3FEND、NIST AI RMF。

该项目的核心目的不是提供脚本集合或博客教程，而是一个 **AI 原生的结构化操作知识库**，每个技能都编码了真实从业者的工作流程。它采用渐进式披露架构——AI 代理仅需约 30 tokens 扫描 YAML 前置信息即可判断相关性，匹配后才加载完整工作流（500-2000 tokens），极大优化 token 使用效率。

这是目前**唯一一个将每个技能同时映射到全部五大安全框架的开源技能库**，支持 Claude Code、GitHub Copilot、OpenAI Codex CLI、Cursor、Windsurf、Gemini CLI 等 20+ AI 编码平台。项目提供 CITATION.cff 文件，支持学术引用，版本已迭代至 v1.2.0。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **754 个结构化技能** | 覆盖渗透测试、数字取证、威胁情报、事件响应、云安全、OT/SCADA 安全、AI 安全等 |
| **26 个安全领域** | 包括 Web 应用安全、云安全、威胁狩猎、数字取证、合规等 |
| **五大框架映射** | 每个技能同时映射到 MITRE ATT&CK、NIST CSF 2.0、MITRE ATLAS、D3FEND、NIST AI RMF |
| **渐进式披露架构** | AI 代理仅需 ~30 tokens 扫描 YAML 前置信息即可判断相关性 |
| **agentskills.io 标准** | 采用 YAML frontmatter + 结构化 Markdown 的标准格式 |
| **ATT&CK Navigator 层** | 提供 ATT&CK 覆盖率可视映射文件 |
| **一键安装** | 支持 `npx skills add`、`git clone`、Claude Code 插件市场等多种安装方式 |
| **跨平台兼容** | 支持 26+ AI 平台，包括 Claude Code、Copilot、Codex CLI、Cursor 等 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **技能格式** | Markdown (.md) + YAML frontmatter |
| **元数据索引** | JSON (index.json) |
| **框架映射** | YAML/Markdown (mappings/ 目录) |
| **验证工具** | JavaScript/Node.js (tools/ 目录) |
| **CI/CD** | GitHub Actions |
| **插件配置** | .claude-plugin/ (Claude Code 插件配置) |
| **安装方式** | npx (Node.js 包管理) |

---

## 项目亮点

### 五框架统一覆盖
没有其他开源技能库将每个技能映射到全部五大安全框架，这是该项目的独特价值，使安全团队能在统一框架下进行跨维度分析。

### AI 原生设计
专为 AI 代理设计，采用渐进式披露架构，极大优化 token 使用效率，而非简单的内容搬运。

### 广泛的技能覆盖
754 个技能涵盖从 AWS 加固、SQL 注入防护到 Cobalt Strike 分析、智能合约漏洞审计等前沿领域，是目前最全面的 AI 安全技能库。

### 跨平台兼容
支持 26+ AI 编码平台，不绑定特定工具链，任何支持 Markdown/YAML 的 AI 代理均可使用。

---

## 应用场景

### AI 辅助安全运营 (SecOps)
AI 代理可直接使用技能执行威胁检测、事件响应、日志分析等安全运营任务。

### 自动化渗透测试
技能包含完整的渗透测试工作流，AI 可辅助执行安全评估与漏洞挖掘。

### 云安全加固
涵盖 AWS、Azure、GCP、Kubernetes 安全配置与审计技能，帮助企业实现云环境合规。

### 安全培训与教育
可作为安全从业者的结构化学习资源，每个技能对应真实安全工作流程。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 28,636 |
| **总 Forks** | 3,458 |
| **今日新增 Stars** | 198 |
| **许可证** | Apache License 2.0 |
| **主要语言** | Markdown / YAML |
| **创建时间** | 2026 年 2 月 |
| **最新版本** | v1.2.0 |

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 17 日（再次登上 Trending）

**更新原因**：项目再次登上 GitHub Trending 榜单。

**最新动态**：技能库已扩展到 817 个结构化网络安全技能、29 个安全领域，并映射 MITRE ATT&CK、NIST CSF 2.0、MITRE ATLAS、D3FEND、NIST AI RMF 和 MITRE F3 六套框架。其采用 agentskills.io 标准，可被 Claude Code、Copilot、Codex、Cursor、Gemini CLI 等二十余个平台复用。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 6,900 | 28,123 | +21,223 |
| 总 Forks | 976 | 3,422 | +2,446 |

**核心变化概要**：
- 技能规模从首次分析时的 754 个增至 817 个
- 框架映射扩展为六套，覆盖攻击、防御、AI 风险与反欺诈
- 跨平台兼容范围扩大到二十余种 AI 编码与代理工具

---

### 更新 2 — 2026 年 8 月 18 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：仓库当前仍维持 817 个结构化网络安全技能，覆盖 29 个安全领域，并将技能映射到 MITRE ATT&CK、NIST CSF 2.0、MITRE ATLAS、D3FEND、NIST AI RMF 与 MITRE F3 六套框架。项目继续采用 agentskills.io 标准，兼容 Claude Code、GitHub Copilot、Codex CLI、Cursor、Gemini CLI 和 Hermes Agent 等 20 多个平台。

相较 8 月 17 日的记录，项目新增 513 Stars 和 36 Forks。增长主要来自「标准化安全技能库 + 多框架映射 + 跨 Agent 平台复用」这一组合定位，仓库结构与文档体系保持稳定。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 28,123 | 28,636 | +513 |
| 总 Forks | 3,422 | 3,458 | +36 |

**核心变化概要**：
- 817 个技能、29 个安全领域与六套安全框架映射继续保持完整
- agentskills.io 标准使同一技能库可跨 20 多个 AI Agent 与编码工具复用
- Stars 单日净增 513，达到连续上榜项目的更新门槛
- Forks 增至 3,458，社区复用与二次开发仍在增长

---

## 总结

Anthropic-Cybersecurity-Skills 是目前**最大的 AI 原生网络安全技能库**，以 754 个结构化技能覆盖 26 个安全领域，并将每个技能映射到五大行业框架。项目采用渐进式披露架构优化 AI 代理的 token 效率，支持 26+ AI 编码平台，是 AI + 网络安全交叉领域的重要开源项目，6.9k Stars 反映了社区的高度认可。

---

*数据来源：GitHub 仓库 (mukul975/Anthropic-Cybersecurity-Skills)、Web 搜索结果（2026 年 5 月访问）*
*首次分析：见文件头部 | 最近更新：2026 年 8 月 18 日*

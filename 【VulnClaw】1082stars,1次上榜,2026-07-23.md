# VulnClaw 项目分析

> 🦞 基于 AI Agent + MCP 工具链 + 渗透 Skill 编排的全自动渗透测试工具

## 基本信息

| 项目 | 详情 |
|------|------|
| **仓库地址** | https://github.com/Unclecheng-li/VulnClaw |
| **创建时间** | 2026-04-18 |
| **主要语言** | Python |
| **开源协议** | MIT |
| **Star 数** | 1,082 |
| **Fork 数** | 165 |
| **最新版本** | v0.4.0（PyPI: `vulnclaw` v0.3.1+） |
| **Python 要求** | 3.10+ |
| **贡献者** | 10+（包括 Unclecheng-li、chu0119、FarStar-CN、ww455 等） |

## 项目简介

VulnClaw 是一款 **AI 驱动的渗透测试 CLI 工具**，其核心理念是"说人话，打漏洞"。用户只需通过自然语言输入目标（如"帮我对 http://target.example.com 进行渗透测试"），工具即可自动完成从信息收集、漏洞发现、漏洞利用到报告生成的全流程渗透测试。

技术栈基于 **LLM Agent + MCP（Model Context Protocol）工具链 + 渗透 Skill 编排**，兼容 OpenAI、MiniMax、DeepSeek 等主流大语言模型。

## 核心架构（v0.4.0 重大升级）

### 从"固定轮次"到"目标驱动求解"

v0.4.0 版本进行了核心架构重构，从容易在弱模型上陷入无限循环的**固定轮次工作流**转向基于**状态空间搜索**的求解模式。这是该项目的核心创新点。

### Blackboard + OODA 求解循环

渗透测试被建模为从**起点**（目标）到**目标**（flag/shell/已确认严重漏洞）的有向搜索，由两个基本原语驱动：

- **Fact（事实）**：由真实工具输出确认的客观结论（探索锚点）
- **Intent（意图）**：声明的探索方向（尚未执行）；由 Fact 产生，结论形成新的 Fact

循环结构（`vulnclaw/agent/solver.py`）：
```
REASON（读取完整图） → 目标是否达成？/ 提出新探索 / 无新提议
│
EXPLORE（认领一个 Intent） → 用工具执行 → 将确认的结论写回为 Fact
│
终止：目标达成 / 探索前沿耗尽 / 安全预算耗尽
```

**消除循环的关键设计**：一旦"首页是一个登录表单"成为 Fact，Reason 就不会再提议"检查首页"，而是提议"测试 SQL 注入"。每个 Intent 只被认领一次、结束一次（`concluded` / `abandoned`），从机制上杜绝重复。终止是目标驱动的，而非轮次计数。

### 反幻觉证据门控

弱模型常会伪造 flag。新引擎将**所有真实工具输出**（HTTP 响应体、`python_execute` 输出）作为唯一可信证据记录。无证据支撑的声明标记为 `[未验证]` 并被拒绝为"完成"。

### 结构化推理与自适应反思

- `reasoning_state.py`：结构化的事实/约束/攻击链管理
- `reflexion.py`：失败分类，支持 L0-L4 升级策略

### 漏洞检测插件系统

低耦合插件运行时（`vulnclaw/plugins/`）+ 内置只读 Web 插件（安全头 / JWT / JS 端点分析）。插件结果去重后合并到 `SessionState.findings` 供报告流水线使用。

## 功能模块

### CLI 命令体系

| 命令 | 功能 | 示例 |
|------|------|------|
| `vulnclaw` | 默认 CLI/REPL 交互界面 | `vulnclaw` |
| `vulnclaw tui` | 终端图形化工作台 | `vulnclaw tui --target target.com` |
| `vulnclaw solve <target>` | 目标驱动求解（无固定轮数，拿到目标即停） | `vulnclaw solve target.com --goal "拿到flag"` |
| `vulnclaw run <target>` | 一键全流程渗透（默认走 solve 引擎） | `vulnclaw run 192.168.1.1` |
| `vulnclaw persistent <target>` | 持续性渗透（100轮/周期） | `vulnclaw persistent 192.168.1.1` |
| `vulnclaw recon <target>` | 仅侦察（不执行利用） | `vulnclaw recon target.com` |
| `vulnclaw scan <target>` | 漏洞扫描阶段 | `vulnclaw scan target.com --ports 80,443` |
| `vulnclaw exploit <target>` | 漏洞利用阶段 | `vulnclaw exploit target.com --cve CVE-2024-1234` |
| `vulnclaw report <session>` | 从会话 JSON 生成报告 | `vulnclaw report session_xxx.json` |
| `vulnclaw web` | 启动本地 Web UI | `vulnclaw web --port 8080` |
| `vulnclaw plugins list/info/run` | 插件管理 | `vulnclaw plugins list --stage discovery` |

### 三种使用模式

1. **CLI/REPL 模式**（默认）：自然语言对话 + 自主多轮渗透循环
2. **TUI 工作台模式**（`vulnclaw tui`）：图形化终端工作台，显示授权目标、检查模式、运行概览、安全边界等
3. **Web UI 模式**（`vulnclaw web`）：本地 Web 界面（默认 `127.0.0.1:7788`），支持浏览器端渗透操作

### 自动触发关键词

REPL 内置自动触发关键词：**"渗透测试"、"找flag"、"弱口令爆破"**，或明确说"进入自主渗透模式"。可随时按 `Ctrl+C` 中断。

### LLM 提供商支持

支持 OpenAI、MiniMax、DeepSeek 等多家 LLM 提供商，通过 `vulnclaw config provider <name>` 切换。

## 依赖工具链

- **Python 3.10+**
- **Node.js**（MCP 服务运行所需）
- **nmap**（端口扫描）
- **MCP 服务**：fetch、memory 等

可通过 `vulnclaw doctor` 进行完整环境诊断。

## 项目热度与社区活跃度

- 项目创建仅约 **2 个月**（2026-04-18 至今），已获得 **1,082 Stars** 和 **165 Forks**，增长势头强劲。
- 有 **10+ 贡献者**参与开发，社区贡献活跃。
- 近期重要 PR 包括：i18n 中英文切换支持、第三方 API 兼容修复、Web 国际化、新 Skills 添加、TUI 作用域链式输入修复等。
- 项目标签涵盖：`ai-agent`、`cybersecurity`、`penetration-testing`、`ctf`、`security-tools` 等，定位清晰。

## 技术亮点分析

### 1. 状态空间搜索架构
将渗透测试建模为有向搜索问题而非固定流程，这在 AI 安全工具中是较为前沿的设计。Fact/Intent 图结构有效解决了 LLM Agent 常见的循环和遗忘问题。

### 2. 反幻觉机制
针对 LLM "幻觉"问题的工程化解决方案——以真实工具输出为唯一证据源，拒绝无依据的声明。这对安全测试场景尤为重要，避免生成虚假的漏洞报告。

### 3. MCP 工具链集成
采用 Model Context Protocol 作为工具调用标准，实现了与大模型的标准对接，便于扩展新工具。

### 4. 多模式交互
CLI/REPL、TUI、Web UI 三种交互模式覆盖了不同使用场景，降低了使用门槛。

### 5. 插件化架构
低耦合的插件系统支持自定义漏洞检测逻辑，可扩展性强。

## 潜在关注点

- **项目较新**：创建仅约 2 个月，API 稳定性和长期维护仍需观察。
- **安全边界控制**：自动化渗透工具存在被滥用的风险，项目内置了安全边界机制（如 `safety boundary` 可限制仅允许端口、禁止 exploit 等），但部署和使用需注意合规性。
- **模型依赖**：效果高度依赖底层 LLM 能力，弱模型可能无法完成复杂渗透任务。

## 总结

VulnClaw 是一款设计理念先进的 AI 渗透测试工具，其 **Fact/Intent 状态空间搜索架构** 和 **反幻觉证据门控** 是核心技术创新。项目定位 CTF 与授权渗透测试场景，以自然语言交互大幅降低了安全测试门槛。虽然项目尚处于早期阶段，但增长势头良好、社区活跃，值得持续关注其发展。

---

*分析生成时间：2026-06-30*

# TradingView MCP 项目分析

## 项目名称
**TradingView MCP** — 连接 AI 编码代理与 TradingView 桌面端的 MCP 桥接工具
- **GitHub**: [tradesdontlie/tradingview-mcp](https://github.com/tradesdontlie/tradingview-mcp)
- **许可证**: MIT

---

## 项目概述

TradingView MCP 是一个创新性的桥接工具，旨在将 AI 编码代理（如 Claude Code）与本地运行的 TradingView 桌面应用连接起来。项目通过 Chrome DevTools Protocol (CDP) 实现通信，为用户提供 AI 辅助的图表分析、Pine Script 脚本开发以及工作流自动化能力。

该项目的核心架构非常简洁：Claude Code 通过 MCP Server（stdio 协议）与本地 TradingView Desktop（Electron 应用）建立连接，而中间的桥梁正是 CDP 调试协议。所有数据处理均在本地完成，不涉及任何外部数据传输，确保了用户交易数据的安全性和隐私性。

项目强调其非官方性质，明确声明不隶属于 TradingView Inc.，并且要求用户拥有有效的 TradingView 订阅，不绕过任何付费墙。这种合规意识在同类工具中较为难得。

---

## 核心功能

| 功能类别 | 具体能力 | 说明 |
|:---------|:---------|:-----|
| **图表读取** | `chart_get_state`、`data_get_study_values`、`quote_get`、`data_get_ohlcv` | 获取交易品种、时间框架、技术指标值（RSI/MACD/BB/EMA）、实时价格及 K 线数据 |
| **自定义指标数据** | `data_get_pine_lines`、`data_get_pine_labels`、`data_get_pine_tables`、`data_get_pine_boxes` | 读取 Pine Script 绘制的支撑/阻力位、文本标注、数据表格及价格区间 |
| **图表控制** | `chart_set_symbol`、`chart_set_timeframe`、`chart_set_type`、`chart_manage_indicator`、`chart_scroll_to_date` | 切换交易品种、时间周期、图表类型，添加/移除指标，跳转至指定日期 |
| **多面板与标签管理** | `pane_list`、`pane_set_layout`、`tab_list`、`tab_new`、`tab_switch` | 支持 1/2x2/4/6/8 等多种网格布局，以及标签页的创建、切换和关闭 |
| **Pine Script 开发** | 编辑器操作、语法检查、脚本编译、自动修复 | 完整的 Pine Script 开发工作流，支持 AI 辅助编写和调试策略脚本 |
| **CLI 命令** | 30 个独立命令行工具 | 可脱离 Claude Code 独立使用，适合终端用户和自动化脚本 |
| **绘图与标注** | 趋势线、水平线、文本标注管理 | AI 可直接在图表上绘制分析标注 |

---

## 技术栈

| 技术组件 | 详情 |
|:---------|:-----|
| **主要语言** | JavaScript（占比 98.2%） |
| **运行时** | Node.js 18+ |
| **通信协议** | MCP (Model Context Protocol) 通过 stdio 传输 |
| **桥接协议** | Chrome DevTools Protocol (CDP)，端口 9222 |
| **核心依赖** | `@modelcontextprotocol/sdk`、`chrome-remote-interface` |
| **目标应用** | TradingView Desktop（基于 Electron/Chromium） |
| **兼容平台** | macOS、Windows、Linux |
| **AI 代理** | Claude Code（主要）、支持任何具备 MCP 能力的终端 |

架构设计体现了"零外部依赖"理念，仅依赖两个 npm 包即可运行。通过 CDP 协议直接与 TradingView 的 Electron 进程通信，无需 API Key 或云端服务。

---

## 项目亮点

### 1. 极致的工具密度：78 个 MCP 工具 + 30 个 CLI 命令

项目在仅 93 次提交的情况下，实现了 108 个可用工具/命令，展现出极高的开发效率。覆盖了从基础图表读取、指标分析到高级的多面板管理、Pine Script 开发等完整工作流。这种"工具即服务"的设计思路，使得 AI 代理能够对 TradingView 进行几乎全面的程序化操控。

### 2. 本地优先的安全架构

所有数据处理严格在本地完成，不连接 TradingView 服务器，不存储或传输市场数据。通过 CDP 协议仅与本地 Electron 应用通信，避免了云端中间人风险。对于交易场景中极度敏感的行情数据和策略信息，这种架构选择至关重要。

### 3. 双模式运行：MCP 服务器 + 独立 CLI

项目不仅可作为 Claude Code 的 MCP 服务器运行，还提供了 30 个独立 CLI 命令，支持脱离 AI 代理直接在终端使用。这种灵活性大大拓展了适用场景——无论是 AI 驱动的智能分析，还是传统的脚本自动化，都能很好地覆盖。

### 4. Pine Script 开发工作流闭环

项目不仅读取图表数据，还深度集成了 Pine Script 编辑器的操控能力，包括语法检查、脚本编译和自动修复。这意味着 AI 代理可以完成"分析图表 → 识别机会 → 编写策略 → 编译部署"的完整闭环，将 AI 辅助量化交易开发提升到了新的高度。

---

## 应用场景

### 1. AI 辅助量化策略开发

量化交易开发者可以利用 Claude Code 的推理能力，结合 TradingView MCP 提供的实时图表数据和技术指标，快速迭代交易策略。AI 能够直接读取 RSI、MACD、布林带等指标数值，分析市场状态，并自动生成对应的 Pine Script 策略代码，大幅缩短策略研发周期。

### 2. 多品种实时监控与自动化工作流

通过多面板（最高 8 宫格）和标签页管理功能，用户可以同时监控多个交易品种。结合 AI 代理的自动化能力，可实现"扫描品种 → 识别信号 → 切换图表 → 执行分析 → 输出报告"的全自动工作流，适合需要覆盖大量品种的交易员和分析师。

### 3. 交易教育与图表分析辅助

对于交易学习者，该项目可以让 AI 充当"图表分析导师"的角色。AI 可以读取当前图表的技术指标、支撑阻力位、自定义标注等信息，提供结构化的市场分析解读，帮助用户理解价格行为和技术形态。

### 4. Pine Script 插件生态开发

Pine Script 开发者可以利用该项目实现更高效的开发调试流程。AI 代理能够直接在 TradingView 的 Pine Editor 中操作，实现代码编写、语法检查、编译验证的一体化流程，显著降低开发中的试错成本。

---

## Star 数据

| 指标 | 数值 |
|:-----|:-----|
| **⭐ Stars** | 4,633 |
| **🍴 Forks** | 2,161 |
| **Fork/Star 比率** | 46.6%（远高于 GitHub 平均水平，说明用户高度参与） |
| **📝 提交次数** | 93 |
| **📅 创建时间** | 2026 年 3 月 29 日 |
| **📅 分析时间** | 2026 年 7 月 21 日 |
| **📈 增长周期** | 约 4 个月 |
| **日均 Star 增长** | 约 38 Star/天（爆发式增长） |

项目在短短 4 个月内积累了超过 4,600 个 Star 和 2,100 个 Fork，增长速度极其迅猛。高达 46.6% 的 Fork/Star 比率表明大量开发者不仅是"围观"，而是积极参与到项目的使用和二次开发中。这反映出市场对"AI + 交易分析"这一交叉领域的强烈需求，以及 MCP 协议生态的快速扩展势头。

---

## 总结

TradingView MCP 是一个精准定位"AI 代理 × 交易图表分析"交叉领域的创新工具。它巧妙地利用 CDP 协议打通了 AI 编码代理与 TradingView Desktop 之间的壁垒，以极简的技术架构（仅两个核心依赖）实现了 108 个功能工具，覆盖了图表读取、指标分析、Pine Script 开发和工作流自动化等完整场景。

项目在 4 个月内获得 4,600+ Star 的爆发式增长，印证了 MCP 协议生态的蓬勃发展和交易从业者对 AI 辅助工具的迫切需求。其"本地优先"的安全设计、双模式运行架构以及对合规性的重视，都体现了成熟的项目治理理念。

需要注意的是，项目依赖 TradingView 的未公开内部 API，存在因版本更新而失效的风险。此外，自动化数据采集可能与 TradingView 的使用条款存在潜在冲突，用户需自行评估风险。尽管如此，作为 MCP 生态在金融交易领域的标杆级应用，TradingView MCP 为"AI Agent 操控桌面应用"这一新兴范式提供了极具参考价值的实践案例。

*数据来源：GitHub 仓库 (tradesdontlie/tradingview-mcp)，2026 年 7 月访问*
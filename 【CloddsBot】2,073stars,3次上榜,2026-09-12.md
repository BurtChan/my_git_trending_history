# CloddsBot 项目分析

## 项目名称

**CloddsBot** — 开源个人 AI 交易终端：一个 Claude 驱动的自主交易 Agent，覆盖预测市场、加密现货、永续合约与 Bittensor 挖矿

- **GitHub**: [alsk1992/CloddsBot](https://github.com/alsk1992/CloddsBot)
- **许可证**: MIT

---

## 项目概述

CloddsBot（Claude + Odds = Clodds）是一个运行在自己机器上的**个人 AI 交易终端**。用户通过 21 个消息平台（Telegram、Discord、WhatsApp 等）中的任意一个与它对话，即可在 10 个预测市场（Polymarket、Kalshi 等）、7 家期货交易所（Binance、Hyperliquid 等）以及 Solana/EVM 全链 DeFi 上执行交易——扫描机会、即时执行、管理风险，「你睡觉时它也在工作」。

项目为 Colosseum Agent Hackathon（Solana）而建，12 天开发出功能完整的自主交易 Agent。内置 118+ 交易策略、鲸鱼追踪、套利检测、跟单和 DCA 机器人，全部通过自然语言对话驱动。项目自带 CLAUDE 发行的 Solana 代币（Clodds CA），并内置 x402「Agent 商业协议」实现机器对机器支付——Agent 可以用 USDC 钱包直接为计算资源付费，无需 API key。

增长数据同样引人注目：2026 年 1 月创建，14 天内获得 10,700+ 次 git clone，今日单日 +299 Star。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 自然语言交易 | 通过聊天即可下单、查询持仓、调整策略，Claude 理解意图并执行 |
| 21 消息渠道 | Telegram/Discord/WhatsApp/Slack 等全平台接入，WebChat 内置 |
| 1000+ 市场覆盖 | 10 预测市场 + 7 期货交易所 + Solana/EVM 链上 DEX |
| 118+ 交易策略 | 套利、跟单、DCA、鲸鱼追踪等策略库 |
| Token 发射 | 集成 Pump.fun/Raydium/Orca 的代币发射与做市 |
| Compute API | Agent 用 USDC 钱包按需购买 LLM/代码执行/爬虫/存储等计算资源 |
| x402 支付协议 | 机器对机器支付的 Agent 商业协议，无需 API key |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | TypeScript 5.3（含 Rust fast-broadcast 模块） |
| 分发 | npm 全局安装（`npm install -g clodds`） |
| AI | Claude（8 家 LLM 供应商可切换） |
| 区块链 | Solana（Jupiter/Pump.fun/Raydium/Orca）、EVM（Base/ETH/Arbitrum/Optimism/Polygon） |
| 挖矿 | Bittensor TAO subnet |
| 部署 | Docker / docker-compose / systemd |

---

## 项目亮点

### 全对话式交易闭环
从行情扫描到风险管理的完整交易生命周期都浓缩进自然语言对话。30 秒 onboard 向导配置完 API key 和消息渠道即可开始交易，内置 WebChat（`localhost:18789`）提供 Claude 风格的侧边栏界面，支持 Artifacts 自动提取和会话搜索。

### Agent 商业协议先行者
x402 + Compute API 的组合让 Agent 之间可以用稳定币直接结算计算资源——LLM 调用 $0.000003/token、沙箱代码执行 $0.001/秒、交易执行 $0.01/次。这是「Agent 经济」基础设施的早期实物实现。

### 安全与可审计设计
自带 AUDIT.md、SECURITY.md、SECURITY_AUDIT 文档与 OpenAPI 3.0 规范，119 个技能模块化组织，439 次提交的工程节奏配合完整文档体系，在同类 hackathon 项目中工程成熟度罕见。

---

## 应用场景

### 个人量化交易者
不想写代码的交易者用对话即可部署策略组合，覆盖预测市场到期套利、链上土狗狙击、期货杠杆等场景。

### Agent 经济实验者
研究 x402 支付协议与 Agent 间结算的开发者，可直接复用其 Compute API 定价与支付证明流。

### Solana 生态开发者
Pump.fun 发射、Jupiter 聚合、Percolator 链上永续的完整集成代码可作参考实现。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 2,073 |
| 总 Forks | 277 |
| 今日新增 | +556 |
| 创建时间 | 2026-01-26 |
| 主要语言 | TypeScript |
| 许可证 | MIT |

---

## 总结

CloddsBot 把「AI 自主交易」从概念做成了 npm 一行命令即可安装的实物，21 渠道对话 + 1000+ 市场 + x402 Agent 支付的组合在开源交易 Agent 赛道独树一帜，是 Agent 经济基础设施方向的标志性早期项目。

## 📋 更新记录

### 更新 1 — 2026年9月11日

**更新原因**：连续登上 GitHub Trending 榜单（今日 +223 Stars，API 精确数据）

- Star 从 1,294 增至 1,517（+223），Forks 从 238 增至 248（+10）。
- 连续第二日登上 Trending，首日 +299 后次日仍保持 +200 以上增速。
- 定位为加密货币/DeFi 套利 Agent（topics: agi/arbitrage/crypto/defi），仓库最近推送 2026-09-10。

**Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 1,294 | 1,517 | +223 |
| 总 Forks | 238 | 248 | +10 |
| 今日新增 | — | +223 | — |

---

### 更新 2 — 2026年9月12日

**更新原因**：连续登上 GitHub Trending 榜单（今日 +556 Stars，API 精确数据）

**最新动态**：
- CloddsBot 持续受到关注，Star 数继续攀升，社区对「自主 AI 交易代理」方向的兴趣明显升温。
- 项目定位为跨 1000+ 市场（Polymarket、Kalshi、Binance、Hyperliquid、Solana DEX、5 条 EVM 链）自主运行的开源交易代理，基于 Claude 构建，支持 Agent commerce protocol 机器间支付。
- 开源可自托管（Self-hosted）仍是其核心卖点。

**Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|---------|---------|------|
| 总 Stars | 1,517 | 2,073 | +556 |
| 总 Forks | 248 | 277 | +29 |
| 今日新增 | — | +556 | — |

**核心变化**：
- Star 1,517 → 2,073（+556），连续第三天登上 Trending，增势稳定。
- Forks 248 → 277（+29），社区贡献活跃度同步上升。
- 开放 Issue 数约 37，项目处于快速迭代期。

*数据来源：GitHub 仓库 (alsk1992/CloddsBot)，2026 年 9 月访问*
*首次分析：2026 年 9 月 10 日 | 最近更新：2026年9月12日*

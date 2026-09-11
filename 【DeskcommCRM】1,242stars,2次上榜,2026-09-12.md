# DeskcommCRM 项目分析

## 项目名称

**DeskcommCRM** — 开源 AI 销售 OS：自托管 CRM + 原生 AI Agent + WhatsApp 集成，Kommo/Octadesk/Intercom 的开源替代

- **GitHub**: [melgarafael/DeskcommCRM](https://github.com/melgarafael/DeskcommCRM)
- **许可证**: MIT

---

## 项目概述

DeskcommCRM 自称「o Sistema Operacional de Vendas」（销售操作系统），是巴西开发者社区出品的开源 AI CRM。它瞄准一个具体而真实的市场：**靠聊天卖货的中小企业**——WhatsApp 生态里的大量巴西/拉美生意人，原本要在 Kommo、Octadesk、Intercom 这类 SaaS 里付月费。DeskcommCRM 提供自托管替代：原生 AI Agent 处理对话、RAG 知识库回答产品问题、MCP 协议就绪、多租户架构、符合巴西 LGPD 数据保护法。

项目工程化程度极高：3,805 次提交，仓库内能看到完整的 spec 驱动开发痕迹——`.specs/`（Spec Kit 规格）、`.changes/` 变更日志、`.claude/`/`.codex/`/`.agents/skills/` 多套 AI Agent 配置并存，是一个「AI 深度参与开发的开源 SaaS」的活标本。技术栈 Next.js + Supabase + TypeScript，配套 docker scheduler 与 HostGator 部署套件（照顾巴西本地虚拟主机用户）。

今日 +126 Star、总 1,043 Star，458 Fork（Fork 比例异常高，自托管部署需求驱动）首次登榜。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 自托管 CRM | 多租户架构，销售管道与客户管理全部数据自持 |
| 原生 AI Agent | 对话式销售代理，自动应答与跟单 |
| WhatsApp 集成 | 通过 WAHA 网关接入 WhatsApp API，聊天即成交渠道 |
| RAG 知识库 | 产品资料检索增强，AI 回答有据可依 |
| MCP 就绪 | Model Context Protocol 支持，可接入外部工具生态 |
| LGPD 合规 | 巴西通用数据保护法开箱合规 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 前端/全栈 | Next.js + TypeScript |
| 后端/数据 | Supabase（Postgres） |
| 消息网关 | WAHA（WhatsApp HTTP API） |
| 部署 | Docker + scheduler、HostGator 部署套件 |
| 开发方式 | Spec Kit 规格 + Claude/Codex Agent 协作 |

---

## 项目亮点

### 精准的差异化定位
不做通用 CRM，而是「聊天卖货场景的 AI 销售操作系统」，用 WhatsApp + AI Agent + 自托管三板斧对抗 SaaS 月费，在拉美市场有天然土壤。

### 规范的 Spec 驱动 + AI 协作开发
.specs/.changes/.claude/.codex 多目录展示了 AI 时代开源项目的工程范式：规格先行、Agent 执行、变更留痕。

### 高 Fork 密度
458 Fork / 1,043 Star 接近 44%，说明大量用户是拿来部署而非围观，自托管 SaaS 的真实需求可见一斑。

---

## 应用场景

### WhatsApp 电商与私域销售
以聊天为主要成交渠道的中小商家，AI Agent 7×24 接待 + 人工接管。

### 需要数据自持的销售团队
对客户数据出境敏感（LGPD/GDPR 类合规要求）的企业，自托管 CRM + 本地 RAG。

### 二次开发的 SaaS 创业者
MIT 协议 + 多租户 + 完整部署套件，适合作为垂直行业 CRM 的起点。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 1,242 |
| 总 Forks | 478 |
| 今日新增 | +199 |

---

## 总结

DeskcommCRM 是「AI Agent + 自托管」两股潮流在 CRM 赛道的交汇点，用 WhatsApp-native 的姿态服务被 SaaS 定价劝退的聊天卖货人群。

---

*数据来源：GitHub 仓库 (melgarafael/DeskcommCRM)，2026 年 9 月访问*
*首次分析：2026 年 9 月 11 日 | 最近更新：2026年9月12日*

---

## 📋 更新记录

### 更新 1 — 2026年9月12日

**更新原因**：再次登上 GitHub Trending 榜单（今日 +199 Stars，API 精确数据）

**最新动态**：
- DeskcommCRM 是开源自托管 AI 销售 OS：原生 AI Agent + WhatsApp（WAHA）集成，定位 Kommo、Octadesk、Intercom 的开源替代。
- 支持 MCP、多租户，面向巴西市场（LGPD 合规）的聊天式销售场景。
- 上榜次日增长持续，Star 突破 1,200。

**Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|---------|---------|------|
| 总 Stars | 1,043 | 1,242 | +199 |
| 总 Forks | 458 | 478 | +20 |
| 今日新增 | — | +199 | — |

**核心变化**：
- Star 1,043 → 1,242（+199），连续第二天登上 Trending。
- Forks 458 → 478（+20），Fork 基数大（自托管部署需求强）。
- 开放 Issue 数约 86。

# OpenBot (CopilotKit) 项目分析

## 项目名称
**OpenBot** — 企业可真正拥有的开源 AI 同事平台：每个 Bot 一台专属电脑，所有动作先经策略裁决、后留审计记录
- **GitHub**: [CopilotKit/OpenBot](https://github.com/CopilotKit/OpenBot)
- **许可证**: MIT

---

## 项目概述

OpenBot 是 CopilotKit 团队推出的开源 Agent 平台，定位是「你的公司能真正拥有的 AI 助手」——形态上和 ChatGPT/Claude/Grok 一样是对话式助手，但根本差异在于：它完整运行在你自己的基础设施上，模型自选、数据落在你自己的 PostgreSQL、每一处都可以改。项目明确自称「模板而非产品」：没有托管版本、没有可依赖的 npm 包，克隆仓库、替换 `examples/` 下的租户包、填入自己的同事/频道/技能后即可运行。

它的核心隐喻是「每个同事一台电脑」：每个 Bot 由 supervisor 分配一个独立容器，里面有专属 Chromium 浏览器（独立登录态与浏览器档案）、`/workspace` 工作区卷和受控的 shell。Bot 可以浏览网页、填表单、跑命令、处理文件，但**所有**工具调用都必须经过唯一的网关——网关解析目标、按 CEL 策略裁决（deny 优先于 allow、缺策略即拒绝、规则损坏也拒绝）、写入审计行，然后才执行或点名规则拒绝。这解决了 Agent 落地企业最核心的治理问题：一个「能用你工具的 Agent」和一个「你可以放心让它接触工具的 Agent」之间的差距。

互联互通基于 AG-UI 开放协议（agent-to-user 交互协议）：任何讲 AG-UI 的端点都可以成为一个 Bot，无论用 LangGraph、Mastra、CrewAI、Pydantic AI、Google ADK 构建还是手写，治理随协议而非框架走。项目由 CopilotKit（AG-UI 协议的主要推动者）出品，创建于 2026 年 8 月，10 月进入 v0.2.0，当前处于 Beta 阶段但迭代极快，上榜首日即冲到 Trending 第 3 位（trendshift 当日 #3）。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 每 Bot 一台电脑 | 独立容器 + `/workspace` 卷 + 独立浏览器档案，支持 gVisor（`COMPUTER_RUNTIME=runsc`）硬隔离 |
| 网关即唯一入口 | 解析目标 → CEL 策略裁决 → 审计落库 → 才执行；不存在绕过审计的执行路径 |
| CEL 策略、默认失败关闭 | 规则可检视 `tool.name`/`intent`/`page.url`/`command`/`file.*`/`mcp.*`/`initiator.*` 等，可按发起者区分（拒绝定时任务但放行人工触发） |
| 实时观看与接管 | 屏幕直播 Bot 正在看什么，Activity 标签显示它跑过/读过/存过什么；撞到登录墙或 2FA 时请求人工接管，交接全程留痕 |
| 带来任意 Agent | 任何 AG-UI 端点即 Bot，端点注册与重定向都做目标校验，私有地址默认拒绝（白名单 `AGENT_ENDPOINT_ALLOWED_HOSTS`） |
| 组件而非纯文本回复 | 沙箱化 React 组件在 `/admin/playground` 浏览器内编写、免部署发布，每次调用都校验组件存在且未被对该 Bot 隐匿 |
| 受治理的 MCP | 内置 Google Drive/Notion/Parallel/Exa/Firecrawl 目录，Composio 中转数百应用；未知工具一律按写操作对待 |
| 例行任务（Routines） | 按日程让 Bot 以你的身份在指定频道干活；15 分钟下限、20 条上限、连续 10 次失败自动熔断 |
| 企业身份与审计 | Google/Microsoft/Okta/SAML/OIDC 登录（按邮箱域路由），`/admin/audit` 可读的审计轨迹，每条拒绝都带触发规则 |
| 密钥不出现在转录 | 凭证静态加密、API 永不回传、审计事件只记「请求过密钥及长度」不记内容 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 前端 | React + Vite（app，端口 3010） |
| 后端 | Hono API server + CopilotKit runtime（3001） |
| Bot 电脑 | Chromium 容器 + /workspace（agent-computer，4100），gVisor 可选 |
| Agent 接入 | AG-UI 协议（内置 OpenAI PoC Bot + LangGraph Bot 示例） |
| 数据 | PostgreSQL + pgvector（策略/审计/凭证/授权/组件元数据） |
| 记忆与线程 | CopilotKit Intelligence（可托管可自托管，免费 Developer 计划可本地跑） |
| 部署 | Docker Compose 一键起；单镜像含内嵌 PostgreSQL，无需 Kubernetes |
| 运行时 | Bun 1.4+（app、API、测试） |

---

## 项目亮点

### 治理优先的 Agent 架构
「先裁决、后执行、必留痕」不是口号而是架构约束：网关是唯一通道，审计行先于执行写入，Cel 策略默认失败关闭。`initiator.*` 维度甚至能区分「人发起的运行」与「定时任务发起的运行」——这是企业 Agent 治理里少见的细粒度设计。

### 真正的「模板而非产品」哲学
不发布包、不做托管、所有 workspace 私有——OpenBot 的商业设计是「我们帮你建，或和你一起建」（CopilotKit 的工程服务入口就放在 README 顶部），开源本身即获客与信任建设。对使用者来说，这意味着零锁定：拿走代码就拥有全部。

### AG-UI 生态的战略卡位
Bot 不绑定任何 Agent 框架，LangGraph/Mastra/CrewAI/手写端点以同一种方式接入，治理骑在协议上。CopilotKit 借此把 AG-UI 从「交互协议」升级为「企业 Agent 接入的事实标准入口」，与 OpenMausBot 等「自带 CLI Agent」路线形成鲜明互补。

### 开箱即用的企业样本
`examples/fintech/` 附带 12 个预置同事（通用助手、知识问答、风险分析师 + 费用审核/会议纪要/发布说明/工单分诊/新人答疑/访谈整理/续约盘点/客服反馈聚类等），每个都是一个目录下的配置而非代码——复制、改写、上手成本极低。

---

## 应用场景

### 企业内部 Agent 平台自建
数据不出自有 PostgreSQL、模型凭证自己管、每一步可审计——适合对合规和数据主权有硬要求的金融/医疗/政企场景，SAML/OIDC 对接存量身份体系。

### Agent 治理与安全研究
CEL 策略引擎、fail-closed 语义、审计轨迹设计本身就是一份「Agent 治理怎么做」的参考实现；`/admin/boundaries` 可以实时加 deny 规则并重放同一浏览器动作验证效果。

### 多框架 Agent 的统一门面
团队里已有 LangGraph 工作流、手写 Agent、CrewAI 编排？各自讲 AG-UI 接进来，共享同一套治理、审计、频道与审批体系，不必迁移框架。

### 内部工具的「同事化」改造
费用审核、工单分诊、发布说明这类流程性工作，用预置模板配上自家政策文档即可变成一个可观察、可接管的数字同事，通过 Slack/Teams/短信继续对话。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 8,650 |
| 总 Forks | 1,097 |
| 今日新增 | +758 stars（API 口径） |
| Open Issues | 64 |
| 主要语言 | TypeScript |
| 创建时间 | 2026-08-17 |
| 最新版本 | v0.2.0（2026-10-12） |
| 许可证 | MIT |

---

## 📋 更新记录

### 更新 1 — 2026 年 11 月 1 日

**更新原因**：再次登上 GitHub Trending（第 2 次上榜），Stars 从 7,892 增长至 8,650（+758，API 精确数据），Forks 从 1,036 增至 1,097（+61），Open Issues 55 → 64。

**最新动态**：OpenBot 迭代极快，近两日合流多项核心能力：Bot 独立浏览器与内置 Recorder（在 Bot 自己的浏览器中记录任务）、按请求隔离的「一人一机」计算环境、会话底部开口与 turns 栏 UI 改进，以及标准目录 Bot 授权收窄（默认授予整个标准目录但排除四项）。README 新增 GitHub Trending #5 徽章，社区热度延续。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 7,892 | 8,650 | +758 |
| 总 Forks | 1,036 | 1,097 | +61 |
| 今日新增 | +240 | +758 | — |
| Open Issues | 55 | 64 | +9 |

**核心变化概要**：

1. Stars 7,892 → 8,650（+758），第 2 次上榜，今日 Trending #5
2. Bot 独立浏览器 + Recorder 内置，「一人一机」隔离计算环境落地
3. UI 迭代：会话底部开口、turns 栏、窄分栏折叠等体验优化

---

## 总结

OpenBot 把「企业级 Agent 平台」最难也最容易被开源方案忽略的部分——策略网关、审计轨迹、fail-closed 治理——做成了默认架构，再用 AG-UI 协议把框架锁死问题一并解掉；它不是又一个 Agent 框架，而是让公司「拥有」而非「租用」AI 同事的那张模板。

---

*数据来源：GitHub 仓库 (CopilotKit/OpenBot)，2026 年 10 月访问*
*首次分析：2026 年 10 月 30 日 | 最近更新：2026 年 11 月 1 日*

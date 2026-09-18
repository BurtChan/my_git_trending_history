# GitDiagram 项目分析

## 项目名称
**GitDiagram** — 把任意 GitHub 仓库在几秒内变成可交互的架构图
- **GitHub**: [ahmedkhaleel2004/gitdiagram](https://github.com/ahmedkhaleel2004/gitdiagram)
- **许可证**: MIT

---

## 项目概述

GitDiagram 是一款开源的「仓库可视化」工具：输入任意公开或私有 GitHub 仓库地址，它会在几秒内自动生成一张**系统级架构图**，并把图中每个组件与其真实源码文件/目录链接起来。用户还可以玩一个小技巧——把 GitHub URL 中的 `hub` 改成 `diagram`，即可直接打开该仓库的架构图（gitdiagram.com）。

与「画文件夹树」类工具不同，GitDiagram 定位 **architecture-first**：它抓取仓库的文件树、README 和有界的源码摘录，交给大模型（默认 OpenAI GPT-5.6 Sol，低推理档位）生成带分组、节点、边、形状与标签的图 AST，再经确定性编译器转为 Mermaid 渲染。生成过程采用**流式输出**，解释文本与图结构边生成边展示。

项目由个人开发者 ahmedkhaleel2004 维护，上线后快速增长，目前已有 1.6 万 Star，是「AI 读代码」赛道中工具链闭环最完整的可视化方案之一。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 架构级图表 | 解析仓库树+README+源码摘录，生成系统级架构图而非目录树 |
| 交互式源码链接 | 点击图中组件直接跳转 GitHub 上的真实文件/目录 |
| 流式生成 | 图规划与英文架构解说流式到达，无需整页等待 |
| 私有仓库支持 | 浏览器本地提供细粒度 GitHub Token，私有产物存独立受保护命名空间 |
| 导出 | 复制 Mermaid 源码或下载 PNG 渲染图 |
| 多 Provider | 默认 OpenAI，自托管可切换 OpenRouter |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 应用 | Next.js 16 App Router、React 19、TypeScript、Tailwind CSS、Radix UI |
| 生成 API | 同源 Next.js Route Handlers（Vercel Bun 运行时） |
| 存储 | Cloudflare R2（图表产物） |
| 协调 | Upstash Redis（配额、取消、锁、短时失败态） |
| AI | OpenAI / OpenRouter |
| 分析 | PostHog |
| 部署 | Vercel 为唯一生产运行时，保留 Railway/Docker 冷备方案 |

---

## 项目亮点

### 两阶段生成 + 严格验证
第一模型阶段流式输出架构解说，第二阶段返回受尺寸约束的图 AST；服务器验证标识符、连通性、规模与每个链接路径是否真实存在于仓库，非法输出带聚焦反馈重试（Luna 修复模型仅在结构校验失败时调用）。

### 确定性编译与纵深安全
验证后的 AST 由确定性编译器转为全转义的 Mermaid（仅允许 GitHub 链接）；浏览器端再对源码做 sanitize、以严格安全模式渲染、对结果 SVG 二次 sanitize 并重放链接白名单——三层防线防止模型输出注入。

### 工程化配额与状态管理
长任务跑在 Vercel 300 秒函数预算内，应用层 deadline 更短以保证配额对账与落盘完成；显式上游 deadline、重试、结构化日志、心跳与分布式取消（Redis 锁 + newest-session-wins 持久化），成功产物持久化到 R2，重访不再消耗模型调用。

### 极简且诚实的架构
README 明确声明「没有独立的 FastAPI 实现、没有 Postgres、没有 Neon 运行时」，全部能力收敛在单一 Next.js 应用中，Docker/Railway 仅作灾备冷启动配方。

---

## 应用场景

### 新仓库快速摸底
接手陌生代码库时，先生成一张架构图建立全局认知，再按图索骥点击进入关键模块源码，显著降低上手成本。

### 技术评审与文档
将 Mermaid 源码导出到文档/PR 描述中，为架构评审提供可版本化的图形材料。

### 团队 onboarding
新成员通过交互式图表自助理解系统分层与依赖关系，减少口头讲解成本。

### 私有代码库审计
在企业内部仓库上使用（Token 仅在浏览器本地提供），快速获得第三方依赖与模块边界的可视化视图。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 16,232 |
| 总 Forks | 1,250 |
| 今日新增 | +145 |
| 创建时间 | 2024 年 12 月 15 日 |
| 开源协议 | MIT |
| 主要语言 | TypeScript |

---

## 总结

GitDiagram 把「AI 理解代码库」这件事从纯文本摘要升级为可交互的架构图，并用两阶段生成、严格验证与确定性编译保证了图的准确性与安全性，是 AI 辅助代码认知工具中工程完成度很高的代表作。

---

*数据来源：GitHub 仓库 (ahmedkhaleel2004/gitdiagram)，2026 年 9 月访问*

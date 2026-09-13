# Ever Gauzy 项目分析

## 项目名称
**Ever Gauzy** — 面向协作/按需/共享经济的开源企业经营管理平台（ERP/CRM/HRM/ATS/PM 一体化）
- **GitHub**: [ever-co/ever-gauzy](https://github.com/ever-co/ever-gauzy)
- **许可证**: AGPL-3.0

---

## 项目概述

Ever Gauzy 是 Ever 公司打造的开源商业管理平台，把 ERP（企业资源计划）、CRM（客户关系管理）、HRM（人力资源管理）、ATS（招聘追踪）与项目管理（PM）整合进同一套系统，并配套员工工时追踪与生产力监控。项目始于 2019 年，至今累计 27,000+ 次提交，是开源 ERP 赛道中工程投入最重的项目之一。

平台采用 Headless API 架构（API 文档公开），前端为 Angular，后端为 NestJS，使用 Nx monorepo 管理，可自托管（Docker Compose / Render / Fly.io 配置齐备），也可使用官方 SaaS（gauzy.co）。母公司 Ever 生态还包括 Ever Teams（工作生产力平台）与刚发布的 Ever Works（自主运营企业的开放 Agent 运行时），后者是本次登上 Trending 的直接导火索——README 顶部大力宣传 Ever Works，为其导流大量关注。

对中小团队而言，它的价值在于「一套系统替代 ERP+CRM+HR SaaS 组合」：会计/发票、销售管道、目标 KPI、库存供应链、请假审批、多组织多币种多语言，功能覆盖面远超同类轻量开源方案。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| ERP 套件 | 会计、开票、估价、收支管理、库存与供应链 |
| CRM | 联系人/线索/客户管理、销售管道、提案 |
| HRM/ATS | 员工档案、入职流程、招聘追踪、面试管理 |
| 工时追踪 | 时间管理、活动追踪、排班、Timesheets |
| 项目管理 | 任务、目标/KPI/OKR、团队部门 |
| Headless API | 完整 REST API，支撑 Ever Teams 等前端 |
| 集成生态 | Upwork、HubStaff 等第三方集成、邮件模板、导入导出 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 前端 | Angular + Angular Material |
| 后端 | NestJS (Node.js) + TypeORM |
| 架构 | Nx monorepo、lerna、微服务化 packages |
| 数据库 | PostgreSQL（兼容多种） |
| 部署 | Docker Compose、Render、Fly.io、DigitalOcean |
| 质量 | Jest、Codacy、Sonar、commitlint、Husky |

---

## 项目亮点

### 工程成熟度罕见
27,628 次提交、完善的 CI/lint/测试体系（Jest/Codacy/Sonar/crowdin 国际化），七年持续迭代，代码库本身就是大型 NestJS+Angular monorepo 的工程范本。

### 全模块一体化的开源替代
ERP+CRM+HRM+ATS+PM+工时追踪一体化，配合 Ever Teams 移动/桌面端，可以整体替代 Odoo 之外的多套 SaaS 组合，AGPL-3.0 对自托管友好。

### Agent 时代的新故事
官方新发布的 Ever Works 号称「24/7 自主研究、交付并维护整个业务的开放 Agent 运行时」，把传统 ERP 与 Agentic 工作流挂钩，是本轮 Trending 关注度的来源。

---

## 应用场景

### 中小企业一体化管理
一家公司用一套自托管系统跑完财务开票、客户管理、招聘、考勤与项目管理，避免多套 SaaS 数据孤岛。

### 二次开发底座
Headless API + monorepo 结构适合在其上构建垂直行业管理系统，社区有大量集成示例。

### ERP/HR SaaS 创业原型
AGPL 开源 + Docker 一键部署，创业团队可以极低成本验证产品想法，再决定商业化路径。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 4,510 |
| 总 Forks | 895 |
| 今日新增 | +58 |
| 主要语言 | TypeScript |
| 许可证 | AGPL-3.0 |
| 创建时间 | 2019-06-02 |

---

## 总结

Ever Gauzy 是开源世界里少见的「全家桶式」企业经营管理平台——七年打磨的 NestJS+Angular 工程底座加上 ERP/CRM/HRM 全模块覆盖，借 Ever Works Agent 运行时发布的热度重回大众视野，是自托管企业管理软件的务实选择。

---

*数据来源：GitHub 仓库 (ever-co/ever-gauzy)，2026 年 9 月访问*

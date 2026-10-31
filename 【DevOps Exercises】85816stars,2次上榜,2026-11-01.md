# DevOps Exercises 项目分析

## 项目名称
**devops-exercises** — 覆盖 Linux、Kubernetes、Docker、AWS、Terraform、CI/CD 等 60+ 技术主题的 DevOps/SRE 面试题与练习库（2,624 道题）
- **GitHub**: [bregman-arie/devops-exercises](https://github.com/bregman-arie/devops-exercises)
- **许可证**: CC-BY-SA-4.0（NOASSERTION，Creative Commons 署名-相同方式共享）
- **语言**: Markdown（纯文档知识库）
- **作者**: Arie Bregman（DevOps/SRE 资深从业者，另维护 python-exercises、go-exercises 等姊妹仓库）

---

## 项目概述

devops-exercises 是 GitHub 上最知名的 DevOps 学习与面试准备资源之一，累计 2,624 道练习题与问答题，覆盖从操作系统到云原生的完整技术图谱：Linux、Git、网络、虚拟化、DNS、Bash/Shell、Kubernetes、Docker、OpenShift、CI/CD、Jenkins、GitLab、Circle CI、Ansible、Terraform、Puppet、AWS、Azure、GCP、OpenStack、Prometheus、Grafana、Argo、Elastic、Kafka、SQL/NoSQL、MongoDB、大数据、可观测性、混沌工程、安全、系统设计、软技能等。

项目采用「主题目录 + 问答式练习」的组织方式：每个主题一个 README，问题后附答案（答案通常紧跟在问题块之后），部分主题配有专门的练习场景（如 coding/python、coding 下的动手练习）。此外还提供 **证书备考专题**（AWS Cloud Practitioner、Solutions Architect、AZ-900、CKA 等）和 **面试准备指南**（prepare_for_interview.md），以及 Google Play 上的配套 App（KubePrep、Linux Master、System Design Hero）。

这是一个长青项目：多年积累与持续社区贡献（796 commits）使其内容深度和广度都极为扎实。本次登上 Trending（+341/日）反映 DevOps/AI 时代运维技能学习需求的持续热度——在 AI 编码工具普及的背景下，基础设施与运维知识反而成为工程师的差异化竞争力。

---

## 核心功能

| 功能 | 说明 |
| --- | --- |
| 2,624 道问答练习 | 覆盖 60+ 技术主题，问答形式附答案，适合系统学习与面试冲刺 |
| 主题知识图谱 | DevOps/Git/网络/K8s/容器/CI-CD/云平台/数据库/可观测性/安全/系统设计等分类目录 |
| 证书备考专题 | AWS CPA/SAA、AZ-900、CKA 等认证的专项题库 |
| 面试准备指南 | prepare_for_interview.md 提供面试策略与常见流程建议 |
| 配套移动 App | KubePrep、Linux Master、System Design Hero（Google Play） |
| 多语言版本 | 英文为主，含中文（README-zh_CN）与葡语版本 |
| 姊妹练习库 | python-exercises、go-exercises 提供配套编程练习 |

---

## 技术栈

| 组件 | 技术 |
| --- | --- |
| 内容形式 | 纯 Markdown 知识库（无代码框架依赖） |
| 测试/CI | Travis CI（历史配置）+ GitHub Actions workflows |
| 贡献模型 | 社区 PR 贡献题目（CONTRIBUTING.md 规范） |
| 语言覆盖 | 英语（主）、简体中文、葡萄牙语 |

---

## 项目亮点

### 极广且成体系的知识覆盖

从 DNS、Bash 脚本这类基础，到 K8s、服务网格、混沌工程这类云原生进阶，再到系统设计与软技能——2,624 道题几乎构成了一份完整的 DevOps/SRE 岗位能力大纲，这在单一仓库中极为罕见。

### 问答式学习优于被动阅读

每道题先呈现问题（面试官视角），答案紧随其后，读者可以先自测再看答案。这种主动回忆式学习对面试准备特别有效，也被大量培训机构和大学课程引用为教材。

### 长青社区与持续维护

796 commits、20.5K forks 的社区规模意味着题目持续被纠错和补充；作者同时维护多个配套练习仓库，形成完整的「运维学习宇宙」。老而弥坚，多年后仍在 Trending 榜单出现即是生命力的证明。

### 配套认证路径

CKA、AWS SAA、AZ-900 等专项备考文件将泛学习与认证目标直接挂钩，为求职者提供了可执行的路径。

---

## 应用场景

### DevOps/SRE 岗位面试准备

按目标岗位的主题清单逐主题过题，配合证书备考专题，是最直接的使用方式。

### 团队内训与知识考核

技术团队可用题库做内部分享、新人培训的考核题源，或用于模拟面试。

### 系统学习 DevOps 知识体系

对想转入运维/平台工程的开发者，按主题目录顺序学习可获得完整知识框架。

### 面试官出题参考

反向使用：面试官可从题库挑选或改编题目，快速组装一场有深度的技术面试。

---

## Star 数据

| 指标 | 数值 |
| --- | --- |
| 总 Stars | 85,816 |
| 总 Forks | 20,536 |
| 今日新增 | +233 |
| 首次上榜 | 2026-10-31（2 次上榜） |

## 📋 更新记录

### 更新 1 — 2026 年 11 月 1 日

**更新原因**：次日继续登上 GitHub Trending（第 2 次上榜），今日 +233 stars（API 口径），Star 85,583 → 85,816，Forks 20,521 → 20,536（+15），Open Issues 56。

**最新动态**：
- 2,624 道题覆盖 Linux/K8s/AWS/Terraform/Prometheus 等 60+ 主题，含 AWS/Azure/CKA 认证备考路径
- 长青学习库型项目（796 commits、20.5K forks）回榜，DevOps/SRE 技能学习需求稳定
- 配套 KubePrep / Linux Master 等 Google Play 应用形成学习生态闭环

**核心变化概要**：
- 连续第二日在榜，+233 stars 符合长青项目自然增速
- Forks +15，社区贡献稳定
- 问答式主动学习模式在 AI 时代仍是面试备考刚需

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 85,583 | 85,816 | +233 |
| 总 Forks | 20,521 | 20,536 | +15 |
| 今日新增 | +341 | +233 | — |

---

## 总结

2,624 道题覆盖 60+ 主题的 DevOps/SRE 长青学习库，以问答式主动学习 + 认证备考路径 + 20K forks 社区沉淀，成为运维领域事实上的开源标准教材。

---

*数据来源：GitHub 仓库 (bregman-arie/devops-exercises)，2026 年 11 月 1 日访问*
*首次分析：2026-10-31 | 最近更新：2026-11-01*

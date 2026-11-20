# App Store Compliance 项目分析

## 项目名称
**App Store Compliance Playbook** — 避免 iOS/Android 应用被应用商店拒绝的开源合规手册与预提交自动检查工具
- **GitHub**: [mjmirza/app-store-compliance](https://github.com/mjmirza/app-store-compliance)
- **许可证**: OpenRoots Agent License 2.3（2026-08-24 前的历史版本保留 MIT/CC BY 4.0）
- **语言**: Shell / Python（数据与规则以 JSON 为主）

---

## 项目概述

App Store Compliance Playbook 的目标一句话概括：**让「被应用商店拒绝」从随机事故变成设计上不会发生的失败模式（designed-out failure mode）**。它把 Apple App Store 与 Google Play 两大商店的审核规则整理成一份持续维护的开源手册，收录了 **117 种有据可查的拒绝模式（rejection patterns）及其修复方案**，并配套一个可在提交前运行的自动检查守卫（pre-submission guard）。

项目最有价值的定位是它对审核流程的本质理解：作者把商店审核员视为「一个只跑一次、在真机运行、无法读取你的意图、也没有耐心排查配置的对抗性集成测试」。演示账号缺失、后端未上线、权限字符串没有真实用途、隐私表单与运行时行为不符——每一个都是确定性拒绝，而每一个都可以在按下提交按钮之前被拦截。

除了历史拒绝模式，项目还跟踪 **95 个监管截止日期**（EU AI Act、DSA、COPPA、各州年龄法等），为面向儿童/欧洲市场的开发者提供合规时间线预警。同时它原生面向 AI 编码代理：以 Claude Code Skill 的形式分发，让代理在写完应用后直接跑一次合规体检。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 117 种拒绝模式库 | 每条均标注 Apple/Google 官方指引编号与修复方案，数据存于 `data/rejection-patterns.json` |
| 预提交守卫 | 终端两条命令即可扫描项目，输出潜在拒绝风险清单，2 分钟完成首次检查 |
| 隐私清单与 Data Safety 校验 | 核对 Apple Privacy Manifest 与 Google Data safety 表单和运行时行为是否一致 |
| 95 个监管截止日期跟踪 | 覆盖 EU AI Act、数字服务法（DSA）、COPPA、美国各州未成年人年龄法等 |
| AI 代理 Skill | 可安装进 Claude Code 等 AI 编码工具，代理可自主运行合规检查（`doctor` 诊断模式） |
| 申诉手册 | 已被拒时的 appeal playbook，10 分钟内定位最可能的拒绝原因并撰写申诉 |
| 元数据审计 | `scripts/metadata-audit.py` 检查应用名称/截图/描述中的违禁词与误导性声明 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 规则数据 | JSON（rejection-patterns / detection-recipes / regulatory-deadlines） |
| 检查脚本 | Python + Shell（install.sh / validate.py / metadata-audit.py） |
| 引用生成 | `scripts/generate-references.py` 从数据自动生成 references/ 文档 |
| AI 集成 | Claude Code Skill（agent-os 目录）、AGENTS.md 代理协议 |
| 文档站 | GitHub Pages（mjmirza.github.io/app-store-compliance） |
| CI | GitHub Actions（每个规则变更自动验证引用来源） |

---

## 项目亮点

### 一切事实可溯源
项目的「唯一标准」是：每一条事实性声明都必须追溯到 Apple 或 Google 的现行官方文档，绝不发明指引编号或统计数据。CI 会自动验证引用有效性，规则库因此可以放心作为团队合规 checklist 使用。

### 审核员即对抗性测试的工程化思维
不把上架审核当作玄学，而是当作一次性的对抗性集成测试来对待。所有检查项都围绕「审核员在真机上需要看到什么」设计，将模糊的「经验」转化为可执行、可自动化的确定性检查。

### 监管合规的前瞻覆盖
不仅覆盖两大商店的现行审核规则，还跟踪 EU AI Act 等尚在分阶段生效的法规截止日期。对出海开发者而言，这相当于把「法务要盯的事」变成了版本化的数据文件。

### 为 AI 编码代理而生
2026 年的独立开发者大量使用 Claude Code/Codex 写应用，但上架合规仍是盲区。该项目以 Skill 形式嵌入代理工作流，把「写完就提交」升级为「写完先体检」，补齐了 AI 开发闭环的最后一环。

---

## 应用场景

### 独立开发者首次上架
第一次提交 iOS/Android 应用时最容易踩隐私政策、演示账号、权限说明等坑。提交前跑一次守卫脚本，按拒绝模式库自查，可以把最常见的首轮拒绝消灭在提交之前。

### 被 App Store 拒绝后的快速申诉
打开申诉手册，按症状匹配 117 种模式中的具体条目，获得该模式下社区验证过的申诉写法与修复步骤，把反复试错的申诉周期压缩到一天以内。

### 团队级合规流水线
把守卫脚本接入 CI，使每次构建都自动检查隐私清单与 Data Safety 一致性；配合截止日期数据，团队可以提前规划儿童隐私、欧盟合规等功能排期。

### AI 辅助开发工作流集成
在 Claude Code 中安装 Skill 后，代理在生成应用代码的同时即执行合规约束（权限最小化、隐私声明同步等），从源头减少需要人工返工的合规问题。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 2,591 |
| 总 Forks | 168 |
| 今日新增 Stars | 874 |
| 创建时间 | 2026-06-06 |
| 主要语言 | Shell / Python |
| Open Issues | 32 |
| 许可证 | OpenRoots Agent License 2.3 |

## 📋 更新记录

### 更新 1 — 2026 年 11 月 20 日（第 2 次上榜）

**更新原因**：再次登上 GitHub Trending（第 2 次上榜），总 Stars 从 1,515 增至 1,695（+180，API 精确数据）。

**最新动态**：11 月 14-15 日密集发布 v2.3.0（deadline provenance 与 November sweep）与 v2.4.0（upload paths、iOS 13 最低版本、IPv6、debuggable 与 64-bit ABI 检查），并补入亚太区监管截止日期；Forks 115 → 122（+7）；Open Issues 27 → 32（+5）。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| Stars | 1,515 | 1,695 | +180 |
| Forks | 115 | 122 | +7 |
| 今日新增 | 542 | 180 | — |
| Open Issues | 27 | 32 | +5 |

**核心变化概要**：

1. 两日连发 v2.3.0 与 v2.4.0，检查项扩展至上传路径、IPv6 与 ABI 层面
2. Stars 1,515 → 1,695（+180），连续两天在榜
3. 监管截止日期库完成 November sweep，新增 6 个已验证截止日期


---
### 更新 2 — 2026 年 11 月 21 日（第 3 次上榜）

**更新原因**：连续第三日登上 Trending，单日新增 874 Stars（Trending 快照），Star 总数从 1,695 跃升至 2,591（+896），增速显著加快。

**最新动态**：

Star 从 1,695 增长至 2,591（API 精确值 +896），上榜第三天单日增量从 +180 放大到近 900，进入爆发期。Fork 从 122 增至 168（+46），社区参与度同步抬升。

内容侧持续高频更新：拒绝模式库扩展至 117 种（此前为 117 种并持续修正措辞），监管截止日期库维持 95 个（EU AI Act、DSA、COPPA、各州年龄法）的 November sweep 状态，CHANGELOG 沿用两日一版的节奏。

许可信息确认：项目当前以 OpenRoots Agent License 2.3（SPDX LicenseRef-OpenRoots-ORA-2.3）发布，2026 年 8 月 24 日前的历史版本仍保留 MIT/CC BY 4.0 条款；企业集成前需注意该许可证与 MIT 的差异。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 1,695 | 2,591 | +896 |
| 总 Forks | 122 | 168 | +46 |
| 今日新增 | 180 | 874 | — |
| Open Issues | 32 | 32 | +0 |

**核心变化概要**：
- Star 从 1,695 增长至 2,591（+896），第 3 次上榜，连续第三日在榜，单日增量放大近 5 倍
- Fork 从 122 增至 168（+46），独立开发者与合规团队同步涌入
- 许可证确认为 OpenRoots Agent License 2.3，企业集成需评估与 MIT 的差异


## 总结

App Store Compliance Playbook 把应用商店审核从「碰运气」变成可工程化的确定性流程——117 种拒绝模式、95 个监管截止日期、预提交自动守卫与 AI 代理 Skill 四件套，让任何 iOS/Android 开发者都能在提交前把最常见的拒绝原因排查干净，是 2026 年独立开发与 AI 辅助开发工作流中非常实用的合规基础设施。

---

*数据来源：GitHub 仓库 (mjmirza/app-store-compliance)，2026 年 11 月访问*
*首次分析：2026 年 11 月 | 最近更新：2026 年 11 月 21 日*

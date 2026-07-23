# Open Code Review 更新

## 📰 最新动态

### 2026年7月24日 — Star 数从 4,647 暴增至 11,336，增长超 140%

Alibaba 开源代码审查工具 Open Code Review 经历了爆发式增长，Star 数从上次分析时的 4,647 增长至 11,336，增幅超过 140%。今日单日新增 265 颗 Star，在 Trending 榜上持续保持存在感。

项目开发节奏极为活跃，近期连续发布 v1.7.13（7月20日）、v1.7.14（7月21日）、v1.7.15（7月22日）三个版本。关键改进包括：新增 PowerShell 一键安装脚本（install.ps1），降低了 Windows 用户的上手门槛；新增 Gerrit CI 集成示例（Jenkins + Gerrit Trigger），扩展了企业级 CI/CD 场景的覆盖；新增 Pot 和 Po 代码审查规则，丰富了内置的静态分析能力。

在稳定性方面，v1.7.15 修复了 LLM 循环中文件级注释的竞态条件（pool submission racing），修复了合并提交的 diff 审查逻辑（现在正确对比第一个父提交），以及二进制文件标记和行计数的状态机问题。v1.7.14 修复了 LLM 工具调用参数为 nil 时的 panic 问题。这些修复表明 Open Code Review 正在从阿里巴巴内部工具向成熟的社区项目快速演进。

值得一提的是，Open Code Review 已支持 Codex 原生市场清单（marketplace manifest），这意味着用户可以通过 Codex CLI 直接安装和使用该工具，进一步降低了 AI 编码工作流中的集成成本。

---

*关联项目：[Open Code Review 项目分析](./Open%20Code%20Review%20项目分析.md)*
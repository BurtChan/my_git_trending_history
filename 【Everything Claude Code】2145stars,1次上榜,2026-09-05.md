# Everything Claude Code 项目分析

## 项目名称
**Everything Claude Code** — 经过生产级实战检验的 Claude Code 全套工具箱（agents/commands/skills/rules/hooks）
- **GitHub**: [WorldFlowAI/everything-claude-code](https://github.com/WorldFlowAI/everything-claude-code)
- **许可证**: MIT

---

## 项目概述
Everything Claude Code 是作者 affaanmustafa（Anthropic × Forum Ventures 黑客松 2025 年 9 月冠军，获奖作品 zenith.chat 完全用 Claude Code 构建）沉淀的 Claude Code 配置全家桶，涵盖 agents、commands、skills、rules、hooks、MCP configs、插件等全部扩展维度。

与碎片化的配置片段合集不同，它强调「经过多个生产应用实战检验」的完整工作流体系，并配套两篇深度指南（Shorthand Guide 入门 + Longform Guide 进阶）系统讲解使用哲学。仓库结构清晰地按扩展类型分目录（agents/commands/skills/rules/hooks/mcp-configs 等 14 个目录），27 个 commit 保持精炼。

---

## 核心功能

| 模块 | 内容 |
|------|------|
| agents | 生产级子智能体定义 |
| commands | 自定义斜杠命令集 |
| skills | 技能库 |
| rules | 项目规则与编码规范注入 |
| hooks | 生命周期钩子（自动格式化、防护检查等） |
| mcp-configs | MCP 服务器配置模板（20-30 个可选） |
| contexts / examples | 上下文管理方案与示例 |
| 指南 | Shorthand Guide（入门）+ Longform Guide（进阶），发布于 X |

---

## 技术栈
| 组件 | 技术 |
|------|------|
| 目标平台 | Claude Code |
| 扩展机制 | agents / commands / skills / hooks / plugins / MCP |
| 项目说明 | WORLDFLOWAI.md 项目记忆文件 |

---

## 项目亮点

### 上下文窗口治理经验
项目给出少见的量化建议：200K 上下文窗口在启用过多 MCP 后可能缩水到 70K；建议配置 20-30 个 MCP 但每项目启用不超过 10 个、活跃工具不超过 80 个，用 disabledMcpServers 精细控制。这是高频踩坑点的实战数据。

### 全维度覆盖
从 prompt 层（commands/rules）到执行层（agents/hooks）再到工具层（MCP configs），一份仓库覆盖 Claude Code 全部扩展机制，可作为「配置参考架构」整体借鉴。

### 冠军背书的可信度
黑客松夺冠经历 + 多个生产应用验证，配置不是玩具级演示，而是真实交付压力下打磨的方案。

---

## 应用场景

### 团队 Claude Code 规范化
为团队制定统一的 agents/rules/hooks 基线，避免每人一套碎片段配置。

### MCP 瘾戒断
按项目的 MCP 治理方案（配置多、启用少）解决上下文被工具定义挤占的常见问题。

### 学习配置演进
配合两篇指南阅读，理解每类扩展的适用边界与组合方式，少走弯路。

---

## Star 数据
| 指标 | 数值 |
|------|------|
| 总 Stars | 2,145 |
| 总 Forks | 349 |
| 今日新增 Stars | 87 |
| 主要语言 | —（配置仓库） |
| 许可证 | 未标明（README 注明 MIT） |
| 创建时间 | 2026-01-23 |

---

## 总结
Everything Claude Code 把一位黑客松冠军的 Claude Code 使用体系完整开源：不仅给配置，还给出「怎么管上下文、怎么组合扩展」的方法论。对从单文件 CLAUDE.md 走向系统化智能体工程的开发者，它是目前最完整的参考实现之一。

---

*数据来源：GitHub 仓库 (WorldFlowAI/everything-claude-code)，2026 年 9 月访问*

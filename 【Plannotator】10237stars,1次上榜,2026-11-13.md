# Plannotator 项目分析

## 项目名称
**Plannotator** — AI 编码代理的浏览器端审阅工作台：标注计划、评审代码、一键反馈给 Agent
- **GitHub**: [backnotprop/plannotator](https://github.com/backnotprop/plannotator)
- **许可证**: Apache-2.0

---

## 项目概述
Plannotator 是一个本地运行、基于浏览器的 AI 编码代理审阅界面（review surface），定位是「你与多个 Agent 之间缺失的审阅层」。它通过插件、hooks 和命令直接接入 Claude Code、Codex、Copilot CLI、Gemini CLI、OpenCode、Kiro、Droid、Amp、DeepSeek Harness、Pi 等十余个主流编码代理，也支持 Grok Bot、Muse、Hermes、OpenClaw 等个人助理。当 Agent 提出决策、计划或完成工作时，应用自动在浏览器中打开，你可以对计划、规格说明、Markdown、HTML 等交互式产物进行标注、评论，并将反馈一键发回给 Agent 执行。

随着多 Agent 并行工作流普及，开发者的核心痛点从「写代码」转移到「审阅 Agent 的产出」——终端里的长输出既难读又难批注。Plannotator 把这一环节产品化：Inbox 收件箱汇总所有 Agent 的决策、原型、方案变体与计划，Diff/PR 审阅提供可视化界面，全部反馈回流给 Agent 形成闭环。这种「Agent 干活、人签字」的交互范式正成为 AI 编码工具链的新标配，项目上线即冲上 Trending 并获得万余 Star，验证了该方向的真实需求。

---

## 核心功能
| 功能 | 描述 |
|------|------|
| Plannotator Inbox | 多 Agent 收件箱：汇总决策、原型、方案变体、计划，一个界面掌握全部 Agent 动态 |
| 文档/计划标注 | 对计划、规格、Markdown、HTML 及其他交互式产物直接批注，反馈一键发回 Agent |
| 代码评审 | 可视化 Diff 与 PR 审阅界面，替代终端里阅读 patch 的原始体验 |
| 多 Agent 接入 | 通过插件/hooks/命令接入 10+ 编码代理（Claude Code、Codex、Copilot CLI、Gemini CLI 等）与个人助理 |
| 本地运行 | 浏览器端本地应用，产物与反馈数据不出本机 |
| 终端伴侣（Herdr Annotate） | 提供终端内标注能力，覆盖不同工作流偏好 |

---

## 技术栈
| 组件 | 技术 |
|------|------|
| 形态 | 本地浏览器应用（Web UI） |
| 接入机制 | Agent 插件、hooks、斜杠命令 |
| 兼容协议 | 各主流编码 Agent 的扩展点 + ACP 类协议 |
| 许可证 | Apache-2.0 |

---

## 项目亮点
### 1. 补齐多 Agent 工作流的「人类审阅层」
Agent 并行干活的时代，瓶颈在于人跟不上。Plannotator Inbox 把分散在各终端会话中的决策和产物集中到一个收件箱，用户逐项批准/修改/拒绝，掌握全局进度。

### 2. 一键反馈回流形成闭环
标注不是终点——批注、评论、修改意见直接发回原 Agent 继续执行，构成「提案→审阅→反馈→修正」的完整回路，而非单向展示。

### 3. 广泛的 Agent 生态兼容
官方支持 Claude Code、Codex、Copilot CLI、Gemini CLI、OpenCode、Kiro、Droid、Amp、DeepSeek Harness、Pi 等，还兼容个人助理，不绑定单一工具链。

### 4. 本地优先的隐私姿态
应用本地运行、浏览器打开，计划和代码产物不上传第三方服务，对企业敏感场景友好。

---

## 应用场景
### 多 Agent 并行开发管理
同时运行多个 Claude Code/Codex 会话的团队，用 Inbox 统一接收各 Agent 的方案提案并逐项裁决，避免在多个终端间来回切换。

### 方案与计划评审
Agent 提出实现计划后，直接在浏览器中对计划文档划线批注，把修改要求发回 Agent 重做，替代口头/聊天式需求传达。

### PR 与 Diff 审阅加速
可视化审阅 Agent 生成的大段代码改动，逐行评论后自动反馈，让代码评审跟上 AI 的产出速度。

---

## Star 数据
| 指标 | 数值 |
|------|------|
| 总 Stars | 10,237 |
| 今日新增 | +100 |
| 总 Forks | 776 |
| 核心语言 | TypeScript |
| 许可证 | Apache-2.0 |

---

## 总结
Plannotator 抓住了多 Agent 编码时代「人审不过来」的核心痛点，用浏览器收件箱 + 标注 + 一键反馈闭环，把 Agent 产出的审阅环节做成了独立产品，是 Agent 工具链从「能干活」走向「可管理」的关键拼图。

---

*数据来源：GitHub 仓库 (backnotprop/plannotator)，2026 年 11 月访问*

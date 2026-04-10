# Hermes Agent 项目分析

> [!info] 一句话总结
> **Hermes Agent 是由 Nous Research 开发的一款具备自我学习能力的 AI 智能体，能够从经验中自动创建和优化技能，跨会话积累记忆并建立用户模型，同时支持多云平台部署和多消息渠道接入。**

---

## 基本信息

| 项目 | 详情 |
|---|---|
| **项目名称** | Hermes Agent |
| **GitHub 地址** | https://github.com/NousResearch/hermes-agent |
| **Stars** | 42,970 (+5,794 today) |
| **Forks** | 持续增长中 |
| **标语** | The agent that grows with you（与你共同成长的智能体） |
| **开发团队** | Nous Research |
| **开源许可证** | MIT License |
| **主要语言** | Python 3.11 |
| **官方文档** | https://hermes-agent.nousresearch.com/docs |
| **社区** | Discord / GitHub Discussions / Skills Hub |

---

## 解决的核心问题

传统 AI 智能体存在以下痛点，Hermes Agent 针对性地予以解决：

1. **缺乏持续学习能力** — 每次对话从零开始，无法从过往经验中学习。Hermes 内建闭环学习机制，完成任务后自动生成可复用的"技能"，并在使用过程中不断自我优化。
2. **跨会话记忆断层** — 对话结束即遗忘。Hermes 拥有持久化记忆系统（FTS5 全文检索 + LLM 摘要），能搜索历史对话，并通过 Honcho 辩证式用户建模逐渐深入理解用户偏好。
3. **部署灵活性差** — 多数 Agent 绑定本地环境。Hermes 支持六种终端后端（本地、Docker、SSH、Daytona、Singularity、Modal），可在 5 美元 VPS、GPU 集群或无服务器基础设施上运行，闲置时几乎零成本。
4. **模型锁定** — 换模型需要改代码。Hermes 支持 Nous Portal、OpenRouter（200+ 模型）、z.ai/GLM、Kimi/Moonshot、MiniMax、OpenAI 等多家提供商，一条命令即可切换。

---

## 核心特性

### 1. 闭环学习系统（Closed Learning Loop）
- **技能自动创建**：完成复杂任务后自主生成可复用技能
- **技能自我改进**：使用过程中不断优化已有技能
- **记忆持久化**：周期性提示（nudge）将重要信息写入长期记忆
- **会话检索**：FTS5 全文搜索历史对话，LLM 自动摘要实现跨会话回忆
- **用户建模**：基于 Honcho 辩证法构建用户画像，越用越了解你
- **开放标准**：兼容 agentskills.io 开放标准

### 2. 全功能终端界面（TUI）
- 多行编辑
- 斜杠命令自动补全
- 对话历史浏览
- 中断重定向
- 流式工具输出

### 3. 多平台消息网关
一次网关部署，覆盖所有平台：
- Telegram、Discord、Slack、WhatsApp、Signal
- 语音备忘录转录
- 跨平台对话连续性

### 4. 定时任务调度
- 内建 cron 调度器
- 自然语言定义任务
- 支持日报、夜间备份、周度审计等自动化场景
- 结果可投递至任意平台

### 5. 子智能体并行化
- 派生隔离子智能体进行并行工作流
- 编写 Python 脚本通过 RPC 调用工具
- 将多步管线压缩为零上下文成本的单轮操作

### 6. 灵活部署
六种终端后端：本地、Docker、SSH、Daytona、Singularity、Modal。Daytona 和 Modal 提供无服务器持久化，空闲时休眠、按需唤醒。

### 7. 研究就绪
- 批量轨迹生成
- Atropos 强化学习环境
- 轨迹压缩，用于训练下一代工具调用模型

---

## 技术栈

| 层级 | 技术 |
|---|---|
| **核心语言** | Python 3.11 |
| **包管理** | uv（Astral 出品） |
| **LLM 接入** | Nous Portal / OpenRouter / OpenAI / Anthropic / z.ai / Kimi / MiniMax 等多提供商 |
| **消息平台** | Telegram Bot API / Discord.py / Slack API / WhatsApp / Signal |
| **搜索/存储** | SQLite FTS5（全文检索） |
| **用户建模** | Honcho 辩证式建模引擎 |
| **技能标准** | agentskills.io 开放标准 |
| **RL 训练** | Tinker-Atropos 子模块 |
| **部署/容器** | Docker / SSH / Daytona / Singularity / Modal |
| **测试** | pytest |
| **许可证** | MIT |

---

## 使用场景

| 场景 | 说明 |
|---|---|
| **个人 AI 助手** | 通过 Telegram/Discord 等渠道随时对话，跨设备无缝衔接 |
| **开发辅助** | 终端内使用 TUI 进行代码编写、调试、文件管理等操作 |
| **自动化运维** | 定时执行备份、审计、报告等任务，结果自动推送到指定平台 |
| **团队协作** | 多人通过不同消息平台与同一 Agent 交互，共享技能和记忆 |
| **AI 研究** | 批量生成工具调用轨迹，用于 RL 训练下一代模型 |
| **无服务器 Agent** | 在 Modal/Daytona 上部署，空闲零成本，按需唤醒 |

---

## 快速安装

```bash
# 一键安装（Linux / macOS / WSL2）
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash

# 初始化
source ~/.bashrc
hermes              # 开始对话
hermes setup        # 完整设置向导
hermes model        # 选择 LLM 提供商和模型
hermes gateway      # 启动消息网关
```

> [!warning] Windows 用户请先安装 WSL2，不支持原生 Windows 环境。

---

## 从 OpenClaw 迁移

Hermes 提供完整的 OpenClaw 迁移支持：

```bash
hermes claw migrate              # 交互式迁移
hermes claw migrate --dry-run    # 预览迁移内容
```

可迁移内容包括：SOUL.md 人格文件、记忆、技能、命令白名单、消息平台配置、API 密钥、TTS 资源等。

---

## 相关链接

- **GitHub**: https://github.com/NousResearch/hermes-agent
- **官方文档**: https://hermes-agent.nousresearch.com/docs
- **Skills Hub**: 兼容 agentskills.io 开放标准
- **Discord**: Nous Research 社区
- **许可证**: MIT

---

> [!tip] 适合人群
> 需要一个**能学习、能记忆、能自我优化**的 AI Agent 的开发者、研究人员和自动化爱好者。尤其适合希望 Agent 跨平台运行、不被单一模型锁定、并且部署成本可控的用户。

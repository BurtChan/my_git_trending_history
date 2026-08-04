# Learn Claude Code 项目分析

> **Bash is all you need** — 从零到一构建一个类 Claude Code 的 Agent Harness，12 个渐进式课程教你理解 AI Agent 的本质。

- **GitHub**: [shareAI-lab/learn-claude-code](https://github.com/shareAI-lab/learn-claude-code)
- **团队**: shareAI-lab
- **许可证**: MIT
- **语言**: Python（教学实现）+ Next.js（Web 平台）
- **文档语言**: English / 中文 / 日本語

---

## 核心理念

### The Model IS the Agent

这个项目开宗明义：**Agent 是模型本身，不是框架，不是 prompt chain，不是拖拽工作流。**

真正的 Agent 历史：
- 2013 — DeepMind DQN 打 Atari（单个神经网络学打游戏）
- 2019 — OpenAI Five 征服 Dota 2（5 个神经网络打败世界冠军）
- 2019 — AlphaStar 星际争霸 Grandmaster
- 2019 — 腾讯绝悟统治王者荣耀
- 2024-2025 — LLM Agent 重塑软件工程

所有里程碑的共性：**Agent 永远是模型，不是周围的代码。**

### 什么是 Harness（线束）

项目引入了一个关键概念——**Harness**：

```
Harness = Tools + Knowledge + Observation + Action Interfaces + Permissions

    Tools:          文件 I/O、Shell、网络、数据库、浏览器
    Knowledge:      产品文档、领域参考、API 规格、风格指南
    Observation:    git diff、错误日志、浏览器状态、传感器数据
    Action:         CLI 命令、API 调用、UI 交互
    Permissions:    沙箱、审批工作流、信任边界
```

> 模型做决策，Harness 执行。模型推理，Harness 提供上下文。模型是驾驶员，Harness 是车辆。

### Claude Code 的本质

```
Claude Code = 一个 Agent 循环
            + 工具（bash、read、write、edit、glob、grep、browser...）
            + 按需技能加载
            + 上下文压缩
            + 子 Agent 派生
            + 带依赖图的任务系统
            + 异步邮箱的团队协调
            + 并行执行的 worktree 隔离
            + 权限治理
```

关键洞察：Claude Code 不试图成为 Agent 本身，而是**信任模型，专注于构建 Harness**。

---

## 12 个渐进式课程

| 阶段 | 课程 | 主题 | 格言 | 工具数 |
|------|------|------|------|--------|
| **Phase 1: 循环** | s01 | Agent Loop | 一个循环 + Bash 就是全部 | 1 |
| | s02 | Tool Use | 加工具就是加一个 handler | 4 |
| **Phase 2: 规划** | s03 | TodoWrite | 没有计划的 Agent 会迷失 | 5 |
| | s04 | Subagents | 大任务拆解，每个子任务干净上下文 | 5 |
| | s05 | Skills | 需要时才加载知识，不要 upfront | 5 |
| | s06 | Context Compact | 上下文会满，你需要腾空间 | 5 |
| **Phase 3: 持久化** | s07 | Tasks | 大目标拆小任务，排序，持久化到磁盘 | 8 |
| | s08 | Background Tasks | 慢操作后台运行，Agent 继续思考 | 6 |
| **Phase 4: 团队** | s09 | Agent Teams | 任务太大就委派给队友 | 9 |
| | s10 | Team Protocols | 队友需要共享的沟通规则 | 12 |
| | s11 | Autonomous Agents | 队友自己扫描任务板并认领 | 14 |
| | s12 | Worktree Isolation | 各自在自己的目录工作，互不干扰 | 16 |

---

## 核心代码模式

整个项目的核心就是这一个循环：

```python
def agent_loop(messages):
    while True:
        response = client.messages.create(
            model=MODEL, system=SYSTEM,
            messages=messages, tools=TOOLS,
        )
        messages.append({"role": "assistant",
                         "content": response.content})

        if response.stop_reason != "tool_use":
            return

        results = []
        for block in response.content:
            if block.type == "tool_use":
                output = TOOL_HANDLERS[block.name](**block.input)
                results.append({
                    "type": "tool_result",
                    "tool_use_id": block.id,
                    "content": output,
                })
        messages.append({"role": "user", "content": results})
```

每个课程在这个循环之上叠加一个 Harness 机制——**循环本身永远不变**。循环属于 Agent，机制属于 Harness。

---

## 学习路径

```
Phase 1: THE LOOP                    Phase 2: PLANNING & KNOWLEDGE
==================                   ==============================
s01  The Agent Loop          [1]     s03  TodoWrite               [5]
     while + stop_reason                  TodoManager + nag reminder
     |                                    |
     +-> s02  Tool Use            [4]     s04  Subagents            [5]
              dispatch map: name->handler     fresh messages[] per child
                                              |
                                         s05  Skills               [5]
                                              SKILL.md via tool_result
                                              |
                                         s06  Context Compact      [5]
                                              3-layer compression

Phase 3: PERSISTENCE                 Phase 4: TEAMS
==================                   =====================
s07  Tasks                   [8]     s09  Agent Teams             [9]
     file-based CRUD + deps graph         teammates + JSONL mailboxes
     |                                    |
s08  Background Tasks        [6]     s10  Team Protocols          [12]
     daemon threads + notify queue        shutdown + plan approval FSM
                                          |
                                     s11  Autonomous Agents       [14]
                                          idle cycle + auto-claim
                                     |
                                     s12  Worktree Isolation      [16]
                                          task + optional isolated execution
```

---

## 项目结构

```
learn-claude-code/
|
|-- agents/                        # Python 参考实现（s01-s12 + s_full）
|-- docs/{en,zh,ja}/               # 心智模型优先的文档（3 种语言）
|-- web/                           # 交互式学习平台（Next.js）
|-- skills/                        # s05 的技能文件
+-- .github/workflows/ci.yml      # CI：类型检查 + 构建
```

---

## 快速开始

```bash
git clone https://github.com/shareAI-lab/learn-claude-code
cd learn-claude-code
pip install -r requirements.txt
cp .env.example .env   # 填入你的 ANTHROPIC_API_KEY

python agents/s01_agent_loop.py       # 从这里开始
python agents/s12_worktree_task_isolation.py  # 完整进阶终点
python agents/s_full.py               # 毕业项目：所有机制综合

# Web 学习平台
cd web && npm install && npm run dev   # http://localhost:3000
```

---

## 学习指南

> 这个项目通过 12 个渐进式课程**反向工程 Claude Code 的内部机制**。每节课用最少的代码实现 Claude Code 的一个核心功能，让你从使用者视角理解"它为什么这样工作"，从而更高效地使用 Claude Code。

### 核心原则：模型即 Agent，代码即 Harness

Claude Code 的核心就是一个循环：

```
用户输入 → 模型思考 → 调用工具 → 拿到结果 → 继续思考 → ... → 最终回答
```

所有 12 节课都是在这个循环之上叠加机制，**循环本身永远不变**。你使用 Claude Code 时看到的每一个功能，背后都是这个循环在跑。

### 学习方法

**每个课程的正确姿势：先跑通 → 体验功能 → 对应到 Claude Code 的实际用法**

1. `python agents/s0X_xxx.py` 跑起来，观察行为
2. 理解这节课实现的机制对应 Claude Code 的哪个功能
3. 思考：我平时用 Claude Code 时，怎么更好地利用这个功能？

---

### Phase 1: THE LOOP — 理解 Claude Code 的底层（1-2 天）

> 这两个课程让你明白 Claude Code 不是魔法，而是一个模型驱动的循环。

#### s01: The Agent Loop — Claude Code 为什么能自己干活？

```
文件：agents/s01_agent_loop.py
工具数：1（Bash）
对应 Claude Code 功能：你输入一句话，它就能自己执行命令
```

**你将理解：**
- Claude Code 背后就是一个 `while True` 循环，模型决定继续还是停下
- 你给它的每一句话，都进入这个循环，模型决定调用哪个工具
- **使用提示**：Claude Code 有时候会"停不下来"或"太早停"，这就是 stop_reason 判断的问题

**动手实验：**
```bash
python agents/s01_agent_loop.py
# 让它执行一个简单任务，观察它怎么"自己决定"调用 Bash
# 这就是你在 Claude Code 中输入指令后发生的事
```

#### s02: Tool Use — Claude Code 为什么能读写文件？

```
文件：agents/s02_tool_use.py
工具数：4（Bash + Read + Write + Glob）
对应 Claude Code 功能：文件读写、代码搜索
```

**你将理解：**
- Claude Code 每个工具（Read、Write、Edit、Glob、Grep...）就是一个 handler 函数
- 模型根据你的需求自主选择用哪个工具
- **使用提示**：如果你发现 Claude Code 总是用错工具（比如用 Bash cat 而不是 Read），可能是工具描述不够清晰，可以通过 CLAUDE.md 引导

**动手实验：**
```bash
python agents/s02_tool_use.py
# 让它读一个文件、创建一个文件，观察它怎么选择工具
# 这对应你在 Claude Code 中让它改代码的行为
```

---

### Phase 2: PLANNING & KNOWLEDGE — 为什么 Claude Code 有时候很聪明有时候很蠢（2-3 天）

> 这四个课程解释 Claude Code 的"思考方式"——计划、拆解、知识加载、上下文管理。

#### s03: TodoWrite — 为什么 Claude Code 会自己列任务清单？

```
文件：agents/s03_todowrite.py
工具数：5（+TodoWrite）
对应 Claude Code 功能：TaskCreate/TaskUpdate/TaskList
```

**你将理解：**
- Claude Code 遇到复杂任务时会自动创建待办列表，这背后就是 TodoWrite 机制
- "nag reminder"：每次循环都提醒它还有哪些未完成任务，防止遗忘
- **使用提示**：给它一个复杂任务时，可以说"先列个计划"，效果比直接让它干更好；你也可以用 `/tasks` 查看它的任务进度

**动手实验：**
```bash
python agents/s03_todowrite.py
# 给它一个多步骤任务，观察它怎么自动创建和追踪任务
# 这就是你在大任务中看到 Claude Code 自己列 todo 的原因
```

#### s04: Subagents — 为什么 Claude Code 会"派小弟"干活？

```
文件：agents/s04_subagents.py
工具数：5（+Subagent）
对应 Claude Code 功能：Agent 工具（子 Agent 派生）
```

**你将理解：**
- Claude Code 用子 Agent 来并行处理独立任务（比如同时研究多个项目）
- 子 Agent 拿到干净的上下文（不带父 Agent 的对话历史），避免信息污染
- 子 Agent 的结果被压缩后返回给主 Agent
- **使用提示**：如果你发现 Claude Code 在并行处理多个任务，这就是 Subagent 机制在工作；你可以说"用子 Agent 并行研究这些项目"来主动触发

#### s05: Skills — 为什么 CLAUDE.md 这么重要？

```
文件：agents/s05_skills.py
工具数：5（+SkillLoad）
对应 Claude Code 功能：CLAUDE.md、Skill 加载、按需知识注入
```

**你将理解：**
- Claude Code 不会把所有知识一次性塞进上下文（太浪费 token）
- 知识是按需加载的——当它需要某个领域的知识时，才读取对应的 SKILL.md
- 你写的 CLAUDE.md 就是在给 Claude Code 注入"技能"
- **使用提示**：写好 CLAUDE.md 是高效使用 Claude Code 的关键——告诉它项目约定、代码风格、目录结构，比在对话中反复说更有效

**动手实验：**
```bash
python agents/s05_skills.py
# 看 skills/ 目录下的 SKILL.md 文件结构
# 然后回去看你自己项目的 CLAUDE.md，理解为什么这样写
```

#### s06: Context Compact — 为什么长对话不会爆掉？

```
文件：agents/s06_context_compact.py
工具数：5（+Compact）
对应 Claude Code 功能：自动上下文压缩（System reminder 中的 "compressing prior messages"）
```

**你将理解：**
- 对话太长时 Claude Code 会自动压缩历史消息（你会看到 "compressing prior messages" 的提示）
- 3 层压缩：保留最近消息 → 摘要中间消息 → 丢弃最旧的
- 压缩后关键信息不丢失，但细节可能模糊
- **使用提示**：如果你发现 Claude Code "忘了"之前说过的话，大概率是压缩导致的；重要信息应该在早期明确说清楚，而不是在长对话中间补充

**动手实验：**
```bash
python agents/s06_context_compact.py
# 让它执行一个会产生大量对话的任务，观察压缩何时触发
# 压缩后问它之前的细节，看哪些丢了哪些还在
```

---

### Phase 3: PERSISTENCE — 为什么 Claude Code 能跨会话记住任务（1-2 天）

> 这两个课程解释 Claude Code 的任务持久化机制。

#### s07: Tasks — 为什么 Claude Code 能记住未完成的工作？

```
文件：agents/s07_tasks.py
工具数：8（+TaskCreate/TaskUpdate/TaskList/TaskGet）
对应 Claude Code 功能：TaskCreate/TaskUpdate/TaskList/TaskGet 工具
```

**你将理解：**
- 任务被持久化到磁盘（JSON 文件），Agent 重启后任务还在
- 任务之间可以有依赖关系（A 完成后 B 才能开始）
- **使用提示**：你可以在 CLAUDE.md 中写"先创建任务再执行"，让 Claude Code 的工作更有条理

#### s08: Background Tasks — 为什么 Claude Code 能一边装依赖一边改代码？

```
文件：agents/s08_background_tasks.py
工具数：6（+BackgroundRun）
对应 Claude Code 功能：后台执行（run_in_background）、TaskOutput
```

**你将理解：**
- 慢操作（npm install、跑测试）在后台运行，不阻塞主循环
- Claude Code 能在等测试结果的同时继续写代码
- 后台任务完成后会通知主循环
- **使用提示**：你可以说"后台运行这个命令"来触发后台执行；用 `/tasks` 查看后台任务状态

---

### Phase 4: TEAMS — 为什么 Claude Code 能协调多个 Agent（2-3 天）

> 这四个课程解释 Claude Code 的多 Agent 协作机制（Team、SendMessage 等）。

#### s09: Agent Teams — Claude Code 怎么搞团队协作？

```
文件：agents/s09_agent_teams.py
对应 Claude Code 功能：TeamCreate、Agent 工具（team_name 参数）
```

**你将理解：**
- Team = 共享任务列表 + 成员目录 + 异步消息（类似邮箱）
- 每个队友是独立的 Agent 实例，有自己的上下文和工具
- **使用提示**：在 Claude Code 中，你可以说"用 team 模式"来启动多 Agent 协作

#### s10: Team Protocols — 队友之间怎么沟通？

```
文件：agents/s10_team_protocols.py
对应 Claude Code 功能：SendMessage、shutdown_request、plan_approval
```

**你将理解：**
- 队友之间通过结构化消息通信，不是随意聊天
- shutdown_request：队长让队友下班
- plan_approval：队友提交计划，队长审批
- **使用提示**：理解这些协议后，你能更好地调试多 Agent 协作中的沟通问题

#### s11: Autonomous Agents — 队友怎么自己找活干？

```
文件：agents/s11_autonomous_agents.py
对应 Claude Code 功能：自动任务认领、空闲循环
```

**你将理解：**
- Agent 空闲时自动扫描任务板，发现未分配任务就认领
- 从"你指派"进化到"它自驱"
- **使用提示**：当你启动一个 Team 后，队友会自动认领任务，你不需要手动分配

#### s12: Worktree Isolation — 多个 Agent 怎么避免冲突？

```
文件：agents/s12_worktree_task_isolation.py
对应 Claude Code 功能：EnterWorktree、git worktree 隔离
```

**你将理解：**
- 每个 Agent 在独立的 git worktree 目录工作，互不干扰
- 不会出现"你改了我的文件"的冲突
- 完成后可以合并或丢弃
- **使用提示**：让多个 Agent 并行修改代码时，确保它们各自在 worktree 中工作

---

### 毕业项目

```bash
python agents/s_full.py
```

将所有 12 节课的机制综合到一个文件中。跑通这个文件，你就完全理解了 Claude Code 的内部架构。

---

### 推荐学习节奏

| 阶段 | 天数 | 课程 | 学完后你能理解什么 |
|------|------|------|--------------------|
| Day 1 | 1 天 | s01 + s02 | Claude Code 为什么能自己读写文件和执行命令 |
| Day 2 | 1 天 | s03 + s04 | 为什么它会列任务清单、为什么它会派子 Agent |
| Day 3 | 1 天 | s05 + s06 | CLAUDE.md 为什么重要、为什么长对话不会爆 |
| Day 4 | 1 天 | s07 + s08 | 为什么它能记住任务、为什么能后台跑命令 |
| Day 5-6 | 2 天 | s09 + s10 | 多 Agent 协作怎么沟通、怎么审批 |
| Day 7 | 1 天 | s11 + s12 | 队友怎么自己找活干、怎么避免代码冲突 |
| Day 8 | 1 天 | s_full.py | 把所有理解串起来 |

### Web 学习平台（可选）

```bash
cd web && npm install && npm run dev   # http://localhost:3000
```

交互式学习平台，提供可视化界面辅助理解。

---

## 衍生产品

### Kode Agent CLI
> `npm i -g @shareai-lab/kode`

开源编程 Agent CLI，支持 Skill & LSP、Windows、可插拔 GLM / MiniMax / DeepSeek 等开放模型。

### Kode Agent SDK
可嵌入后端、浏览器扩展、嵌入式设备的 Agent SDK，无 per-user 进程开销。

### 姊妹项目 claw0
在相同 Agent 核心之上，增加 Heartbeat（30s 自动唤醒）和 Cron（自调度），将 Agent 从"用完即弃"变为"常驻助手"，支持 13+ IM 平台。

---

## 适用人群

| 角色 | 收获 |
|------|------|
| **AI 应用开发者** | 理解 Agent Harness 的构建原理 |
| **Claude Code 用户** | 深入理解工具背后的设计哲学 |
| **Agent 框架开发者** | 学习从循环到团队协作的渐进式设计 |
| **AI 工程学习者** | 12 节课从零掌握 Agent 系统设计 |

---

## 一句话总结

> Learn Claude Code 是一个**从零到一的 Agent Harness 工程教学项目**，核心理念是"模型即 Agent，代码即 Harness"，通过 12 个渐进式课程反向工程 Claude Code 的架构——从一个简单循环到支持团队协作和 worktree 隔离的完整系统，教你理解并构建 AI Agent 的运行环境。

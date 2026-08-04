# Claude HowTo 项目分析

> **Master Claude Code in a Weekend** — 一份可视化、示例驱动的 Claude Code 完全指南，从基础概念到高级 Agent 编排，附带即用型复制粘贴模板。

- **项目名称**: Claude HowTo
- **GitHub**: [luongnv89/claude-howto](https://github.com/luongnv89/claude-howto)
- **Stars**: 5,900+
- **Forks**: 690+
- **许可证**: MIT
- **语言**: Markdown（教程内容）+ Python（脚本/测试）+ Shell（Hooks）
- **作者**: luongnv89（Luong Nguyen）
- **版本**: v2.2.0（2026 年 3 月更新）
- **兼容**: Claude Code 2.1+，支持 Claude Sonnet 4.6 / Opus 4.6 / Haiku 4.5
- **文档语言**: English / Tiếng Việt / 中文

---

## 解决什么问题

你安装了 Claude Code，跑了几个提示词，然后呢？

Claude HowTo 精准定位了三个核心痛点：

1. **官方文档只描述功能，不教组合。** 你知道 slash commands 存在，但不知道如何将它们与 hooks、memory、subagents 串联成一个真正节省时间的完整工作流。
2. **没有清晰的学习路径。** 应该先学 MCP 还是 hooks？先学 Skills 还是 Subagents？结果是泛泛浏览，样样不精。
3. **示例太基础。** 一个 "hello world" 级别的 slash command 无法帮你构建生产级的代码审查流水线——那条线需要 memory、专业 Agent 委派和自动安全扫描。

**本质问题：你把 Claude Code 90% 的能力留在了桌面上，而你甚至不知道自己不知道什么。**

---

## 核心功能

### 10 个教程模块

项目提供了覆盖 Claude Code 所有特性的 10 个渐进式教程模块，每个模块都配有 Mermaid 图解和即用型配置文件：

| 序号 | 模块 | 难度 | 预计时间 | 核心内容 |
|------|------|------|----------|----------|
| 1 | **Slash Commands** | 入门 | 30 分钟 | 用户调用的快捷命令，存为 Markdown 文件 |
| 2 | **Memory** | 入门+ | 45 分钟 | 跨会话持久化上下文（CLAUDE.md） |
| 3 | **Checkpoints** | 中级 | 45 分钟 | 会话快照与回溯，安全实验 |
| 4 | **CLI Basics** | 入门+ | 30 分钟 | 命令行交互、标志位与选项 |
| 5 | **Skills** | 中级 | 1 小时 | 可复用的自动触发能力 |
| 6 | **Hooks** | 中级 | 1 小时 | 事件驱动的 Shell 自动化（4 类 25 种事件） |
| 7 | **MCP** | 中级+ | 1 小时 | Model Context Protocol，接入外部工具和 API |
| 8 | **Subagents** | 中级+ | 1.5 小时 | 隔离上下文的专业 AI 助手 |
| 9 | **Advanced Features** | 高级 | 2-3 小时 | Planning Mode、Extended Thinking、后台任务、权限模式 |
| 10 | **Plugins** | 高级 | 2 小时 | 打包命令 + Agent + MCP + Hooks 的完整解决方案 |

**完整学习路径总计：11-13 小时。但 15 分钟即可获得即时价值。**

### 即用型配置文件

每个模块都提供可直接复制到项目中的生产级模板：

- **Slash Commands**: `optimize.md`、`pr.md`、`generate-api-docs.md`
- **Memory**: 项目级 / 目录级 / 个人级 CLAUDE.md 模板
- **Skills**: `code-review/`、`brand-voice/`、`doc-generator/`
- **Subagents**: `code-reviewer.md`、`test-engineer.md`、`documentation-writer.md`、`secure-reviewer.md`、`implementation-agent.md`
- **MCP**: `github-mcp.json`、`database-mcp.json`、`filesystem-mcp.json`、`multi-mcp.json`
- **Hooks**: `format-code.sh`、`pre-commit.sh`、`security-scan.sh`、`log-bash.sh`、`validate-prompt.sh`、`notify-team.sh`
- **Plugins**: `pr-review/`、`devops-automation/`、`documentation/`

### 内置自评估系统

- `/self-assessment` — 交互式测验，识别知识盲区并生成个性化学习路线
- `/lesson-quiz [topic]` — 每个模块学完后的针对性测验

### EPUB 离线阅读

```bash
uv run scripts/build_epub.py
```

可将全部内容和渲染后的 Mermaid 图表生成为 EPUB 电子书，支持离线阅读。

---

## 与官方文档的对比

| 维度 | 官方文档 | Claude HowTo |
|------|----------|-------------|
| **格式** | 参考文档 | 可视化教程 + Mermaid 图 |
| **深度** | 功能描述 | 底层工作原理 |
| **示例** | 基础代码片段 | 生产级即用模板 |
| **结构** | 按功能组织 | 渐进式学习路径（入门到高级）|
| **入门引导** | 自行探索 | 引导式路线图，含时间估算 |
| **自我评估** | 无 | 交互式测验 |

---

## 技术栈

| 层面 | 技术 |
|------|------|
| **教程内容** | Markdown + Mermaid 图表 |
| **Hooks 脚本** | Shell (Bash) |
| **构建/测试脚本** | Python |
| **代码质量** | Ruff（Lint + Format）、Bandit（安全扫描）、mypy（类型检查）|
| **测试框架** | pytest + Codecov |
| **Python 版本** | 3.10 / 3.11 / 3.12 |
| **包管理** | uv |
| **CI/CD** | GitHub Actions（main/develop 推送 + PR 自动测试）|
| **离线出版** | 自定义 EPUB 生成脚本 |

---

## 使用场景

### 典型工作流组合

| 场景 | 组合的特性 |
|------|-----------|
| **自动化代码审查** | Slash Commands + Subagents + Memory + MCP |
| **团队 Onboarding** | Memory + Slash Commands + Plugins |
| **CI/CD 自动化** | CLI Reference + Hooks + Background Tasks |
| **文档生成** | Skills + Subagents + Plugins |
| **安全审计** | Subagents + Skills + Hooks（只读模式）|
| **DevOps 流水线** | Plugins + MCP + Hooks + Background Tasks |
| **复杂重构** | Checkpoints + Planning Mode + Hooks |

### 示例：完整代码审查工作流

```
用户: /review-pr

Claude:
1. 加载项目 memory（编码规范）
2. 通过 GitHub MCP 获取 PR
3. 委派给 code-reviewer subagent
4. 委派给 test-engineer subagent
5. 综合分析结果
6. 输出完整的审查报告
```

### 适用人群

| 角色 | 收获 |
|------|------|
| **Claude Code 新手** | 15 分钟上手，2.5 小时掌握基础 |
| **中级用户** | 学习 Hooks、MCP、Subagents 的高级组合 |
| **高级用户** | 构建完整的 Plugin 和自动化流水线 |
| **团队负责人** | 统一团队 Memory 和标准化工作流 |
| **DevOps 工程师** | CLI Headless 模式集成 CI/CD |

---

## 项目结构

```
claude-howto/
├── 01-slash-commands/          # Slash 命令模板
├── 02-memory/                  # Memory 配置模板（项目/目录/个人级）
├── 03-skills/                  # Skills 定义（含脚本和模板）
├── 04-subagents/               # Subagent 定义
├── 05-mcp/                     # MCP 服务器配置
├── 06-hooks/                   # Hook 脚本（4 类 25 种事件）
├── 07-plugins/                 # 完整插件包
├── 08-checkpoints/             # Checkpoint 使用示例
├── 09-advanced-features/       # 高级功能配置
├── 10-cli/                     # CLI 参考文档
├── resources/logos/            # 项目 Logo
├── scripts/                    # Python 脚本（EPUB 生成、测试）
└── README.md                   # 项目说明
```

---

## 快速开始

```bash
# 1. 克隆仓库
git clone https://github.com/luongnv89/claude-howto.git
cd claude-howto

# 2. 复制第一个 Slash Command
mkdir -p /path/to/your-project/.claude/commands
cp 01-slash-commands/optimize.md /path/to/your-project/.claude/commands/

# 3. 在 Claude Code 中试用
# /optimize

# 4. 设置项目 Memory
cp 02-memory/project-CLAUDE.md /path/to/your-project/CLAUDE.md

# 5. 安装一个 Skill
cp -r 03-skills/code-review ~/.claude/skills/
```

**1 小时基础配置**：

```bash
# Slash commands（15 分钟）
cp 01-slash-commands/*.md .claude/commands/

# 项目 Memory（15 分钟）
cp 02-memory/project-CLAUDE.md ./CLAUDE.md

# 安装 Skill（15 分钟）
cp -r 03-skills/code-review ~/.claude/skills/

# 周末目标：添加 Hooks、Subagents、MCP、Plugins
```

---

## 详细学习指南

> Claude HowTo 的核心价值不是"读文档"，而是**复制模板、立刻用上**。每个模块都有可直接复制到项目中的配置文件。

### 这个项目到底是什么？

用一句话说：**这是一份教你如何正确使用 Claude Code 的实战教程**。

它不是 Claude Code 官方文档的翻译，也不是原理讲解。它是这样的东西：

- 你 clone 下来后，里面有 10 个文件夹
- 每个文件夹对应 Claude Code 的一个功能（Slash Commands、Memory、Hooks、MCP 等）
- 每个文件夹里有**可以直接复制到你项目中用的配置文件**
- 你复制过去，在 Claude Code 里就能直接用了

**类比**：如果说官方文档是"字典"（查功能用的），那 Claude HowTo 就是"作文范文大全"（直接抄来用的）。

### 10 个模块详解

---

#### 模块 1: Slash Commands（30 分钟）

**对应文件夹**: `01-slash-commands/`

**这是什么**：你在 Claude Code 里输入 `/optimize`、`/pr` 这样的命令，背后就是 Slash Commands。它本质上就是一个 Markdown 文件，放在 `.claude/commands/` 目录下。

**怎么用**：
```bash
# 复制命令文件到你的项目
mkdir -p /path/to/your-project/.claude/commands
cp 01-slash-commands/optimize.md /path/to/your-project/.claude/commands/

# 然后在 Claude Code 中输入 /optimize 就能用了
```

**项目提供的模板**：
- `optimize.md` — 代码优化分析
- `pr.md` — 自动准备 Pull Request
- `generate-api-docs.md` — API 文档生成器

**你的收获**：学会创建自定义命令，把常用操作变成一个 `/命令`，省去重复输入。

---

#### 模块 2: Memory（45 分钟）

**对应文件夹**: `02-memory/`

**这是什么**：CLAUDE.md 文件。Claude Code 每次启动时会自动读取这个文件，相当于给 Claude 的"长期记忆"。你在 CLAUDE.md 里写的东西，每次对话 Claude 都知道。

**三级 Memory**：
| 级别 | 文件位置 | 作用 |
|------|----------|------|
| **个人级** | `~/.claude/CLAUDE.md` | 你的个人偏好（如"用中文回复"） |
| **项目级** | `项目根目录/CLAUDE.md` | 项目约定（如"用 TypeScript，用 ESLint"） |
| **目录级** | `项目子目录/CLAUDE.md` | 目录特定规则（如 API 目录下"遵循 RESTful 规范"） |

**怎么用**：
```bash
# 设置项目级 Memory
cp 02-memory/project-CLAUDE.md /path/to/your-project/CLAUDE.md
# 编辑这个文件，写入你的项目规范

# 设置个人级 Memory
cp 02-memory/personal-CLAUDE.md ~/.claude/CLAUDE.md
# 写入你的个人偏好
```

**你的收获**：这是 Claude Code 最重要的功能之一。写好 CLAUDE.md 后，Claude 每次都按你的规范工作，不用每次重复说。

---

#### 模块 3: Checkpoints（45 分钟）

**对应文件夹**: `08-checkpoints/`

**这是什么**：Claude Code 每次你输入消息时都会自动保存一个"快照"。如果你不满意 Claude 的操作，可以回退到之前的状态。

**怎么用**：
- 每次你输入消息，自动创建一个 Checkpoint
- 按 `Esc` 两次或输入 `/rewind` 可以回退
- 回退时选择：恢复代码 + 对话 / 只恢复对话 / 只恢复代码 / 从这里总结 / 取消

**你的收获**：放心让 Claude 做实验性的修改，不满意可以一键回退。特别适合复杂重构。

---

#### 模块 4: CLI Basics（30 分钟）

**对应文件夹**: `10-cli/`

**这是什么**：Claude Code 命令行的各种用法。不只是 `claude` 回车进去聊天，还有很多强大的命令行参数。

**常用命令**：
```bash
# 交互模式
claude "解释这个项目"

# 非交互模式（管道/脚本用）
claude -p "review this code"

# 把文件内容传给 Claude
cat error.log | claude -p "解释这个错误"

# JSON 输出（给脚本用）
claude -p --output-format json "列出所有函数"

# 恢复之前的会话
claude -r "feature-auth" "继续实现"
```

**你的收获**：学会把 Claude Code 集成到脚本和 CI/CD 中，不只是手动聊天。

---

#### 模块 5: Skills（1 小时）

**对应文件夹**: `03-skills/`

**这是什么**：Skills 是比 Slash Commands 更高级的功能。Slash Commands 是你手动触发的（`/命令`），而 Skills 是**自动触发**的——当 Claude 检测到相关任务时自动调用。

**项目提供的 Skills**：
- `code-review/` — 代码审查（含脚本和模板）
- `brand-voice/` — 品牌文案一致性检查
- `doc-generator/` — API 文档生成

**怎么安装**：
```bash
# 个人级（所有项目都能用）
cp -r 03-skills/code-review ~/.claude/skills/

# 项目级（只有当前项目能用）
cp -r 03-skills/code-review /path/to/project/.claude/skills/
```

**你的收获**：让 Claude 在需要时自动调用专业能力，不需要你手动触发。

---

#### 模块 6: Hooks（1 小时）

**对应文件夹**: `06-hooks/`

**这是什么**：Hooks 是事件驱动的自动化脚本。当 Claude Code 发生特定事件时（如写文件、执行命令），自动运行你配置的 Shell 脚本。

**4 类 25 种事件**：
| 类型 | 事件举例 | 用途 |
|------|----------|------|
| **工具事件** | 写文件前/后、执行命令前/后 | 自动格式化、安全扫描 |
| **会话事件** | 会话开始/结束、Agent 停止 | 初始化、清理 |
| **任务事件** | 用户提交提示词、任务完成 | 日志记录、通知 |
| **生命周期事件** | 配置变更、文件变更、上下文压缩 | 响应环境变化 |

**项目提供的 Hook 脚本**：
- `format-code.sh` — 写文件前自动格式化代码
- `pre-commit.sh` — 提交前自动跑测试
- `security-scan.sh` — 写文件后自动安全扫描
- `log-bash.sh` — 记录所有 Bash 命令
- `validate-prompt.sh` — 验证用户输入
- `notify-team.sh` — 事件发生时通知团队

**怎么配置**：
```bash
mkdir -p ~/.claude/hooks
cp 06-hooks/*.sh ~/.claude/hooks/
chmod +x ~/.claude/hooks/*.sh
```

然后在 `~/.claude/settings.json` 中配置：
```json
{
  "hooks": {
    "PreToolUse": [{
      "matcher": "Write",
      "hooks": ["~/.claude/hooks/format-code.sh"]
    }],
    "PostToolUse": [{
      "matcher": "Write",
      "hooks": ["~/.claude/hooks/security-scan.sh"]
    }]
  }
}
```

**你的收获**：实现"Claude 写代码 → 自动格式化 → 自动安全扫描"的自动化流水线。

---

#### 模块 7: MCP（1 小时）

**对应文件夹**: `05-mcp/`

**这是什么**：Model Context Protocol（模型上下文协议）。让 Claude Code 能连接外部工具和 API，比如 GitHub、数据库、文件系统等。

**项目提供的 MCP 配置**：
- `github-mcp.json` — GitHub 集成（获取 PR、Issue 等）
- `database-mcp.json` — 数据库查询
- `filesystem-mcp.json` — 文件操作
- `multi-mcp.json` — 多个 MCP 服务器组合

**怎么配置**：
```bash
# 设置环境变量
export GITHUB_TOKEN="your_token"

# 通过 CLI 添加 MCP 服务器
claude mcp add github -- npx -y @modelcontextprotocol/server-github

# 或手动编辑 .mcp.json（项目中有模板）
```

**你的收获**：让 Claude 直接操作 GitHub、数据库等外部服务，不再只是一个代码编辑器。

---

#### 模块 8: Subagents（1.5 小时）

**对应文件夹**: `04-subagents/`

**这是什么**：Subagent（子 Agent）是专业化的 AI 助手。主 Claude 可以把特定任务委派给子 Agent，每个子 Agent 有自己的专业提示词和隔离的上下文。

**项目提供的 Subagent 定义**：
- `code-reviewer.md` — 代码质量分析专家
- `test-engineer.md` — 测试策略和覆盖率专家
- `documentation-writer.md` — 技术文档撰写专家
- `secure-reviewer.md` — 安全审计专家（只读模式）
- `implementation-agent.md` — 功能实现专家

**怎么安装**：
```bash
cp 04-subagents/*.md /path/to/project/.claude/agents/
```

**实际效果**：当你让 Claude 做代码审查时，它会自动委派给 code-reviewer 子 Agent，子 Agent 拿到独立的上下文去分析，结果返回给主 Agent。这样主 Agent 不会被大量代码细节淹没。

**你的收获**：构建专业化团队，让每个子 Agent 聚焦一个领域，结果比单个 Agent 做所有事更好。

---

#### 模块 9: Advanced Features（2-3 小时）

**对应文件夹**: `09-advanced-features/`

**这是什么**：Claude Code 的高级功能集合。

**包含的功能**：
| 功能 | 说明 |
|------|------|
| **Planning Mode** | 写代码前先制定详细计划，让你审批后再执行 |
| **Extended Thinking** | 深度思考模式（按 `Alt+T` 切换），让 Claude 对复杂问题思考更久 |
| **Background Tasks** | 长时间运行的任务放到后台，不阻塞主对话 |
| **Permission Modes** | 权限控制：`default`（每次询问）、`acceptEdits`（自动编辑）、`plan`（只计划）、`dontAsk`（不询问）、`bypassPermissions`（完全自动） |
| **Headless Mode** | CI/CD 中无交互运行：`claude -p "跑测试并生成报告"` |
| **Session Management** | 会话管理：`/resume`、`/rename`、`/fork`、`claude -c`、`claude -r` |

**你的收获**：掌握 Claude Code 的全部高级能力，适合处理复杂项目和自动化场景。

---

#### 模块 10: Plugins（2 小时）

**对应文件夹**: `07-plugins/`

**这是什么**：Plugin 是 Claude Code 功能的最高层级封装——一个 Plugin = 命令 + Agent + MCP + Hooks 的完整包。装一个 Plugin 等于装了一套完整的解决方案。

**项目提供的 Plugin**：
- `pr-review/` — 完整的 PR 审查流水线
- `devops-automation/` — 部署和监控自动化
- `documentation/` — 文档生成自动化

**怎么安装**：
```bash
/plugin install pr-review
/plugin install devops-automation
```

**你的收获**：一个命令装一套完整工作流，适合团队级别的标准化。

---

### 实战工作流示例

#### 示例 1：自动化代码审查

```
你输入: /review-pr

Claude 自动执行:
1. 读取项目 CLAUDE.md（你的编码规范）
2. 通过 GitHub MCP 获取 PR 内容
3. 委派给 code-reviewer 子 Agent（分析代码质量）
4. 委派给 test-engineer 子 Agent（检查测试覆盖）
5. 综合两个子 Agent 的结果
6. 输出完整的审查报告
```

**用到的功能**: Slash Commands + Subagents + Memory + MCP

#### 示例 2：自动化部署

```
你输入: /deploy production

Claude 自动执行:
1. 运行 pre-deploy hook（验证环境）
2. 委派给 deployment-specialist 子 Agent
3. 通过 Kubernetes MCP 执行部署
4. 监控进度
5. 运行 post-deploy hook（健康检查）
6. 报告状态
```

**用到的功能**: Plugins + MCP + Hooks + Background Tasks

---

### 推荐学习节奏

| 天数 | 学习内容 | 学完后你能做什么 |
|------|----------|------------------|
| Day 1 | Slash Commands + Memory（1 小时） | 创建自定义命令，设置项目规范 |
| Day 2 | Skills + Checkpoints（1.5 小时） | 让 Claude 自动调用能力，放心做实验 |
| Day 3 | Hooks + CLI（1.5 小时） | 自动化格式化和安全扫描，集成脚本 |
| Day 4 | MCP + Subagents（2.5 小时） | 连接外部服务，构建专业 Agent 团队 |
| Day 5 | Advanced Features + Plugins（4 小时） | 完全掌握 Claude Code，构建自动化流水线 |

**总计约 11-13 小时，一个周末可以搞定。**

---

### 与 Learn Claude Code 的区别

| 维度 | Claude HowTo | Learn Claude Code |
|------|-------------|-------------------|
| **目的** | 教你使用 Claude Code | 教你理解 Claude Code 的内部原理 |
| **方式** | 复制模板，直接用 | 用 Python 从零实现每个功能 |
| **产出** | 你的 Claude Code 配置文件 | 你对 Agent 架构的理解 |
| **适合** | 想高效使用 Claude Code 的人 | 想深入理解 Agent 机制的人 |
| **先后顺序** | 先学这个 | 再学这个（有了使用经验后更好理解） |

**建议路径**：先花一个周末学 Claude HowTo（学会用），再花一周学 Learn Claude Code（理解原理）。

---

## 一句话总结

> Claude HowTo 是一份**结构化、可视化、示例驱动的 Claude Code 完全指南**，覆盖从 Slash Commands 到 Plugin 的全部 10 大特性，通过 Mermaid 图解理解底层原理、生产级即用模板实现即时价值、渐进式学习路径在 11-13 小时内将用户从入门带到精通——让 Claude Code 用户真正释放 100% 的能力。

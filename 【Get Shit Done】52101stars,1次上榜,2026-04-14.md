# Get Shit Done (GSD) 项目分析

**项目地址**：https://github.com/gsd-build/get-shit-done

## 项目概述

Get Shit Done（GSD）是一个轻量而强大的元提示（Meta-Prompting）、上下文工程（Context Engineering）和规格驱动开发（Spec-Driven Development）系统，专为 Claude Code 等 AI 编码工具设计。由独立开发者 TÂCHES 创建，GSD 的核心理念是解决 AI 编码中的"上下文腐烂"问题——即随着上下文窗口被填满，Claude 的代码质量逐渐下降的现象。通过将大任务拆分为小计划、每个计划使用全新上下文执行、并行波次调度，GSD 实现了稳定可靠的 AI 自主编码。

- **作者**：TÂCHES（独立开发者）
- **许可证**：MIT
- **npm 包**：get-shit-done-cc
- **最新版本**：v1.35.0（2026-04-11）
- **提交次数**：1,848 次
- **支持平台**：Claude Code、OpenCode、Gemini CLI、Kilo、Codex、Copilot、Cursor、Windsurf、Antigravity、Augment、Trae、Qwen Code、Cline、CodeBuddy

## 核心功能

### 工作流程（6 步循环）
1. **初始化项目** (`/gsd-new-project`)：提问 → 研究 → 需求提取 → 路线图生成
2. **讨论阶段** (`/gsd-discuss-phase N`)：捕获实现决策，识别灰色地带
3. **计划阶段** (`/gsd-plan-phase N`)：研究 → 创建 2-3 个原子任务计划 → 验证
4. **执行阶段** (`/gsd-execute-phase N`)：并行波次执行，每个计划独立上下文，原子提交
5. **验证工作** (`/gsd-verify-work N`)：用户验收测试，自动诊断失败
6. **完成里程碑** (`/gsd-complete-milestone`)：归档里程碑，标记发布

### 波次执行引擎
将计划按依赖关系分组为"波次"，波次内并行执行，波次间串行执行：
- 独立计划 → 同一波次 → 并行运行
- 依赖计划 → 后续波次 → 等待依赖完成
- 文件冲突 → 串行计划或合并为同一计划

### 快速模式 (`/gsd-quick`)
适用于不需要完整规划的临时任务：
- `--discuss` 标志：轻量级讨论
- `--research` 标志：执行前调研
- `--validate` 标志：启用计划检查和验证
- `--full` 标志：启用所有阶段

### 上下文工程
通过文件系统管理 Claude 的上下文：

| 文件 | 作用 |
|------|------|
| `PROJECT.md` | 项目愿景，始终加载 |
| `research/` | 生态知识（技术栈、架构、陷阱） |
| `REQUIREMENTS.md` | v1/v2 需求范围 |
| `ROADMAP.md` | 路线图和进度 |
| `STATE.md` | 决策、阻塞项、状态——跨会话记忆 |
| `PLAN.md` | 原子任务（XML 结构） |
| `SUMMARY.md` | 执行摘要 |
| `todos/` | 待办想法 |
| `threads/` | 跨会话的持久上下文线程 |
| `seeds/` | 前瞻性想法，在合适的里程碑自动浮现 |

### XML 提示格式
每个计划使用 XML 结构优化 Claude 的理解：
```xml
<task type="auto">
  <name>创建登录端点</name>
  <files>src/app/api/auth/login/route.ts</files>
  <action>使用 jose 进行 JWT 认证</action>
  <verify>curl -X POST localhost:3000/api/auth/login 返回 200 + Set-Cookie</verify>
  <done>有效凭据返回 Cookie，无效返回 401</done>
</task>
```

### 多 Agent 编排
每个阶段使用相同的模式：轻量编排器生成专业 Agent，收集结果，路由到下一步：

| 阶段 | 编排器 | Agent |
|------|--------|-------|
| 研究 | 协调、汇总 | 4 个并行研究员调查技术栈、功能、架构、陷阱 |
| 计划 | 验证、迭代 | 计划器创建计划，检查器验证，循环直到通过 |
| 执行 | 分组波次、跟踪 | 执行器并行实现，每个拥有全新 200K 上下文 |
| 验证 | 呈现结果 | 验证器检查代码库，调试器诊断失败 |

### 原子 Git 提交
每个任务完成后立即获得独立的原子提交：
```
abc123f docs(08-02): complete user registration plan
def456g feat(08-02): add email confirmation flow
hij789k feat(08-02): implement password hashing
```

### 安全加固
自 v1.27 起内置多层安全防护：
- 路径遍历防护
- Prompt 注入检测
- PreToolUse 提示守卫钩子
- 安全 JSON 解析
- Shell 参数验证
- CI 就绪的注入扫描器

### 模型配置
控制每个 Agent 使用的 Claude 模型：

| 配置 | 计划 | 执行 | 验证 |
|------|------|------|------|
| quality | Opus | Opus | Sonnet |
| balanced（默认） | Opus | Sonnet | Sonnet |
| budget | Sonnet | Sonnet | Haiku |
| inherit | 继承 | 继承 | 继承 |

## 技术栈

| 层面 | 技术 |
|------|------|
| 主要语言 | JavaScript (69.7%) |
| 辅助语言 | TypeScript (29.7%), Shell (0.6%) |
| 包管理 | npm (get-shit-done-cc) |
| 测试框架 | Vitest |
| 构建工具 | npm scripts |
| 运行时 | Node.js |
| 版本迭代 | 48 个 Release |

## 项目亮点

- **解决核心痛点**：攻克"上下文腐烂"——AI 编码中最大的质量杀手
- **15+ 运行时支持**：不仅支持 Claude Code，还覆盖 Cursor、Copilot、Gemini CLI 等主流 AI 编码工具
- **零配置快速启动**：`npx get-shit-done-cc@latest` 一行命令安装
- **上下文保持新鲜**：主会话上下文始终保持在 30-40%，繁重工作在子 Agent 中完成
- **企业级安全**：多层 Prompt 注入防护、路径遍历防护、敏感文件保护
- **波次并行执行**：智能依赖分析，最大化并行效率
- **独立开发者验证**：被 Amazon、Google、Shopify、Webflow 的工程师信任使用
- **快速迭代**：1,848 次提交，48 个 Release，持续演进
- **完善的生态系统**：Workstreams、多项目工作区、Brownfield 代码库映射

## 应用场景

- **独立开发者/创业者**：用 AI 从零构建完整产品，GSD 确保代码质量稳定
- **大型功能开发**：将复杂功能拆分为安全的增量步骤，AI 自动实现
- **代码库重构**：通过 Brownfield 模式分析现有代码，规划并执行重构
- **团队协作**：多 Workstream 并行开发，独立的里程碑管理
- **AI 编码工具评测**：同一规格在不同 AI 工具上执行，对比效果
- **技术债务清理**：系统性规划和执行技术债务偿还计划
- **快速原型**：使用 Quick 模式快速实现临时功能

## Star 数据

- 总 Star 数：52,101
- Fork 数：4,366
- 今日增长：+655
- Watcher 数：225
- 发布版本：48 个（最新 v1.35.0）
- 社区：Discord

## 总结

Get Shit Done 是 AI 辅助编码领域一个极具实用价值的项目。它不试图替代 AI 编码工具，而是作为"元层"解决这些工具的根本缺陷——上下文腐烂。通过精巧的上下文工程（文件系统作为记忆载体）、XML 提示格式优化、波次并行执行和多 Agent 编排，GSD 让 AI 编码从"偶尔能用"进化为"稳定可靠"。52K+ 的 Star 数和 1,848 次提交证明了这一方法论的有效性和社区的认可。对于任何认真使用 AI 进行软件开发的开发者，GSD 提供了一个经过实战验证的系统化方案。作者 TÂCHES 作为独立开发者的背景也赋予了项目独特的视角——不搞企业级繁文缛节，只关注"把事情做成"。

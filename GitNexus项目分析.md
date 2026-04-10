# GitNexus 项目分析

> **零服务器代码智能引擎** — 将代码仓库转化为知识图谱，让 AI 编程助手真正理解代码结构。

- **GitHub**: [abhigyanpatwari/GitNexus](https://github.com/abhigyanpatwari/GitNexus)
- **Stars**: 23.4k | **Forks**: 2.6k | **贡献者**: 58 人
- **最新版本**: v1.5.3 (2026-04-01)
- **许可证**: PolyForm Noncommercial（企业商用需授权）
- **在线体验**: [gitnexus.vercel.app](https://gitnexus.vercel.app)

---

## 解决什么问题

当前 AI 编程工具（Cursor、Claude Code、Codex 等）编辑代码时，不知道函数改动的影响范围。例如改了 `UserService.validate()`，AI 不知道有 47 个函数依赖它的返回类型，导致**破坏性变更被提交**。

## 核心创新：预计算关系智能

传统 Graph RAG 给 LLM 原始图边，让 LLM 自己探索，需要多轮查询。GitNexus **在索引时就完成聚类、追踪、评分**，一次调用返回完整上下文：

- **可靠性** — LLM 不会遗漏上下文，工具响应已包含完整信息
- **Token 效率** — 不需要 10 轮查询来理解一个函数
- **模型民主化** — 小模型也能工作，因为工具做了重活

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **知识图谱构建** | 多阶段索引：文件结构 → Tree-sitter AST 提取符号 → 解析跨文件依赖 → 聚类分组 → 追踪执行流 |
| **影响分析 (Impact)** | 改一个函数，立即知道谁依赖它、影响范围、风险等级 |
| **上下文视图 (Context)** | 360 度查看符号：谁调用它、它调用谁、参与哪些执行流程 |
| **变更检测** | 提交前分析 git diff，映射受影响的符号和流程 |
| **多文件重命名** | 跨文件协调重命名，结合图谱 + 文本搜索 |
| **混合搜索** | BM25 + 语义搜索 + RRF 融合排序 |
| **Wiki 生成** | 基于知识图谱自动生成文档 |

---

## 两种使用方式

### 1. CLI + MCP（日常开发推荐）

```bash
# 索引仓库
npx gitnexus analyze

# 配置 MCP（一次性）
npx gitnexus setup

# 启动 MCP 服务器
npx gitnexus mcp
```

通过 MCP 协议向 AI 工具暴露 **16 个工具**（11 个单仓库 + 5 个多仓库组），支持 **14 种语言**。

**编辑器支持：**

| 编辑器 | MCP | Skills | Hooks | 支持级别 |
|--------|-----|--------|-------|---------|
| Claude Code | ✅ | ✅ | ✅ | 完整 |
| Cursor | ✅ | ✅ | — | MCP + Skills |
| Codex | ✅ | ✅ | — | MCP + Skills |
| Windsurf | ✅ | — | — | MCP |

### 2. Web UI（快速探索）

- 地址：gitnexus.vercel.app
- 无需安装，纯浏览器运行
- 拖入 ZIP 文件即可生成交互式图谱
- 代码不离开浏览器，保护隐私
- 限制：受浏览器内存约束（约 5k 文件）

---

## 技术栈

| 层级 | CLI | Web |
|------|-----|-----|
| **运行时** | Node.js (原生) | 浏览器 (WASM) |
| **解析** | Tree-sitter 原生绑定 | Tree-sitter WASM |
| **数据库** | LadybugDB 原生 | LadybugDB WASM |
| **嵌入模型** | HuggingFace transformers.js | transformers.js (WebGPU) |
| **搜索** | BM25 + 语义 + RRF | BM25 + 语义 + RRF |
| **Agent 接口** | MCP (stdio) | LangChain ReAct |
| **可视化** | — | Sigma.js + Graphology (WebGL) |
| **前端** | — | React 18, TypeScript, Vite, Tailwind v4 |

---

## 支持的语言（14 种）

TypeScript、JavaScript、Python、Java、Kotlin、C#、Go、Rust、PHP、Ruby、Swift、C、C++、Dart

每个语言支持不同程度的功能：导入解析、命名绑定、导出检测、继承关系、类型注解、构造函数推断、配置解析、框架检测、入口点识别。

---

## 工具示例

### 影响分析

```
impact({target: "UserService", direction: "upstream", minConfidence: 0.8})

TARGET: Class UserService (src/services/user.ts)

UPSTREAM (what depends on this):
  Depth 1 (WILL BREAK):
    handleLogin [CALLS 90%] -> src/api/auth.ts:45
    handleRegister [CALLS 90%] -> src/api/auth.ts:78
  Depth 2 (LIKELY AFFECTED):
    authRouter [IMPORTS] -> src/routes/auth.ts
```

### 上下文视图

```
context({name: "validateUser"})

incoming:
  calls: [handleLogin, handleRegister, UserController]
  imports: [authRouter]

outgoing:
  calls: [checkPassword, createSession]

processes:
  - name: LoginFlow (step 2/7)
  - name: RegistrationFlow (step 3/5)
```

### 变更检测

```
detect_changes({scope: "all"})

summary:
  changed_count: 12
  affected_count: 3
  risk_level: medium
  affected_processes: [LoginFlow, RegistrationFlow]
```

---

## MCP 工具一览（16 个）

| 工具 | 功能 |
|------|------|
| `list_repos` | 发现所有已索引的仓库 |
| `query` | 流程分组混合搜索 |
| `context` | 360 度符号视图 |
| `impact` | 爆炸半径分析 |
| `detect_changes` | Git diff 影响映射 |
| `rename` | 多文件协调重命名 |
| `cypher` | 原始 Cypher 图查询 |
| `group_list` | 列出仓库组 |
| `group_sync` | 跨仓库契约匹配 |
| `group_contracts` | 查看跨仓库链接 |
| `group_query` | 跨仓库执行流搜索 |
| `group_status` | 仓库组新鲜度检查 |

---

## 安全与隐私

- **CLI**: 全部本地运行，无网络调用。索引存储在 `.gitnexus/`（已 gitignore）
- **Web**: 全部在浏览器内运行，代码不上传任何服务器
- 开源，可自行审计

---

## 企业版功能

- PR 自动审查（爆炸半径分析）
- 自动更新代码 Wiki
- 自动重索引
- 多仓库统一图谱
- OCaml 语言支持
- 优先功能/语言支持

官网：[akonlabs.com](https://akonlabs.com)

---

## 一句话总结

> GitNexus 给 AI 编程工具装上**代码架构大脑** — 通过构建知识图谱，让 AI 改代码时能看到完整依赖关系和影响范围，不再盲目编辑。

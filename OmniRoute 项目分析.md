# OmniRoute 项目分析

## 项目名称

**OmniRoute** — 免费AI网关：一个端点连接237个AI供应商（50+免费），为Claude Code、Codex、Cursor、Cline、Copilot等编程代理提供统一接入

- **GitHub 仓库**：[diegosouzapw/OmniRoute](https://github.com/diegosouzapw/OmniRoute)
- **项目主页**：[https://omniroute.online](https://omniroute.online)
- **开源协议**：MIT
- **主语言**：TypeScript

---

## 项目概述

OmniRoute 是一个功能极其丰富的开源 AI 网关，其核心理念是「**一个端点，永不中断**」。项目于 2026 年 2 月创建，仅约 5 个月便积累了超过 **8,800 个 Star**（今日新增 387），成为 GitHub 上增长最快的 AI 基础设施项目之一。

OmniRoute 将 **237 个 AI 供应商**（其中 50+ 提供免费额度，11 个永久免费无需注册）聚合在单一 `/v1` 端点之后，每月可提供约 **16 亿免费 token**（首次注册含赠金可达约 21 亿）。它不仅是一个简单的 API 代理，更是一个完整的 AI 中间件平台——集成了 17 种路由策略、9 引擎 token 压缩管线、3 层弹性容灾、MCP/A2A 协议支持、持久化记忆、护栏系统、评估框架、语义缓存以及 3 级代理隐身等企业级功能。

在 AI 编程工具（Coding Agent）爆发式增长的 2026 年，OmniRoute 的出现精准解决了一个核心痛点：开发者同时使用 Claude Code、Cursor、Copilot 等多种编程工具时，需要为每个工具分别配置不同的模型和 API 密钥。OmniRoute 通过 OpenAI ↔ Claude ↔ Gemini ↔ Responses API 的自动格式翻译，让所有编程工具只需配置一个 Base URL 即可无缝接入 237 个供应商的全部模型资源，并通过智能降级确保「永不停机」。

---

## 核心功能

### 1. 多供应商聚合（237 个供应商）

OmniRoute 按认证类型和能力维度对供应商进行了精细分类：

**按认证类型：**
- **20 个 OAuth 供应商**：Claude Code、Codex、Cursor、Gemini CLI、Antigravity 等编程工具的订阅服务
- **158 个 API Key 供应商**：OpenAI、Groq、NVIDIA、Cerebras、Mistral、DeepSeek、Qwen 等
- **11 个永久免费供应商**：Kiro、Qoder、Pollinations、LongCat、Cloudflare AI、Gemini CLI、NVIDIA NIM、Cerebras 等（无需信用卡）
- **11 个本地模型供应商**：Ollama、LM Studio、vLLM、llama.cpp 等

**按能力维度：**
23 个 Web 搜索 · 11 个搜索 · 7 个音频 · 24 个图像 · 14 个视频 · 14 个 Embeddings · 8 个 Rerank · 6 个音乐生成

### 2. Combo 系统 — 旗舰特性

Combo 是 OmniRoute 最具创新性的功能——它将多个模型串联成一条自动降级链。当某个模型的配额耗尽时，请求会无缝滑向下一个可用模型，用户完全无感。

**零配置自动模式：**

| 模型 ID | 优化目标 |
|---------|---------|
| `auto` | 🎯 平衡默认（LKGP 策略——粘性回退到上次成功的供应商） |
| `auto/coding` | 🧑‍💻 代码生成质量优先 |
| `auto/fast` | ⚡ 最低延迟优先 |
| `auto/cheap` | 💰 每单位 token 成本最低优先 |
| `auto/offline` | 🔋 最大配额/速率限制余量 |
| `auto/smart` | 🔭 质量优先 + 10% 探索新供应商 |

**示例 Combo 链：**
```
Combo: "always-on" Strategy: priority
1. cc/claude-opus-4-7 ← 订阅（充分使用）
2. cx/gpt-5.5 ← 第二订阅
3. glm/glm-5.1 ← 低价备份（$0.5/1M token）
4. kr/claude-sonnet-4.5 ← 免费无限（永不失败）
结果：4 层降级 = 零停机
```

### 3. 17 种路由策略

覆盖从简单到复杂的全部路由需求：

- **耗尽订阅类**：`priority`（优先级）、`fill-first`（填满优先）
- **负载分散类**：`round-robin`（轮询）、`p2c`（功率选择）、`least-used`（最少使用）
- **成本优化类**：`cost-optimized`（成本最优）
- **上下文感知类**：`context-relay`（上下文中继）、`context-optimized`（上下文优化）
- **随机类**：`random`（随机）、`strict-random`（严格随机）
- **智能自适应类**：`auto`（自动）、`lkgp`（上次好提供商粘性）、`reset-aware`（重置感知）、`reset-window`（重置窗口）、`headroom`（余量优先）、`fusion`（融合）

### 4. 9 引擎 Token 压缩管线（节省 15-95%）

这是 OmniRoute 最独特的技术亮点。9 个压缩引擎以管线方式顺序执行，每个引擎可独立启停：

| # | 引擎 | 功能 |
|---|------|------|
| 1 | Session-Dedup | 删除跨轮次重复内容 |
| 2 | CCR | 将大块内容归档，按需检索 |
| 3 | RTK | 智能工具结果过滤、去重和截断 |
| 4 | Headroom | 无损表格压缩（约 30%+） |
| 5 | Caveman | 规则化散文压缩（约 65-75%） |
| 6 | LLMLingua-2 | 基于 MobileBERT ONNX 的 ML 语义剪枝 |
| 7 | Lite | 空白和图片 URL 修剪 |
| 8 | Aggressive | 摘要 + 渐进老化 |
| 9 | Ultra | 启发式 token 剪枝 + 可选 SLM 层 |

**压缩预设：**

| 模式 | 节省率 | 适用场景 |
|------|--------|---------|
| 🪶 Lite | ~15% | 始终开启的安全默认 |
| 🪨 Standard (Caveman) | ~30% | 日常编码 |
| ⚡ Aggressive | ~50% | 长时间工具密集会话 |
| 🔥 Ultra | ~75% | 最大节省 |
| 🧰 RTK | 60-90% | Shell/测试/构建/Git 输出 |
| 🔗 Stacked (RTK → Caveman) | **78-95%** | 混合提示词 + 工具日志 |

**实测效果：**
- 原文（69 token）：*"The reason your React component is re-rendering is likely because you're creating a new object reference on each render cycle..."*
- 压缩后（19 token）：*"New object ref each render. Inline object prop = new ref = re-render. Wrap in useMemo."*

代码块、URL 和结构化数据始终保持字节级完整无损。

### 5. 3 层弹性容灾

| 层级 | 作用范围 | 触发条件 | 处理方式 |
|------|---------|---------|---------|
| 🔌 熔断器（Circuit Breaker） | 整个供应商 | 供应商宕机 | 跳过该供应商直到恢复（懒恢复探测） |
| 💤 连接冷却（Cooldown） | 单个账号/密钥 | 密钥被限速 | 仅冷却该密钥，其他密钥继续服务 |
| 🎯 模型锁定（Lockout） | 供应商 + 模型 | 模型配额耗尽 | 仅隔离该模型，其他模型继续服务 |

### 6. 代理隐身与 3 级代理

为绕过地区性 API 封锁（如俄罗斯、中国、伊朗、古巴、土耳其等）设计：
- 3 级代理：全局 · 按供应商 · 按连接
- 支持 SOCKS5 和 HTTP(S) 代理
- 一键代理市场（1proxy marketplace）
- 通过 wreq-js 实现 TLS JA3/JA4 指纹伪装
- CLI 指纹匹配每个供应商
- 跨请求 IP 保持（IP preservation）
- IPv4/IPv6 出口控制

### 7. MCP 与 A2A 协议支持

**MCP Server（95 个工具）：**
```bash
$ claude mcp add omniroute --type http --url http://localhost:20128/api/mcp/stream
✓ omniroute connected — 95 tools available
```
- 95 个工具，横跨 30 个作用域（路由、配额、记忆、技能等）
- 3 种传输层：stdio / HTTP / SSE

**A2A Server（6 个技能）：**
- 基于 JSON-RPC 2.0 + Agent Card
- 技能包括：智能路由、配额管理、发现、成本分析、健康报告

### 8. 持久化记忆

采用 FTS5 全文关键词搜索 + Qdrant 向量检索的混合召回架构，实现跨会话的持久化对话记忆。

### 9. 16+ 编程代理兼容

Claude Code、Codex、Cursor、Cline、GitHub Copilot、Gemini CLI、OpenCode、Kilo Code、Droid、Continue、Roo Code、Antigravity 等——全部通过单一端点配置即可使用。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 主语言 | TypeScript |
| 前端框架 | Next.js 16 |
| 运行时 | Node.js >= 22.0.0 |
| 部署方式 | npm 全局安装 / Docker / Desktop / PWA |
| ML 推理 | MobileBERT ONNX（LLMLingua-2 语义剪枝） |
| 向量存储 | Qdrant（记忆系统） |
| 全文搜索 | SQLite FTS5（记忆系统） |
| 代理协议 | SOCKS5 / HTTP(S)，TLS JA3/JA4 指纹伪装 |
| 标准 API | OpenAI / Claude / Gemini / Responses API 自动翻译 |
| 协议 | MCP（stdio/HTTP/SSE）、A2A（JSON-RPC 2.0） |
| 测试 | 14,965+ 测试用例 |
| 国际化 | 42 个语言区域 |
| 许可证 | MIT |

---

## 项目亮点

### 1. 「免费 AI 的终极网关」——精准的产品定位

OmniRoute 切中了 2026 年 AI 编程工具生态的一个核心痛点： Claude Code、Cursor、Copilot 等工具各自绑定特定的模型供应商，开发者切换工具时需要重新配置模型和密钥，且免费额度分散在不同平台难以充分利用。OmniRoute 以「一个端点、237 个供应商、永不中断」的极简理念，将所有复杂性隐藏在网关层之后，为开发者提供了统一、免费、可靠的 AI 接入体验。

### 2. 9 引擎压缩管线——从「节省 token」到「智能优化」

token 压缩并非新概念，但 OmniRoute 将其提升到了前所未有的高度。9 个可独立启停的压缩引擎组成管线，从简单的空白修剪到基于 ML 的语义剪枝（LLMLingua-2），从规则化散文压缩（Caveman）到工具结果智能过滤（RTK），层层递进。最强大的 Stacked 模式（RTK → Caveman 管线串联）可在混合提示词 + 工具日志场景下达到 78-95% 的压缩率，这对于工具密集型的 AI 编程场景（Claude Code、Codex 等）意味着巨大的成本节省。14,965 个测试用例确保了压缩的可靠性和正确性。

### 3. 4 层自动降级——真正的「零停机」

从 Subscription → API Key → Cheap → Free 的 4 层降级架构，配合 3 层弹性容灾（熔断器、连接冷却、模型锁定），确保即使在极端情况下（订阅过期、API Key 限速、模型配额耗尽），请求仍然能被路由到可用的免费供应商。这种「永不停机」的设计理念对于依赖 AI 进行持续开发的团队而言价值巨大。

### 4. Combo 系统——模型编排的声明式抽象

Combo 系统将复杂的模型编排逻辑抽象为声明式的配置。用户只需指定优化目标（coding/fast/cheap/offline/smart），系统自动选择最优路由策略和降级链。这种设计大幅降低了 AI 网关的使用门槛——从专家级配置简化为「选择模式」。

### 5. 全面的隐私与合规能力

3 级代理（全局/供应商/连接级）、TLS 指纹伪装、IP 保持等功能的加入，使 OmniRoute 不仅仅是一个技术工具，更是一个面向全球开发者（包括网络受限地区）的实用解决方案。PII 脱敏、安全内容过滤等护栏功能则确保了企业级使用场景下的合规性。

### 6. 令人惊叹的工程规模

14,965+ 测试用例、42 个语言区域、95 个 MCP 工具、17 种路由策略、237 个供应商适配器——这些数字背后是一个工程规模远超同类开源项目的庞大代码库。对于一个创建仅约 5 个月的项目而言，这种工程深度非常罕见。

---

## 应用场景

### 1. 个人开发者的零成本 AI 编程环境

对于预算有限的个人开发者，OmniRoute 提供了一种完全免费的方式接入 Claude、GPT、Gemini 等顶级模型。只需 `npm install -g omniroute && omniroute` 即可启动，然后将 Claude Code 或 Cursor 的 Base URL 指向 `localhost:20128/v1`，即可享受每月约 16 亿免费 token 的 AI 能力。

### 2. 团队的统一 AI 网关

对于使用多种编程工具的团队，OmniRoute 可作为统一的 AI 网关基础设施。团队成员无论使用 Claude Code、Cursor 还是 Copilot，都通过同一个端点访问 AI 能力，管理员可在 Dashboard 中统一监控配额使用、管理 API 密钥、配置路由策略。

### 3. 高 token 消耗场景的成本优化

对于大量使用 AI 编程助手的开发者（如全天候使用 Claude Code 进行项目开发），token 消耗是显著的成本压力。OmniRoute 的 9 引擎压缩管线（特别是 Stacked 模式的 78-95% 压缩率）可将 token 消耗降低一个数量级，配合自动路由到最便宜的可用供应商，实现显著的成本优化。

### 4. 网络受限地区的 AI 接入

对于位于 API 访问受限地区（如中国大陆、俄罗斯、伊朗等）的开发者，OmniRoute 的 3 级代理和 TLS 指纹伪装功能提供了一种可靠的方式来接入全球 AI 服务。

### 5. AI 应用的弹性后端

对于构建 AI 应用的开发者，OmniRoute 可作为弹性后端——其 17 种路由策略、自动降级和熔断机制为应用提供了生产级的可靠性保障，而 MCP 和 A2A 协议支持则使其能够无缝融入现代 AI Agent 架构。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Star 数** | 8,846 |
| **今日新增 Star** | 387 |
| **总 Fork 数** | 1,412 |
| **开发语言** | TypeScript |
| **许可证** | MIT |
| **创建时间** | 2026-02-13 |
| **项目年龄** | 约 5 个月 |
| **AI 供应商数** | 237（50+ 免费，11 永久免费） |
| **免费 Token/月** | ~16 亿 |
| **路由策略数** | 17 |
| **MCP 工具数** | 95 |
| **测试用例数** | 14,965+ |
| **国际化语言** | 42 |
| **支持编码代理** | 16+ |

### Star 增长分析

从 2026 年 2 月 13 日创建到 2026 年 7 月 1 日，OmniRoute 在约 5 个月内积累了 8,846 个 Star，平均每月增长约 1,770 个 Star。今日单日新增 387 个 Star，增长势头十分强劲。作为对比，许多知名开源项目需要一年以上才能达到这一 Star 量级。考虑到 AI 网关是一个相对垂直的领域，OmniRoute 的增长速度反映了开发者对「统一 AI 接入 + 免费 token + token 压缩」这一组合方案的强烈需求。

---


---

## 📋 更新记录

### 更新 1 — 2026 年 7 月 24 日（再次登上 Trending）
**更新原因**：Stars 从 22,804 增长至 27,204（+4,400），今日新增 1,929 星，v3.8.x 快速迭代发布

**最新动态**：
OmniRoute 持续快速迭代，已进入 v3.8.x 版本周期（当前 v3.8.49）。在这个版本周期中，项目新增了零配置自动路由功能、多个新 AI 供应商（Command Code、Z.AI 等）、更丰富的 OAuth 流程和更深的弹性容灾机制。Combo 目标健康分析和结构化 Combo 构建器为用户提供了可视化的路由链路组装体验。v3.6.8 版本新增了对 Claude Opus 4.7 的原生支持（含扩展上下文和缓存）、Node.js 24 LTS 完整兼容、以及 31 种语言的国际化和组合功能支持。项目已从最初描述的 237 个供应商扩展至 251 个（90+ 免费），每月免费 token 从 16 亿增至约 16 亿以上，并新增了 AgentRouter 和 Qoder AI 等零成本入口。Dashboard 安全性也得到加强，所有管理 API 路由强制会话认证。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 22,804 | 27,204 | +4,400 |
| 总 Forks | 2,800 | 3,565 | +765 |
| 主语言 | TypeScript | TypeScript | - |
| 许可证 | MIT | MIT | - |

**核心变化概要**：
- Stars 从 22,804 增长至 27,204，今日新增 1,929 星，保持快速迭代
- v3.8.x 版本周期新增零配置自动路由、Combo 健康分析、结构化 Combo 构建器
- AI 供应商从 237 扩展至 251 个（90+ 免费），新增 Command Code、Z.AI 等
- 新增 Claude Opus 4.7 原生支持、Node.js 24 LTS 兼容、31 语言国际化
- Forks 从约 2,800 增至 3,565，500+ 贡献者持续参与开发

---

---

## 📋 更新记录

### 更新 2 — 2026 年 7 月 25 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：
OmniRoute 作为 AI 编码网关的定位更加清晰和强大。从最初的 API 代理快速演变为覆盖 290+ 供应商和 500+ 模型的全功能 AI 网关。v3.7.0/v3.8.49 版本带来了 Cloudflare Workers AI 边缘推理支持、AWS Polly 语音合成集成、AgentRouter 供应商等重要更新。内置技能系统（file_read、file_write、http_request、eval_code、execute_command）通过 Docker 沙箱执行，增强了与 Claude Code、Codex、Cursor 等编码工具的深度集成能力。500+ 贡献者的社区规模使其成为 AI 网关领域最活跃的开源项目之一。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 22,804 | 29,127 | +6,323 |
| 总 Forks | - | 3,565 | - |

**核心变化概要**：
- Stars 从约 22.8K 增长至约 29.1K，单日新增 1,929 星，增长势头强劲
- 供应商扩展至 290+（90+ 免费），覆盖 500+ 模型，成为最全面的 AI 网关之一
- 新增 Cloudflare Workers AI 集成，支持边缘推理
- 引入 AgentRouter 作为新供应商（$200 免费额度）和 workspace 内置技能系统

---

## ?? 更新记录

### 更新 1 — 2026 年 7 月 26 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：Stars 从 22.8K 增长至 29.1K，作为免费 AI 网关持续迷你增长。今日单日 +1,929 Stars，反映社区对免费 AI 接入层的强烈需求。
- 提供商数从 200+ 扩展至 290+，免费提供商从 50+ 增至 90+
- 新增 Auto-Combo 引擎，基于 12 个因素（健康、配额、成本、延迟等）智能评分选择
- 新增 Cerebras、NVIDIA NIM、Cloudflare AI 等提供商集成
- 支持 33 个 CLI 工具，包括 Claude Code、Codex CLI、Cline、Kilo Code 等
- Docker 部署支持，含 Caddy HTTPS 和 Cloudflare Tunnels

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 22,804 | 29,127 | +6,323 |
| 总 Forks | 2,800 | 3,565 | +765 |

**核心变化概要**：
- 提供商数从 200+ 扩展至 290+，免费提供商从 50+ 增至 90+
- 新增 Auto-Combo 引擎，基于 12 个因素（健康、配额、成本、延迟等）智能评分选择
- 新增 Cerebras、NVIDIA NIM、Cloudflare AI 等提供商集成
- 支持 33 个 CLI 工具，包括 Claude Code、Codex CLI、Cline、Kilo Code 等
- Docker 部署支持，含 Caddy HTTPS 和 Cloudflare Tunnels

## 总结

OmniRoute 是 2026 年 AI 基础设施领域最具野心的开源项目之一。它不仅仅是一个 API 代理——而是一个功能全面、工程精良的 AI 中间件平台，覆盖了从供应商聚合、智能路由、token 压缩、弹性容灾到协议支持（MCP/A2A）、隐私保护、记忆管理等全栈需求。

**核心价值总结：**

1. **极致聚合**：237 个供应商、16 亿免费 token/月，一个端点全部搞定
2. **智能节省**：9 引擎压缩管线最高节省 95% token，Staked 模式下实测效果惊人
3. **永不中断**：4 层降级 + 3 层容灾，从付费订阅到免费供应商的完整降级链
4. **零门槛接入**：`npm install -g omniroute` 一行命令启动，所有编程工具即插即用
5. **工程深度**：14,965+ 测试、42 种语言、95 个 MCP 工具，工程规模远超同类项目
6. **全球可用**：3 级代理 + TLS 指纹伪装，覆盖网络受限地区

**与同类项目对比：**

| 维度 | OmniRoute | FreeLLMAPI | OneAPI |
|------|-----------|------------|--------|
| 供应商数量 | 237 | 17 | ~100 |
| 永久免费供应商 | 11 | 4 | 少量 |
| 路由策略 | 17 种 | 基础 failover | 基础负载均衡 |
| Token 压缩 | 9 引擎管线（最高 95%） | ❌ | ❌ |
| MCP/A2A 支持 | ✅（95 工具） | ❌ | ❌ |
| 代理隐身 | ✅（TLS 指纹伪装） | ❌ | 基础代理 |
| 编程代理兼容 | 16+ | 基础兼容 | 需手动配置 |
| 测试覆盖 | 14,965+ | 有限 | 有限 |

OmniRoute 的定位比 FreeLLMAPI 更为全面和野心勃勃——它不仅聚合免费 token，更构建了一个完整的 AI 中间件生态。对于任何使用 AI 编程工具的开发者而言，OmniRoute 都是一个值得认真评估的基础设施选择。其 8,846 个 Star 和每日 387 个新增 Star 的增长速度，充分印证了市场对这类「统一 AI 网关」方案的迫切需求。

---

*数据来源：GitHub 仓库 (diegosouzapw/OmniRoute)，2026 年 7 月 21 日 访问*

*数据来源：GitHub 仓库 (diegosouzapw/OmniRoute), 2026 年 7 月访问*
*首次分析：2026 年 7 月 | 最近更新：2026 年 7 月*
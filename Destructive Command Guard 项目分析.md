# Destructive Command Guard 项目分析

## 项目名称
**Destructive Command Guard (dcg)** — 高性能 AI 编程代理危险命令拦截器，防止代理执行破坏性操作
- **GitHub**: [Dicklesworthstone/destructive_command_guard](https://github.com/Dicklesworthstone/destructive_command_guard)
- **许可证**: MIT

---

## 项目概述
Destructive Command Guard（简称 dcg）是一个用 Rust 编写的高性能安全钩子工具，专门用于拦截 AI 编程代理（如 Claude Code、Codex CLI、Gemini CLI、Cursor 等）执行的危险 shell 和 git 命令。随着 AI 编程代理在日常开发中的普及，代理偶尔会执行灾难性命令（如 `rm -rf ./src`、`git reset --hard`、`DROP TABLE users`），导致代码丢失和系统损坏。dcg 通过 PreToolUse 钩子在命令执行前进行拦截，提供阻止说明和更安全的替代方案。

dcg 采用零配置设计，开箱即用即可拦截常见的危险命令。它提供了 50+ 安全规则包，覆盖数据库、Kubernetes、Docker、AWS/GCP/Azure 云平台、Terraform 基础设施即代码、CI/CD 管道、密钥管理等各个领域。项目利用 SIMD 加速实现亚毫秒级过滤延迟，采用 Fail-Open 设计确保不会因超时或解析错误阻塞正常工作流。

项目支持 12+ 主流 AI 编程代理和 IDE，包括 Claude Code、Codex CLI、Gemini CLI、GitHub Copilot CLI、Cursor IDE、Hermes Agent、Grok 等，安装方式统一且简洁，支持 Linux、macOS、Windows（含 WSL）全平台。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 零配置防护 | 开箱即用拦截危险 git 和文件系统命令，无需额外配置 |
| 50+ 安全规则包 | 覆盖数据库、K8s、Docker、云平台、Terraform、CI/CD、密钥管理等 |
| 亚毫秒级延迟 | 基于 SIMD 加速的命令过滤，对工作流几乎零感知 |
| Heredoc/内联脚本扫描 | 捕获 `python -c "os.remove(...)"` 等嵌入脚本中的危险操作 |
| 智能上下文检测 | 区分数据用途（如 `grep "rm -rf"`）和执行用途（如 `rm -rf /`） |
| Fail-Open 设计 | 超时或解析错误时不阻塞工作流，确保开发者体验不受影响 |
| SARIF 输出 | `dcg scan` 生成标准 SARIF 2.1.0 格式报告，便于集成安全工具链 |
| 多代理支持 | 兼容 12+ 主流 AI 编程代理和 IDE |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | Rust (Edition 2024, nightly) |
| 规则引擎 | 自研 SIMD 加速匹配引擎 |
| 配置格式 | TOML |
| 安装方式 | Shell 脚本 / PowerShell / 源码编译 |

---

## 项目亮点

### 首个系统性解决 AI 代理安全隐患的工具
dcg 是目前唯一专门针对 AI 编程代理危险命令拦截的系统性工具。它不依赖代理自身的安全机制（因为不同代理的安全能力参差不齐），而是通过操作系统级别的钩子实现统一防护，为所有 AI 编程代理提供了一致的安全底线。

### 模块化规则包架构
dcg 采用模块化的安全规则包设计，用户可以按需启用特定领域的规则包（如数据库、Kubernetes、AWS 等），也可以自定义规则。这种设计使得安全策略可以随团队需求灵活扩展，而不会因为规则过多影响性能。

### 智能上下文感知
dcg 的核心创新之一是上下文检测能力——它能区分命令是作为数据被引用（如搜索日志中的 `rm -rf`），还是作为命令被执行。这避免了误报对正常工作流的干扰，是实际可用性的关键保障。

---

## 应用场景

### AI 编程代理日常使用防护
开发团队使用 Claude Code、Cursor 等 AI 编程代理时，dcg 作为安全网防止代理误执行破坏性命令。特别是在代理处理涉及 git 操作、文件删除、数据库修改等高风险任务时，dcg 的拦截能力至关重要。

### DevOps/基础设施自动化安全
在 AI 代理辅助基础设施管理（Terraform、Kubernetes、Docker）的场景中，dcg 的云平台和容器相关规则包可以防止代理误删云资源、误操作容器集群等灾难性操作。

### 企业级安全合规
对于对安全合规有严格要求的企业，dcg 的 SARIF 输出和可审计日志可以与现有安全工具链集成，满足安全审计和合规检查的需求。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 2,435 |
| 总 Forks | 91 |
| 今日新增 | 444 |
| 主要语言 | Rust |
| 创建时间 | 2026-01-07 |

---

## 总结
Destructive Command Guard 是 AI 编程时代的安全基础设施工具，以亚毫秒级性能为 12+ 主流 AI 代理提供统一的危险命令拦截能力，50+ 模块化规则包覆盖从本地文件系统到云端基础设施的全方位安全防护。

---

*数据来源：GitHub 仓库 (Dicklesworthstone/destructive_command_guard)，2026 年 7 月访问*

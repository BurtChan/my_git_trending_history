# Shannon - AI 自动化渗透测试工具

## 基本信息

| 属性 | 详情 |
|------|------|
| **项目名称** | Shannon (Shannon Lite) |
| **开发团队** | Keygraph |
| **GitHub 地址** | [https://github.com/KeygraphHQ/shannon](https://github.com/KeygraphHQ/shannon) |
| **项目描述** | 自主式白盒 AI 渗透测试工具，面向 Web 应用和 API 安全测试 |
| **开源许可** | AGPL-3.0 (Shannon Lite) / 商业许可 (Shannon Pro) |
| **主要语言** | TypeScript / Node.js |
| **官方站点** | [keygraph.io](https://keygraph.io) |

---

## 解决什么问题

现代开发团队借助 Claude Code、Cursor 等 AI 工具持续高速交付代码，但渗透测试通常一年只做一次。这造成了一个巨大的安全空白：在其余 364 天里，漏洞可能不知不觉地被推送到生产环境。

Shannon 的目标就是填补这一空白，提供按需的、自动化的渗透测试能力，可以针对每次构建或发布运行，从而将安全测试从"年度事件"转变为"持续流程"。

---

## 核心特性

### 1. 全自主运行
- 一条命令即可启动完整渗透测试
- 自动处理 2FA/TOTP 登录（包括 SSO）、浏览器导航、漏洞利用和报告生成
- 无需人工干预

### 2. 可复现的 PoC 漏洞利用
- 最终报告仅包含经过验证的、可利用的发现
- 提供可直接复制粘贴的概念验证 (Proof-of-Concept) 代码
- 无法被成功利用的漏洞不会被报告（"No Exploit, No Report" 原则）

### 3. OWASP 漏洞覆盖
- 注入攻击 (Injection)
- 跨站脚本 (XSS)
- 服务端请求伪造 (SSRF)
- 身份认证/授权绕过 (Broken Authentication & Authorization)

### 4. 代码感知的动态测试
- 分析源代码以指导攻击策略
- 结合浏览器自动化和 CLI 工具对运行中的应用执行真实漏洞利用
- 白盒+黑盒结合的混合测试方法

### 5. 集成安全工具链
- Nmap - 端口扫描与服务识别
- Subfinder - 子域名发现
- WhatWeb - Web 技术指纹识别
- Schemathesis - API 模式测试

### 6. 并行处理
- 漏洞分析和利用阶段按攻击类别并发运行
- 5 个并行代理同时工作

---

## 技术架构

Shannon 采用多代理 (Multi-Agent) 架构，基于 Anthropic Claude Agent SDK 构建，通过五个阶段完成安全测试：

```
阶段 1: 预侦察 (Pre-Reconnaissance)
  → Nmap、Subfinder、WhatWeb 扫描 + 源代码分析
  → 识别应用框架、入口点和潜在攻击面

阶段 2: 侦察 (Reconnaissance)
  → 构建综合攻击面地图
  → 通过浏览器自动化实时探索应用

阶段 3: 漏洞分析 (Vulnerability Analysis)
  → 5 个并行代理按 OWASP 类别搜索潜在缺陷
  → 执行结构化数据流分析，追踪用户输入到危险汇聚点的路径

阶段 4: 漏洞利用 (Exploitation)
  → 将假设转化为实际攻击证明
  → 严格执行"无法利用 = 不报告"策略

阶段 5: 报告生成 (Reporting)
  → 汇总所有已验证发现
  → 生成专业级渗透测试报告
```

每次扫描在独立的临时 Docker 容器中运行，通过 Temporal 任务队列管理。

---

## 技术栈

| 类别 | 技术 |
|------|------|
| **AI 引擎** | Anthropic Claude (Haiku / Sonnet / Opus 三层模型) |
| **运行时** | Node.js 18+, Docker |
| **包管理** | pnpm |
| **工作流引擎** | Temporal |
| **安全工具** | Nmap, Subfinder, WhatWeb, Schemathesis |
| **CI 支持** | CLI / 可集成到 CI/CD 流程 |
| **云 AI 支持** | AWS Bedrock, Google Vertex AI, 自定义端点 |

---

## 产品线对比

| 能力 | Shannon Lite (免费) | Shannon Pro (商业) |
|------|---------------------|---------------------|
| **许可** | AGPL-3.0 | 商业 |
| **静态分析** | 代码审查提示 | 完整 CPG 数据流分析 + LLM 推理 |
| **动态测试** | 自主 AI 渗透测试 | 渗透测试 + 静态-动态关联 |
| **SCA/秘密扫描** | 无 | 有，含可达性分析 |
| **业务逻辑测试** | 无 | 自动不变量发现 + 模糊测试 |
| **CI/CD 集成** | 手动/CLI | 原生 CI/CD, GitHub PR 扫描 |
| **部署** | CLI | 托管云或自托管 |

---

## 性能基准

- 在 XBOW 安全基准测试中，Shannon Lite 取得了 **96.15% (100/104 次利用成功)** 的成绩
- 在 OWASP Juice Shop 中发现了 **20+ 个漏洞**，包括认证绕过和数据库泄露
- 完整测试运行通常需要 **1~1.5 小时**
- 使用 Claude 4.5 Sonnet 模型的成本约 **$50 USD**（视应用复杂度而定）

---

## 使用方式

```bash
# 快速开始 (推荐)
npx @keygraph/shannon setup                          # 配置凭据
npx @keygraph/shannon start -u https://your-app.com -r /path/to/repo

# 支持工作区恢复
npx @keygraph/shannon start -u https://your-app.com -r /path/to/repo -w my-audit

# 查看日志和状态
npx @keygraph/shannon logs <workspace>
npx @keygraph/shannon status
```

---

## 适用场景

1. **开发团队自测** - 每次构建前运行自动化渗透测试，将安全左移
2. **安全团队辅助** - 作为渗透测试的补充工具，提供持续的漏洞检测
3. **CI/CD 集成** - 在流水线中自动执行安全验证 (Shannon Pro)
4. **安全培训与演练** - 对 OWASP Juice Shop 等靶场进行实战演练
5. **合规审计** - 生成带有可复现 PoC 的专业渗透测试报告

---

## 注意事项

- **仅限白盒测试** - 需要访问应用源代码
- **严禁用于生产环境** - 利用代理会主动执行攻击，可能修改/删除数据
- **需要明确授权** - 必须获得目标系统所有者的书面授权
- **需要人工审查** - LLM 仍可能产生幻觉内容，人工验证不可省略
- **Windows 支持** - 推荐 WSL2 方式运行

---

## 一句话总结

> Shannon 是一款基于多代理架构和 Anthropic Claude 的自主式白盒 AI 渗透测试工具，通过源代码分析识别攻击向量并执行真实漏洞利用来验证漏洞，以"无法利用即不报告"的原则为 Web 应用和 API 安全提供按需、持续的安全测试能力。

---

## 相关链接

- [GitHub 仓库](https://github.com/KeygraphHQ/shannon)
- [Keygraph 官网](https://keygraph.io)
- [Discord 社区](https://github.com/KeygraphHQ/shannon#community--support)
- [基准测试详情](https://github.com/KeygraphHQ/shannon#benchmark)

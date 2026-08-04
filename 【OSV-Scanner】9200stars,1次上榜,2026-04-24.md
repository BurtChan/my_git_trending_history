# OSV-Scanner 项目分析

## 项目名称

**OSV-Scanner** — Google 开源的漏洞扫描工具，连接项目依赖与全球最大开源漏洞数据库

- **GitHub**: [google/osv-scanner](https://github.com/google/osv-scanner)
- **许可证**: Apache-2.0

---

## 项目概述

OSV-Scanner 是由 Google 开发并维护的**免费开源漏洞扫描工具**，使用 Go 语言编写，是 OSV.dev（全球最大的开源漏洞数据库）的官方扫描前端。它将项目的依赖列表与已知漏洞进行匹配，帮助开发者快速识别软件供应链中的安全风险。

OSV-Scanner 的核心优势在于其背后强大的 OSV.dev 数据库——该数据库聚合了 30 多个权威漏洞来源（包括 GitHub Security Advisories、PyPA、RustSec、Global Security Database 等），提供统一、机器可读的漏洞信息。与其他商业漏洞扫描工具不同，OSV-Scanner 采用精确的版本映射机制，显著减少了误报率，让开发者获得真正可操作的漏洞通知。

V2 版本引入了**引导式修复（Guided Remediation）**功能，不仅能发现漏洞，还能分析依赖图并推荐最小化的版本升级方案，按严重程度、依赖深度和投资回报率排序——这一功能通常只有昂贵的商业工具才具备。此外，OSV-Scanner 支持容器镜像扫描、SBOM 扫描、许可证扫描等企业级功能，同时提供 CLI 工具和 Go 库两种使用方式。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **多生态依赖扫描** | 支持 11+ 语言生态系统和 19+ 锁文件格式（npm、Maven、Go、Python、Rust 等） |
| **容器镜像扫描** | 感知 Docker 层级的扫描，识别 Debian/Ubuntu/Alpine 基础镜像中的漏洞包，精确定位引入漏洞的层 |
| **引导式修复** | 分析依赖图，推荐最小版本升级方案，按严重程度、依赖深度和 ROI 排序（支持 npm 和 Maven） |
| **SBOM 扫描** | 支持扫描 CycloneDX（sbom.cdx.json）等格式的软件物料清单 |
| **许可证扫描** | 实验性依赖许可证合规扫描功能 |
| **CI/CD 集成** | 官方 GitHub Action（google/osv-scanner-action），支持 SARIF 输出，可对接 GitHub Security 选项卡 |
| **离线扫描** | 支持离线操作，适用于气隙环境 |
| **交互式 HTML 报告** | 生成丰富的交互式 HTML 漏洞报告 |
| **Go 库调用** | 可作为 Go 包导入，用于编程集成（github.com/google/osv-scanner/v2/pkg/osvscanner） |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Go（Golang） |
| **核心库** | OSV-Scalibr — Google 可扩展的软件组成分析库 |
| **数据源** | OSV.dev API、deps.dev API、各包管理器注册中心 |
| **漏洞数据库** | OSV.dev — 聚合 30+ 漏洞公告来源 |
| **CI/CD** | GitHub Actions（官方 Action: google/osv-scanner-action） |
| **安装方式** | 预编译二进制、go install、Homebrew、Docker、GitHub Releases |
| **文档** | Jekyll + Just the Docs 主题 |

---

## 项目亮点

### 精准度远超同类工具
OSV 格式将漏洞明确映射到受影响的精确包版本，相比闭源替代方案产生显著更少的误报。每个漏洞公告来自开放、权威、社区可改进的来源。

### 引导式修复降低修复成本
不仅能发现漏洞，还能主动推荐最小化的版本升级方案并按优先级排序——这一功能通常只有昂贵的商业安全工具（如 Snyk、Dependabot Pro）才提供。

### 容器层级感知扫描
精确定位 Docker 镜像中引入每个漏洞包的具体层，过滤掉基础镜像中的无关发现，为开发者提供精准的修复上下文。

### 完全免费开源
Apache 2.0 许可证，无需账号、无使用限制、无付费墙。由 Google 持续维护和更新。

---

## 应用场景

### CI/CD 流水线安全门禁
通过 GitHub Actions 集成，在 PR 合并前自动扫描依赖漏洞，发现关键漏洞时阻止合并。

### 容器镜像安全审计
在部署到生产镜像仓库前扫描 Docker 镜像，确保不将已知漏洞带入生产环境。

### 依赖升级规划
使用引导式修复（osv-scanner fix）获取 npm 和 Maven 项目的优先级升级建议，减少人工评估工作量。

### OpenSSF Scorecard 合规
OSV-Scanner 集成了 OpenSSF Scorecard 的漏洞检查项，帮助开源项目提升安全评分。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 9,200+ |
| **总 Forks** | 600+ |
| **今日新增 Stars** | 147 |
| **许可证** | Apache-2.0 |
| **创建时间** | 2022 年 11 月 |
| **主要语言** | Go |

---

## 总结

OSV-Scanner 是 Google 出品的**开源漏洞扫描标准工具**，9.2k+ Stars。它基于全球最大的开源漏洞数据库 OSV.dev，支持 11+ 语言生态系统和容器镜像扫描，提供商业级引导式修复功能。完全免费开源（Apache-2.0），是任何注重供应链安全的开发团队的必备工具。

---

*数据来源：GitHub 仓库 (google/osv-scanner)、google.github.io/osv-scanner（2026 年 4 月访问）*

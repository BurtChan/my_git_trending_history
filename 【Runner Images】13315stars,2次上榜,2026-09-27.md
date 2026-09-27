# GitHub Actions Runner Images 项目分析

## 项目名称

**Runner Images** — GitHub Actions 托管运行器虚拟机镜像的源码仓库，CI 基础设施透明化的官方窗口

- **GitHub**: [actions/runner-images](https://github.com/actions/runner-images)
- **许可证**: MIT
- **语言**: PowerShell / Packer 模板
- **创建时间**: 2019-06-05

---

## 项目概述

这个仓库包含构建 GitHub Actions 托管运行器（GitHub-hosted runners）与 Azure Pipelines Microsoft 托管代理所用 VM 镜像的全部源码。每一次你在 GitHub Actions 上跑 `runs-on: ubuntu-latest`，背后都是这个仓库的 Packer 模板构建出来的虚拟机镜像。

它的价值在于「基础设施即文档」：CI 环境里预装了什么版本的 Node、Python、Docker，全部公开可查；镜像何时更新、哪个工具被移除，都有 issue 和 commit 记录可追溯。13,315 stars 来自全球开发者——不是因为它是个「产品」，而是因为几乎所有 CI 用户都依赖它，遇到「昨天还能跑今天挂了」的环境问题时第一反应就是来这个仓库查变更。

当前提供 Ubuntu 26.04（x64 与 arm64）等镜像，明确表示不计划支持其他 Linux 发行版（建议用 Docker 或自托管运行器替代），macOS 镜像源码开源但 CI 暂不接受外部 PR。2025 年起 arm64 运行器正式可用，arm64 镜像成为新热点。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| VM 镜像源码 | Ubuntu / Windows / macOS 全平台镜像的 Packer 生成模板 |
| 预装软件清单 | 每个镜像的 Included Software 文档（如 Ubuntu2604-Readme.md） |
| 自定义构建 | docs 提供从源码自建 VM 镜像与 Azure 资源的完整指引 |
| 预装策略文档 | 明确哪些工具装最新版、哪些锁定版本（Preinstallation Policy） |
| 变更追踪 | 镜像部署计划与工具变更通过 issue 公告 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 镜像构建 | Packer + Azure DevOps pipelines |
| 脚本 | PowerShell（Windows）与 Bash（Linux） |
| 平台 | Azure 虚拟机 |

---

## 项目亮点

### CI 环境全透明
预装软件逐项公开、版本策略成文——把「云上黑盒 CI 环境」变成可审计的开源基础设施，这是 GitHub Actions 生态信任的基石。

### arm64 时代的先行者
Ubuntu 26.04 arm64 镜像与 arm64 托管运行器同步落地，为 ARM 服务器与 Apple Silicon 本地开发的一致性测试铺路。

### 自建运行器路径
提供从本仓库源码构建完全自定义 VM 镜像的文档，企业可以预装自有工具链后接入 Azure，实现「托管体验 + 定制环境」兼得。

---

## 应用场景

### CI 故障排查
流水线莫名失败时，查镜像预装软件清单与近期部署公告，快速定位是否为环境变更（工具升降级、镜像退役）所致。

### 锁定可复现环境
将 workflow 的 runs-on 固定到具体镜像标签（如 ubuntu-26.04）而非 latest，配合本仓库的版本清单规划升级窗口。

### 构建定制化自托管镜像
参照仓库模板与文档，在预装清单中加入公司内部工具链，构建自有镜像用于自托管运行器。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 13,315 |
| 总 Forks | 3,869 |
| 今日新增 | +111 |
| Open Issues | 137 |

## 📋 更新记录

### 更新 1 — 2026年9月27日

时隔一天再次登上 Trending，Star 增长稳定（+111），反映 CI 环境变更透明化需求持续存在。

近期动态：仓库维持高频镜像版本发布节奏，9 月 25 日一次性推送 ubuntu26 / win22 / win25 / win11-arm64 / win11-vs2026-arm64 等多条镜像版本更新（版本号 20260920–20260922 系列），其中 win11-vs2026-arm64 与 win25 均为面向 Visual Studio 2026 新工具链的镜像迭代；仓库保持每日 readme 版本同步，是「基础设施即文档」运作模式的持续体现。

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|------|------|------|
| 总 Stars | 13,204 | 13,315 | +111 |
| 总 Forks | 3,857 | 3,869 | +12 |
| 今日新增 | +13 | +111 | — |
| Open Issues | 131 | 137 | +6 |

**核心变化：**
- ubuntu26 镜像版本 20260920.143.1 发布，x64 与 arm64 双架构同步维护
- win11-vs2026-arm64 镜像迭代（20260920.164.1），跟进 Visual Studio 2026 工具链
- win25 镜像版本 20260922.270.2 更新，保持 Windows 25 预览环境同步
- Open Issues 从 131 增至 137，社区对镜像变更的跟踪讨论活跃

---

## 总结

全球最大 CI 平台的运行器镜像源码仓库——「跑在 ubuntu-latest 上」这行 YAML 背后的一切都在这里透明公开，是 CI 基础设施可审计性的标杆实践。

---

*数据来源：GitHub 仓库 (actions/runner-images)，2026 年 9 月 27 日访问*

*首次分析：2026 年 9 月 26 日 | 最近更新：2026 年 9 月 27 日*

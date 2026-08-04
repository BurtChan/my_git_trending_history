# CUA 项目分析

## 项目名称

**Cua (Computer-Use Agents)** — 开源计算机使用代理基础设施平台，用于训练、评估和部署桌面 AI 代理

- **GitHub**: [trycua/cua](https://github.com/trycua/cua)
- **许可证**: MIT

---

## 项目概述

Cua（Computer-Use Agents）是一个为计算机使用代理构建的开源基础设施和工具链。项目旨在为研究人员和工程师提供一个安全、可复现的环境，用于训练、评估和部署能够自主控制桌面操作系统的 AI 代理。项目包含沙箱环境、SDK、基准测试和开发工具，支持代理与真实应用程序和窗口进行交互，覆盖 macOS、Linux、Windows、Android 等多个操作系统平台。

项目的核心理念是"构建、基准测试和部署使用计算机的代理"。它通过提供 Agent-Ready 沙箱，使 AI 代理能够在隔离的虚拟环境中安全地与完整桌面操作系统进行交互，执行点击、输入、浏览等操作。项目由 Francesco Bonacci 领导，他曾就职于微软，共同撰写了 Windows Agent Arena 论文，在计算机使用代理领域有深厚积累。

Cua 项目采用 Monorepo 架构，包含多个子包：cuabot（多代理计算机使用沙箱 CLI）、cua-agent（AI 代理框架）、cua-bench（基准测试和 RL 环境）、lume（Apple Silicon 上的 macOS/Linux 虚拟化管理）。项目还提供 Cua Cloud 云服务，支持大规模部署计算机使用代理，并推出了 Cua Playground 让用户可以直接在浏览器中体验代理和沙箱功能。

---

## 核心功能

- 多操作系统沙箱支持（Linux 容器、Linux VM、macOS、Windows、Android、自定义镜像）
- CuaBot 多代理协同计算机使用，支持代理与人类在同一沙箱桌面交互
- Cua-Bench 基准测试平台，支持 OSWorld、ScreenSpot、Windows Arena 等标准评测
- Lume 虚拟化管理，在 Apple Silicon 上实现接近原生性能的 macOS/Linux VM 管理
- cua-agent AI 代理框架，支持多个模型提供商和简化 API
- Human-In-The-Loop 人机协同支持
- Composite Agents 组合代理能力，允许组合多个代理协同工作
- App-Use 功能，将代理交互限制在特定应用程序中
- VLM Router 视觉语言模型路由器，支持在不同模型提供商间切换
- Trajectory Viewer 轨迹查看器，用于探索、调试和分析代理行为
- Cua CLI 命令行工具，直接管理 Cua Cloud 资源
- 沙箱化 Python 执行，在隔离虚拟环境中安全运行 Python 函数
- 云容器部署，支持大规模云端部署计算机使用代理
- Cua Playground 浏览器内体验代理和沙箱

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Python |
| **前端/CLI** | TypeScript / JavaScript |
| **macOS 虚拟化** | Swift（Apple Virtualization.Framework） |
| **依赖管理** | uv（Python）、pnpm（Node.js） |
| **容器化** | Docker |
| **虚拟化** | QEMU/KVM |
| **代码格式化** | Black、Ruff、isort（Python）；Prettier（JS/TS） |
| **CI/CD** | GitHub Actions |
| **代码质量** | Pre-commit hooks |

---

## 项目亮点

### 全平台覆盖
支持 Linux 容器、Linux VM、macOS、Windows、Android 及自定义镜像（.qcow2、.iso），是目前支持操作系统最全面的计算机使用代理平台之一。

### 端到端工具链
从沙箱环境、代理框架到基准评测和云部署，提供完整的开发-测试-部署流水线，开发者无需拼接多个工具。

### Apple Silicon 优化
通过 Lume 组件利用 Apple Virtualization.Framework，在 Apple Silicon 上实现接近原生性能的 macOS/Linux 虚拟化，解决了 ARM 平台上桌面代理测试的难题。

### 多代理协同与人机交互
CuaBot 支持多个代理和人类在同一沙箱桌面中协同操作，Human-In-The-Loop 机制让 AI 代理可以在需要时请求人类干预，开创了协作式计算机使用的新模式。

---

## 应用场景

### AI 代理研究与训练
研究人员可以利用 Cua 的安全沙箱环境和轨迹录制工具，收集高质量的人类操作轨迹数据，用于训练和微调计算机使用模型。

### 自动化测试与 QA
企业可利用计算机使用代理自动执行跨平台桌面应用的 UI 测试、回归测试和兼容性测试，覆盖 macOS、Linux 和 Windows 多个平台。

### RPA 与业务流程自动化
将重复性的桌面操作（如数据录入、报表生成、系统配置等）交由 AI 代理自动完成，提高工作效率。

### 基准评测与模型对比
利用 Cua-Bench 在 OSWorld、ScreenSpot、Windows Arena 等标准基准上评估和对比不同计算机使用代理的性能，为模型选型提供依据。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 14,100 |
| **总 Forks** | 872 |
| **今日新增 Stars** | Trending 日榜上榜 |
| **许可证** | MIT |
| **创建时间** | ~2025 年 |
| **主要语言** | Python |
| **贡献者** | 61 人 |

---

## 总结

Cua 是一个快速崛起的开源计算机使用代理基础设施项目，以约 14,100 颗 Star 和 872 个 Fork 成为 GitHub 热门项目。它通过提供全平台沙箱、代理框架、基准测试和云部署等端到端工具链，大幅降低了构建、评估和部署桌面控制 AI 代理的门槛。项目在 Apple Silicon 优化、多代理协同、人机交互等方面表现突出，适用于 AI 研究、自动化测试、RPA 等多个场景，是计算机使用代理领域最完善的开源基础设施之一。

---

*数据来源：GitHub 仓库 (trycua/cua)，2026 年 4 月访问*

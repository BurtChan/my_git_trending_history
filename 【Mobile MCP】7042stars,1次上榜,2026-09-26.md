# Mobile MCP 项目分析

## 项目名称

**Mobile MCP** — 移动设备自动化与数据抓取的 MCP Server，覆盖 iOS/Android 真机、模拟器与仿真器

- **GitHub**: [mobile-next/mobile-mcp](https://github.com/mobile-next/mobile-mcp)
- **许可证**: Apache-2.0
- **语言**: TypeScript
- **创建时间**: 2025-03-28

---

## 项目概述

Mobile MCP 是 Mobile Next 团队开源的 Model Context Protocol 服务器，让 AI Agent 通过标准 MCP 接口直接操控移动设备：在真机、模拟器（Android Emulator / iOS Simulator）上执行 UI 操作、截屏、抓取应用数据。2025 年 3 月创建以来已获得 7,042 stars，是移动端 Agent 化工具链中的热门项目。

它的核心理念是把「移动设备驱动能力」抽象为一组 MCP 工具——Agent 调用 open-app、tap、swipe、screenshot 等原子操作，即可完成「打开 App→搜索→下单→截图汇报」这类跨应用自动化流程，无需为每个 App 编写专用脚本。仓库提供 Docker 部署、多语言 README（含中文）、ROADMAP 公开演进计划，并内置 skills/mobile-automation 技能目录，可被 Claude 等支持 Skills 的 Agent 直接装载。作为 Mobile Next 工具链的一部分，它还能与云端远程真机服务联动。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 跨平台设备驱动 | iOS 真机/Simulator、Android 真机/Emulator 统一接口 |
| UI 自动化 | 启动 App、点击、滑动、输入等原子操作 |
| 截屏与视觉定位 | 获取屏幕截图供 Agent 视觉判断 |
| 数据抓取 | 从 App 界面提取文本与结构化数据 |
| mobile-automation Skill | 内置 Agent 技能包，Claude 等 Agent 直接装载使用 |
| 云端真机联动 | 接入 Mobile Next cloud 远程设备池 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 实现 | TypeScript（Node.js） |
| 协议 | Model Context Protocol (MCP) |
| 设备通信 | ADB（Android）/ xcrun simctl（iOS）等 |
| 质量保障 | Mocha + c8 覆盖率，Husky 钩子 |
| 部署 | npm / Docker |

---

## 项目亮点

### 一套接口驱动所有移动端形态
真机、模拟器、仿真器统一抽象，Agent 不需要关心底层差异——iOS 用 simulator、Android 用 emulator 的测试矩阵可以在同一个会话里切换。

### Agent Skill 原生设计
skills/mobile-automation 目录表明项目按「Agent 技能包」形态交付，而非仅是给开发者用的库——这是 2026 年工具项目向 Agent 生态靠拢的典型形态。

### 开放治理与本地隐私承诺
ROADMAP 公开、社区反馈驱动优先级；隐私政策明确「本地运行、只与你连接的设备通信」，对设备数据不出本地是敏感场景的关键承诺。

---

## 应用场景

### AI 驱动的移动端 E2E 测试
用自然语言描述测试用例，Agent 通过 Mobile MCP 在真机上执行并截图验证，替代传统 Appium 脚本维护。

### 跨 App 自动化工作流
「打开购物 App 比价→截图→发到群里」这类跨应用流程，由 Agent 编排 MCP 原子操作完成。

### 移动端数据采集
对无 API 的 App，通过 UI 驱动+屏幕抓取的方式获取数据，适合个人自动化的轻量采集需求。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 7,042 |
| 总 Forks | 626 |
| 今日新增 | +143 |
| Open Issues | 43 |

---

## 总结

把 iOS/Android 真机与模拟器封装成 MCP 工具集的移动自动化服务器——Agent 用一套接口驱动所有移动设备形态，是移动端 Agent 化浪潮中的基础设施级项目。

---

*数据来源：GitHub 仓库 (mobile-next/mobile-mcp)，2026 年 9 月访问*

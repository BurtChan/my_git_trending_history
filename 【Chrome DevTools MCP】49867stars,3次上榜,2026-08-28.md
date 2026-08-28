# Chrome DevTools MCP 项目分析

## 项目名称

**Chrome DevTools MCP** — Chrome DevTools 团队官方推出的 MCP 服务器，让 AI 编码助手能够控制并检查真实的 Chrome 浏览器

- **GitHub**: [ChromeDevTools/chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp)
- **许可证**: Apache License 2.0

---

## 项目概述

Chrome DevTools MCP 是由 Google Chrome DevTools 团队官方开源的 Model Context Protocol (MCP) 服务器实现。它充当 AI 编码助手与 Chrome 浏览器之间的桥梁，让 Gemini、Claude、Copilot 等 AI 代理能够直接控制真实的 Chrome 浏览器实例，执行调试、自动化测试和性能分析等操作。项目于 2025 年底进入公开预览阶段，并被 Chrome 官方开发者博客正式发布推荐。

该项目的核心价值在于将开发者日常依赖的 Chrome DevTools 能力（DOM 检查、网络分析、性能追踪、控制台调试等）以标准化 MCP 协议暴露给 AI 代理。AI 编码助手不再局限于分析代码文本，而是可以在真实浏览器中"看到"页面渲染效果、诊断网络错误、追踪性能瓶颈，并自动验证修复是否生效——这代表着 AI 辅助开发从"写代码"迈向"端到端构建和调试网页"的重要一步。

项目底层基于 Puppeteer 实现 Chrome 自动化，通过 Chrome DevTools Protocol (CDP) 与浏览器通信，提供包括输入自动化（点击、拖拽、填写表单）、页面导航、网络请求监控、JavaScript 执行、性能追踪、Lighthouse 审计、内存快照等 20+ 工具。支持与 Claude Code、VS Code Copilot、Cursor、Gemini CLI、JetBrains AI、Windsurf、Warp 等 20 余种主流 AI 编码客户端集成。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| click / drag / hover | 模拟点击、拖拽、悬停等页面交互操作 |
| fill / fill_form | 在输入框中填写文本或选择选项 |
| type_text / press_key | 输入文本或按键组合 |
| upload_file | 通过元素上传文件 |
| navigate_page / navigate_page_history | 页面导航与历史操作 |
| new_page / close_page / list_pages / select_page | 标签页管理 |
| wait_for | 等待指定文本出现在页面上 |
| take_screenshot | 截取页面或元素截图 |
| take_snapshot | 基于 a11y 树获取页面文本快照 |
| evaluate_script | 在页面中执行 JavaScript 函数 |
| list_console_messages / get_console_message | 获取控制台消息 |
| list_network_requests / get_network_request | 监控网络请求 |
| performance_start_trace / performance_stop_trace | 性能追踪录制 |
| performance_analyze_insight | 分析具体性能洞察 |
| take_memory_snapshot | 捕获堆内存快照，检测内存泄漏 |
| lighthouse_audit | 执行 Lighthouse 审计获取评分报告 |
| emulate | 模拟暗黑模式、CPU 节流、地理位置、网络条件 |
| resize_page | 调整页面窗口尺寸 |
| handle_dialog | 处理浏览器对话框 |

---

## 技术栈

| 类别 | 技术 |
|------|------|
| 主要语言 | TypeScript |
| 运行时 | Node.js (≥ v20.19) |
| 浏览器自动化 | Puppeteer / Chrome DevTools Protocol (CDP) |
| 通信协议 | Model Context Protocol (MCP)，通过 stdio 传输 |
| 包管理 | npm，支持 npx 一键运行 |
| 目标浏览器 | Google Chrome / Chrome for Testing |

---

## 项目亮点

1. **官方出品，权威可靠**：由 Google Chrome DevTools 团队直接维护，是 Chrome 官方认可的 MCP 集成方案，更新活跃，代码质量有保障。
2. **工具链极其丰富**：提供 20+ 精心设计的调试工具，覆盖输入自动化、网络分析、性能追踪、内存检测、Lighthouse 审计等全方位 DevTools 能力。
3. **生态兼容性极强**：支持 Claude Code、VS Code Copilot、Cursor、Gemini CLI、JetBrains AI、Windsurf 等 20+ 主流 AI 编码客户端，一行配置即可接入。
4. **零门槛快速上手**：通过 `npx chrome-devtools-mcp@latest` 一行命令即可启动，支持 headless 模式、自动连接浏览器实例、slim 模式等灵活配置。

---

## 应用场景

1. **AI 辅助 Web 调试**：开发者用自然语言描述问题（如"localhost:8080 的图片加载不出来"），AI 代理自动检查网络请求和控制台错误并给出修复方案。
2. **自动化性能优化**：AI 代理启动性能追踪，分析 LCP 等核心指标，自动定位性能瓶颈并实施优化代码修改后验证效果。
3. **端到端测试与表单验证**：AI 代理自动填写表单、点击提交、等待响应，验证用户交互流程是否正常工作。
4. **CSS/布局问题诊断**：AI 通过截图和 DOM 快照分析页面布局异常，自动检测并修复样式问题。

---

## Star 数据

| 指标 | 数据 |
|------|------|
| 总 Stars | ⭐ 49,867 |
| 总 Forks | 🍴 3,498 |
| 主要语言 | TypeScript |
| 许可证 | Apache License 2.0 |
| 最新版本 | v0.21.0 |
| 贡献者 | 75+ |

---

## 📋 更新记录

### 更新 1 — 2026 年 7 月 31 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：Chrome DevTools MCP 持续快速发展，Star 数从 35,500 增长至约 48,251（+12,751）。v1.6.0 版本（2026 年 7 月 14 日）引入了多项重要功能：实验性 TOON（结构化内容输出）支持、堆快照关闭工具、扩展 Service Worker 日志、内存调试工具、URL 模式过滤（allowedUrlPattern/blockedUrlPattern）以及多第三方开发者工具供应商处理。项目由 Google Chrome DevTools 团队官方维护，将 Chrome DevTools 完整能力通过 MCP 协议暴露给 AI 编程 Agent，已成为前端开发领域 AI Agent 工具链的核心组件。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 35,500 | 48,251 | +12,751 |
| 总 Forks | 3,269 | 3,269 | — |

**核心变化概要**：
- Star 数增长超 12,700，逼近 5 万大关
- v1.6.0 重大更新（2026 年 7 月 14 日），新增内存调试、TOON 输出等高级功能
- 支持多第三方开发者工具供应商，扩展兼容性
- Google 官方持续投入维护，已成为 AI Agent 前端开发的标准 MCP 服务器

---

### 更新 2 — 2026 年 8 月 28 日（再次登上 Trending）

**更新原因**：项目再次登上 GitHub Trending 榜单，时隔近一个月重返

**最新 Star 数据**：

| 总 Stars | 48,251 | 49,867 | +1,616 |
| 总 Forks | 3,269 | 3,498 | +229 |

**核心变化概要**：
- Star 数 48,251 → 49,867（+1,616），逼近 5 万大关，第 3 次登上 Trending
- 8 月 28 日当天仍有推送，Google 官方团队持续高强度维护
- 与 Claude Code、Copilot、Cursor 等 20+ AI 客户端的集成生态进一步巩固


---

## 总结

**Chrome DevTools MCP** 是 Google Chrome DevTools 团队官方推出的 MCP 服务器，通过标准化协议将 Chrome 浏览器完整的调试、自动化和性能分析能力赋予 AI 编码助手。项目以 TypeScript 编写，基于 Puppeteer 和 CDP 实现，提供 20+ 精心设计的工具（涵盖页面交互、网络监控、性能追踪、内存分析、Lighthouse 审计等），并与 Claude Code、Copilot、Cursor、Gemini 等 20+ 主流 AI 客户端无缝集成。凭借官方团队背书、活跃的社区和极低的上手门槛（一行 npx 命令即可启动），该项目已成为 AI 辅助 Web 开发领域最受欢迎的基础设施之一，拥有超过 35,000 Stars 和 2,200 Forks，代表了 AI 编码从"写代码"走向"端到端构建和调试真实网页"的重要趋势。

---

*数据来源：GitHub 仓库 (ChromeDevTools/chrome-devtools-mcp)，2026 年 7 月访问*
*首次分析：2026 年 7 月 | 最近更新：2026 年 8 月 28 日*

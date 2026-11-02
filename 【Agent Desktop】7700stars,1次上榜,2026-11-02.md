# Scrapling 爬虫框架 项目分析

## 项目名称
**Scrapling** — 反检测优先的新一代 Python 网页爬取框架
- **GitHub**: [D4Vinci/Scrapling](https://github.com/D4Vinci/Scrapling)
- **许可证**: BSD-3-Clause

---

## 项目概述
Scrapling 是一个为「被反爬系统围猎」的场景而生的 Python 网页爬取库。它把三件事做成了一个统一框架：高性能 HTML 解析、自适应元素定位、以及带隐身能力的抓取通道（普通 HTTP、动态浏览器、隐身浏览器三档）。

项目最大的差异化在于「自适应元素重定位（Adaptive Matching）」：页面结构变化后，Scrapling 仍能根据元素文本、位置、属性等相似度特征找回原目标，大幅降低爬虫因网站改版而失效的维护成本。配合内置的 Cloudflare/Turnstile 求解、TLS 指纹伪装（curl_cffi）与 Playwright 隐身浏览器，Scrapling 成为 Python 爬虫领域「反检测 + 自愈定位」双能力标杆。

2026 年 11 月的 v0.5 大版本将 MCP server、CAPTCHA 求解与 AI 工具链全面升级，使其同时成为 AI Agent 网页数据采集的热门底座。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 自适应元素定位 | 页面结构变化后按相似度自动重定位目标元素（find/find_all 带 adaptive=True） |
| 三档抓取通道 | Fetcher（快速 HTTP）/ DynamicFetcher（Playwright）/ StealthyFetcher（隐身浏览器+指纹伪装） |
| Cloudflare 求解 | 内置 Challenge Solver，v0.5 改进延迟组件检测与有界重试 |
| MCP Server | AI 代理可经 MCP 协议调用完整爬取能力，v0.5 几乎可解决任意 CAPTCHA |
| 会话状态持久化 | save_state()/load_state() 保存 cookies/localStorage/IndexedDB，跨运行复用登录态 |
| 网络录制 | record_requests=True 记录页面全部已完成请求，供离线检查响应 |
| Spider 框架 | CrawlSpider/ContentSpider 支持 BFS/DFS 策略、检查点续爬、sitemap 支持 |
| RAG 输出 | 一行输出 RAG-ready Markdown（SiteToMarkdownSpider），面向 AI 数据管线 |
| Shadow DOM | pierce_shadow=True 提取开放 Shadow DOM，支持 CLI --pierce-shadow |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | Python |
| HTTP 引擎 | curl_cffi（TLS 指纹伪装） |
| 浏览器自动化 | Playwright（Camoufox 隐身分支） |
| 解析引擎 | lxml + 自研自适应匹配 |
| AI 集成 | MCP 协议 server |
| 安装 | pip install scrapling[all] |

---

## 项目亮点

### 自适应重定位解决「爬虫脆弱性」
传统选择器在网站改版后立即失效。Scrapling 记录元素的文本、属性、树位置等特征，结构变化后按相似度评分重新锁定目标，把「维护爬虫」的成本压缩一个量级。

### 反检测能力产品化
不把隐身当作附加选项，而是默认能力：TLS/JA3 指纹、浏览器指纹、字体/Canvas 伪装与 Cloudflare 求解内置于主流程，StealthyFetcher 开箱即对抗主流反爬系统。

### 面向 AI 时代的数据采集
MCP server 让 Claude 等 Agent 直接调度爬取；RAG-ready Markdown 一行输出；十语言文档与活跃社区使其成为 LLM 数据管线高频选型。

---

## 应用场景

### 生产级长期爬虫
电商价格监控、内容聚合等需要数月稳定运行的项目，自适应定位显著降低网站改版导致的失效频率。

### AI 数据管线
为大模型训练/RAG 采集语料：站点转 Markdown spider + MCP 集成，从「写爬虫」变成「配任务」。

### 对抗强反爬目标
Cloudflare、PerimeterX 等防护站点，利用内置求解器与隐身浏览器通道获取数据。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 92,055 |
| 总 Forks | 9,710 |
| 今日新增 Stars | 892 |
| Open Issues | 18 |
| 语言 | Python |
| 许可证 | BSD-3-Clause |

---

## 总结
Scrapling 用「自适应元素定位 + 默认隐身 + AI 工具链」三板斧重新定义了 Python 爬虫框架的完成度，v0.5 之后既是反爬对抗的工程标杆，也是 AI Agent 采集数据的默认底座之一。

---

*数据来源：GitHub 仓库 (D4Vinci/Scrapling)，2026 年 11 月访问*
*首次分析：2026 年 5 月 | 最近更新：2026 年 11 月 2 日*

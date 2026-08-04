# CloakBrowser 项目分析

## 项目名称

**CloakBrowser** — 基于 C++ 源码级补丁的隐身 Chromium 浏览器，完美绕过所有主流机器人检测

- **GitHub**: [CloakHQ/CloakBrowser](https://github.com/CloakHQ/CloakBrowser)
- **许可证**: 自定义许可证（Chromium 二进制文件遵循 Chromium 许可证）

---

## 项目概述

CloakBrowser 是一款隐身 Chromium 浏览器，能够通过所有主流机器人检测测试。它是 Playwright 和 Puppeteer 的直接替代品，提供了一个经过 C++ 源码级别修改的真实 Chromium 二进制文件——不是通过 JavaScript 注入，不是通过配置标志，而是通过编译进二进制文件的实际源码补丁。

项目之所以诞生，是因为反机器人检测系统（Cloudflare、reCAPTCHA、FingerprintJS 等）在检测自动化浏览器方面变得越来越复杂。现有的解决方案如 `playwright-stealth`、`undetected-chromedriver` 和 `Camoufox` 依赖于运行时 JavaScript 注入或配置补丁，这些方案经常在浏览器更新时失效，且无法达到足够高的检测分数。CloakBrowser 采用了一种根本不同的方法——直接修补 Chromium 的 C++ 源代码，生成一个对反机器人系统来说与普通浏览器无法区分的二进制文件。

当前版本基于 Chromium 145（v0.3.0），在 reCAPTCHA v3 中获得 0.9 的高分（服务端验证），通过 Cloudflare Turnstile 和 FingerprintJS 的所有 30 项检测测试，是目前开源领域检测分数最高的隐身浏览器方案。

---

## 核心功能

### 1. 源码级隐身
对 Chromium 二进制文件进行 25-49 个 C++ 源码级补丁，涵盖 Canvas、WebGL、音频指纹等各个维度，从底层消除自动化痕迹。

### 2. 全面的检测通过
通过 30/30 项机器人检测测试，包括：
- reCAPTCHA v3（分数：0.9，服务端验证）
- Cloudflare Turnstile（非交互测试自动通过）
- FingerprintJS（机器人检测：通过）
- BrowserScan（评级：NORMAL，4/4）
- ShieldSquare

### 3. 无感集成
作为 Playwright 和 Puppeteer 的直接替代品，只需更换 import 即可使用，无需学习新的 API：
```python
from cloakbrowser import playwright
with playwright() as p:
    browser = p.chromium.launch()
    page = browser.new_page()
    page.goto("https://protected-site.com")
```

### 4. 人类行为模拟
`humanize=True` 标志使所有鼠标、键盘和滚动交互与真实用户无法区分，提供 `default` 和 `careful` 两种交互速度预设。

### 5. AI 代理兼容
开箱即用支持 AI 浏览器代理（browser-use、agent-browser、Claude Computer Use、OpenAI Operator），提供 MCP（Model Context Protocol）服务器用于 AI 代理集成。

### 6. CDP 远程访问
支持 Chrome DevTools Protocol 的远程访问模式，方便分布式部署。

### 7. 指纹管理
支持自动生成随机指纹或确定性身份，可配置存储配额、平台伪装、HTTP/2 控制等。

### 8. 多平台支持
支持 Linux x64、macOS（Intel 和 Apple Silicon）、Windows（即将推出），提供 Docker 镜像。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要语言** | Python（SDK）、JavaScript/TypeScript（Node.js 包）、C++（Chromium 补丁） |
| **浏览器引擎** | Chromium 145（自定义 Fork 并补丁） |
| **自动化 API** | Playwright（主要）、Puppeteer（次要） |
| **AI 代理集成** | MCP（Model Context Protocol）、CDP Server |
| **容器化** | Docker、Docker Compose |
| **代理支持** | HTTP、SOCKS5 |
| **安装方式** | `pip install cloakbrowser` / `npm install cloakbrowser` |

---

## 项目亮点

### 唯一的 C++ 源码级 Chromium 隐身方案
与 playwright-stealth（JS 注入）、undetected-chromedriver（配置补丁）、Camoufox（Firefox C++ 补丁）不同，CloakBrowser 是目前唯一一个在 Chromium 引擎上进行 C++ 源码级别修改的开源方案，具有最高的兼容性和检测通过率。

### 零学习成本
完全兼容 Playwright/Puppeteer API，只需替换一行 import 即可从标准浏览器切换到隐身浏览器，无需修改任何业务代码。

### 免费的 Multilogin 替代品
Multilogin、GoLogin、AdsPower 等商业反检测浏览器月费 $49-$299，CloakBrowser 以免费开源的方式提供同等甚至更优的检测绕过能力。

### AI 代理原生支持
专为 AI 代理场景设计，提供 MCP 服务器和人类行为模拟，使 Claude Computer Use、OpenAI Operator 等 AI 代理能够自然地与受保护网站交互。

---

## 应用场景

### Web 数据采集
采集受反机器人保护网站的数据而不被封锁，支持 Cloudflare、reCAPTCHA 等主流防护。

### AI 代理网页交互
使 AI 代理能够与需要人类行为特征的 Web 服务进行交互，突破自动化检测限制。

### 自动化测试
在反机器人保护背后测试应用程序，模拟真实用户行为进行端到端测试。

### 多账号管理
通过配套的 CloakBrowser-Manager（Web GUI）管理多个浏览器配置文件，支持不同指纹身份。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | ~2,500 |
| **总 Forks** | ~205 |
| **许可证** | 自定义（Chromium 许可证） |
| **主要语言** | Python / C++ |
| **当前版本** | v0.3.0（Chromium 145） |

---

## 总结

CloakBrowser 是一款基于 C++ 源码级补丁的隐身 Chromium 浏览器，通过 30/30 项机器人检测测试，reCAPTCHA v3 分数高达 0.9。它作为 Playwright/Puppeteer 的直接替代品，零学习成本即可使用，同时提供 MCP 服务器和人类行为模拟功能，是 AI 代理网页交互和 Web 数据采集领域的开源利器，相当于免费版的 Multilogin/GoLogin。

---

*数据来源：GitHub 仓库 (CloakHQ/CloakBrowser)、cloakbrowser.dev（2026 年 5 月访问）*

# Stremio Web 项目分析

## 项目名称
**Stremio Web** — Stremio 官方 Web 端：「Freedom to Stream」现代媒体中心的一站式流媒体 UI
- **GitHub**: [Stremio/stremio-web](https://github.com/Stremio/stremio-web)
- **许可证**: GPL-2.0

---

## 项目概述
Stremio 是老牌开源媒体中心（Smart Code OOD 出品，始于 2015 年前后），理念是「一个应用聚合所有视频内容」：电影、剧集、频道、直播通过官方与社区 addon 生态接入，库与观看进度跨设备云同步。stremio-web 是其官方 Web 界面仓库，也是 web.stremio.com 线上产品与可安装 PWA 的源码，与桌面端共享同一套 UI 架构。

技术上最有意思的一点是它的架构分层：这个仓库只是 React「渲染层」，真正的状态机与业务大脑在 stremio-core——一个用 Rust 编写、编译为 WebAssembly 并跑在 Web Worker 里的引擎，UI 与 core 之间通过消息通信。播放则交给 stremio-video 播放抽象层，按环境自动选择播放器实现。这种「Rust 核心 + WASM + React 壳」的架构在开源前端项目中相当超前。项目有 6,762 次提交、50+ 社区语言翻译，是影音发烧友圈（尤其搭配自建媒体服务器人群）的常青工具，本次登上 Trending 与其 addon 生态的持续活跃有关。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| Addon 内容聚合 | 电影/剧集/频道目录由社区 addon 生态提供，按需装卸 |
| 跨设备同步 | 媒体库与「继续观看」随 Stremio 账号全端同步 |
| 投屏 | Chromecast 大屏播放 |
| 字幕 | addon 提供 + 本地字幕，样式可自定义 |
| 键盘优先播放器 | 全键盘播放控制 |
| 50+ 语言 | 社区翻译（stremio-translations） |
| 可安装 PWA | 作为独立应用安装运行 |
| Docker 支持 | 仓库自带 Dockerfile，可自托管 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| UI | React + webpack + TypeScript |
| 核心引擎 | stremio-core（Rust → WebAssembly，Web Worker 运行） |
| 播放 | stremio-video 播放器抽象层 |
| 构建 | Node.js 22+ / pnpm 11+ |
| 部署 | Docker / GitHub Pages（development 分支自动部署） |

---

## 项目亮点

### Rust → WASM 的核心/UI 分离架构
全部业务状态（addon 协议、库、同步）在 Rust 写成的 stremio-core 中计算，Web、桌面、移动端各平台复用同一个 Rust 核心，UI 只做渲染——彻底消灭多端逻辑不一致，这是多数跨平台媒体应用梦寐以求的架构。

### addon 协议构成的开放式内容生态
内容目录、元数据、字幕、流源全部通过公开 addon 协议接入，社区 SDK（stremio-addon-sdk）让任何人都能用 Node.js 写一个内容源，形成类似浏览器扩展的开放生态，是 Stremio 十年不衰的根本。

### 老牌项目的现代工程化改造样本
6,762 次提交的十年老库完成了 webpack/ESLint flat config/PWA/Docker 全面现代化，development 分支持续自动部署到 GitHub Pages 供尝鲜，展示了长周期开源产品如何保持工程活力。

---

## 应用场景

### 个人/家庭媒体中心
聚合多来源视频内容、统一库管理与追剧进度，配合 Chromecast 覆盖客厅大屏场景。

### 自托管流媒体前端
Docker 自部署 + 账号同步，在自有设备上搭建可控的家庭流媒体入口，数据不经第三方前端。

### 跨端架构学习参考
对想实践「Rust core + WASM + 各端 UI」架构的团队，stremio-web 与 stremio-core 的通信边界划分是可直接研读的生产级代码。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ 总 Stars | 13,381 |
| 🍴 总 Forks | 1,541 |
| 📈 今日新增 | 121 stars |
| 许可证 | GPL-2.0 |
| 主要语言 | JavaScript/TypeScript |

---

## 总结
Stremio Web 是开源媒体中心赛道的常青树官方 Web 端：addon 开放生态 + Rust/WASM 核心/UI 分离的前瞻架构，对影音发烧友是实用工具，对前端与跨端架构工程师则是一份稀有的生产级参考实现。

---

*数据来源：GitHub 仓库 (Stremio/stremio-web)，2026 年 9 月访问*

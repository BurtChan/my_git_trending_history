# God's Eye View 项目分析

## 项目名称
**God's Eye View** — 浏览器里的间谍卫星模拟器——只不过数据是真实的：基于实景三维地球的开源空间情报实时可视化平台
- **GitHub**: [bilawalsidhu/gods-eye-view](https://github.com/bilawalsidhu/gods-eye-view)
- **许可证**: 自定义（NOASSERTION，仓库含 LICENSE 文件）

---

## 项目概述

God's Eye View（曾用名 WorldView）出身于 YouTube 上累计播放量超 500 万的「God's Eye View」病毒式传播系列视频——作者 Bilawal Sidhu 把电影《爱国者游戏》里那种"上帝视角卫星监控"搬进了浏览器。2026 年 6 月创建后仅两个月即登上 GitHub Trending，首日新增近 2,000 Stars。

项目的核心卖点一句话可以概括：**一个零成本的 GEOINT/OSINT（地理空间情报/开源情报）沙盘**。它在 Google 实景三维瓦片（Photorealistic 3D Tiles）构建的地球表面上，实时叠加全球飞机、船舶、卫星、地震、军事航班、城市摄像头、无线电电台等十余类公开数据层，再配上一个由 OpenAI Realtime API 驱动的免手持语音智能体——你可以直接对它说"带我去 LAX，选中最近的在空航班"。

技术选型上极为克制：无框架、Vanilla JavaScript + CesiumJS + Vite，源码结构清晰（每个数据层一个模块），明确以"可读、可魔改"为设计目标。作者定位它是"近年空间智能工具浪潮的起点客户端"——不是产品，是一块画布。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| 实景三维地球 | Google Photorealistic 3D Tiles + CesiumJS，支持 Google 3D / Bing / OSM 地图栈切换 |
| 多层实时数据 | 全球飞机（OpenSky/adsb.lol）、船舶（AISStream AIS）、卫星（CelesTrak）、地震（USGS）、火灾（FIRMS）、交通（TomTom）、城市 CCTV、Radio Broadcast、共享单车（GBFS）、发射日程（Launch Library 2） |
| 军事航班层 | ADS-B 军用航空流量以琥珀色高亮显示 |
| 语音智能体 | OpenAI Realtime API，28 个语音工具、4 类任务，免手持指挥视角切换与目标选取 |
| AI HUD 情报摘要 | 随视角移动实时刷新的五词"情报式"场景读出 |
| 电影化场景导演 | scenes/ 内置运镜导演模块，可编排电影感飞行视角 |
| 建模视图兜底 | 无实时画面处用清晰标注的建模视图替代，明确区分真实与模拟 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 前端 | Vanilla JavaScript（无框架）+ Vite |
| 三维渲染 | CesiumJS + Google Photorealistic 3D Tiles |
| 语音/AI | OpenAI Realtime API |
| 数据源 | OpenSky、adsb.lol、AISStream、CelesTrak、USGS、FIRMS、TomTom、GBFS、Launch Library 2 等公开 API |
| 安全 | 服务端密钥代理（OpenAI/AISStream/OpenSky OAuth 等仅 localhost 暴露 Google Maps 与 Cesium ion 凭证）、限流、$5 会话费用上限 |

---

## 项目亮点

### 公开数据的情报级融合
把十余个分散的公开实时数据源统一到一块三维地球上，配上军航高亮、AI HUD 摘要，"用公开数据还原间谍卫星"的叙事极具传播力——这正是 5M+ 播放视频反向引流 Star 的核心飞轮。

### 无框架的"可魔改"工程哲学
拒绝 React/Vue，纯 Vanilla JS + 每层数据一个模块的目录结构，加上本地优先的密钥代理与威胁模型文档（SECURITY.md），让二次开发门槛降到最低——作者明确欢迎"加一个城市包、一个数据源、一个语音工具"。

### 分级成本设计
大多数数据层 $0 无需注册；可选层（AISStream、FIRMS、TomTom）提供免费开发者额度；仅 OpenAI 语音按量计费且内置 $2 预警 + $5 会话硬上限——"不跟销售团队谈话也能体验 GEOINT"。

---

## 应用场景

### OSINT/地理空间情报学习
安全研究者和爱好者可以在真实数据上练习多源情报融合、目标追踪与态势感知，是 GEOINT 教学与演练的低成本沙盘。

### 空间智能应用原型开发
想验证"实时数据 + 三维地球 + 语音交互"产品形态的团队，可以直接 fork 作为起点客户端，替换或叠加自有数据层。

### 内容创作与影视级运镜
电影化场景导演模块 + 实景地球，适合制作地图类视频内容——项目本身就源自 YouTube 创作者，创作基因明显。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 7,709 |
| 总 Forks | 1,770 |
| 今日新增 | +1,984 |
| 创建时间 | 2026-06-22 |
| 语言 | JavaScript |
| Open Issues | 80 |

---

## 总结

God's Eye View 用"电影级上帝视角 + 全公开真实数据"的反差叙事，把 GEOINT 从企业合同制的神秘领域拉到任何人的浏览器里；无框架 Vanilla JS 的克制工程与分级成本设计让它既是可传播的演示，也是可严肃魔改的空间智能开发底座。

---

*数据来源：GitHub 仓库 (bilawalsidhu/gods-eye-view)，2026 年 8 月访问*

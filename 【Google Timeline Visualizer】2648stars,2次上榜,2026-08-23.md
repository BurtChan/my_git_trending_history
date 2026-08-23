# Google Timeline Visualizer 项目分析

## 项目名称
**Google Timeline Visualizer** — 把 Google 位置历史（Timeline）数据变成动画旅行视频
- **GitHub**: [mahlernim/google-timeline-visualizer](https://github.com/mahlernim/google-timeline-visualizer)
- **许可证**: MIT

---

## 项目概述
Google Timeline Visualizer 是一个把 Google 地图"时间线"（原"位置历史"）导出的 JSON 数据转化为动画旅行视频的工具。用户在手机上导出 `Timeline.json`，选择日期范围后，应用会在地图上以动画形式重现行程轨迹，并生成可供观看分享的 MP4 视频——类似"我的年度旅行回顾"。

项目 2025 年 12 月创建，2026 年 8 月首次登上 GitHub Trending（单日 +1,053 stars）。项目由个人开发者（mahlernim，Ahn Lab）维护，提供 Android 原生应用、iOS 网页应用和桌面 Python 脚本三种形态，并附韩语/日语 README，在韩日社区传播较广。

---

## 核心功能
| 功能 | 描述 |
|------|------|
| 动画视频生成 | 选择月份区间或精确日期，地图摄像机跟随行程移动，输出 MP4 |
| 多平台 | Android 原生 App（Kotlin）、iPhone Safari 网页版（免安装、本地渲染）、桌面 Python 版 |
| 摄像机控制 | steady 等多种镜头运动模式、长途飞行沿大圆航线平滑插值 |
| GPS 离群点过滤 | 默认保守过滤孤立异常坐标，可关闭 |
| Timeline 恢复指引 | 附带恢复丢失 Google 地图时间线的教程文档 |
| 多语言 | 英/韩/日/简中/繁中/西/法/德/巴葡 9 种语言 |

---

## 技术栈
| 组件 | 技术 |
|------|------|
| Android App | Kotlin + Gradle，要求 Android 8.0+ |
| iPhone | Safari 16.4+ Web 应用（H.264 编码，本地渲染不上传） |
| 桌面版 | Python 3.9+ + FFmpeg |
| 底图 | OpenStreetMap 数据 + CARTO 瓦片服务 |
| 测试 | 独立 tests/test-fixtures 目录，CI validate workflow |

---

## 项目亮点
### 隐私优先设计
无 Google 登录、无定位权限、无分析埋点、无宽存储权限；Timeline 文件从不上传，视频渲染全程在设备本地完成，仅底图瓦片请求会暴露查看区域。

### 支持 Google 新旧导出格式
同时支持 Android/iOS 直挂数组格式、旧版 `semanticSegments` 格式、raw location 回退，以及 E7/度/`geo:` 等多种坐标表示，跨国际日期变更线的行程也能正确处理。

### "Google 关停位置历史"背景下的刚需
Google 已将 Timeline 改为端侧存储并逐步收紧导出，大量用户趁机导出历史数据留念，这类可视化工具正好承接了这波需求，是本次登上 Trending 的主要驱动。

---

## 应用场景
### 个人年度旅行回顾
把一年的出差/旅行轨迹做成动画视频，年底分享社交平台。
### 情侣/家庭共同轨迹可视化
两人合并行程，重走旅行路的动画纪念。
### 隐私敏感用户的本地处理
不愿把位置数据交给第三方云服务的用户，全程离线生成视频。

---

## Star 数据
| 指标 | 数值 |
|------|------|
| 总 Stars | 2,648 |
| 总 Forks | 311 |
| 今日新增 | +441 |
| 创建时间 | 2025-12-16 |

---

## 📋 更新记录

### 更新 1 — 2026年8月23日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：Google Timeline Visualizer 连续第三天上榜（8/21 首榜、8/22、8/23），Star 从 2,220 增长至 2,648，单日再增 441。受益于 Google 位置历史（Timeline）政策变动引发的用户数据导出潮，这款「本地渲染 + 隐私优先」的旅行动画生成工具持续承接流量；Fork 数也从 254 涨至 311，说明不少用户开始自行定制渲染样式。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 2,220 | 2,648 | +428 |
| 总 Forks | 254 | 311 | +57 |

**核心变化概要**：
- Star 增长 +428，连续 3 天上榜（8/21–8/23）
- Google Timeline 政策变动红利仍在持续释放
- Fork 增速显著（+57），社区定制需求升温


---

## 总结
一个踩中"Google Timeline 政策变动"时间窗口的隐私优先型小工具，用本地渲染 + 多平台覆盖把位置历史变成可分享的旅行动画，工程完成度和隐私细节都超出同类周末项目水准。

---

*数据来源：GitHub 仓库 (mahlernim/google-timeline-visualizer)，2026 年 8 月访问*
*首次分析：2026 年 8 月 | 最近更新：2026 年 8 月*

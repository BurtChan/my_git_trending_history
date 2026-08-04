# YTLite 项目分析

## 项目名称

**YTLite** — iOS 上 YouTube 的灵活增强工具

- **GitHub**: [dayanch96/YTLite](https://github.com/dayanch96/YTLite)
- **许可证**: 无（开源）

---

## 项目概述

YTLite 是一款专为 iOS 平台设计的 YouTube 增强工具，通过越狱或侧载方式注入 YouTube 应用，提供超过 100 项自定义选项。它允许用户突破 YouTube 官方应用的限制，实现视频下载、界面定制、播放器增强等功能，是 iOS 平台上最受欢迎的 YouTube 增强方案之一。

项目主要由 Logos（Theos 框架的预处理器语言）和 Objective-C 编写，以 Theos 插件的形式运行。YTLite 整合了多个知名的 YouTube 增强插件功能，包括 YouPiP（画中画）、YTUHD（超高清）、Return YouTube Dislikes（恢复踩数）、YouQuality（画质选择）和 DontEatMyContent（防止裁剪），实现了"一装全有"的便捷体验。

YTLite 支持最新的 YouTube 版本（已确认兼容 20.42.3），持续更新维护，社区活跃。项目提供了完善的设置管理系统，支持配置的导出、导入和恢复。

---

## 核心功能

### 1. 视频与内容下载
支持下载视频、音频、缩略图、帖子（Community Posts）和用户头像，可自定义下载质量和格式。

### 2. 界面深度定制
- 移除 Feed 中的各类推荐元素（广告、推广、浮窗等）
- 自定义 Tab 栏顺序
- OLED 深色模式
- Shorts 专属模式

### 3. 播放器增强
- 手势控制（音量、亮度、快进快退）
- 默认画质设置
- 首选音轨选择
- 画中画（PiP）支持

### 4. SponsorBlock 集成
内置 SponsorBlock 功能，自动跳过视频中的赞助商片段、片头片尾等非内容部分。

### 5. 信息复制
一键复制视频信息、评论内容和帖子信息，方便分享和引用。

### 6. 设置管理
支持设置的保存、加载和恢复，可清除缓存，配置迁移便捷。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Logos（75.5%） |
| **底层框架** | Objective-C（24.2%） |
| **构建工具** | Makefile（0.3%） |
| **注入框架** | Theos |
| **平台** | iOS（越狱/侧载） |
| **许可证** | 无 |

---

## 项目亮点

### 百项自定义选项
超过 100 项可配置选项，几乎涵盖了 YouTube 应用的方方面面，从界面布局到播放行为都可精细调整。

### 多插件合一
整合了 YouPiP、YTUHD、Return YouTube Dislikes、YouQuality、DontEatMyContent 等多个独立插件的核心功能，一次安装即可获得完整的增强体验。

### 持续更新适配
紧跟 YouTube 版本更新，确保每次 YouTube 升级后仍能正常使用，兼容性维护到位。

### 活跃的社区生态
拥有活跃的开发者社区，4.6k+ Stars 和 20k+ Forks，社区贡献活跃，问题响应及时。

---

## 应用场景

### 无广告观看体验
移除 YouTube 应用中的各类广告和推广内容，获得纯净的观看体验。

### 离线视频观看
下载视频和音频到本地，在无网络环境下观看 YouTube 内容。

### 高级播放控制
设置默认画质、音轨偏好，使用手势控制播放，提升日常使用效率。

### OLED 屏幕优化
启用 OLED 深色模式，在 iPhone 等 OLED 设备上获得更纯粹的黑色显示效果和省电体验。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 4,684 |
| **总 Forks** | 20,106 |
| **今日新增 Stars** | ~43 |
| **许可证** | 无 |
| **主要语言** | Logos / Objective-C |

---

## 总结

YTLite 是 iOS 平台上功能最全面的 YouTube 增强工具，4.6k+ Stars。它以 Logos 和 Objective-C 编写，通过 Theos 框架注入 YouTube 应用，提供超过 100 项自定义选项，涵盖视频下载、界面定制、播放器增强、SponsorBlock 等功能。项目整合了多个知名 YouTube 增强插件，一次安装即可获得完整的增强体验，是 iOS 用户优化 YouTube 使用体验的首选方案。

---

*数据来源：GitHub 仓库 (dayanch96/YTLite)，2026 年 4 月访问*

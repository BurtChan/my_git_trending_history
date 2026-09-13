# Cool Retro Term 项目分析

## 项目名称
**Cool Retro Term** — 模拟老式阴极射线管（CRT）显示器的养眼终端模拟器
- **GitHub**: [Swordfish90/cool-retro-term](https://github.com/Swordfish90/cool-retro-term)
- **许可证**: GPL-3.0（仓库内含 gpl-2.0.txt / gpl-3.0.txt，GitHub 识别为 GPL）

---

## 项目概述

Cool Retro Term 是一个高仿老式阴极射线管显示器观感的终端模拟器，主打 eye-candy：荧光绿/琥珀色辉光、扫描线、屏幕曲率、余晖残留（phosphor glow）、开机闪烁等复古效果一应俱全，同时保持可定制与相对轻量。项目 2013 年创建，是 GitHub 上最著名的「颜值型终端」，时隔多年再次登上 Trending——一个十三年历史的老项目至今仍能靠情怀与视觉冲击力吸引新用户。

技术上它基于 Konsole 的 QML 移植版 qmltermwidget 构建，使用 Qt6，支持 Linux 与 macOS。内置多个经典主题：Default Amber（琥珀单色）、IBM DOS、Default Green（荧光绿）等，通过右键菜单即可调整颜色、字体与效果。安装方面提供 AppImage / dmg 直接下载，也被 Ubuntu、Fedora、Arch 等主流发行版官方收录——`apt install cool-retro-term` 即可拥有。

它的存在证明了「无用之用」：没有生产力增益，却在 Hacker News / Reddit 上常年是「show your terminal」帖的顶流，大量开发者拿它跑 htop、vim、cmatrix 截图，甚至用于影视道具与黑客主题演示。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| CRT 效果 | 辉光、扫描线、曲率、余晖、闪烁、噪点等实时着色器效果 |
| 经典主题 | Default Amber / IBM DOS / Default Green 等预设 |
| 可定制 | 右键菜单调整颜色、字体、效果强度 |
| 跨平台 | Linux（AppImage/发行版包）+ macOS（dmg），要求 Qt6 |
| 完整终端 | 基于 qmltermwidget（Konsole 移植），日常命令行可用 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | C++ / QML |
| 框架 | Qt6 + qmltermwidget（Konsole 的 QML 移植） |
| 单实例 | KDSingleApplication |
| 打包 | AppImage、Snap、dmg、各发行版官方包 |

---

## 项目亮点

### 十三年长青的情怀爆款
2013 年至今仍是终端美学的代名词，26K+ Stars，是「老项目重回 Trending」现象的最佳样本。

### 着色器级 CRT 拟真
不是贴图模拟，而是实时 OpenGL 着色器实现的辉光/扫描线/余晖，观感远超各类 CSS 仿终端网页。

### 零门槛安装
主流发行版官方仓库收录 + AppImage 免编译，一行命令即可体验。

---

## 应用场景

### 复古终端美学
给桌面环境配一台「时光机」终端，跑 cmatrix、htop、vim 截图发圈的标配道具。

### 影视/演示道具
黑客主题短片、复古计算机展览、科技活动现场演示的即时氛围工具。

### 着色器学习样本
QML + GLSL 实现 CRT 效果的完整开源实现，是学习实时后处理效果的入门范例。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 26,122 |
| 总 Forks | 1,014 |
| 今日新增 | +98 |
| 主要语言 | QML/C++ |
| 许可证 | GPL |
| 创建时间 | 2013-11-22 |

---

## 总结

Cool Retro Term 用实时着色器把阴极射线管的辉光与扫描线搬回现代桌面，十三年长青的终端美学图腾——不提升生产力，但持续为全球开发者提供快乐。

---

*数据来源：GitHub 仓库 (Swordfish90/cool-retro-term)，2026 年 9 月访问*

# Lighthouse 项目分析

## 项目名称

**Lighthouse** — Harbour Masters 团队对《Banjo-Kazooie》的开源重制版（Powered by libultraship）

- **GitHub**: [HarbourMasters/Lighthouse](https://github.com/HarbourMasters/Lighthouse)
- **许可证**: CC0-1.0（公共领域贡献）

---

## 项目概述

Lighthouse 是由 Harbour Masters 团队开发的开源项目，旨在将经典 N64 游戏《Banjo-Kazooie》移植到现代平台运行。项目基于 libultraship 引擎构建，拥有超过 1,399 次提交，目前处于积极开发状态。Lighthouse 不包含任何受版权保护的素材，用户需自行提供合法游戏 ROM。

作为经典游戏逆向工程的产物，Lighthouse 代表了游戏保存（Game Preservation）社区的又一重要成果。Harbour Masters 团队此前已成功完成了《Zelda: Ocarina of Time》的 Ship of Harkinian 移植项目，积累了丰富的 N64 游戏重制经验。Lighthouse 延续了这一技术路线，为经典 3D 平台游戏提供了跨平台的现代体验。

项目支持 DirectX 11、OpenGL 和 Metal 三种图形后端，覆盖 Windows、macOS 和 Linux 全平台。除了基本的游戏运行，Lighthouse 还提供了多语言包支持、Romhack 加载、自定义素材替换等高级功能，为社区 MOD 创作和游戏研究提供了便利。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **跨平台运行** | 支持 Windows（DirectX 11）、macOS（Metal）、Linux（OpenGL）三大平台 |
| **ROM 验证** | 内置 SHA-1 校验和验证，支持美版 v1.0/v1.1、日版、PAL 版四种零售版本 |
| **多语言支持** | 以不同区域 ROM 作为语言包，支持英/法/德/日多语言切换 |
| **Romhack 支持** | 通过设置菜单加载修补版 ROM 作为 MOD（仅支持美版 v1.0） |
| **自定义素材** | 支持 .o2r/.otr 格式的自定义素材文件，放置于 mods 目录即可加载 |
| **灵活控制** | 支持键盘映射、标准控制器映射，以及自定义映射配置 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要语言** | C |
| **引擎** | libultraship |
| **图形后端** | DirectX 11 / OpenGL / Metal |
| **许可证** | CC0-1.0 |

---

## 项目亮点

### 经典游戏保存与现代化
Lighthouse 让经典 N64 游戏《Banjo-Kazooie》在现代硬件和操作系统上焕发新生，是游戏保存（Game Preservation）运动的重要实践。

### 三大图形后端全平台覆盖
同时支持 DirectX 11（Windows 默认）、OpenGL（全平台通用）和 Metal（macOS 默认），确保在各平台上都能获得最佳渲染性能。

### 社区驱动的 MOD 生态
通过 Romhack 加载和自定义素材系统，为社区创作者提供了扩展游戏内容的框架，延续了原作的寿命和玩法多样性。

### Harbour Masters 团队技术积累
团队拥有 Ship of Harkinian（《Zelda: OoT》重制）的成功经验，在 N64 逆向工程和现代平台移植领域技术成熟。

---

## 应用场景

### 游戏保存与研究
为游戏研究者和爱好者提供在现代平台上运行和分析经典 N64 游戏的能力，助力游戏历史保存。

### 跨平台游戏体验
让原本只能在 N64 主机上运行的《Banjo-Kazooie》，在 PC、Mac 和 Linux 上流畅运行。

### MOD 创作与分享
基于 Romhack 和自定义素材系统，社区可以创作和分享基于原作的新内容、新关卡。

### 逆向工程学习参考
项目代码是 N64 游戏逆向工程和现代重制的优秀学习案例，涵盖图形渲染、音频处理、输入系统等多个领域。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 172 |
| **总 Forks** | 13 |
| **今日新增 Stars** | ~62 |
| **许可证** | CC0-1.0 |
| **主要语言** | C |
| **创建时间** | 2024 年 11 月 |

---

## 总结

Lighthouse 是 **经典 N64 游戏《Banjo-Kazooie》的开源重制项目**，172 Stars。由经验丰富的 Harbour Masters 团队基于 libultraship 引擎打造，支持三大操作系统和三种图形后端。项目延续了团队在游戏保存和逆向工程领域的优秀传统，为经典游戏在现代平台上运行提供了完整解决方案。

---

*数据来源：GitHub 仓库 (HarbourMasters/Lighthouse)，2026 年 8 月 2 日 访问*

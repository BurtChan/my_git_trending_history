# Spirula Studio 项目分析

## 项目名称
**Spirula Studio** — 跨厂商 3D 高斯泼溅（Gaussian Splatting）训练器：视频 → Splat → Mesh，支持 Vulkan 与 CUDA
- **GitHub**: [harry7557558/spirula-studio](https://github.com/harry7557558/spirula-studio)
- **许可证**: GPL-3.0

---

## 项目概述

Spirula Studio（前身为 spirulae-splat，名字源自深海头足纲软体动物 Spirula——鹦鹉螺的远亲）是一个跨厂商的 3D Gaussian Splatting 桌面训练器，由开发者 harry7557558 几乎独立完成开发与维护。它实现了从普通视频输入到 3D 高斯泼溅场景、再到网格（Mesh）输出的完整管线，与依赖 NVIDIA CUDA 生态的主流方案不同，它同时支持 Vulkan 和 CUDA 两条渲染/计算路径——意味着 AMD、Intel 等 GPU 用户同样能进行高质量的 3DGS 训练。

项目采用 C++/CMake 构建，代码库包含 src（核心训练代码）、viewer（查看器）、tools（工具集）、reference（参考实现）等模块，提供 Windows（build_cuda\spirula.exe）与 Linux（build_cuda/spirula）双平台构建产物。项目还维护着与 Megascapes Library 的合作——由 Spirula Studio 训练的专业级 splat 场景已上架 Megascapes 资产库，并在 SuperSplat 平台开设了专门的软件专页与用户作品集。

以 617 Stars、今日 +86 的成绩首次登上 GitHub Trending，说明 3D 高斯泼溅这一从学术界（SIGGRAPH 2023）走向工业界的技术，正在催生一批面向创作者的桌面工具。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 视频转 Splat | 从普通视频输入训练 3D 高斯泼溅场景 |
| Splat 转 Mesh | 从泼溅场景导出网格模型，打通传统 3D 管线 |
| Vulkan / CUDA 双路径 | 跨 GPU 厂商支持，不锁定 NVIDIA |
| 内置查看器 | viewer 模块提供训练结果实时预览 |
| 双平台构建 | Windows 与 Linux 均有官方构建流程 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心语言 | C++（CMake 构建） |
| 计算/渲染后端 | Vulkan 与 CUDA |
| 形态 | 桌面应用（spirula 可执行文件） |
| 生态 | SuperSplat、Megascapes Library |

---

## 项目亮点

### 跨厂商 GPU 支持
3DGS 训练工具几乎清一色绑定 CUDA（NVIDIA），Spirula Studio 的 Vulkan 路径让 AMD/Intel 显卡用户也能参与高斯泼溅创作，显著拓宽了受众面。

### 完整的创作管线
视频输入 → Splat 训练 → Mesh 导出的一站式覆盖，创作者无需在多个工具间搬运数据。

### 单人维护的高完成度
作者以一己之力维护训练器、查看器、文档与构建系统，且作品已进入专业资产库（Megascapes），质量经受住了商业级检验。

---

## 应用场景

### 实景三维重建
用手机拍摄的视频快速生成可交互的高斯泼溅场景，用于 VR/AR 内容、数字孪生。

### 游戏/影视资产制作
Splat 转 Mesh 能力可将扫描场景导入 Blender、Unity 等传统 DCC 与引擎管线。

### 非 NVIDIA 平台的 3DGS 实验
拥有 AMD/Intel GPU 的研究者与爱好者进行高斯泼溅算法实验的低门槛入口。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 739 |
| **总 Forks** | 56 |
| **今日新增 Stars** | +122 |
| **许可证** | GPL-3.0 |
| **主要语言** | C++ |

## 📋 更新记录

### 更新 1 — 2026 年 9 月 24 日（连续第二日在榜）

**更新原因**：昨日（9 月 23 日）首次分析后连续第二日在榜，Star 单日净增 +122（+19.8%），单日增速接近两成，小体量项目热度快速放大。

**最新动态**：单人开发的高斯泼溅训练器持续高频迭代：v2026.9.13（9 月 13 日发布）从图像/视频的遥测元数据恢复度量尺度与朝向、支持恢复中断的数据集创建任务、为结构从运动添加双目鱼眼 rig 约束、支持从 GoPro .360 视频创建数据集，并修复 EXIF 方向导致的旋转/倒置重建问题；更早的 v2026.9.8 引入 LoMa 特征检测匹配与 EXIF GPS 度量尺度恢复。跨 GPU 厂商（Vulkan/CUDA）、视频到 Splat 到 Mesh 全管线的桌面端方案持续吸引 3D 创作社区关注。

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 617 | 739 | +122 |
| 总 Forks | 50 | 56 | +6 |

- 连续第二日在榜，单日增速 +19.8%，小体量项目热度快速放大
- 1-2 周一个版本的迭代节奏，v2026.9.13 聚焦 SfM 前端与训练质量
- 单人维护 + GPL-3.0 开源，高斯泼溅创作门槛最低的桌面端方案之一

---

## 总结

Spirula Studio 是 3D 高斯泼溅平民化的代表工具：单人开发、跨 GPU 厂商（Vulkan/CUDA）、视频到 Splat 到 Mesh 全管线打通，作品已进入 Megascapes 专业资产库。对创作者而言，它是目前进入高斯泼溅创作门槛最低的桌面端方案之一。

---

*数据来源：GitHub 仓库 (harry7557558/spirula-studio)，2026 年 9 月 24 日访问*
*首次分析：2026 年 9 月 23 日 | 最近更新：2026 年 9 月 24 日*

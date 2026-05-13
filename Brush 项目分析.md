# Brush 项目分析

## 项目名称

**Brush** — 面向所有人的跨平台 3D 重建引擎，基于高斯溅射（Gaussian Splatting）技术

- **GitHub**: [ArthurBrussee/brush](https://github.com/ArthurBrussee/brush)
- **许可证**: Apache License 2.0

---

## 项目概述

Brush 是一款由 Arthur Brussee 开发的开源 3D 重建引擎，核心采用高斯溅射（Gaussian Splatting）技术，旨在将高质量的 3D 重建能力带给所有人。该项目最初源于 Google Research 的 brush_splat 仓库，经过独立迭代发展，已成为一个功能完善、跨平台的 3D 重建工具。

Brush 的最大特色在于其极致的跨平台兼容性——它可以在 macOS、Windows、Linux 桌面端运行，支持 AMD、NVIDIA、Intel 等各种 GPU 厂商，甚至可以在 Android 移动设备和 Web 浏览器（通过 WebGPU）中运行。这意味着用户无需高端 NVIDIA 显卡即可进行 3D 重建工作，大幅降低了使用门槛。

项目底层采用 Rust 语言编写，并集成了 Burn 机器学习框架，实现了从训练到渲染的全流程支持。最新版本（v0.3.0）引入了 MCMC 溅射变体训练方法，在保证高重建质量的同时显著提升了训练速度，并且在 MipNeRF360 基准测试中的 PSNR/SSIM 指标已超越 gsplat。

---

## 核心功能

### 高斯溅射 3D 重建
基于最先进的高斯溅射技术，从 2D 图像集重建高质量 3D 场景。

### MCMC 训练方法
v0.3.0 引入改进的 MCMC 溅射变体，提供更高质量的重建结果。

### 跨平台支持
原生运行于 macOS、Windows、Linux，支持 AMD/NVIDIA/Intel GPU。

### 移动端与 Web 端支持
可在 Android 设备上运行；通过 WebGPU 在浏览器中直接运行（支持 Chrome、Edge）。

### 实时交互训练
训练过程中可以实时与场景交互，动态可视化重建进度。

### 多种数据格式支持
支持 COLMAP 和 Nerfstudio 数据集格式输入。

### Web 查看器
在线加载 .ply 和 .compressed.ply 文件，支持通过 URL 流式传输数据。

### 无依赖二进制
提供免依赖的可执行文件，开箱即用。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要编程语言** | Rust |
| **机器学习框架** | Burn |
| **图形渲染** | WebGPU / wgpu |
| **Web 构建** | wasm-pack / npm |
| **移动端构建** | cargo-ndk (Android NDK) |
| **可视化/调试** | Rerun |
| **数据格式** | COLMAP、Nerfstudio、PLY |
| **许可证** | Apache License 2.0 |

---

## 项目亮点

### 极致跨平台
业界罕见的全平台 3D 重建方案，从桌面到移动端到浏览器全覆盖，且不依赖 CUDA，AMD/Intel GPU 用户也能使用。

### 高性能 Rust 实现
使用 Rust 语言从头构建，兼顾安全性与性能，通过 Burn 框架实现跨后端机器学习推理。

### 浏览器内 3D 重建
借助 WebGPU 技术，用户无需安装任何软件即可在浏览器中完成 3D 重建和查看，提供了在线演示。

### 质量超越标杆
v0.2.0 起在 MipNeRF360 基准测试中的 PSNR/SSIM 指标已超越 gsplat，证明了其实际可用性。

---

## 应用场景

### 3D 场景数字化
利用普通照片集快速重建真实场景的 3D 模型，适用于建筑、文化遗产数字化保护等领域。

### AR/VR 内容创作
为增强现实和虚拟现实应用快速生成真实感 3D 场景资产，降低内容制作成本。

### 教育与科研演示
在浏览器中直接进行 3D 重建演示，无需复杂的环境配置，便于教学和学术交流。

### 移动端 3D 扫描
在 Android 设备上直接进行 3D 重建，适用于户外现场快速采集和建模。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | ~4,258 |
| **总 Forks** | 227 |
| **开放 Issues** | 43 |
| **最近更新** | 2026-05-13 |
| **主要语言** | Rust |
| **许可证** | Apache License 2.0 |

---

## 总结

Brush 是一个极具创新性的开源 3D 重建项目，它将前沿的高斯溅射技术与 Rust 的性能和安全优势相结合，实现了从桌面到浏览器到移动端的真正全平台覆盖。项目不依赖 CUDA、支持免安装浏览器使用、重建质量超越主流方案（gsplat），且采用 Apache 2.0 许可证，极大降低了 3D 重建技术的使用门槛。对于 3D 视觉、AR/VR、数字孪生等领域的开发者和研究者来说，Brush 是一个值得关注和尝试的优秀工具。

---

*数据来源：GitHub 仓库 (ArthurBrussee/brush)*

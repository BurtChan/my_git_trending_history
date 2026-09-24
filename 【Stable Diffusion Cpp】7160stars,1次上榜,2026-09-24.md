# 项目名 项目分析

## 项目名称
**stable-diffusion.cpp** — 纯 C/C++ 实现的扩散模型推理：SD/Flux/Wan 等模型在 CPU 上的 GGUF 量化推理
- **GitHub**: [leejet/stable-diffusion.cpp](https://github.com/leejet/stable-diffusion.cpp)
- **许可证**: MIT

---

## 项目概述

stable-diffusion.cpp 是 leejet 开发的扩散模型纯 C/C++ 推理实现，精神上对标 llama.cpp 之于 LLM：依赖极简、可量化、可在 CPU（及各类加速后端）上本地运行 Stable Diffusion 全家桶——SD 1.x/2.x/SDXL/SD3、Flux、Wan（视频生成）等主流 diffusion 模型，支持 GGUF 量化格式以大幅降低显存/内存占用。

项目自 2023 年 8 月持续迭代至今（908 commits、691 个 release、113 位贡献者），基于 ggml 张量库构建，支持多种加速后端。近期动态密集：2026 年 9 月 23 日刚发布 master-908 版本，包含圆形 RoPE 重构与图像模型支持扩展（#2039）、Qwen Image 2.1 alpha 通道输入（#2021）、fp8 处理兼容上游 ggml（#2001）等改进。100% C++ 的单语言构成在 AI 项目中相当罕见。今日以 7,160 Stars、+33 增速登上 Trending。

## 核心功能

| 功能 | 说明 |
|------|------|
| 多模型支持 | SD 1.x/2.x、SDXL、SD3、Flux、Wan 视频生成等扩散模型家族 |
| GGUF 量化 | 与 llama.cpp 生态一致的量化权重格式，显著降低内存占用 |
| 多加速后端 | 基于 ggml，支持 CUDA/Vulkan/Metal 等 ggml 后端及纯 CPU |
| 图像编辑 | 支持 image-to-image、inpainting 等编辑工作流 |
| 多平台构建 | CMake 构建，提供 Docker 镜像（含 Vulkan NVIDIA 支持） |

## 技术栈

| 组件 | 技术 |
|------|------|
| 主语言 | C++（100%） |
| 张量库 | ggml（llama.cpp 同源） |
| 构建 | CMake |
| 部署 | 二进制 / Docker（Vulkan/CUDA） |

## 项目亮点

### llama.cpp 模式成功复刻到图像领域
把「纯 C++ + ggml + GGUF 量化 + CPU 可跑」的配方完整搬到 diffusion 模型上，与 llama.cpp 生态工具链互通。

### 模型跟进速度快
Qwen Image 2.1、Flux、Wan 等新模型在发布后短期内即获支持，2026 年 9 月仍在高频提交。

### 极致轻量的部署粒度
无 Python 依赖、单二进制即可运行，适合嵌入式、老硬件和无 Python 环境的设备。

## 应用场景

### 低配硬件本地出图
无独显或小显存设备上用 GGUF 量化模型本地生成图像。

### 边缘/嵌入式图像生成
单二进制 C++ 程序易于交叉编译部署到边缘设备。

### llama.cpp 生态整合
与本地 LLM 栈（GGUF 工具链、kompute 后端等）共享同一套量化与加载基础设施。

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 7,160 |
| 总 Forks | 809 |
| 今日新增 | +33 |
| 创建时间 | 2023 年 8 月 |

## 总结

stable-diffusion.cpp 把 llama.cpp 的成功配方（ggml + GGUF + 纯 C++）完整复刻到扩散模型领域，三年持续迭代覆盖 SD/Flux/Wan 全家族，是本地低资源图像与视频生成的基石项目。

---

*数据来源：GitHub 仓库 (leejet/stable-diffusion.cpp)，2026 年 9 月 24 日访问*

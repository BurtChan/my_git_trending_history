# DeepEP 项目分析

## 项目名称

**DeepEP** — DeepSeek 开源的高性能 MoE 专家并行通信库

- **GitHub**: [deepseek-ai/DeepEP](https://github.com/deepseek-ai/DeepEP)
- **许可证**: MIT

---

## 项目概述

DeepEP（Deep Expert Parallelism）是 DeepSeek 开源的高性能通信库，专门为**混合专家（MoE）模型架构**和**专家并行（Expert Parallelism, EP）** 系统设计。它在 DeepSeek 开源周第 2 天（2025 年 2 月）发布，是 DeepSeek 开源其大语言模型基础构建块承诺的重要组成部分。

MoE 模型（如拥有 671B 参数/每个 token 激活 37B 的 DeepSeek-V3）将专家子模型分片到多个 GPU 上，在"分发"（将 token 发送到正确的专家 GPU）和"合并"（收集结果）阶段产生通信瓶颈。DeepEP 通过提供高度优化的 all-to-all GPU 内核来解决这一瓶颈，是首个专门针对 MoE 专家并行通信的开源库。

DeepEP 可实现高达 **~160 GB/s NVLink** 和 **~127 GB/s RDMA** 的带宽，延迟低至 **77 μs**。它在 DeepSeek 的生产环境中经过实战验证，为 DeepSeek-V3 和 DeepSeek-R1 等旗舰模型提供动力。通过开源 DeepEP，DeepSeek 使更广泛的 AI 社区能够高效地跨多节点 GPU 集群扩展 MoE 架构。LMSYS 在 96-H100 基准测试中使用 DeepEP 实现了每节点 52.3k 输入 token/秒和 22.3k 输出 token/秒的性能，输出吞吐量比原始张量并行提升高达 5 倍。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **高吞吐量常规内核** | MoE 分发/合并的 all-to-all GPU 内核，NVLink 达 153-158 GB/s，RDMA 达 43-57 GB/s |
| **低延迟 RDMA 内核** | 面向推理解码的超低延迟内核，RDMA 带宽达 127 GB/s，延迟 77-314 μs |
| **FP8 低精度支持** | 支持 FP8 运算，减少内存占用并加速计算 |
| **非对称带宽转发** | 专为节点内和节点间非对称带宽场景设计的专用内核 |
| **NVLink & RDMA 双支持** | 完整支持 NVLink（节点内）和 RDMA/InfiniBand（节点间）连接 |
| **训练 & 推理双优化** | 分离的内核路径：面向训练/prefill 的吞吐量优化 + 面向解码的延迟优化 |
| **GPU 资源重叠** | 支持计算和数据传输同时进行，最大化 GPU 利用率 |
| **灵活网络配置** | 支持 InfiniBand、RoCE、虚拟通道流量隔离、自适应路由和拥塞控制 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | CUDA（GPU 内核，含 PTX 汇编优化）+ Python（绑定、示例） |
| **构建系统** | setup.py + setuptools，CUDA 扩展编译 |
| **核心依赖** | PyTorch、CUDA Toolkit、NVSHMEM（节点间 & 低延迟功能） |
| **硬件目标** | NVIDIA Ampere（A100, SM80）、Hopper（H800, SM90） |
| **网络** | NVLink、InfiniBand、RDMA/RoCE |
| **版本** | 1.2.1 |
| **许可证** | MIT（NVSHMEM 部分遵循 NVSHMEM SLA） |

---

## 项目亮点

### 首个开源 EP 通信库
DeepEP 是首个专门为 MoE 专家并行通信设计的开源库。此前，这一关键基础设施仅存在于大型 AI 实验室的闭源项目中。

### 生产级大规模验证
在 DeepSeek-V3 和 DeepSeek-R1——有史以来最大的开源 MoE 模型——的生产环境中经过实战验证。LMSYS 基准测试显示输出吞吐量提升高达 5 倍。

### 双模式内核架构
同时提供面向训练/prefill 的**吞吐量优化内核**和面向推理解码的**延迟优化 RDMA 内核**，用户可针对不同工作负载进行优化而无需权衡。低延迟内核与腾讯网络平台部门联合优化，性能提升达 30%。

### 深度生态集成
作为 DeepSeek 开源 MoE 技术栈的一部分，与 DeepGEMM（矩阵乘法）、EPLB（负载均衡器）、FlashMLA（注意力机制）、DualPipe 无缝集成。支持 SGLang 和 vLLM 推理框架。AMD 也创建了 ROCm 移植版。

---

## 应用场景

### 大规模 MoE 模型训练
在多节点 GPU 集群上训练 100B+ 参数的 MoE 大语言模型，DeepEP 的高吞吐量内核最小化 all-to-all 通信瓶颈。

### MoE 推理服务
部署 MoE 模型进行生产推理，利用低延迟 RDMA 内核实现快速解码响应。LMSYS 实现了 $0.20/1M 输出 token 的成本——仅为 DeepSeek 官方 API 的 1/5。

### Prefill-Decode 分离式服务
将 prefill 和 decode 阶段分离到不同 GPU 组，DeepEP 的两批次重叠（TBO）和 EPLB 特性降低延迟和内存使用。

### 多节点 GPU 集群扩展
使用 InfiniBand/RDMA 网络将 MoE 工作负载扩展到单节点边界之外，自适应路由和拥塞管理使其适用于大规模 HPC 部署。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 9,200+ |
| **总 Forks** | 1,200+ |
| **今日新增 Stars** | 29 |
| **许可证** | MIT |
| **创建时间** | 2025 年 2 月 |
| **主要语言** | CUDA |

---

## 总结

DeepEP 是 DeepSeek 开源的**首个 MoE 专家并行通信库**，9.2k+ Stars。它提供高度优化的 all-to-all GPU 内核，实现 160 GB/s NVLink 和 127 GB/s RDMA 带宽，在 DeepSeek-V3/R1 生产环境中经过验证。支持训练和推理双优化、FP8 低精度、灵活网络配置，与 SGLang、vLLM 等推理框架无缝集成，是大规模 MoE 模型训练和部署的关键基础设施。

---

*数据来源：GitHub 仓库 (deepseek-ai/DeepEP)、LMSYS Blog（2026 年 4 月访问）*

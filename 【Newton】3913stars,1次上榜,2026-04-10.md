# Newton 项目分析

> **一句话总结** -- 由 Disney Research、Google DeepMind 和 NVIDIA 联合发起的 GPU 加速物理仿真引擎，基于 NVIDIA Warp 构建，专为机器人学家和仿真研究者设计，支持可微仿真与多物理场耦合。

- **GitHub**: [newton-physics/newton](https://github.com/newton-physics/newton)
- **语言**: Python
- **Stars**: 3,913 | **今日新增**: 67
- **Forks**: 411
- **许可证**: Apache-2.0（代码）/ CC-BY-4.0（文档）
- **发起方**: Disney Research、Google DeepMind、NVIDIA
- **隶属**: Linux Foundation 项目

---

## 解决什么问题

机器人研究与仿真领域长期面临三大痛点：

1. **仿真速度瓶颈**：传统物理引擎（如 MuJoCo CPU 模式）在大规模并行仿真时性能不足，无法满足强化学习中数万环境同时运行的需求。
2. **多物理场割裂**：刚体、软体、流体、布料、线缆等不同物理模态通常需要不同工具链处理，缺乏统一的仿真框架。
3. **不可微分**：多数仿真器不支持梯度反传，阻碍了基于梯度的策略优化和系统辨识等研究方向的探索。

Newton 的核心目标是提供一个 **GPU 原生、可微分、多物理场统一** 的仿真平台，让机器人研究者能在同一框架内完成从刚体动力学到颗粒物质、从布料仿真到逆向动力学的全部工作流，同时享受 GPU 并行带来的数量级加速。

---

## 核心功能

| 功能领域 | 说明 |
| --- | --- |
| **GPU 加速仿真** | 基于 NVIDIA Warp 的 CUDA 内核，支持大规模并行环境仿真，适用于强化学习的大 batch 训练 |
| **MuJoCo Warp 后端** | 集成 MuJoCo Warp 作为主要物理后端，提供高精度刚体与关节动力学仿真 |
| **多物理场支持** | 涵盖刚体、软体（FEM）、布料（弹簧-质点）、线缆、流体（MPM）、颗粒物质等多种物理模态 |
| **可微仿真 (DiffSim)** | 支持通过仿真管道进行梯度反传，可用于基于梯度的优化、系统辨识、策略学习 |
| **逆向运动学 (IK)** | 内置 IK 求解器，支持 Franka、H1 等机器人的逆运动学求解与自定义配置 |
| **传感器仿真** | 支持接触传感器、相机（Tiled Camera）、IMU 等传感器模型的仿真 |
| **OpenUSD 支持** | 原生支持 OpenUSD 格式，可与 NVIDIA Omniverse 等 USD 生态工具无缝集成 |
| **多后端查看器** | 提供 OpenGL 实时查看器、USD 文件输出、ReRun 可视化等多种查看方式 |
| **丰富的机器人模型** | 内置 Cartpole、G1、H1、Anymal C/D、UR10、Panda、Allegro Hand 等机器人示例 |
| **可扩展架构** | 支持用户自定义物理模型、关节类型、力场和约束条件 |

---

## 技术栈

| 层级 | 技术 | 说明 |
| --- | --- | --- |
| **核心框架** | NVIDIA Warp | Python 框架，支持在 GPU 上运行高性能仿真与可微编程 |
| **物理后端** | MuJoCo Warp | MuJoCo 的 GPU 加速版本，Newton 的主要物理后端 |
| **编程语言** | Python 3.10+ | 用户 API 层全部使用 Python |
| **GPU 计算** | CUDA 12 | 需要 NVIDIA GPU（Maxwell 或更新架构），驱动 545+ |
| **可视化** | OpenGL / OpenUSD / ReRun | 多种渲染与可视化后端 |
| **CI/CD** | GitHub Actions + AWS GPU | 使用云端 GPU 进行持续集成测试 |
| **代码覆盖** | Codecov | 持续跟踪代码覆盖率 |
| **项目管理** | Linux Foundation | 社区治理，遵循 LF 行为准则 |

---

## 使用场景

| 场景 | 说明 |
| --- | --- |
| **机器人强化学习** | 利用 GPU 并行运行数千个仿真环境，加速策略训练（如 Anymal 行走、机械臂操控） |
| **可微仿真与优化** | 通过梯度反传进行系统参数辨识、轨迹优化、策略梯度学习 |
| **软体与布料仿真** | 仿真软体机器人、可变形物体、布料交互（如衣物穿脱、布料折叠） |
| **线缆与束线仿真** | 仿真线缆扭曲、Y 型分叉、束线滞后等工业场景 |
| **颗粒物质与流体** | 使用 MPM（物质点法）仿真沙土、雪、粘性流体等，支持与刚体的双向耦合 |
| **逆向运动学** | 为机械臂、人形机器人求解关节目标配置，支持多目标约束 |
| **接触丰富场景** | 螺栓螺母装配、砖块堆叠、金字塔构建、RJ45 插头等精密接触仿真 |
| **传感器模拟** | 在仿真环境中生成 IMU 数据、接触力数据、相机图像，用于感知算法开发 |
| **仿真研究与教学** | 丰富的示例库覆盖基础物理到复杂多物理场，适合教学与研究原型验证 |

---

## 安装与上手

安装极为简便，一行命令即可开始：

```bash
pip install "newton[examples]"
python -m newton.examples basic_pendulum
```

支持的平台包括 Linux（x86-64、aarch64）、Windows（x86-64）和 macOS（仅 CPU）。无需本地安装 CUDA Toolkit，NVIDIA GPU 驱动 545+ 即可。

---

## 项目亮点

- **顶级发起方**：由 Disney Research、Google DeepMind、NVIDIA 三家重量级机构联合发起，技术实力背书强
- **Linux Foundation 治理**：采用开源基金会治理模式，保证项目的长期中立性和社区驱动
- **从 warp.sim 的自然演进**：Newton 扩展并泛化了 NVIDIA Warp 中已废弃的 `warp.sim` 模块，延续了成熟的技术积累
- **示例极其丰富**：涵盖 60+ 示例，从基础钟摆到复杂多物理场耦合，覆盖机器人、布料、线缆、MPM、IK、DiffSim 等所有核心功能
- **Apache-2.0 许可**：商业友好的开源许可证，企业可放心使用

---

## 一句话总结

> Newton 是一个由 Disney Research、Google DeepMind 和 NVIDIA 联合打造、Linux Foundation 治理的 GPU 加速多物理场仿真引擎，通过 NVIDIA Warp 和 MuJoCo Warp 实现高性能并行仿真与可微计算，为机器人学研究提供从刚体到流体的全栈仿真解决方案。

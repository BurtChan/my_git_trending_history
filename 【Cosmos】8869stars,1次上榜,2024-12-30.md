# Cosmos 项目分析

## 项目名称
**Cosmos** — NVIDIA 面向物理 AI 的开放世界模型平台

- **GitHub**: [NVIDIA/cosmos](https://github.com/NVIDIA/cosmos)
- **许可证**: OpenMDW-1.1（Linux Foundation 发布的 AI 模型专用开放许可证，允许自由使用、修改和分发）

---

## 项目概述

NVIDIA Cosmos 是 NVIDIA 于 2025 年 CES 上首次发布的开放世界基础模型（World Foundation Model）平台，旨在为物理 AI（Physical AI）的开发提供世界模型、数据集和工具链。Cosmos 的核心目标是将机器人、自动驾驶汽车、智慧基础设施等需要理解和操作物理世界的 AI 系统的开发周期从数月压缩到数天。

Cosmos 3 于 2026 年 COMPUTEX 上发布，是该平台的最新一代模型家族。它基于 NVIDIA 独创的 **Mixture-of-Transformers（MoT）混合 Transformer 架构**，将自回归（AR）Transformer 用于推理和扩散 Transformer（DM）用于多模态生成统一在同一个架构中。两种模式共享相同的 Transformer 骨干网络和统一的 **3D 多维旋转位置编码（mRoPE）**，能够跨模态编码空间/时间结构。

Cosmos 3 的一个重大突破是其 **全模态（Omnimodal）** 能力——它支持 5 种输入模态（文本、图像、视频、音频、动作）和 5 种输出模态，是目前最强大的多模态物理 AI 模型之一。模型家族包含 Nano（16B）和 Super（64B）两个规模的版本，以及专用于机器人和自动驾驶的变体。

该平台已获得 Linux Foundation 的背书，NVIDIA 宣布 Cosmos、Isaac GR00T、Ising 和 Nemotron 等核心模型家族将统一采用 Linux Foundation 发布的 **OpenMDW-1.1** 开放许可证，建立了明确的开放模型分发框架。此外，NVIDIA 成立了 **Cosmos 联盟**（Cosmos Coalition），联合丰田、Uber、Kioxia 等行业合作伙伴共同推动物理 AI 生态标准化。

---

## 核心功能

### 1. 双运行时架构

Cosmos 3 提供两个互补的运行时表面：

| 运行时 | 输入 | 输出 | 核心用途 |
|--------|------|------|----------|
| **Reasoner（推理器）** | 文本、视觉 | 文本、JSON | 世界理解、物理推理、任务规划、动作预测、具身智能推理、自主系统决策 |
| **Generator（生成器）** | 文本、视觉、音频、动作 | 视觉、音频、动作、文本 | 世界生成、物理仿真、未来预测、合成数据生成、策略学习、机器人训练 |

### 2. 多种生成工作流

| 工作流 | 输入 | 输出 | 说明 |
|--------|------|------|------|
| 文本生成图像 | 文本 | 图像 | 从文本描述生成场景 |
| 文本生成视频 | 文本 | 视频 | 从密集描述生成工业级视频 |
| 文本生成视频+音频 | 文本 | 视频+音频 | 同步生成音视频内容 |
| 图像生成视频 | 文本+图像 | 视频 | 机器人操作动画 |
| 正向动力学 | 文本+视觉+动作 | 视觉 | 未来状态推演 |
| 动作策略 | 文本+视觉 | 动作+视频 | 动作轨迹生成+回放视频 |
| 视频理解 | 视频 | 文本/JSON | 详细视频描述、时序定位 |
| 具身推理 | 视频+问题 | 文本 | 下一步动作预测 |

### 3. 多种动作条件维度

Cosmos 支持多种机器人形态的动作空间维度：

| 机器人类型 | 动作维度 |
|------------|----------|
| 相机运动 | 9D |
| 自动驾驶 | 9D |
| 自我中心运动 | 57D |
| 单臂机器人 | 10D（DROID/UR/Fractal/Bridge/UMI） |
| 双臂机器人 | 20D（双 DROID 手臂） |
| 人形机器人 | 29D（AgiBot） |

### 4. 丰富的模型变体

| 模型 | 参数量 | 核心能力 |
|------|--------|----------|
| Cosmos3-Nano | 16B | 紧凑型全模态世界模型 |
| Cosmos3-Super | 64B | 前沿级全模态世界模型 |
| Cosmos3-Super-Text2Image | 64B | 高保真文本生成图像 |
| Cosmos3-Super-Image2Video | 64B | 时间连贯的图像生成视频 |
| Cosmos3-Nano-Policy-DROID | 16B | 视觉语言机器人操控策略 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心架构 | Mixture-of-Transformers（MoT）— 自回归 Transformer + 扩散 Transformer 统一架构 |
| 位置编码 | 3D 多维旋转位置编码（mRoPE），跨模态编码空间/时间结构 |
| 模型规模 | 16B（Nano） / 64B（Super） |
| 支持分辨率 | 256p / 480p / 720p |
| 支持帧率 | 10 / 16 / 24 / 30 FPS |
| 支持宽高比 | 16:9 / 4:3 / 1:1 / 3:4 / 9:16 |
| 精度 | BF16 |
| GPU 架构 | NVIDIA Ampere / Hopper / Blackwell |
| 许可证 | OpenMDW-1.1（Linux Foundation 发布的开放 AI 模型许可证） |
| 模型托管 | Hugging Face（nvidia 组织） |
| 框架代码 | [github.com/NVIDIA/cosmos-framework](https://github.com/NVIDIA/cosmos-framework) |

---

## 项目亮点

### Mixture-of-Transformers 统一架构

Cosmos 3 最核心的技术创新是其 MoT 架构。传统方法中，推理任务（如 VLM）和生成任务（如视频生成）通常使用完全不同的模型架构。Cosmos 3 将自回归 Transformer（用于推理、理解和文本生成）和扩散 Transformer（用于视觉、音频、视频生成）统一在同一个模型中，两种模式共享 Transformer 骨干和 mRoPE 位置编码。这种设计让一个模型同时具备推理、生成和行动（Reason, Generate, Act）三大能力，是真正的全模态世界模型。

### 全模态输入输出

Cosmos 3 支持文本、图像、视频、音频、动作五种输入模态和五种输出模态的自由组合。例如，它可以接收一段文本描述和一张图片，输出一段带同步音频的视频；也可以接收一个视频片段和一段动作序列，预测未来的物理状态。这种全模态能力使其能够直接处理物理 AI 中的复杂多模态任务，无需多个模型的串联。

### Cosmos 联盟生态

NVIDIA 联合 Toyota、Uber、Kioxia、Figure AI、Agility Robotics 等行业领军企业成立了 Cosmos 联盟。这种生态策略意味着 Cosmos 正在成为物理 AI 领域的**事实标准平台**——联盟成员越多，基于 Cosmos 构建的上下游工具链和训练数据越丰富，替代方案的竞争力就越弱。Uber 将其海量出行数据与 Cosmos + NVIDIA DGX Cloud 结合，加速自动驾驶 AI 训练，就是这一生态优势的典型体现。

### OpenMDW-1.1 开放许可

Linux Foundation 发布的 OpenMDW-1.1 是专为 AI 模型分发设计的开放许可证，允许用户自由使用、修改和分发模型材料，同时对输出不做限制。NVIDIA 将 Cosmos、Isaac GR00T、Ising、Nemotron 四大模型家族统一采用此许可证，标志着 NVIDIA 在 AI 模型开放分发上的重大转变，为全球 AI 社区提供了明确且宽松的使用框架。

---

## 应用场景

### 自动驾驶训练与仿真

自动驾驶是 Cosmos 的核心应用场景之一。通过 Cosmos 的 Generator 运行时，开发者可以从文本描述或真实驾驶数据生成逼真的驾驶场景视频（包括音频），用于训练自动驾驶系统的感知和决策模块。Cosmos 支持专门的 9D 自动驾驶动作空间，能够进行前向动力学推演——给定当前状态和驾驶动作，预测未来几秒的道路场景变化。这大幅降低了实车测试的成本和风险，将训练周期从数月压缩到数天。

### 机器人操控与策略学习

Cosmos 提供了从单臂（10D）到双臂（20D）再到人形机器人（29D）的完整动作空间支持。Cosmos3-Nano-Policy-DROID 是专门为 DROID 机械臂操控任务训练的策略模型，可直接输出动作轨迹并附带可视化回放视频。开发者可以用合成数据训练机器人策略，再用真实数据微调，实现从仿真到现实的平滑迁移。

### 物理推理与场景理解

Cosmos 的 Reasoner 运行时支持丰富的物理推理任务：视频描述、时序事件定位、物理合理性判断、下一步动作预测等。这些能力可用于构建更安全的机器人系统——在执行动作前，先用 Reasoner 判断物理环境的合理性，避免危险操作。对于智慧基础设施场景，Cosmos 能理解监控视频中的物理状态并预测异常事件。

### 工业合成数据生成

对于数据稀缺的物理 AI 场景（如极端天气驾驶、罕见工业事故），Cosmos 可以根据文本描述生成高质量合成训练数据。支持 720p 分辨率、24fps、最长 300 帧（约 12.5 秒）的视频生成，以及同步音频输出。这意味着开发者可以用极低的成本构建覆盖各种边缘情况的数据集，大幅提升 AI 系统的鲁棒性。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 8,869 |
| 🍴 Forks | 573 |
| 📈 今日新增 | 138 stars |
| 📅 创建时间 | 2024 年 12 月 30 日 |
| 💻 主要语言 | Jupyter Notebook |
| 📄 许可证 | OpenMDW-1.1 |
| 🏷️ 所属组织 | NVIDIA |
| 🤗 模型托管 | [Hugging Face - nvidia/cosmos3](https://huggingface.co/collections/nvidia/cosmos3) |

---

## 总结

NVIDIA Cosmos 是目前物理 AI 领域最全面的开放世界模型平台，其 Mixture-of-Transformers 统一架构实现了推理、生成和行动三大能力的融合，全模态输入输出覆盖了从文本到音频、从图像到动作的完整物理 AI 交互链。Cosmos 联盟的建立和 OpenMDW-1.1 许可证的采用，标志着 NVIDIA 正在从硬件供应商向物理 AI 基础设施平台转型。对于从事机器人、自动驾驶、工业仿真等物理 AI 开发的研究者和工程师来说，Cosmos 是一个值得深入关注的核心平台。

---

*数据来源：GitHub 仓库 (NVIDIA/cosmos)，2025 年 6 月访问*

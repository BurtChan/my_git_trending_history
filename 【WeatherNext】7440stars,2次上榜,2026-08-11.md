# WeatherNext 项目分析

## 项目名称
**WeatherNext** — Google DeepMind 的全球中期天气预报与热带气旋预测 AI 模型家族
- **GitHub**: [google-deepmind/weathernext](https://github.com/google-deepmind/weathernext)
- **许可证**: Apache-2.0（代码）/ CC BY 4.0（其他材料）

---

## 项目概述

WeatherNext 是 Google DeepMind 与 Google Research 开发的全球中期天气预报与热带气旋预测模型家族的开源仓库，目前的核心是 WeatherNext 2（WN2）——全球中期大气与气旋联合预测模型，同时托管了前代模型 GraphCast（图神经网络确定性预测）和 GenCast（扩散模型集合预测）的代码与文档。2026 年，WeatherNext 在气旋预测上取得突破：论文发表于 Nature（《Operational tropical cyclone forecasting with AI》），其模型在 2025 年大西洋飓风季实时运行。

WN2 采用 0.25° 分辨率（约 30 公里网格），在 ECMWF HRES 业务数据上微调，可直接用业务 HRES 初始条件初始化（而非 ERA5 再分析数据），训练数据覆盖到 2024 年。模型基于 FGN（联合概率预测，从边际分布出发）架构，同时预测天气场与气旋轨迹。除了 WN2，仓库还提供 WeatherNext Cyclones（复现论文结果的专用模型，含 2023/2024/2025 三套权重）和 WeatherNext Cyclones Mini（1° 分辨率的轻量版本，适合单 TPU/GPU 或低内存环境）。

对用户而言，除了自己跑模型，Google 还提供了多种直接获取 WN2 每日预测数据的方式：Google Cloud（Earth Engine、BigQuery、Vertex AI）、WeatherLab（含气旋轨迹）和 OpenMeteo（含 API 与交互式构建器），大幅降低了使用门槛。

## 核心功能

- **全球中期天气预报**：0.25° 分辨率（约 30km），预测温度、风速、位势高度等大气变量
- **热带气旋预测**：同一模型直接输出气旋轨迹，2025 年大西洋飓风季业务化运行（FNV3/GDMI）
- **确定性预测（GraphCast）**：基于图神经网络的确定性中期预报
- **集合预测（GenCast）**：基于扩散模型的概率集合预报，可评估极端天气风险
- **轻量版模型**：WeatherNext Cyclones Mini（1° 分辨率），低算力设备可跑
- **多平台数据服务**：Google Cloud / WeatherLab / OpenMeteo 提供每日预测数据流

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心框架 | JAX（含 JAX 兼容的 xarray 工具） |
| 模型架构 | FGN（WN2）、图神经网络（GraphCast）、扩散模型（GenCast） |
| 主要语言 | Python |
| 训练数据 | ECMWF ERA5（Zarr，经 WeatherBench2 获取）、HRES 业务数据 |
| 硬件要求 | TPU 优先；非 Mini 模型需 H100 级 GPU，Mini 模型 P100 可推理 |
| 许可证 | Apache-2.0（代码）/ CC BY 4.0（其他材料） |

## 项目亮点

### 业务化运行的气旋预测
WN2 气旋模型在 2025 年大西洋飓风季实时运行（NHC 后处理版本称 GDMI），是少数进入业务流程的 AI 天气预报模型，论文发表于 Nature，含 2025 年 NHC 流域的实测评估。

### 直接吃业务初始条件
WN2 针对 ECMWF HRES 业务分析数据微调，可直接从业务初始条件初始化，无需先跑再分析数据转换，与欧洲中期天气预报中心的业务链条无缝衔接。

### 全家桶式模型仓库
一个仓库涵盖三代模型（GraphCast → GenCast → WN2）与专用气旋模型，是研究 WeatherNext 家族模型的唯一入口，方便横向对比与复现。

### 多路径开放获取
除开源权重外，Google Cloud / WeatherLab / OpenMeteo 三条数据通道让非研究者也能直接消费 WN2 每日预测，降低 AI 天气预报的应用门槛。

## 应用场景

### 气象业务与防灾
气象机构可将 WN2 纳入预报链条，用 AI 模型的气旋轨迹预测辅助台风路径研判与防灾减灾决策，尤其适合热带气旋高发地区。

### 极端天气风险评估
GenCast 的扩散模型集合预测可输出概率化的极端天气（高温、强降水、强风）风险，服务于保险精算、能源调度和应急管理。

### 学术研究与模型复现
研究者可用仓库代码复现 Nature 论文结果，对比三代模型性能，或在 WN2 基础上微调、改进用于区域预报。

### 数据产品与 API 服务
通过 OpenMeteo API 或 Google Cloud 数据流，开发者可以把 WN2 预测集成进天气类 App、农业决策系统或能源预测平台。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 7,440 |
| 总 Forks | 959 |
| 主要语言 | Python |
| 许可证 | Apache-2.0 |
| 创建时间 | 2023-07-14 |

---

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 11 日（再次登上 Trending）

**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：WeatherNext 于 8 月 6 日迎来重大里程碑：DeepMind 在 Nature 发表论文《Operational tropical cyclone forecasting with AI》并同步开源 WeatherNext 2、WeatherNext Cyclones 与轻量版 2-mini 全套代码与权重。论文显示其气旋预测平均比现有业务系统多出约一整天的提前量（三天预报精度相当于此前两天的水平），相当于气象领域约十年的进步。模型将集合规模从去年的 50 条预测扩至 1,000 条，单个 15 天预报在 TPU 上不到一分钟即可生成；WeatherNext 2-mini 可在单个 TPU 的免费 Colab 笔记本上运行，大幅降低使用门槛。开源与论文发布带动 Star 数从 6,927 快速攀升至 7,440（+513），连续第二日登上 Trending。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 6,927 | 7,440 | +513 |
| 总 Forks | 913 | 959 | +46 |

**核心变化概要**：

- Nature 论文发表 + 全套模型开源（WN2 / Cyclones / 2-mini），Stars 6,927 → 7,440（+513）
- 气旋预测平均多出约一天提前量，相当于气象领域约十年进步
- 集合规模扩至 1,000 条预测，2-mini 可在免费 Colab 单 TPU 运行

---

## 总结

WeatherNext 是 Google DeepMind 将 AI 引入天气预报的标志性开源项目，从 GraphCast、GenCast 到业务化的 WeatherNext 2，三代模型齐聚一仓，0.25° 分辨率、直接消费业务初始条件、2025 年飓风季实战验证，代表了 AI 中期天气预报的当前最高水平。

---

*数据来源：GitHub 仓库 (google-deepmind/weathernext)，2026 年 8 月访问*
*首次分析：2026 年 8 月 | 最近更新：2026 年 8 月*

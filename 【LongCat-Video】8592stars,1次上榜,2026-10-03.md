# LongCat-Video 项目分析

## 项目名称
**LongCat-Video** — 美团龙猫团队的 13.6B 参数基础视频生成模型，统一 Text-to-Video / Image-to-Video / Video-Continuation 三任务
- **GitHub**: [meituan-longcat/LongCat-Video](https://github.com/meituan-longcat/LongCat-Video)
- **许可证**: MIT
- **语言**: Python
- **模型**: HuggingFace meituan-longcat/LongCat-Video
- **技术报告**: arXiv 2510.22200

---

## 项目概述

LongCat-Video 是美团 LongCat（龙猫）团队发布的 13.6B 参数基础视频生成模型，在文生视频（Text-to-Video）、图生视频（Image-to-Video）和视频续写（Video-Continuation）三大任务上使用**单一统一架构**原生支持，各单项任务均表现强劲。官方将其定位为迈向世界模型的第一步。

该项目最突出的能力是**长视频生成**：模型原生在 Video-Continuation 任务上预训练，可以生成分钟级长度的视频而不出现色彩漂移或质量退化——这是当前开源视频生成模型的普遍短板。推理效率上，通过时间与空间双轴的 coarse-to-fine（由粗到细）生成策略，可在数分钟内产出 720p、30fps 视频；Block Sparse Attention（块稀疏注意力）进一步增强了高分辨率下的效率。

训练层面采用多奖励 GRPO（Group Relative Policy Optimization）强化学习，在内部与公开基准上的综合评估显示，其性能与领先的开源视频生成模型乃至最新商业方案相当。生态方面，团队还在同一仓库迭代了 LongCat-Video-Avatar 系列（音频驱动的人物视频生成），v1.5 版已用 Whisper-Large 替换 Wav2Vec2 实现更精准的唇同步，并支持 8 步蒸馏加速推理。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 统一三任务架构 | 单一模型原生支持 Text-to-Video、Image-to-Video、Video-Continuation |
| 分钟级长视频生成 | Video-Continuation 预训练，长视频无色彩漂移、无质量退化 |
| 高效推理 | 时空双轴 coarse-to-fine 策略，数分钟生成 720p/30fps；Block Sparse Attention 提升高分辨率效率 |
| 多奖励 GRPO | 强化学习对齐，开源基准与商业方案相当的性能 |
| Avatar 1.5 扩展 | 音频驱动人物视频生成：Whisper-Large 唇同步、长视频时序稳定、风格化域泛化（动漫/动物/复杂实景）、单流+多流音频输入、8 步蒸馏加速 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 模型规模 | 13.6B 参数 |
| 生成策略 | Coarse-to-Fine（时间轴 + 空间轴） |
| 注意力优化 | Block Sparse Attention |
| 对齐训练 | Multi-Reward GRPO（RLHF） |
| Avatar 唇同步 | Whisper-Large（v1.5，替代 Wav2Vec2） |
| 输出规格 | 720p @ 30fps，分钟级时长 |

---

## 项目亮点

### 长视频生成的开源标杆
开源视频模型普遍「几秒即崩」（色彩漂移、主体变形），LongCat-Video 靠原生 Video-Continuation 预训练把可用时长拉到分钟级，直接命中工业界内容生产的核心痛点。

### 单模型多任务，工程成本友好
不用为文生视频、图生视频、视频续写分别维护模型，一套 13.6B 权重全包，部署和微调成本大幅降低。

### 大厂背书 + 宽松许可
美团出品、MIT 许可、权重全量开放（HuggingFace + ModelScope 双渠道），商业可用性明确，在国产开源视频模型中诚意十足。

---

## 应用场景

### 长视频内容生产
营销短片、动画分镜、课程视频等需要数十秒到分钟级时长的场景，续写式生成保证前后一致性。

### 图生视频 / 老照片动态化
单张图片驱动生成动态视频，配合 Avatar 系列可做数字人播报、口型对齐的虚拟形象视频。

### 视频续写与补全
已有素材的无缝续写、补帧与延展，适合影视后期和素材二次创作流程。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 8,592 |
| 🍴 Forks | 1,517 |
| 📈 今日新增 | +43 |

---

## 总结

美团龙猫的 LongCat-Video 用一个 13.6B 统一模型把文生视频、图生视频、视频续写和分钟级长视频生成全部打通，MIT 开源 + 全量权重，是当前工业可用性最强的国产开源视频生成模型之一。

---

*数据来源：GitHub 仓库 (meituan-longcat/LongCat-Video)，2026 年 10 月访问*
*首次分析：见文件头部 | 最近更新：2026 年 10 月 3 日*

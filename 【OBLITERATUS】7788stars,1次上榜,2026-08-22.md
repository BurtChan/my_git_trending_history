# OBLITERATUS 项目分析

## 项目名称
**OBLITERATUS** — 最先进的开源 LLM 拒绝行为移除（abliteration）研究工具包
- **GitHub**: [elder-plinius/OBLITERATUS](https://github.com/elder-plinius/OBLITERATUS)
- **许可证**: AGPL-3.0（+ 商业双许可）

---

## 项目概述
OBLITERATUS 由知名提示词黑客 Pliny the Prompter（elder-plinius）开发，是研究与大模型"拒绝行为"移除的开源工具包。它实现 abliteration 技术族：定位模型内部负责内容拒绝的表征方向（refusal direction），在不重训、不微调的前提下"外科手术式"地移除，同时保留模型核心语言能力。仓库 7,788 stars，2026 年 8 月 22 日首次登上 Trending（单日 +63）。

项目特别之处在于"分布式研究实验"定位：每次开启遥测的 obliteration 运行都会贡献匿名基准数据，形成众包数据集反哺下一代 abliteration 研究。

---

## 核心功能
| 功能 | 描述 |
|------|------|
| 拒绝方向探测 | 探测隐藏态定位 refusal direction，可视化各层拒绝分布 |
| 多种提取策略 | PCA、均值差、稀疏自编码机分解、白化 SVD |
| 干预方式 | 推理时置零或推离拒绝方向 |
| 能力纠缠度量 | 量化拒绝与通用能力的纠缠度、合规-连贯权衡 |
| Gradio 界面 | HuggingFace Spaces 免代码操作（ZeroGPU 免费额度） |
| Python API | 暴露激活张量、方向向量、跨层对齐矩阵等中间产物 |

---

## 技术栈
| 组件 | 技术 |
|------|------|
| 语言 | Python（pyproject + uv） |
| 界面 | Gradio（HF Spaces / Colab 一键运行） |
| 部署 | Dockerfile、HF Spaces、Colab notebook |
| 理论基础 | Arditi et al. 2024、Gabliteration、grimjim 双投影、Turner et al. 2023、Rimsky et al. 2024 |

---

## 项目亮点
### 单命令/零命令流水线
`obliteratus obliterate <model> --method advanced` 一条命令完成，或 Colab "Run All"，研究门槛极低。

### 众包科研模式
把工具使用本身变成数据贡献——跨架构拒绝方向、硬件性能画像、方法对比在单一实验室无法企及的规模上积累。

### 严谨的研究定位与免责框架
明确对标 HarmBench/JailbreakBench 等安全研究工件，AGPL + 商业双许可，并附带完整责任声明。

---

## 应用场景
### 对齐机制可解释性研究
研究拒绝行为在 transformer 激活空间中的几何结构。
### 红队与安全评估
评估安全训练对后训练修改的鲁棒性。
### 自部署模型行为定制
部署方自行决定模型行为边界，而非接受训练时锁定的拒绝策略。

---

## Star 数据
| 指标 | 数值 |
|------|------|
| 总 Stars | 7,788 |
| 总 Forks | 1,432 |
| 今日新增 | +63 |
| 创建时间 | 2026 年（145 commits） |

---

## 总结
把 abliteration 从论文变成"一条命令"的完整研究工具包，加上众包数据集的飞轮设计，是目前 LLM 拒绝行为研究方向工程化程度最高的开源实现。

---

*数据来源：GitHub 仓库 (elder-plinius/OBLITERATUS)，2026 年 8 月访问*

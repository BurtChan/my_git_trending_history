# Kronos 项目分析

> **一句话总结：Kronos 是首个面向金融市场 K 线（蜡烛图）数据的开源基础模型，通过专用分词器将连续 OHLCV 数据转化为层次化离散 Token，再以自回归 Transformer 进行预训练，为量化交易、价格预测等金融任务提供统一的基础模型能力。**

---

## 一、基本信息

| 项目 | 详情 |
|------|------|
| **项目名称** | Kronos: A Foundation Model for the Language of Financial Markets |
| **GitHub 地址** | https://github.com/shiyu-coder/Kronos |
| **Star 数** | ~11,967+（2026 年 4 月 10 日，当日 +223） |
| **Fork 数** | 持续增长中 |
| **开源协议** | MIT License |
| **主要语言** | Python |
| **作者/组织** | Yu Shi（施宇）、Zongliang Fu、Shuo Chen、Bohan Zhao、Wei Xu、Changshui Zhang、Jian Li |
| **机构背景** | 清华大学 / 相关学术机构 |
| **论文** | arXiv:2508.02739（2025 年 8 月） |
| **会议** | AAAI 2026（已录用，2025 年 11 月确认） |
| **模型托管** | Hugging Face（NeoQuasar 组织） |
| **创建时间** | 2025 年 |
| **GitHub Topics** | foundation-model, financial-markets, k-line, time-series, transformer, quantitative-finance |

---

## 二、解决什么问题

### 2.1 核心痛点

金融市场时间序列预测面临几个关键挑战：

1. **金融数据的高噪声特性**：金融 K 线数据（OHLCV）具有极高噪声和非平稳性，通用时间序列基础模型（TSFM）难以有效处理。传统模型在金融场景中的表现往往不理想。

2. **缺乏面向金融的专用基础模型**：尽管大语言模型在文本领域取得了巨大成功，但金融市场核心的 K 线数据是连续多维数值序列，无法直接用文本范式处理。此前没有专门面向 K 线数据的开源基础模型。

3. **量化任务的碎片化**：价格预测、趋势判断、波动率估计等量化任务各自独立建模，缺乏统一的模型底座来同时支撑多种下游任务。

4. **多交易所、多品种的泛化难题**：全球有 45+ 交易所，数据分布差异巨大。从头训练特定市场模型的成本高、泛化差。

### 2.2 Kronos 的解法

Kronos 借鉴 NLP 领域"文本分词 + 自回归预训练"的范式，将其迁移到金融 K 线数据上：先用专用分词器将连续 OHLCV 数据量化为层次化离散 Token，再用大型自回归 Transformer 对这些 Token 进行预训练，从而构建一个能理解"金融市场语言"的基础模型。

---

## 三、核心功能

### 3.1 专用金融 K 线分词器（Kronos-Tokenizer）

- 将连续的多维 K 线数据（Open/High/Low/Close/Volume）量化为**层次化离散 Token**
- 两个版本：`Kronos-Tokenizer-base`（上下文 512）和 `Kronos-Tokenizer-2k`（上下文 2048）
- 分词器可针对特定市场数据进行微调，以更好地捕捉目标市场的数据分布特征

### 3.2 K 线序列预测

- 输入历史 K 线数据，自动完成归一化、分词、预测、反归一化全流程
- 支持概率预测：通过温度（Temperature）和核采样（Top-p）控制生成多样性
- 支持多条路径采样并取平均，提升预测鲁棒性
- `KronosPredictor` 类封装了完整预测流程，几行代码即可获得预测结果

### 3.3 批量预测（predict_batch）

- 支持同时对多个资产或多个时间段进行并行预测
- 利用 GPU 并行计算能力，大幅提升推理效率
- 自动独立处理每条序列的归一化与反归一化

### 3.4 微调流程（Fine-tuning）

- 提供完整的微调 Pipeline，支持将 Kronos 适配到自有数据
- 两阶段微调：先微调分词器，再微调预测模型
- 内置 A 股市场示例：使用 Qlib 数据进行微调与回测
- 支持多 GPU 训练（torchrun）
- 提供回测评估脚本，输出累计收益曲线等可视化结果

### 3.5 模型矩阵（Model Zoo）

| 模型 | 参数量 | 上下文长度 | 开源状态 |
|------|--------|------------|----------|
| Kronos-mini | 4.1M | 2048 | 开源 |
| Kronos-small | 24.7M | 512 | 开源 |
| Kronos-base | 102.3M | 512 | 开源 |
| Kronos-large | 499.2M | 512 | 未开源 |

所有开源模型均托管在 Hugging Face Hub 的 NeoQuasar 组织下，可直接加载使用。

### 3.6 在线演示（Live Demo）

- 提供 BTC/USDT 交易对的实时 24 小时预测可视化
- 可直观感受模型预测效果

---

## 四、技术栈

### 4.1 核心技术

| 技术 | 用途 |
|------|------|
| **Python 3.10+** | 核心开发语言 |
| **PyTorch** | 深度学习框架，模型训练与推理 |
| **Transformer（Decoder-only）** | 模型架构，自回归生成 |
| **Hugging Face Transformers** | 模型分发与加载（`from_pretrained`） |
| **Pandas** | 数据处理与时间序列操作 |
| **torchrun** | 多 GPU 分布式训练 |

### 4.2 微调生态

| 技术 | 用途 |
|------|------|
| **Qlib** | 微软开源的量化投资平台，用于 A 股数据准备与回测 |
| **Comet.ml**（可选） | 实验追踪与可视化 |
| **pickle** | 数据序列化存储 |

### 4.3 关键算法创新

- **层次化离散分词**：将连续 OHLCV 多维数据量化为多层次离散表示，保留价格结构与波动信息
- **两阶段训练框架**：分词器预训练 + Transformer 自回归预训练，解耦表征学习与序列建模
- **概率预测机制**：通过采样策略（Temperature、Top-p）生成多条预测路径，提供预测不确定性估计

---

## 五、使用场景

### 5.1 量化交易策略研发

- 使用 Kronos 对目标市场进行微调，生成价格预测信号
- 结合投资组合优化模型，构建完整的量化策略
- 项目内置 A 股 Top-K 策略示例，可作为起点

### 5.2 金融时间序列预测

- 股票、期货、加密货币等多品种的价格走势预测
- 支持多种时间频率（5 分钟线、日线等）
- 支持 OHLCV 全维度预测（开高低收量额）

### 5.3 波动率与风险分析

- 通过多条采样路径评估市场不确定性
- 为风险管理提供概率化的价格区间估计

### 5.4 学术研究

- 论文已被 AAAI 2026 录用，具有学术参考价值
- 可作为金融 AI 领域的基准模型（Baseline）
- 便于复现论文实验结果

### 5.5 多市场泛化应用

- 预训练数据覆盖 45+ 全球交易所
- 通过微调可快速适配到特定交易所或交易品种
- 跨市场迁移能力适用于新兴市场或流动性较差的品种

### 5.6 金融数据理解与表征学习

- 分词器提供的离散化表征可用于下游聚类、分类等任务
- 为金融数据的表示学习提供新范式

---

## 六、架构设计亮点

### 6.1 "金融语言"范式创新

Kronos 的核心创新在于将 NLP 中成熟的"分词 + 自回归预训练"范式迁移到金融 K 线数据上。通过将连续 OHLCV 数据离散化为 Token，使得 Transformer 架构这一在 NLP 领域被充分验证的技术可以直接应用于金融时间序列。

### 6.2 层次化分词机制

不同于简单的标量量化，Kronos 的分词器生成层次化的离散 Token，能够在不同粒度上捕捉价格变动的结构信息。这种设计使得模型在保留高频细节的同时也能理解宏观走势。

### 6.3 模型规模梯度设计

从 4.1M（mini）到 499.2M（large）的参数量梯度，覆盖了从边缘设备部署到高性能服务器计算的不同场景需求。用户可根据计算资源和精度要求灵活选择。

### 6.4 完整的微调与评估闭环

项目不只提供推理代码，还提供完整的微调 Pipeline（分词器微调 + 模型微调）和基于 Qlib 的回测评估流程，形成了从数据准备到策略评估的闭环。

---

## 七、快速上手

### 安装与推理

```bash
pip install -r requirements.txt
```

```python
from model import Kronos, KronosTokenizer, KronosPredictor

# 加载模型与分词器
tokenizer = KronosTokenizer.from_pretrained("NeoQuasar/Kronos-Tokenizer-base")
model = Kronos.from_pretrained("NeoQuasar/Kronos-small")

# 初始化预测器
predictor = KronosPredictor(model, tokenizer, max_context=512)

# 准备数据并预测
pred_df = predictor.predict(
    df=x_df,
    x_timestamp=x_timestamp,
    y_timestamp=y_timestamp,
    pred_len=120,
    T=1.0,
    top_p=0.9,
    sample_count=1
)
```

### 微调

```bash
# 微调分词器
torchrun --standalone --nproc_per_node=2 finetune/train_tokenizer.py

# 微调预测模型
torchrun --standalone --nproc_per_node=2 finetune/train_predictor.py

# 回测评估
python finetune/qlib_test.py --device cuda:0
```

---

## 八、项目生态与社区

- **AAAI 2026 录用**：顶会论文背书，学术影响力强
- **Hugging Face 模型分发**：所有开源模型可通过 `from_pretrained` 一行代码加载
- **活跃增长**：11,967+ Stars，单日增长 223，位列 GitHub Trending
- **与 Qlib 生态打通**：可直接使用微软 Qlib 的数据和回测框架
- **MIT 开源协议**：商用友好，无使用限制

---

## 九、注意事项

- **非生产就绪**：项目作者明确指出，提供的微调与回测示例仅为演示，不是可直接上线的量化交易系统。实际生产环境需要组合优化、风险因子中性化等更复杂的技术。
- **Kronos-large 未开源**：最大的 499.2M 参数模型尚未开源。
- **信号不等于 Alpha**：模型输出的是原始预测信号，需要经过投资组合优化才能转化为可用的 Alpha。

---

## 十、总结

> **Kronos 是首个面向金融市场 K 线数据的开源基础模型，它通过创新的层次化分词器将连续 OHLCV 数据转化为离散 Token，再以自回归 Transformer 进行大规模预训练（覆盖 45+ 全球交易所），为量化交易、价格预测和金融时间序列分析提供统一的基础模型底座。论文被 AAAI 2026 录用，模型从 4.1M 到 499.2M 参数梯度覆盖不同计算场景，并提供完整的微调与回测 Pipeline，是金融 AI 领域的重要开源贡献。**

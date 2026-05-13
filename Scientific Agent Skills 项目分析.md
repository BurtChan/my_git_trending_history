# Scientific Agent Skills 项目分析

## 项目名称

**Scientific Agent Skills** — 面向科研人员的 135 个即用型 AI Agent 科学技能集合

- **GitHub**: [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills)
- **许可证**: MIT License

---

## 项目概述

**Scientific Agent Skills**（前身为 Claude Scientific Skills）是由 K-Dense Inc. 开发并开源的一个综合性科研项目，提供 **135 个即用型科学和研究技能**，旨在为支持开放 Agent Skills 标准的 AI 代理赋能。该项目覆盖了从癌症基因组学、药物靶标结合、分子动力学到 RNA 速度分析、地球空间科学、时间序列预测等广泛的科学领域，同时集成 **78+ 科学数据库**，使 AI 代理能够高效、可靠地执行复杂的科研工作流。

项目最初以"Claude Scientific Skills"命名，专注于 Claude Code 生态。随着发展，项目更名为"Scientific Agent Skills"，扩展了兼容性——现在可运行于 Cursor、Claude Code、Codex 等任何支持 Agent Skills 标准的 AI 代理平台。此外，K-Dense 还推出了配套的桌面应用 **K-Dense BYOK**（Bring Your Own Key），支持 40+ 大模型选择，提供完整的科研工作空间，包括网络搜索、文件处理和所有 135 项技能的访问权限。

项目在安全方面也做出了重要投入：每个技能均通过 **Cisco AI Defense Skill Scanner** 进行安全扫描，确保用户在使用过程中免受潜在恶意行为的威胁。同时，社区贡献活跃，项目欢迎来自全球研究者的技能添加、改进和问题反馈。

---

## 核心功能

### 科学数据库与数据访问
- **78+ 科学数据库集成**：覆盖 PubMed、NCBI、UniProt、PDB 等主流科研数据库的统一查询接口

### 生物信息学与基因组学
- **Scanpy / AnnData**：单细胞 RNA-seq 分析
- **Biopython**：分子生物学工具包
- **Deeptools**：NGS 分析工具
- **Gget**：快速查询 20+ 生物信息学数据库

### 化学信息学与药物发现
- **RDKit / Datamol**：药物发现与分子操作
- **DeepChem**：分子机器学习与特征化
- **DiffDock**：蛋白质-配体结合姿态预测
- **MedChem**：药物化学过滤器

### 蛋白质工程与设计
- **ESM**：蛋白质语言模型
- **FlowIO**：流式细胞术数据预处理

### 机器学习与深度学习
- **PyTorch / TensorFlow** 生态集成
- **Dask**：分布式计算，处理超内存工作流
- **Aeon**：时间序列机器学习

### 临床研究与精准医学
- **Clinical Reports**：临床报告撰写
- **DepMap**：癌症依赖图谱查询

### 科学沟通与出版
- **LaTeX Posters**：科研海报制作
- **Literature Review**：系统性文献综述

### 实验室自动化与 LIMS 集成
- **Benchling Integration**：实验室数据管理自动化
- **LabArchive Integration**：电子实验记录本 API 集成
- **LatchBio Integration**：生物信息学工作流构建

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要编程语言** | Python |
| **Agent 标准** | 开放 Agent Skills 标准 (agentskills.io) |
| **安装工具** | npx / GitHub CLI (gh skill) |
| **安全扫描** | Cisco AI Defense Skill Scanner |
| **云计算平台** | Modal（可选） |
| **MCP 集成** | Streamable-http 传输协议 |
| **桌面应用** | K-Dense BYOK（开源 AI 联合科学家） |
| **兼容 AI 代理** | Claude Code、Cursor、Codex 等 |
| **许可证** | MIT License |

---

## 项目亮点

### 覆盖面广，技能丰富
涵盖 135 个即用型技能，横跨生物信息学、化学信息学、药物发现、基因组学、蛋白质组学、神经科学、材料科学、工程仿真、临床研究等 18+ 个学科领域，是目前最全面的 AI 科研技能集合之一。

### 跨平台兼容性强
项目已从 Claude Code 专属扩展为支持所有主流 AI 代理（Cursor、Codex 等）的开放标准，大幅降低了使用门槛，真正实现了"一次安装，多平台通用"。

### 安全可靠，社区活跃
所有技能均经过 Cisco AI Defense 安全扫描，且项目拥有活跃的开源社区（2,300+ Fork、32 个开放 Issue、持续不断的 Pull Request），确保了技能的质量与安全性。

### 一键安装，即用即走
支持 `npx scientific-agent-skills install` 一行命令安装，也支持 GitHub CLI `gh skill` 方式，极大简化了部署流程。

---

## 应用场景

### 药物发现与药物重定位
通过分子动力学模拟、蛋白质-配体对接（DiffDock）、药物化学过滤（MedChem）和虚拟筛选等技能，构建从靶标识别到候选药物筛选的完整流水线。

### 单细胞与多组学分析
整合 RNA-seq、蛋白质组学和代谢组学数据（Scanpy、AnnData、MatchMS 等），实现多组学生物标志物发现，支持精准医学研究。

### 临床研究与合规文档
利用临床报告撰写、ISO 13485 认证文档准备、临床决策支持等技能，加速临床试验文档编写与监管合规流程。

### 跨学科科研工作流自动化
通过实验室自动化集成（Benchling、LabArchive、Ginkgo Cloud Lab）、文献综述、假说生成和可视化工具，将科研人员从重复性工作中解放出来。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | ~20,876 |
| **总 Forks** | ~2,307 |
| **开放 Issue 数** | 32 |
| **创建日期** | 2025 年 10 月 19 日 |
| **最近更新** | 2026 年 5 月 13 日 |
| **许可证** | MIT License |
| **主要编程语言** | Python |

---

## 总结

Scientific Agent Skills 是当前 AI for Science 领域最全面的开源技能集合之一。由 K-Dense Inc. 开发维护，该项目以 135 个精心策划的科研技能覆盖了从基础数据分析到前沿药物发现的完整科研链条，并凭借开放 Agent Skills 标准实现了跨 AI 代理平台的广泛兼容。20,000+ GitHub Star 充分证明了其社区影响力。对于任何希望利用 AI 辅助科研工作的研究者来说，无论是生物学家、化学家还是数据科学家，这个项目都是一个值得关注的强大工具。

---

*数据来源：GitHub 仓库 (K-Dense-AI/scientific-agent-skills)，数据采集时间 2026 年 5 月 13 日*

# Scenario Agent Skills 项目分析

## 项目名称
**Scenario Agent Skills** — 教 AI 编码代理用 Scenario 生成生产级游戏/创意内容的技能库
- **GitHub**: [scenario-labs/skills](https://github.com/scenario-labs/skills)
- **许可证**: MIT

---

## 项目概述

Scenario Agent Skills 是 Scenario（scenario.com，面向游戏行业的 AI 生成平台）官方发布的 Agent Skills 合集，通过 Agent Skills 开放规范（SKILL.md 格式）教会 Claude Code、Cursor、Codex、Copilot 等 70+ AI 编码代理使用 Scenario MCP 服务器来创建生产级内容：图像、视频、音频、纹理、天空盒、3D 资产和自定义训练模型，面向游戏、娱乐及各类创意领域。

技能库分两大类：第一类是通过 Scenario MCP 服务器工作的云端技能（80+ 个），覆盖图像生成/编辑、品牌套件、产品摄影、故事板、游戏资产（精灵图、图标、tileset、像素风）、精灵动画、纹理、天空盒、3D 模型、视频生成与剪辑、音频/音乐、模型训练与质量把关等全流程；第二类是「专家工具（Expert Tools）」——驱动本机安装的 DCC 软件和游戏引擎（ZBrush、Blender、Maya、Unreal、Unity、Godot、Roblox Studio）的技能家族，从专家教程、大会演讲和官方文档中蒸馏而来，每个家族文件夹的 README 记录了构建方法与验证程度。

项目创建于 2026 年 8 月，三日在榜累计达 2,929。它代表了「垂类平台 + Agent Skills 分发」的新模式：平台能力通过标准化技能文件直接进入开发者的 AI 工作流。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **图像生成/编辑** | 文生图、多参考合成、产品摄影、品牌套件、遮罩修复、文字覆盖卡 |
| **游戏资产** | 精灵图/图标/道具/tileset/像素画/概念图/透明背景/风格一致批量生成 |
| **精灵动画** | 走路/待机/VFX 动画序列，GIF 与 sprite sheet 输出、帧切片、像素清理 |
| **3D 与纹理** | 无缝纹理、天空盒、3D 模型生成与 GLB 预览、可行走空间 |
| **视频与音频** | 视频生成、剪辑、调色、音乐视频、音效、音乐生成 |
| **模型训练** | 场景一致性、身份库、自定义模型训练与质量门槛 |
| **专家工具** | 驱动 ZBrush/Blender/Maya/Unreal/Unity/Godot/Roblox Studio 本机软件 |
| **发行管理** | release-please 自动版本化、CHANGELOG、可 pin 审定版本安装 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 技能格式 | Agent Skills 开放规范（SKILL.md） |
| 安装分发 | npx skills CLI（70+ agent 兼容）、skills.sh 生态目录 |
| 平台接入 | Scenario MCP 服务器（HTTP transport + OAuth/API key） |
| 脚本测试 | Python 3.11+（unittest）、TypeScript（vitest）、ffmpeg |
| 工程化 | pnpm、commitlint、cspell、husky、OpenSSF Scorecard、CI |

---

## 项目亮点

### 1. 垂类平台的 Agent Skills 分发范式
Scenario 把自家平台的完整能力（生成、训练、质检、资产管理）蒸馏成 80+ 个标准化技能文件，AI 编码代理装上即会用——这可能是垂直 SaaS 拥抱 Agent 生态最彻底的案例之一。

### 2. 专家工具的「知识蒸馏」工程
驱动本机 DCC 软件/游戏引擎的技能家族不是简单 API 封装，而是从专家教程、大会演讲、官方文档中蒸馏出的程序性知识，每个家族 README 如实记录构建方法与验证边界。

### 3. 工程质量罕见地严格
每个技能自带脚本测试套件（CI 同跑）、OpenSSF Scorecard、可 pin 的审定 release、Conventional Commits 规范——把一个「prompt 合集」做成了有完整软件工程纪律的项目。

### 4. 按角色/目标组织的安装矩阵
INSTALL.md 按 2D 美术到制作人等角色、游戏美术到 ChatGPT 宠物等成果组织安装命令，一条命令装齐一个岗位所需的全部技能。

---

## 应用场景

### 游戏工作室资产生产管线
美术团队在 Claude Code/Cursor 中批量生成风格一致的精灵图、图标、纹理，再走专家工具技能进 Blender/Unity 精修。

### 独立游戏开发者
一人团队用 skill 链完成从概念图、sprite 动画到天空盒、音效的全流程内容生产。

### 品牌与营销内容
brand-kit、product-shots、video-ads、UGC 技能支持非游戏创意垂直领域的批量内容生产。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 2,929 |
| 总 Forks | 263 |
| 今日新增 | +627 |
| Open Issues | 41 |
| 语言 | Python |
| 创建时间 | 2026-08-12 |

---

## 总结

Scenario Agent Skills 把游戏 AI 生成平台的全部能力封装成 80+ 个符合开放规范的 Agent 技能，配合驱动 ZBrush/Blender/Unity 等本机软件的专家工具，展示了垂类平台在 Agent 时代的全新分发形态。

## 📋 更新记录

### 更新 1 — 2026年11月5日

**更新原因**：Scenario Agent Skills 上榜第二日，Stars 2,109 → 2,302（+193，API 精确数据），Forks 233 → 244（+11），Open Issues 36 → 37。

**最新动态**：
- scenario-blender-blockout 技能新增自行车 kind 与骑手 recipe（#315，11 月 3 日合入），3D 场景资产生成覆盖面继续扩展
- 依赖治理常态化：reportlab 依赖下限升级由 Dependabot 驱动，CI 对 Dependabot PR 标题 lint 自动跳过（#362）
- skills-v0.60.1（10 月 29 日）后保持活跃合入，技能库版本化管理模式运行平稳

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|---------|---------|------|
| 总 Stars | 2,109 | 2,302 | +193 |
| 总 Forks | 233 | 244 | +11 |
| 今日新增 | — | +193 | — |
| Open Issues | 36 | 37 | +1 |

**核心变化概要**：

1. Star +193（+9.2%），连续两天稳定上榜，增速平稳
2. 3D 场景类技能（blender-blockout）持续加料，垂类纵深是核心差异化
3. Forks +11，企业评估型关注与社区贡献并存

### 更新 2 — 2026年11月6日

**更新原因**：Scenario Agent Skills 上榜第三日，Stars 2,302 → 2,929（+627，API 精确数据），Forks 244 → 263（+19），Open Issues 37 → 41。

**最新动态**：
- 单日增量 +627 较昨日 +193 放大三倍以上，「游戏资产生成 Agent Skills」赛道曝光进入加速期
- 官方定位清晰：通过 Scenario MCP 让任意 AI Agent 产出生产级图像/视频/音频/3D，并有专家技能团队驱动 Blender、Maya、ZBrush、Unreal、Unity 工作流
- skills CLI 可将技能装入 70+ Agent，分发面覆盖主流编程代理生态

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|---------|---------|------|
| 总 Stars | 2,302 | 2,929 | +627 |
| 总 Forks | 244 | 263 | +19 |
| 今日新增 | — | +627 | — |
| Open Issues | 37 | 41 | +4 |

**核心变化概要**：

1. 增速三级跳（+224 → +193 → +627），自首日 2,109 起三日涨幅约 39%
2. 垂类（游戏资产/3D）+ MCP 标准化组合卡位清晰，差异化明显
3. Forks +19，游戏工作室型用户开始评估接入
---

*数据来源：GitHub 仓库 (scenario-labs/skills)，2026 年 11 月访问*

*首次分析：2026 年 11 月 4 日 | 最近更新：2026 年 11 月 6 日*

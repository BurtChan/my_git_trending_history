# 项目名称

**HyperFrames** — 用 HTML 编写，渲染为视频，为 AI 智能体而生

- GitHub 仓库：[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes)
- 项目主页：[hyperframes.heygen.com](https://hyperframes.heygen.com)
- 许可证：Apache-2.0
- 开发语言：TypeScript
- 开发者：HeyGen

---

## 项目概述

HyperFrames 是由 AI 视频领域头部企业 HeyGen 推出的开源视频渲染框架，其核心理念极为简洁：用编写网页的方式创建视频。开发者通过 HTML + CSS 定义视频的视觉布局，使用 GSAP、CSS 动画、Lottie、Three.js 等前端动画工具控制时间轴和运动效果，最终由 HyperFrames 引擎将这段"可交互网页"逐帧渲染为确定性的 MP4 视频。无需视频编辑器、无需 React 构建、无需复杂的学习曲线——只要你会写网页，就能制作视频。

项目创建于 2025 年 3 月 27 日，截至 2026 年 6 月已获得 29,783 个 GitHub Star 和 2,804 个 Fork，日增 369 Star，增长势头强劲。这一成绩在视频技术开源项目中极为亮眼，反映了市场对"程序化视频生成"这一范式的强烈兴趣。已知的采用者包括知名开源项目 tldraw 和 TanStack，证明了框架的实用性和可靠性。

HyperFrames 的技术架构清晰而优雅：CLI 工具负责项目初始化、预览和渲染；Core 提供核心抽象；Engine 驱动无头 Chrome 逐帧 seek 动画；Producer 协调编码流程输出 MP4。整个渲染过程是确定性的——相同的输入永远产生相同的输出，这对于版本控制、自动化流水线和 AI 生成的可重复性至关重要。项目还提供了 Catalog（可复用的视频组件库）、Agent Skills（AI 智能体集成）、Studio 编辑器（可视化编辑）和 AWS Lambda 渲染（云端扩展）等配套设施。

---

## 核心功能

### HTML 原生视频创作

HyperFrames 的核心理念是"HTML 即视频"。视频场景就像网页一样组织——用 HTML 元素定义视觉元素，用 CSS 控制样式，用动画库编排时间轴。每个视频项目本质上就是一个 HTML 文件，配合 data 属性控制场景切换、时间节点等元数据。这种 HTML-first 的方式让前端开发者能以最熟悉的工具创作视频。

### 多引擎动画支持

支持多种前端动画方案：GSAP（主推动画库）、CSS Animations/Transitions、Lottie（JSON 动画）、Three.js（3D 场景）、Anime.js 和 WAAPI（Web Animations API）。关键要求是动画必须是"可 seek 的"——能够跳转到任意时间点获取精确状态，这是逐帧渲染的前提。

### 确定性逐帧渲染

渲染引擎在无头 Chrome 中打开 HTML 文档，按照视频帧率逐帧 seek 动画状态，通过 Puppeteer 截取每一帧画面，最终用 FFmpeg 编码为 MP4。这个过程完全确定性，同样的输入产生完全一致的输出，支持精确的版本控制和 CI/CD 集成。

### CLI 工作流

HyperFrames CLI 以非交互式为默认设计——所有输入通过命令行参数传递，输出为纯文本，错误时立即退出。这种设计使 AI 智能体能够可靠地驱动每一条命令，无需处理交互式提示或复杂输出解析。典型流程：`npx hyperframes render --output demo.mp4`。

### AI 智能体集成（Agent Skills）

HyperFrames 提供了专门的 Agent Skills，教会 Claude Code、Cursor、Gemini CLI、Codex 等 AI 编程助手完成完整的视频制作流程：规划视频结构 → 编写有效 HTML → 连接可 seek 动画 → 添加媒体资源 → Lint 检查 → 预览 → 渲染输出。AI 可以直接用自然语言描述视频需求，由智能体完成全部编码工作。

### 组件目录（Catalog）与设计系统（frame.md）

Catalog 提供可复用的视频组件块（如标题动画、过渡效果、数据可视化等），加速视频创作。frame.md 是 HyperFrames 独创的设计系统——它将 Web 端的设计规格"反转"为视频端的规范，生成 DESIGN.md 供 AI 智能体直接读取和运用，让智能体无需猜测就能正确设置视频的尺寸、字体、间距等视觉参数。

### 云端渲染（AWS Lambda）

支持通过 AWS Lambda 进行云端渲染，适合需要批量生产视频或不能在本地运行无头浏览器的场景。结合本地 CLI 开发和云端批量渲染，形成了完整的开发-生产工作流。

---

## 技术栈

| 类别 | 技术 |
|------|------|
| 开发语言 | TypeScript |
| 许可证 | Apache-2.0 |
| 动画引擎 | GSAP（主推）、CSS Animations、Lottie、Three.js、Anime.js、WAAPI |
| 渲染引擎 | 无头 Chrome（Puppeteer） |
| 视频编码 | FFmpeg |
| 云端渲染 | AWS Lambda |
| 核心模块 | @hyperframes/core、@hyperframes/engine、@hyperframes/producer |
| 创作工具 | @hyperframes/studio、@hyperframes/player |
| CLI | hyperframes（npm） |
| 设计系统 | frame.md |
| AI 集成 | Agent Skills（Claude Code、Cursor、Gemini CLI、Codex） |

---

## 项目亮点

### HTML-first，零构建步骤

与 Remotion（React-based 视频框架）形成鲜明对比：HyperFrames 无需构建步骤，直接使用原生 HTML + CSS，开发者无需学习 React 或任何框架特有的 API。一个 HTML 文件就是一个视频项目，用浏览器打开即可预览，用 CLI 即可渲染。这种极简的体验大大降低了视频编程的门槛。

### 确定性输出的工程价值

视频不再是"渲染一次看运气"的黑箱产物，而是如同代码一样可版本控制、可重复构建的确定性产出物。结合 Git 版本管理，视频的每次修改都有完整的变更历史，支持分支、合并、回滚等标准开发工作流。

### AI 原生架构

从 CLI 的非交互式设计到 frame.md 设计系统，再到 Agent Skills 的完整教学流程，HyperFrames 的每个层面都为 AI 智能体驱动做了优化。AI 编程助手不仅能"写"视频，还能"预览"和"渲染"视频，形成完整的闭环。这种深度 AI 集成在视频工具中是首创性的。

### Apache 2.0 宽松许可

与 Remotion 的专有许可不同，HyperFrames 采用 Apache 2.0 许可证，允许商业使用、修改和分发，且不要求衍生作品开源。这对于企业用户和商业产品集成极为友好。

### 知名项目背书

tldraw（流行的白板协作工具）和 TanStack（知名前端工具库家族）等知名开源项目的采用，为 HyperFrames 提供了强有力的技术背书，证明了框架在真实产品中的可靠性。

### 快速增长的生态系统

项目创建仅约 15 个月就积累了近 3 万 Star，日增 369 Star，同时已建立了完整的 NPM 包矩阵（7 个核心包）、在线 Playground（hyperframes.dev）和 Studio 编辑器，生态系统发展速度令人印象深刻。

---

## 应用场景

### 程序化视频生成

开发者通过代码批量生成产品演示、教程、数据报告等视频内容。结合模板和动态数据，实现千人千面的个性化视频，大幅降低视频制作成本。

### AI 智能体视频创作

利用 Claude Code、Cursor 等 AI 编程助手，通过自然语言描述直接生成视频。AI 智能体完成从构思到渲染的全流程，非技术人员也能"说出"一段视频。

### 产品发布与 UI 演示

将产品设计稿或 Figma 导出的 HTML 快速转化为产品展示视频，特别适合 SaaS 产品的功能发布、更新公告等场景。tldraw 的采用正是这一方向的典型案例。

### 社交媒体内容批量生产

结合 AWS Lambda 云端渲染能力，批量生产适配不同平台尺寸和风格的视频内容，实现社交媒体内容的规模化、自动化产出。

### 开发者工具演示视频

为开源项目、API 文档、开发者工具制作交互式演示视频。代码驱动的制作方式与开发者工作流天然契合，版本控制能力保证了文档视频与代码的同步更新。

### 网站到视频（Website-to-Video）

将现有网站页面直接转化为视频，用于产品展示、营销推广。HyperFrames 的 HTML 原生特性使得这一过程极为自然——网页本身就是视频的源代码。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 当前 Star 数 | 29,783 |
| 当前 Fork 数 | 2,804 |
| 日增 Star（2026-06-22） | 369 |
| 项目创建时间 | 2025-03-27 |
| 开源许可 | Apache-2.0 |
| 开发语言 | TypeScript |
| 主要话题标签 | video, html, animation, cli, rendering, deterministic, gsap, ai-agents, ffmpeg |
| 知名采用者 | tldraw、TanStack |

---

## 总结

HyperFrames 代表了视频制作领域的一次重要范式转移——从图形化编辑器的"所见即所得"到代码驱动的"所写即所得"。HeyGen 凭借其在 AI 视频领域的深厚积累，精准地捕捉到了程序化视频生成这一新兴需求，并以 HTML-first 的极简哲学降低了参与门槛。

项目最核心的创新在于将确定性渲染与 AI 智能体深度结合。frame.md 设计系统和 Agent Skills 的引入，使 AI 编程助手能够真正完成视频的全生命周期创作，这是与传统视频工具和 Remotion 等编程视频框架的关键区别。Apache 2.0 许可证的选择也体现了 HeyGen 通过开源构建生态而非封闭变现的战略意图。

近 3 万 Star、日增 369 的增长曲线、tldraw 和 TanStack 等重量级采用者的背书，以及 HeyGen 的品牌加持，使得 HyperFrames 有望成为"程序化视频"这一新品类的标准工具。对于前端开发者和 AI 应用构建者而言，HyperFrames 提供了一条从"写代码"到"做视频"的最短路径。

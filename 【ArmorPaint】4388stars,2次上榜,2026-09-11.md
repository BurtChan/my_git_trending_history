# ArmorPaint 项目分析

## 项目名称

**ArmorPaint** — 开源 3D PBR 纹理绘制软件：直接在 3D 模型表面绘制物理材质，全 GPU 加速的射线追踪笔刷

- **GitHub**: [armory3d/armorpaint](https://github.com/armory3d/armorpaint)
- **许可证**: Zlib（源码），发行版付费

---

## 项目概述

ArmorPaint 是 armory3d 组织（Armory 3D 游戏引擎作者 Lubos Lenco）开发的 **3D PBR（基于物理渲染）纹理绘制软件**。与在 2D 画布上展开 UV 再手绘的传统流程不同，ArmorPaint 让美术直接在 3D 模型表面绘制——笔刷由光线追踪加速，材质通道（Base Color / Normal / Roughness / Metallic 等）实时分离输出，所见即所得。

项目采用「源码开放 + 发行版付费」模式：全部开发在 GitHub 公开进行，但官方预编译二进制在 armorpaint.org 付费下载以支持项目资金。自行编译需要 C++ 工具链（各平台均有详细文档），支持 Windows / Linux / macOS / iOS / Android 甚至 WASM 目标，编译还提供了 c23 `#embed` 数据嵌入等前沿特性支持。

作为一个 2017 年创建、6,173 次提交的长期项目，ArmorPaint 已是 Blender/Substance 之外独立游戏与小团队美术管线的常用选择，今日以 +73 Star 重返 Trending。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| 3D 直接绘制 | 在模型表面直接绘制 PBR 材质，无需在 2D UV 画布间切换 |
| 光线追踪笔刷 | 笔刷投射由 GPU 光线追踪加速，复杂 UV 接缝也能正确落笔 |
| 材质通道输出 | Base Color / Normal / Roughness / Metallic / Opacity / Emissive / Height 多通道分层导出 |
| 程序化材质 | 内置节点式程序化材质与智能材质库 |
| 多平台 | 桌面四平台 + iOS/Android 平板 + WASM 浏览器目标 |
| 本地化 | 提供语言文件生成脚本，支持多语言界面 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | C++（clang 格式化，.clang-format 规范） |
| 渲染 | 自研 GPU 后端（Vulkan/Metal/D3D/WebGPU） |
| 构建 | haxe 工具链（base/make） |
| 仓库结构 | base（引擎核心）/ paint（应用逻辑）双模块 |

---

## 项目亮点

### 光线追踪加速的笔刷体验
笔刷采样通过硬件光线追踪完成，绘制跨 UV 接缝、高密度网格时依然精准，这是它与 2D 图层软件绘制流程拉开代差的核心技术。

### 全平台覆盖包括移动端与 WASM
同一代码库编译到桌面、平板和浏览器（`--target wasm --compile --embed`），美术可以在 iPad 上接续工作流，这在同类 PBR 绘制工具中极为罕见。

### 「源码即产品」的可持续开源
所有开发公开、二进制付费的模式运行 8 年以上（2017-2026），既保证了代码可审计与社区贡献，又为作者提供了持续资金，是垂直工具开源可持续性的范本案例。

---

## 应用场景

### 独立游戏美术管线
Blender 建模 → ArmorPaint 绘制 PBR 纹理 → 游戏引擎导入，全免费（自编译）管线替代 Substance Painter 订阅。

### 影视与动画资产
高精度模型的多通道材质输出直接对接渲染器的 USD/材质工作流。

### 图形编程学习者
C++ 手写 GPU 后端 + 光线追踪笔刷的实现是学习实时渲染工程的优秀教材级代码库。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 4,388 |
| 总 Forks | 519 |
| 今日新增 | +87 |
| 创建时间 | 2017-02-06 |
| 主要语言 | C++ |
| 许可证 | Zlib |

---

## 📋 更新记录

### 更新 1 — 2026 年 9 月 11 日

**再次登上 Trending**。ArmorPaint 1.0 正式版于 9 月 4 日发布，结束八年 Early Access，热度持续发酵。

ArmorPaint 1.0 将核心代码用 C 语言重写，性能大幅提升，可在更大的 3D 资产上交互式绘制、承载更多更高分辨率的纹理层。新版本加入基础雕刻与 UV 编辑系统、蒙皮角色时间轴回放，以及 AI 图像超分与照片转材质生成。图形后端全面支持 Direct3D 12、Vulkan、Metal 与 WebGPU，光追经由 D3D12（Windows）/Vulkan（Linux、Android）/Metal（macOS、iOS）提供。官方称代码库精简到可装进两张 1.44MB 软盘。

| 指标 | 上次记录 | 最新数据 | 变化 |
|---|---|---|---|
| 总 Stars | 4,237 | 4,388 | +151 |
| 总 Forks | 508 | 519 | +11 |

**核心变化**：
- 1.0 正式版发布（2026-09-04），结束 8 年早期访问
- C 语言重写核心，支持更大资产与更多高分辨率纹理层
- 新增雕刻模式、Decimate/Subdivide/Smooth/Bevel 修改器、基础 UV 编辑器
- 新增 Timeline 标签页，支持蒙皮网格动画回放与补间动画
- AI 图像超分与照片转材质；D3D12/Vulkan/Metal/WebGPU 图形后端

---

## 总结

ArmorPaint 用 8 年的持续打磨证明「源码开放 + 发行版付费」可以让专业级 3D 绘制工具长期存活，光线追踪笔刷带来的直接绘制体验是它在 Blender 与商业软件夹缝中的立身之本。

---

*数据来源：GitHub 仓库 (armory3d/armorpaint)，2026 年 9 月访问*
*首次分析：2026-09-10 | 最近更新：2026-09-11*

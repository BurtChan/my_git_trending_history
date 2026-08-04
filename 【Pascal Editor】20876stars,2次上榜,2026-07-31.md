# Pascal Editor 项目分析

## 一句话总结

Pascal Editor 是一款基于 React Three Fiber 和 WebGPU 构建的开源 3D 建筑编辑器，支持在浏览器中创建、编辑和分享 3D 建筑项目，面向建筑师、室内设计师和房地产开发者。

---

## 基本信息

| 属性 | 详情 |
|------|------|
| **项目名称** | Pascal Editor |
| **GitHub 地址** | https://github.com/pascalorg/editor |
| **官方站点** | https://editor.pascal.app |
| **Stars** | 9,593 |
| **Forks** | 1,235 |
| **许可证** | MIT License |
| **主要语言** | TypeScript |
| **作者** | Aymeric Rabot, Wassim Samad |
| **组织** | pascalorg |
| **创建时间** | 2025 年 10 月 |
| **NPM 包** | @pascal-app/core, @pascal-app/viewer |

---

## 解决什么问题

传统的 3D 建筑建模工具（如 SketchUp、Revit、AutoCAD）大多为桌面端原生应用，安装成本高、学习曲线陡峭，且协作与分享困难。Pascal Editor 的核心目标是提供一个**完全运行在浏览器中的 3D 建筑编辑器**，无需安装任何软件，即可完成从绘制墙体、放置门窗、创建楼板到生成屋顶的完整建筑设计流程，并支持一键分享项目。

该项目将复杂的 3D 建筑建模能力以 Web 应用的形式交付，大幅降低了建筑设计和空间规划的门槛。

---

## 核心功能

### 建筑建模

- **墙体绘制** -- 通过 WallTool 交互式绘制墙体，支持厚度调整，自动处理墙角斜接（mitering）
- **楼板创建** -- 通过 SlabTool 绘制多边形楼板，自动生成楼层几何体
- **天花板生成** -- 自动为每个楼层生成天花板结构
- **屋顶生成** -- 根据楼层轮廓自动生成屋顶几何体
- **区域划分** -- 通过 ZoneTool 在楼层内划分功能区域（如客厅、卧室、厨房）

### 元素放置

- **门窗放置** -- 在墙体上自动开洞并放置门、窗等建筑构件（通过 CSG 布尔运算实现）
- **灯具放置** -- 在天花板或楼板上放置灯具
- **家具/设备放置** -- 在楼板上放置家具和固定设备
- **碰撞检测** -- 通过 SpatialGridManager 进行放置验证，防止物体重叠

### 场景管理

- **层级结构** -- 支持 Site -> Building -> Level 多级建筑层级
- **楼层显示模式** -- 支持堆叠（Stacked）、展开（Exploded）、单独（Solo）三种楼层展示方式
- **3D 扫描参考** -- 支持导入 3D 扫描数据作为设计参考
- **2D 参考图** -- 支持导入 2D 平面图作为设计底图
- **撤销/重做** -- 50 步历史记录，支持完整的操作回退

### 编辑交互

- **选择工具** -- SelectTool 支持层级化选择导航（Site -> Building -> Level -> Zone -> Items）
- **相机聚焦** -- 点击节点自动聚焦相机到目标对象
- **事件系统** -- 基于 mitt 的类型化事件总线，支持节点点击、悬浮、右键菜单等交互

---

## 技术架构

项目采用 Turborepo monorepo 架构，分为三个主要包：

```
editor-v2/
├── apps/
│   └── editor/          # Next.js 应用（编辑器 UI）
├── packages/
│   ├── core/            # Schema 定义、状态管理、系统逻辑
│   └── viewer/          # 3D 渲染组件
```

### 职责分离

| 包 | 职责 |
|------|------|
| **@pascal-app/core** | 节点 Schema 定义、场景状态管理（Zustand）、几何生成系统、空间查询、事件总线 |
| **@pascal-app/viewer** | 基于 React Three Fiber 的 3D 渲染、默认相机/控制器、后处理效果 |
| **apps/editor** | UI 组件、编辑工具、自定义交互行为、编辑器专用系统 |

### 核心设计模式

**节点系统（Node System）**

所有建筑元素以 Node 形式组织，存储在扁平字典中（非嵌套树），通过 `parentId` 和 `children` 数组维护层级关系：

```
Site
└── Building
    └── Level
        ├── Wall -> Item（门、窗）
        ├── Slab
        ├── Ceiling -> Item（灯具）
        ├── Roof
        ├── Zone
        ├── Scan（3D 参考扫描）
        └── Guide（2D 参考图）
```

**脏标记系统（Dirty Nodes）**

节点变更时被标记为"脏"（dirty），系统在每帧（useFrame）中仅处理脏节点的几何体重建，实现高效的增量更新。

**场景注册表（Scene Registry）**

将节点 ID 映射到 Three.js Object3D 对象，系统可直接访问 3D 对象而无需遍历场景图。

**渲染器-系统分离**

渲染器（Renderer）是创建占位 mesh/group 的 React 组件，系统（System）是在渲染循环中更新几何体的 React 组件。两者解耦，各司其职。

### 数据流

```
用户操作（点击、拖拽）
    -> 工具处理器（Tool Handler）
    -> useScene.createNode() / updateNode()
    -> 节点添加/更新 + 标记为脏
    -> React 重新渲染 NodeRenderer
    -> useRegistry() 注册 3D 对象
    -> System 检测脏节点（useFrame）
    -> 通过 sceneRegistry 更新几何体
    -> 清除脏标记
```

---

## 技术栈

| 技术 | 用途 |
|------|------|
| **React 19** | UI 框架 |
| **Next.js 16** | 应用框架（SSR/路由） |
| **Three.js** | 3D 渲染引擎（WebGPU 渲染器） |
| **React Three Fiber** | React 声明式 Three.js 绑定 |
| **Drei** | R3F 实用工具库 |
| **Zustand** | 状态管理 |
| **Zundo** | 撤销/重做（50 步历史） |
| **Zod** | Schema 验证 |
| **three-bvh-csg** | CSG 布尔运算（墙体开洞） |
| **mitt** | 类型化事件总线 |
| **Turborepo** | Monorepo 管理 |
| **Bun** | 包管理器与运行时 |
| **IndexedDB** | 场景数据持久化 |

---

## 典型使用场景

1. **建筑设计** -- 建筑师在浏览器中快速绘制建筑平面图并生成 3D 模型，用于概念设计和方案验证
2. **室内设计** -- 室内设计师创建房间布局、划分功能区域、放置家具，直观展示设计方案
3. **房地产展示** -- 开发者为待售楼盘创建 3D 户型图，通过链接直接分享给潜在买家
4. **装修规划** -- 业主导入 3D 扫描数据作为参考，在现有空间基础上规划装修方案
5. **协作设计** -- 团队成员通过分享链接实时查看和讨论设计方案，无需安装专业软件
6. **教育用途** -- 建筑和设计专业学生使用免费工具学习空间设计和建筑建模

---

## 项目亮点

- **纯 Web 实现** -- 完全在浏览器中运行，无需安装任何桌面软件，打开即用
- **WebGPU 渲染** -- 采用下一代 WebGPU 渲染器，性能优于传统 WebGL
- **CSG 布尔运算** -- 使用 three-bvh-csg 实现精确的墙体开洞（门窗），这是 Web 端较少见的实时 CSG 能力
- **模块化架构** -- core/viewer/editor 三层分离，core 和 viewer 可作为独立 NPM 包被其他项目复用
- **脏标记优化** -- 增量几何更新机制确保仅重建变化的节点，保障大规模场景的编辑流畅度
- **NPM 生态** -- @pascal-app/core 和 @pascal-app/viewer 已发布到 NPM，开发者可直接集成到自己的 Web 3D 项目中

---

## 📋 更新记录

### 更新 1 — 2026 年 7 月 31 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：Pascal Editor 实现了显著增长，Star 数从 9,593 增长至约 20,876（+11,283），翻倍增长。作为基于 React Three Fiber + WebGPU 的浏览器端 3D 建筑编辑器，Pascal Editor 通过 core/viewer/editor 三层分离架构，实现了从墙体绘制到门窗放置的完整建筑设计流程。项目在社区中活跃度持续走高，已有超过 2,600 个 Fork，活跃 Discord 社区，editor.pascal.app 展示了大量社区创作的 3D 建筑项目。支持 50 步撤销/重做、碰撞吸附网格、爆炸视图等功能，全部在浏览器端本地运行，无需下载或注册。MIT 开源许可证。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 9,593 | 20,876 | +11,283 |
| 总 Forks | 2,629 | 2,629 | — |

**核心变化概要**：
- Star 数翻倍增长，从约 9.6K 增至 20.9K，社区关注度显著提升
- 浏览器端 3D 建筑编辑器定位得到市场验证，Fork 数增长至 2,600+
- editor.pascal.app 展示了丰富的社区项目（别墅、学校、集装箱住宅等）
- 核心架构（Turborepo 三层分离）和增量几何更新机制持续优化

---

## 一句话总结

> Pascal Editor 是一款基于 React Three Fiber + WebGPU 的开源浏览器端 3D 建筑编辑器，通过模块化的节点系统、CSG 布尔运算和增量几何更新机制，实现了从墙体绘制到门窗放置的完整建筑设计流程，并以 core/viewer/editor 三层分离的架构提供了高度可复用的 3D 建筑渲染能力。

---

*数据来源：GitHub 仓库 README 及 API（2026 年 4 月访问）*

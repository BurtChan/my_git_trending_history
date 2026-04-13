# BlenderMCP 项目分析

## 项目概述

BlenderMCP 是一个将 Blender 3D 建模软件与 Claude AI 通过 Model Context Protocol（MCP）连接的集成工具。它让 Claude 能够直接控制和操作 Blender，实现自然语言驱动的 3D 建模、场景创建和素材管理。项目由两个核心组件构成：运行在 Blender 内部的插件（Addon）和实现 MCP 协议的外部服务器。

## 核心功能

- **双向通信**：通过基于 TCP Socket 的 JSON 协议实现 Claude 与 Blender 的实时交互
- **3D 对象操控**：创建、修改、删除 Blender 中的 3D 对象，支持完整的场景编辑
- **材质控制**：应用和修改材质、颜色，实现自然语言描述的材质调整
- **场景检查**：获取当前 Blender 场景的详细信息，包括视口截图理解
- **代码执行**：在 Blender 中运行任意 Python 代码，实现高级自动化
- **3D 资产集成**：支持 Poly Haven（HDRI/纹理/模型）、Sketchfab（模型搜索下载）、Hyper3D Rodin（AI 生成 3D 模型）、Hunyuan3D
- **远程主机支持**：可通过环境变量配置连接远程 Blender 实例

## 技术栈

- **语言**：Python
- **协议**：Model Context Protocol（MCP）
- **通信方式**：TCP Socket + JSON 协议
- **3D 引擎**：Blender 3.0+
- **包管理**：uv（Python 包管理器）
- **资产源**：Poly Haven API、Sketchfab、Hyper3D Rodin、Hunyuan3D
- **集成平台**：Claude Desktop、Claude Code、Cursor、VS Code
- **许可证**：开源

## 项目亮点

- **自然语言建 3D**：用一句话描述就能生成完整的 3D 场景，极大地降低了 3D 创作门槛
- **丰富的资产生态**：集成多个 3D 资产平台，从模型搜索到 HDRI 环境一应俱全
- **AI 生成 3D 模型**：通过 Hyper3D Rodin 和 Hunyuan3D 实现文本/图片转 3D 模型
- **多 IDE 支持**：无缝集成 Claude Desktop、Claude Code、Cursor 和 VS Code
- **视口截图理解**：Claude 能查看 Blender 视口截图，更好理解场景状态

## 应用场景

- **快速原型设计**：用自然语言快速创建 3D 场景原型，加速设计迭代
- **游戏开发**：快速搭建游戏场景、放置道具、调整光照
- **建筑可视化**：通过对话创建室内外场景，调整材质和光照
- **教育演示**：用对话创建 3D 教学模型和动画
- **内容创作**：为视频、动画制作快速生成场景和道具
- **参考图转 3D**：给一张参考图片，自动生成对应的 Blender 场景

## Star 数据

- 总 Star 数：19,154
- Fork 数：1,862
- 今日增长：+215

## 总结

BlenderMCP 是 AI + 3D 创作领域的一个突破性项目。它通过 MCP 协议将大语言模型的能力延伸到 3D 建模领域，让不会 Blender 的人也能通过自然语言创建 3D 内容。对于专业 3D 艺术家，它提供了快速原型和场景搭建的新方式。随着 AI 生成 3D 模型能力的提升，BlenderMCP 有望成为 3D 创作工作流中的核心工具。

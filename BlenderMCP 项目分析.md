# BlenderMCP 项目分析

## 项目名称与地址

**BlenderMCP - Blender Model Context Protocol Integration**

项目地址：https://github.com/ahujasid/blender-mcp

作者：Siddharth (ahujasid)

Discord 社区：项目提供官方 Discord 频道用于反馈和灵感分享

## 项目概述

BlenderMCP 是一个将 Blender 3D 建模软件与 Claude AI 通过 Model Context Protocol（MCP）连接的集成工具。它让 Claude 能够直接控制和操作 Blender，实现自然语言驱动的 3D 建模、场景创建和素材管理。这一集成使得用户可以用日常语言描述来创建和编辑 3D 场景，极大地降低了 3D 创作的门槛。

项目由两个核心组件构成：运行在 Blender 内部的插件（addon.py）和实现 MCP 协议的外部服务器。两者通过基于 TCP Socket 的 JSON 协议进行双向通信。当前版本为 1.5.5，支持 Blender 3.0+ 和 Python 3.10+。

BlenderMCP 是第三方集成工具，非 Blender 官方出品。项目特别声明没有官方网站，提醒用户注意甄别非官方站点。

## 核心功能

### 双向通信

通过基于 TCP Socket 的 JSON 协议实现 Claude 与 Blender 的实时双向交互。命令以 JSON 对象发送（包含 type 和 params），响应也是 JSON 对象（包含 status 和 result/message）。默认端口为 9876。

### 3D 对象操控

创建、修改和删除 Blender 中的 3D 对象，支持完整的场景编辑操作：

- 创建基础几何体（立方体、球体、圆柱体、平面等）
- 变换操作（移动、旋转、缩放）
- 对象层级管理（父子关系、分组）
- 布尔运算和修改器应用

### 材质与外观控制

通过自然语言描述应用和修改材质、颜色，实现逼真的视觉效果：

- 设置物体颜色和材质属性（金属度、粗糙度等）
- 创建和分配新材质
- 调整光照参数
- 实现特定风格的外观（如"让这辆车变成红色金属漆"）

### 场景检查

获取当前 Blender 场景的详细信息，包括：

- 场景中的所有对象列表和层级
- 每个对象的位置、旋转、缩放
- 使用的材质和纹理
- **视口截图理解**：Claude 能查看 Blender 视口截图，更好理解当前场景状态（v1.5.5 新增）

### 代码执行

在 Blender 中运行任意 Python 代码，实现高级自动化操作。此功能强大但需要注意安全风险，建议在使用前保存工作。

### 3D 资产集成

集成了多个 3D 资产平台，提供丰富的素材资源：

- **Poly Haven**：通过 API 获取高质量的 HDRI 环境贴图、纹理贴图和 3D 模型（需要在 Blender 插件中启用复选框）
- **Sketchfab**：搜索和下载在线 3D 模型库中的模型（v1.5.5 新增）
- **Hyper3D Rodin**：AI 生成 3D 模型，通过文本描述或参考图片生成（免费试用密钥每日有限额，可获取自己的密钥）
- **Hunyuan3D**：支持腾讯混元 3D 模型生成（v1.5.5 新增）

### 远程主机支持

通过环境变量配置连接远程 Blender 实例：

```bash
export BLENDER_HOST='host.docker.internal'
export BLENDER_PORT=9876
```

## 技术栈

- **核心语言**：Python
- **协议**：Model Context Protocol（MCP）
- **通信方式**：TCP Socket + JSON 协议（默认端口 9876）
- **3D 引擎**：Blender 3.0+
- **Python 版本**：3.10+
- **包管理**：uv（Astral 出品的高性能 Python 包管理器）
- **MCP 服务器**：通过 uvx 运行 blender-mcp 包
- **资产源**：Poly Haven API、Sketchfab、Hyper3D Rodin、Hunyuan3D
- **集成平台**：Claude Desktop、Claude Code CLI、Cursor、Visual Studio Code
- **遥测**：匿名工具使用统计（可通过环境变量或设置完全禁用）

## 安装与配置

### 前置条件

- Blender 3.0 或更新版本
- Python 3.10 或更新版本
- uv 包管理器

### 安装 uv 包管理器

```bash
# macOS
brew install uv

# Windows（PowerShell）
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"

# Windows 添加到用户 PATH
$localBin = "$env:USERPROFILE\.local\bin"
$userPath = [Environment]::GetEnvironmentVariable("Path", "User")
[Environment]::SetEnvironmentVariable("Path", "$userPath;$localBin", "User")
```

### 安装 Blender 插件

1. 从 GitHub 仓库下载 `addon.py` 文件
2. 打开 Blender
3. 进入 Edit > Preferences > Add-ons
4. 点击"Install..."并选择下载的 `addon.py` 文件
5. 勾选"Interface: Blender MCP"旁边的复选框启用插件

### 配置 Claude Desktop

编辑 Claude Desktop 配置文件（Claude > Settings > Developer > Edit Config > claude_desktop_config.json）：

```json
{
    "mcpServers": {
        "blender": {
            "command": "uvx",
            "args": [
                "blender-mcp"
            ]
        }
    }
}
```

### 配置 Claude Code CLI

```bash
claude mcp add blender uvx blender-mcp
```

### 配置 Cursor

- **Mac**：Settings > MCP，粘贴相同的 JSON 配置（全局或项目级别）
- **Windows**：Settings > MCP > Add Server，需要使用 cmd 包装：

```json
{
    "mcpServers": {
        "blender": {
            "command": "cmd",
            "args": ["/c", "uvx", "blender-mcp"]
        }
    }
}
```

### 配置 Visual Studio Code

VS Code 中点击 Install 按钮即可一键安装 blender-mcp 扩展。

## 使用方法

### 启动连接

1. 在 Blender 中打开 3D 视口侧边栏（按 N 键）
2. 找到"BlenderMCP"标签页
3. 如需使用 Poly Haven 资产，勾选对应复选框（可选）
4. 点击"Connect to Claude"按钮
5. 确保 MCP 服务器已在终端中运行

### 示例命令

以下是可以对 Claude 说的一些示例：

- "Create a low poly scene in a dungeon, with a dragon guarding a pot of gold"
- "Create a beach vibe using HDRIs, textures, and models like rocks and vegetation from Poly Haven"
- 给一张参考图片，让它创建对应的 Blender 场景
- "Generate a 3D model of a garden gnome through Hyper3D"
- "Get information about the current scene, and make a threejs sketch from it"
- "Make this car red and metallic"
- "Create a sphere and place it above the cube"
- "Make the lighting like a studio"
- "Point the camera at the scene, and make it isometric"

### 环境变量配置

| 变量名 | 说明 | 默认值 |
|--------|------|--------|
| BLENDER_HOST | Blender Socket 服务器主机地址 | localhost |
| BLENDER_PORT | Blender Socket 服务器端口 | 9876 |

## 遥测控制

BlenderMCP 收集匿名使用数据以改进工具。可通过以下方式控制：

1. **Blender 内**：Edit > Preferences > Add-ons > Blender MCP，取消勾选遥测同意复选框
2. **环境变量**：完全禁用所有遥测

```json
{
    "mcpServers": {
        "blender": {
            "command": "uvx",
            "args": ["blender-mcp"],
            "env": {
                "DISABLE_TELEMETRY": "true"
            }
        }
    }
}
```

## 项目亮点

- **自然语言建 3D**：用一句话描述就能生成完整的 3D 场景，极大降低 3D 创作门槛。非专业用户也能快速创建 3D 内容
- **丰富的资产生态**：集成 Poly Haven、Sketchfab、Hyper3D Rodin、Hunyuan3D 四大资产平台，从模型搜索到 HDRI 环境一应俱全
- **AI 生成 3D 模型**：通过 Hyper3D Rodin 和 Hunyuan3D 实现文本/图片转 3D 模型，这是 3D 创作的前沿技术
- **多 IDE 支持**：无缝集成 Claude Desktop、Claude Code、Cursor 和 VS Code 四大主流 AI 编码平台
- **视口截图理解**：Claude 能查看 Blender 视口截图，精准理解场景当前状态，做出更准确的编辑决策
- **活跃维护**：当前版本 1.5.5，持续添加新功能（Sketchfab、Hunyuan3D 等为近期新增）
- **远程支持**：可连接远程 Blender 实例，适合团队协作和云端渲染场景

## 应用场景

- **快速原型设计**：用自然语言快速创建 3D 场景原型，加速设计迭代。如"创建一个带光源的工作室场景"
- **游戏开发**：快速搭建游戏场景、放置道具、调整光照。如"创建一个低多边形森林场景"
- **建筑可视化**：通过对话创建室内外场景，调整材质和光照。如"创建一个现代客厅，木质地板，大面积窗户"
- **教育演示**：用对话创建 3D 教学模型和动画，降低教学准备时间
- **内容创作**：为视频、动画制作快速生成场景和道具
- **参考图转 3D**：给一张参考图片，自动生成对应的 Blender 场景，适合设计概念可视化
- **Three.js 开发辅助**：在 Blender 中创建场景后导出为 Three.js 可用的格式

## Star 数据

- 总 Star 数：19,154
- Fork 数：1,862
- 今日增长：+215
- 当前版本：1.5.5
- 支持平台：Claude Desktop、Claude Code、Cursor、VS Code

## 总结

BlenderMCP 是 AI + 3D 创作领域的一个突破性项目。它通过 MCP 协议将大语言模型的能力延伸到 3D 建模领域，让不会 Blender 操作的人也能通过自然语言创建 3D 内容。项目架构清晰——Blender 插件负责接收命令和执行操作，MCP 服务器负责协议翻译和连接管理——两者通过简洁的 JSON over TCP 协议通信。

对于专业 3D 艺术家，BlenderMCP 提供了快速原型和场景搭建的新方式，可以显著提升工作效率。集成四大资产平台（Poly Haven、Sketchfab、Hyper3D Rodin、Hunyuan3D）的策略非常务实，让用户可以一站式获取所需资源。支持多个 AI 平台（Claude Desktop、Claude Code、Cursor、VS Code）的集成也展现了项目的开放性和实用性。随着 AI 生成 3D 模型能力的不断提升，BlenderMCP 有望成为 3D 创作工作流中的核心工具。

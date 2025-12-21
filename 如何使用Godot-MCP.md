# 如何使用Godot MCP

Godot MCP是一个模型上下文协议（MCP）服务器，允许AI助手直接与Godot游戏引擎交互。以下是详细的使用指南：

## 1. 安装与配置

### 安装步骤：
```bash
git clone https://github.com/Coding-Solo/godot-mcp.git
cd godot-mcp
npm install
npm run build
```

### 配置AI助手：
根据你使用的AI助手，在相应配置文件中添加MCP服务器设置：

**对于Cline**，在配置文件中添加：
```json
{
  "mcpServers": {
    "godot": {
      "command": "node",
      "args": ["/absolute/path/to/godot-mcp/build/index.js"],
      "env": {
        "DEBUG": "true"
      },
      "disabled": false,
      "autoApprove": [
        "launch_editor",
        "run_project",
        "get_debug_output",
        // ... 其他工具
      ]
    }
  }
}
```

**对于Cursor**，可以通过UI或项目配置文件`.cursor/mcp.json`添加。

## 2. 核心功能

Godot MCP提供了14个强大的工具：

1. **项目管理**：
   - `launch_editor` - 启动Godot编辑器
   - `run_project` - 运行Godot项目
   - `get_project_info` - 获取项目信息
   - `list_projects` - 列出目录中的项目

2. **调试工具**：
   - `get_debug_output` - 获取调试输出
   - `stop_project` - 停止运行的项目
   - `get_godot_version` - 获取Godot版本

3. **场景操作**：
   - `create_scene` - 创建新场景
   - `add_node` - 向场景添加节点
   - `load_sprite` - 加载精灵到Sprite2D节点
   - `save_scene` - 保存场景
   - `export_mesh_library` - 导出网格库

4. **UID管理**（适用于Godot 4.4+）：
   - `get_uid` - 获取文件UID
   - `update_project_uids` - 更新项目UID引用

## 3. 使用示例

配置完成后，你可以使用自然语言提示AI助手执行操作：

```
"Launch the Godot editor for my project at /path/to/project"

"Run my Godot project and show me any errors"

"Create a new scene with a Player node in my Godot project"

"Add a Sprite2D node to my player scene and load the character texture"

"Export my 3D models as a MeshLibrary for use with GridMap"
```

## 4. 技术优势

- **无临时文件**：使用捆绑的GDScript处理复杂操作，保持系统清洁
- **统一接口**：所有操作通过标准化的MCP接口进行
- **实时反馈**：AI助手可以直接看到操作结果，形成有效的反馈循环
- **安全设计**：路径验证和错误处理确保操作安全

这种设计使得AI助手能够真正"理解"和操作Godot项目，而不仅仅是生成代码建议，大大提升了开发效率。
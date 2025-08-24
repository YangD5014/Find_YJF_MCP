# YJF_MCP - 杨建飞位置查询MCP服务器

## 项目简介

YJF_MCP 是一个基于 Model Context Protocol (MCP) 的服务器，专门用于查询和获取用户 "杨建飞 (Yang Jianfei)" 的位置信息。该服务器提供了一个简洁的接口，可以通过 MCP 协议与各种客户端进行通信，获取最新的位置记录。

## 功能特性

- 📍 **位置查询**: 获取杨建飞用户的最新位置信息
- 🔄 **实时数据**: 支持获取最新的位置记录
- 📊 **灵活配置**: 可自定义查询参数（用户ID、记录数量限制）
 🔌 **MCP协议**: 基于 FastMCP 框架，支持标准 MCP 协议通信
- 🛡️ **安全可靠**: 通过数据库查询确保数据安全性

## 技术栈

- **Python 3.x**: 主要开发语言
- **FastMCP**: MCP 服务器框架
- **数据库**: 支持位置数据存储和查询
- **MCP Protocol**: Model Context Protocol 通信协议

## 安装说明

### 前置要求

- Python 3.8 或更高版本
- pip 包管理器

### 安装步骤

1. **克隆项目**
   ```bash
   cd /Users/yangjianfei/Documents/HBuilderProjects/LOC/YJF_MCP
   ```

2. **安装依赖**
   ```bash
   pip install -r requirements.txt
   # 或者使用 uv（推荐）
   uv sync
   ```

3. **配置数据库**
   - 确保数据库连接配置正确
   - 检查 `user_location.py` 中的数据库连接参数

## 使用方法

### 启动 MCP 服务器

```bash
# 使用 stdio 传输模式
python -m src.yjf_mcp

# 或者直接运行主模块
python src/yjf_mcp/__init__.py
```

### MCP 工具使用

该 MCP 服务器提供了一个主要工具：

#### `get_user_latest_location`

获取杨建飞用户的最新位置记录。

**参数：**
- `user_id` (int, 可选): 用户ID，默认为 1
- `limit` (int, 可选): 返回记录数量限制，默认为 1

**返回值：**
- JSON 格式的位置信息字符串

**使用示例：**
```python
# 获取默认用户（ID=1）的最新位置
result = get_user_latest_location()

# 获取指定用户的最新3条位置记录
result = get_user_latest_location(user_id=1, limit=3)
```

### 返回数据格式

位置信息包含以下字段：
```json
{
  "user_id": 1,
  "latitude": 39.9042,
  "longitude": 116.4074,
  "address": "北京市朝阳区xxx街道",
  "timestamp": "2024-01-01 12:00:00",
  "accuracy": 10.5
}
```

## 项目结构

```
YJF_MCP/
├── src/
│   └── yjf_mcp/
│       ├── __init__.py          # 主入口文件，MCP服务器配置
│       └── user_location.py     # 位置查询逻辑实现
├── pyproject.toml              # 项目配置文件
├── requirements.txt            # Python依赖
├── README.md                  # 项目说明文档
└── .gitignore                 # Git忽略文件
```

## 配置说明

### 数据库配置

在 `user_location.py` 中配置数据库连接参数：
- 数据库主机地址
- 数据库端口
- 数据库名称
- 用户名和密码

### MCP 服务器配置

在 `__init__.py` 中可以配置：
- 服务器名称
- 传输模式（stdio、sse等）
- 工具注册和权限设置

## 开发说明

### 添加新工具

1. 在 `__init__.py` 中添加新的工具函数
2. 使用 `@mcp.tool()` 装饰器注册工具
3. 实现工具逻辑并返回格式化结果

### 扩展功能

- 支持更多用户的位置查询
- 添加位置历史记录查询
- 集成地图服务API
- 添加位置分析和统计功能

## 故障排除

### 常见问题

1. **导入错误**: 确保使用相对导入（`.user_location`）
2. **数据库连接失败**: 检查数据库配置和网络连接
3. **MCP协议错误**: 确保客户端和服务器版本兼容

### 调试方法

```bash
# 启用详细日志
export PYTHONPATH=/path/to/src
python -m src.yjf_mcp --debug
```

## 许可证

本项目采用 MIT 许可证。详见 [LICENSE](LICENSE) 文件。

## 贡献指南

欢迎提交 Issue 和 Pull Request 来改进项目！

## 联系方式

如有问题或建议，请通过以下方式联系：
- 项目 Issues: [GitHub Issues](https://github.com/yourusername/YJF_MCP/issues)
- 邮箱: your-email@example.com

---

**注意**: 本项目专门为杨建飞用户的位置查询而设计，请确保在使用前已获得相关用户的授权和同意。
# YJF_MCP - 杨建飞位置查询MCP服务器

## 项目简介

YJF_MCP 是一个基于 Model Context Protocol (MCP) 的服务器，专门用于查询和获取用户 "杨建飞 (Yang Jianfei)" 的位置信息。该服务器提供了一个简洁的接口，可以通过 MCP 协议与各种客户端进行通信，获取最新的位置记录。

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

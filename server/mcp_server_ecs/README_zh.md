# ECS MCP Server 

## 版本信息
v0.1.0

## 产品描述

ECS MCP Server 是一个模型上下文协议(Model Context Protocol)服务器，为MCP客户端(如Claude Desktop)提供与火山引擎ECS服务交互的能力。可以基于自然语言对云端实例资源进行全链路管理，支持实例、镜像、地域、可用区、可用资源、系统事件的查询操作，实现ECS资源的高效管理。

## 分类
云服务器

## 功能

- 查询实例信息
- 查询事件信息
- 查询地域信息

## 可用工具

- `describe_instances`: [查询实例列表](https://www.volcengine.com/docs/6396/70466)
- `describe_images`: [查询镜像列表](https://www.volcengine.com/docs/6396/70808)
- `describe_instance_types`: [查询实例规格列表](https://www.volcengine.com/docs/6396/92769)
- `describe_available_resource`: [查询可用资源](https://www.volcengine.com/docs/6396/76279)
- `describe_system_events`: [查询系统事件](https://www.volcengine.com/docs/6396/129399)
- `describe_regions`: [查询地域列表](https://www.volcengine.com/docs/6396/1053194)
- `describe_zones`: [查询可用区列表](https://www.volcengine.com/docs/6396/120518)

## 使用指南

### 前置准备
- Python 3.12+
- UV

**Linux/macOS:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows:**
```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### 安装
克隆仓库:
```bash
git clone https://github.com/volcengine/mcp-server/tree/main/mcp_server_ecs.git
```

### 使用方法
启动服务器:

#### UV
```bash
cd mcp_server_ecs
uv run mcp-server-ecs

# 使用sse模式启动(默认为stdio)
uv run mcp-server-ecs -t sse
```

使用客户端与服务器交互:
```
Claude Desktop | Cline | Cursor | Trae | ...
```

## 配置

MCP服务器的主要配置文件位于:

```
src/mcp_server_ecs/conf/settings.toml
src/mcp_server_ecs/conf/.secrets.toml
```

此配置文件包含服务器的日志记录和火山引擎账户AK|SK配置

### 环境变量

以下环境变量可用于配置MCP服务器:

| 环境变量 | 描述 | 默认值 |
|----------|------|--------|
| `FASTMCP_PORT` | MCP server监听端口 | `8000` |
| `VOLC_ACCESSKEY` | 火山引擎账号ACCESSKEY | - |
| `VOLC_SECRETKEY` | 火山引擎账号SECRETKEY | - |
| `VOLC_REGION` | 火山引擎资源region | - |
| `VOLC_ENDPOINT` | 火山引擎endpoint | - |

例如，在启动服务器前设置这些环境变量:

```bash
export FASTMCP_PORT=8000
export VOLC_ACCESSKEY={ak}
export VOLC_SECRETKEY={sk}
export VOLC_REGION={sk}
export VOLC_ENDPOINT={endpoint}

```

### uvx 启动
```json
{
    "mcpServers": {
        "mcp-server-ecs": {
            "command": "uvx",
            "args": [
            "--from",
            "git+https://github.com/volcengine/mcp-server#subdirectory=server/mcp_server_ecs",
            "mcp-server-ecs"
          ],
            "env": {
                "VOLC_ACCESSKEY": "",
                "VOLC_SECRETKEY": "",
                "VOLC_ENDPOINT": "",
                "FASTMCP_PORT": ""
            }
        }
    }
}

## 示例
### Cursor
![Image](https://lf3-beecdn.bytetos.com/obj/ies-fe-bee-upload/bee_prod/biz_950/tos_333f0ad0f93c311bae4259ce2ab9022c.jpg)
![Image](https://lf3-beecdn.bytetos.com/obj/ies-fe-bee-upload/bee_prod/biz_950/tos_49abb4af5fb42f55052558867daff3d6.jpg)


# 证书
MIT

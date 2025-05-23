# Volc Mongo SDK MCP Server 
[https://www.volcengine.com/product/mongodb]

## 版本信息
v1

## 产品描述
火山 mongo 管控面 sdk 的 mcp server，使客户可以自然语言的方式调用SDK

## 分类

#文档型数据库MongoDB

## 标签
#存储#数据库#文档型#MongoDB
## Tools

### list_db_instances
#### 详细描述:
获取MongoDB实例列表和数量
### db_instance_detail
#### 详细描述:
返回MongoDB实例的详情信息
### list_db_instance_backups
#### 详细描述:
获取MongoDB实例备份信息列表
### list_db_instance_params
#### 详细描述:
获取MongoDB实例参数列表
### describe_slow_log
#### 详细描述:
获取MongoDB慢日志列表


## 可适配平台  
可以使用 cline, cursor, claude desktop 或支持MCP server调用的的其他终端


## 鉴权方式  
从 volcengine 管理控制台获取 volcengine 访问密钥 ID、秘密访问密钥和区域

## 安装部署  

### 系统依赖
- 安装 Python 3.10 或者更高版本
- 安装 uv 
  - 如果是linux系统 
  ```
  curl -LsSf https://astral.sh/uv/install.sh | sh
  ```
  - 如果是window系统 
  ```
  powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
  ```
- 同步依赖项并更uv.lock:
  ```bash
  uv sync
  ```
- 构建cmp server:
  ```bash
  uv build
  ```
### 使用 Claude Desktop

On MacOS: `~/Library/Application\ Support/Claude/claude_desktop_config.json`
On Windows: `%APPDATA%/Claude/claude_desktop_config.json`

<details>
  <summary> Servers Configuration </summary>

```json
{
  "mcpServers": {
    "mongo_mcp_server": {
      "disabled": false,
      "command": "uvx",
      "args": [
        "--directory",
        "/<path to mcp-servers>/mcp-servers/src/git/mongodb-mgr-sdk-mcp-server/src/mcp_server_mongodb/",
        "run",
        "server.py"
      ],
      "env": {
        "VOLC_ACCESSKEY": "your-access-key-id",
        "VOLC_SECRETKEY": "your-access-key-secret",
        "VOLC_REGION": "VOLC_REGION"
      },
      "transportType": "stdio"
    }
  }
}
```

</details>

### 使用 UVX

```json
{
    "mcpServers": {
        "las-dataset-mcp": {
            "command": "uvx",
            "args": [
            "--from",
            "git+https://github.com/volcengine/mcp-server#subdirectory=server/mcp_server_mongodb",
            "mcp-server-mognodb"
          ],
            "env": {
                "VOLC_ACCESSKEY": "your-access-key-id",
                "VOLC_SECRETKEY": "your-access-key-secret",
                "VOLC_REGION": "VOLC_REGION"
            }
        }
    }
}
```

## License
MIT



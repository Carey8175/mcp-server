# ECS MCP Server 


## Version
v0.1.0

## Overview

ECS MCP Server is a Model Context Protocol server that provides MCP clients (such as Claude Desktop) with the ability to interact with the Volcengine ECS service. It enables full-chain management of cloud instance resources based on natural language, supporting query operations for instances, images, regions, availability zones, available resources, and system events, thereby achieving efficient management of ECS resources.

## Category
ECS

## Features

- Query instance information
- Query event information 
- Query region information

## Available Tools

- `describe_instances`: [query instance list](https://www.volcengine.com/docs/6396/70466)
- `describe_images`: [query image list](https://www.volcengine.com/docs/6396/70808)
- `describe_instance_types`: [query instance type list](https://www.volcengine.com/docs/6396/92769)
- `describe_available_resource`: [query available resources](https://www.volcengine.com/docs/6396/76279)
- `describe_system_events`: [query system events](https://www.volcengine.com/docs/6396/129399)
- `describe_regions`: [query region list](https://www.volcengine.com/docs/6396/1053194)
- `describe_zones`: [query availability zone list](https://www.volcengine.com/docs/6396/120518)

## Usage Guide

### Prerequisites
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

### Installation
Clone the repository:
```bash
git clone https://github.com/volcengine/mcp-server/tree/main/mcp_server_ecs.git
```

### Usage
Start the server:

#### UV
```bash
cd mcp_server_ecs
uv run mcp-server-ecs

# Start with sse mode (default is stdio)
uv run mcp-server-ecs -t sse
```

Use a client to interact with the server:
```
Claude Desktop | Cline | Cursor | Trae | ...
```

## Configuration

The main configuration file for the MCP server is located at:

```
src/mcp_server_ecs/conf/settings.toml
src/mcp_server_ecs/conf/.secrets.toml
```

This configuration file contains key settings for the server, such as logging and Volcengine account AK|SK configuration.

### Environment Variables

The following environment variables are available for configuring the MCP server:

| Environment Variable | Description | Default Value |
|----------|------|--------|
| `FASTMCP_PORT` | MCP server listening port | `8000` |
| `VOLC_ACCESSKEY` | Volcengine account ACCESSKEY | - |
| `VOLC_SECRETKEY` | Volcengine account SECRETKEY | - |
| `VOLC_REGION` | Volcengine resource region | - 
| `VOLC_ENDPOINT` | Volcengine endpoint | - |

For example, set these environment variables before starting the server:

```bash
export FASTMCP_PORT=8000
export VOLC_ACCESSKEY={ak}
export VOLC_SECRETKEY={sk}
export VOLC_REGION={sk}
export VOLC_ENDPOINT={endpoint}

```

### Run with uvx
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

```

## Examples
### Cursor
![Image](https://lf3-beecdn.bytetos.com/obj/ies-fe-bee-upload/bee_prod/biz_950/tos_333f0ad0f93c311bae4259ce2ab9022c.jpg)
![Image](https://lf3-beecdn.bytetos.com/obj/ies-fe-bee-upload/bee_prod/biz_950/tos_49abb4af5fb42f55052558867daff3d6.jpg)


# License
MIT

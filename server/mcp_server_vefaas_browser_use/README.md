# MCP Server 产品名称：veFaaS browser-use MCP Server

![logo](https://lf3-beecdn.bytetos.com/obj/ies-fe-bee-upload/bee_prod/biz_950/tos_8fc72d37e54a2b28d334112241dd84ca.png)

## 版本信息

v0.0.1

## 产品描述

### 短描述

veFaaS browser-use MCP server 自动化你的浏览器操作任务。

### 长描述（建议50字，不超过100字）

veFaaS browser-use MCP server 可以让用户仅输入检索任务，就可以由大模型分析拆解任务，调用浏览器实时搜索任务，最后整合输出任务结果。

## 分类

FaaS，函数服务，函数

## 标签

veFaaS，函数服务，browser-use，浏览器

## Tools

本 MCP Server 产品提供以下 Tools (工具/能力):

### Tool 1: create_browser_use_task

#### 类型

实例

#### 详细描述

发起浏览器操作任务

输出：

- 返回任务结果

#### 最容易被唤起的 Prompt示例

```
查看今日北京天气
```

## 可适配平台  

Python, Cursor, Claude macOS App, Cline

## 服务开通链接 (整体产品)  

<https://console.volcengine.com/vefaas>

## 鉴权方式  

OAuth 2.0

## 在不同平台的配置

### 方舟

#### 体验中心

1. 查看 MCP Server 详情
在大模型生态广场，选择合适的 veFaaS MCP Server，并查看详情
2. 选择 MCP Server 即将运行的平台
检查当前 MCP Server 已适配的平台，并选择合适的平台
3. 查看并对比可用的 Tools
仔细查看可用的 Tools 的功能描述与所需的输入参数，并尝试运行对应的功能。
4. 获取专属的URL或代码示例
检查账号登录状态与服务开通情况，生成唯一URL
5. 去对应的Client的平台进行使用
点击快捷跳转按钮，前往方舟平台的体验中心进行对应MCP Server的体验

### UVX

```json
{
  "mcpServers": {
    "vefaas-browser-use": {
      "command": "uvx",
      "args": [
        "--from",
        "git+https://github.com/volcengine/mcp-server#subdirectory=server/mcp_server_vefaas_browser_use",
        "mcp-server-vefaas-browser-use"
      ],
      "env": {
        "BROWSER_USE_ENDPOINT": "https://xxxxxxxxxxx.apigateway-cn-beijing.volceapi.com"
      }
    }
  }
}
```

## License

volcengine/mcp-server is licensed under the MIT License.

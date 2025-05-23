
# MCP Server 产品名称：
证书中心 MCP Server

## 版本信息
v1

## 产品描述
### 短描述
基于 MCP 管理证书资源
### 长描述
证书中心 官方推出的 MCP Server 提供强大的查询能力，支持通过自然语言便捷地申请以及查询证书，提升了数据访问的直观性与效率。可以与火山引擎云产品MCP 组合，助力构建更智能的业务应用场景。

## 分类
企业应用

## 标签
域名与网站，SSL证书

## Tools
本 MCP Server 产品提供以下 Tools (工具/能力):
### Tool1: quick_apply_certificate
 - 详细描述：调用本接口创建一个付费证书订单并提交证书申请。
 - 触发示例：调用 quick_apply_certificate 获取相关数据
### Tool2: certificate_get_instance
 - 详细描述：调用本接口查询指定SSL证书实例的详情。
 - 触发示例：调用 certificate_get_instance 获取相关数据
### Tool3: import_certificate
 - 详细描述：调用本接口上传一本SSL证书到证书中心。
 - 触发示例：调用 import_certificate 获取相关数据
### Tool4: certificate_get_instance_list
 - 详细描述：调用本接口获取SSL证书实例列表。
 - 触发示例：调用 certificate_get_instance_list 获取相关数据
### Tool5: certificate_add_organization
 - 详细描述：调用本接口创建一个信息模板。
 - 触发示例：调用 certificate_add_organization 获取相关数据
### Tool6: certificate_get_organization
 - 详细描述：调用本接口创建一个信息模板。
 - 触发示例：调用 certificate_get_organization 获取相关数据
### Tool7: certificate_get_organization_list
 - 详细描述：调用本接口获取已有信息模板列表。
 - 触发示例：调用 certificate_get_organization_list 获取相关数据
### Tool8: list_tags_for_resources
 - 详细描述：调用本接口查询您的证书中心资源绑定的标签。
 - 触发示例：调用 list_tags_for_resources 获取相关数据



## 最容易被唤起的 Prompt示例
### quick_apply_certificate
我想要申请一本证书。 
### certificate_get_instance_list
我想要查看下我的证书列表。


# 可适配平台  
可以使用 cline, cursor, claude desktop 或支持MCP server调用的的其他终端

## 服务开通链接 (整体产品)
<https://console.volcengine.com/certificate-center>


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
    - 构建mcp server:
    ```bash
    uv build
    ```

## Using uv (recommended)
When using uv no specific installation is needed. We will
use uvx to directly run mcp-server-tos.

### 本地配置
- 添加以下配置到你的 mcp settings 文件中

```json
{
    "mcpServers": {
      "mcp-server": {
        "command": "uv",
        "args": [
          "--directory",
          "/ABSOLUTE/PATH/TO/PARENT/mcp_server_certificate_center/src/certificate_service",
          "run",
           "mcp-server-certificate-center"
        ],
        "env": {
          "VOLCENGINE_ACCESS_KEY": "your access-key-id",
          "VOLCENGINE_SECRET_KEY": "your access-key-secret",
          "VOLCENGINE_REGION": "your region",
        }
      }
    }
  }
```

OR

- 添加以下配置到你的 mcp settings 文件中
```json
{
  "mcpServers": {
    "mcp-server": {
      "command": "uv",
      "args": [
        "--directory",
        "/ABSOLUTE/PATH/TO/PARENT/mcp_server_certificate_center/src/certificate_service",
        "run",
        "server.py"
      ],
      "env": {
        "VOLCENGINE_ACCESS_KEY": "your access-key-id",
        "VOLCENGINE_SECRET_KEY": "your access-key-secret",
        "VOLCENGINE_REGION": "your region"
      }
    }
  }
}
```

## Using uvx
### 本地配置
- 添加以下配置到你的 mcp settings 文件中
```json
{
  "mcp-server": {
    "tos-mcp": {
      "command": "uvx",
      "args": [
        "--from",
        "git+https://github.com/volcengine/mcp-server#subdirectory=server/mcp_server_certificate_center",
        "mcp-server-certificate-center"
      ],
      "env": {
        "VOLCENGINE_ACCESS_KEY": "your access-key-id",
        "VOLCENGINE_SECRET_KEY": "your access-key-secret",
        "VOLCENGINE_REGION": "your region",
      }
    }
  }
}
```


# License
MIT
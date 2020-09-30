# ListListeners

调用ListListeners查询监听列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListListeners&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListListeners|系统规定参数。取值：**ListListeners**。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|PageNumber|Integer|是|1|列表的页码，默认值为**1**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域，仅取值**cn-hangzhou**。 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Listeners|Array of Listeners| |监听信息。 |
|BackendPorts|Array of BackendPort| |后端服务器端口信息。 |
|FromPort|String|80|后端服务器的起始端口。 |
|ToPort|String|80|后端服务器的结束端口。 |
|Certificates|Array of Certificate| |SSL证书信息。 |
|Id|String|44983xxxx-cn-hangzhou|SSL证书ID。 |
|Type|String|Server|证书类型。

 目前，仅支持返回**Server**（服务端证书）。 |
|ClientAffinity|String|SOURCE\_IP|客户端亲和性。

 -   返回为空（默认）时：不保持客户端亲和性，即不能确保来自同一客户端的连接请求始终定向到同一终端节点。
-   返回为**SOURCE\_IP**时，保持客户端亲和性。即客户端访问有状态的应用程序时，可以将来自同一客户端的所有请求都定向到同一终端节点，而不考虑源端口和协议。 |
|CreateTime|Long|1577786252000|监听的创建时间。 |
|Description|String|Listener|监听的描述信息。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听ID。 |
|Name|String|Listener|监听的名称。 |
|PortRanges|Array of PortRanges| |监听端口信息。 |
|FromPort|Integer|20|用来接收请求并向终端节点进行转发的起始监听端口。 |
|ToPort|Integer|20|用来接收请求并向终端节点进行转发的结束监听端口。 |
|Protocol|String|TCP|监听的网络传输协议类型。

 -   **TCP**：TCP协议。
-   **UDP**：UDP协议。 |
|ProxyProtocol|Boolean|true|是否开启了保持客户端源IP功能。

 -   **true**：开启了保持客户端源IP功能。开启后，支持后端服务查看客户端的原始IP地址。
-   **false**：未开启了保持客户端源IP功能。 |
|State|String|active|监听的状态。

 -   **active**：正常。
-   **creating**：创建中。
-   **configuring**：配置中。 |
|PageNumber|Integer|1|当前页码。 |
|PageSize|Integer|10|每页包含的条目数。 |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |
|TotalCount|Integer|1|列表条目数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListListeners
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&PageNumber=1
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListListenersResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <Listeners>
        <ClientAffinity></ClientAffinity>
        <Name>dede</Name>
        <PortRanges>
              <ToPort>80</ToPort>
              <FromPort>80</FromPort>
        </PortRanges>
        <State>active</State>
        <CreateTime>1581669998000</CreateTime>
        <Protocol>TCP</Protocol>
        <ListenerId>lsr-bp12tl35dpsilnsb1****</ListenerId>
  </Listeners>
  <RequestId>4150E70A-E6FB-4707-BF71-39483DF85C74</RequestId>
</ListListenersResponse>
```

`JSON` 格式

```
{
  "PageNumber": 1,
  "TotalCount": 1,
  "PageSize": 10,
  "Listeners": [
    {
      "ClientAffinity": "",
      "Name": "dede",
      "PortRanges": [
        {
          "ToPort": 80,
          "FromPort": 80
        }
      ],
      "State": "active",
      "CreateTime": 1581669998000,
      "Protocol": "TCP",
      "ListenerId": "lsr-bp12tl35dpsilnsb1****"
    }
  ],
  "RequestId": "4150E70A-E6FB-4707-BF71-39483DF85C74"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


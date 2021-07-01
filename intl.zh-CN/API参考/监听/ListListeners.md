# ListListeners

调用ListListeners查询监听列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListListeners&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListListeners|系统规定参数。取值：**ListListeners**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|TotalCount|Integer|1|列表条目数。 |
|Listeners|Array of Listeners| |监听信息。 |
|Certificates|Array of Certificate| |SSL证书信息。 |
|Type|String|Server|证书类型。

 目前，仅支持返回**Server**（服务端证书）。 |
|Id|String|44983xxxx-cn-hangzhou|SSL证书ID。 |
|BackendPorts|Array of BackendPort| |后端服务器端口信息。 |
|FromPort|String|80|后端服务器的起始端口。 |
|ToPort|String|80|后端服务器的结束端口。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听ID。 |
|Description|String|Listener|监听的描述信息。 |
|State|String|active|监听的状态。

 -   **active**：正常。
-   **creating**：创建中。
-   **configuring**：配置中。 |
|ClientAffinity|String|SOURCE\_IP|客户端亲和性。

 -   返回为空（默认）时：不保持客户端亲和性，即不能确保来自同一客户端的连接请求始终定向到同一终端节点。
-   返回为**SOURCE\_IP**时，保持客户端亲和性。即客户端访问有状态的应用程序时，可以将来自同一客户端的所有请求都定向到同一终端节点，而不考虑源端口和协议。 |
|Protocol|String|TCP|监听的网络传输协议类型。

 -   **TCP**：TCP协议。
-   **UDP**：UDP协议。 |
|CreateTime|Long|1577786252000|监听创建时间的时间戳。 |
|PortRanges|Array of PortRanges| |监听端口信息。 |
|FromPort|Integer|20|用来接收请求并向终端节点进行转发的起始监听端口。 |
|ToPort|Integer|20|用来接收请求并向终端节点进行转发的结束监听端口。 |
|Name|String|Listener|监听的名称。 |
|ProxyProtocol|Boolean|true|是否开启了保持客户端源IP功能。

 -   **true**：开启了保持客户端源IP功能。开启后，支持后端服务查看客户端的原始IP地址。
-   **false**：未开启了保持客户端源IP功能。 |
|AcceleratorId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|PageSize|Integer|10|每页包含的条目数。 |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |
|PageNumber|Integer|1|当前页码。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListListeners
&RegionId=cn-hangzhou
&PageNumber=1
&PageSize=10
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListListenersResponse>
    <TotalCount>1</TotalCount>
    <Listeners>
        <Certificates>
            <Type>Server</Type>
            <Id>44983xxxx-cn-hangzhou</Id>
        </Certificates>
        <BackendPorts>
            <FromPort>80</FromPort>
            <ToPort>80</ToPort>
        </BackendPorts>
        <ListenerId>lsr-bp1bpn0kn908w4nbw****</ListenerId>
        <Description>Listener</Description>
        <State>active</State>
        <ClientAffinity>SOURCE_IP</ClientAffinity>
        <Protocol>TCP</Protocol>
        <CreateTime>1577786252000</CreateTime>
        <PortRanges>
            <FromPort>20</FromPort>
            <ToPort>20</ToPort>
        </PortRanges>
        <Name>Listener</Name>
        <ProxyProtocol>true</ProxyProtocol>
        <AcceleratorId>ga-bp1odcab8tmno0hdq****</AcceleratorId>
    </Listeners>
    <PageSize>10</PageSize>
    <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8	</RequestId>
    <PageNumber>1</PageNumber>
</ListListenersResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "TotalCount" : 1,
  "Listeners" : [ {
    "Certificates" : [ {
      "Type" : "Server",
      "Id" : "44983xxxx-cn-hangzhou"
    } ],
    "BackendPorts" : [ {
      "FromPort" : "80",
      "ToPort" : "80"
    } ],
    "ListenerId" : "lsr-bp1bpn0kn908w4nbw****",
    "Description" : "Listener",
    "State" : "active",
    "ClientAffinity" : "SOURCE_IP",
    "Protocol" : "TCP",
    "CreateTime" : 1577786252000,
    "PortRanges" : [ {
      "FromPort" : 20,
      "ToPort" : 20
    } ],
    "Name" : "Listener",
    "ProxyProtocol" : true,
    "AcceleratorId" : "ga-bp1odcab8tmno0hdq****"
  } ],
  "PageSize" : 10,
  "RequestId" : "6FEA0CF3-D3B9-43E5-A304-D217037876A8\t",
  "PageNumber" : 1
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


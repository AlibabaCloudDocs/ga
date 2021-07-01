# DescribeListener

调用DescribeListener查询监听。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DescribeListener&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeListener|系统规定参数。取值：**DescribeListener**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|ListenerId|String|是|lsr-bp1bpn0kn908w4nbw\*\*\*\*|要查询的监听的ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Description|String|Listener|监听的描述信息。 |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |
|State|String|active|监听的状态。

 -   **active**：正常。
-   **creating**：创建中。
-   **configuring**：配置中。 |
|CreateTime|String|1577786252000|监听创建时间的时间戳。 |
|PortRanges|Array of PortRanges| |监听端口信息。 |
|FromPort|Integer|20|用来接收请求并向终端节点进行转发的起始监听端口。 |
|ToPort|Integer|20|用来接收请求并向终端节点进行转发的结束监听端口。 |
|BackendPorts|Array of BackendPort| |后端端口信息。 |
|FromPort|String|80|后端服务器接收请求的起始端口。

 当您的监听协议为HTTPS，且监听的端口和后端服务器提供服务的端口一致时才需填写该项。其中，后端服务器接收请求的起始端口和结束端口需相同。 |
|ToPort|String|80|后端服务器接收请求的结束端口。 |
|Certificates|Array of Certificate| |SSL证书列表。 |
|Type|String|Server|证书类型。

 目前，仅支持返回**Server**（服务端证书）。 |
|Id|String|449\*\*\*\*-cn-hangzhou|SSL证书ID。

 仅HTTPS协议的监听需要配置该项。 |
|Protocol|String|TCP|监听的网络传输协议类型。

 -   **TCP**：TCP协议。
-   **UDP**：UDP协议。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听ID。 |
|ClientAffinity|String|SOURCE\_IP|客户端亲和性。

 -   返回为空时：不保持客户端亲和性，即不能确保来自同一客户端的连接请求始终定向到同一终端节点。
-   返回为**SOURCE\_IP**时，保持客户端亲和性。即客户端访问有状态的应用程序时，可以将来自同一客户端的所有请求都定向到同一终端节点，而不考虑源端口和协议。 |
|Name|String|Listener|监听的名称。 |
|RelatedAcls|Array of relatedAcls| |监听绑定的访问控制策略组信息。 |
|AclId|String|123|监听绑定的访问策略组ID。 |
|Status|String|off|是否开启访问控制功能。

 取值：**on**或**off**（默认值）。 |
|AclType|String|white|访问控制类型：

 -   **white**：

仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问全球加速监听。如果开启了白名单访问，但访问策略组中没有添加任何IP，则全球加速监听会转发全部请求。

-   **black**：来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则全球加速监听会转发全部请求。


 当**AclStatus**参数的值为on时，该参数必选。 |
|AcceleratorId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|ProxyProtocol|Boolean|false|是否开启保持客户端源IP功能。

 -   **true**：开启保持客户端源IP功能。开启后，支持后端服务查看客户端的原始IP地址。
-   **false**（默认值）：不开启保持客户端源IP功能。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeListener
&RegionId=cn-hangzhou
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeListenerResponse>
    <Description>Listener</Description>
    <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8	</RequestId>
    <State>active</State>
    <CreateTime>1577786252000</CreateTime>
    <PortRanges>
        <FromPort>20</FromPort>
        <ToPort>20</ToPort>
    </PortRanges>
    <BackendPorts>
        <FromPort>80</FromPort>
        <ToPort>80</ToPort>
    </BackendPorts>
    <Certificates>
        <Type>Server</Type>
        <Id>449****-cn-hangzhou</Id>
    </Certificates>
    <Protocol>TCP</Protocol>
    <ListenerId>lsr-bp1bpn0kn908w4nbw****</ListenerId>
    <ClientAffinity>SOURCE_IP</ClientAffinity>
    <Name>Listener</Name>
    <RelatedAcls>
        <AclId>123</AclId>
        <Status>off</Status>
    </RelatedAcls>
    <AclType>white</AclType>
    <AcceleratorId>ga-bp1odcab8tmno0hdq****</AcceleratorId>
    <ProxyProtocol>false</ProxyProtocol>
</DescribeListenerResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "Description" : "Listener",
  "RequestId" : "6FEA0CF3-D3B9-43E5-A304-D217037876A8\t",
  "State" : "active",
  "CreateTime" : "1577786252000",
  "PortRanges" : [ {
    "FromPort" : 20,
    "ToPort" : 20
  } ],
  "BackendPorts" : [ {
    "FromPort" : "80",
    "ToPort" : "80"
  } ],
  "Certificates" : [ {
    "Type" : "Server",
    "Id" : "449****-cn-hangzhou"
  } ],
  "Protocol" : "TCP",
  "ListenerId" : "lsr-bp1bpn0kn908w4nbw****",
  "ClientAffinity" : "SOURCE_IP",
  "Name" : "Listener",
  "RelatedAcls" : [ {
    "AclId" : "123",
    "Status" : "off"
  } ],
  "AclType" : "white",
  "AcceleratorId" : "ga-bp1odcab8tmno0hdq****",
  "ProxyProtocol" : false
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


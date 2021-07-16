# CreateListener

调用CreateListener创建监听。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=CreateListener&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateListener|系统规定参数。取值：**CreateListener**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|Name|String|否|Listener|监听的名称。

 名称长度为2~128个字符，以大小写字母或中文开头，可包含数字、下划线（\_）和短划线（-）。 |
|Description|String|否|Listener|监听的描述信息。 |
|ClientAffinity|String|否|SOURCE\_IP|客户端亲和性。

 -   取值为空（默认）时：不保持客户端亲和性，即不能确保来自同一客户端的连接请求始终定向到同一终端节点。
-   取值为**SOURCE\_IP**时，保持客户端亲和性。即客户端访问有状态的应用程序时，可以将来自同一客户端的所有请求都定向到同一终端节点，而不考虑源端口和协议。 |
|Protocol|String|否|tcp|监听的网络传输协议类型，取值：

 -   **tcp**：TCP协议。
-   **udp**：UDP协议。
-   **http**：HTTP协议。
-   **https**：HTTPS协议。

 **说明：** 目前，HTTP和HTTPS监听协议白名单开放，如需使用，请[提交工单](https://selfservice.console.aliyun.com/ticket/createIndex.htm)。 |
|ProxyProtocol|Boolean|否|false|是否开启保持客户端源IP功能。

 -   **true**：开启保持客户端源IP功能。开启后，支持后端服务查看客户端的原始IP地址。
-   **false**（默认值）：不开启保持客户端源IP功能。 |
|PortRanges.N.FromPort|Integer|是|20|用来接收请求并向终端节点进行转发的起始监听端口。

 **说明：** 对于HTTP或HTTPS协议的监听，只支持配置一个监听端口，即起始监听端口和结束监听端口需相同。 |
|PortRanges.N.ToPort|Integer|是|20|用来接收请求并向终端节点进行转发的结束监听端口。 |
|Certificates.N.Id|String|否|449\*\*\*\*-cn-hangzhou|SSL证书ID。

 **说明：** 仅HTTPS协议的监听需要配置该参数。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateListener
&RegionId=cn-hangzhou
&ClientToken=123e4567-e89b-12d3-a456-426655440000	
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&Name=Listener
&Description=Listener
&ClientAffinity=SOURCE_IP
&Protocol=tcp
&ProxyProtocol=false
&PortRanges=[{"FromPort":20,"ToPort":20}]
&Certificates=[{"Id":"449****-cn-hangzhou"}]
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<CreateListenerResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
    <ListenerId>lsr-bp1bpn0kn908w4nbw****</ListenerId>
</CreateListenerResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "04F0F334-1335-436C-A1D7-6C044FE73368",
  "ListenerId" : "lsr-bp1bpn0kn908w4nbw****"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ProtocalIllegal.Listener|The specified listener protocol is invalid.|监听协议配置非法|
|400|NotExist.Accelerator|The accelerated instance does not exist.|加速实例不存在|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|
|400|QuotaExceeded.Listener|The maximum number of listeners is exceeded.|监听器达到Quota限制|
|400|QuotaExceeded.ListenerPort|The maximum number of listener ports is exceeded.|监听端口达到Quota限制|
|400|PortRangeIllegal.Listener|The specified listener port range is invalid.|监听端口范围配置非法|
|400|PortRangeIllegal.Count|The hugePort listener only supports one port range.|海量端口监听（端口数\>300）仅支持配置一个端口范围|
|400|PortConflict.Listener|The listener port configuration is in conflict.|监听端口配置冲突|
|400|PortRangeIllegal.ExceedGaAbility|The listener port range is invalid. For each accelerator instance, you can only create a listener with port range over 300 for each protocol \(TCP and UDP\).|监听端口范围非法，每个全球加速实例只支持创建每种协议\(TCP/UDP\)各一个端口范围超过300的监听|
|400|PortRangeIllegal.UDP|UDP ports 250, 4789, and 4790 are system reserved ports.|UDP监听的250、4789和4790端口为系统保留端口，暂不对外开放|
|400|SystemPort.Listener|Ports 65500-65535 are system reserved ports.|端口65500-65535为系统保留端口|
|400|PortRanges.MustOne|The portRanges must be one for HTTPS and HTTP type listener.|HTTPS/HTTP类型监听只支持一个端口|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


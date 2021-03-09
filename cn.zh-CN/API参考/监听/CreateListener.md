# CreateListener

调用CreateListener创建监听。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=CreateListener&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateListener|系统规定参数。取值：**CreateListener**。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|PortRanges.N.FromPort|Integer|是|20|用来接收请求并向终端节点进行转发的起始监听端口。

 **说明：** 对于HTTP或HTTPS协议的监听，只支持配置一个监听端口，即起始监听端口和结束监听端口需相同。 |
|PortRanges.N.ToPort|Integer|是|20|用来接收请求并向终端节点进行转发的结束监听端口。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|Name|String|否|Listener|监听的名称。

 名称长度为2~128个字符，以大小写字母或中文开头，可包含数字、下划线（\_）和短划线（-）。 |
|Description|String|否|Listener|监听的描述信息。 |
|ClientAffinity|String|否|SOURCE\_IP|客户端亲和性。

 -   取值为空（默认）时：不保持客户端亲和性，即不能确保来自同一客户端的连接请求始终定向到同一终端节点。
-   取值为**SOURCE\_IP**时，保持客户端亲和性。即客户端访问有状态的应用程序时，可以将来自同一客户端的所有请求都定向到同一终端节点，而不考虑源端口和协议。 |
|Protocol|String|否|tcp|监听的网络传输协议类型，取值：

 -   **tcp**：TCP协议。
-   **udp**：UDP协议。
-   **HTTP**：HTTP协议。
-   **HTTPS**：HTTPS协议。

 **说明：** 目前，HTTP和HTTPS监听协议白名单开放，如需使用，请提交工单。 |
|ProxyProtocol|Boolean|否|false|是否开启保持客户端源IP功能。

 -   **true**：开启保持客户端源IP功能。开启后，支持后端服务查看客户端的原始IP地址。
-   **false**（默认值）：不开启保持客户端源IP功能。 |
|Certificates.N.Id|String|否|449\*\*\*\*-cn-hangzhou|SSL证书ID。

 **说明：** 仅HTTPS协议的监听需要配置该参数。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateListener
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&PortRanges.1.FromPort=20
&PortRanges.1.ToPort=20
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CreateListenerResponse>
      <ListenerId>lsr-bp1bpn0kn908w4nbw****</ListenerId>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</CreateListenerResponse>
```

`JSON`格式

```
{
   "ListenerId": "lsr-bp1bpn0kn908w4nbw****",
   "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ProtocalIllegal.Listener|The specified listener protocol is invalid.|监听协议配置非法|
|400|NotExist.Accelerator|The accelerated instance does not exist.|加速实例不存在|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|
|400|QuotaExceeded.Listener|The maximum number of listeners is exceeded.|监听器达到Quota限制|
|400|PortRangeIllegal.Listener|The specified listener port range is invalid.|监听端口范围配置非法|
|400|PortConflict.Listener|The listener port configuration is in conflict.|监听端口配置冲突|
|400|QuotaExceeded.ListenerPort|The maximum number of listener ports is exceeded.|监听端口达到Quota限制|

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


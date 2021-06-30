# ConfigEndpointProbe

调用ConfigEndpointProbe配置终端节点时延探测。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ConfigEndpointProbe&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ConfigEndpointProbe|系统规定参数。取值：**ConfigEndpointProbe**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|EndpointGroupId|String|是|epg-bp1dmlohjjz4kqaun\*\*\*\*|终端节点组ID。 |
|EndpointType|String|是|Ip|终端节点类型。取值：

 -   **Ip**：云下自定义IP。
-   **Domain**：云下自定义域名。
-   **EIP**：云上EIP。
-   **PublicIp**：云上公网IP。
-   **ECS**：云上ECS。
-   **SLB**：云上SLB。 |
|Endpoint|String|是|127.XX.XX.21|终端节点。 |
|ProbeProtocol|String|否|tcp|时延探测协议。取值范围：

 -   **tcp**：TCP协议。
-   **icmp**：ICMP协议。 |
|ProbePort|String|否|80|时延探测端口。取值范围：**0**～**65535**。 |
|Enable|String|是|true|是否开启时延探测。取值：**true**或**false**（默认值）。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ConfigEndpointProbe
&RegionId=cn-hangzhou
&ClientToken=123e4567-e89b-12d3-a456-426655440000
&EndpointGroupId=epg-bp1dmlohjjz4kqaun****
&EndpointType=Ip
&Endpoint=127.XX.XX.21
&ProbeProtocol=tcp
&ProbePort=80
&Enable=true
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ConfigEndpointProbeResponse>
    <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
</ConfigEndpointProbeResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6FEA0CF3-D3B9-43E5-A304-D217037876A8"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


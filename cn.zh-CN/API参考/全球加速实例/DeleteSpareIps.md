# DeleteSpareIps

调用DeleteSpareIps删除CNAME备用IP。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DeleteSpareIps&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteSpareIps|系统规定参数。取值：**DeleteSpareIps**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值：**cn-hangzhou**。 |
|ClientToken|String|否|1F4B6A4A-C89E-489E-BAF1-52777EE148EF|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|DryRun|Boolean|否|true|是否只预检此次请求，取值：

 -   **true**：发送检查请求，不会创建资源。检查项包括是否填写了必需参数、请求格式、业务限制。如果检查不通过，则返回对应错误。如果检查通过，则返回错误码`DryRunOperation`。
-   **false**（默认值）：发送正常请求，通过检查后返回HTTP 2xx状态码并直接进行操作。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|SpareIps.N|String|是|\['127.0.XX.XX', '139.0.XX.XX'\]|CNAME备用IP列表，当加速区域异常时，流量切换到备用IP。

 IP间用半角逗号（,）分隔，N的取值范围：**0**~**2**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteSpareIps
&RegionId=cn-hangzhou
&ClientToken=1F4B6A4A-C89E-489E-BAF1-52777EE148EF
&DryRun=true
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&SpareIps=["['127.0.XX.XX', '139.0.XX.XX']"]
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeleteSpareIpsResponse>
    <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
</DeleteSpareIpsResponse>
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

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


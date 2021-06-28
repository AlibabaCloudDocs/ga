# DeleteBandwidthPackage

调用DeleteBandwidthPackage删除带宽包。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DeleteBandwidthPackage&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteBandwidthPackage|系统规定参数。取值：**DeleteBandwidthPackage**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|BandwidthPackageId|String|是|gbwp-bp1sgzldyj6b4q7cx\*\*\*\*|需要删除的带宽包的ID。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |
|BandwidthPackageId|String|gbwp-bp1sgzldyj6b4q7cx\*\*\*\*|需要删除的带宽包的ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteBandwidthPackage
&RegionId=cn-hangzhou
&BandwidthPackageId=gbwp-bp1sgzldyj6b4q7cx****
&ClientToken=123e4567-e89b-12d3-a456-426655440000
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeleteBandwidthPackageResponse>
    <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
    <BandwidthPackageId>gbwp-bp1sgzldyj6b4q7cx****</BandwidthPackageId>
</DeleteBandwidthPackageResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6FEA0CF3-D3B9-43E5-A304-D217037876A8",
  "BandwidthPackageId" : "gbwp-bp1sgzldyj6b4q7cx****"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NotExist.BandwidthPackage|The bandwidth package does not exist.|带宽包不存在|
|400|StateError.BandwidthPackage|The state of bandwidth package is invalid.|带宽包状态非法|
|400|BindExist.BandwidthPackage|The bandwidth package is already bound.|带宽包已经绑定|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


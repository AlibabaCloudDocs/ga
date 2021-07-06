# BandwidthPackageAddAccelerator

调用BandwidthPackageAddAccelerator将带宽包与全球加速实例绑定。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=BandwidthPackageAddAccelerator&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|BandwidthPackageAddAccelerator|系统规定参数。取值：**BandwidthPackageAddAccelerator**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|BandwidthPackageId|String|是|gbwp-bp1sgzldyj6b4q7cx\*\*\*\*|与全球加速实例绑定的带宽包的ID。 |
|AcceleratorId|String|是|ga-bp1qe94o52ot4pkfn\*\*\*\*|与带宽包绑定的全球加速实例的ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|B7770CB9-9745-4FE5-9EDA-D14B01A12A50|请求ID。 |
|Accelerators|Array of String|ga-bp1qe94o52ot4pkfn\*\*\*\*|与带宽包绑定的全球加速实例的ID。 |
|BandwidthPackageId|String|gbwp-bp1sgzldyj6b4q7cx\*\*\*\*|与全球加速实例绑定的带宽包的ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=BandwidthPackageAddAccelerator
&RegionId=cn-hangzhou
&BandwidthPackageId=gbwp-bp1sgzldyj6b4q7cx****
&AcceleratorId=ga-bp1qe94o52ot4pkfn****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<BandwidthPackageAddAcceleratorResponse>
    <RequestId>B7770CB9-9745-4FE5-9EDA-D14B01A12A50</RequestId>
    <Accelerators>ga-bp1qe94o52ot4pkfn****</Accelerators>
    <BandwidthPackageId>gbwp-bp1sgzldyj6b4q7cx****</BandwidthPackageId>
</BandwidthPackageAddAcceleratorResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "B7770CB9-9745-4FE5-9EDA-D14B01A12A50",
  "Accelerators" : [ "ga-bp1qe94o52ot4pkfn****" ],
  "BandwidthPackageId" : "gbwp-bp1sgzldyj6b4q7cx****"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NotExist.BandwidthPackage|The bandwidth package does not exist.|带宽包不存在|
|400|StateError.BandwidthPackage|The state of bandwidth package is invalid.|带宽包状态非法|
|400|NotExist.BasicBandwidthPackage|You must specify the basic bandwidth package.|缺少基础带宽包|

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


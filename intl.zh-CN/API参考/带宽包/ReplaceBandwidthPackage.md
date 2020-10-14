# ReplaceBandwidthPackage

调用ReplaceBandwidthPackage替换带宽包。

## API描述

调用此接口替换带宽包不会中断全球加速的转发流量。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ReplaceBandwidthPackage&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ReplaceBandwidthPackage|系统规定参数。取值：**ReplaceBandwidthPackage**。 |
|BandwidthPackageId|String|是|gbwp-bp176neb61yhcymow\*\*\*\*|要替换的新的带宽包ID。指定带宽包时，请注意：

 -   仅支持指定未绑定任何全球加速实例的带宽包。
-   如果要替换的带宽包为基础带宽包，请确保要替换的新的基础带宽包的带宽必须大于或等于加速区域中已分配的带宽总额。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域，仅取值**cn-hangzhou**。 |
|TargetBandwidthPackageId|String|是|gbwp-o978hgeb61yhcymow\*\*\*\*|要被替换的旧的带宽包ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|A0EA8CCA-F081-4338-9790-A1C791CCA779|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ReplaceBandwidthPackage
&BandwidthPackageId=gbwp-bp176neb61yhcymow****
&RegionId=cn-hangzhou
&TargetBandwidthPackageId=gbwp-o978hgeb61yhcymow****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ReplaceBandwidthPackageResponse>
      <RequestId>A0EA8CCA-F081-4338-9790-A1C791CCA779</RequestId>
</ReplaceBandwidthPackageResponse>
```

`JSON` 格式

```
{
	"RequestId": "A0EA8CCA-F081-4338-9790-A1C791CCA779"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NotExist.BandwidthPackage|The bandwidth package does not exist.|带宽包不存在|
|400|StateError.BandwidthPackage|The state of bandwidth package is invalid.|带宽包状态非法|
|400|NotExist.BasicBandwidthPackage|You must specify the basic bandwidth package.|缺少基础带宽包|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


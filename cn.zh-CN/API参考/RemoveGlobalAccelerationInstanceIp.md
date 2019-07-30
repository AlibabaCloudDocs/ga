# RemoveGlobalAccelerationInstanceIp {#doc_api_Vpc_RemoveGlobalAccelerationInstanceIp .reference}

调用RemoveGlobalAccelerationInstanceIp接口从带宽共享实例中移除EIP。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=RemoveGlobalAccelerationInstanceIp&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemoveGlobalAccelerationInstanceIp|要执行的操作。 取值：

 **RemoveGlobalAccelerationInstanceIp**。

 |
|GlobalAccelerationInstanceId|String|是|ga-m5ex47zwya1sejyni\*\*\*\*|共享型实例ID。

 |
|IpInstanceId|String|是|eip-bp13e9i2qst4g6jzi\*\*\*\*|EIP实例的ID。

 您可以通过调用[DescribeEipAddresses](~~36018~~)接口查询EIP实例的ID。

 |
|RegionId|String|是|cn-hangzhou|共享带宽型实例所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|RemoveGlobalAccelerationInstanceIp|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=RemoveGlobalAccelerationInstanceIp
&GlobalAccelerationInstanceId=ga-m5ex47zwya1sejyni****
&IpInstanceId=eip-bp13e9i2qst4g6jzi****
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
{
    "RequestId": "01FDDD49-C4B7-4D2A-A8E5-A93915C450A6"
}
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"01FDDD49-C4B7-4D2A-A8E5-A93915C450A6"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidBandwidthPackageId.NotFound|The specified bandwidthPackageId does not exist in our records.|该共享带宽包不存在，请您检查输入参数是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。


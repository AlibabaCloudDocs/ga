# ModifyGlobalAccelerationInstanceSpec {#doc_api_Vpc_ModifyGlobalAccelerationInstanceSpec .reference}

调用ModifyGlobalAccelerationInstanceSpec接口修改全球加速实例的带宽。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyGlobalAccelerationInstanceSpec&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyGlobalAccelerationInstanceSpec|要执行的操作。 取值：

 **ModifyGlobalAccelerationInstanceSpec**。

 |
|Bandwidth|String|是|10|全球加速实例的带宽峰值，单位为Mbps。取值范围：

 **10,20,30,40,50,60,70,80,90,100,200,300,400,500,600,700,800,900,1000** |
|GlobalAccelerationInstanceId|String|是|ga-32s33s\*\*\*\*|全球加速实例的ID。

 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|BD5BCEE8-F62C-40C2-9AC3-89XXXXXXXXX|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyGlobalAccelerationInstanceSpec
&Bandwidth=10
&GlobalAccelerationInstanceId=ga-32s33s****
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyGlobalAccelerationInstanceSpecResponse>
      <RequestId>BD5BCEE8-F62C-40C2-9AC3-89XXXXXXXXX</RequestId>
</ModifyGlobalAccelerationInstanceSpecResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"BD5BCEE8-F62C-40C2-9AC3-89XXXXXXXXX"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidGlobalAccelerationInstanceId.NotFound|The specified GlobalAccelerationInstanceId is not found.|全球加速实例不存在。|
|400|InvalidGlobalAccelerationInstanceName.Malformed|The specified Name is not valid.|名称格式不正确。|
|400|InvalidGlobalAccelerationInstanceDescription.Malformed|The specified Description is not valid.|描述格式不正确。|
|400|InvalidParameter|The parameter is invalid.|该参数值不合法。|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。


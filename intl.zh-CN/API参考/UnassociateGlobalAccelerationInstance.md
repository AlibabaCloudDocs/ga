# UnassociateGlobalAccelerationInstance {#doc_api_Vpc_UnassociateGlobalAccelerationInstance .reference}

调用UnassociateGlobalAccelerationInstance接口解绑与全球加速实例关联的后端服务实例。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=UnassociateGlobalAccelerationInstance&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UnassociateGlobalAccelerationInstance|要执行的操作。 取值：

 **UnassociateGlobalAccelerationInstance**。

 |
|GlobalAccelerationInstanceId|String|是|ga-1sxee33\*\*\*\*|全球加速实例的ID。

 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|InstanceType|String|否|EcsInstance|实例类型，取值：

 -   **RemoteEcsInstance**：ECS实例
-   **RemoteSlbInstance**：负载均衡实例
-   **RemoteEniInstance**：弹性网卡实例

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|BD5BCEE8-F62C-40C2-9AC3-89XXXXXXXXX|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=UnassociateGlobalAccelerationInstance
&GlobalAccelerationInstanceId=ga-1sxee33****
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UnassociateGlobalAccelerationInstanceResponse>
      <RequestId>BD5BCEE8-F62C-40C2-9AC3-89XXXXXXXXX</RequestId>
</UnassociateGlobalAccelerationInstanceResponse>
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
|404|InvalidGlobalAccelerationInstanceId.NotFound|The specified GlobalAccelerationInstanceId is not found.|全球加速实例不存在。|
|400|IncorrectGlobalAccelerationInstanceIdStatus|Current GlobalAccelerationInstance status does not support this operation.|指定的全球加速实例状态不支持此操作|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。


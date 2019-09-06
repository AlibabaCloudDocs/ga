# DescribeServerRelatedGlobalAccelerationInstances {#doc_api_Vpc_DescribeServerRelatedGlobalAccelerationInstances .reference}

调用DescribeServerRelatedGlobalAccelerationInstances接口查询指定后端服务器绑定的全球加速实例。

**说明：** 该接口仅支持查询带宽独享型实例。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeServerRelatedGlobalAccelerationInstances&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeServerRelatedGlobalAccelerationInstances|要执行的操作。 取值：

 **DescribeServerRelatedGlobalAccelerationInstances**。

 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ServerId|String|是|i-12s3sdf\*\*\*\*|后端服务实例的ID。

 |
|ServerType|String|否|EcsInstance|后端服务实例的类型，取值：

 -   **EcsInstance**（默认值）：ECS实例
-   **SlbInstance**：负载均衡实例

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|GlobalAccelerationInstances| | |全球加速实例信息列表。

 |
|GlobalAccelerationInstanceId|String|ga-t4nku6vv9\*\*\*\*|全球加速实例 ID。

 |
|IpAddress|String|12.34.56.78|全球加速实例公网 IP。

 |
|RegionId|String|ap-southeast-1|全球加速实例所属地域ID。

 |
|ServerIpAddress|String|172.24.52.234|后端服务IP地址。

 |
|RequestId|String|A8252014-D8DE-4D85-AF35-AFEXXXXXXX|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeServerRelatedGlobalAccelerationInstances
&RegionId=cn-hangzhou
&ServerId=i-12s3sdf****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeServerRelatedGlobalAccelerationInstancesResponse>
	  <GlobalAccelerationInstances>
		    <GlobalAccelerationInstance>
			      <GlobalAccelerationInstanceId>ga-t4nku6vv9****</GlobalAccelerationInstanceId>
			      <IpAddress>12.34.56.78</IpAddress>
			      <RegionId>ap-southeast-1</RegionId>
			      <ServerIpAddress>172.24.52.234</ServerIpAddress>
		    </GlobalAccelerationInstance>
	  </GlobalAccelerationInstances>
	  <RequestId>A8252014-D8DE-4D85-AF35-AFEXXXXXXX</RequestId>
</DescribeServerRelatedGlobalAccelerationInstancesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"A8252014-D8DE-4D85-AF35-AFEXXXXXXX",
	"GlobalAccelerationInstances":{
		"GlobalAccelerationInstance":[
			{
				"GlobalAccelerationInstanceId":"ga-t4nku6vv9****",
				"RegionId":"ap-southeast-1",
				"IpAddress":"12.34.56.78",
				"ServerIpAddress":"172.24.52.234"
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidBackendServerId.NotFound|The specified BackendServerId is not found.|后端服务器实例不存在，请您检查后端服务器实例是否正确。|
|400|InvalidBackendServerId.NotInVPC|The specified BackendServerId is not in VPC.|指定的 BackendServerId 不是 VPC 类型。|
|400|InvalidBackendServerType.NotFound|The specified BackendServerType is not supported.|指定的后端服务器类型不支持。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。


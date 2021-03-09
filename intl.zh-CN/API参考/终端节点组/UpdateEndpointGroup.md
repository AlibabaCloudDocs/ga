# UpdateEndpointGroup

调用UpdateEndpointGroup修改终端节点组配置信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=UpdateEndpointGroup&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateEndpointGroup|系统规定参数。取值：**UpdateEndpointGroup**。 |
|EndpointConfigurations.N.Endpoint|String|是|120.XX.XX.21|终端节点的IP或域名。 |
|EndpointConfigurations.N.Type|String|是|Ip|终端节点类型，取值：

 -   **Domain**：自定义域名。
-   **Ip**：自定义IP。
-   **PublicIp**：阿里云公网IP。
-   **ECS**：阿里云ECS实例。
-   **SLB**：阿里云SLB实例。

 **说明：** 终端节点类型取值为**ECS**或**SLB**时，如果服务关联角色不存在，系统会自动创建一个名称为AliyunServiceRoleForGaVpcEndpoint的服务关联角色。更多信息，请参见[服务关联角色](~~178360~~)。 |
|EndpointConfigurations.N.Weight|Integer|是|20|终端节点的权重。

 取值范围：**0**~**255**。

 **说明：** 如果某个终端节点的权重设置为0，全球加速将终止向该终端节点分发流量，请您谨慎操作。 |
|EndpointGroupId|String|是|epg-bp1dmlohjjz4kqaun\*\*\*\*|终端节点组ID。 |
|EndpointGroupRegion|String|是|cn-hangzhou|终端节点组所属的地域ID。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|Name|String|否|group1|终端节点组的名称。

 名称长度为2~128个字符，以大小写字母或中文开头，可包含数字、下划线（\_）和短划线（-）。 |
|Description|String|否|EndpointGroup|终端节点组描述信息。 |
|TrafficPercentage|Integer|否|20|监听有多个终端节点组时的权重。 |
|HealthCheckIntervalSeconds|Integer|否|3|健康检查的时间间隔，单位为秒。 |
|HealthCheckPath|String|否|/healthcheck|健康检查路径。 |
|HealthCheckPort|Integer|否|20|健康检查的端口。 |
|HealthCheckProtocol|String|否|tcp|健康检查的协议。

 -   **tcp**：TCP协议。
-   **http**：HTTP协议。
-   **https**：HTTPS协议。 |
|ThresholdCount|Integer|否|3|健康检查判定终端节点为不健康的次数。 |
|EndpointRequestProtocol|String|否|HTTP|后端服务协议。取值：

 -   **HTTP**
-   **HTTPS**

 **说明：**

-   仅为HTTP或HTTPS协议的监听实例创建终端节点组时才支持配置该项。
-   对于HTTP协议的监听实例，后端服务协议支持且仅支持HTTP。 |
|EndpointConfigurations.N.EnableClientIPPreservation|Boolean|否|false|是否开启保持客户端源IP功能，取值：

 -   **true**：开启保持客户端源IP功能。
-   **false**（默认值）：不开启保持客户端源IP功能。 |
|PortOverrides.N.ListenerPort|Integer|否|443|配置端口映射中的监听端口。

 **说明：**

-   仅为HTTP或HTTPS协议的监听实例创建终端节点组时才支持创建端口映射关系。
-   端口映射中的监听端口必须与当前监听实例的监听端口一致。 |
|PortOverrides.N.EndpointPort|Integer|否|80|配置端口映射中的终端节点端口。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateEndpointGroup
&EndpointConfigurations.1.Endpoint=120.XX.XX.21
&EndpointConfigurations.1.Type=Ip
&EndpointConfigurations.1.Weight=20
&EndpointGroupId=epg-bp1dmlohjjz4kqaun****
&EndpointGroupRegion=cn-hangzhou
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<UpdateEndpointGroupResponse>
      <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
</UpdateEndpointGroupResponse>
```

`JSON`格式

```
{
	"RequestId":"6FEA0CF3-D3B9-43E5-A304-D217037876A8"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NotExist.EndPointGroup|The endpoint group does not exist.|终端节点组不存在|
|400|StateError.EndPointGroup|The specified state of endpoint group is invalid.|终端节点组状态非法|
|400|NotExist.Listener|The listener does not exist.|监听器不存在|
|400|NotActive.Listener|The state of the listener is not active.|监听器状态非稳态|
|400|NotExist.Accelerator|The accelerated instance does not exist.|加速实例不存在|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|
|400|QuotaExceeded.EndPoint|The maximum number of endpoints is exceeded.|终端节点达到Quota限制|
|400|NoPermission.VpcEndpoint|You are not authorized to perform the operation.|用户没有创建服务关联角色的权限，请联系主账号或权限管理员授权当前用户AliyunGlobalAccelerationFullAccess或者创建服务关联角色的自定义权限。自定义权限策略的相关信息如下： ServiceName：vpcendpoint.ga.aliyuncs.com 服务关联角色名称：AliyunServiceRoleForGaVpcEndpoint 执行该操作所需的用户权限：ram:CreateServiceLinkedRole|
|400|QuotaExceeded.PortOverride|The number of port override exceeds the limit.|端口转发数量超过限制|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


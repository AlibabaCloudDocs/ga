# CreateEndpointGroup

调用CreateEndpointGroup创建终端节点组。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=CreateEndpointGroup&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateEndpointGroup|系统规定参数。取值：**CreateEndpointGroup**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|Name|String|否|group1|终端节点组的名称。

 名称长度为2~128个字符，以大小写字母或中文开头，可包含数字、下划线（\_）和短划线（-）。 |
|Description|String|否|EndpointGroup|终端节点组描述信息。 |
|EndpointGroupRegion|String|是|cn-hangzhou|终端节点组所属的地域ID。 |
|ListenerId|String|是|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|TrafficPercentage|Integer|否|20|监听实例有多个终端节点组时的权重。 |
|HealthCheckIntervalSeconds|Integer|否|3|健康检查的时间间隔，单位为秒。 |
|HealthCheckPath|String|否|/healthcheck|健康检查路径。 |
|HealthCheckPort|Integer|否|20|健康检查的端口。 |
|HealthCheckProtocol|String|否|tcp|健康检查的协议。

 -   **tcp**：TCP协议。
-   **http**：HTTP协议。
-   **https**：HTTPS协议。 |
|ThresholdCount|Integer|否|3|健康检查判定终端节点为不健康的次数。 |
|EndpointRequestProtocol|String|否|HTTP|后端服务协议。取值：

 -   **HTTP**（默认值）
-   **HTTPS**

 **说明：**

-   仅为HTTP或HTTPS协议的监听实例创建终端节点组时才支持配置该项。
-   对于HTTP协议的监听实例，后端服务协议支持且仅支持HTTP。 |
|EndpointGroupType|String|否|default|终端节点组类型。取值：

 -   **default**（默认值）：默认终端节点组。
-   **virtual**：虚拟终端节点组。

 **说明：** 仅HTTP或HTTPS协议的监听实例才支持创建虚拟终端节点组。 |
|HealthCheckEnabled|Boolean|否|true|是否开启健康检查。

 -   **true**（默认值）：开启健康检查。
-   **false**：关闭健康检查。 |
|EndpointConfigurations.N.Type|String|是|Ip|终端节点类型，取值：

 -   **Domain**：自定义域名。
-   **Ip**：自定义IP。
-   **PublicIp**：阿里云公网IP。
-   **ECS**：阿里云ECS实例。
-   **SLB**：阿里云SLB实例。

 **说明：** 终端节点类型取值为**ECS**或**SLB**时，如果服务关联角色不存在，系统会自动创建一个名称为AliyunServiceRoleForGaVpcEndpoint的服务关联角色。更多信息，请参见[服务关联角色](~~178360~~)。 |
|EndpointConfigurations.N.EnableClientIPPreservation|Boolean|否|false|是否使用TOA方式开启保持客户端源IP功能，取值：

 -   **true**：开启保持客户端源IP功能。
-   **false**（默认值）：不开启保持客户端源IP功能。 |
|EndpointConfigurations.N.Weight|Integer|是|20|终端节点的权重。

 取值范围：**0**~**255**。

 **说明：** 如果某个终端节点的权重设置为0，全球加速将终止向该终端节点分发流量，请您谨慎操作。 |
|EndpointConfigurations.N.Endpoint|String|是|120.XX.XX.21|终端节点的IP或域名。 |
|PortOverrides.N.ListenerPort|Integer|否|443|配置端口映射中的监听端口。

 **说明：**

-   仅为HTTP或HTTPS协议的监听实例创建终端节点组时才支持创建端口映射关系。
-   端口映射中的监听端口必须与当前监听实例的监听端口一致。 |
|PortOverrides.N.EndpointPort|Integer|否|80|配置端口映射中的终端节点端口。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|EndpointGroupId|String|epg-bp1dmlohjjz4kqaun\*\*\*\*|终端节点组ID。 |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateEndpointGroup
&RegionId=cn-hangzhou
&ClientToken=123e4567-e89b-12d3-a456-426655440000	
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&Name=group1
&Description=EndpointGroup
&EndpointGroupRegion=cn-hangzhou
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&TrafficPercentage=20
&HealthCheckIntervalSeconds=3
&HealthCheckPath=/healthcheck
&HealthCheckPort=20
&HealthCheckProtocol=tcp
&ThresholdCount=3
&EndpointConfigurations=[{"Type":"Ip","EnableClientIPPreservation":false,"Weight":20,"Endpoint":"120.XX.XX.21"}]
&EndpointRequestProtocol=HTTP
&EndpointGroupType=default
&PortOverrides=[{"ListenerPort":443,"EndpointPort":80}]
&HealthCheckEnabled=true
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<CreateEndpointGroupResponse>
    <EndpointGroupId>epg-bp1dmlohjjz4kqaun****</EndpointGroupId>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</CreateEndpointGroupResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "EndpointGroupId" : "epg-bp1dmlohjjz4kqaun****",
  "RequestId" : "04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NotExist.ListenerPort|The listening port %s does not exist.|监听端口 %s 不存在|
|400|NoPermission.EnableHealthCheck|You do not have permission to enable health check.|没有开启健康检查的权限，请联系加白名单|
|400|NotExist.Listener|The listener does not exist.|监听器不存在|
|400|NotActive.Listener|The state of the listener is not active.|监听器状态非稳态|
|400|NotExist.Accelerator|The accelerated instance does not exist.|加速实例不存在|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|
|400|NotExist.BusinessRegion|The business region does not exist.|业务region并不存在|
|400|NotExist.BasicBandwidthPackage|You must specify the basic bandwidth package.|缺少基础带宽包|
|400|QuotaExceeded.EndPoint|The maximum number of endpoints is exceeded.|终端节点达到Quota限制|
|400|Exist.EndpointGroup|The endpoint group already exists.|终端节点组已经存在|
|400|NoPermission.VpcEndpoint|You are not authorized to perform the operation.|用户没有创建服务关联角色的权限，请联系主账号或权限管理员授权当前用户AliyunGlobalAccelerationFullAccess或者创建服务关联角色的自定义权限。自定义权限策略的相关信息包含以下内容：ServiceName为vpcendpoint.ga.aliyuncs.com，服务关联角色名称为AliyunServiceRoleForGaVpcEndpoint，执行该操作所需的用户权限为ram:CreateServiceLinkedRole。|
|400|QuotaExceeded.PortOverride|The number of port override exceeds the limit.|端口转发数量超过限制|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


# UpdateEndpointGroups

调用UpdateEndpointGroups批量修改某个监听下的终端节点组。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=UpdateEndpointGroups&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateEndpointGroups|系统规定参数。取值：**UpdateEndpointGroups**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值：**cn-hangzhou**。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|DryRun|Boolean|否|true|是否只预检此次请求，取值：

 -   **true**：发送检查请求，不会创建资源。检查项包括是否填写了必需参数、请求格式、业务限制。如果检查不通过，则返回对应错误。如果检查通过，则返回错误码`DryRunOperation`。
-   **false**（默认值）：发送正常请求，通过检查后返回HTTP 2xx状态码并直接进行操作。 |
|ListenerId|String|是|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|EndpointGroupConfigurations.N.EndpointGroupName|String|否|group1|终端节点组名称。 |
|EndpointGroupConfigurations.N.EndpointGroupDescription|String|否|group1|终端节点组的描述信息。 |
|EndpointGroupConfigurations.N.TrafficPercentage|Long|否|20|监听实例有多个终端节点组时的权重。 |
|EndpointGroupConfigurations.N.HealthCheckEnabled|Boolean|否|true|是否开启健康检查。

 -   **true**：开启健康检查。
-   **false**（默认值）：关闭健康检查。 |
|EndpointGroupConfigurations.N.HealthCheckIntervalSeconds|Long|否|3|健康检查的时间间隔，单位为秒。 |
|EndpointGroupConfigurations.N.HealthCheckPath|String|否|/healthcheck|健康检查路径。 |
|EndpointGroupConfigurations.N.HealthCheckPort|Long|否|20|健康检查的端口。 |
|EndpointGroupConfigurations.N.HealthCheckProtocol|String|否|tcp|健康检查的协议。

 -   **tcp**：TCP协议。
-   **http**：HTTP协议。
-   **https**：HTTPS协议。 |
|EndpointGroupConfigurations.N.ThresholdCount|Long|否|3|健康检查判定终端节点为不健康的次数。 |
|EndpointGroupConfigurations.N.EndpointConfigurations.N.Type|String|否|Ip|终端节点类型。

 -   **Domain**：自定义域名。
-   **Ip**：自定义IP。
-   **PublicIp**：阿里云公网IP。
-   **ECS**：阿里云ECS实例。
-   **SLB**：阿里云SLB实例。 |
|EndpointGroupConfigurations.N.EndpointConfigurations.N.Weight|Long|否|20|终端节点的权重。 |
|EndpointGroupConfigurations.N.EndpointConfigurations.N.Endpoint|String|否|120.XX.XX.21|终端节点的IP或域名。 |
|EndpointGroupConfigurations.N.EndpointRequestProtocol|String|否|HTTP|后端服务协议。取值：

 -   **HTTP**：HTTP协议。
-   **HTTPS**：HTTPS协议。 |
|EndpointGroupConfigurations.N.PortOverrides.N.ListenerPort|Long|否|443|监听端口。 |
|EndpointGroupConfigurations.N.PortOverrides.N.EndpointPort|Long|否|80|终端节点端口。 |
|EndpointGroupConfigurations.N.EnableClientIPPreservationToa|Boolean|否|false|是否使用TOA方式保留客户端源IP。取值范围：**true**或**false**（默认值）。 |
|EndpointGroupConfigurations.N.EnableClientIPPreservationProxyProtocol|Boolean|否|false|是否使用ProxyProtocol方式保留客户端源IP。取值范围：**true**或**false**（默认值）。 |
|EndpointGroupConfigurations.N.EndpointGroupId|String|是|ep-bp1d2utp8qqe2a44t3qeq|终端节点ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |
|EndpointGroupIds|Array of String|\['epg-bp1dmlohjjz4kqaun\*\*\*\*','epg-bp1v1u72cx35ogofe\*\*\*\*', ...\]|终端节点组ID列表。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateEndpointGroups
&RegionId=cn-hangzhou
&ClientToken=123e4567-e89b-12d3-a456-426655440000
&DryRun=true
&EndpointGroupConfigurations=[{"EndpointGroupName":"group1","EndpointGroupDescription":"group1","TrafficPercentage":20,"HealthCheckEnabled":true,"HealthCheckIntervalSeconds":3,"HealthCheckPath":"/healthcheck","HealthCheckPort":20,"HealthCheckProtocol":"tcp","ThresholdCount":3,"EndpointConfigurations":[{"Type":"Ip","Weight":20,"Endpoint":"120.XX.XX.21"}],"EndpointRequestProtocol":"HTTP","PortOverrides":[{"ListenerPort":443,"EndpointPort":80}],"EnableClientIPPreservationToa":false,"EnableClientIPPreservationProxyProtocol":false,"EndpointGroupId":"ep-bp1d2utp8qqe2a44t3qeq"}]
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<UpdateEndpointGroupsResponse>
    <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
    <EndpointGroupIds>['epg-bp1dmlohjjz4kqaun****','epg-bp1v1u72cx35ogofe****', ...]</EndpointGroupIds>
</UpdateEndpointGroupsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6FEA0CF3-D3B9-43E5-A304-D217037876A8",
  "EndpointGroupIds" : [ "['epg-bp1dmlohjjz4kqaun****','epg-bp1v1u72cx35ogofe****', ...]" ]
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission.EnableHealthCheck|You do not have permission to enable health check.|没有开启健康检查的权限，请联系加白名单|
|400|NotExist.EndPointGroup|The endpoint group does not exist.|终端节点组不存在|
|400|StateError.EndPointGroup|The specified state of endpoint group is invalid.|终端节点组状态非法|
|400|NotExist.Listener|The listener does not exist.|监听器不存在|
|400|NotActive.Listener|The state of the listener is not active.|监听器状态非稳态|
|400|NotExist.Accelerator|The accelerated instance does not exist.|加速实例不存在|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|
|400|QuotaExceeded.EndPoint|The maximum number of endpoints is exceeded.|终端节点达到Quota限制|
|400|NoPermission.VpcEndpoint|You are not authorized to perform the operation.|用户没有创建服务关联角色的权限，请联系主账号或权限管理员授权当前用户AliyunGlobalAccelerationFullAccess或者创建服务关联角色的自定义权限。自定义权限策略的相关信息包含以下内容：ServiceName为vpcendpoint.ga.aliyuncs.com，服务关联角色名称为AliyunServiceRoleForGaVpcEndpoint，执行该操作所需的用户权限为ram:CreateServiceLinkedRole。|
|400|QuotaExceeded.PortOverride|The number of port override exceeds the limit.|端口转发数量超过限制|

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


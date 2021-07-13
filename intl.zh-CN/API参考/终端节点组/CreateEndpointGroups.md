# CreateEndpointGroups

调用CreateEndpointGroups创建终端节点组列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=CreateEndpointGroups&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateEndpointGroups|系统规定参数。取值：**CreateEndpointGroups**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属地域ID，仅取值**cn-hangzhou**。 |
|ClientToken|String|否|1F4B6A4A-C89E-489E-BAF1-52777EE148EF|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|DryRun|Boolean|否|true|是否只预检此次请求，取值：

 -   **true**：发送检查请求，不会创建资源。检查项包括是否填写了必需参数、请求格式、业务限制。如果检查不通过，则返回对应错误。如果检查通过，则返回错误码DryRunOperation。
-   **false**（默认值）：发送正常请求，通过检查后返回HTTP 2xx状态码并直接进行操作。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|ListenerId|String|是|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|EndpointGroupConfigrations.N.EndpointGroupName|String|否|group1|终端节点组名称。 |
|EndpointGroupConfigrations.N.EndpointGroupDescription|String|否|group1|终端节点组的描述信息。 |
|EndpointGroupConfigrations.N.EndpointGroupRegion|String|是|cn-hangzhou|终端节点组所属的地域ID。 |
|EndpointGroupConfigrations.N.TrafficPercentage|Long|否|20|监听实例有多个终端节点组时的权重。 |
|EndpointGroupConfigrations.N.HealthCheckEnabled|Boolean|否|true|是否开启健康检查。

 -   **true**：开启健康检查。
-   **false**：关闭健康检查。 |
|EndpointGroupConfigrations.N.HealthCheckIntervalSeconds|Long|否|3|健康检查的时间间隔，单位为秒。 |
|EndpointGroupConfigrations.N.HealthCheckPath|String|否|/healthcheck|健康检查路径。 |
|EndpointGroupConfigrations.N.HealthCheckPort|Long|否|20|健康检查的端口。 |
|EndpointGroupConfigrations.N.HealthCheckProtocol|String|否|tcp|健康检查的协议。

 -   **tcp**：TCP协议。
-   **http**：HTTP协议。
-   **https**：HTTPS协议。 |
|EndpointGroupConfigrations.N.ThresholdCount|Long|否|3|健康检查判定终端节点为不健康的次数。 |
|EndpointGroupConfigrations.N.EndpointConfigurations.N.Type|String|否|Ip|终端节点类型。

 -   **Domain**：自定义域名。
-   **Ip**：自定义IP。
-   **PublicIp**：阿里云公网IP。
-   **ECS**：阿里云ECS实例。
-   **SLB**：阿里云SLB实例。 |
|EndpointGroupConfigrations.N.EndpointConfigurations.N.Weight|Long|否|20|终端节点的权重。 |
|EndpointGroupConfigrations.N.EndpointConfigurations.N.Endpoint|String|否|120.XX.XX.21|终端节点的IP或域名。 |
|EndpointGroupConfigrations.N.EndpointRequestProtocol|String|否|HTTP|后端服务协议。

 -   **HTTP**
-   **HTTPS** |
|EndpointGroupConfigrations.N.EndpointGroupType|String|否|default|终端节点组类型。

 -   **default**：默认终端节点组。
-   **virtual**：虚拟终端节点组。 |
|EndpointGroupConfigrations.N.PortOverrides.N.ListenerPort|Long|否|443|监听端口。 |
|EndpointGroupConfigrations.N.PortOverrides.N.EndpointPort|Long|否|80|终端节点端口。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |
|EndpointGroupIds|Array of String|\['epg-bp1dmlohjjz4kqaun\*\*\*\*','epg-bp1v1u72cx35ogofe\*\*\*\*', ...\]|终端节点组ID列表。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateEndpointGroups
&RegionId=cn-hangzhou
&ClientToken=1F4B6A4A-C89E-489E-BAF1-52777EE148EF
&DryRun=true
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&EndpointGroupConfigrations=[{"EndpointGroupName":"group1","EndpointGroupDescription":"group1","EndpointGroupRegion":"cn-hangzhou","TrafficPercentage":20,"HealthCheckEnabled":true,"HealthCheckIntervalSeconds":3,"HealthCheckPath":"/healthcheck","HealthCheckPort":20,"HealthCheckProtocol":"tcp","ThresholdCount":3,"EndpointConfigurations":[{"Type":"Ip","Weight":20,"Endpoint":"120.XX.XX.21"}],"EndpointRequestProtocol":"HTTP","EndpointGroupType":"default","PortOverrides":[{"ListenerPort":443,"EndpointPort":80}]}]
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<CreateEndpointGroupsResponse>
    <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
    <EndpointGroupIds>['epg-bp1dmlohjjz4kqaun****','epg-bp1v1u72cx35ogofe****', ...]</EndpointGroupIds>
</CreateEndpointGroupsResponse>
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

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


# DescribeEndpointGroup

调用DescribeEndpointGroup查询指定终端节点组信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DescribeEndpointGroup&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeEndpointGroup|系统规定参数。取值：**DescribeEndpointGroup**。 |
|EndpointGroupId|String|是|epg-bp14sz7ftcwwjgrdm\*\*\*\*|要查询的终端节点组的ID。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属地域ID，仅取值**cn-hangzhou**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Description|String|group1|终端节点组的描述信息。 |
|EndpointConfigurations|Array of EndpointConfigurations| |终端节点配置信息。 |
|EnableClientIPPreservation|Boolean|false|是否开启了保持客户端源IP功能。

 -   **true**：开启了保持客户端源IP功能。
-   **false**：未开启保持客户端源IP功能。 |
|Endpoint|String|120.XX.XX.21|终端节点的IP或域名。 |
|ProbePort|Integer|80|延时监控的探测端口。 |
|ProbeProtocol|String|tcp|延时监控的探测协议。

 -   **icmp**：icms协议。
-   **tcp**：tcp协议。 |
|Type|String|Ip|终端节点类型。

 -   **Domain**：自定义域名。
-   **Ip**：自定义IP。
-   **PublicIp**：阿里云公网IP。
-   **ECS**：阿里云ECS实例。
-   **SLB**：阿里云SLB实例。 |
|Weight|Integer|20|终端节点的权重。 |
|EndpointGroupId|String|epg-bp14sz7ftcwwjgrdm\*\*\*\*|终端节点组ID。 |
|EndpointGroupRegion|String|cn-hangzhou|终端节点组所属的地域ID。 |
|EndpointGroupType|String|default|终端节点组类型。

 -   **default**：默认终端节点组。
-   **virtual**：虚拟终端节点组。 |
|EndpointRequestProtocol|String|HTTP|后端服务协议。

 -   **HTTP**
-   **HTTPS** |
|ForwardingRuleIds|List|frule-bp19a3t3yzr21q3\*\*\*\*|终端节点组关联的转发策略ID。 |
|HealthCheckIntervalSeconds|Integer|3|健康检查的时间间隔，单位为秒。 |
|HealthCheckPath|String|/healthcheck|健康检查路径。 |
|HealthCheckPort|Integer|20|健康检查的端口。 |
|HealthCheckProtocol|String|tcp|健康检查的协议。

 -   **tcp**：TCP协议。
-   **http**：HTTP协议。
-   **https**：HTTPS协议。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|Name|String|group1|终端节点组的名称。 |
|PortOverrides|Array of PortOverrides| |端口映射关系。 |
|EndpointPort|Integer|80|终端节点端口。 |
|ListenerPort|Integer|443|监听端口。 |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |
|State|String|active|终端节点组的状态。

 -   **init**：初始化。
-   **active**：正常。
-   **creating**：创建中。
-   **configuring**：配置中。 |
|ThresholdCount|Integer|3|健康检查判定终端节点为不健康的次数。 |
|TotalCount|Integer|10|列表条目数。 |
|TrafficPercentage|Integer|20|监听实例有多个终端节点组时的权重。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeEndpointGroup
&EndpointGroupId=epg-bp14sz7ftcwwjgrdm****
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DescribeEndpointGroupResponse>
  <EndpointGroupId>epg-bp14sz7ftcwwjgrdm****</EndpointGroupId>
  <RequestId>5B79B4DF-FF0C-480B-B4E3-77C53B52C852</RequestId>
  <ThresholdCount>3</ThresholdCount>
  <EndpointRequestProtocol>HTTP</EndpointRequestProtocol>
  <PortOverrides>
        <ListenerPort>443</ListenerPort>
        <EndpointPort>100</EndpointPort>
  </PortOverrides>
  <EndpointGroupRegion>cn-hangzhou</EndpointGroupRegion>
  <State>active</State>
  <EndpointConfigurations>
        <Type>PublicIp</Type>
        <Endpoint>114.XX.XX.209</Endpoint>
        <EnableClientIPPreservation>false</EnableClientIPPreservation>
        <Weight>200</Weight>
  </EndpointConfigurations>
  <EndpointGroupType>default</EndpointGroupType>
  <ListenerId>lsr-bp1s0vzbi5bxlx5pw****</ListenerId>
</DescribeEndpointGroupResponse>
```

`JSON`格式

```
{
  "ForwardingRuleIds": [],
  "EndpointGroupId": "epg-bp14sz7ftcwwjgrdm****",
  "RequestId": "5B79B4DF-FF0C-480B-B4E3-77C53B52C852",
  "ThresholdCount": 3,
  "EndpointRequestProtocol": "HTTP",
  "PortOverrides": [
    {
      "ListenerPort": 443,
      "EndpointPort": 100
    }
  ],
  "EndpointGroupRegion": "cn-hangzhou",
  "State": "active",
  "EndpointConfigurations": [
    {
      "Type": "PublicIp",
      "Endpoint": "114.XX.XX.209",
      "EnableClientIPPreservation": false,
      "Weight": 200
    }
  ],
  "EndpointGroupType": "default",
  "ListenerId": "lsr-bp1s0vzbi5bxlx5pw****"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


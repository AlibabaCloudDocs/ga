# ListEndpointGroups

调用ListEndpointGroups查询终端节点组列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListEndpointGroups&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListEndpointGroups|系统规定参数。取值：**ListEndpointGroups**。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。 |
|ListenerId|String|否|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|EndpointGroupType|String|否|virtual|终端节点组类型。取值：

 -   **default**：默认终端节点组。
-   **virtual**：虚拟终端节点组。
-   空值：表示查询所有默认终端节点组和虚拟终端节点组。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|EndpointGroups|Array of EndpointGroups| |终端节点组配置信息。 |
|Description|String|group1|终端节点组的描述信息。 |
|EndpointConfigurations|Array of EndpointConfigurations| |终端节点配置信息。 |
|EnableClientIPPreservation|Boolean|false|是否开启保持客户端源IP功能。

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
|EndpointGroupId|String|epg-bp16jdc00bhe97sr5\*\*\*\*|终端节点组ID。 |
|EndpointGroupIpList|List|101.XX.XX.22|下车点IP列表。 |
|EndpointGroupRegion|String|cn-hangzhou|终端节点组所属的地域ID。 |
|EndpointGroupType|String|default|终端节点组类型。取值：

 -   **default**：默认终端节点组。
-   **virtual**：虚拟终端节点组。 |
|EndpointRequestProtocol|String|HTTP|后端服务协议。取值：

 -   **HTTP**
-   **HTTPS** |
|ForwardingRuleIds|List|frule-bp19a3t3yzr21q3\*\*\*\*|终端节点组关联的转发策略ID。 |
|HealthCheckIntervalSeconds|Integer|3|健康检查的时间间隔，单位为秒。 |
|HealthCheckPath|String|/healthcheck|健康检查路径。 |
|HealthCheckPort|Integer|10|健康检查的端口。 |
|HealthCheckProtocol|String|tcp|健康检查的协议。

 -   **tcp**：TCP协议。
-   **http**：HTTP协议。
-   **https**：HTTPS协议。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|Name|String|group1|终端节点组的名称。 |
|PortOverrides|Array of PortOverrides| |端口映射关系。 |
|EndpointPort|Integer|80|终端节点端口。 |
|ListenerPort|Integer|443|监听端口。 |
|State|String|active|终端节点组的状态。

 -   **init**：初始化。
-   **active**：正常。
-   **creating**：创建中。
-   **configuring**：配置中。 |
|ThresholdCount|Integer|3|健康检查判定终端节点为不健康的次数。 |
|TrafficPercentage|Integer|20|监听有多个终端节点组时的权重。 |
|PageNumber|Integer|1|当前页码。 |
|PageSize|Integer|10|每页包含的条目数。 |
|RequestId|String|A052D49E-CCC2-41DB-816C-DC3381503194|请求ID。 |
|TotalCount|Integer|10|列表条目数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListEndpointGroups
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListEndpointGroupsResponse>
  <TotalCount>1</TotalCount>
  <RequestId>A052D49E-CCC2-41DB-816C-DC3381503194</RequestId>
  <PageSize>10</PageSize>
  <PageNumber>1</PageNumber>
  <EndpointGroups>
        <EndpointGroupIpList>39.XX.XX.42</EndpointGroupIpList>
        <EndpointGroupIpList>39.XX.XX.106</EndpointGroupIpList>
        <EndpointGroupIpList>47.XX.XX.140</EndpointGroupIpList>
        <EndpointGroupIpList>39.XX.XX.162</EndpointGroupIpList>
        <EndpointGroupRegion>cn-hangzhou</EndpointGroupRegion>
        <EndpointGroupId>epg-bp16jdc00bhe97sr5****</EndpointGroupId>
        <State>active</State>
        <ThresholdCount>3</ThresholdCount>
        <EndpointConfigurations>
              <EnableProxyProtocol>false</EnableProxyProtocol>
              <Type>PublicIp</Type>
              <Endpoint>123.XX.XX.108</Endpoint>
              <EnableClientIPPreservation>true</EnableClientIPPreservation>
              <Weight>100</Weight>
        </EndpointConfigurations>
        <EndpointGroupType>default</EndpointGroupType>
        <ListenerId>lsr-bp1bpn0kn908w4nbw****</ListenerId>
  </EndpointGroups>
</ListEndpointGroupsResponse>
```

`JSON`格式

```
{
  "TotalCount": 1,
  "RequestId": "A052D49E-CCC2-41DB-816C-DC3381503194",
  "PageSize": 10,
  "PageNumber": 1,
  "EndpointGroups": [
    {
      "EndpointGroupIpList": [
        "39.XX.XX.42",
        "39.XX.XX.106",
        "47.XX.XX.140",
        "39.XX.XX.162"
      ],
      "PortOverrides": [],
      "EndpointGroupRegion": "cn-hangzhou",
      "ForwardingRuleIds": [],
      "EndpointGroupId": "epg-bp16jdc00bhe97sr5****",
      "State": "active",
      "ThresholdCount": 3,
      "EndpointConfigurations": [
        {
          "EnableProxyProtocol": false,
          "Type": "PublicIp",
          "Endpoint": "123.XX.XX.108",
          "EnableClientIPPreservation": true,
          "Weight": 100
        }
      ],
      "EndpointGroupType": "default",
      "ListenerId": "lsr-bp1bpn0kn908w4nbw****"
    }
  ]
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


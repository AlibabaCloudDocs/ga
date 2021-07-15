# ListEndpointGroups

调用ListEndpointGroups查询终端节点组列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListEndpointGroups&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListEndpointGroups|系统规定参数。取值：**ListEndpointGroups**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|ListenerId|String|否|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|EndpointGroupType|String|否|virtual|终端节点组类型。取值：

 -   **default**：默认终端节点组。
-   **virtual**：虚拟终端节点组。
-   空值：表示查询所有默认终端节点组和虚拟终端节点组。 |
|AccessLogSwitch|String|否|on|是否开启访问日志。取值:

 -   **on**：开启访问日志。
-   **off**（默认值）：关闭访问日志。 |
|EndpointGroupId|String|否|epg-bp16jdc00bhe97sr5\*\*\*\*|终端节点组ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|TotalCount|Integer|10|列表条目数。 |
|PageSize|Integer|10|每页包含的条目数。 |
|RequestId|String|A052D49E-CCC2-41DB-816C-DC3381503194|请求ID。 |
|PageNumber|Integer|1|当前页码。 |
|EndpointGroups|Array of EndpointGroups| |终端节点组配置信息。 |
|EndpointGroupId|String|epg-bp16jdc00bhe97sr5\*\*\*\*|终端节点组ID。 |
|EndpointGroupIpList|Array of String|101.XX.XX.22|加速区域列表。 |
|EndpointGroupUnconfirmedIpList|Array of String|101.XX.XX.22|全球加速实例升级后新增待确认的终端节点组IP列表。 |
|State|String|active|终端节点组的状态。

 -   **init**：初始化。
-   **active**：正常。
-   **creating**：创建中。
-   **configuring**：配置中。 |
|HealthCheckPath|String|/healthcheck|健康检查路径。 |
|EndpointGroupRegion|String|cn-hangzhou|终端节点组所属的地域ID。 |
|HealthCheckIntervalSeconds|Integer|3|健康检查的时间间隔，单位为秒。 |
|TrafficPercentage|Integer|20|监听有多个终端节点组时的权重。 |
|HealthCheckProtocol|String|tcp|健康检查的协议。

 -   **tcp**：TCP协议。
-   **http**：HTTP协议。
-   **https**：HTTPS协议。 |
|ThresholdCount|Integer|3|健康检查判定终端节点为不健康的次数。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|AcceleratorId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|EndpointConfigurations|Array of EndpointConfigurations| |终端节点配置信息。 |
|Type|String|Ip|终端节点类型。

 -   **Domain**：自定义域名。
-   **Ip**：自定义IP。
-   **PublicIp**：阿里云公网IP。
-   **ECS**：阿里云ECS实例。
-   **SLB**：阿里云SLB实例。 |
|EnableClientIPPreservation|Boolean|false|是否开启保持客户端源IP功能。

 -   **true**：开启了保持客户端源IP功能。
-   **false**：未开启保持客户端源IP功能。 |
|Weight|Integer|20|终端节点的权重。 |
|ProbeProtocol|String|tcp|延时监控的探测协议。

 -   **icmp**：ICMP协议。
-   **tcp**：TCP协议。 |
|Endpoint|String|120.XX.XX.21|终端节点的IP或域名。 |
|ProbePort|Integer|80|延时监控的探测端口。 |
|EndpointId|String|ep-bp1d2utp8qqe2a44t3qeq|终端节点ID。 |
|PortOverrides|Array of PortOverrides| |端口映射关系。 |
|ListenerPort|Integer|443|监听端口。 |
|EndpointPort|Integer|80|终端节点端口。 |
|ForwardingRuleIds|Array of String|frule-bp19a3t3yzr21q3\*\*\*\*|终端节点组关联的转发策略ID。 |
|EndpointGroupType|String|default|终端节点组类型。取值：

 -   **default**：默认终端节点组。
-   **virtual**：虚拟终端节点组。 |
|EndpointRequestProtocol|String|HTTP|后端服务协议。取值：

 -   **HTTP**：HTTP协议。
-   **HTTPS**：HTTPS协议。 |
|Description|String|group1|终端节点组的描述信息。 |
|Name|String|group1|终端节点组的名称。 |
|HealthCheckPort|Integer|10|健康检查的端口。 |
|HealthCheckEnabled|Boolean|true|是否开启健康检查。

 -   **true**（默认值）：开启健康检查。
-   **false**：关闭健康检查。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListEndpointGroups
&RegionId=cn-hangzhou
&PageNumber=1
&PageSize=10
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&EndpointGroupType=virtual
&AccessLogSwitch=on
&EndpointGroupId=epg-bp16jdc00bhe97sr5****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListEndpointGroupsResponse>
    <TotalCount>10</TotalCount>
    <PageSize>10</PageSize>
    <RequestId>A052D49E-CCC2-41DB-816C-DC3381503194	</RequestId>
    <PageNumber>1</PageNumber>
    <EndpointGroups>
        <EndpointGroupId>epg-bp16jdc00bhe97sr5****</EndpointGroupId>
        <EndpointGroupIpList>101.XX.XX.22</EndpointGroupIpList>
        <EndpointGroupUnconfirmedIpList>101.XX.XX.22</EndpointGroupUnconfirmedIpList>
        <State>active</State>
        <HealthCheckPath>/healthcheck</HealthCheckPath>
        <EndpointGroupRegion>cn-hangzhou</EndpointGroupRegion>
        <HealthCheckIntervalSeconds>3</HealthCheckIntervalSeconds>
        <TrafficPercentage>20</TrafficPercentage>
        <HealthCheckProtocol>tcp</HealthCheckProtocol>
        <ThresholdCount>3</ThresholdCount>
        <ListenerId>lsr-bp1bpn0kn908w4nbw****</ListenerId>
        <AcceleratorId>ga-bp1odcab8tmno0hdq****</AcceleratorId>
        <EndpointConfigurations>
            <Type>Ip</Type>
            <EnableClientIPPreservation>false</EnableClientIPPreservation>
            <Weight>20</Weight>
            <ProbeProtocol>tcp</ProbeProtocol>
            <Endpoint>120.XX.XX.21</Endpoint>
            <ProbePort>80</ProbePort>
            <EndpointId>ep-bp1d2utp8qqe2a44t3qeq</EndpointId>
        </EndpointConfigurations>
        <PortOverrides>
            <ListenerPort>443</ListenerPort>
            <EndpointPort>80</EndpointPort>
        </PortOverrides>
        <ForwardingRuleIds>frule-bp19a3t3yzr21q3****</ForwardingRuleIds>
        <EndpointGroupType>default</EndpointGroupType>
        <EndpointRequestProtocol>HTTP</EndpointRequestProtocol>
        <Description>group1</Description>
        <Name>group1</Name>
        <HealthCheckPort>10</HealthCheckPort>
        <HealthCheckEnabled>true</HealthCheckEnabled>
    </EndpointGroups>
</ListEndpointGroupsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "TotalCount" : 10,
  "PageSize" : 10,
  "RequestId" : "A052D49E-CCC2-41DB-816C-DC3381503194\t",
  "PageNumber" : 1,
  "EndpointGroups" : [ {
    "EndpointGroupId" : "epg-bp16jdc00bhe97sr5****",
    "EndpointGroupIpList" : [ "101.XX.XX.22" ],
    "EndpointGroupUnconfirmedIpList" : [ "101.XX.XX.22" ],
    "State" : "active",
    "HealthCheckPath" : "/healthcheck",
    "EndpointGroupRegion" : "cn-hangzhou",
    "HealthCheckIntervalSeconds" : 3,
    "TrafficPercentage" : 20,
    "HealthCheckProtocol" : "tcp",
    "ThresholdCount" : 3,
    "ListenerId" : "lsr-bp1bpn0kn908w4nbw****",
    "AcceleratorId" : "ga-bp1odcab8tmno0hdq****",
    "EndpointConfigurations" : [ {
      "Type" : "Ip",
      "EnableClientIPPreservation" : false,
      "Weight" : 20,
      "ProbeProtocol" : "tcp",
      "Endpoint" : "120.XX.XX.21",
      "ProbePort" : 80,
      "EndpointId" : "ep-bp1d2utp8qqe2a44t3qeq"
    } ],
    "PortOverrides" : [ {
      "ListenerPort" : 443,
      "EndpointPort" : 80
    } ],
    "ForwardingRuleIds" : [ "frule-bp19a3t3yzr21q3****" ],
    "EndpointGroupType" : "default",
    "EndpointRequestProtocol" : "HTTP",
    "Description" : "group1",
    "Name" : "group1",
    "HealthCheckPort" : 10,
    "HealthCheckEnabled" : true
  } ]
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


# DescribeEndpointGroup

调用DescribeEndpointGroup查询指定终端节点组信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DescribeEndpointGroup&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeEndpointGroup|系统规定参数。取值：**DescribeEndpointGroup**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属地域ID，仅取值**cn-hangzhou**。 |
|EndpointGroupId|String|是|epg-bp14sz7ftcwwjgrdm\*\*\*\*|要查询的终端节点组的ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|HealthCheckIntervalSeconds|Integer|3|健康检查的时间间隔，单位为秒。 |
|TrafficPercentage|Integer|20|监听实例有多个终端节点组时的权重。 |
|EndpointGroupId|String|epg-bp14sz7ftcwwjgrdm\*\*\*\*|终端节点组ID。 |
|Description|String|group1|终端节点组的描述信息。 |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |
|HealthCheckPath|String|/healthcheck|健康检查路径。 |
|ThresholdCount|Integer|3|健康检查判定终端节点为不健康的次数。 |
|Name|String|group1|终端节点组的名称。 |
|EndpointGroupRegion|String|cn-hangzhou|终端节点组所属的地域ID。 |
|TotalCount|Integer|10|列表条目数。 |
|State|String|active|终端节点组的状态。

 -   **init**：初始化。
-   **active**：正常。
-   **creating**：创建中。
-   **configuring**：配置中。 |
|HealthCheckProtocol|String|tcp|健康检查的协议。

 -   **tcp**：TCP协议。
-   **http**：HTTP协议。
-   **https**：HTTPS协议。 |
|HealthCheckPort|Integer|20|健康检查的端口。 |
|EndpointConfigurations|Array of EndpointConfigurations| |终端节点配置信息。 |
|Type|String|Ip|终端节点类型。

 -   **Domain**：自定义域名。
-   **Ip**：自定义IP。
-   **PublicIp**：阿里云公网IP。
-   **ECS**：阿里云ECS实例。
-   **SLB**：阿里云SLB实例。 |
|EnableClientIPPreservation|Boolean|false|是否开启了保持客户端源IP功能。

 -   **true**：开启了保持客户端源IP功能。
-   **false**：未开启保持客户端源IP功能。 |
|Weight|Integer|20|终端节点的权重。 |
|ProbeProtocol|String|tcp|时延探测协议。取值范围：

 -   **tcp**：TCP协议。
-   **icmp**：ICMP协议。 |
|Endpoint|String|120.XX.XX.21|终端节点的IP或域名。 |
|ProbePort|Integer|80|延时监控的探测端口。 |
|PortOverrides|Array of PortOverrides| |端口映射关系。 |
|ListenerPort|Integer|443|监听端口。 |
|EndpointPort|Integer|80|终端节点端口。 |
|EndpointRequestProtocol|String|HTTP|后端服务协议。

 -   **HTTP**
-   **HTTPS** |
|EndpointGroupType|String|default|终端节点组类型。

 -   **default**：默认终端节点组。
-   **virtual**：虚拟终端节点组。 |
|ForwardingRuleIds|Array of String|frule-bp19a3t3yzr21q3\*\*\*\*|终端节点组关联的转发策略ID。 |
|AcceleratorId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|SlsRegion|String|cn-hangzhou|SLS地域。 |
|SlsProjectName|String|pn-01|SLS项目名称。 |
|SlsLogStoreName|String|lsn-01|SLS日志库名称。 |
|AccessLogSwitch|String|on|日志绑定状态。取值:

 -   **on**：已绑定
-   **off**：未绑定
-   **binding**：绑定中
-   **unbinding**：未绑定 |
|EnableAccessLog|Boolean|on|是否开启访问日志。取值:

 -   **on**：开启访问日志。
-   **off**：关闭访问日志。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeEndpointGroup
&RegionId=cn-hangzhou
&EndpointGroupId=epg-bp14sz7ftcwwjgrdm****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeEndpointGroupResponse>
    <HealthCheckIntervalSeconds>3</HealthCheckIntervalSeconds>
    <TrafficPercentage>20</TrafficPercentage>
    <EndpointGroupId>epg-bp14sz7ftcwwjgrdm****</EndpointGroupId>
    <Description>group1</Description>
    <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8	</RequestId>
    <HealthCheckPath>/healthcheck</HealthCheckPath>
    <ThresholdCount>3</ThresholdCount>
    <Name>group1</Name>
    <EndpointGroupRegion>cn-hangzhou</EndpointGroupRegion>
    <TotalCount>10</TotalCount>
    <State>active</State>
    <HealthCheckProtocol>tcp</HealthCheckProtocol>
    <HealthCheckPort>20</HealthCheckPort>
    <EndpointConfigurations>
        <Type>Ip</Type>
        <EnableClientIPPreservation>false</EnableClientIPPreservation>
        <Weight>20</Weight>
        <ProbeProtocol>tcp</ProbeProtocol>
        <Endpoint>120.XX.XX.21</Endpoint>
        <ProbePort>80</ProbePort>
    </EndpointConfigurations>
    <PortOverrides>
        <ListenerPort>443</ListenerPort>
        <EndpointPort>80</EndpointPort>
    </PortOverrides>
    <EndpointRequestProtocol>HTTP</EndpointRequestProtocol>
    <EndpointGroupType>default</EndpointGroupType>
    <ForwardingRuleIds>frule-bp19a3t3yzr21q3****</ForwardingRuleIds>
    <AcceleratorId>ga-bp1odcab8tmno0hdq****</AcceleratorId>
    <ListenerId>lsr-bp1bpn0kn908w4nbw****</ListenerId>
    <SlsRegion>cn-hangzhou</SlsRegion>
    <SlsProjectName>pn-01</SlsProjectName>
    <SlsLogStoreName>lsn-01</SlsLogStoreName>
    <AccessLogSwitch>on</AccessLogSwitch>
    <EnableAccessLog>false</EnableAccessLog>
</DescribeEndpointGroupResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "HealthCheckIntervalSeconds" : 3,
  "TrafficPercentage" : 20,
  "EndpointGroupId" : "epg-bp14sz7ftcwwjgrdm****",
  "Description" : "group1",
  "RequestId" : "6FEA0CF3-D3B9-43E5-A304-D217037876A8\t",
  "HealthCheckPath" : "/healthcheck",
  "ThresholdCount" : 3,
  "Name" : "group1",
  "EndpointGroupRegion" : "cn-hangzhou",
  "TotalCount" : 10,
  "State" : "active",
  "HealthCheckProtocol" : "tcp",
  "HealthCheckPort" : 20,
  "EndpointConfigurations" : [ {
    "Type" : "Ip",
    "EnableClientIPPreservation" : false,
    "Weight" : 20,
    "ProbeProtocol" : "tcp",
    "Endpoint" : "120.XX.XX.21",
    "ProbePort" : 80
  } ],
  "PortOverrides" : [ {
    "ListenerPort" : 443,
    "EndpointPort" : 80
  } ],
  "EndpointRequestProtocol" : "HTTP",
  "EndpointGroupType" : "default",
  "ForwardingRuleIds" : [ "frule-bp19a3t3yzr21q3****" ],
  "AcceleratorId" : "ga-bp1odcab8tmno0hdq****",
  "ListenerId" : "lsr-bp1bpn0kn908w4nbw****",
  "SlsRegion" : "cn-hangzhou",
  "SlsProjectName" : "pn-01",
  "SlsLogStoreName" : "lsn-01",
  "AccessLogSwitch" : "on",
  "EnableAccessLog" : false
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


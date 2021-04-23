# DescribeEndpointGroup

Queries the information about an endpoint group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=DescribeEndpointGroup&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeEndpointGroup|The operation that you want to perform. Set the value to **DescribeEndpointGroup**. |
|EndpointGroupId|String|Yes|epg-bp14sz7ftcwwjgrdm\*\*\*\*|The ID of the endpoint group. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the Global Accelerator \(GA\) instance. Set the value to **cn-hangzhou**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Description|String|group1|The description of the endpoint group. |
|EndpointConfigurations|Array of EndpointConfigurations| |The configuration of the endpoint. |
|EnableClientIPPreservation|Boolean|false|Indicates whether client IP addresses are reserved. Valid values:

 -   **true**: Client IP addresses are reserved.
-   **false**: Client IP addresses are not reserved. |
|Endpoint|String|120.XX.XX.21|The IP address or domain name of the endpoint. |
|ProbePort|Integer|80|The port that is used to monitor latency. |
|ProbeProtocol|String|tcp|The protocol that is used to monitor latency. Valid values:

 -   **icmp**: Inter-Carrier Messaging Service \(ICMS\)
-   **tcp**: Transmission Control Protocol \(TCP\) |
|Type|String|Ip|The type of the endpoint. Valid values:

 -   **Domain**: a custom domain name
-   **Ip**: a custom IP address
-   **PublicIp**: an Alibaba Cloud public IP address
-   **ECS**: an Elastic Compute Service \(ECS\) instance
-   **SLB**: a Server Load Balancer \(SLB\) instance |
|Weight|Integer|20|The weight of the endpoint. |
|EndpointGroupId|String|epg-bp14sz7ftcwwjgrdm\*\*\*\*|The ID of the endpoint group. |
|EndpointGroupRegion|String|cn-hangzhou|The ID of the region where the endpoint group is deployed. |
|EndpointGroupType|String|default|The type of the endpoint group. Valid values:

 -   **default**: a default endpoint group
-   **virtual**: a virtual endpoint group |
|EndpointRequestProtocol|String|HTTP|The protocol of the backend service.

 -   **HTTP**
-   **HTTPS** |
|ForwardingRuleIds|List|frule-bp19a3t3yzr21q3\*\*\*\*|The ID of the forwarding rule that is associated with the endpoint group. |
|HealthCheckIntervalSeconds|Integer|3|The interval at which health checks are performed. Unit: seconds. |
|HealthCheckPath|String|/healthcheck|The path of the health check. |
|HealthCheckPort|Integer|20|The port of the health check. |
|HealthCheckProtocol|String|tcp|The protocol of the health check. Valid values:

 -   **tcp**: TCP
-   **http**: HTTP
-   **https**: HTTPS |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|The ID of the listener. |
|Name|String|group1|The name of the endpoint group. |
|PortOverrides|Array of PortOverrides| |The port mapping correlation. |
|EndpointPort|Integer|80|The endpoint port. |
|ListenerPort|Integer|443|The listener port. |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|The ID of the request. |
|State|String|active|The state of the endpoint group. Valid values:

 -   **init**: The endpoint group is being initialized.
-   **active**: The endpoint group is running as expected.
-   **creating**: The endpoint group is being created.
-   **configuring**: The endpoint group is being configured. |
|ThresholdCount|Integer|3|The number of consecutive failed heath checks that must occur before an endpoint can be considered unhealthy. |
|TotalCount|Integer|10|The total number of entries. |
|TrafficPercentage|Integer|20|The weight of the listener if the listener is associated with multiple endpoint groups. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeEndpointGroup
&EndpointGroupId=epg-bp14sz7ftcwwjgrdm****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

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

`JSON` format

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

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


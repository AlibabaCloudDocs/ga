# ListEndpointGroups

Queries endpoint groups.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=ListEndpointGroups&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListEndpointGroups|The operation that you want to perform. Set the value to **ListEndpointGroups**. |
|AcceleratorId|String|Yes|ga-bp1odcab8tmno0hdq\*\*\*\*|The ID of the Global Accelerator \(GA\) instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the GA instance is deployed. Set the value to **cn-hangzhou**. |
|PageNumber|Integer|No|1|The number of the page to return. Default value: **1**. |
|PageSize|Integer|No|10|The number of entries to return on each page. Maximum value: **50**. Default value: **10**. |
|ListenerId|String|No|lsr-bp1bpn0kn908w4nbw\*\*\*\*|The ID of the listener. |
|EndpointGroupType|String|No|virtual|The type of the endpoint group. Valid values:

-   **default**: a default endpoint group
-   **virtual**: a virtual endpoint group
-   If you leave this parameter empty, all default and virtual endpoint groups are queried. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|EndpointGroups|Array of EndpointGroups| |The configuration of the endpoint group. |
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
-   **ECS**: an Alibaba Cloud Elastic Compute Service \(ECS\) instance
-   **SLB**: an Alibaba Cloud Server Load Balancer \(SLB\) instance |
|Weight|Integer|20|The weight of the endpoint. |
|EndpointGroupId|String|epg-bp16jdc00bhe97sr5\*\*\*\*|The ID of the endpoint group. |
|EndpointGroupIpList|List|101.XX.XX.22|Endpoint Group IP list. |
|EndpointGroupRegion|String|cn-hangzhou|The ID of the region where the endpoint group is deployed. |
|EndpointGroupType|String|default|The type of the endpoint group. Valid values:

-   **default**: a default endpoint group
-   **virtual**: a virtual endpoint group |
|EndpointRequestProtocol|String|HTTP|The protocol of the backend service. Valid values:

-   **HTTP**
-   **HTTPS** |
|ForwardingRuleIds|List|frule-bp19a3t3yzr21q3\*\*\*\*|The ID of the forwarding rule that is associated with the endpoint group. |
|HealthCheckIntervalSeconds|Integer|3|The interval at which health checks are performed. Unit: seconds. |
|HealthCheckPath|String|/healthcheck|The path of the health check. |
|HealthCheckPort|Integer|10|The port of the health check. |
|HealthCheckProtocol|String|tcp|The protocol of the health check.

-   **tcp**: TCP
-   **http**: HTTP
-   **https**: HTTPS |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|The ID of the listener. |
|Name|String|group1|The name of the endpoint group. |
|PortOverrides|Array of PortOverrides| |The port mapping correlation. |
|EndpointPort|Integer|80|The endpoint port. |
|ListenerPort|Integer|443|The listener port. |
|State|String|active|The state of the endpoint group. Valid values:

-   **init**: The endpoint group is being initialized.
-   **active**: The endpoint group is running as expected.
-   **creating**: The endpoint group is being created.
-   **configuring**: The listener is being configured. |
|ThresholdCount|Integer|3|The number of consecutive failed heath checks that must occur before an endpoint can be considered unhealthy. |
|TrafficPercentage|Integer|20|The weight of the listener when the listener is associated with multiple endpoint groups. |
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|10|The number of entries returned per page. |
|RequestId|String|A052D49E-CCC2-41DB-816C-DC3381503194|The ID of the request. |
|TotalCount|Integer|10|The total number of entries returned. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=ListEndpointGroups
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

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

`JSON` format

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

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


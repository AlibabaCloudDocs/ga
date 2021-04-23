# CreateEndpointGroup

Creates an endpoint group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=CreateEndpointGroup&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateEndpointGroup|The operation that you want to perform. Set the value to **CreateEndpointGroup**. |
|AcceleratorId|String|Yes|ga-bp1odcab8tmno0hdq\*\*\*\*|The ID of the Global Accelerator \(GA\) instance. |
|EndpointConfigurations.N.Endpoint|String|Yes|120.XX.XX.21|The IP address or domain name of the endpoint. |
|EndpointConfigurations.N.Type|String|Yes|Ip|The type of the endpoint. Valid values:

 -   **Domain**: a custom domain name
-   **Ip**: a custom IP address
-   **PublicIp**: an Alibaba Cloud public IP address
-   **ECS**: an Elastic Compute Service \(ECS\) instance
-   **SLB**: a Server Load Balancer \(SLB\) instance

 **Note:** You can set the endpoint type to **ECS** or **SLB**. If a service-linked role does not exist, the system automatically creates the service-linked role AliyunServiceRoleForGaVpcEndpoint. For more information, see [Service-linked roles](~~178360~~). |
|EndpointConfigurations.N.Weight|Integer|Yes|20|The weight of the endpoint.

 Valid values: **0** to **255**.

 **Note:** If you set the weight of an endpoint to 0, GA stops distributing network traffic to the endpoint. Proceed with caution. |
|EndpointGroupRegion|String|Yes|cn-hangzhou|The ID of the region where the endpoint group is deployed. |
|ListenerId|String|Yes|lsr-bp1bpn0kn908w4nbw\*\*\*\*|The ID of the listener associated with the endpoint groups that you want to query. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the GA instance is deployed. Set the value to **cn-hangzhou**. |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000|The client token that is used to ensure the idempotence of the request.

 You can use the client to generate the value, but you must ensure that it is unique among different requests. The token can contain only ASCII characters and cannot exceed 64 characters in length. |
|Name|String|No|group1|The name of the endpoint group.

 The name must be 2 to 128 characters in length, and can contain letters, digits, underscores \(\_\), and hyphens \(-\). The name must start with a letter. |
|Description|String|No|EndpointGroup|The description of the endpoint group. |
|TrafficPercentage|Integer|No|20|The weight of the listener if the listener is associated with multiple endpoint groups. |
|HealthCheckIntervalSeconds|Integer|No|3|The interval at which health checks are performed. Unit: seconds. |
|HealthCheckPath|String|No|/healthcheck|The path of the health check. |
|HealthCheckPort|Integer|No|20|The port of the health check. |
|HealthCheckProtocol|String|No|tcp|The protocol of the health check. Valid values:

 -   **tcp**: TCP
-   **http**: HTTP
-   **https**: HTTPS |
|ThresholdCount|Integer|No|3|The number of consecutive failed heath checks that must occur before an endpoint can be considered unhealthy. |
|EndpointRequestProtocol|String|No|HTTP|The protocol of the backend service. Valid values:

 -   **HTTP**\(Default\)
-   **HTTPS**

 **Note:**

-   You can set this parameter only when you create an endpoint group for an HTTP or HTTPS listener.
-   An HTTP listener supports only HTTP as the backend service protocol. |
|EndpointGroupType|String|No|default|The type of the endpoint group. Valid values:

 -   **default**: a default endpoint group. This is the default value.
-   **virtual**: a virtual endpoint group

 **Note:** You can create virtual endpoint groups for only HTTP or HTTPS listeners. |
|EndpointConfigurations.N.EnableClientIPPreservation|Boolean|No|false|Specifies whether to reserve client IP addresses. Valid values:

 -   **true**: Client IP addresses are reserved.
-   **false**: Client IP addresses are not reserved. This is the default value. |
|PortOverrides.N.ListenerPort|Integer|No|443|The listener port configured for port mapping.

 **Note:**

-   You can configure port mapping for only an HTTP or HTTPS listener.
-   The listener port configured for port mapping must be the same as that of the current listener. |
|PortOverrides.N.EndpointPort|Integer|No|80|The endpoint port that is configured for port mapping. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|EndpointGroupId|String|epg-bp1dmlohjjz4kqaun\*\*\*\*|The ID of the endpoint group. |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=CreateEndpointGroup
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&EndpointConfigurations.1.Endpoint=120.XX.XX.21
&EndpointConfigurations.1.Type=Ip
&EndpointConfigurations.1.Weight=20
&EndpointGroupRegion=cn-hangzhou
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateEndpointGroupResponse>    
      <EndpointGroupId>epg-bp1dmlohjjz4kqaun****</EndpointGroupId>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</CreateEndpointGroupResponse>
```

`JSON` format

```
{
  "EndpointGroupId":"epg-bp1dmlohjjz4kqaun****",
  "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NotExist.Listener|The listener does not exist.|The error message returned because the specified listener does not exist.|
|400|NotActive.Listener|The state of the listener is not active.|The error message returned because the state of the specified listener is unstable.|
|400|NotExist.Accelerator|The accelerated instance does not exist.|The error message returned because the specified GA instance does not exist.|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|The error message returned because the state of the specified GA instance in invalid.|
|400|NotExist.BusinessRegion|The business region does not exist.|The error message returned because the specified region does not exist.|
|400|NotExist.BasicBandwidthPackage|You must specify the basic bandwidth package.|The error message returned because the required basic bandwidth plan is not specified.|
|400|QuotaExceeded.EndPoint|The maximum number of endpoints is exceeded.|The error message returned because the number of endpoints has reached the upper limit.|
|400|Exist.EndpointGroup|The endpoint group already exists.|The error message returned because the specified endpoint group already exists.|
|400|NoPermission.VpcEndpoint|You are not authorized to perform the operation.|The error message returned because you are unauthorized to create a service-linked role. Contact the Alibaba Cloud account or administrator to authorize your current account the service-linked role AliyunGlobalAccelerationFullAccess or obtain the custom permissions to create the service-linked role. Information about custom permissions: ServiceName: vpcendpoint.ga.aliyuncs.com The name of the service-linked role: AliyunServiceRoleForGaVpcEndpoint Required permission: ram:CreateServiceLinkedRole|
|400|QuotaExceeded.PortOverride|The number of port override exceeds the limit.|The error message returned because the number of port forwarding times has reached the upper limit.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


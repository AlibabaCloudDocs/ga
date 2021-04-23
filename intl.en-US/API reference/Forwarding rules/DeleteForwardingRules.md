# DeleteForwardingRules

Deletes a forwarding rule.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=DeleteForwardingRules&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|RegionId|String|Yes|cn-hangzhou|The region ID of the Global Accelerator \(GA\) instance. Set the value to **cn-hangzhou**. |
|ClientToken|String|No|02fb3da4\*\*\*\*|The client token that is used to ensure the idempotence of the request.

 You can use the client to generate the value, but you must ensure that it is unique among different requests. The token can contain only ASCII characters and cannot exceed 64 characters in length. |
|ForwardingRuleIds|Array of String|Yes|frule-bp19a3t3yzr21q3\*\*\*\*|The ID of the forwarding rule. |
|AcceleratorId|String|Yes|ga-bp17frjjh0udz4q\*\*\*\*|The ID of the GA instance. |
|ListenerId|String|Yes|lsr-bp1s0vzbi5bxlx5\*\*\*\*|The ID of the listener. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ForwardingRules|Array of ForwardingRules| |The information about the forwarding rule. |
|ForwardingRuleId|String|frule-bp19a3t3yzr21q3\*\*\*\*|The ID of the forwarding rule. |
|RequestId|String|CFC67ED9-4AB1-431F-B6E3-A752B7B8CCD4|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DeleteForwardingRules
&AcceleratorId=ga-bp17frjjh0udz4q****
&ForwardingRuleIds=frule-bp19a3t3yzr21q3****
&ListenerId=lsr-bp1s0vzbi5bxlx5****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeleteForwardingRulesResponse>
<ForwardingRules>
    <ForwardingRuleId>frule-bp19a3t3yzr21q3****</ForwardingRuleId>
</ForwardingRules>
<RequestId>CFC67ED9-4AB1-431F-B6E3-A752B7B8CCD4</RequestId>
</DeleteForwardingRulesResponse>
```

`JSON` format

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "ForwardingRules" : [ {
    "ForwardingRuleId" : "frule-bp19a3t3yzr21q3****"
  } ],
  "RequestId" : "CFC67ED9-4AB1-431F-B6E3-A752B7B8CCD4"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NotExist.Listener|The listener does not exist.|The error message returned because the specified listener does not exist.|
|400|NotActive.Listener|The state of the listener is not active.|The error message returned because the specified listener is in an unstable state.|
|400|NotExist.Accelerator|The accelerated instance does not exist.|The error message returned because the specified GA instance does not exist.|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|The error message returned because the specified GA instance is in an unstable state.|
|400|NotExist.BusinessRegion|The business region does not exist.|The error message returned because the specified region does not exist.|
|400|NotExist.BasicBandwidthPackage|You must specify the basic bandwidth package.|The error message returned because the required basic bandwidth plan is not specified.|
|400|QuotaExceeded.EndPoint|The maximum number of endpoints is exceeded.|The error message returned because the number of endpoints has reached the upper limit.|
|400|Exist.EndpointGroup|The endpoint group already exists.|The error message returned because the specified endpoint group already exists.|
|400|NoPermission.VpcEndpoint|You are not authorized to perform the operation.|The error message returned because you are unauthorized to create a service-linked role. Contact the Alibaba Cloud account or administrator to authorize your current account the service-linked role AliyunGlobalAccelerationFullAccess or obtain the custom permissions to create the service-linked role. Information about custom permissions: ServiceName: vpcendpoint.ga.aliyuncs.com The name of the service-linked role: AliyunServiceRoleForGaVpcEndpoint Required permission: ram:CreateServiceLinkedRole|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


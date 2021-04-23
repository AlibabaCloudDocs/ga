# CreateForwardingRules

Creates a forwarding rule.

## Scenarios

HTTP or HTTPS listeners of Global Accelerator \(GA\) support domain-based and path-based forwarding rules. After HTTPS or HTTP listeners receive requests that are destined for different domain names or paths, requests are forwarded to endpoint groups based on forwarding rules. We recommend that you understand forwarding conditions of forwarding rules before you call this operation. For more information, see [Forwarding rules](~~204224~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=CreateForwardingRules&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|RegionId|String|Yes|cn-hangzhou|The region ID of the GA instance. Set the value to **cn-hangzhou**. |
|ClientToken|String|No|02fb3da4\*\*\*\*|The client token that is used to ensure the idempotence of the request.

 You can use the client to generate the value, but you must ensure that it is unique among different requests. The token can contain only ASCII characters and cannot exceed 64 characters in length. |
|AcceleratorId|String|Yes|ga-bp17frjjh0udz4q\*\*\*\*|The ID of the GA instance. |
|ListenerId|String|Yes|lsr-bp1s0vzbi5bxlx5\*\*\*\*|The ID of the listener. |
|ForwardingRules|Array|Yes| |The list of forwarding rule configurations. |
|Priority|Integer|No|1000|The order of the forwarding rule.

 **Note:** The value only specifies the order in which the forwarding rule is displayed in the console and does not specify the priority of the forwarding rule. |
|RuleConditions|Array|Yes| |The list of forwarding conditions. |
|RuleConditionType|String|No|Host|The type of the forwarding condition. Valid values:

 -   **Host**: a domain name
-   **Path**: a path |
|PathConfig|Object|No| |Configurations |
|Values|Array of String|No|/test|The path.

 The path must be 1 to 128 characters in length and must start with a forward slash \(/\). It can contain letters, digits, dollar signs \($\), hyphens \(-\), underscores \(\_\), periods \(.\), plus signs \(+\), forward slashes \(/\), ampersands \(&\), tildes \(~\), at signs \(@\), colons \(:\), and apostrophes \('\).Supported wildcard characters are asterisks \(\*\) and question marks \(?\). |
|HostConfig|Object|No| |Configurations |
|Values|Array of String|No|www.test.com|The domain name.

 The domain name must be 3 to 128 characters in length and can contain letters, digits, hyphens \(-\), and periods \(.\).Supported wildcard characters are asterisks \(\*\) and question marks \(?\). |
|RuleActions|Array|Yes| |The forwarding action. |
|Order|Integer|Yes|20|The order.

 **Note:** The value only specifies the order in which the forwarding rule is displayed in the console and does not specify the priority of the forwarding rule. A forwarding rule can be associated with only one endpoint group. |
|RuleActionType|String|Yes|ForwardGroup|The type of the forwarding action. Default value: **ForwardGroup**. |
|ForwardGroupConfig|Object|Yes| |The forwarding configurations. |
|ServerGroupTuples|Array|Yes| |The configurations of the endpoint group. |
|EndpointGroupId|String|Yes|epg-bp1ieei9664r5nv\*\*\*\*|The ID of the endpoint group. |
|ForwardingRuleName|String|No|test|The name of the forwarding rule.

 The name must be 2 to 128 characters in length, and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF|The ID of the request. |
|ForwardingRules|Array of ForwardingRules| |The information about the forwarding rule. |
|ForwardingRuleId|String|frule-bp1dii16gu9qdvb34\*\*\*\*|The ID of the forwarding rule. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=CreateForwardingRules
&RegionId=cn-hangzhou
&ClientToken=02fb3da4****
&AcceleratorId=ga-bp17frjjh0udz4q****
&ListenerId=lsr-bp1s0vzbi5bxlx5****
&ForwardingRules=[{"Priority":1000,"RuleConditions":[{"RuleConditionType":"Host","PathConfig":{"Values":["/test"]},"HostConfig":{"Values":["www.test.com"]}}],"RuleActions":[{"Order":2,"RuleActionType":"ForwardGroup","ForwardGroupConfig":{"ServerGroupTuples":[{"EndpointGroupId":"epg-bp1ieei9664r5nv****"}]}}],"ForwardingRuleName":"test"}]
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

<CreateForwardingRulesResponse>
<RequestId>64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF</RequestId>
<ForwardingRules>
    <ForwardingRuleId>frule-bp1dii16gu9qdvb34****</ForwardingRuleId>
</ForwardingRules>
</CreateForwardingRulesResponse>
```

`JSON` format

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF",
  "ForwardingRules" : [ {
    "ForwardingRuleId" : "frule-bp1dii16gu9qdvb34****"
  } ]
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
|400|QuotaExceeded.ForwardingRule|The number of forwarding rule exceeds the limit.|The error message returned because the number of forwarding rules has reached the upper limit.|
|400|QuotaExceeded.RuleConditionConfig|The number of path and host exceeds the limit.|The error message returned because the numbers of paths and domain names have reached the upper limit.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


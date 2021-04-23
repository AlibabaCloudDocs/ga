# ListForwardingRules

Queries forwarding rules.

**Note:** You can call this operation to query only custom forwarding rules. Default forwarding rules cannot be queried.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=ListForwardingRules&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|RegionId|String|Yes|cn-hangzhou|The region ID of the Global Accelerator \(GA\) instance. Set the value to **cn-hangzhou**. |
|ClientToken|String|No|02fb3da4\*\*\*\*|The client token that is used to ensure the idempotence of the request.

 You can use the client to generate the value, but you must ensure that it is unique among different requests. The token can contain only ASCII characters and cannot exceed 64 characters in length. |
|ListenerId|String|Yes|lsr-bp1s0vzbi5bxlx5pw\*\*\*\*|The ID of the listener. |
|AcceleratorId|String|Yes|ga-bp17frjjh0udz4qzk\*\*\*\*|The ID of the GA instance. |
|ForwardingRuleId|String|No|frule-bp19a3t3yzr21q3\*\*\*\*|The ID of the forwarding rule. |
|NextToken|String|No|FFBBOCFx\*\*\*\*|The token that is used to start the next query. |
|MaxResults|Integer|Yes|2|The maximum number of forwarding rules that can be queried.

 Valid values: **1** to **100**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CFC67ED9-4AB1-431F-B6E3-A752B7B8CCD4|The ID of the request. |
|TotalCount|Integer|1|The total number of forwarding rules. |
|NextToken|String|FFBBOCFx\*\*\*\*|The token that is used to start the next query. |
|MaxResults|Integer|2|The maximum number of forwarding rules that can be queried. |
|ForwardingRules|Array of ForwardingRules| |The list of forwarding rules. |
|Priority|Integer|5000|The priority of the forwarding rule. |
|ForwardingRuleId|String|frule-bp19a3t3yzr21q3\*\*\*\*|The ID of the forwarding rule. |
|ForwardingRuleName|String|auto\_named\_rule|The name of the forwarding rule. |
|ForwardingRuleStatus|String|active|The state of the forwarding rule.

 -   **active**: The forwarding rule is working as expected.
-   **configuring**: The configurations of the forwarding rule are being modified. |
|RuleConditions|Array of RuleConditions| |The forwarding condition. |
|RuleConditionType|String|Host|The type of the forwarding condition.

 -   **Host**: a domain name
-   **Path**: a path |
|PathConfig|object| |Configurations |
|Values|Array of String|/test|The path. |
|HostConfig|object| |Configurations |
|Values|Array of String|www.example.icu|The domain name. |
|RuleActions|Array of RuleActions| |The forwarding action. |
|Order|Integer|1|The priority. |
|RuleActionType|String|ForwardGroup|The type of the forwarding action.

 Default value: **ForwardGroup**. |
|ForwardGroupConfig|object| |The configuration of the forwarding action. |
|ServerGroupTuples|Array of ServerGroupTuples| |The information about the endpoint group. |
|EndpointGroupId|String|epg-bp1ieei9664r5nv\*\*\*\*|The ID of the endpoint group. |
|ListenerId|String|lsr-bp1s0vzbi5bxlx5\*\*\*\*|The ID of the listener. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=ListForwardingRules
&RegionId=cn-hangzhou
&ClientToken=02fb3da4****
&ListenerId=lsr-bp1s0vzbi5bxlx5pw****
&AcceleratorId=ga-bp17frjjh0udz4qzk****
&ForwardingRuleId=frule-bp19a3t3yzr21q3****
&NextToken=FFBBOCFx****
&MaxResults=2
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListForwardingRulesResponse>
<TotalCount>1</TotalCount>
<RequestId>CFC67ED9-4AB1-431F-B6E3-A752B7B8CCD4</RequestId>
<MaxResults>2</MaxResults>
<ForwardingRules>
    <RuleActions>
        <RuleActionType>ForwardGroup</RuleActionType>
        <Order>1</Order>
        <ForwardGroupConfig>
            <ServerGroupTuples>
                <EndpointGroupId>epg-bp1ieei9664r5nv****</EndpointGroupId>
            </ServerGroupTuples>
        </ForwardGroupConfig>
    </RuleActions>
    <ForwardingRuleName>auto_named_rule</ForwardingRuleName>
    <Priority>5000</Priority>
    <ForwardingRuleId>frule-bp19a3t3yzr21q3****</ForwardingRuleId>
    <RuleConditions>
        <PathConfig/>
        <HostConfig>
            <Values>www.example.icu</Values>
        </HostConfig>
        <RuleConditionType>Host</RuleConditionType>
    </RuleConditions>
    <ForwardingRuleStatus>active</ForwardingRuleStatus>
    <ListenerId>lsr-bp1s0vzbi5bxlx5****</ListenerId>
</ForwardingRules>
</ListForwardingRulesResponse>
```

`JSON` format

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "TotalCount" : 1,
  "RequestId" : "CFC67ED9-4AB1-431F-B6E3-A752B7B8CCD4",
  "MaxResults" : 2,
  "ForwardingRules" : [ {
    "RuleActions" : [ {
      "RuleActionType" : "ForwardGroup",
      "Order" : 1,
      "ForwardGroupConfig" : {
        "ServerGroupTuples" : [ {
          "EndpointGroupId" : "epg-bp1ieei9664r5nv****"
        } ]
      }
    } ],
    "ForwardingRuleName" : "auto_named_rule",
    "Priority" : 5000,
    "ForwardingRuleId" : "frule-bp19a3t3yzr21q3****",
    "RuleConditions" : [ {
      "PathConfig" : { },
      "HostConfig" : {
        "Values" : [ "www.example.icu" ]
      },
      "RuleConditionType" : "Host"
    } ],
    "ForwardingRuleStatus" : "active",
    "ListenerId" : "lsr-bp1s0vzbi5bxlx5****"
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

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


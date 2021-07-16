# ListForwardingRules

调用ListForwardingRules查看已经创建的转发策略信息。

**说明：** 调用该接口只能查看自定义转发策略信息，无法查看默认转发策略信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListForwardingRules&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListForwardingRules|系统规定参数。取值：**ListForwardingRules**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属的地域ID，仅取值：**cn-hangzhou**。 |
|ClientToken|String|否|02fb3da4\*\*\*\*|客户端Token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。 |
|ListenerId|String|是|lsr-bp1s0vzbi5bxlx5pw\*\*\*\*|监听实例ID。 |
|AcceleratorId|String|是|ga-bp17frjjh0udz4qzk\*\*\*\*|全球加速实例ID。 |
|ForwardingRuleId|String|否|frule-bp19a3t3yzr21q3\*\*\*\*|转发策略ID。 |
|NextToken|String|否|FFBBOCFx\*\*\*\*|下一个查询开始的Token。 |
|MaxResults|Integer|是|2|允许查询的转发策略的个数。

 取值范围：**1**~**100**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CFC67ED9-4AB1-431F-B6E3-A752B7B8CCD4|请求ID。 |
|TotalCount|Integer|1|转发策略总个数。 |
|NextToken|String|FFBBOCFx\*\*\*\*|下一个查询开始的Token。 |
|MaxResults|Integer|2|允许查询的转发策略个数。 |
|ForwardingRules|Array of ForwardingRules| |转发策略信息列表。 |
|Priority|Integer|5000|转发策略优先级。

 **说明：** 当前转发策略优先级无实际意义，仅作为转发策略在控制台的显示顺序。 |
|ForwardingRuleId|String|frule-bp19a3t3yzr21q3\*\*\*\*|转发策略ID。 |
|ForwardingRuleName|String|auto\_named\_rule|转发策略名称。 |
|ForwardingRuleStatus|String|active|转发策略状态。

 -   **active**：正常。
-   **configuring**：变配中。 |
|RuleConditions|Array of RuleConditions| |转发条件列表。 |
|RuleConditionType|String|Host|转发条件类型。

 -   **Host**：域名。
-   **Path**：路径。 |
|PathConfig|Object| |路径配置信息。 |
|Values|Array of String|/test|路径。

 路径长度为1~128个字符，必须以正斜线（/）开头，只允许包含字母、数字、美元符号（$）、短划线（-）、下划线（\_）、半角句号（.）、加号（+）、正斜线（/）、and（&）、波浪线（~）、at（@）、半角冒号（:）、撇号（'），支持使用星号（\*）和半角问号（?）作为通配符。 |
|HostConfig|Object| |域名配置信息。 |
|Values|Array of String|www.example.com|域名。

 域名长度为3~128个字符，允许包含字母、数字、短划线（-）和半角句号（.），支持使用星号（\*）和半角问号（?）作为通配符。 |
|RuleActions|Array of RuleActions| |转发动作。 |
|Order|Integer|1|转发优先级。

 **说明：** 当前无实际意义。一个转发策略当前只支持关联一个终端节点组。 |
|RuleActionType|String|ForwardGroup|转发动作类型。

 默认值：**ForwardGroup**。 |
|ForwardGroupConfig|Object| |转发动作配置信息。 |
|ServerGroupTuples|Array of ServerGroupTuples| |终端节点组信息。 |
|EndpointGroupId|String|epg-bp1ieei9664r5nv\*\*\*\*|终端节点组ID。 |
|ListenerId|String|lsr-bp1s0vzbi5bxlx5\*\*\*\*|监听实例ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListForwardingRules
&RegionId=cn-hangzhou
&ClientToken=02fb3da4****
&ListenerId=lsr-bp1s0vzbi5bxlx5pw****
&AcceleratorId=ga-bp17frjjh0udz4qzk****
&ForwardingRuleId=frule-bp19a3t3yzr21q3****
&NextToken=FFBBOCFx****
&MaxResults=2
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListForwardingRulesResponse>
    <RequestId>CFC67ED9-4AB1-431F-B6E3-A752B7B8CCD4</RequestId>
    <TotalCount>1</TotalCount>
    <NextToken>FFBBOCFx****</NextToken>
    <MaxResults>2</MaxResults>
    <ForwardingRules>
        <Priority>5000</Priority>
        <ForwardingRuleId>frule-bp19a3t3yzr21q3****</ForwardingRuleId>
        <ForwardingRuleName>auto_named_rule</ForwardingRuleName>
        <ForwardingRuleStatus>active</ForwardingRuleStatus>
        <RuleConditions>
            <RuleConditionType>Host</RuleConditionType>
            <PathConfig>
                <Values>/test</Values>
            </PathConfig>
            <HostConfig>
                <Values>www.example.com</Values>
            </HostConfig>
        </RuleConditions>
        <RuleActions>
            <Order>1</Order>
            <RuleActionType>ForwardGroup</RuleActionType>
            <ForwardGroupConfig>
                <ServerGroupTuples>
                    <EndpointGroupId>epg-bp1ieei9664r5nv****</EndpointGroupId>
                </ServerGroupTuples>
            </ForwardGroupConfig>
        </RuleActions>
        <ListenerId>lsr-bp1s0vzbi5bxlx5****</ListenerId>
    </ForwardingRules>
</ListForwardingRulesResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "CFC67ED9-4AB1-431F-B6E3-A752B7B8CCD4",
  "TotalCount" : 1,
  "NextToken" : "FFBBOCFx****",
  "MaxResults" : 2,
  "ForwardingRules" : [ {
    "Priority" : 5000,
    "ForwardingRuleId" : "frule-bp19a3t3yzr21q3****",
    "ForwardingRuleName" : "auto_named_rule",
    "ForwardingRuleStatus" : "active",
    "RuleConditions" : [ {
      "RuleConditionType" : "Host",
      "PathConfig" : {
        "Values" : [ "/test" ]
      },
      "HostConfig" : {
        "Values" : [ "www.example.com" ]
      }
    } ],
    "RuleActions" : [ {
      "Order" : 1,
      "RuleActionType" : "ForwardGroup",
      "ForwardGroupConfig" : {
        "ServerGroupTuples" : [ {
          "EndpointGroupId" : "epg-bp1ieei9664r5nv****"
        } ]
      }
    } ],
    "ListenerId" : "lsr-bp1s0vzbi5bxlx5****"
  } ]
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NotExist.Listener|The listener does not exist.|监听器不存在|
|400|NotActive.Listener|The state of the listener is not active.|监听器状态非稳态|
|400|NotExist.Accelerator|The accelerated instance does not exist.|加速实例不存在|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|
|400|NotExist.BusinessRegion|The business region does not exist.|业务region并不存在|
|400|NotExist.BasicBandwidthPackage|You must specify the basic bandwidth package.|缺少基础带宽包|
|400|QuotaExceeded.EndPoint|The maximum number of endpoints is exceeded.|终端节点达到Quota限制|
|400|Exist.EndpointGroup|The endpoint group already exists.|终端节点组已经存在|
|400|NoPermission.VpcEndpoint|You are not authorized to perform the operation.|用户没有创建服务关联角色的权限，请联系主账号或权限管理员授权当前用户AliyunGlobalAccelerationFullAccess或者创建服务关联角色的自定义权限。自定义权限策略的相关信息包含以下内容：ServiceName为vpcendpoint.ga.aliyuncs.com，服务关联角色名称为AliyunServiceRoleForGaVpcEndpoint，执行该操作所需的用户权限为ram:CreateServiceLinkedRole。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


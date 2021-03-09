# UpdateForwardingRules

调用UpdateForwardingRules更新转发策略。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=UpdateForwardingRules&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|RegionId|String|是|cn-hangzhou|全球加速实例所属的地域ID，仅取值：**cn-hangzhou**。 |
|ClientToken|String|否|02fb3da4\*\*\*\*|客户端Token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。 |
|AcceleratorId|String|是|ga-bp17frjjh0udz4q\*\*\*\*|全球加速实例ID。 |
|ListenerId|String|是|lsr-bp1s0vzbi5bxlx5\*\*\*\*|监听实例ID。 |
|ForwardingRules|Array|是| |转发策略配置信息列表。 |
|Priority|Integer|是|1000|转发策略优先级。

 **说明：** 当前转发策略优先级无实际意义，仅作转发策略在控制台的显示顺序。 |
|RuleConditions|Array|是| |转发条件列表。 |
|RuleConditionType|String|是|Host|转发条件类型。支持以下两种转发类型：

 -   **Host**：域名。
-   **Path**：路径。 |
|PathConfig|Object|否| |路径配置信息。 |
|Values|Array of String|否|/test|路径配置。

 路径长度为1~128个字符，必须以正斜线（/）开头，只允许包含字母、数字、美元符号（$）、短划线（-）、下划线（\_）、半角句号（.）、加号（+）、正斜线（/）、and（&）、波浪线（~）、at（@）、半角冒号（:）、撇号（'），支持使用星号（\*）和半角问号（?）作为通配符。 |
|HostConfig|Object|否| |域名配置信息。 |
|Values|Array of String|否|www.test.com|域名配置。

 域名长度为3~128个字符，允许包含字母、数字、短划线（-）和半角句号（.），支持使用星号（\*）和半角问号（?）作为通配符。 |
|RuleActions|Array|是| |转发动作。 |
|Order|Integer|是|2|转发优先级。

 **说明：** 当前无实际意义。一个转发策略当前只支持关联一个终端节点组。 |
|RuleActionType|String|是|ForwardGroup|转发动作类型。默认值：**ForwardGroup**。 |
|ForwardGroupConfig|Object|是| |转发配置。 |
|ServerGroupTuples|Array|是| |终端节点组配置。 |
|EndpointGroupId|String|是|epg-bp1ieei9664r5nv\*\*\*\*|终端节点组ID。 |
|ForwardingRuleId|String|是|frule-bp1dii16gu9qdvb34\*\*\*\*|转发策略ID。 |
|ForwardingRuleName|String|否|test|转发策略名称。

 名称长度为2~128个英文或中文字符，必须以大小写字母或中文开头，可包含数字、半角句号（.）、下划线（\_）和短划线（-）。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ForwardingRules|Array of ForwardingRules| |转发策略信息。 |
|ForwardingRuleId|String|frule-bp1dii16gu9qdvb34\*\*\*\*|转发策略ID。 |
|RequestId|String|64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateForwardingRules
&RegionId=cn-hangzhou
&ClientToken=02fb3da4****
&AcceleratorId=ga-bp17frjjh0udz4q****
&ListenerId=lsr-bp1s0vzbi5bxlx5****
&ForwardingRules=[{"Priority":1000,"RuleConditions":[{"RuleConditionType":"Host","PathConfig":{"Values":["/test"]},"HostConfig":{"Values":["www.test.com"]}}],"RuleActions":[{"Order":2,"RuleActionType":"ForwardGroup","ForwardGroupConfig":{"ServerGroupTuples":[{"EndpointGroupId":"epg-bp1ieei9664r5nv****"}]}}],"ForwardingRuleId":"frule-bp1dii16gu9qdvb34****","ForwardingRuleName":"test"}]
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<UpdateForwardingRulesResponse>
<RequestId>64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF</RequestId>
<ForwardingRules>
    <ForwardingRuleId>frule-bp1dii16gu9qdvb34****</ForwardingRuleId>
</ForwardingRules>
</UpdateForwardingRulesResponse>
```

`JSON`格式

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
|400|NoPermission.VpcEndpoint|You are not authorized to perform the operation.|用户没有创建服务关联角色的权限，请联系主账号或权限管理员授权当前用户AliyunGlobalAccelerationFullAccess或者创建服务关联角色的自定义权限。自定义权限策略的相关信息如下： ServiceName：vpcendpoint.ga.aliyuncs.com 服务关联角色名称：AliyunServiceRoleForGaVpcEndpoint 执行该操作所需的用户权限：ram:CreateServiceLinkedRole|
|400|QuotaExceeded.RuleConditionConfig|The number of path and host exceeds the limit.|路径和域名数量超过限制|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


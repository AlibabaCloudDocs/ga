# DeleteForwardingRules

调用DeleteForwardingRules删除转发策略。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DeleteForwardingRules&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteForwardingRules|系统规定参数。取值：**DeleteForwardingRules**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属的地域ID，仅取值：**cn-hangzhou**。 |
|ClientToken|String|否|02fb3da4\*\*\*\*|客户端Token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。 |
|ForwardingRuleIds|Array of String|是|frule-bp19a3t3yzr21q3\*\*\*\*|转发策略ID。 |
|AcceleratorId|String|是|ga-bp17frjjh0udz4q\*\*\*\*|全球加速实例ID。 |
|ListenerId|String|是|lsr-bp1s0vzbi5bxlx5\*\*\*\*|监听实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ForwardingRules|Array of ForwardingRules| |转发策略信息。 |
|ForwardingRuleId|String|frule-bp19a3t3yzr21q3\*\*\*\*|转发策略ID。 |
|RequestId|String|CFC67ED9-4AB1-431F-B6E3-A752B7B8CCD4|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteForwardingRules
&RegionId=cn-hangzhou
&ClientToken=02fb3da4****
&ForwardingRuleIds=["frule-bp19a3t3yzr21q3****"]
&AcceleratorId=ga-bp17frjjh0udz4q****
&ListenerId=lsr-bp1s0vzbi5bxlx5****
&公共请求参数
```

正常返回示例

`XML`格式

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

`JSON`格式

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

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


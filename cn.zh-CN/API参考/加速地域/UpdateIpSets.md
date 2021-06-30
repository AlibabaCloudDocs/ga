# UpdateIpSets

调用UpdateIpSets修改加速区域中的多个加速地域。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=UpdateIpSets&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateIpSets|系统规定参数。取值：**UpdateIpSets**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域，仅取值**cn-hangzhou**。 |
|IpSets.N.Bandwidth|Integer|是|4|要修改的加速地域带宽，单位为**Mbps**。 |
|IpSets.N.IpSetId|String|是|ips-bp11c9mpphtb1xkds\*\*\*\*|要修改的加速地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|685662FF-B1CE-4D5C-A4C8-2FF3C2146BFC|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateIpSets
&RegionId=cn-hangzhou
&IpSets=[{"Bandwidth":4,"IpSetId":"ips-bp11c9mpphtb1xkds****"}]
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<UpdateIpSetsResponse>
    <RequestId>685662FF-B1CE-4D5C-A4C8-2FF3C2146BFC</RequestId>
</UpdateIpSetsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "685662FF-B1CE-4D5C-A4C8-2FF3C2146BFC"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Repeat.IpSets|The configuration of IpSet is duplicated.|IpSet配置重复|
|400|NotExist.IpSets|The IpSet does not exist.|IpSet不存在|
|400|NotActive.IpSet|The state of IpSet is not active.|IpSet状态非稳态|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|
|400|NotExist.BasicBandwidthPackage|You must specify the basic bandwidth package.|缺少基础带宽包|
|400|GreaterThanGa.IpSetBandwidth|The total bandwidth for IpSet exceeds the total bandwidth of the GA instance.|IpSet配置的总带宽超过GA实例的总带宽|

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


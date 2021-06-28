# DetachLogStoreFromEndpointGroup

调用DetachLogStoreFromEndpointGroup解除SLS日志库和终端节点组的关联关系。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DetachLogStoreFromEndpointGroup&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DetachLogStoreFromEndpointGroup|系统规定参数。取值：**DetachLogStoreFromEndpointGroup**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|ListenerId|String|是|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|ClientToken|String|否|02fb3da4\*\*\*\*|客户端Token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。 |
|EndpointGroupIds.N|String|是|\['epg-bp1dmlohjjz4kqaun\*\*\*\*','epg-bp1v1u72cx35ogofe\*\*\*\*', ...\]|终端节点组ID列表。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DetachLogStoreFromEndpointGroup
&RegionId=cn-hangzhou
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&EndpointGroupIds=["['epg-bp1dmlohjjz4kqaun****','epg-bp1v1u72cx35ogofe****', ...]"]
&ClientToken=02fb3da4****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DetachLogStoreFromEndpointGroupResponse>
    <RequestId>64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF</RequestId>
</DetachLogStoreFromEndpointGroupResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


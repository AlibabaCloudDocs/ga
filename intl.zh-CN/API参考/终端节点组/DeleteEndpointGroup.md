# DeleteEndpointGroup

调用DeleteEndpointGroup删除终端节点组。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DeleteEndpointGroup&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteEndpointGroup|系统规定参数。取值：**DeleteEndpointGroup**。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|AcceleratorId|String|否|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|EndpointGroupId|String|是|epg-bp1dmlohjjz4kqaun\*\*\*\*|要删除的终端节点组ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteEndpointGroup
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&EndpointGroupId=epg-bp1dmlohjjz4kqaun****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeleteEndpointGroupResponse>
    <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
</DeleteEndpointGroupResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6FEA0CF3-D3B9-43E5-A304-D217037876A8"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NotExist.EndPointGroup|The endpoint group does not exist.|终端节点组不存在|
|400|StateError.EndPointGroup|The specified state of endpoint group is invalid.|终端节点组状态非法|
|400|NotExist.Listener|The listener does not exist.|监听器不存在|
|400|NotActive.Listener|The state of the listener is not active.|监听器状态非稳态|
|400|NotExist.Accelerator|The accelerated instance does not exist.|加速实例不存在|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


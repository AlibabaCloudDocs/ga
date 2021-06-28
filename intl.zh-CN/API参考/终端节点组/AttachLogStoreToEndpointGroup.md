# AttachLogStoreToEndpointGroup

调用AttachLogStoreToEndpointGroup关联SLS日志库到终端节点组。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=AttachLogStoreToEndpointGroup&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AttachLogStoreToEndpointGroup|系统规定参数。取值：**AttachLogStoreToEndpointGroup**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属的地域ID，仅取值：**cn-hangzhou**。 |
|SlsProjectName|String|是|pn-01|SLS项目名称。 |
|SlsLogStoreName|String|是|lsn-01|SLS日志库名称。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|ListenerId|String|是|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|SlsRegionId|String|是|cn-hangzhou|SLS地域ID。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|EndpointGroupIds.N|String|是|\['epg-bp1dmlohjjz4kqaun\*\*\*\*','epg-bp1v1u72cx35ogofe\*\*\*\*', ...\]|终端节点组ID列表。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=AttachLogStoreToEndpointGroup
&RegionId=cn-hangzhou
&SlsProjectName=pn-01
&SlsLogStoreName=lsn-01
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&SlsRegionId=cn-hangzhou
&EndpointGroupIds=["'epg-bp1dmlohjjz4kqaun****','epg-bp1v1u72cx35ogofe****', ..."]
&ClientToken=123e4567-e89b-12d3-a456-426655440000
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<AttachLogStoreToEndpointGroupResponse>
    <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
</AttachLogStoreToEndpointGroupResponse>
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
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|
|400|NotExist.Accelerator|The accelerated instance does not exist.|加速实例不存在|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


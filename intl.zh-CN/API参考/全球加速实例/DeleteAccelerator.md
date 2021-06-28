# DeleteAccelerator

调用DeleteAccelerator删除指定的全球加速实例。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DeleteAccelerator&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteAccelerator|系统规定参数。取值：**DeleteAccelerator**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属地域ID，仅取值**cn-hangzhou**。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|要删除的全球加速实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |
|AcceleratorId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteAccelerator
&RegionId=cn-hangzhou
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeleteAcceleratorResponse>
    <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
    <AcceleratorId>ga-bp1odcab8tmno0hdq****</AcceleratorId>
</DeleteAcceleratorResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6FEA0CF3-D3B9-43E5-A304-D217037876A8",
  "AcceleratorId" : "ga-bp1odcab8tmno0hdq****"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NotExist.Accelerator|The accelerated instance does not exist.|加速实例不存在|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|
|400|BindExist.Accelerator|The accelerated instance is already bound to a bandwidth package.|加速实例已经绑定带宽包|
|400|Exist.IpSet|The IpSet already exists.|IpSet已经存在|
|400|Exist.Listener|The listener already exists.|监听器存在|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


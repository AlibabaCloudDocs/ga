# DeleteIpSet

调用DeleteIpSet删除一个加速地域。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DeleteIpSet&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteIpSet|系统规定参数。取值：**DeleteIpSet**。 |
|RegionId|String|否|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|ClientToken|String|否|DD61839A-5CC5-404B-8C6E-56066F0C432D|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|AcceleratorId|String|否|ga-bp1yeeq8yfoyszmqy\*\*\*\*|全球加速实例ID。 |
|IpSetId|String|是|ips-bp11r5jb8ogp122xl\*\*\*\*|要删除的加速地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|DD61839A-5CC5-404B-8C6E-56066F0C432D|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteIpSet
&RegionId=cn-hangzhou
&ClientToken=DD61839A-5CC5-404B-8C6E-56066F0C432D
&AcceleratorId=ga-bp1yeeq8yfoyszmqy****
&IpSetId=ips-bp11r5jb8ogp122xl****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeleteIpSetResponse>
    <RequestId>DD61839A-5CC5-404B-8C6E-56066F0C432D</RequestId>
</DeleteIpSetResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "DD61839A-5CC5-404B-8C6E-56066F0C432D"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NotExist.IpSet|The IpSet does not exist.|IpSet不存在|
|400|StateError.IpSet|The state of IpSet is invalid.|IpSet状态非法|
|400|NotExist.Accelerator|The accelerated instance does not exist.|加速实例不存在|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


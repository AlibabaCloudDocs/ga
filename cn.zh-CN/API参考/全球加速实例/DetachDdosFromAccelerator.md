# DetachDdosFromAccelerator

调用DetachDdosFromAccelerator将DDoS高防实例与全球加速实例解绑。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DetachDdosFromAccelerator&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DetachDdosFromAccelerator|系统规定参数。取值：**DetachDdosFromAccelerator**。 |
|AcceleratorId|String|否|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|RegionId|String|否|cn-hangzhou|全球加速实例所在的地域，仅取值**cn-hangzhou**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|DdosId|String|ddoscoo-cn-zz11vq7j\*\*\*\*|与全球加速实例解绑的DDoS高防实例ID。 |
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DetachDdosFromAccelerator
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DetachDdosFromAcceleratorResponse>  
      <DdosId>ddoscoo-cn-zz11vq7j****</DdosId>
      <RequestId>E9C82FD2-C77F-4F10-B185-2F4E2670289E</RequestId>
</DetachDdosFromAcceleratorResponse>
```

`JSON` 格式

```
{
  "DdosId": "ddoscoo-cn-zz11vq7j****",
  "RequestId": "E9C82FD2-C77F-4F10-B185-2F4E2670289E"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


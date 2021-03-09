# UpdateAccelerator

调用UpdateAccelerator修改全球加速实例。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=UpdateAccelerator&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateAccelerator|系统规定参数。取值：**UpdateAccelerator**。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例的ID。 |
|RegionId|String|否|cn-hangzhou|全球加速实例所属的地域，仅取值：**cn-hangzhou**。 |
|ClientToken|String|否|123e4567\*\*\*\*|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|Name|String|否|Accelerator|全球加速实例的名称。

 名称长度为2~128个字符，以大小写字母或中文开头，可包含数字、下划线（\_）或短划线（-）。 |
|Description|String|否|Accelerator|全球加速实例的描述信息。 |
|Spec|String|否|1|全球加速实例的规格，取值：

 -   **1**：小型Ⅰ。
-   **2**：小型Ⅱ。
-   **3**：小型Ⅲ。
-   **5**：中型Ⅰ。
-   **8**：中型Ⅱ。
-   **10**：中型Ⅲ。

 实例规格不同，定义也不同。更多信息，请参见[实例规格](~~153127~~)。 |
|AutoPay|Boolean|否|true|是否自动付费，取值：

 -   **false**（默认值）：不开启自动付费，生成订单后需要到订单中心完成支付。
-   **true**：开启自动付费，自动支付订单。 |
|AutoUseCoupon|Boolean|否|false|是否使用优惠券自动支付账单。取值：

 -   **true**：使用。
-   **false**（默认值）：不使用。

 **说明：** 仅**AutoPay**为**true**时，该项才生效。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateAccelerator
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<UpdateAcceleratorResponse>
      <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
</UpdateAcceleratorResponse>
```

`JSON`格式

```
{
	"RequestId":"6FEA0CF3-D3B9-43E5-A304-D217037876A8"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NotExist.Accelerator|The accelerated instance does not exist.|加速实例不存在|
|400|IllegalParameter.Spec|The specified Spec is invalid.|入参Spec非法格式|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|加速实例状态非法|

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


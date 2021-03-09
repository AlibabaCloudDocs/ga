# CreateAccelerator

调用CreateAccelerator创建一个全球加速实例。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=CreateAccelerator&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateAccelerator|系统规定参数。

 取值：**CreateAccelerator**。 |
|Duration|Integer|是|1|购买时长。

 -   当**PricingCycle**取值**Month**时，**Duration**取值范围为**1**~**9**。
-   当**PricingCycle**取值**Year**时，**Duration**取值范围为**1**~**3**。 |
|PricingCycle|String|是|Month|计费周期。取值：

 -   **Month**：按月计费。
-   **Year**：按年计费。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属的地域ID，仅取值：**cn-hangzhou**。 |
|Spec|String|是|1|全球加速实例的规格，取值：

 -   **1**：小型Ⅰ。
-   **2**：小型Ⅱ。
-   **3**：小型Ⅲ。
-   **5**：中型Ⅰ。
-   **8**：中型Ⅱ。
-   **10**：中型Ⅲ。

 实例规格不同，定义也不同。更多信息，请参见[实例规格](~~153127~~)。 |
|ClientToken|String|否|123e4567\*\*\*\*|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|Name|String|否|test|全球加速实例的名称。

 名称长度为2~128个字符，以大小写字母或中文开头，可包含数字、下划线（\_）或短划线（-）。 |
|AutoPay|Boolean|否|true|是否自动付费，取值：

 -   **false**（默认值）：不开启自动付费，生成订单后需要到订单中心完成支付。
-   **true**：开启自动付费，自动支付订单。 |
|AutoUseCoupon|String|否|true|是否使用优惠券自动支付账单。取值：

 -   **true**：使用。
-   **false**（默认值）：不使用。

 **说明：** 仅**AutoPay**为**true**时，该项才生效。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AcceleratorId|String|ga-bp17frjjh0udz4qz\*\*\*\*|全球加速实例ID。 |
|OrderId|String|2082574365|订单ID。

 如果您未自动支付账单，请您前往订单中心完成支付。 |
|RequestId|String|F591955F-5CB5-4CCE-A75D-17CF2085CE22|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateAccelerator
&Duration=1
&PricingCycle=Month
&RegionId=cn-hangzhou
&Spec=1
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CreateAcceleratorResponse>
  <RequestId>F591955F-5CB5-4CCE-A75D-17CF2085CE22</RequestId>
  <OrderId>2082574365</OrderId>
  <AcceleratorId>ga-bp1m9qeneer8cw3qq****</AcceleratorId>
</CreateAcceleratorResponse>
```

`JSON`格式

```
{
  "RequestId": "F591955F-5CB5-4CCE-A75D-17CF2085CE22",
  "OrderId": "2082574365",
  "AcceleratorId": "ga-bp1m9qeneer8cw3qq****"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


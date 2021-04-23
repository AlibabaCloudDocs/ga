# CreateAccelerator

Creates a Global Accelerator \(GA\) instance.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=CreateAccelerator&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateAccelerator|The operation that you want to perform.

 Set the value to **CreateAccelerator**. |
|Duration|Integer|Yes|1|The subscription duration.

 -   If **PricingCycle**is set to **Month**, **Duration**can be set from **1** to **9**.
-   If **PricingCycle**is set to **Year**, **Duration**can be set from **1** to **3**. |
|PricingCycle|String|Yes|Month|The billing cycle. Valid values:

 -   **Month**: billed on a monthly basis.
-   **Year**: billed on an annual basis. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the GA instance. Set the value to **cn-hangzhou**. |
|Spec|String|Yes|1|The type of the GA instance. Valid values:

 -   **1**: Small Ⅰ
-   **2**: Small Ⅱ
-   **3**: Small Ⅲ
-   **5**: Medium Ⅰ
-   **8**: Medium Ⅱ
-   **10**: Medium Ⅲ

 Different instance types have different definitions. For more information, see [Instance types](~~153127~~). |
|ClientToken|String|No|123e4567\*\*\*\*|The client token that is used to ensure the idempotency.

 You can use the client to generate the value, but you must ensure that it is unique among different requests. The token can contain only ASCII characters and cannot exceed 64 characters in length. |
|Name|String|No|test|The name of the GA instance.

 The name must be 2 to 128 characters in length and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |
|AutoPay|Boolean|No|true|Specifies whether to enable automatic payments. Valid values:

 -   **false**: disables automatic payments. This is the default value. After an order is generated, you must go to the Order Center to complete the payment.
-   **true**: enables automatic payments. After an order is generated, the system automatically deducts your account balance to pay for the order. |
|AutoUseCoupon|String|No|true|Specifies whether to automatically pay for bills with coupons. Valid values:

 -   **true**: uses coupons.
-   **false**: does not use coupons. This is the default value.

 **Note:** Only if **AutoPay**is set to **true**, this parameter is available. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|AcceleratorId|String|ga-bp17frjjh0udz4qz\*\*\*\*|The ID of the GA instance. |
|OrderId|String|2082574365|The ID of the order.

 If bills are not automatically paid, go to the Order Center to complete the payments. |
|RequestId|String|F591955F-5CB5-4CCE-A75D-17CF2085CE22|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=CreateAccelerator
&Duration=1
&PricingCycle=Month
&RegionId=cn-hangzhou
&Spec=1
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateAcceleratorResponse>
  <RequestId>F591955F-5CB5-4CCE-A75D-17CF2085CE22</RequestId>
  <OrderId>2082574365</OrderId>
  <AcceleratorId>ga-bp1m9qeneer8cw3qq****</AcceleratorId>
</CreateAcceleratorResponse>
```

`JSON` format

```
{
  "RequestId": "F591955F-5CB5-4CCE-A75D-17CF2085CE22",
  "OrderId": "2082574365",
  "AcceleratorId": "ga-bp1m9qeneer8cw3qq****"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


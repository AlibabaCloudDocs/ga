# UpdateAccelerator

Modifies a Global Accelerator \(GA\) instance

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=UpdateAccelerator&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|UpdateAccelerator|The operation that you want to perform. Set the value to **UpdateAccelerator**. |
|AcceleratorId|String|Yes|ga-bp1odcab8tmno0hdq\*\*\*\*|The ID of the GA instance. |
|RegionId|String|No|cn-hangzhou|The region where the GA instance is deployed. Set the value to **cn-hangzhou**. |
|ClientToken|String|No|123e4567\*\*\*\*|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. The token can contain only ASCII characters and cannot exceed 64 characters in length. |
|Name|String|No|Accelerator|The name of the GA instance.

The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |
|Description|String|No|Accelerator|The description of the GA instance. |
|Spec|String|No|1|The specification of the GA instance. Valid values:

-   **1**: Small Ⅰ
-   **2**: Small Ⅱ
-   **3**: Small Ⅲ
-   **5**: Medium Ⅰ
-   **8**: Medium Ⅱ
-   **10**: Medium Ⅲ

Different instance specifications have different definitions. For more information, see [Instance specifications](~~153127~~). |
|AutoPay|Boolean|No|true|Specifies whether to enable automatic payments. Valid values:

-   **false**: disables automatic payments. This is the default value. After an order is generated, you must go to the Order Center to complete the payment.
-   **true**: enables automatic payments. After an order is generated, the system automatically deducts your account balance to pay for the order. |
|AutoUseCoupon|Boolean|No|false|Specifies whether to automatically pay for bills with coupons. Valid values:

-   **true**: uses coupons.
-   **false**: does not use coupons. This is the default value.

**Note:** Only if **AutoPay**is set to **true**, this parameter is available. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=UpdateAccelerator
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<UpdateAcceleratorResponse>
      <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
</UpdateAcceleratorResponse>
```

`JSON` format

```
{
    "RequestId":"6FEA0CF3-D3B9-43E5-A304-D217037876A8"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NotExist.Accelerator|The accelerated instance does not exist.|The error message returned because the specified GA instance does not exist.|
|400|IllegalParameter.Spec|The specified Spec is invalid.|The error message returned because Spec is set to an invalid value.|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|The error message returned because the state of the specified GA instance in invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


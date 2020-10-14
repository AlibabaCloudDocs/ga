# ReplaceBandwidthPackage

Replaces a bandwidth plan with a required one. The replaced bandwidth plan has been associated with a Global Accelerator \(GA\) instance.

## Description

When you call this operation to replace the bandwidth plan, the GA instance continues to forward network traffic.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=ReplaceBandwidthPackage&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ReplaceBandwidthPackage|The operation that you want to perform. Set the value to **ReplaceBandwidthPackage**. |
|BandwidthPackageId|String|Yes|gbwp-bp176neb61yhcymow\*\*\*\*|The ID of the required bandwidth plan. When you specify a bandwidth plan, note the following limits:

-   Only the bandwidth plan that is not associated with a GA instance can be specified.
-   If you replace a basic bandwidth plan, make sure that the bandwidth provided by the required plan is not less than the total bandwidth that is assigned to the specified acceleration area. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the GA instance. Set the value to **cn-hangzhou**. |
|TargetBandwidthPackageId|String|Yes|gbwp-o978hgeb61yhcymow\*\*\*\*|The ID of the bandwidth plan that you want to replace. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|A0EA8CCA-F081-4338-9790-A1C791CCA779|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=ReplaceBandwidthPackage
&BandwidthPackageId=gbwp-bp176neb61yhcymow****
&RegionId=cn-hangzhou
&TargetBandwidthPackageId=gbwp-o978hgeb61yhcymow****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ReplaceBandwidthPackageResponse>
      <RequestId>A0EA8CCA-F081-4338-9790-A1C791CCA779</RequestId>
</ReplaceBandwidthPackageResponse>
```

`JSON` format

```
{
    "RequestId": "A0EA8CCA-F081-4338-9790-A1C791CCA779"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|NotExist.BandwidthPackage|The bandwidth package does not exist.|The error message returned because the specified bandwidth plan does not exist.|
|400|StateError.BandwidthPackage|The state of bandwidth package is invalid.|The error message returned because the specified bandwidth plan status is invalid.|
|400|NotExist.BasicBandwidthPackage|You must specify the basic bandwidth package.|The error message returned because the required basic bandwidth plan is not specified.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


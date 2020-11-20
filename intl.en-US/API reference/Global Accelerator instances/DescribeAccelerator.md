# DescribeAccelerator

Queries the information about a Global Accelerator \(GA\) instance.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=DescribeAccelerator&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeAccelerator|The operation that you want to perform. Set the value to **DescribeAccelerator**. |
|AcceleratorId|String|Yes|ga-bp1odcab8tmno0hdq\*\*\*\*|The ID of the GA instance to query. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the GA instance. Set the value to **cn-hangzhou**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|AcceleratorId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|The ID of the GA instance. |
|BasicBandwidthPackage|Struct| |The details of the basic bandwidth plan that is bound to the GA instance. |
|Bandwidth|Integer|2|The bandwidth that is provided by the basic bandwidth plan. |
|BandwidthType|String|Basic|The bandwidth type of the basic bandwidth plan. Valid values:

 -   **Basic**: the basic type of bandwidth used for the GA service.
-   **Enhanced**: the enhanced type of bandwidth used in the GA service.
-   **Advanced**: the advanced type of bandwidth used in the GA service. |
|InstanceId|String|gbwp-bp1d8xk8bg139j0fw\*\*\*\*|The ID of the basic bandwidth plan. |
|CenId|String|cen-hjkduu767hc\*\*\*\*|The ID of the Cloud Enterprise Network \(CEN\) instance to which the GA instance is attached. |
|CreateTime|Long|1577786252000|The time when the GA instance was created. |
|CrossDomainBandwidthPackage|Struct| |The details of the cross-border acceleration bandwidth plan that is bound to the GA instance.

 This array is returned only after you query instances that are deployed in regions outside mainland China. |
|Bandwidth|Integer|2|The bandwidth that is provided by the cross-border acceleration bandwidth plan, in **Mbit/s**. |
|InstanceId|String|gbwp-bp1d8xk8bg139j0fw\*\*\*\*|The ID of the cross-border acceleration bandwidth plan. |
|DdosId|String|ddoscoo-cn-zz11vq7j\*\*\*\*|The ID of the Anti-DDoS Pro instance or the Anti-DDoS Premium instance that was disassociated from the GA instance. |
|Description|String|Accelerator|The description of the GA instance. |
|DnsName|String|ga-bp1j80t5\*\*\*\*.uisnetwork.com|The Canonical Name \(CNAME\) that is assigned to the GA instance. |
|ExpiredTime|Long|1577786252000|The time when the GA instance expires. |
|InstanceChargeType|String|PREPAY|The billing method of the GA instance. |
|Name|String|Accelerator|The name of the GA instance. |
|RegionId|String|cn-hangzhou|The region ID of the GA instance. |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|The ID of the request. |
|SecondDnsName|String|ga-bp1f609c76zg6zuna\*\*\*\*-1.aliyunga0047.com|The CNAME that is used to integrate the GA instance with the Anti-DDoS service. |
|Spec|String|1|The size of the GA instance. Valid values:

 -   **1**: Small I
-   **2**: Small II
-   **3**: Small III
-   **5**: Medium I
-   **8**: Medium II
-   **10**: Medium III |
|State|String|active|The state of the GA instance. Valid values:

 -   **init**: The instance is being initialized.
-   **active**: The instance is in the running state.
-   **configuring**: The instance is being configured.
-   **binding**: A bandwidth plan is being bound to the instance.
-   **unbinding**: A bandwidth plan is being unbound from the instance.
-   **Deleting**: The instance is being deleted.
-   **financialLocked**: The instance is locked due to overdue payments. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeAccelerator
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeAcceleratorResponse>     
      <DnsName>ga-bp1j80t5gulpw****.uisnetwork.com</DnsName>
      <Spec>1</Spec>
      <BasicBandwidthPackage>
            <BandwidthType>Basic</BandwidthType>
            <InstanceId>gbwp-bp1d8xk8bg139j0fw****</InstanceId>
            <Bandwidth>2</Bandwidth>
      </BasicBandwidthPackage>
      <State>active</State>
      <RegionId>cn-hangzhou</RegionId>
      <CreateTime>1581653081000</CreateTime>
      <RequestId>64966488-B3E3-41E2-9570-4596117EC12E</RequestId>
      <InstanceChargeType>PREPAY</InstanceChargeType>
      <ExpiredTime>1584201600000</ExpiredTime>
      <AcceleratorId>ga-bp1j80t5gulpwx12r****</AcceleratorId>
</DescribeAcceleratorResponse>
```

`JSON` format

```
{
  "DnsName": "ga-bp1j80t5gulpw****.uisnetwork.com",
  "Spec": "1",
  "BasicBandwidthPackage": {
    "BandwidthType": "Basic",
    "InstanceId": "gbwp-bp1d8xk8bg139j0fw****",
    "Bandwidth": 2
  },
  "State": "active",
  "RegionId": "cn-hangzhou",
  "CreateTime": 1581653081000,
  "RequestId": "64966488-B3E3-41E2-9570-4596117EC12E",
  "InstanceChargeType": "PREPAY",
  "ExpiredTime": 1584201600000,
  "AcceleratorId": "ga-bp1j80t5gulpwx12r****"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


# ListAccelerators

Queries Global Accelerator \(GA\) instances for your account.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=ListAccelerators&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListAccelerators|The operation that you want to perform. Set the value to **ListAccelerators**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the GA instance belongs. Set the value to **cn-hangzhou**. |
|PageNumber|Integer|No|1|The number of the page to return. Default value: **1**. |
|PageSize|Integer|No|10|The number of entries to return on each page. Maximum value: **50**. Default value: **10**. |
|AcceleratorId|String|No|ga-bp1odcab8tmno0hdq\*\*\*\*|The ID of the GA instance to return. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Accelerators|Array of Accelerators| |The information about the returned GA instances. |
|AcceleratorId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|The ID of the GA instance. |
|Bandwidth|Integer|5|The bandwidth of the GA instance, in **Mbit/s**. |
|BasicBandwidthPackage|Struct| |The details of the basic bandwidth plan that is bound to the GA instance. |
|Bandwidth|Integer|2|The bandwidth that is provided by the basic bandwidth plan. |
|BandwidthType|String|Basic|The bandwidth type of the basic bandwidth plan. Valid values:

 -   **Basic**: the basic type of bandwidth used for the GA service.
-   **Enhanced**: the enhanced type of bandwidth used in the GA service.
-   **Advanced**: the advanced type of bandwidth used in the GA service. |
|InstanceId|String|gbwp-bp1d8xk8bg139j0fw\*\*\*\*|The ID of the basic bandwidth plan. |
|CenId|String|cen-hjfufhjfuwff\*\*\*\*|The ID of the Cloud Enterprise Network \(CEN\) instance to which the GA instance is attached. |
|CreateTime|Long|1577786252000|The time when the GA instance was created. |
|CrossDomainBandwidthPackage|Struct| |The details of the cross-border acceleration bandwidth plan that is bound to the GA instance.

 This array is returned only after you query instances that are deployed in regions outside mainland China. |
|Bandwidth|Integer|2|The bandwidth that is provided by the cross-border acceleration bandwidth plan, in **Mbit/s**. |
|InstanceId|String|gbwp-bp1d8xk8bg139j0fw\*\*\*\*|The ID of the cross-border acceleration bandwidth plan. |
|DdosId|String|ddoscoo-cn-zz11vq7j\*\*\*\*|The ID of the Anti-DDoS Pro instance or the Anti-DDoS Premium instance that is associated with the GA instance. |
|Description|String|Accelerator|The description of the GA instance. |
|DnsName|String|ga-bp1j80t5\*\*\*\*.uisnetwork.com|The canonical name \(CNAME\) that is assigned to the GA instance. |
|ExpiredTime|Long|1577786252000|The time when the GA instance expires. |
|InstanceChargeType|String|PREPAY|The billing method of the GA instance. **PREPAY** is returned. This value indicates the subscription billing method. |
|Name|String|Accelerator|The name of the GA instance. |
|RegionId|String|cn-hangzhou|The region ID of the GA instance. |
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
-   **finacialLocked**: The instance is locked due to overdue payments. |
|Type|String|None|An invalid parameter. |
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|10|The number of entries returned per page. |
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|The ID of the request. |
|TotalCount|Integer|10|The total number of returned entries. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=ListAccelerators
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListAcceleratorsResponse>
  <PageNumber>10</PageNumber>
  <TotalCount>2</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>E9C82FD2-C77F-4F10-B185-2F4E2670289E</RequestId>
  <Accelerators>
        <Description></Description>
        <DnsName>ga-bp1e98ijosxvu3vgb****.uisnetwork.com</DnsName>
        <State>active</State>
        <RegionId>cn-hangzhou</RegionId>
        <CreateTime>1581597755000</CreateTime>
        <CrossDomainBandwidthPackage>
              <InstanceId>gbwp-bp1pa01cgpfv3v4ti****</InstanceId>
              <Bandwidth>3</Bandwidth>
        </CrossDomainBandwidthPackage>
        <BasicBandwidthPackage>
              <BandwidthType>Basic</BandwidthType>
              <InstanceId>gbwp-bp17ep9hxkrrbxvq7****</InstanceId>
              <Bandwidth>2</Bandwidth>
        </BasicBandwidthPackage>
        <InstanceChargeType>PREPAY</InstanceChargeType>
        <ExpiredTime>1584115200000</ExpiredTime>
        <AcceleratorId>ga-bp1e98ijosxvu3vgb****</AcceleratorId>
  </Accelerators>
  <Accelerators>
        <Description></Description>
        <DnsName>ga-bp1j80t5gulpwx12r****.uisnetwork.com</DnsName>
        <State>active</State>
        <RegionId>cn-hangzhou</RegionId>
        <CreateTime>1581653081000</CreateTime>
        <CrossDomainBandwidthPackage></CrossDomainBandwidthPackage>
        <BasicBandwidthPackage>
              <BandwidthType>Basic</BandwidthType>
              <InstanceId>gbwp-bp1d8xk8bg139j0fw****</InstanceId>
              <Bandwidth>2</Bandwidth>
        </BasicBandwidthPackage>
        <InstanceChargeType>PREPAY</InstanceChargeType>
        <ExpiredTime>1584201600000</ExpiredTime>
        <AcceleratorId>ga-bp1j80t5gulpwx12r****</AcceleratorId>
  </Accelerators>
</ListAcceleratorsResponse>
```

`JSON` format

```
{
  "PageNumber": 10,
  "TotalCount": 2,
  "PageSize": 10,
  "RequestId": "E9C82FD2-C77F-4F10-B185-2F4E2670289E",
  "Accelerators": [
    {
      "Description": "",
      "DnsName": "ga-bp1e98ijosxvu3vgb****.uisnetwork.com",
      "State": "active",
      "RegionId": "cn-hangzhou",
      "CreateTime": 1581597755000,
      "CrossDomainBandwidthPackage": {
        "InstanceId": "gbwp-bp1pa01cgpfv3v4ti****",
        "Bandwidth": 3
      },
      "BasicBandwidthPackage": {
        "BandwidthType": "Basic",
        "InstanceId": "gbwp-bp17ep9hxkrrbxvq7****",
        "Bandwidth": 2
      },
      "InstanceChargeType": "PREPAY",
      "ExpiredTime": 1584115200000,
      "AcceleratorId": "ga-bp1e98ijosxvu3vgb****"
    },
    {
      "Description": "",
      "DnsName": "ga-bp1j80t5gulpwx12r****.uisnetwork.com",
      "State": "active",
      "RegionId": "cn-hangzhou",
      "CreateTime": 1581653081000,
      "CrossDomainBandwidthPackage": {},
      "BasicBandwidthPackage": {
        "BandwidthType": "Basic",
        "InstanceId": "gbwp-bp1d8xk8bg139j0fw****",
        "Bandwidth": 2
      },
      "InstanceChargeType": "PREPAY",
      "ExpiredTime": 1584201600000,
      "AcceleratorId": "ga-bp1j80t5gulpwx12r****"
    }
  ]
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


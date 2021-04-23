# DescribeIpSet

Queries an accelerated region.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=DescribeIpSet&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeIpSet|The operation that you want to perform. Set the value to **DescribeIpSet**. |
|IpSetId|String|Yes|ips-bp11ilwqjdkjeg9r7\*\*\*\*|The ID of the accelerated region.

 You can call the [ListIpSets](~~153247~~)operation to query IDs of accelerated regions. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the GA instance is deployed. Set the value to **cn-hangzhou**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|AccelerateRegionId|String|cn-huhehaote|The ID of the accelerated region. |
|Bandwidth|Integer|3|The bandwidth that is allocated to the accelerated region. Unit: Mbit/s. |
|IpAddressList|List|39.XX.XX.220|The list of accelerated IP addresses in the accelerated region. |
|IpSetId|String|ips-bp11ilwqjdkjeg9r7\*\*\*\*|The ID of the accelerated region. |
|IpVersion|String|IPv4|The IP version.

 -   **IPv4**
-   **IPv6** |
|RequestId|String|6D2BFF54-6AF2-4679-88C4-2F2E187F16CB|The ID of the request. |
|State|String|active|The state of the accelerated region. Valid values:

 -   **init**: The accelerated region is being initialized.
-   **active**: The accelerated region is in the running state.
-   **updating**: The accelerated region is being configured.
-   **Deleting**: The accelerated region is being deleted. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeIpSet
&IpSetId=ips-bp11ilwqjdkjeg9r7****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeIpSetResponse>
  <IpSetId>ips-bp11ilwqjdkjeg9r7****</IpSetId>
  <RequestId>6D2BFF54-6AF2-4679-88C4-2F2E187F16CB</RequestId>
  <IpVersion>IPv4</IpVersion>
  <State>active</State>
  <Bandwidth>2</Bandwidth>
  <IpAddressList>121.XX.XX.180</IpAddressList>
  <AccelerateRegionId>cn-hangzhou</AccelerateRegionId>
</DescribeIpSetResponse>
```

`JSON` format

```
{
  "IpSetId": "ips-bp11ilwqjdkjeg9r7****",
  "RequestId": "6D2BFF54-6AF2-4679-88C4-2F2E187F16CB",
  "IpVersion": "IPv4",
  "State": "active",
  "Bandwidth": 2,
  "IpAddressList": [
    "121.XX.XX.180"
  ],
  "AccelerateRegionId": "cn-hangzhou"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


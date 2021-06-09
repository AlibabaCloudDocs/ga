# ListBusiRegions

Queries regions that support Global Accelerator \(GA\).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=ListBusiRegions&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListBusiRegions|The operation that you want to perform. Set the value to **ListBusiRegions**. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the GA instance. Set the value to **cn-hangzhou**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Regions|Array of Regions| |The information about the regions. |
|LocalName|String|Hangzhou|The region name. |
|RegionId|String|cn-hangzhou|The region ID. |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=ListBusiRegions
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<RequestId>1A2262A0-B50A-4C27-8543-E91D9447F967</RequestId>
<Regions>
    <RegionId>cn-qingdao</RegionId>
    <LocalName>China (Qingdao)</LocalName>
</Regions>
<Regions>
    <RegionId>us-west-1</RegionId>
    <LocalName>US (Silicon Valley)</LocalName>
</Regions>
<Regions>
    <RegionId>cn-beijing</RegionId>
    <LocalName>China (Beijing)</LocalName>
</Regions>
<Regions>
    <RegionId>cn-hangzhou</RegionId>
    <LocalName>China (Hangzhou)</LocalName>
</Regions>
<Regions>
    <RegionId>cn-shanghai</RegionId>
    <LocalName>China (Shanghai)</LocalName>
</Regions>
<Regions>
    <RegionId>cn-chengdu</RegionId>
    <LocalName>China (Chengdu)</LocalName>
</Regions>
<Regions>
    <RegionId>cn-shenzhen</RegionId>
    <LocalName>China (Shenzhen)</LocalName>
</Regions>
<Regions>
    <RegionId>cn-hongkong</RegionId>
    <LocalName>China (Hong Kong)</LocalName>
</Regions>
<Regions>
    <RegionId>ap-northeast-1</RegionId>
    <LocalName>Japan (Tokyo)</LocalName>
</Regions>
<Regions>
    <RegionId>ap-south-1</RegionId>
    <LocalName>India (Mumbai)</LocalName>
</Regions>
<Regions>
    <RegionId>ap-southeast-1</RegionId>
    <LocalName>Singapore</LocalName>
</Regions>
<Regions>
    <RegionId>ap-southeast-2</RegionId>
    <LocalName>Australia (Sydney)</LocalName>
</Regions>
<Regions>
    <RegionId>ap-southeast-3</RegionId>
    <LocalName>Malaysia (Kuala Lumpur)</LocalName>
</Regions>
<Regions>
    <RegionId>ap-southeast-5</RegionId>
    <LocalName>Indonesia (Jakarta)</LocalName>
</Regions>
<Regions>
    <RegionId>us-east-1</RegionId>
    <LocalName>>US (Virginia)</LocalName>
</Regions>
<Regions>
    <RegionId>eu-central-1</RegionId>
    <LocalName>Germany (Frankfurt)</LocalName>
</Regions>
<Regions>
    <RegionId>eu-west-1</RegionId>
    <LocalName>UK (London)</LocalName>
</Regions>
<Regions>
    <RegionId>ap-northeast-2-pop</RegionId>
    <LocalName>South Korea</LocalName>
</Regions>
```

`JSON` format

```
{
  "RequestId": "1A2262A0-B50A-4C27-8543-E91D9447F967",
  "Regions": [
    {
      "RegionId": "cn-qingdao",
      "LocalName": "China (Qingdao)"
    },
    {
      "RegionId": "us-west-1",
      "LocalName": "US (Silicon Valley)"
    },
    {
      "RegionId": "cn-beijing",
      "LocalName": "China (Beijing)"
    },
    {
      "RegionId": "cn-hangzhou",
      "LocalName": "China (Hangzhou)"
    },
    {
      "RegionId": "cn-shanghai",
      "LocalName": "China (Shanghai)"
    },
    {
      "RegionId": "cn-chengdu",
      "LocalName": "China (Chengdu)"
    },
    {
      "RegionId": "cn-shenzhen",
      "LocalName": "China (Shenzhen)"
    },
    {
      "RegionId": "cn-hongkong",
      "LocalName": "China (Hong Kong)"
    },
    {
      "RegionId": "ap-northeast-1",
      "LocalName": "Japan (Tokyo)"
    },
    {
      "RegionId": "ap-south-1",
      "LocalName": "India (Mumbai)"
    },
    {
      "RegionId": "ap-southeast-1",
      "LocalName": "Singapore"
    },
    {
      "RegionId": "ap-southeast-2",
      "LocalName": "Australia (Sydney)"
    },
    {
      "RegionId": "ap-southeast-3",
      "LocalName": "Malaysia (Kuala Lumpur)"
    },
    {
      "RegionId": "ap-southeast-5",
      "LocalName": "Indonesia (Jakarta)"
    },
    {
      "RegionId": "us-east-1",
      "LocalName": "US (Virginia)"
    },
    {
      "RegionId": "eu-central-1",
      "LocalName": "Germany (Frankfurt)"
    },
    {
      "RegionId": "eu-west-1",
      "LocalName": "UK (London)"
    },
    {
      "RegionId": "ap-northeast-2-pop",
      "LocalName": "South Korea"
    }
  ]
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


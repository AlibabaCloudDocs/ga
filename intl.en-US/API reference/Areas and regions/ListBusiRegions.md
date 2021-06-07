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
    <LocalName>青岛</LocalName>
</Regions>
<Regions>
    <RegionId>us-west-1</RegionId>
    <LocalName>美国（硅谷）</LocalName>
</Regions>
<Regions>
    <RegionId>cn-beijing</RegionId>
    <LocalName>北京</LocalName>
</Regions>
<Regions>
    <RegionId>cn-hangzhou</RegionId>
    <LocalName>杭州</LocalName>
</Regions>
<Regions>
    <RegionId>cn-shanghai</RegionId>
    <LocalName>上海</LocalName>
</Regions>
<Regions>
    <RegionId>cn-chengdu</RegionId>
    <LocalName>成都</LocalName>
</Regions>
<Regions>
    <RegionId>cn-shenzhen</RegionId>
    <LocalName>深圳</LocalName>
</Regions>
<Regions>
    <RegionId>cn-hongkong</RegionId>
    <LocalName>中国香港</LocalName>
</Regions>
<Regions>
    <RegionId>ap-northeast-1</RegionId>
    <LocalName>日本</LocalName>
</Regions>
<Regions>
    <RegionId>ap-south-1</RegionId>
    <LocalName>印度</LocalName>
</Regions>
<Regions>
    <RegionId>ap-southeast-1</RegionId>
    <LocalName>新加坡</LocalName>
</Regions>
<Regions>
    <RegionId>ap-southeast-2</RegionId>
    <LocalName>悉尼</LocalName>
</Regions>
<Regions>
    <RegionId>ap-southeast-3</RegionId>
    <LocalName>马来西亚</LocalName>
</Regions>
<Regions>
    <RegionId>ap-southeast-5</RegionId>
    <LocalName>印度尼西亚</LocalName>
</Regions>
<Regions>
    <RegionId>us-east-1</RegionId>
    <LocalName>美国（弗吉尼亚）</LocalName>
</Regions>
<Regions>
    <RegionId>eu-central-1</RegionId>
    <LocalName>德国</LocalName>
</Regions>
<Regions>
    <RegionId>eu-west-1</RegionId>
    <LocalName>英国</LocalName>
</Regions>
<Regions>
    <RegionId>ap-northeast-2-pop</RegionId>
    <LocalName>韩国</LocalName>
</Regions>
```

`JSON` format

```
{
  "RequestId": "1A2262A0-B50A-4C27-8543-E91D9447F967",
  "Regions": [
    {
      "RegionId": "cn-qingdao",
      "LocalName": "青岛"
    },
    {
      "RegionId": "us-west-1",
      "LocalName": "美国（硅谷）"
    },
    {
      "RegionId": "cn-beijing",
      "LocalName": "北京"
    },
    {
      "RegionId": "cn-hangzhou",
      "LocalName": "杭州"
    },
    {
      "RegionId": "cn-shanghai",
      "LocalName": "上海"
    },
    {
      "RegionId": "cn-chengdu",
      "LocalName": "成都"
    },
    {
      "RegionId": "cn-shenzhen",
      "LocalName": "深圳"
    },
    {
      "RegionId": "cn-hongkong",
      "LocalName": "中国香港"
    },
    {
      "RegionId": "ap-northeast-1",
      "LocalName": "日本"
    },
    {
      "RegionId": "ap-south-1",
      "LocalName": "印度"
    },
    {
      "RegionId": "ap-southeast-1",
      "LocalName": "新加坡"
    },
    {
      "RegionId": "ap-southeast-2",
      "LocalName": "悉尼"
    },
    {
      "RegionId": "ap-southeast-3",
      "LocalName": "马来西亚"
    },
    {
      "RegionId": "ap-southeast-5",
      "LocalName": "印度尼西亚"
    },
    {
      "RegionId": "us-east-1",
      "LocalName": "美国（弗吉尼亚）"
    },
    {
      "RegionId": "eu-central-1",
      "LocalName": "德国"
    },
    {
      "RegionId": "eu-west-1",
      "LocalName": "英国"
    },
    {
      "RegionId": "ap-northeast-2-pop",
      "LocalName": "韩国"
    }
  ]
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


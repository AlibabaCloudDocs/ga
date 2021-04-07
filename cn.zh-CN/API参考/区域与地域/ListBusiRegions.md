# ListBusiRegions

调用ListBusiRegions查询加速业务支持的地域。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListBusiRegions&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListBusiRegions|系统规定参数。取值：**ListBusiRegions**。 |
|RegionId|String|是|cn-hangzhou|全球加速所在的地域。取值：**cn-hangzhou**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Regions|Array of Regions| |地域信息。 |
|LocalName|String|杭州|地域名称。 |
|RegionId|String|cn-hangzhou|地域ID。 |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListBusiRegions
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

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

`JSON`格式

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

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


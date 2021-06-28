# ListAvailableBusiRegions

调用ListAvailableBusiRegions查询可用的加速业务地域。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListAvailableBusiRegions&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAvailableBusiRegions|系统规定参数。取值：**ListAvailableBusiRegions**。 |
|RegionId|String|是|cn-hangzhou|全球加速所在的地域ID。取值：**cn-hangzhou**。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|请求ID。 |
|Regions|Array of Regions| |地域信息。 |
|LocalName|String|青岛|地域名称。 |
|RegionId|String|cn-qingdao|地域ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAvailableBusiRegions
&RegionId=cn-hangzhou
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListAvailableBusiRegionsResponse>
    <RequestId>DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6</RequestId>
    <Regions>
        <LocalName>青岛</LocalName>
        <RegionId>cn-qingdao</RegionId>
    </Regions>
</ListAvailableBusiRegionsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6",
  "Regions" : [ {
    "LocalName" : "青岛",
    "RegionId" : "cn-qingdao"
  } ]
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


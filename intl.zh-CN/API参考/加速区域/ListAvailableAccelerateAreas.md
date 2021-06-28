# ListAvailableAccelerateAreas

调用ListAvailableAccelerateAreas查询可用的加速地域。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListAvailableAccelerateAreas&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAvailableAccelerateAreas|系统规定参数。取值：**ListAvailableAccelerateAreas**。 |
|RegionId|String|是|cn-hangzhou|全球加速所在的地域ID，仅取值**cn-hangzhou**。 |
|AcceleratorId|String|是|ga-bp1yeeq8yfoyszmqy\*\*\*\*|全球加速实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|A9B4E54C-9CCD-4002-91A9-D38C6C209192|请求ID。 |
|Areas|Array of Areas| |区域信息列表。 |
|LocalName|String|华北|区域名称。 |
|AreaId|String|cn-huabei|区域ID。 |
|RegionList|Array of RegionList| |地域信息列表。 |
|LocalName|String|青岛|地域名称。 |
|RegionId|String|cn-qingdao|地域ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAvailableAccelerateAreas
&RegionId=cn-hangzhou
&AcceleratorId=ga-bp1yeeq8yfoyszmqy****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListAvailableAccelerateAreasResponse>
    <RequestId>A9B4E54C-9CCD-4002-91A9-D38C6C209192</RequestId>
    <Areas>
        <LocalName>华北</LocalName>
        <AreaId>cn-huabei</AreaId>
        <RegionList>
            <LocalName>青岛</LocalName>
            <RegionId>cn-qingdao</RegionId>
        </RegionList>
    </Areas>
</ListAvailableAccelerateAreasResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "A9B4E54C-9CCD-4002-91A9-D38C6C209192",
  "Areas" : [ {
    "LocalName" : "华北",
    "AreaId" : "cn-huabei",
    "RegionList" : [ {
      "LocalName" : "青岛",
      "RegionId" : "cn-qingdao"
    } ]
  } ]
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


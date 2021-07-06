# UpdateBandwidthPackage

调用UpdateBandwidthPackage修改带宽包的配置。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=UpdateBandwidthPackage&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateBandwidthPackage|系统规定参数。取值：**UpdateBandwidthPackage**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|BandwidthPackageId|String|是|gbwp-bp1sgzldyj6b4q7cx\*\*\*\*|要修改的带宽包的ID。 |
|Name|String|否|testName|带宽包的名称。 |
|Description|String|否|testDescription|带宽包的描述。 |
|Bandwidth|Integer|否|2|带宽包的带宽值。 |
|BandwidthType|String|否|Basic|带宽类型，取值：

 -   **Basic**：标准加速带宽。
-   **Enhanced**：增强加速带宽。
-   **Advanced**：精品加速带宽。

 **说明：** 目前，仅支持**Basic**变配到**Enhanced**，而不支持将**Enhanced**和**Advanced**变配到其他类型的加速带宽。 |
|AutoPay|Boolean|否|true|是否自动付费，取值：

 -   **false**（默认值）：不开启自动付费，生成订单后需要到订单中心完成支付。
-   **true**：开启自动付费，自动支付订单。 |
|AutoUseCoupon|Boolean|否|false|是否使用代金券，取值：

 -   **true**：使用。
-   **false**（默认值）：不使用。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|BandwidthPackage|String|gbwp-bp1eo4f57z1kbbcmn\*\*\*\*|带宽包ID。 |
|Description|String|testDescription|带宽包的描述。 |
|RequestId|String|1DF3A3CB-B621-44F8-9870-C20D034D7AB|请求ID。 |
|Name|String|testName|带宽包的名称。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateBandwidthPackage
&RegionId=cn-hangzhou
&BandwidthPackageId=gbwp-bp1sgzldyj6b4q7cx****
&Name=testName
&Description=testDescription
&Bandwidth=2
&BandwidthType=Basic
&AutoPay=true
&AutoUseCoupon=false
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<UpdateBandwidthPackageResponse>
    <BandwidthPackage>gbwp-bp1eo4f57z1kbbcmn****</BandwidthPackage>
    <Description>testDescription</Description>
    <RequestId>1DF3A3CB-B621-44F8-9870-C20D034D7AB</RequestId>
    <Name>testName</Name>
</UpdateBandwidthPackageResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "BandwidthPackage" : "gbwp-bp1eo4f57z1kbbcmn****",
  "Description" : "testDescription",
  "RequestId" : "1DF3A3CB-B621-44F8-9870-C20D034D7AB",
  "Name" : "testName"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|StateError.BandwidthPackage|The state of bandwidth package is invalid.|带宽包状态非法|
|400|NotExist.BandwidthPackage|The bandwidth package does not exist.|带宽包不存在|
|400|UpgradeError.BandwidthPackage|The bandwidth package configurations should be either all upgrades or all downgrades.|带宽包变配项目应当全是升配或降配|

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


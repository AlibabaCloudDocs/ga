# DescribeBandwidthPackage

调用DescribeBandwidthPackage查询带宽包。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DescribeBandwidthPackage&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeBandwidthPackage|系统规定参数。取值：**DescribeBandwidthPackage**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|BandwidthPackageId|String|是|gbwp-bp1sgzldyj6b4q7cx\*\*\*\*|要查询的带宽包的ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|CbnGeographicRegionIdB|String|Global|跨域加速包的互通区域B。

 仅国际站支持返回该参数。 |
|CbnGeographicRegionIdA|String|China-mainland|跨域加速包的互通区域A。

 仅国际站支持返回该参数。 |
|Description|String|testDescription|带宽包的描述。 |
|RequestId|String|4B6DBBB0-2D01-4C6A-A384-4129266E6B78|请求ID。 |
|CreateTime|String|1578966918000|带宽包创建时间的时间戳。 |
|Name|String|testName|带宽包的名称。 |
|BandwidthType|String|Basic|带宽类型。

 -   **Basic**：标准加速带宽。
-   **Enhanced**：增强加速带宽。
-   **Advanced**：精品加速带宽。 |
|Type|String|Basic|带宽包的类型。

 -   **Basic**：基础带宽包。
-   **CrossDomain**：跨域加速包。

 中国站仅支持返回**Basic**。 |
|Accelerators|Array of String|ga-bp1qe94o52ot4pkfn\*\*\*\*|带宽包绑定的全球加速实例ID。 |
|State|String|active|带宽包的状态。

 -   **init**：初始化。
-   **active**：可用。
-   **binded**：已绑定。
-   **binding**：绑定中。
-   **unbinding**：解绑中。
-   **updating**：更新中。
-   **finacialLocked**：欠费锁定。 |
|ChargeType|String|PREPAY|付费类型，仅返回**PREPAY**（包年包月）。 |
|Bandwidth|Integer|2|带宽包的带宽值，单位为Mbps。 |
|ExpiredTime|String|1578966918000|带宽包过期时间的时间戳。 |
|BandwidthPackageId|String|gbwp-bp1sgzldyj6b4q7cx\*\*\*\*|带宽包ID。 |
|RegionId|String|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|BillingType|String|PayByTraffic|后付费计费方式，取值：

 -   **PayByTraffic**：流量计费。
-   **PayBY95**：95计费。 |
|Ratio|Integer|30|95计费保底比例。取值范围：**30**~**100**。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeBandwidthPackage
&RegionId=cn-hangzhou
&BandwidthPackageId=gbwp-bp1sgzldyj6b4q7cx****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeBandwidthPackageResponse>
    <CbnGeographicRegionIdB>Global</CbnGeographicRegionIdB>
    <CbnGeographicRegionIdA>China-mainland</CbnGeographicRegionIdA>
    <Description>testDescription</Description>
    <RequestId>4B6DBBB0-2D01-4C6A-A384-4129266E6B78</RequestId>
    <CreateTime>1578966918000</CreateTime>
    <Name>testName</Name>
    <BandwidthType>Basic</BandwidthType>
    <Type>Basic</Type>
    <Accelerators>ga-bp1qe94o52ot4pkfn****</Accelerators>
    <State>active</State>
    <ChargeType>PREPAY</ChargeType>
    <Bandwidth>2</Bandwidth>
    <ExpiredTime>1578966918000</ExpiredTime>
    <BandwidthPackageId>gbwp-bp1sgzldyj6b4q7cx****</BandwidthPackageId>
    <RegionId>cn-hangzhou</RegionId>
    <BillingType>PayByTraffic</BillingType>
    <Ratio>30</Ratio>
</DescribeBandwidthPackageResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "CbnGeographicRegionIdB" : "Global",
  "CbnGeographicRegionIdA" : "China-mainland",
  "Description" : "testDescription",
  "RequestId" : "4B6DBBB0-2D01-4C6A-A384-4129266E6B78",
  "CreateTime" : "1578966918000",
  "Name" : "testName",
  "BandwidthType" : "Basic",
  "Type" : "Basic",
  "Accelerators" : [ "ga-bp1qe94o52ot4pkfn****" ],
  "State" : "active",
  "ChargeType" : "PREPAY",
  "Bandwidth" : 2,
  "ExpiredTime" : "1578966918000",
  "BandwidthPackageId" : "gbwp-bp1sgzldyj6b4q7cx****",
  "RegionId" : "cn-hangzhou",
  "BillingType" : "PayByTraffic",
  "Ratio" : 30
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


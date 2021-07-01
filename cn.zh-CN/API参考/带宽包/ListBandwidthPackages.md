# ListBandwidthPackages

调用ListBandwidthPackages查询带宽包列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListBandwidthPackages&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListBandwidthPackages|系统规定参数。取值：**ListBandwidthPackages**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**100**，默认值为**10**。 |
|State|String|否|active|带宽包的状态，取值：

 -   **init**：初始化。
-   **active**：可用。
-   **binded**：已绑定。
-   **binding**：绑定中。
-   **unbinding**：解绑中。
-   **updating**：更新中。
-   **finacialLocked**：欠费锁定。 |
|Type|String|否|Basic|带宽包的类型，取值：

 -   **Basic**：基础带宽包。
-   **CrossDomain**：跨域加速包。

 中国站仅支持取值**Basic**。 |
|BandwidthPackageId|String|否|gbwp-bp1sgzldyj6b4q7cx\*\*\*\*|带宽包ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|TotalCount|Integer|10|列表条目数。 |
|PageSize|Integer|10|每页包含的条目数。 |
|RequestId|String|4B6DBBB0-2D01-4C6A-A384-4129266E6B78|请求ID。 |
|PageNumber|Integer|1|当前页码。 |
|BandwidthPackages|Array of BandwidthPackage| |带宽包详情。 |
|Type|String|Basic|带宽包的类型。

 -   **Basic**：基础带宽包。
-   **CrossDomain**：跨域加速包。

 中国站仅支持返回**Basic**。 |
|BandwidthType|String|Basic|带宽类型。

 -   **Basic**：标准加速带宽。
-   **Enhanced**：增强加速带宽。
-   **Advanced**：精品加速带宽。 |
|State|String|active|带宽包的状态。

 -   **init**：初始化。
-   **active**：可用。
-   **binded**：已绑定。
-   **binding**：绑定中。
-   **unbinding**：解绑中。
-   **updating**：更新中。
-   **finacialLocked**：欠费锁定。 |
|CreateTime|String|1578966918000|带宽包的创建时间。 |
|ChargeType|String|PREPAY|付费类型，仅返回**PREPAY**（包年包月）。 |
|RegionId|String|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|CbnGeographicRegionIdA|String|China-mainland|跨域加速包的互通区域A。

 仅国际站支持返回该参数。 |
|BandwidthPackageId|String|gbwp-bp1sgzldyj6b4q7cx\*\*\*\*|带宽包ID。 |
|Bandwidth|Integer|2|带宽包的带宽值，单位为Mbps。 |
|Description|String|testDescription|带宽包的描述。 |
|ExpiredTime|String|1578966918000|带宽包的到期时间。 |
|Accelerators|Array of String|ga-bp1qe94o52ot4pkfn\*\*\*\*|带宽包绑定的全球加速实例ID。 |
|CbnGeographicRegionIdB|String|Global|跨域加速包的互通区域B。

 仅国际站支持返回该参数。 |
|Name|String|testName|带宽包的名称。 |
|BillingType|String|PayByTraffic|后付费计费方式。取值：

 -   **PayByTraffic**：流量计费。
-   **PayBY95**：95计费。 |
|Ratio|Integer|30|95计费保底比例。取值范围：**30**~**100**。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListBandwidthPackages
&RegionId=cn-hangzhou
&PageNumber=1
&PageSize=10
&State=active
&Type=Basic
&BandwidthPackageId=gbwp-bp1sgzldyj6b4q7cx****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListBandwidthPackagesResponse>
    <TotalCount>10</TotalCount>
    <PageSize>10</PageSize>
    <RequestId>4B6DBBB0-2D01-4C6A-A384-4129266E6B78</RequestId>
    <PageNumber>1</PageNumber>
    <BandwidthPackages>
        <Type>Basic</Type>
        <BandwidthType>Basic</BandwidthType>
        <State>active</State>
        <CreateTime>1578966918000</CreateTime>
        <ChargeType>PREPAY</ChargeType>
        <RegionId>cn-hangzhou</RegionId>
        <CbnGeographicRegionIdA>China-mainland</CbnGeographicRegionIdA>
        <BandwidthPackageId>gbwp-bp1sgzldyj6b4q7cx****</BandwidthPackageId>
        <Bandwidth>2</Bandwidth>
        <Description>testDescription</Description>
        <ExpiredTime>1578966918000</ExpiredTime>
        <Accelerators>ga-bp1qe94o52ot4pkfn****</Accelerators>
        <CbnGeographicRegionIdB>Global</CbnGeographicRegionIdB>
        <Name>testName</Name>
        <BillingType>PayByTraffic</BillingType>
        <Ratio>30</Ratio>
    </BandwidthPackages>
</ListBandwidthPackagesResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "TotalCount" : 10,
  "PageSize" : 10,
  "RequestId" : "4B6DBBB0-2D01-4C6A-A384-4129266E6B78",
  "PageNumber" : 1,
  "BandwidthPackages" : [ {
    "Type" : "Basic",
    "BandwidthType" : "Basic",
    "State" : "active",
    "CreateTime" : "1578966918000",
    "ChargeType" : "PREPAY",
    "RegionId" : "cn-hangzhou",
    "CbnGeographicRegionIdA" : "China-mainland",
    "BandwidthPackageId" : "gbwp-bp1sgzldyj6b4q7cx****",
    "Bandwidth" : 2,
    "Description" : "testDescription",
    "ExpiredTime" : "1578966918000",
    "Accelerators" : [ "ga-bp1qe94o52ot4pkfn****" ],
    "CbnGeographicRegionIdB" : "Global",
    "Name" : "testName",
    "BillingType" : "PayByTraffic",
    "Ratio" : 30
  } ]
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


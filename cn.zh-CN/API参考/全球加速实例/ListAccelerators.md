# ListAccelerators

调用ListAccelerators查询全球加速实例列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListAccelerators&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAccelerators|系统规定参数。取值：**ListAccelerators**。 |
|RegionId|String|是|cn-hangzhou|全球加速所在的地域ID，仅取值**cn-hangzhou**。 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。 |
|AcceleratorId|String|否|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|State|String|否|active|全球加速实例的状态。

 -   **init**：初始化。
-   **active**：可用。
-   **configuring**：配置中。
-   **binding**：绑定中。
-   **unbinding**：解绑中。
-   **deleting**：删除中。
-   **finacialLocked**：欠费锁定。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|TotalCount|Integer|10|列表条目数。 |
|PageSize|Integer|10|每页包含的条目数。 |
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|请求ID。 |
|Accelerators|Array of Accelerators| |全球加速实例信息。 |
|DnsName|String|ga-bp1j80t5\*\*\*\*.uisnetwork.com|全球加速实例分配的CNAME地址。 |
|Type|String|None|无效参数。 |
|SecondDnsName|String|ga-bp1f609c76zg6zuna\*\*\*\*-1.aliyunga0047.com|全球加速与DDoS高防联动后分配的CNAME。 |
|Spec|String|1|全球加速实例的规格。

 -   **1**：小型1。
-   **2**：小型2。
-   **3**：小型3。
-   **5**：中型1。
-   **8**：中型2。
-   **10**：中型3。 |
|State|String|active|全球加速实例的状态。

 -   **init**：初始化。
-   **active**：可用。
-   **configuring**：配置中。
-   **binding**：绑定中。
-   **unbinding**：解绑中。
-   **deleting**：删除中。
-   **finacialLocked**：欠费锁定。 |
|CreateTime|Long|1577786252000|全球加速实例创建时间的时间戳。 |
|CenId|String|cen-hjfufhjfuwff\*\*\*\*|全球加速实例绑定的云企业网实例。 |
|DdosId|String|ddoscoo-cn-zz11vq7j\*\*\*\*|与全球加速实例绑定的DDoS高防实例ID。 |
|BasicBandwidthPackage|Object| |全球加速实例绑定的基础带宽包的详情。 |
|Bandwidth|Integer|2|基础带宽包的带宽值，单位为**Mbps**。 |
|BandwidthType|String|Basic|基础带宽包的带宽类型。

 -   **Basic**：标准加速带宽。
-   **Enhanced**：增强加速带宽。
-   **Advanced**：精品加速带宽。 |
|InstanceId|String|gbwp-bp1d8xk8bg139j0fw\*\*\*\*|基础带宽包的实例ID。 |
|RegionId|String|cn-hangzhou|全球加速实例所在的地域ID，仅取值**cn-hangzhou**。 |
|InstanceChargeType|String|PREPAY|全球加速实例的计费方式，仅支持返回**PREPAY**（包年包月）。 |
|AcceleratorId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|Description|String|Accelerator|全球加速实例的描述信息。 |
|Bandwidth|Integer|5|全球加速实例的带宽，单位为**Mbps**。 |
|ExpiredTime|Long|1577786252000|全球加速实例到期时间的时间戳。 |
|Name|String|Accelerator|全球加速实例的名称。 |
|CrossDomainBandwidthPackage|Object| |全球加速实例绑定的跨域加速包的详情。

 仅国际站返回该数组。 |
|Bandwidth|Integer|2|跨域加速包的带宽值，单位为**Mbps**。 |
|InstanceId|String|gbwp-bp1d8xk8bg139j0fw\*\*\*\*|跨域加速包的实例ID。 |
|PageNumber|Integer|1|当前页码。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAccelerators
&RegionId=cn-hangzhou
&PageNumber=1
&PageSize=10
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&State=active
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListAcceleratorsResponse>
    <TotalCount>10</TotalCount>
    <PageSize>10</PageSize>
    <RequestId>DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6	</RequestId>
    <Accelerators>
        <DnsName>ga-bp1j80t5****.uisnetwork.com</DnsName>
        <Type>None</Type>
        <SecondDnsName>ga-bp1f609c76zg6zuna****-1.aliyunga0047.com</SecondDnsName>
        <Spec>1</Spec>
        <State>active</State>
        <CreateTime>1577786252000</CreateTime>
        <CenId>cen-hjfufhjfuwff****</CenId>
        <DdosId>ddoscoo-cn-zz11vq7j****</DdosId>
        <BasicBandwidthPackage>
            <Bandwidth>2</Bandwidth>
            <BandwidthType>Basic</BandwidthType>
            <InstanceId>gbwp-bp1d8xk8bg139j0fw****</InstanceId>
        </BasicBandwidthPackage>
        <RegionId>cn-hangzhou</RegionId>
        <InstanceChargeType>PREPAY</InstanceChargeType>
        <AcceleratorId>ga-bp1odcab8tmno0hdq****</AcceleratorId>
        <Description>Accelerator</Description>
        <Bandwidth>5</Bandwidth>
        <ExpiredTime>1577786252000</ExpiredTime>
        <Name>Accelerator</Name>
        <CrossDomainBandwidthPackage>
            <Bandwidth>2</Bandwidth>
            <InstanceId>gbwp-bp1d8xk8bg139j0fw****</InstanceId>
        </CrossDomainBandwidthPackage>
    </Accelerators>
    <PageNumber>1</PageNumber>
</ListAcceleratorsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "TotalCount" : 10,
  "PageSize" : 10,
  "RequestId" : "DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6\t",
  "Accelerators" : [ {
    "DnsName" : "ga-bp1j80t5****.uisnetwork.com",
    "Type" : "None",
    "SecondDnsName" : "ga-bp1f609c76zg6zuna****-1.aliyunga0047.com",
    "Spec" : "1",
    "State" : "active",
    "CreateTime" : 1577786252000,
    "CenId" : "cen-hjfufhjfuwff****",
    "DdosId" : "ddoscoo-cn-zz11vq7j****",
    "BasicBandwidthPackage" : {
      "Bandwidth" : 2,
      "BandwidthType" : "Basic",
      "InstanceId" : "gbwp-bp1d8xk8bg139j0fw****"
    },
    "RegionId" : "cn-hangzhou",
    "InstanceChargeType" : "PREPAY",
    "AcceleratorId" : "ga-bp1odcab8tmno0hdq****",
    "Description" : "Accelerator",
    "Bandwidth" : 5,
    "ExpiredTime" : 1577786252000,
    "Name" : "Accelerator",
    "CrossDomainBandwidthPackage" : {
      "Bandwidth" : 2,
      "InstanceId" : "gbwp-bp1d8xk8bg139j0fw****"
    }
  } ],
  "PageNumber" : 1
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


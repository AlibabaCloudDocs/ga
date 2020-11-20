# ListAccelerators

调用ListAccelerators查询全球加速实例列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListAccelerators&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAccelerators|系统规定参数。取值：**ListAccelerators**。 |
|RegionId|String|是|cn-hangzhou|全球加速所在的地域，仅取值**cn-hangzhou**。 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。 |
|AcceleratorId|String|否|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Accelerators|Array of Accelerators| |全球加速实例信息。 |
|AcceleratorId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|Bandwidth|Integer|5|全球加速实例的带宽，单位为**Mbps**。 |
|BasicBandwidthPackage|Struct| |全球加速实例绑定的基础带宽包的详情。 |
|Bandwidth|Integer|2|基础带宽包的带宽值。 |
|BandwidthType|String|Basic|基础带宽包的带宽类型。

 -   **Basic**：标准加速带宽。
-   **Enhanced**：增强加速带宽。
-   **Advanced**：精品加速带宽。 |
|InstanceId|String|gbwp-bp1d8xk8bg139j0fw\*\*\*\*|基础带宽包的实例ID。 |
|CenId|String|cen-hjfufhjfuwff\*\*\*\*|全球加速实例绑定的云企业网实例。 |
|CreateTime|Long|1577786252000|全球加速实例创建的时间。 |
|CrossDomainBandwidthPackage|Struct| |全球加速实例绑定的跨域加速包的详情。

 仅国际站返回该数组。 |
|Bandwidth|Integer|2|跨域加速包的带宽值，单位为**Mbps**。 |
|InstanceId|String|gbwp-bp1d8xk8bg139j0fw\*\*\*\*|跨域加速包的实例ID。 |
|DdosId|String|ddoscoo-cn-zz11vq7j\*\*\*\*|与全球加速实例绑定的DDoS高防实例ID。 |
|Description|String|Accelerator|全球加速实例的描述信息。 |
|DnsName|String|ga-bp1j80t5\*\*\*\*.uisnetwork.com|全球加速实例分配的CNAME地址。 |
|ExpiredTime|Long|1577786252000|全球加速实例到期的时间。 |
|InstanceChargeType|String|PREPAY|全球加速实例的计费方式，仅支持返回**PREPAY**（包年包月）。 |
|Name|String|Accelerator|全球加速实例的名称。 |
|RegionId|String|cn-hangzhou|全球加速实例所在的地域。 |
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
|Type|String|None|无效参数。 |
|PageNumber|Integer|1|当前页码。 |
|PageSize|Integer|10|每页包含的条目数。 |
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|请求ID。 |
|TotalCount|Integer|10|列表条目数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAccelerators
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListAcceleratorsResponse>
  <PageNumber>10</PageNumber>
  <TotalCount>2</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>E9C82FD2-C77F-4F10-B185-2F4E2670289E</RequestId>
  <Accelerators>
        <Description></Description>
        <DnsName>ga-bp1e98ijosxvu3vgb****.uisnetwork.com</DnsName>
        <State>active</State>
        <RegionId>cn-hangzhou</RegionId>
        <CreateTime>1581597755000</CreateTime>
        <CrossDomainBandwidthPackage>
              <InstanceId>gbwp-bp1pa01cgpfv3v4ti****</InstanceId>
              <Bandwidth>3</Bandwidth>
        </CrossDomainBandwidthPackage>
        <BasicBandwidthPackage>
              <BandwidthType>Basic</BandwidthType>
              <InstanceId>gbwp-bp17ep9hxkrrbxvq7****</InstanceId>
              <Bandwidth>2</Bandwidth>
        </BasicBandwidthPackage>
        <InstanceChargeType>PREPAY</InstanceChargeType>
        <ExpiredTime>1584115200000</ExpiredTime>
        <AcceleratorId>ga-bp1e98ijosxvu3vgb****</AcceleratorId>
  </Accelerators>
  <Accelerators>
        <Description></Description>
        <DnsName>ga-bp1j80t5gulpwx12r****.uisnetwork.com</DnsName>
        <State>active</State>
        <RegionId>cn-hangzhou</RegionId>
        <CreateTime>1581653081000</CreateTime>
        <CrossDomainBandwidthPackage></CrossDomainBandwidthPackage>
        <BasicBandwidthPackage>
              <BandwidthType>Basic</BandwidthType>
              <InstanceId>gbwp-bp1d8xk8bg139j0fw****</InstanceId>
              <Bandwidth>2</Bandwidth>
        </BasicBandwidthPackage>
        <InstanceChargeType>PREPAY</InstanceChargeType>
        <ExpiredTime>1584201600000</ExpiredTime>
        <AcceleratorId>ga-bp1j80t5gulpwx12r****</AcceleratorId>
  </Accelerators>
</ListAcceleratorsResponse>
```

`JSON` 格式

```
{
  "PageNumber": 10,
  "TotalCount": 2,
  "PageSize": 10,
  "RequestId": "E9C82FD2-C77F-4F10-B185-2F4E2670289E",
  "Accelerators": [
    {
      "Description": "",
      "DnsName": "ga-bp1e98ijosxvu3vgb****.uisnetwork.com",
      "State": "active",
      "RegionId": "cn-hangzhou",
      "CreateTime": 1581597755000,
      "CrossDomainBandwidthPackage": {
        "InstanceId": "gbwp-bp1pa01cgpfv3v4ti****",
        "Bandwidth": 3
      },
      "BasicBandwidthPackage": {
        "BandwidthType": "Basic",
        "InstanceId": "gbwp-bp17ep9hxkrrbxvq7****",
        "Bandwidth": 2
      },
      "InstanceChargeType": "PREPAY",
      "ExpiredTime": 1584115200000,
      "AcceleratorId": "ga-bp1e98ijosxvu3vgb****"
    },
    {
      "Description": "",
      "DnsName": "ga-bp1j80t5gulpwx12r****.uisnetwork.com",
      "State": "active",
      "RegionId": "cn-hangzhou",
      "CreateTime": 1581653081000,
      "CrossDomainBandwidthPackage": {},
      "BasicBandwidthPackage": {
        "BandwidthType": "Basic",
        "InstanceId": "gbwp-bp1d8xk8bg139j0fw****",
        "Bandwidth": 2
      },
      "InstanceChargeType": "PREPAY",
      "ExpiredTime": 1584201600000,
      "AcceleratorId": "ga-bp1j80t5gulpwx12r****"
    }
  ]
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


# DescribeAccelerator

调用DescribeAccelerator查询指定的全球加速实例信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DescribeAccelerator&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeAccelerator|系统规定参数。取值：**DescribeAccelerator**。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|要查询的全球加速实例ID。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属的地域，仅取值：**cn-hangzhou**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AcceleratorId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|BasicBandwidthPackage|Struct| |全球加速实例绑定的基础带宽包的详情。 |
|Bandwidth|Integer|2|基础带宽包的带宽值。 |
|BandwidthType|String|Basic|基础带宽包的带宽类型。

 -   **Basic**：标准加速带宽。
-   **Enhanced**：增强加速带宽。
-   **Advanced**：精品加速带宽。 |
|InstanceId|String|gbwp-bp1d8xk8bg139j0fw\*\*\*\*|基础带宽包的实例ID。 |
|CenId|String|cen-hjkduu767hc\*\*\*\*|全球加速实例绑定的云企业网实例ID。 |
|CreateTime|Long|1577786252000|全球加速实例创建的时间。 |
|CrossDomainBandwidthPackage|Struct| |全球加速实例绑定的跨域加速包的详情。

 仅国际站支持返回该数组。 |
|Bandwidth|Integer|2|跨域加速包的带宽值，单位为**Mbps**。 |
|InstanceId|String|gbwp-bp1d8xk8bg139j0fw\*\*\*\*|跨域加速包的实例ID。 |
|DdosId|String|ddoscoo-cn-zz11vq7j\*\*\*\*|与全球加速实例解绑的DDoS高防实例ID。 |
|Description|String|Accelerator|全球加速实例的描述信息。 |
|DnsName|String|ga-bp1j80t5\*\*\*\*.uisnetwork.com|全球加速实例分配的CNAME地址。 |
|ExpiredTime|Long|1577786252000|全球加速实例到期的时间。 |
|InstanceChargeType|String|PREPAY|全球加速实例的计费方式。 |
|Name|String|Accelerator|全球加速实例的名称。 |
|RegionId|String|cn-hangzhou|全球加速实例所在的地域。 |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。 |
|SecondDnsName|String|ga-bp1f609c76zg6zuna\*\*\*\*-1.aliyunga0047.com|全球加速联动DDoS高防实例的CNAME。 |
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

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeAccelerator
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeAcceleratorResponse>     
      <DnsName>ga-bp1j80t5gulpw****.uisnetwork.com</DnsName>
      <Spec>1</Spec>
      <BasicBandwidthPackage>
            <BandwidthType>Basic</BandwidthType>
            <InstanceId>gbwp-bp1d8xk8bg139j0fw****</InstanceId>
            <Bandwidth>2</Bandwidth>
      </BasicBandwidthPackage>
      <State>active</State>
      <RegionId>cn-hangzhou</RegionId>
      <CreateTime>1581653081000</CreateTime>
      <RequestId>64966488-B3E3-41E2-9570-4596117EC12E</RequestId>
      <InstanceChargeType>PREPAY</InstanceChargeType>
      <ExpiredTime>1584201600000</ExpiredTime>
      <AcceleratorId>ga-bp1j80t5gulpwx12r****</AcceleratorId>
</DescribeAcceleratorResponse>
```

`JSON` 格式

```
{
  "DnsName": "ga-bp1j80t5gulpw****.uisnetwork.com",
  "Spec": "1",
  "BasicBandwidthPackage": {
    "BandwidthType": "Basic",
    "InstanceId": "gbwp-bp1d8xk8bg139j0fw****",
    "Bandwidth": 2
  },
  "State": "active",
  "RegionId": "cn-hangzhou",
  "CreateTime": 1581653081000,
  "RequestId": "64966488-B3E3-41E2-9570-4596117EC12E",
  "InstanceChargeType": "PREPAY",
  "ExpiredTime": 1584201600000,
  "AcceleratorId": "ga-bp1j80t5gulpwx12r****"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


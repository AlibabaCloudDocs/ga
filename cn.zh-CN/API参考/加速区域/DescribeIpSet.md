# DescribeIpSet

调用DescribeIpSet查询加速地域信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DescribeIpSet&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeIpSet|系统规定参数。取值：**DescribeIpSet**。 |
|IpSetId|String|是|ips-bp11ilwqjdkjeg9r7\*\*\*\*|加速地域ID。

 您可以调用[ListIpSets](~~153247~~)查询指定全球加速实例下包含的加速地域ID。 |
|RegionId|String|是|cn-hangzhou|全球加速所在的地域ID，仅取值**cn-hangzhou**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AccelerateRegionId|String|cn-huhehaote|加速地域ID。 |
|Bandwidth|Integer|3|加速地域分配的带宽。单位：Mbps。 |
|IpAddressList|List|39.XX.XX.220|加速IP列表。 |
|IpSetId|String|ips-bp11ilwqjdkjeg9r7\*\*\*\*|加速地域ID。 |
|IpVersion|String|IPv4|IP地址协议版本。

 -   **IPv4**
-   **IPv6** |
|RequestId|String|6D2BFF54-6AF2-4679-88C4-2F2E187F16CB|请求ID。 |
|State|String|active|加速地域状态。

 -   **init**：初始化。
-   **active**：运行中。
-   **updating**：配置中。
-   **deleting**：删除中。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeIpSet
&IpSetId=ips-bp11ilwqjdkjeg9r7****
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DescribeIpSetResponse>
  <IpSetId>ips-bp11ilwqjdkjeg9r7****</IpSetId>
  <RequestId>6D2BFF54-6AF2-4679-88C4-2F2E187F16CB</RequestId>
  <IpVersion>IPv4</IpVersion>
  <State>active</State>
  <Bandwidth>2</Bandwidth>
  <IpAddressList>121.XX.XX.180</IpAddressList>
  <AccelerateRegionId>cn-hangzhou</AccelerateRegionId>
</DescribeIpSetResponse>
```

`JSON`格式

```
{
  "IpSetId": "ips-bp11ilwqjdkjeg9r7****",
  "RequestId": "6D2BFF54-6AF2-4679-88C4-2F2E187F16CB",
  "IpVersion": "IPv4",
  "State": "active",
  "Bandwidth": 2,
  "IpAddressList": [
    "121.XX.XX.180"
  ],
  "AccelerateRegionId": "cn-hangzhou"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


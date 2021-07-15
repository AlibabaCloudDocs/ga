# GetHealthStatus

调用GetHealthStatus获取监听实例的健康状态信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=GetHealthStatus&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetHealthStatus|系统规定参数。取值：**GetHealthStatus**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属的地域ID，仅取值：**cn-hangzhou**。 |
|ClientToken|String|否|5A2CFF0E-5718-45B5-9D4D-70B3FF3898|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|DryRun|Boolean|否|true|是否只预检此次请求，取值：

 -   **true**：发送检查请求，不会创建资源。检查项包括是否填写了必需参数、请求格式、业务限制。如果检查不通过，则返回对应错误。如果检查通过，则返回错误码`DryRunOperation`。
-   **false**（默认值）：发送正常请求，通过检查后返回HTTP 2xx状态码并直接进行操作。 |
|AcceleratorId|String|是|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|ListenerId|String|是|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF|请求ID。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|HealthStatus|String|normal|监听的健康状态。取值范围：

 -   **normal**：正常。
-   **abnormal**：异常。
-   **partiallyAbnormal**：部分异常。 |
|EndpointGroups|Array of endpointGroupHealthStatuses| |终端节点组信息。 |
|EndpointGroupId|String|epg-bp14sz7ftcwwjgrdm\*\*\*\*|终端节点组的ID。 |
|EndpointGroupType|String|default|终端节点组类型。

 -   **default**：默认终端节点组。
-   **virtual**：虚拟终端节点组。 |
|HealthStatus|String|normal|终端节点组的健康状态。取值范围：

 -   **init**：初始化
-   **normal**：正常。
-   **abnormal**：异常。
-   **partiallyAbnormal**：部分异常。 |
|ForwardingRuleIds|Array of String|frule-bp134k63nmtwmnweexxxx|转发策略ID列表。 |
|Endpoints|Array of endpointHealthStatuses| |终端节点信息。 |
|EndpointId|String|ep-hp33b2e43fays7s8\*\*\*\*|终端节点ID。 |
|Address|String|127.xxx.xxx.xxx|终端节点地址。 |
|HealthStatus|String|normal|终端节点的健康状态。取值范围：

 -   **init**：初始化
-   **normal**：正常。
-   **abnormal**：异常。
-   **partiallyAbnormal**：部分异常。 |
|HealthDetail|String|无|终端节点的健康检查明细。 |
|Port|Long|80|终端节点的端口。 |
|Type|String|Ip|终端节点类型。

 -   **Domain**：自定义域名。
-   **Ip**：自定义IP。
-   **PublicIp**：阿里云公网IP。
-   **ECS**：阿里云ECS实例。
-   **SLB**：阿里云SLB实例。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetHealthStatus
&RegionId=cn-hangzhou
&ClientToken=5A2CFF0E-5718-45B5-9D4D-70B3FF3898
&DryRun=true
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetHealthStatusResponse>
    <RequestId>64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF</RequestId>
    <ListenerId>lsr-bp1bpn0kn908w4nbw****</ListenerId>
    <HealthStatus>normal</HealthStatus>
    <EndpointGroups>
        <EndpointGroupId>epg-bp14sz7ftcwwjgrdm****</EndpointGroupId>
        <EndpointGroupType>default</EndpointGroupType>
        <HealthStatus>normal</HealthStatus>
        <ForwardingRuleIds>frule-bp134k63nmtwmnweexxxx</ForwardingRuleIds>
        <Endpoints>
            <EndpointId>ep-hp33b2e43fays7s8****</EndpointId>
            <Address>127.xxx.xxx.xxx</Address>
            <HealthStatus>normal</HealthStatus>
            <HealthDetail>无</HealthDetail>
            <Port>80</Port>
            <Type>Ip</Type>
        </Endpoints>
    </EndpointGroups>
</GetHealthStatusResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF",
  "ListenerId" : "lsr-bp1bpn0kn908w4nbw****",
  "HealthStatus" : "normal",
  "EndpointGroups" : [ {
    "EndpointGroupId" : "epg-bp14sz7ftcwwjgrdm****",
    "EndpointGroupType" : "default",
    "HealthStatus" : "normal",
    "ForwardingRuleIds" : [ "frule-bp134k63nmtwmnweexxxx" ],
    "Endpoints" : [ {
      "EndpointId" : "ep-hp33b2e43fays7s8****",
      "Address" : "127.xxx.xxx.xxx",
      "HealthStatus" : "normal",
      "HealthDetail" : "无",
      "Port" : 80,
      "Type" : "Ip"
    } ]
  } ]
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


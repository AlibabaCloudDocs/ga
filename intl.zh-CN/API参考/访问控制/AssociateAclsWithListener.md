# AssociateAclsWithListener

调用AssociateAclsWithListener关联ACL到监听。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=AssociateAclsWithListener&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AssociateAclsWithListener|系统规定参数。取值：**AssociateAclsWithListener**。 |
|RegionId|String|是|64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF|请求ID。 |
|ListenerId|String|是|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |
|AclType|String|是|white|访问控制类型：

 -   **White**：仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问全球加速监听。如果开启了白名单访问，但访问策略组中没有添加任何IP，则全球加速监听不会转发请求。
-   **Black**：来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。如果开启了黑名单访问，但访问策略组中没有添加任何IP，则全球加速监听会转发全部请求。 |
|ClientToken|String|否|02fb3da4\*\*\*\*|客户端Token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。 |
|DryRun|Boolean|否|true|是否只预检此次请求，取值：

 -   **true**：发送检查请求，不会创建资源。检查项包括是否填写了必需参数、请求格式、业务限制。如果检查不通过，则返回对应错误。如果检查通过，则返回错误码`DryRunOperation`。
-   **false**（默认值）：发送正常请求，通过检查后返回HTTP 2xx状态码并直接进行操作。 |
|AclIds.N|String|是|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL实例ID，最多支持关联3个ACL实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF|请求ID。 |
|AclIds|Array of String|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL实例ID，最多支持关联3个ACL实例ID。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=AssociateAclsWithListener
&RegionId=64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF
&AclIds=["nacl-hp34s2h0xx1ht4nwo****"]
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&AclType=white
&ClientToken=02fb3da4****
&DryRun=true
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<AssociateAclsWithListenerResponse>
    <RequestId>64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF</RequestId>
    <AclIds>nacl-hp34s2h0xx1ht4nwo****</AclIds>
    <ListenerId>lsr-bp1bpn0kn908w4nbw****</ListenerId>
</AssociateAclsWithListenerResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF",
  "AclIds" : [ "nacl-hp34s2h0xx1ht4nwo****" ],
  "ListenerId" : "lsr-bp1bpn0kn908w4nbw****"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


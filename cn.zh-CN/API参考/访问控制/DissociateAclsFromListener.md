# DissociateAclsFromListener

调用DissociateAclsFromListener将ACL与监听解除关联。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DissociateAclsFromListener&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DissociateAclsFromListener|系统规定参数。取值：**DissociateAclsFromListener**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属的地域ID，仅取值：**cn-hangzhou**。 |
|ListenerId|String|是|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID |
|ClientToken|String|否|5A2CFF0E-5718-45B5-9D4D-70B3FF3898|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。

 若您未指定，则系统自动使用API请求的RequestId作为ClientToken标识。每次API请求的RequestId可能不一样。 |
|DryRun|Boolean|否|true|是否只预检此次请求，取值：

 -   **true**：发送检查请求，不会创建资源。检查项包括是否填写了必需参数、请求格式、业务限制。如果检查不通过，则返回对应错误。如果检查通过，则返回错误码`DryRunOperation`。
-   **false**（默认值）：发送正常请求，通过检查后返回HTTP 2xx状态码并直接进行操作。 |
|AclIds.N|String|是|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL实例ID，一次最多支持将3个ACL实例与监听解除关联。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID |
|AclIds|Array of String|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL实例ID，一次最多支持将3个ACL实例与监听解除关联。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听实例ID |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DissociateAclsFromListener
&RegionId=cn-hangzhou
&AclIds=["nacl-hp34s2h0xx1ht4nwo****"]
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&ClientToken=5A2CFF0E-5718-45B5-9D4D-70B3FF3898
&DryRun=true
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DissociateAclsFromListenerResponse>
    <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    <AclIds>nacl-hp34s2h0xx1ht4nwo****</AclIds>
    <ListenerId>lsr-bp1bpn0kn908w4nbw****</ListenerId>
</DissociateAclsFromListenerResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "CEF72CEB-54B6-4AE8-B225-F876FF7BA984",
  "AclIds" : [ "nacl-hp34s2h0xx1ht4nwo****" ],
  "ListenerId" : "lsr-bp1bpn0kn908w4nbw****"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


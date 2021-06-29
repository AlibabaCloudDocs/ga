# RemoveEntriesFromAcl

调用RemoveEntriesFromAcl删除访问控制策略组中的IP条目。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=RemoveEntriesFromAcl&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemoveEntriesFromAcl|系统规定参数。取值：**RemoveEntriesFromAcl**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属的地域ID，仅取值：**cn-hangzhou**。 |
|AclId|String|是|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL实例ID |
|ClientToken|String|否|593B0448-D13E-4C56-AC0D-FDF0FDE0E9A3|保证请求幂等性。

 从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|DryRun|Boolean|否|true|是否只预检此次请求，取值：

 -   **true**：发送检查请求，不会创建资源。检查项包括是否填写了必需参数、请求格式、业务限制。如果检查不通过，则返回对应错误。如果检查通过，则返回错误码DryRunOperation。
-   **false**（默认值）：发送正常请求，通过检查后返回HTTP 2xx状态码并直接进行操作。 |
|AclEntries.N.Entry|String|否|10.0.1.1/24|访问控制条目IP地址段。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF|请求ID |
|AclId|String|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL ID |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=RemoveEntriesFromAcl
&RegionId=cn-hangzhou
&AclId=nacl-hp34s2h0xx1ht4nwo****
&AclEntries=[{"Entry":"10.0.1.1/24"}]
&ClientToken=593B0448-D13E-4C56-AC0D-FDF0FDE0E9A3
&DryRun=true
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<RemoveEntriesFromAclResponse>
    <RequestId>64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF</RequestId>
    <AclId>nacl-hp34s2h0xx1ht4nwo****</AclId>
</RemoveEntriesFromAclResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF",
  "AclId" : "nacl-hp34s2h0xx1ht4nwo****"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


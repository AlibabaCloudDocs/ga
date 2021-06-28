# DeleteAcl

调用DeleteAcl删除访问控制。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=DeleteAcl&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteAcl|系统规定参数。取值：**DeleteAcl**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值：**cn-hangzhou**。 |
|AclId|String|是|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL ID。 |
|ClientToken|String|否|02fb3da4\*\*\*\*|客户端Token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。 |
|DryRun|Boolean|否|true|是否只预检此次请求，取值：

 -   **true**：发送检查请求，不会创建资源。检查项包括是否填写了必需参数、请求格式、业务限制。如果检查不通过，则返回对应错误。如果检查通过，则返回错误码DryRunOperation。
-   **false**（默认值）：发送正常请求，通过检查后返回HTTP 2xx状态码并直接进行操作。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。 |
|AclId|String|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteAcl
&RegionId=cn-hangzhou
&AclId=nacl-hp34s2h0xx1ht4nwo****
&ClientToken=02fb3da4****
&DryRun=true
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeleteAclResponse>
    <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
    <AclId>nacl-hp34s2h0xx1ht4nwo****</AclId>
</DeleteAclResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "365F4154-92F6-4AE4-92F8-7FF34B540710",
  "AclId" : "nacl-hp34s2h0xx1ht4nwo****"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ga)查看更多错误码。


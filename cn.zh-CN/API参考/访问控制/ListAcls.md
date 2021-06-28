# ListAcls

调用ListAcls查询某一个地域的ACL列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=ListAcls&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAcls|系统规定参数。取值：**ListAcls**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所属的地域ID，仅取值：**cn-hangzhou**。 |
|ClientToken|String|否|02fb3da4\*\*\*\*|客户端Token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。 |
|AclIds|Array of String|否|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL ID，一次最多支持查询20个ACL ID。 |
|AclName|String|否|test-acl|ACL名称。一次最多支持查询10个ACL名称。

 长度为2~128个字符，必须以大小写字母或中文开头，可包含数字，半角句号（.），下划线（\_）和短划线（-）。 |
|NextToken|String|否|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|用来标记当前开始读取的位置，为空表示从头开始。 |
|MaxResults|Integer|否|50|本次读取的最大数据记录数量，此参数为可选参数，取值**1**~**100**，参数传入为空时，默认为**20**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF|请求ID。 |
|TotalCount|Integer|10|本次请求条件下的数据总量。 |
|NextToken|String|FFmyTO70t\*\*\*\*|用来标记当前开始读取的位置，为空表示从头开始。 |
|MaxResults|Integer|5|本次读取的最大数据记录数量，此参数为可选参数，取值1~100，参数传入为空时，默认为20。 |
|Acls|Array of GaAcls| |ACL列表。 |
|AclId|String|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL ID。 |
|AclName|String|test-acl|ACL名称。 |
|AddressIPVersion|String|IPv4|ACL IP版本，取值：IPv4。 |
|AclStatus|String|Available|ACL状态，取值：

 -   **Provisioning**：创建中。
-   **Available**：正常可用状态。
-   **Configuring**：配置中。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAcls
&RegionId=cn-hangzhou
&ClientToken=02fb3da4****
&AclIds=["nacl-hp34s2h0xx1ht4nwo****"]
&AclName=test-acl
&NextToken=caeba0bbb2be03f84eb48b699f0a****
&MaxResults=50
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListAclsResponse>
    <RequestId>64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF</RequestId>
    <TotalCount>10</TotalCount>
    <NextToken>FFmyTO70t****</NextToken>
    <MaxResults>5</MaxResults>
    <Acls>
        <AclId>nacl-hp34s2h0xx1ht4nwo****</AclId>
        <AclName>test-acl</AclName>
        <AddressIPVersion>IPv4</AddressIPVersion>
        <AclStatus>Available</AclStatus>
    </Acls>
</ListAclsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "64ADAB1E-0B7F-4FD8-A404-3BECC0E9CCFF",
  "TotalCount" : 10,
  "NextToken" : "FFmyTO70t****",
  "MaxResults" : 5,
  "Acls" : [ {
    "AclId" : "nacl-hp34s2h0xx1ht4nwo****",
    "AclName" : "test-acl",
    "AddressIPVersion" : "IPv4",
    "AclStatus" : "Available"
  } ]
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


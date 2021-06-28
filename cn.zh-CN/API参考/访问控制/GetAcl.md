# GetAcl

调用GetAcl获取访问控制策略。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=GetAcl&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAcl|系统规定参数。取值：**GetAcl**。 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域ID，仅取值：**cn-hangzhou**。 |
|AclId|String|是|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。 |
|AclId|String|nacl-hp34s2h0xx1ht4nwo\*\*\*\*|ACL实例ID。 |
|AddressIPVersion|String|IPv4|ACL IP版本，取值：IPv4。 |
|AclStatus|String|Available|ACL状态，取值：

 -   **Provisioning**：创建中
-   **Available**：正常可用状态
-   **Configuring**：配置中 |
|AclEntries|Array of AclEntries| |添加的访问控制条目列表。最多支持20个访问控制条目。 |
|Entry|String|10.0.1.1/24|访问控制条目IP地址段。 |
|EntryDescription|String|test-entry|访问控制条目备注描述，长度限制为1~256个字符，允许包含字母、数字、短划线（-）、正斜线（/）、半角句号（.）和下划线（\_），支持中文字符。 |
|RelatedListeners|Array of RelatedListeners| |关联的监听列表。 |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|监听ID。 |
|AclType|String|White|访问控制类型：

 -   **White**：仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问全球加速实例监听。如果开启了白名单访问，但访问策略组中没有添加任何IP，则全球加速实例监听不会转发请求。
-   **Black**：来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。如果开启了黑名单访问，但访问策略组中没有添加任何IP，则全球加速实例监听会转发全部请求。 |
|AcceleratorId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|全球加速实例ID。 |
|AclName|String|test-acl|ACL的名称。必须以大小写字母或中文开头，可包含数字，半角句号（.），下划线（\_）和短划线（-），限制长度为2~128个字符。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetAcl
&RegionId=cn-hangzhou
&AclId=nacl-hp34s2h0xx1ht4nwo****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetAclResponse>
    <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    <AclId>nacl-hp34s2h0xx1ht4nwo****</AclId>
    <AddressIPVersion>IPv4</AddressIPVersion>
    <AclStatus>Available</AclStatus>
    <AclEntries>
        <Entry>10.0.1.1/24</Entry>
        <EntryDescription>test-entry</EntryDescription>
    </AclEntries>
    <RelatedListeners>
        <ListenerId>lsr-bp1bpn0kn908w4nbw****</ListenerId>
        <AclType>White</AclType>
        <AcceleratorId>ga-bp1odcab8tmno0hdq****</AcceleratorId>
    </RelatedListeners>
    <AclName>test-acl</AclName>
</GetAclResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "CEF72CEB-54B6-4AE8-B225-F876FF7BA984",
  "AclId" : "nacl-hp34s2h0xx1ht4nwo****",
  "AddressIPVersion" : "IPv4",
  "AclStatus" : "Available",
  "AclEntries" : [ {
    "Entry" : "10.0.1.1/24",
    "EntryDescription" : "test-entry"
  } ],
  "RelatedListeners" : [ {
    "ListenerId" : "lsr-bp1bpn0kn908w4nbw****",
    "AclType" : "White",
    "AcceleratorId" : "ga-bp1odcab8tmno0hdq****"
  } ],
  "AclName" : "test-acl"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


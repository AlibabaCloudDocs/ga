# AttachDdosToAccelerator

调用AttachDdosToAccelerator将DDoS高防实例与全球加速实例绑定。

## API描述

调用该接口时，系统会判断全球加速是否拥有服务关联角色AliyunServiceRoleForGaAntiDdos：

-   如果全球加速不存在服务关联角色AliyunServiceRoleForGaAntiDdos，系统会自动创建该服务关联角色，并为该服务关联角色添加名称为AliyunServiceRolePolicyForGaAntiDdos的权限策略，授予全球加速拥有访问DDoS高防实例的权限。
-   如果全球加速已经拥有服务关联角色AliyunServiceRoleForGaAntiDdos，则不会重复创建该服务关联角色。

详细信息，请参见[AliyunServiceRoleForGaAntiDdos](~~186805~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ga&api=AttachDdosToAccelerator&type=RPC&version=2019-11-20)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AttachDdosToAccelerator|系统规定参数。取值：**AttachDdosToAccelerator**。 |
|AcceleratorId|String|否|ga-bp1odcab8tmno0hdq\*\*\*\*|要绑定DDoS高防实例的全球加速实例ID。 |
|DdosId|String|否|ddoscoo-cn-zz11vq7j\*\*\*\*|要绑定到全球加速实例的DDoS高防实例ID。 |
|DdosRegionId|String|否|cn-hangzhou|DDoS高防实例所在的地域，取值：

 -   **cn-hangzhou**：中国内地。
-   **ap-southeast-1**：非中国内地。 |
|RegionId|String|否|cn-hangzhou|全球加速实例所在的地域，仅取值**cn-hangzhou**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|DdosId|String|ddoscoo-cn-zz11vq7j\*\*\*\*|绑定到全球加速实例的DDoS高防实例ID。 |
|GaId|String|ga-bp1odcab8tmno0hdq\*\*\*\*|绑定了DDoS高防实例的全球加速实例ID。 |
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=AttachDdosToAccelerator
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<AttachDdosToAcceleratorResponse>
      <DdosId>ddoscoo-cn-zz11vq7j****</DdosId>
      <GaId>ga-bp1odcab8tmno0hdq****</GaId>
      <RequestId>E9C82FD2-C77F-4F10-B185-2F4E2670289E</RequestId>
</AttachDdosToAcceleratorResponse>
```

`JSON` 格式

```
{
  "DdosId": "ddoscoo-cn-zz11vq7j****",
  "GaId": "ga-bp1odcab8tmno0hdq****",
  "RequestId": "E9C82FD2-C77F-4F10-B185-2F4E2670289E"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|DdosId.Error|Failed to find the DDoS instance based on the DDoS ID.|获取DDoS信息失败|
|400|NoPermission.GaDdosRoleSession|You are not authorized to perform the operation.|用户没有创建服务关联角色的权限，请联系主账号或权限管理员授权当前用户AliyunGlobalAccelerationFullAccess或者创建服务关联角色的自定义权限。自定义权限策略的相关信息如下： ServiceName：ddos.ga.aliyuncs.com 服务关联角色名称：AliyunServiceRoleForGaAntiDDos 执行该操作所需的用户权限：ram:CreateServiceLinkedRole|

访问[错误中心](https://error-center.aliyun.com/status/product/Ga)查看更多错误码。


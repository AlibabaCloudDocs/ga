# API概览

全球加速提供以下API供您使用。

## 全球加速实例

|API|描述|
|---|--|
|[DescribeAccelerator](/intl.zh-CN/API参考/全球加速实例/DescribeAccelerator.md)|查询指定的全球加速实例信息。|
|[ListAccelerators](/intl.zh-CN/API参考/全球加速实例/ListAccelerators.md)|查询全球加速实例列表。|
|[UpdateAccelerator](/intl.zh-CN/API参考/全球加速实例/UpdateAccelerator.md)|修改全球加速实例。|
|[CreateAccelerator](/intl.zh-CN/API参考/全球加速实例/CreateAccelerator.md)|创建一个全球加速实例。|
|[DeleteAccelerator](/intl.zh-CN/API参考/全球加速实例/DeleteAccelerator.md)|删除指定的全球加速实例。|

## 带宽包

|API|描述|
|---|--|
|[BandwidthPackageAddAccelerator](/intl.zh-CN/API参考/带宽包/BandwidthPackageAddAccelerator.md)|将带宽包与全球加速实例绑定。|
|[BandwidthPackageRemoveAccelerator](/intl.zh-CN/API参考/带宽包/BandwidthPackageRemoveAccelerator.md)|将带宽包与全球加速实例解绑。|
|[DescribeBandwidthPackage](/intl.zh-CN/API参考/带宽包/DescribeBandwidthPackage.md)|查询带宽包。|
|[ListBandwidthPackages](/intl.zh-CN/API参考/带宽包/ListBandwidthPackages.md)|查询带宽包列表。|
|[UpdateBandwidthPackage](/intl.zh-CN/API参考/带宽包/UpdateBandwidthPackage.md)|修改带宽包。|
|[ReplaceBandwidthPackage](/intl.zh-CN/API参考/带宽包/ReplaceBandwidthPackage.md)|替换带宽包。|

## 加速地域

|API|描述|
|---|--|
|[CreateIpSets](/intl.zh-CN/API参考/加速地域/CreateIpSets.md)|创建加速地域。|
|[DescribeIpSet](/intl.zh-CN/API参考/加速地域/DescribeIpSet.md)|查询加速地域。|
|[ListIpSets](/intl.zh-CN/API参考/加速地域/ListIpSets.md)|查询加速地域列表。|
|[UpdateIpSet](/intl.zh-CN/API参考/加速地域/UpdateIpSet.md)|修改加速区域中指定的加速地域。|
|[UpdateIpSets](/intl.zh-CN/API参考/加速地域/UpdateIpSets.md)|修改加速区域中的多个加速地域。|
|[DeleteIpSet](/intl.zh-CN/API参考/加速地域/DeleteIpSet.md)|删除一个加速地域。|
|[DeleteIpSets](/intl.zh-CN/API参考/加速地域/DeleteIpSets.md)|删除多个加速地域。|

## 监听

|API|描述|
|---|--|
|[CreateListener](/intl.zh-CN/API参考/监听/CreateListener.md)|创建监听。|
|[DescribeListener](/intl.zh-CN/API参考/监听/DescribeListener.md)|查询监听。|
|[ListListeners](/intl.zh-CN/API参考/监听/ListListeners.md)|查询监听列表。|
|[UpdateListener](/intl.zh-CN/API参考/监听/UpdateListener.md)|修改监听。|
|[DeleteListener](/intl.zh-CN/API参考/监听/DeleteListener.md)|删除监听。|

## 终端节点组

|API|描述|
|---|--|
|[CreateEndpointGroup](/intl.zh-CN/API参考/终端节点组/CreateEndpointGroup.md)|创建终端节点组。|
|[DescribeEndpointGroup](/intl.zh-CN/API参考/终端节点组/DescribeEndpointGroup.md)|查询指定终端节点组。|
|[ListEndpointGroups](/intl.zh-CN/API参考/终端节点组/ListEndpointGroups.md)|查询终端节点组列表。|
|[UpdateEndpointGroup](/intl.zh-CN/API参考/终端节点组/UpdateEndpointGroup.md)|修改终端节点组的业务配置。|
|[UpdateEndpointGroupAttribute](/intl.zh-CN/API参考/终端节点组/UpdateEndpointGroupAttribute.md)|修改终端节点组的名称和描述。|
|[DeleteEndpointGroup](/intl.zh-CN/API参考/终端节点组/DeleteEndpointGroup.md)|删除终端节点组。|

## 区域与地域

|API|描述|
|---|--|
|[ListAccelerateAreas](/intl.zh-CN/API参考/区域与地域/ListAccelerateAreas.md)|查询可用的加速区域和地域。|
|[ListBusiRegions](/intl.zh-CN/API参考/区域与地域/ListBusiRegions.md)|查询加速业务支持的地域。|
|[DescribeRegions](/intl.zh-CN/API参考/区域与地域/DescribeRegions.md)|查询实例部署的地域。|

## 转发策略

|API|描述|
|---|--|
|[CreateForwardingRules](/intl.zh-CN/API参考/转发策略/CreateForwardingRules.md)|创建转发策略。|
|[UpdateForwardingRules](/intl.zh-CN/API参考/转发策略/UpdateForwardingRules.md)|更新转发策略。|
|[ListForwardingRules](/intl.zh-CN/API参考/转发策略/ListForwardingRules.md)|查看已经创建的转发策略信息。|
|[DeleteForwardingRules](/intl.zh-CN/API参考/转发策略/DeleteForwardingRules.md)|删除转发策略。|

## 访问控制

|API|描述|
|---|--|
|[UpdateAclAttribute](/intl.zh-CN/API参考/访问控制/UpdateAclAttribute.md)|修改访问控制策略组属性。|
|[AddEntriesToAcl](/intl.zh-CN/API参考/访问控制/AddEntriesToAcl.md)|在访问控制策略组中添加IP条目。|
|[ListAcls](/intl.zh-CN/API参考/访问控制/ListAcls.md)|查询某一个地域的ACL列表。|
|[GetAcl](/intl.zh-CN/API参考/访问控制/GetAcl.md)|获取访问控制策略。|
|[DeleteAcl](/intl.zh-CN/API参考/访问控制/DeleteAcl.md)|删除访问控制。|
|[AssociateAclsWithListener](/intl.zh-CN/API参考/访问控制/AssociateAclsWithListener.md)|关联ACL到监听。|
|[DissociateAclsFromListener](/intl.zh-CN/API参考/访问控制/DissociateAclsFromListener.md)|将ACL与监听解除关联。|


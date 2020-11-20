# AliyunServiceRoleForGaVpcEndpoint

如果您的全球加速不存在服务关联角色AliyunServiceRoleForGaVpcEndpoint，您在配置云服务器ECS或负载均衡SLB为全球加速终端节点时，系统会自动创建服务关联角色AliyunServiceRoleForGaVpcEndpoint。

## AliyunServiceRoleForGaVpcEndpoint简介

AliyunServiceRoleForGaVpcEndpoint是全球加速的一种服务关联角色SLR（Service Linked Role），在配置全球加速终端节点时，全球加速需要拥有该服务关联角色才能将云服务器ECS和负载均衡SLB添加为全球加速的终端节点。

**说明：** 服务关联角色是指与某个云服务关联的访问控制（RAM）角色。在某些场景下，为了完成云服务的某个功能，需要获取访问其他云服务的权限。通过服务关联角色，您可以更好的创建云服务正常操作所需的权限，避免误操作带来的风险。更多关于服务关联角色的信息，请参见[服务关联角色](/intl.zh-CN/角色管理/服务关联角色.md)。

## 创建服务关联角色AliyunServiceRoleForGaVpcEndpoint所需的权限

主账号默认拥有创建服务关联角色AliyunServiceRoleForGaVpcEndpoint的权限，RAM用户必须拥有以下权限，才可以创建服务关联角色AliyunServiceRoleForGaVpcEndpoint：

```
{
      "Action": "ram:CreateServiceLinkedRole",
      "Resource": "*",
      "Effect": "Allow",
      "Condition": {
        "StringEquals": {
          "ram:ServiceName": "vpcendpoint.ga.aliyuncs.com"
        }
      }
}
```

您可以通过以下两种方式为RAM用户授予创建AliyunServiceRoleForGaVpcEndpoint所需的权限：

-   为RAM用户添加管理员权限策略AliyunGlobalAccelerationFullAccess。详细信息，请参见[为RAM角色授权](/intl.zh-CN/角色管理/为RAM角色授权.md)。

    **说明：** 创建全球加速服务关联角色AliyunServiceRoleForGaVpcEndpoint的权限通常包含在管理员权限策略AliyunGlobalAccelerationFullAccess中，因此只要拥有全球加速的管理员权限，就可以为全球加速创建服务关联角色AliyunServiceRoleForGaVpcEndpoint。

-   添加自定义权限策略，并为RAM用户授权。自定义权限策略包含以下权限：

    ```
    {
          "Action": "ram:CreateServiceLinkedRole",
          "Resource": "*",
          "Effect": "Allow",
          "Condition": {
            "StringEquals": {
              "ram:ServiceName": "vpcendpoint.ga.aliyuncs.com"
            }
          }
    }
    ```

    详细信息，请参见[创建自定义策略](/intl.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)和[为RAM角色授权](/intl.zh-CN/角色管理/为RAM角色授权.md)。


## 创建服务关联角色AliyunServiceRoleForGaVpcEndpoint

您在配置云服务器ECS或负载均衡SLB为全球加速终端节点时，系统会判断全球加速是否拥有服务关联角色AliyunServiceRoleForGaVpcEndpoint：

-   如果全球加速不存在服务关联角色AliyunServiceRoleForGaVpcEndpoint，系统会自动创建该服务关联角色，并为该服务关联角色添加名称为AliyunServiceRoleForGaVpcEndpoint的权限策略，授予全球加速拥有访问云服务器ECS和负载均衡SLB的权限，策略内容如下：

    ```
    {
      "Version": "1",
      "Statement": [
        {
          "Effect": "Allow",
          "Resource": "*",
          "Action": [
            "ecs:CreateNetworkInterface",
            "ecs:DeleteNetworkInterface",
            "ecs:DescribeNetworkInterfaces",
            "ecs:ModifyNetworkInterfaceAttribute",
            "ecs:DescribeSecurityGroups",
            "ecs:CreateSecurityGroup",
            "ecs:AuthorizeSecurityGroup",
            "ecs:AuthorizeSecurityGroupEgress",
            "ecs:RevokeSecurityGroup",
            "ecs:RevokeSecurityGroupEgress",
            "ecs:JoinSecurityGroup",
            "ecs:LeaveSecurityGroup",
            "ecs:DeleteSecurityGroup",
            "ecs:DescribeSecurityGroupAttribute",
            "ecs:DescribeSecurityGroups",
            "ecs:DescribeSecurityGroupReferences",
            "ecs:ModifySecurityGroupAttribute",
            "ecs:ModifySecurityGroupEgressRule",
            "ecs:ModifySecurityGroupPolicy",
            "ecs:ModifySecurityGroupRule",
            "vpc:DescribeVSwitches"
          ]
        },
        {
          "Action": "ram:DeleteServiceLinkedRole",
          "Resource": "*",
          "Effect": "Allow",
          "Condition": {
            "StringEquals": {
              "ram:ServiceName": "vpcendpoint.ga.aliyuncs.com"
            }
          }
        }
      ]
    }
    ```

-   如果全球加速已经拥有服务关联角色AliyunServiceRoleForGaVpcEndpoint，则不会重复创建该服务关联角色。

## 删除服务关联角色AliyunServiceRoleForGaVpcEndpoint

系统不会自动删除全球加速的服务关联角色AliyunServiceRoleForGaVpcEndpoint，如果您要删除该服务关联角色，请先删除终端节点类型为云服务器ECS和负载均衡SLB的终端节点，然后再删除服务关联角色AliyunServiceRoleForGaVpcEndpoint。详细信息，请参见：

-   [删除监听](/intl.zh-CN/用户指南/监听/删除监听.md)
-   [删除服务关联角色](/intl.zh-CN/角色管理/服务关联角色.md)


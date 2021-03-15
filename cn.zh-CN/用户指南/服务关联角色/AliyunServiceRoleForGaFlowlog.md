# AliyunServiceRoleForGaFlowlog

本文为您介绍全球加速服务关联角色AliyunServiceRoleForGaFlowlog的应用场景，以及如何创建删除服务关联角色。

## AliyunServiceRoleForGaFlowlog简介

AliyunServiceRoleForGaFlowlog是全球加速的一种服务关联角色SLR（Service Linked Role）。拥有该角色后，阿里云全球加速服务可以访问您的日志服务（SLS），将流日志投递到您的SLS。

**说明：** 服务关联角色是指与某个云服务关联的访问控制（RAM）角色。在某些场景下，为了完成云服务的某个功能，需要获取访问其他云服务的权限。通过服务关联角色，您可以更好的创建云服务正常操作所需的权限，避免误操作带来的风险。更多信息，请参见[服务关联角色](/cn.zh-CN/角色管理/服务关联角色.md)。

## 创建服务关联角色AliyunServiceRoleForGaFlowlog所需的权限

主账号默认拥有创建服务关联角色AliyunServiceRoleForGaFlowlog的权限，RAM用户必须拥有以下权限，才可以进行创建：

```
{
      "Action": "ram:CreateServiceLinkedRole",
      "Resource": "*",
      "Effect": "Allow",
      "Condition": {
        "StringEquals": {
          "ram:ServiceName": "flowlog.ga.aliyuncs.com"
        }
      }
}
```

您可以通过以下两种方式为RAM用户授予创建AliyunServiceRoleForGaFlowlog所需的权限：

-   为RAM用户添加管理员权限策略AliyunGlobalAccelerationFullAccess。具体操作，请参见[为RAM角色授权](/cn.zh-CN/角色管理/为RAM角色授权.md)。

    **说明：** 创建全球加速服务关联角色的权限通常包含在管理员权限策略AliyunGlobalAccelerationFullAccess中，因此只要拥有全球加速的管理员权限，就可以为全球加速创建服务关联角色。

-   添加自定义权限策略，并为RAM用户授权。自定义权限策略包含以下权限：

    ```
    {
          "Action": "ram:CreateServiceLinkedRole",
          "Resource": "*",
          "Effect": "Allow",
          "Condition": {
            "StringEquals": {
              "ram:ServiceName": "flowlog.ga.aliyuncs.com"
            }
          }
    }
    ```

    具体操作，请参见[创建自定义策略](/cn.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)和[为RAM角色授权](/cn.zh-CN/角色管理/为RAM角色授权.md)。


## 创建服务关联角色AliyunServiceRoleForGaFlowlog

为全球加速实例开启流日志的投递功能，系统会自动创建服务关联角色AliyunServiceRoleForGaFlowlog，并为该服务关联角色添加名称为AliyunServiceRolePolicyForGaFlowlog的权限策略，授予全球加速拥有访问用户流日志的权限，策略内容如下：

```
{
  "Version": "1",
  "Statement": [
    {
      "Action": [
        "log:PostLogStoreLogs"
      ],
      "Resource": "*",
      "Effect": "Allow"
    },
    {
      "Action": "ram:DeleteServiceLinkedRole",
      "Resource": "*",
      "Effect": "Allow",
      "Condition": {
        "StringEquals": {
          "ram:ServiceName": "flowlog.ga.aliyuncs.com"
        }
      }
    }
  ]
}
```

## 删除服务关联角色AliyunServiceRoleForGaFlowlog

系统不会自动删除全球加速的服务关联角色AliyunServiceRoleForGaFlowlog，如果您要删除该服务关联角色，请先删除所有全球加速实例，然后再删除服务关联角色AliyunServiceRolePolicyForGaFlowlog。具体操作，请参见[删除服务关联角色](/cn.zh-CN/角色管理/服务关联角色.md)。


# AliyunServiceRoleForGaAntiDdos

如果您的全球加速不存在服务关联角色AliyunServiceRoleForGaVpcEndpoint，您在为全球加速提升DDoS阈值时，系统会自动创建服务关联角色AliyunServiceRoleForGaVpcEndpoint，以获取访问DDoS高防实例的权限。

## AliyunServiceRoleForGaAntiDdos简介

AliyunServiceRoleForGaAntiDdos是全球加速的一种服务关联角色SLR（Service Linked Role），在为全球加速提升DDoS阈值时，需要拥有该服务关联角色才能访问DDoS高防实例。如何提升DDoS阈值，请参见[提升DDoS阈值](/cn.zh-CN/用户指南/全球加速实例/提升DDoS阈值.md)。

**说明：** 服务关联角色是指与某个云服务关联的访问控制（RAM）角色。在某些场景下，为了完成云服务的某个功能，需要获取访问其他云服务的权限。通过服务关联角色，您可以更好的创建云服务正常操作所需的权限，避免误操作带来的风险。更多关于服务关联角色的信息，请参见[服务关联角色](/cn.zh-CN/角色管理/服务关联角色.md)。

## 创建服务关联角色AliyunServiceRoleForGaAntiDdos所需的权限

主账号默认拥有创建服务关联角色AliyunServiceRoleForGaAntiDdos的权限，RAM用户必须拥有以下权限，才可以创建服务关联角色AliyunServiceRoleForGaAntiDdos：

```
{
    "Action": "ram:CreateServiceLinkedRole",
    "Resource": "*",
    "Effect": "Allow",
    "Condition": {
        "StringEquals": {
            "ram:ServiceName": "ddos.ga.aliyuncs.com"
        }
    }
}
```

您可以通过以下两种方式为RAM用户授予创建AliyunServiceRoleForGaAntiDdos所需的权限：

-   为RAM用户添加管理员权限策略AliyunGlobalAccelerationFullAccess。详细信息，请参见[为RAM角色授权](/cn.zh-CN/角色管理/为RAM角色授权.md)。

    **说明：** 创建全球加速服务关联角色AliyunServiceRoleForGaAntiDdos的权限通常包含在管理员权限策略AliyunGlobalAccelerationFullAccess中，因此只要拥有全球加速的管理员权限，就可以为全球加速创建服务关联角色AliyunServiceRoleForGaAntiDdos。

-   添加自定义权限策略，并为RAM用户授权。自定义权限策略包含以下权限：

    ```
    {
        "Action": "ram:CreateServiceLinkedRole",
        "Resource": "*",
        "Effect": "Allow",
        "Condition": {
            "StringEquals": {
                "ram:ServiceName": "ddos.ga.aliyuncs.com"
            }
        }
    }
    ```

    详细信息，请参见[创建自定义策略](/cn.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)和[为RAM角色授权](/cn.zh-CN/角色管理/为RAM角色授权.md)。


## 创建服务关联角色AliyunServiceRoleForGaAntiDdos

您在为全球加速提升DDoS阈值时，系统会判断全球加速是否拥有服务关联角色AliyunServiceRoleForGaAntiDdos：

-   如果全球加速不存在服务关联角色AliyunServiceRoleForGaAntiDdos，系统会自动创建该服务关联角色，并为该服务关联角色添加名称为AliyunServiceRolePolicyForGaAntiDdos的权限策略，授予全球加速拥有访问DDoS高防实例的权限，策略内容如下：

    ```
    {
      "Version": "1",
      "Statement": [
        {
          "Effect": "Allow",
          "Resource": "*",
          "Action": [
            "yundun-ddoscoo:DescribeInstanceDetails"
          ]
        },
        {
          "Action": "ram:DeleteServiceLinkedRole",
          "Resource": "*",
          "Effect": "Allow",
          "Condition": {
            "StringEquals": {
              "ram:ServiceName": "ddos.ga.aliyuncs.com"
            }
          }
        }
      ]
    }
    ```

-   如果全球加速已经拥有服务关联角色AliyunServiceRoleForGaAntiDdos，则不会重复创建该服务关联角色。

## 删除服务关联角色AliyunServiceRoleForGaAntiDdos

系统不会自动删除全球加速的服务关联角色AliyunServiceRoleForGaAntiDdos，如果您要删除该服务关联角色，请先删除全球加速与DDoS高防实例的绑定关系。详细信息，请参见：

-   [重置DDoS阈值](/cn.zh-CN/用户指南/全球加速实例/重置DDoS阈值.md)
-   [删除服务关联角色](/cn.zh-CN/角色管理/服务关联角色.md)


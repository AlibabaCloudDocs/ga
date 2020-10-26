# Service-linked role

This topic describes the service-linked role AliyunServiceRoleForGaVpcEndpoint of Global Accelerator \(GA\). It also provides more information about how to create and delete the service-linked role.

## What is a service-linked role?

A service-linked role is a Resource Access Management \(RAM\) role. It can be assumed only by the linked service. You can use an Alibaba Cloud service to access other Alibaba Cloud services. This allows you to implement a specific feature. This requires that you first authorize the Alibaba Cloud service to access other services. Service-linked roles allow you to simplify the authorization and avoid the risks caused by user errors. For more information, see [Service linked roles](/intl.en-US/RAM Role Management/Service linked roles.md).

## Permissions required to create and delete the service-linked role

The following sample code shows the permission that is required for you to manually create or delete the service-linked role for GA. This permission is also required for the system to automatically to create the service-linked role for GA.

**Note:** The permission to create the service-linked role is included in the administrator permission policy AliyunGlobalAccelerationFullAccess. Therefore, if you are granted the administrator permissions, you can create the service-linked role for GA.

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

## Create the service-linked role

You can set the endpoint type to Elastic Compute Service \(ECS\) or Server Load Balancer \(SLB\). In this case, if the service-linked role AliyunServiceRoleForGaVpcEndpoint does not exist, the system automatically creates the service-linked role. This service-linked role is associated with the permission policy AliyunServiceRolePolicyForGaVpcEndpoint. This way, GA is authorized to access other Alibaba Cloud resources. The following sample code shows the permission policy.

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

## Delete the service-linked role

Before you can delete the service-linked role AliyunServiceRoleForGaVpcEndpoint from GA, delete the endpoint group in which the endpoint type is set to ECS or SLB. For more information, see:

-   [Delete a listener](/intl.en-US/User Guide/Listeners/Delete a listener.md)
-   [Delete a service linked role](/intl.en-US/RAM Role Management/Service linked roles.md)


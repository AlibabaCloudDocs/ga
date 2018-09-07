# Manage shared-bandwidth instances {#concept_ezy_mhy_5db .concept}

A shared-bandwidth Global Acceleration instance provides the Internet bandwidth only and no public IP. You can add multiple Elastic IP Addresses \(EIPs\) to a shared-bandwidth instance and then bind these EIPs to the backend servers to be accelerated.

## Create Instance {#section_yn4_qhy_5db .section}

Before configuring acceleration services, you must create a Global Acceleration instances. By sharing the instance bandwidth, the shared-bandwidth instance help you save Internet cost. For more information, see [Step 1. Create a Global Acceleration instance](../../../../intl.en-US/Quick Start/Configure a dedicated-bandwidth Global Acceleration instance.md#section_scl_pxw_5db).

## Add an EIP {#section_cfb_jvy_5db .section}

No public IP is provided for shared-bandwidth instances. You must add an EIP to it to accelerate the Internet access. For more information, see [EN-US\_TP\_21106.md\#](intl.en-US/User Guide/Shared-bandwidth instances/Add an EIP.md#).

## Bind a backend service {#section_pyj_cly_5db .section}

After creating a shared-bandwidth instance and binding EIPs, you can bind the EIPs to the backend servers. Shared-bandwidth instances support adding SLB instances of the VPC network and ECS secondary ENI. Up to 50 EIPs can be added to a shared-bandwidth instance and each EIP can be bound to a backend service. For more information, see [Bind a backend service](intl.en-US/User Guide/Shared-bandwidth instances/Bind a backend service.md#).

## Add an instance name {#section_esj_lky_5db .section}

To add a name for the instance, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the left-side navigation pane, click **Global Acceleration**.
3.  Click **Shared Bandwidth** and find the target instance.
4.  Rest the pointer on the instance ID, and then click the displayed pencil icon.
5.  In the displayed dialog box, enter a name and then click **OK**.

    The name can contain 2-128 characters and must start with an English or Chinese character. It can contain numbers, underscores and hyphens.


## Add an instance description {#section_r5q_rky_5db .section}

To add a description for the instance, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the left-side navigation pane, click **Global Acceleration**.
3.  Click **Shared Bandwidth** and find the target instance.
4.  Rest the pointer on the description area, and then click the displayed pencil icon.
5.  In the displayed dialog box, enter a description and then click **OK**.

    The description can contain 2-256 characters, but cannot start with `http://` or `https://`.


## Unbind a backend service {#section_q4b_vky_5db .section}

You can unbind a backend service from the EIP when the Internet acceleration is no longer required. To unbind a backend service, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the left-side navigation pane, click **Global Acceleration**.
3.  Click **Shared Bandwidth** and find the target instance.
4.  Click **Unbind** in the **Actions** column.
5.  In the displayed dialog, click **OK**.

## Modify the bandwidth {#section_itk_lky_5db .section}

You can change the bandwidth of an instance any time and the change takes effect immediately. To modify the bandwidth, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the left-side navigation pane, click **Global Acceleration**.
3.  Click **Shared Bandwidth** and find the target instance.
4.  Click **Change Bandwidth** in the **Bandwidth** column of the target Global Acceleration instance. Then, select a new bandwidth based on your needs and complete the payment.

## Renew an instance {#section_yqq_dmy_k2b .section}

You can renew a Global Acceleration instance before it expires to avoid the impact of service interruption on your service. To renew an instance, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the left-side navigation pane, click **Global Acceleration**.
3.  Click **Shared Bandwidth** and find the target instance.
4.  Click **Renew** in the **Actions** column.
5.  Select a new time to purchase and complete the payment.


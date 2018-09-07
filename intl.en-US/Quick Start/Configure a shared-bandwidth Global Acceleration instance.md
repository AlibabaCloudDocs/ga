# Configure a shared-bandwidth Global Acceleration instance {#concept_qgs_tww_5db .concept}

This tutorial explains how to configure a shared-bandwidth Global Acceleration instance to accelerate services deployed on ECS instances of the VPC network. A shared-bandwidth Global Acceleration instance contains only an Internet bandwidth and no public IP. It accelerates the backend services through the added EIPs.

## Scenario {#section_udw_2xw_5db .section}

The ECS instance where the application is deployed is located in China \(Beijing\) and is bound with an EIP to provide external service. Service timeout usually occurs when users in the US \(Silicon Valley\) region access the service. Therefore, the quality and speed of their Internet access needs to be improved.

## Configuration overview {#section_f5h_jxw_5db .section}

To meet the demand for acceleration, a Global Acceleration instance with the following configurations must be created:

-   Instance type: shared bandwidth

    For more information, see [Instance types](../../../../intl.en-US/User Guide/Instance types.md#).

-   Accelerated area: North America

    The area where the Internet access is to be accelerated. The US \(Silicon Valley\) region belongs to the accelerated area of North America.

-   Region: US \(Silicon Valley\)

    The region of the Global Acceleration instance to accelerate the Internet access.

-   Service area: Mainland China

    The region where the backend service is deployed. Beijing belongs to the service area of Mainland China.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12632/15363110381372_en-US.png)


## Prerequisites {#section_rzl_nxw_5db .section}

-   -   An application is deployed on the ECS instance and a secondary ENI is created for the ECS instance.


## Step 1. Create a Global Acceleration instance {#section_scl_pxw_5db .section}

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com) .
2.  In the left-side navigation pane, click **Global Acceleration**.
3.  Click **Shared Bandwidth**, and then click **Create Instance**.
4.  Configure the Global Acceleration instance according to the following information, and then click **Buy Now**.

    |Configuration|Description|
    |:------------|:----------|
    |**Bandwidth Type**| Select the bandwidth type:

    -   **Dedicated Bandwidth**: A dedicated-bandwidth Global Acceleration instance provides a dedicated Internet bandwidth and a public IP for accelerating the Internet access for the added backend service.

The bandwidth of a dedicated-bandwidth Global Acceleration instance is exclusively used by the instance itself.

    -   **Shared Bandwidth**: A shared-bandwidth Global Acceleration instance only contains an Internet bandwidth and no public IP.

You can add one or more Elastic IP Addresses \(EIPs\) to a shared-bandwidth instance. After adding, the EIPs can be used to accelerate the Internet access for the backend services. Additionally, the EIPs share the bandwidth of the shared-bandwidth instance and the Internet cost is reduced.

The regions of the backend services that the EIPs are bound to must be the same.

 In this tutorial, select **Shared Bandwidth**. For more information, see [Instance types](../../../../intl.en-US/User Guide/Instance types.md#).

 |
    |**Accelerated Area**| Select the accelerated area of the Global Acceleration instance.

 An accelerated area is a collection of regions and each accelerated area contains one or more regions. The Global Acceleration instance can accelerate the Internet access for the backend service of users in the selected accelerated area.

 In this tutorial, select **North America**.

 |
    |**Region**| Select the region to which the Global Acceleration instance belongs. The instance must be located in the selected accelerated area.

 In this tutorial, select **US \(Silicon Valley\)**.

 **Note:** The Global Acceleration instance and the backend service cannot be in the same region.

 |
    |**Service area**| Select the area to which the accelerated service belongs.

 An accelerated area is a collection of Alibaba Cloud regions. Each accelerated area contains one or more regions. You can bind ECS instances or SLB instances of the VPC network in the selected service area to accelerate the deployed backend services.

 In this tutorial, select **Mainland China**.

 |
    |**Billing method**|Global Acceleration is billed by bandwidth.|
    |**Bandwidth peak**| Select the peak bandwidth of the Global Acceleration instance. After an instance has been created, you can adjust the peak bandwidth at any time according to your business needs.

 In this tutorial, select **10 Mbps**.

 |
    |**Purchase Quantity**| Select the quantity that you want to purchase.

 In this tutorial, select **1**.

 |
    |**Subscription Duration**| Select the purchase duration.

 In this tutorial, select **1**.

 |


## Step 2. Add EIPs {#section_nk1_2wx_5db .section}

After creating a shared-bandwidth instance, you must add at least one EIP to accelerate the Internet access.  After the EIP is added to the instance:

-   The added EIP shares the bandwidth of the Global Acceleration instance and the original bandwidth of the EIP is disabled.
-   The original billing of the EIP is also disabled. The EIP becomes a public IP and no additional traffic or bandwidth fee is charged.

To add an EIP, follow these steps:

1.  On the Global Acceleration page, click **Shared Bandwidth**.
2.  Click **Add IP Address** in the **Actions** column of the target instance.
3.  On the Add IP Address page, complete these steps:
    -   If there is no unused EIP in your account, click **Buy EIP and add to Global Acceleration**, enter the number of EIPs to buy and click **OK**.

        After the EIP is created, it is automatically added to the shared-bandwidth instance.

    -   If there is an unused EIP under your account, click **Select from EIP list**, select the EIP to bind and click **OK**.

        **Note:** The EIP instance and the Global Acceleration instance must be in the same region.


## Step 3. Bind backend services {#section_ojb_pbx_5db .section}

A shared-bandwidth instance accelerates Internet access through EIPs. After adding an EIP, you need to bind the EIP to the backend service that you want to accelerate. Up to 50 EIPs can be bound to a shared-bandwidth Global Acceleration instance.

Follow these steps to bind a backend service:

1.  On the Global Acceleration page, find the target instance and click the added EIP.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12644/15363110381430_en-US.png)

2.  On the Global Acceleration IP Addresses page, click the **Bind** option of the target EIP.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12644/15363110386956_en-US.png)

3.  In the displayed dialog box, configure the backend service according to the following information:
    -   **Region**: Select the region of the backend service. In this tutorial, select **China North 2**.
    -   **Instance Type**: Select the type of the instance. Shared-bandwidth Global Acceleration instances support binding ECS ENIs and SLB instances of the VPC network. In this tutorial, select **Secondary ENI**.
    -   **Bind Instance**: Select the instance to bind. In this tutorial, select the created ECS ENI.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12644/15363110381447_en-US.png)


## Step 4. Verification {#section_hqp_ndx_5db .section}

After the backend service is bound, you can ping the EIP of the Global Acceleration instance to verify if the configuration takes effect. You can also ping the public IP of the backend server and the EIP of the Global Acceleration instance respectively to compare the latency and packet loss.


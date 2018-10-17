# Configure a dedicated-bandwidth Global Acceleration instance {#concept_qgs_tww_5db .concept}

This tutorial explains how to configure a dedicated-bandwidth Global Acceleration instance to accelerate services deployed on an ECS instance of a VPC network. A dedicated-bandwidth Global Acceleration instance provides a dedicated Internet bandwidth and a public IP for accelerating the Internet access for the added backend service.

## Scenario {#section_udw_2xw_5db .section}

The ECS instance where the application is deployed is located in China \(Beijing\) and is bound to an EIP to provide external service. Service timeout usually occurs when users in the US \(Silicon Valley\) region access the service. Therefore, the quality and speed of their Internet access needs to be improved.

## Configuration overview {#section_f5h_jxw_5db .section}

To meet the demand for acceleration, a Global Acceleration instance with the following configurations must be created:

-   Instance type: dedicated bandwidth

    For more information, see [Instance types](../../../../reseller.en-US/User Guide/Instance types.md#).

-   Accelerated area: North America

    The area where the Internet access is to be accelerated. The US \(Silicon Valley\) region belongs to the accelerated area of North America.

-   Region: US \(Silicon Valley\)

    The region of the Global Acceleration instance, which must be one region within the accelerated area.

-   Service area: Mainland China

    The region where the backend service is deployed. Beijing belongs to the service area of Mainland China.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12632/15397454511372_en-US.png)


## Step 1. Create a Global Acceleration instance {#section_scl_pxw_5db .section}

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc) .
2.  In the left-side navigation pane, click **Global Acceleration**.
3.  Click **Dedicated Bandwidth**, and then click **Create Instance**.
4.  Configure the Global Acceleration instance according to the following information, and then click **Buy Now**.

    |Configuration|Description|
    |:------------|:----------|
    |**Bandwidth Type**| Select the bandwidth type:

    -   **Dedicated Bandwidth**: A dedicated-bandwidth Global Acceleration instance provides a dedicated Internet bandwidth and a public IP for accelerating the Internet access for the added backend service.

The bandwidth of a dedicated-bandwidth Global Acceleration instance is exclusively used by the instance itself.

    -   **Shared Bandwidth**: A shared-bandwidth Global Acceleration instance only contains an Internet bandwidth and no public IP.

You can add one or more Elastic IP Addresses \(EIPs\) to a shared-bandwidth instance. After adding, the EIPs can be used to accelerate the Internet access for the backend services. Additionally, the EIPs share the bandwidth of the shared-bandwidth instance and the Internet cost is reduced.

The regions of the backend services that the EIPs are bound to must be the same.

 In this tutorial, select **Dedicated Bandwidth**. For more information, see [Instance types](../../../../reseller.en-US/User Guide/Instance types.md#).

 |
    |**Accelerated Area**| Select the accelerated area of the Global Acceleration instance.

 An accelerated area is a collection of regions and each accelerated area contains one or more regions. The Global Acceleration instance can accelerate the Internet access for the backend service of users in the selected accelerated area.

 In this tutorial, select **North America**.

 |
    |**Region**| Select the region to which the Global Acceleration instance belongs. The instance must be located in the selected accelerated area.

 In this tutorial, select **US \(Silicon Valley\)**.

 **Note:** The Global Acceleration instance and the backend service cannot be in the same region.

 |
    |**Service Area**| Select the area to which the accelerated service belongs.

 An accelerated area is a collection of Alibaba Cloud regions. Each accelerated area contains one or more regions. You can bind ECS instances or SLB instances of the VPC network in the selected service area to accelerate the deployed backend services.

 In this tutorial, select **Mainland China**.

 |
    |**Billing Method**|Global Acceleration is billed by bandwidth.|
    |**Bandwidth Peak**| Select the peak bandwidth of the Global Acceleration instance. After an instance has been created, you can adjust the peak bandwidth at any time according to your business needs.

 In this tutorial, select **10 Mbps**.

 |
    |**Purchase Quantity**| Select the quantity that you want to purchase.

 In this tutorial, select **1**.

 |
    |**Subscription Duration**| Select the purchase duration.

 In this tutorial, select **1**.

 |


## Step 2. Bind a backend service {#section_ojb_pbx_5db .section}

After a dedicated-bandwidth instance is created, you need to bind the backend service to be accelerated to the dedicated-bandwidth instance. Follow these steps to bind a backend service:

1.  On the Global Acceleration page, click **Dedicated Bandwidth**.
2.  Find the target instance and click **Bind Instance**.
3.  On the Backend Service Instance page, configure the backend service and click **OK**.
    -   **Backend Service Region**: Select the region of the backend service.  The backend service region must belong to the selected service area.

        In this tutorial, select **China North 2 \(Beijing\)**.

    -   **Instance Type**: Select the type of the instance where the backend service is deployed. Currently, Global Acceleration supports accelerating services deployed on ECS instances and SLB instances of the VPC network.

        In this tutorial, select **ECS Instance**.

    -   **Bind Instance**: Select the instance where the backend service to be accelerated is deployed.

        In this tutorial, the ECS instance where the external service is deployed is selected.


When the status of the Global Acceleration instance changes to **Allocated**, the binding is successful. After the instance is successfully bound, the system automatically allocates a backend service address to the backend server.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12632/15397454511391_en-US.png)

## Step 3. Activate the backend service {#section_e2b_xcx_5db .section}

After the backend service is bound, you need to add a NIC sub interface to the bound ECS instance. The IP address of the sub interface is the backend service address allocated by the system. After the backend service is bound to the Global Acceleration instance, the acceleration link is always active as long as the sub interface in the backend server is correctly configured.

**Note:** Activation is required only when the backend service is an ECS instance.

This tutorial takes the Linux system as an example:

1.  On the Global Acceleration page, find the target instance and view the backend service address.

    You can also click **Service Activation** to view the backend service address.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12632/15397454511392_en-US.png)

2.  Run the following command to open the NIC configuration file.

    ```
    sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0:1
    ```

3.  Add the following information in the configuration file.

    ```
    DEVICE=eth0:1
     IPADDR=172.xx.xx. 135
     NETMASK=255.255.255.255
     ONBOOT=yes
    ```

4.  Run the following command to make the configuration take effect.

    ```
    ifup eth0:1
    ```


## Step 4. Verification {#section_hqp_ndx_5db .section}

After the backend service is bound, you can ping the EIP of the Global Acceleration instance to verify if the configuration takes effect. You can also ping the public IP of the backend server and the EIP of the Global Acceleration instance respectively to compare the latency and packet loss.


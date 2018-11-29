# Bind a backend service {#task_pd2_2my_5db .task}

You can bind an ECS instance or an SLB instance of the VPC network to a dedicated-bandwidth instance to accelerate the Internet access deployed on the ECS instance or SLB instance.

Create a dedicated-bandwidth instance.

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc). 
2.  In the left-side navigation pane, click **Global Acceleration** and then click the **Dedicated Bandwidth** tab. 
3.  Select a region, find the target instance and click **Bind Instance**. 
4.  Configure the backend service as follows and then click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    |**Backend Service Region**|Select the region of the backend service.The region of the backend service must be located in the selected service area, but cannot be the same as that of the Global Acceleration instance.

|
    |**Instance Type**| Select the cloud resource where the backend service that you want to accelerate is deployed:

    -   **ECS Instance**: Accelerate the service deployed on an ECS instance of the VPC network.

**Note:** For ECS instances, you must activate the backend service after binding. For more information, see [Activate the ECS backend service](reseller.en-US/User Guide/Dedicated-bandwidth instances/Activate the ECS backend service.md#).

    -   **SLB Instance**: Accelerate the backend service added to an SLB instance of the VPC network.
 **Note:** After binding a backend server to a Global Acceleration instance, the backend server can be accessed from the Internet. Make sure that you have configured corresponding security rules for the ECS instance, or have configured access control policies for the SLB instance.

 |
    |**Bind Instance**| Select the instance you want to bind.

 |



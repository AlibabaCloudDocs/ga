# Bind a backend service {#task_pd2_2my_5db .task}

You can bind the EIP that is added to a shared-bandwidth instance to a secondary Elastic Network Interface \(ENI\) of an ECS instance or an SLB instance of the VPC network to accelerate the Internet access deployed on the ECS instance or SLB instance.

A shared-bandwidth Global Acceleration instance is created and an EIP is added to the instance.

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com). 
2.  In the left-side navigation pane, click **Global Acceleration** and then click **Shared Bandwidth**. 
3.  Find the target instance and click the added IP address. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12637/15363090859668_en-US.png)

4.  On the Global Acceleration IP Addresses page, click the **Bind Instance** option of the target EIP. 
5.  Configure the backend service as follows and then click **OK**. 

    |Configuration|Description |
    |:------------|:-----------|
    |**Region**|Select the region of the backend service.The region of the backend service must be located in the selected service area, but cannot be the same as that of the Global Acceleration instance.

|
    |**Instance Type**| Select the cloud resource that the backend service to be accelerated is deployed:

    -   **Secondary ENI**: Accelerate the service deployed on the ECS instance bound to the selected secondary ENI.

**Note:** Currently, only ECS secondary ENI is supported.

    -   **SLB Instance**: Accelerate the backend service added to the selected SLB instance of the VPC network.
 **Note:** After binding a backend server to a Global Acceleration instance, the backend server can be accessed from the Internet. Make sure that you have configured corresponding security rules for the ECS instance, or have configured access control policies for the SLB instance.

 |
    |**Bind Instance**| Select the instance you want to bind.

 |



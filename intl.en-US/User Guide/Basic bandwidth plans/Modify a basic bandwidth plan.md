# Modify a basic bandwidth plan

You can modify the bandwidth type and maximum bandwidth of a basic bandwidth plan. The modification immediately takes effect.

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the Global Accelerator \(GA\) instance that you want to manage, and click the instance ID.

3.  On the page that appears, click the **Bandwidth Manage** tab.

4.  In the **Basic Bandwidth Package** section, find the basic bandwidth plan that you want to modify, and click **Change Specification** in the **Bandwidth** column.

5.  On the **Upgrade/Downgrade** page, modify the bandwidth type and maximum bandwidth of the basic bandwidth plan. Then, read the Global Accelerator\_Basic Bandwidth Plan \(Subscription\)Terms of Service, select the check box, click **Buy Now**, and then pay for the order.

    **Note:** The type of the bandwidth plan can be changed from only Basic to Enhanced, but cannot be changed from Enhanced or Premium to the other types.

    Basic bandwidth plans support the following types of bandwidth: basic, enhanced, and premium. The following table shows that the acceleration type, acceleration backend service, and acceleration scope of a basic bandwidth plan can vary based on the bandwidth type.

    |Bandwidth type|Workload type|Accelerated object|Acceleration scope|
    |--------------|-------------|------------------|------------------|
    |Basic bandwidth|Applications that are deployed on Alibaba Cloud|    -   Elastic Compute Service \(ECS\)
    -   Server Load Balancer \(SLB\)
    -   Alibaba Cloud public IP address

**Note:** If ECS instances and SLB instances run in classic networks, both types of instances are not supported.

|By default, networking within mainland China is accelerated.You can also purchase a cross-border bandwidth plan. This allows you to optimize the acceleration of networking between mainland China and other areas.|
    |Enhanced bandwidth|    -   Applications that are deployed on Alibaba Cloud
    -   Applications that are not deployed on Alibaba Cloud
|    -   ECS
    -   SLB
    -   Alibaba Cloud public IP address
    -   Custom IP address
    -   Custom domain name
|By default, networking within mainland China is accelerated.You can also purchase a cross-border bandwidth plan. This allows you to optimize the acceleration of networking between mainland China and other areas.|
    |Premium bandwidth|    -   Applications that are deployed on Alibaba Cloud
    -   Applications that are not deployed on Alibaba Cloud
|    -   ECS
    -   SLB
    -   Alibaba Cloud public IP address
    -   Custom IP address
    -   Custom domain name
|By default, network connections are accelerated on a global scale. Network traffic transmitted from mainland China to areas outside China is accelerated in the China \(Hong Kong\) region.If you also purchase a cross-border bandwidth plan, the acceleration of network connections between mainland China and areas outside China are reinforced.|

    **Note:** You can specify ECS or SLB as the backend service type only when your account is included in the whitelist of GA. If you want to specify ECS or SLB as the backend service type, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).


**Related topics**  


[UpdateBandwidthPackage](/intl.en-US/API reference/Bandwidth plans/UpdateBandwidthPackage.md)


# Modify a basic bandwidth plan

You can modify the maximum bandwidth of a basic bandwidth plan. The modification immediately takes effect.

Before you modify a basic bandwidth plan, take note of the following information:

-   You can only upgrade a basic bandwidth plan bandwidth. To downgrade a basic bandwidth plan, you must apply for this feature to be enabled on your account. To enable this feature, [submit a ticketsubmit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).
-   To downgrade a basic bandwidth plan, make sure that the total allocated bandwidth value across all acceleration regions is no greater than the maximum bandwidth value of the downgraded plan.
-   To upgrade or downgrade a basic bandwidth plan and a cross-border acceleration bandwidth plan in settings, take note of the sequence of bandwidth plans that you choose to modify:

    -   Upgrade: upgrade the cross-border acceleration bandwidth plan first and then the basic bandwidth plan.
    -   Downgrade: Downgrade the basic bandwidth plan first and then the cross-border acceleration bandwidth plan.
    For more information about how to modify a cross-region-acceleration bandwidth plan, see [Modify a cross-region acceleration bandwidth plan](/intl.en-US/User Guide/Cross-border acceleration bandwidth plans/Modify a cross-border acceleration bandwidth plan.md).

-   When you upgrade or downgrade a basic bandwidth plan, make sure that the maximum bandwidth value of the basic bandwidth plan is no greater than the maximum bandwidth value supported by your current Global Accelerator \(GA\) instance. For more information about GA instance specifications, see [Global Accelerator overview.](/intl.en-US/User Guide/Global Accelerator instances/Global Accelerator overview.md)

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the Global GA instance and click the instance ID.

3.  On the page that appears, click the **Bandwidth Manage** tab.

4.  In the **Basic Bandwidth Package** section, find the basic bandwidth plan that you want to modify and click **Change Specification** in the **Bandwidth** column.

5.  On the **Upgrade/Downgrade** page, modify the maximum bandwidth of the basic bandwidth plan, select **Global Accelerator\_Basic Bandwidth Plan \(Subscription\) Terms of Service**, and then click **Buy Now** to pay for the order.


**Related topics**  


[UpdateBandwidthPackage](/intl.en-US/API reference/Bandwidth plans/UpdateBandwidthPackage.md)


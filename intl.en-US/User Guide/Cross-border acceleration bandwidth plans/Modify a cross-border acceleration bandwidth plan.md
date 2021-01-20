# Modify a cross-border acceleration bandwidth plan

This topic describes how to modify the bandwidth of a cross-border acceleration bandwidth plan. The modification immediately takes effect.

-   You can only upgrade cross-border acceleration bandwidth plans. To downgrade a cross-border acceleration bandwidth plan, you must apply for this feature to be enabled on your account. To enable this feature, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).
-   To downgrade a cross-border acceleration bandwidth plan, make sure that the total allocated bandwidth value across all acceleration regions is no greater than the maximum bandwidth of the downgraded plan.
-   To upgrade or downgrade a basic bandwidth plan and a cross-border acceleration bandwidth plan in settings, take note of the sequence of bandwidth plans that you choose to modify:

    -   Upgrade: upgrade the cross-border acceleration bandwidth plan first and then the basic bandwidth plan.
    -   Downgrade: Downgrade the basic bandwidth plan first and then the cross-border acceleration bandwidth plan.
    For more information about how to upgrade and downgrade a basic bandwidth plan, see [Modify a basic bandwidth plan](/intl.en-US/User Guide/Basic bandwidth plans/Modify a basic bandwidth plan.md).

-   When you upgrade or downgrade a cross-border acceleration bandwidth plan, make sure that the maximum bandwidth value of the cross-border acceleration bandwidth plan is no greater than the maximum bandwidth value supported by your current Global Accelerator \(GA\) instance. For more information about GA instance types, see [Global Accelerator overview](/intl.en-US/User Guide/Global Accelerator instances/Global Accelerator overview.md).

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the GA instance and click the instance ID.

3.  On the page that appears, click the **Bandwidth Manage** tab.

4.  In the **Cross-region Bandwidth Package** section, find the bandwidth plan that you want to manage and click **Change Specification** in the **Bandwidth** column.

5.  On the **Upgrade/Downgrade** page, modify the bandwidth and select **Cross-Region Acceleration Bandwidth Package \(International Site\) Terms of Service**.

6.  Click **Buy Now** and pay for the order.


**Related topics**  


[UpdateBandwidthPackage](/intl.en-US/API reference/Bandwidth plans/UpdateBandwidthPackage.md)


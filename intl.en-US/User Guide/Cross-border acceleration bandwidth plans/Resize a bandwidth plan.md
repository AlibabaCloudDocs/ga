# Resize a bandwidth plan

This topic describes how to resize a bandwidth plan for cross-region connections. After you modify the bandwidth value, it immediately takes effect.

-   You can only upgrade a bandwidth plan for cross-region connections. Downgrades are not supported.
-   If you want to resize both a basic bandwidth plan and a bandwidth plan for cross-region connections, take note of the following rules:

    -   Upgrade: You must upgrade a bandwidth plan for cross-region connections before you upgrade a basic bandwidth plan.
    -   Downgrade: To downgrade a basic bandwidth plan, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).
    For more information about how to resize a basic bandwidth plan, see [resize a basic bandwidth plan](/intl.en-US/User Guide/Basic bandwidth plans/Modify a basic bandwidth plan.md).

-   When you upgrade a bandwidth plan for cross-region connections, make sure that the new bandwidth value is not greater than the maximum bandwidth value supported by the Global Accelerator \(GA\) instance. For more information about GA instance types, see [Global Accelerator overview](/intl.en-US/User Guide/Global Accelerator instances/Global Accelerator overview.md).

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the GA instance and click its ID.

3.  On the page that appears, click the **Bandwidth Manage** tab.

4.  In the **Cross-region Bandwidth Package** section, find the bandwidth plan that you want to manage and click **Change Specification** in the **Bandwidth** column.

5.  On the **Upgrade/Downgrade** page, resize the bandwidth and select **Cross-Region Acceleration Bandwidth Package \(International Site\) Terms of Service**.

6.  Click **Buy Now** and complete the payment.


**Related topics**  


[UpdateBandwidthPackage](/intl.en-US/API reference/Bandwidth plans/UpdateBandwidthPackage.md)


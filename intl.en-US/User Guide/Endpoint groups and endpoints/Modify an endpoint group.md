---
keyword: [modify the default endpoint group, modify a virtual endpoint group]
---

# Modify an endpoint group

After you add an endpoint group, you can modify it based on your business requirements.

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the Global Accelerator \(GA\) instance that you want to manage and click **Configure Listeners** in the **Actions** column.

3.  On the **Listeners** tab, find the listener and click the endpoint group ID in the **Default Endpoint Group ID/Name** column.

4.  On the **Endpoint Group** tab, you can modify the configurations of the default endpoint group or a virtual endpoint group.

    **Note:** You can configure and modify virtual endpoint groups for only HTTP and HTTPS listeners. For more information about virtual endpoint groups, see [Overview](/intl.en-US/User Guide/Endpoint groups and endpoints/Overview.md).

    -   Modify the default endpoint group
        1.  On the **Endpoint Group** tab, find the default endpoint group and click **Edit Point Group** in the **Actions** column.
        2.  On the **Configure Endpoint Group** page, modify the name and endpoints of the endpoint group, and click **Next**.

            For more information about configurations of the default endpoint group, see [Create an endpoint group](/intl.en-US/User Guide/Endpoint groups and endpoints/Configure an endpoint group.md).

        3.  On the **Confirm** page, review the configurations of the endpoint group.

            If you want to modify the configurations, click **Modify** in the corresponding section to return to the configurations page.

        4.  After you confirm the configurations, click **Submit**.
    -   Modify a virtual endpoint group
        1.  On the **Endpoint Group** tab, find the virtual endpoint group and click **Modify Endpoint Group** in the **Actions** column.
        2.  In the **Edit Virtual Endpoint Group** dialog box, modify the name and endpoints of the virtual endpoint group, and click **Save**.

            For more information about configurations of virtual endpoint groups, see [Create an endpoint group](/intl.en-US/User Guide/Endpoint groups and endpoints/Configure an endpoint group.md).


**Related topics**  


[UpdateListener](/intl.en-US/API reference/Listeners/UpdateListener.md)


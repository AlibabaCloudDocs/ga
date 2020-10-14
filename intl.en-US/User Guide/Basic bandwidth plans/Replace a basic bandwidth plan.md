# Replace a basic bandwidth plan

You can replace a basic bandwidth plan that is associated with a Global Accelerator \(GA\) instance. This allows you to use the basic bandwidth plan that meets your requirements. The GA instance continues to forward network traffic when you replace the basic bandwidth plan.

The required basic bandwidth plan is purchased. The bandwidth provided by the plan is not less than the total bandwidth that has been assigned to the specified acceleration area. For more information, see [Purchase a basic bandwidth plan](/intl.en-US/User Guide/Basic bandwidth plans/Purchase a basic bandwidth plan.md).

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the GA instance that you want to manage and click the instance ID.

3.  On the page that appears, click the **Bandwidth Manage** tab.

4.  In the **Basic Bandwidth Package** section, find the plan that you want to replace and click **Replace** in the **Actions** column of the plan.

5.  In the **Replace Basic Bandwidth Plan** dialog box, select the basic bandwidth plan that you want to use and click **OK**.

    Only the basic bandwidth plan that is in the **Active** state can be selected.


After you replace the original basic bandwidth plan with the required bandwidth plan, the original one is disassociated from the GA instance and the required one is associated with the GA instance.

**Related topics**  


[t1960688.md\#]()


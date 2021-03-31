# Set the weight of an endpoint

Global Accelerator \(GA\) allows you to set the weight of an endpoint in the endpoint group. The weight determines the proportion of requests that GA directs to the endpoint.

GA calculates the sum of the weights of each endpoint in an endpoint group, and then distributes the network traffic to each endpoint based on the proportion of the individual weight to the total weight.

For example, if you want to distribute 1/3 of the network traffic to Endpoint 1 and 2/3 of the network traffic to Endpoint 2, you can set the weight of Endpoint 1 to 1 and that of Endpoint 2 to 2. To disable GA from distributing network traffic to an endpoint, you can set the weight of the endpoint to 0.

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the GA instance and click **Configure Listeners** in the **Actions** column.

3.  On the **Listeners** tab, find the listener and click **Edit Endpoint Group** in the **Actions** column.

4.  On the **Configure Endpoint Group** page, find the endpoint, set the weight, and then click **Next**.

    Valid values for the weight: 0 to 255.

5.  On the **Confirm** page, review the configurations.

6.  After you confirm the configurations, click **Submit**.

    After you submit the configurations, the system requires some time to modify the configurations. During this process, the state of the listener is **Configuring**.


**Related topics**  


[UpdateEndpointGroup](/intl.en-US/API reference/Endpoint groups/UpdateEndpointGroup.md)


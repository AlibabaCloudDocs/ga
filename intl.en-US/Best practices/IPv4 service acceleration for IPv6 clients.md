# IPv4 service acceleration for IPv6 clients

This topic describes how to use Global Accelerator \(GA\) to accelerate the delivery of IPv4 services for IPv6 clients. This improves user experience.

Before you start, make sure that the following requirements are met:

-   An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).
-   IPv6 clients can connect to GA instances deployed in only the China \(Beijing\), China \(Hangzhou\), China \(Shanghai\), China \(Shenzhen\), and China \(Hong Kong\) regions.

The headquarters of a company is located in US \(Silicon Valley\). An on-premises server providing IPv4 services is deployed in the headquarters. The employees of the company in China \(Hong Kong\) use IPv6 clients only. As the company develops, the employees in China \(Hong Kong\) need to use IPv6 clients to access the IPv4 services deployed in US \(Silicon Valley\). The employees also want to reduce issues such as network latency, network jitter, and packet loss caused by unstable cross-border Internet connections.

GA redirects requests from an IPv6 client in the China \(Hong Kong\) region to the nearest access point through an accelerated IP address. The access point receives the requests from the client, and forwards the requests to the Alibaba Cloud global network. GA then converts the IPv6 requests to IPv4 requests, automatically selects routes, and forwards the requests to the endpoint, which is the server in US \(Silicon Valley\).

![Scenario](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3707827951/p132310.png)

## Procedure

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3707827951/p132320.png)

## Step 1: Enter the required information about the web service that you want to accelerate

You can enter the required information about the accelerated web service in the GA console. The system provides the recommended GA instance and basic bandwidth plan to meet your business requirements.

To enter the required information about the web service that you want to accelerate, perform the following steps:

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  In the upper-right corner of the **Instances** page, click **Purchase Guide**.

    **Note:** Skip the step if it is your first time using GA.

    ![Purchase Guide](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2367958951/p103054.png)

3.  In the **Enter the required information to generate a list of recommended services** section, enter the required information.

    -   **Acceleration Region**: Select the region that requires acceleration. **China \(Hong Kong\)** is selected in this example.
    -   **Service Region**: Select the region where the origin servers are located. **US \(Silicon Valley\)** is selected in this example.
    -   **ICP Filing**: If you need to accelerate a web service, specify whether you have requested an Internet Content Provider \(ICP\) number for the domain name of the web service. If the service is not a web service, select **No**. **No** is selected in this example.

        **Note:** All websites must obtain an ICP number before they are permitted to provide services to users in mainland China. For more information, see [What is an ICP filing?]().

    -   **Server Area**: Specify whether the backend servers are deployed on Alibaba Cloud. **Off Alibaba Cloud** is selected in this example.
    -   **Peak Bandwidth Range**: Enter the bandwidth required during peak hours. Unit: Mbit/s. The value is set to **10** in this example.
    -   **Maximum Concurrent Connections**: Specify the maximum number of concurrent connections that the GA instance supports. When the number of existing concurrent connections reaches the upper limit, new connection requests are dropped. The value is set to **5 thousand** in this example.
4.  Click **Generate Service List**.

    After a service list is generated, you can view the list of recommended services.

    ![Recommended service list](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3707827951/p103000.png)


## Step 2: Purchase a GA service bundle

You can purchase a GA service bundle that includes the recommended GA instance and basic bandwidth plan.

To purchase a service bundle, perform the following steps:

1.  Click **Generate Service List**.

    ![Generate Service List](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2367958951/p103007.png)

2.  On the buy page, set the following parameters:

    -   **Term**: Select the subscription duration.

        **Note:** The subscription duration applies to the services in the recommended service bundle. For example, if you set Term to 1 Year,the subscription duration of the specified GA instance, basic bandwidth plan, and cross-border bandwidth plan is set to one year.

    -   **Specification**: Select a specification for the GA instance that you want to create. **Small I \(Specification Unit\)** is selected in this example.

        GA supports the following types of instance specifications: Small I, Small II, Small III, Medium I, Medium II, and Medium III. The acceleration performance can vary based on the instance specification.

        |Instance specification|Number of acceleration regions|Peak bandwidth|Maximum number of concurrent connections|
        |----------------------|------------------------------|--------------|----------------------------------------|
        |Small I|1|20 Mbit/s|5,000|
        |Small II|2|40 Mbit/s|10,000|
        |Small III|3|60 Mbit/s|15,000|
        |Medium I|5|100 Mbit/s|25,000|
        |Medium II|8|160 Mbit/s|40,000|
        |Medium III|10|200 Mbit/s|50,000|

    -   **Bandwidth Type**: Select a bandwidth type for the basic bandwidth plan. **Premium** is selected in this example.

        Basic bandwidth plans support the following types of bandwidth: basic, enhanced, and premium. The following table shows that the acceleration type, acceleration backend service, and acceleration scope of a basic bandwidth plan can vary based on the bandwidth type.

        |Bandwidth type|Workload type|Accelerated object|Acceleration scope|
        |--------------|-------------|------------------|------------------|
        |Basic bandwidth|Applications that are deployed on Alibaba Cloud|        -   Elastic Compute Service \(ECS\)
        -   Server Load Balancer \(SLB\)
        -   Alibaba Cloud public IP address

**Note:** If ECS instances and SLB instances run in classic networks, both types of instances are not supported.

|By default, networking within mainland China is accelerated.You can also purchase a cross-border bandwidth plan. This allows you to optimize the acceleration of networking between mainland China and other areas.|
        |Enhanced bandwidth|        -   Applications that are deployed on Alibaba Cloud
        -   Applications that are not deployed on Alibaba Cloud
|        -   ECS
        -   SLB
        -   Alibaba Cloud public IP address
        -   Custom IP address
        -   Custom domain name
|By default, networking within mainland China is accelerated.You can also purchase a cross-border bandwidth plan. This allows you to optimize the acceleration of networking between mainland China and other areas.|
        |Premium bandwidth|        -   Applications that are deployed on Alibaba Cloud
        -   Applications that are not deployed on Alibaba Cloud
|        -   ECS
        -   SLB
        -   Alibaba Cloud public IP address
        -   Custom IP address
        -   Custom domain name
|By default, network connections are accelerated on a global scale. Network traffic transmitted from mainland China to areas outside China is accelerated in the China \(Hong Kong\) region.If you also purchase a cross-border bandwidth plan, the acceleration of network connections between mainland China and areas outside China are reinforced.|

        **Note:**

        -   You can specify an ECS or SLB instance as an endpoint only if your Alibaba Cloud account is included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).
        -   GA Instance Endpoint Group IP is for end users only and is not shared with other users.
    -   **Peak Bandwidth**: Specify the maximum bandwidth of the basic bandwidth plan. The value is set to **10** Mbit/s in this example.
3.  Click **Buy Now** and complete the payment.

4.  After you complete the payment, associate the basic bandwidth plan with the GA instance. For more information, see [Bind a basic bandwidth plan](/intl.en-US/User Guide/Basic bandwidth plans/Bind a basic bandwidth plan.md).


## Step 3: Add an acceleration area

After you purchase a GA instance, you can add one or more acceleration areas where users are located, and then allocate bandwidth to these areas.

To add an acceleration area, follow these steps:

1.  On the **Instances** page, find the created GA instance and click the instance ID.

2.  On the page that appears, click the **Acceleration Areas** tab. Then, click **Add Acceleration Area**.

3.  In the **Add Acceleration Area** dialog box, set the following parameters, and click **OK**.

    -   **Acceleration Area**: Select the area that requires acceleration. Select **Asia Pacific** in this example.
    -   **Regions**: Select the region where users are located. Select **China \(Hong Kong\)** in this example.
    -   **Bandwidth**: Specify the amount of bandwidth to be allocated to the region. Enter **10** in this example. Unit: Mbit/s.
    -   **Internet Protocol**: Select the IP protocol used by the GA instance. Select **IPv6** in this example.

After an acceleration area is added, GA assigns an IPv6 address to the acceleration region as an accelerated IP address to accelerate connections.

![Accelerated IP address](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3707827951/p132262.png)

## Step 4: Add a listener

Listeners are used to monitor connection requests from clients. GA monitors connection requests received on the specified listener ports and forwards the requests to endpoints through the specified protocol.

To add a listener to the GA instance, perform the following steps:

1.  On the instance details page, click the **Listeners** tab and then click **Add Listener**.

2.  On the **Configure Listener & Protocol** page, set the following parameters for the listener:

    -   **Listener Name**: Enter a name for the listener. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). The name must start with a letter.
    -   **Protocol**: Select a protocol for the listener. **TCP** is selected in this example.
    -   **Port Number**: Enter the number of the listener port that is used to receive requests and forward requests to endpoints. Valid values: 1 to 65499. The value is set to **80** in this example.
    -   **Client Affinity**: Select whether to enable client affinity. If client affinity is enabled, requests from the same client IP address are forwarded to the same endpoint when clients access stateful applications. **Source IP Address** is selected in this example.
    ![Listener](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5963284161/p84395.png)

3.  Click **Next** to configure an endpoint group.


## Step 5: Configure an endpoint group

Each listener is associated with an endpoint group. You can associate an endpoint group with a listener by specifying the regions to which you want to distribute network traffic. After you associate an endpoint group with a listener, network traffic is distributed to the optimal endpoint in the associated endpoint group.

To configure an endpoint group, follow these steps:

1.  In the **Configure Endpoint Group** wizard, configure the endpoint group based on the following information.

    -   **Endpoint Group Name**: Enter a name for the endpoint group. The name must be 2 to 128 characters in length and can contain letters, Chinese characters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter or a Chinese character.
    -   **Region**: Select the region to which the endpoint group belongs. The region specifies where the origin servers are located. Select **US \(Silicon Valley\)** in this example.
    -   **Backend Service**: Specify whether the origin servers are deployed on Alibaba Cloud. Select **Off Alibaba Cloud** in this example.
    -   **Reserve Client IP**: Specify whether to enable the feature of reserving client IP addresses. After this feature is enabled, the origin servers can obtain client IP addresses. Disable the feature in this topic.

        **Note:** The feature of reserving client IP addresses is available only to users who are added to the whitelist. If you are not included in the whitelist and you want to use the feature, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

    -   **Endpoint Configuration**: Configure endpoints.
        -   **Backend Service Type**: Select **Custom IP Address** from the drop-down list.
        -   **Backend Service**: Enter the IP address of the origin server to be accelerated.
        -   **Weight**: Specify a weight for the endpoint. Valid values: 0 to 255. GA distributes network traffic to endpoints based on the predefined weights of the endpoints.

            **Note:** If you set the weight of an endpoint to 0, GA stops distributing network traffic to the endpoint. Proceed with caution.

    ![Endpoint groups](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3707827951/p132269.png)

2.  Click **Next** to check the configurations. After you confirm the configurations, click **Next**.


## Step 6: Verify the settings

To test the acceleration performance, follow these steps:

1.  Open the command-line interface of an IPv6 client in the acceleration region. An IPv6 client in China \(Hong Kong\) is used in this example.

2.  Run the following command to test whether the IPv6 client can access IPv4 services.

    `curl http://[<the accelerated IP address assigned by GA>]`

    The test result indicates that the IPv6 client can access the IPv4 services deployed in the US \(Silicon Valley\) region.

    ![Access IPv4 services](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4707827951/p132270.png)

3.  Run the following command to check the latency of data transmission.

    `curl -o /dev/null -s -w "time_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" "http[s]://<the accelerated IP address assigned by GA>"`

    where:

    -   time\_connect: the period of time that it takes to establish a TCP connection.
    -   time\_starttransfer: the period of time that it takes for the backend server to send the first byte after the client sends a request.
    -   time\_total: the period of time that it takes for the backend server to respond to the session after the client sends a request.
    The test result indicates that GA reduces network latency when the IPv6 client accesses the IPv4 services deployed in the US \(Silicon Valley\) region.

    ![Before Global Accelerator is enabled](../images/p76785.png "Before Global Accelerator is enabled")

    ![After Global Accelerator is enabled](../images/p132272.png "After Global Accelerator is enabled")

    **Note:** The actual performance of the acceleration service provided by GA for accessing IPv4 services from IPv6 clients varies based on your workload.



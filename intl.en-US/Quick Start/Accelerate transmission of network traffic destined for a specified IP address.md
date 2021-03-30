# Accelerate transmission of network traffic destined for a specified IP address

This topic describes how to use Global Accelerator \(GA\) to accelerate connections to backend servers that have specific IP addresses.

The following scenario is used as an example. A company has built two on-premises backend servers including Server 1 and Server 2 in the US \(Silicon Valley\) region and deployed enterprise applications on the servers. Server 1 processes up to 20% of the total workloads. Server 2 processes up to 80% of the total workloads. Unstable network performance may cause issues such as latency, network jitter, and packet loss. This occurs when users from the office in the China \(Hong Kong\) region connect to the enterprise applications deployed in the US \(Silicon Valley\) region over the Internet.

To accelerate connections to the backend servers, you can create a GA instance that provides an access point in China \(Hong Kong\). When users in the China \(Hong Kong\) region send requests to the servers, the access point in the China \(Hong Kong\) region receives the requests and forwards the requests to the endpoints in the US \(Silicon Valley\) region through intelligent routing. The system uses the endpoints to distribute 20% of the requests to Server 1 and 80% of the requests to Server 2.

![Accelerate transmission of network traffic destined for a specified IP address](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9298035951/p102978.png)

## Procedure

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9298035951/p103024.png)

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

        **Note:** You can specify ECS or SLB as the backend service type only when your account is included in the whitelist of GA. If you want to specify ECS or SLB as the backend service type, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

    -   **Peak Bandwidth**: Specify the maximum bandwidth of the basic bandwidth plan. The value is set to **10** Mbit/s in this example.
3.  Click **Buy Now** and complete the payment.

4.  After you complete the payment, associate the basic bandwidth plan with the GA instance. For more information, see [Bind a basic bandwidth plan](/intl.en-US/User Guide/Basic bandwidth plans/Bind a basic bandwidth plan.md).


## Step 3: Add an acceleration area

After you purchase a GA instance, you can add one or more acceleration areas where users are located, and allocate bandwidth to these areas.

To add an acceleration region, perform the following steps:

1.  On the **Instances** page, find the GA instance and click its ID.

2.  Click the **Acceleration Area** tab, and click **Add Region** on the **Asia Pacific** tab.

3.  In the **Add Acceleration Area** dialog box, set the following parameters:

    -   **Regions**: Select the region where users are located. **China \(Hong Kong\)** is selected in this example.
    -   **Bandwidth**: Select a bandwidth value for the acceleration service. The value is set to **10** in this example. Unit: Mbit/s.
    -   **Internet Protocol**: Select the IP version that is used to connect the clients to GA. **IPv4** is selected in this example.
4.  Click **OK**.

    After you add the region, the system assigns an accelerated IP address to the region that is added to the GA instance. This accelerated IP address is used to forward requests from users in the specified region to the specified origin server through GA and accelerate connections to the origin server.

    ![Accelerated IP address](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7275625161/p84380.png)


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


## Step 5: Configure the endpoint group

Each listener is associated with an endpoint group. You can associate an endpoint group with listeners by specifying the regions to which you want to distribute network traffic. After you associate an endpoint group with a listener, traffic is distributed to the optimal endpoint in the associated endpoint group.

To create an endpoint group, perform the following steps:

1.  Enter a name for the endpoint group in the **Endpoint Group Name** field.

    The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). The name must start with a letter.

2.  Select the region to be associated with the endpoint group. This region is also the place where the destination servers are located.

    In this example, **US \(Silicon Valley\)** is selected.

3.  Specify whether the backend services are deployed on Alibaba Cloud. **Off Alibaba Cloud** is selected in this example.

4.  Specify whether to reserve client IP addresses. After the feature is enabled, backend servers can reserve client IP addresses. This feature is disabled in this topic.

    **Note:** This feature is available to only users that are included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

5.  Configure the following parameters:

    1.  **Backend Service Type**: Select **Custom IP Address** from the drop-down list.

    2.  **Backend Service**: Enter the IP address that you want to accelerate. In this example, the IP address of Server 1 is specified.

    3.  **Weight**: Enter a number from 0 to 255 to set a weight for the endpoint. GA routes network traffic to endpoints based on the specified weights. In this example, the weight of Server 1 is set to **10**.

6.  Click **Add Endpoint** to specify Server 2 as an endpoint and set the weight of this endpoint to **40**.

    ![IP address endpoint](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7275625161/p84404.png)

7.  Click **Next** to check the configurations. After you confirm the configurations, click **Submit**.


## Step 6: Test the acceleration performance

To test the acceleration performance, perform the following steps:

1.  Open the command-line interface on the client that is located in China \(Hong Kong\).

2.  Run the following command to check the network latency of data transmission:

    `curl -o /dev/null -s -w "time_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" "http[s]://<Accelerated IP address>[:<Listening port>]"`

    Where:

    -   time\_connect: the period between the time when a request is sent and when a TCP connection is established.
    -   time\_starttransfer: the period between the time when a request is sent and when the client receives the first byte returned by the backend server. After this period, the system starts to transmit data packets.
    -   time\_total: the total connection time. It refers to the time period from when a client sends a connection request to when a backend server responds to the request.
    The following figures show that GA has reduced the latency of the application.

    ![The network latency of data transmission before GA is used](../images/p76785.png "The network latency of data transmission before GA is used")

    ![The latency of data transmission after GA is used](../images/p76786.png "The network latency of data transmission after GA is used")

    **Note:** If you have added a UDP listener to your GA instance, you can use UDPing to test the acceleration performance of UDP traffic. For more information, see [Test the acceleration of UDP traffic](/intl.en-US/Deployment & Maintenance/Test the acceleration of UDP traffic.md).



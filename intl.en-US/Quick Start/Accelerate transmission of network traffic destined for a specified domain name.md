# Accelerate transmission of network traffic destined for a specified domain name

This topic describes how to use Global Accelerator \(GA\) to accelerate connections to origin servers by using domain names of the servers.

The following scenario is introduced as an example. A multinational company is headquartered in the US \(Silicon Valley\) region, where a web service is deployed on two origin servers on the premises. The web service can be accessed through the domain name www.example.com on port 80. When users from the office in the China \(Hong Kong\) region connect to the web service deployed in US \(Silicon Valley\) over the Internet, the network performance is unstable. The unstable network performance may cause issues such as latency, network jitters, and packet loss.

To accelerate connections to the origin servers, you can create a GA instance that provides an access point in China \(Hong Kong\). When users in China \(Hong Kong\) send requests to the servers, the access point in China \(Hong Kong\) receives the requests and forwards the requests to the endpoints in US \(Silicon Valley\) through intelligent routing. GA can improve user experience of the web service.

![Accelerate transmission of network traffic destined for a specified domain name](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1978035951/p103042.png)

## Procedure

![Configure web acceleration through a specified domain name](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1978035951/p103045.png)

## Step 1: Enter the required information about the accelerated web service

You can enter the required information about the accelerated web service in the GA console. The system provides the recommended GA instance and basic bandwidth plan to meet your business requirements.

To enter the required information about the accelerated web service, perform the following steps:

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  In the upper-right corner of the **Instances** page, click **Purchase Guide**.

    **Note:** Skip the preceding step if you are a first-time user.

    ![Purchase Guide](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2367958951/p103054.png)

3.  In the **Enter the required information to generate a list of recommended services** section, enter the required information.

    -   **Acceleration Area**: Select the area that requires acceleration. Select **China \(Hong Kong\)** in this example.
    -   **Service Region**: Select the region where the origin servers are located. **US \(Silicon Valley\)** is selected in this example.
    -   **ICP Filing**: If you need to accelerate a web service, specify whether the domain name of the web service has applied for an Internet Content Provider \(ICP\) number. If the service is not a web service, select **No**. In this example, **No** is selected.

        **Note:** All websites must obtain an ICP number before they are permitted to provide services to users in mainland China. For more information, see [What is an ICP filing?]().

    -   **Server Area**: Specify whether the origin servers are deployed on Alibaba Cloud or in the environments outside Alibaba Cloud. **Off Alibaba Cloud** is selected in this example.
    -   **Peak Bandwidth Range**: Enter the bandwidth required during peak hours. Unit: Mbit/s. The value is set to **10** in this example.
    -   **Maximum Concurrent Connections**: Specify the maximum number of concurrent connections to the GA instance. If the number of existing concurrent connections reaches the upper limit, no extra connections are established. The value is set to **5 thousand** in this example.
4.  Click **Generate Service List**.

    After a list is generated, you can check the recommended services in the list.

    ![Recommended Service List](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3707827951/p103000.png)


## Step 2: Purchase a GA service bundle

You can purchase a GA service bundle that includes the recommended GA instance and basic bandwidth plan.

To purchase a service bundle, perform the following steps:

1.  Click **Generate Service List**.

    ![Generate Service List](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2367958951/p103007.png)

2.  On the buy page, specify the following parameters for the GA instance:

    -   **Term**: Select a subscription duration.

        **Note:** The subscription duration applies to all the services in the recommended service bundle. For example, if you set Term to 1 Year,the subscription duration of the specified GA instance, basic bandwidth plan, and cross-border bandwidth plan is valid for one year.

    -   **Specification**: Select a specification of the GA instance. **Small I** is selected in this example.

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

    -   **Peak Bandwidth**: Specify a value as the peak bandwidth for the basic bandwidth plan. The value is set to **10Mb** in this example.
3.  Click **Buy Now** and pay for the order.


After you purchase the service bundle, the basic bandwidth plan is automatically bound to the GA instance.

## Step 3: Add an acceleration area

After you purchase a GA instance, you can add one or more acceleration areas where users are located, and allocate bandwidth to these areas.

To add an acceleration area, perform the following steps:

1.  On the **Instances** page, find the GA instance that you created and click the instance ID.

2.  On the page that appears, click the **Acceleration Areas** tab. Then, click **Add Acceleration Area**.

3.  In the **Add Acceleration Area** dialog box, specify the following parameters to configure the acceleration area:

    -   **Acceleration Area**: Select the area that requires acceleration. Select **Asia Pacific** in this example.
    -   **Regions**: Select the region where users are located. Select **China \(Hong Kong\)** in this example.
    -   **Bandwidth**: Specify the amount of bandwidth to be allocated to the region. The value is set to **10** in this example. Unit: Mbit/s.
    -   4.  Click **OK**.

    After you add the region, the system assigns an accelerated IP address to the region that is added to the GA instance. This accelerated IP address is used to forward requests of users in the specified region to the specified origin server through GA and accelerate connections to the origin server.

    ![Accelerated IP address](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9298035951/p84380.png)


## Step 4: Add a listener

Listeners are used to monitor connection requests from clients. GA monitors connection requests received on the specified listener ports and forwards the requests to endpoints through the specified protocol.

To add a listener to the GA instance, perform the following steps:

1.  On the instance details page, click the **Listeners** tab. Then, click **Add Listener**.

2.  In the **Configure Listener & Protocol** wizard, specify the following listener parameters:

    -   **Listener Name**: Enter a name for the listener to be created. The name must be 2 to 128 characters in length, and can contain letters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.
    -   **Protocol**: Select a protocol for the listener. **TCP** is selected in this example.
    -   **Port Number**: Enter the listening port number for receiving requests and forwarding requests to the endpoints. Valid values: 1 to 65499. The value is set to **80** in this example.
    -   **Client Affinity**: Select whether to enable client affinity. If client affinity is enabled, requests from a specific client IP address are always forwarded to the same endpoint. The client IP address is considered as the source IP address. **Source IP Address** is selected in this example.
    ![Listeners](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2367958951/p84395.png)

3.  Click **Next** to configure an endpoint group.


## Step 5: Configure an endpoint group

Each listener is associated with an endpoint group. You can associate an endpoint group with listeners by specifying the regions to which you want to distribute network traffic. After you associate an endpoint group with a listener, traffic is distributed to the optimal endpoint in the associated endpoint group.

To create an endpoint group, perform the following steps:

1.  **Endpoint Group Name**: Enter a name for the endpoint group.

2.  Select the region to be associated with the endpoint group. This region is also the place where the origin servers are located.

    **US \(Silicon Valley\)** is selected in this example.

3.  Specify whether the origin servers are deployed on Alibaba Cloud or in the environments outside Alibaba Cloud. **Off Alibaba Cloud** is selected in this example.

4.  Enable or disable the origin servers to reserve client IP addresses in the specified region. After the feature is enabled, origin servers can reserve client IP addresses. This feature is disabled in this topic.

    **Note:** This feature is available to only the accounts that are added to the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

5.  Configure endpoints.

    1.  **Backend Service Type**: Select **Custom Domain Name** from the drop-down list.

    2.  **Backend Service**: Enter the custom domain name that you want to accelerate.

    3.  **Weight**: Specify a weight for the endpoint. Valid values: 0 to 255. GA routes traffic to endpoints based on the predefined weights.

        **Note:** If you set the weight of an endpoint to 0, GA stops to distribute network traffic to the endpoint. Proceed with caution.

    ![Configure endpoints](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1978035951/p84372.png)

6.  Click **Next** to check the configurations. After you confirm the configurations, click **Next**.


## Step 6: Configure a CNAME record

To enable the acceleration service based on the CNAME assigned to your GA instance, you must configure a CNAME record to map your accelerated domain name to the CNAME.

To configure a CNAME record, perform the following steps:

1.  Log on to the [Alibaba Cloud DNS console](https://dc.console.aliyun.com/dns).

2.  On the Manage DNS page, find the domain name that you want to manage, and click **Configure** in the **Actions** column to go to the DNS Settings page.

3.  Click **Add Record** and specify the following parameters:

    1.  **Type**: Select **CNAME** from the drop-down list.

    2.  **Host**: Enter the prefix of the accelerated domain name. The following list shows some examples of the prefix.

        -   If the accelerated domain name is `testcdn.aliyun.com`, set the prefix to `testcdn`.
        -   If the accelerated domain name is `www.aliyun.com`, set the prefix to `www`.
        -   If the accelerated domain name is `aliyun.com`, set the prefix to `@`.
        -   If the accelerated domain name is `*.aliyun.com`, set the prefix to `*`.
    3.  **ISP Line**: Select **Default** from the drop-down list.

    4.  **Value**: Enter the CNAME value that is allocated to your GA instance. You can find the value on the Instances page next to the Instance ID/Name of the instance.

        ![CNAME](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3947958951/p84125.png)

    5.  **TTL**: Select **10 minute \(s\)**.

    6.  Click **OK**.

    **Note:**

    -   A new CNAME record immediately takes effect. If you modify the CNAME record, the record takes effect within 72 hours after the modification.
    -   After you add a CNAME record, it takes about 10 minutes for the system to update the status in the console. The message "You must add the CNAME record" may appear on the Domain Names page. Ignore this message.

## Step 7: Test the acceleration of TCP traffic

To test the acceleration of TCP traffic, perform the following steps:

1.  Open Command Prompt on the client located in the China \(Hong Kong\) region.

2.  Run the following command to test the latency of data transmission:

    `curl -o /dev/null -s -w "time_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" ""http[s]://<Domain name of the origin server>[:<Port>]""`

    where:

    -   time\_connect: the period between the time when a request is sent and when a TCP connection is established.
    -   time\_starttransfer: the period between the time when a request is sent and when the client receives the first byte returned by the origin server. After this period, the system starts to transmit data packets.
    -   time\_total: the period between the time when a request is sent and when the client receives the last byte returned by the origin server. This is the total time consumed for the communication between the client and the origin server.
    The following figures show that GA reduces the latency of the web service.

    ![Data transmission before GA is used](../images/p93976.png "The latency of data transmission before GA is used")

    ![Data transmission after GA is used](../images/p93977.png "The latency of data transmission after GA is used")

    **Note:** If you specify UDP as the protocol when you add a listener, you can test the acceleration performance by using the UDPing network performance measurement tool. For more information, see [Test the acceleration of UDP traffic](/intl.en-US/Deployment & Maintenance/Test the acceleration of UDP traffic.md).



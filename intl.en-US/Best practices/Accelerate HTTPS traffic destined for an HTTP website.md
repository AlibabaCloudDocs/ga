# Accelerate HTTPS traffic destined for an HTTP website

This topic describes how to use Global Accelerator \(GA\) to accelerate HTTPS traffic that is destined for your HTTP website. This improves user experience and enhances the service security.

## Scenario

The following scenario is used as an example. A multinational company has deployed an on-premises origin server at its headquarters in the US \(Silicon Valley\) region, and an HTTP website is hosted on the origin server. The clients that access the website are located in China \(Hong Kong\). The website may encounter the following issues:

-   Data is transmitted in plaintext over HTTP and the requests that are destined for the website are not authenticated. Therefore, security risks may arise.
-   The cross-border connections over the Internet are vulnerable to several issues, such as network latency, network jitter, and packet loss.

You can deploy the GA service and configure HTTPS listeners. When clients in China \(Hong Kong\) send requests to the HTTP website that is deployed in US \(Silicon Valley\), you can use GA to accelerate the HTTPS traffic and encrypt data transmission.

![Scenario](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1747122061/p166508.png)

## Prerequisites

Before you start, make sure the following requirements are met:

-   An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account, click [here](https://account.alibabacloud.com/register/intl_register.htm) to create one.
-   Acceleration of HTTPS traffic is available to only the accounts that are added to the whitelist. To use this feature, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

## Procedure

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1747122061/p166672.png)

## Step 1: Enter the required information about the accelerated web service

You can enter the required information about the accelerated web service in the GA console. The system provides the recommended GA instance and basic bandwidth plan to meet your business requirements.

To enter the required information about the accelerated web service, perform the following steps:

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  In the upper-right corner of the **Instances** page, click **Purchase Guide**.

    **Note:** Skip the preceding step if you are a first-time user.

    ![Purchase Guide](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2367958951/p103054.png)

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

    ![Recommended Service List](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3707827951/p103000.png)


## Step 2: Purchase a service bundle

You can purchase a GA service bundle that includes the recommended GA instance and basic bandwidth plan.

To purchase a service bundle, perform the following steps:

1.  Click **Generate Service List** at the bottom of the Recommended Service List section.

    ![Purchase a GA service bundle](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2367958951/p103007.png)

2.  On the buy page, set the following parameters for the GA instance.

    -   **Term**: Select a subscription duration.

        **Note:** The subscription duration applies to all services in the recommended service bundle. For example, if you set Term to 1 Year, each of the GA instance, basic bandwidth plan, and cross-border acceleration bandwidth plan has a one-year subscription duration.

    -   **Specification**: Select a specification of the GA instance. In this example, **Small I** is selected.

        GA supports the following types of instance specifications: Small I, Small II, Small III, Medium I, Medium II, and Medium III. The acceleration performance can vary based on the instance specification.

        |Instance specification|Number of acceleration regions|Peak bandwidth|Maximum number of concurrent connections|
        |----------------------|------------------------------|--------------|----------------------------------------|
        |Small I|1|20 Mbit/s|5,000|
        |Small II|2|40 Mbit/s|10,000|
        |Small III|3|60 Mbit/s|15,000|
        |Medium I|5|100 Mbit/s|25,000|
        |Medium II|8|160 Mbit/s|40,000|
        |Medium III|10|200 Mbit/s|50,000|

    -   **Bandwidth Type**: Select a bandwidth type for the basic bandwidth plan. In this example, **Premium** is selected.

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

    -   **Peak Bandwidth**: Specify a value as the maximum bandwidth for the basic bandwidth plan. In this example, the value is set to **10Mb**.
3.  Click **Buy Now** and complete the payment.


After you purchase the instance, the system automatically assigns a Canonical Name \(CNAME\) to the GA instance. The base bandwidth plan is automatically associated with the GA instance.

![CNAME of the GA instance](../images/p166644.png "CNAME of the GA instance")

![Basic bandwidth plan automatically associated with the GA instance](../images/p166645.png "Basic bandwidth plan automatically associated with the GA instance")

## Step 3: Add an acceleration area

After you purchase a GA instance, you can add one or more acceleration areas where users are located, and allocate bandwidth to these areas.

To add an acceleration area, perform the following steps:

1.  On the **Instances** page, find the GA instance that you have created and click the instance ID.

2.  On the instance details page, click the **Acceleration Areas** tab. Then, click **Add Acceleration Area**.

3.  In the **Add Acceleration Area** dialog box, set the following parameters, and click **OK**.

    -   **Acceleration Area**: Select the area that requires acceleration. In this example, **Asia Pacific** is selected.
    -   **Regions**: Select the region where users are located. In this example, **China \(Hong Kong\)** is selected.
    -   **Bandwidth**: Specify the amount of bandwidth to be allocated to the region. In this example, **10** is specified. Unit: Mbit/s.
    -   **Internet Protocol**: Select the IP protocol that is used by the GA instance. In this example, **IPv4** is selected.

After the acceleration areas are added, GA assigns an accelerated IP address to each acceleration area to accelerate connections.

![Add an acceleration area](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6416911061/p166558.png)

## Step 4: Add a listener

A listener monitors connection requests from clients and forwards the requests based on the specified protocol and port.

To add a listener to the GA instance, perform the following steps:

1.  On the instance details page, click the **Listeners** tab. Then, click **Add Listener**.

2.  On the **Configure Listener & Protocol** wizard page, set the following listener parameters:

    -   **Listener Name**: Enter a name for the listener to be created.

        The name must be 2 to 128 characters in length, and can contain letters, Chinese characters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter or a Chinese character.

    -   **Protocol**: Select a protocol for the listener. In this example, **HTTPS** is selected.
    -   **Port Number**: Enter a port number or port range. The specified ports receive requests and forward the requests to the endpoints. Valid values: 1 to 65499. In this example, the value is set to **443**.
    -   **Client Affinity**: Enable or disable client affinity. If client affinity is enabled, requests from a specific client IP address are routed to the same endpoint. The client IP address is regarded as the source IP address. In this example, **Source IP Address** is selected.
    ![Configure the listener](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7416911061/p166568.png)

3.  Click **Next** to configure an SSL certificate.


## Step 5 Configure an SSL certificate

After you configure an SSL certificate for your website, the communication with the website is encrypted based on HTTPS. This allows you to secure the transmission of sensitive data.

To configure the SSL certificate, perform the following steps:

1.  On the **Configure SSL Certificate** wizard page, set the following parameters for the SSL certificate:

    -   **Server Certificate**: Select the SSL certificate that has been validated.
    -   **Backend Port**: Enter the port of the backend service. In this example, the value is set to **80**.
    ![Configure an SSL certificate](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2067122061/p166615.png)

2.  Click **Next** to configure an endpoint group.


## Step 6: Configure an endpoint group

Each listener is associated with an endpoint group. You can associate an endpoint group with a listener by specifying the region to which you want to distribute network traffic. After a listener forwards network traffic to the associated endpoint group based on the association rules, GA distributes network traffic to the optimal endpoints of the endpoint group.

To configure an endpoint group, perform the following steps:

1.  On the **Configure Endpoint Group** wizard page, set the following parameters for the endpoint group:

    -   **Endpoint Group Name**: Enter a name for the endpoint group.

        The name must be 2 to 128 characters in length, and can contain letters, Chinese characters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter or a Chinese character.

    -   **Region**: Select the region to which the endpoint group belongs. The region specifies where the origin server is located.

        In this example, **US \(Silicon Valley\)** is selected.

    -   **Backend Service**: Specify whether the origin server is deployed on Alibaba Cloud.

        In this example, **Off Alibaba Cloud** is selected.

    -   **Preserve Client IP**: By default, this feature is enabled. This allows each HTTPS listener to read client IP addresses from the X-Forwarded-For \(XFF\) HTTP header field.

        **Note:** This feature is available to only the accounts that are added to the whitelist. To use this feature, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

    -   **Endpoint Configuration**
        -   **Backend Service Type**: Select **Custom IP Address** from the drop-down list.
        -   **Backend Service**: Enter the IP address of the origin server to be accelerated.
        -   **Weight**: Specify a weight for the endpoint. Valid values: 0 to 255. GA routes network traffic to endpoints based on the predefined weights.

            **Note:** If you set the weight of an endpoint to 0, GA stops distributing network traffic to the endpoint. Proceed with caution.

    ![Configure an endpoint group](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7416911061/p166636.png)

2.  Click **Next** to check the configurations. After you confirm the configurations, click **Next**.


## Step 7: Modify the DNS record

You must add the CNAME that is assigned to the GA instance to the Domain Name System \(DNS\) records. This allows GA to accelerate the network traffic that is destined for your website. The following example shows how to modify the DNS record in the Alibaba Cloud DNS console.

**Note:** If you use the DNS resolution service that is provided by a third-party service provider, log on to the platform of the service provider and modify the DNS record for your website.

To modify the DNS record, perform the following steps:

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com).

2.  On the **Manage DNS** page, find the domain name that you want to manage, and click **Configure** in the **Actions** column.

3.  On the **Configure** page, find the DNS record that you want to modify, and click **Edit** in the **Actions** column.

4.  In the **Edit Record** pane, set **Type** to **CNAME** and set **Value** to the CNAME that is assigned to the GA instance in Step 2. For more information, see [Step 2: Purchase a service bundle](#section_6g9_632_9n4).

    ![Modify the DNS record](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7203177951/p135152.png)

5.  Click **OK**.


## Step 8: Verify the settings

To test how GA accelerates HTTPS traffic destined for the HTTP website that is deployed in US \(Silicon Valley\), perform the following steps:

1.  Use a computer in China \(Hong Kong\) to open a browser.

2.  In the address bar of the browser, enter `https:[Domain name of your website]` to visit the HTTP website.

    The test result shows that the website deployed in US \(Silicon Valley\) can be accessed over HTTPS.

    ![Verify the settings](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7416911061/p166658.png)

3.  Open Command Prompt on the client that is located in China \(Hong Kong\).

4.  On the command line, run the following command to check the network latency of data transmission:

    `curl -o /dev/null -s -w "time_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" "https://<Domain name of your website>"`

    In the request:

    -   time\_connect: The amount of time that it takes to establish a TCP connection.
    -   time\_starttransfer: The data transmission start time. It refers to the time period from when a client sends a request to when a backend server responds to the first byte.
    -   time\_total: The total connection time. It refers to the time period from when a client sends a connection request to when a backend server responds to the request.
    The test result shows that GA reduces the network latency when users in China \(Hong Kong\) access the website deployed in US \(Silicon Valley\).

    ![Before GA is enabled](../images/p76785.png "Before GA is enabled")

    ![After GA is enabled](../images/p76786.png "After GA is enabled")

    **Note:** The test result varies based on the actual workloads.



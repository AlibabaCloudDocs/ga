# GA interacts with Alibaba Cloud CDN to accelerate content retrieval from origin servers

Global Accelerator \(GA\) can interact with Alibaba Cloud Content Delivery Network \(CDN\) to accelerate content retrieval from origin servers. GA uses high-bandwidth BGP lines and the global transmission network of Alibaba Cloud to accelerate content delivery. You can connect CDN to GA to accelerate the delivery of dynamic content on a global scale.

An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account,create an account before you proceed to the next step. To create an Alibaba Cloud account, visit the page: [Create Your Alibaba Cloud Account](https://account.alibabacloud.com/register/intl_register.htm).

The scenario in the following figure is used as an example. A web service is deployed in the US \(Silicon Valley\) region. The origin servers provide web services through elastic IP addresses of Alibaba Cloud. The forwarding port is TCP port 80. Users are located in the China \(Hong Kong\) region. When clients in China \(Hong Kong\) access the web service in US \(Silicon Valley\), issues such as network latency, network jitter, and packet loss may frequently occur. This is because the cross-border Internet is unstable.

You can deploy CDN to accelerate content delivery from your web service. CDN caches frequently requested content on CDN nodes to improve user experience. GA uses high-bandwidth BGP lines and the global transmission network of Alibaba Cloud to accelerate content delivery. You can set CDN to interact with GA to accelerate the delivery of dynamic content on a global scale.

![Scenario](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6203177951/p135023.png)

## Procedure

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6203177951/p135024.png)

## Step 1: Enter the required information about the accelerated web service

You can enter the information about the accelerated web service in the GA console. The system then generates a list of recommended services, including a GA instance and a basic bandwidth plan.

To enter the required information about the accelerated web service, perform the following steps:

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  In the upper-right corner of the **Instances** page, click **Purchase Guide**.

    **Note:** Skip the preceding step if you are a first-time user.

    ![Purchase Guide](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2367958951/p103054.png)

3.  In the **Enter the required information to generate a list of recommended services** section, enter the required information.

    -   **Acceleration Area**: Select the area that requires acceleration. **China \(Hong Kong\)** is selected in this example.
    -   **Service Region**: Select the region where the origin servers are deployed. **US \(Silicon Valley\)** is selected in this example.
    -   **ICP Filing**: If you need to accelerate a web service, specify whether the domain name of the web service has applied for an Internet Content Provider \(ICP\) number. If the service is not a web service, select **No**. **No** is selected in this example.

        **Note:** All websites must obtain an ICP number before they are permitted to provide services to users in mainland China. For more information, see [What is an ICP filing?]().

    -   **Server Area**: Specify whether the origin servers are deployed on Alibaba Cloud or in the environments outside Alibaba Cloud. Select **On Alibaba Cloud** in this example.
    -   **Peak Bandwidth Range**: Enter the bandwidth required during peak hours. Unit: Mbit/s. **10** is entered in this example.
    -   **Maximum Concurrent Connections**: Specify the maximum number of concurrent connections to the GA instance. If the number of existing concurrent connections reaches the upper limit, no extra connections are established. **5 thousand** is selected in this example.
4.  Click **Generate Service List**.

    After a list is generated, you can check the recommended services in the list.

    ![Recommended service list](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6203177951/p134878.png)


## Step 2: Purchase a GA service bundle

You can purchase a GA service bundle based on the recommended service list. The list includes a GA instance and a basic bandwidth plan.

To purchase a service bundle, perform the following steps:

1.  Click **Generate Service List**.

    ![Purchase service bundle](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7203177951/p134881.png)

2.  On the buy page, specify the following parameters for the GA instance:

    -   **Term**: Select a subscription duration.

        **Note:** The subscription duration applies to all services in the service bundle. For example, if you set the subscription duration to one year, you subscribe to both the GA instance and basic bandwidth plan for one year.

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

    -   **Bandwidth Type**: Specify the type of the basic bandwidth plan. **Basic** is specified in this example.

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

    -   **Peak Bandwidth**: Specify the maximum bandwidth of the basic bandwidth plan. **10** Mbit/s is specified in this example.
3.  Click **Buy Now** and pay for the order.


After you purchase the service bundle, the system automatically assigns a CNAME address to the GA instance. Requests destined for the CNAME address are accelerated and resolved to the origin servers.

![CNAME](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7203177951/p134944.png)

The basic bandwidth plan is automatically bound to the GA instance.

![Bind the basic bandwidth plan](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7203177951/p134884.png)

## Step 3: Add an acceleration area

After you purchase a GA instance, you can add one or more acceleration areas where users are located, and then allocate bandwidth to these areas.

To add an acceleration area, perform the following steps:

1.  On the **Instances** page, find the GA instance that you created, and click the instance ID.

2.  On the instance details page, click the **Acceleration Areas** tab. Then, click **Add Acceleration Area**.

3.  In the **Add Acceleration Area** dialog box, specify the following parameters, and click **OK**.

    -   **Acceleration Area**: Select the area that requires acceleration. **Asia Pacific** is selected in this example.
    -   **Regions**: Select the regions where the users are located. **China \(Hong Kong\)** is selected in this example.
    -   **Bandwidth**: Specify the amount of bandwidth to be allocated to the region. **10** Mbit/s is entered in this example.
    -   **Internet Protocol**: Select the IP protocol of the service to be accelerated by GA. **IPv4** is selected in this example.

        **Note:** IPv6 is available to only users in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).


After an acceleration area is added, GA assigns an accelerated IP address to the acceleration area. Clients can connect to the accelerated IP address for content delivery acceleration.

![Add an acceleration area](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7203177951/p134913.png)

## Step 4: Add a listener

Listeners are used to monitor connection requests from clients. GA monitors connection requests received on the specified listener ports and forwards the requests to endpoints through the specified protocol.

To add a listener to the GA instance, perform the following steps:

1.  On the instance details page, click the **Listeners** tab. Then, click **Add Listener**.

2.  In the **Configure Listener & Protocol** wizard, specify the following listener parameters.

    -   **Listener Name**: Enter a name for the listener to be created. The name must be 2 to 128 characters in length, and can contain letters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.
    -   **Protocol**: Select a protocol for the listener. **TCP** is selected in this example.
    -   **Port Number**: Enter the listening port number for receiving requests and forwarding requests to the endpoints. Valid values: 1 to 65499. **80** is entered in this example.
    -   **Client Affinity**: Select whether to enable client affinity. If client affinity is enabled, requests from a specific client IP address are always forwarded to the same endpoint. The client IP address is considered as the source IP address. **Source IP Address** is selected in this example.
    ![Listeners](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5963284161/p84395.png)

3.  Click **Next**.


## Step 5: Configure an endpoint group

Each listener is associated with an endpoint group. You can associate an endpoint group with listeners by specifying the regions to which you want to distribute network traffic. After you associate an endpoint group with a listener, traffic is distributed to the optimal endpoint in the associated endpoint group.

To configure an endpoint group, perform the following steps:

1.  In the **Configure Endpoint Group** wizard, configure the endpoint group based on the following parameters:

    -   **Endpoint Group Name**: Enter a name for the endpoint group. The name must be 2 to 128 characters in length, and can contain letters, Chinese characters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter or Chinese character.
    -   **Region**: Select the region where the endpoint group is created. The region specifies where the origin servers are located. **US \(Silicon Valley\)** is selected in this example.
    -   **Backend Service**: Specify whether the origin servers are deployed on Alibaba Cloud. **Alibaba Cloud** is selected in this example
    -   **Reserve Client IP**: Specify whether to reserve client IP addresses. When this feature is enabled, the origin servers can obtain client IP addresses. This feature is disabled in this example.

        **Note:** The feature of reserving client IP addresses is available only to users in the whitelist. If you are not included in the whitelist and you want to use the feature, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

    -   **Endpoint**: Configure endpoints.
        -   **Backend Service Type**: Select **EIP**.
        -   **Backend Service**: Enter the elastic IP address to be accelerated.
        -   **Weight**: Specify a weight for the endpoint. Valid values: 0 to 255. GA distributes network traffic to endpoints based on the predefined weights.

            **Note:** If you set the weight of an endpoint to 0, Global Accelerator stops distributing network traffic to the endpoint. Proceed with caution.

    ![Configure endpoint group](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3367958951/p129395.png)

2.  Click **Next** to check the configurations. After you confirm the configurations, click **Next**.


## Step 6: Activate Alibaba Cloud CDN

CDN reduces the loads of the origin and helps avoid network congestion. You can use CDN to accelerate website content delivery in different regions and for different scenarios. You must activate CDN before you can use the service.

**Note:** Skip this step if you have activated CDN.

To activate CDN, perform the following steps:

1.  Log on to the [product landing page of Alibaba Cloud CDN](https://www.alibabacloud.com/en/product/cdn).

2.  Click **Buy Now**.

3.  On the activation page, specify Billing Method based on your business requirements.

    For more information about the billing methods of CDN, see [CDN Pricing](https://www.alibabacloud.com/zh/product/cdn/pricing).

4.  Select the **Alibaba Cloud CDN Terms of Service** check box, and click **Activate Now**.

5.  After CDN is activated, click **Console** to log on to the CDN console.


## Step 7: Add a domain name for CDN

CDN retrieves resources from the origin servers and caches them on CDN nodes. When a client requests resources from an accelerated domain name, CDN retrieves the resources from the CDN node that is the nearest to the client.

To add a domain name for CDN, perform the following steps:

1.  In the left-side navigation pane, click **Domain Names**.

2.  On the **Domain Names** page, click **Add Domain Name**.

3.  On the **Add Domain Name** page, specify the following parameters to add a domain name:

    -   **Domain Name to Accelerate**: Enter the domain name of the web service to be accelerated. **www.example.com** is entered in this topic.
    -   **Business Type**: Select the business type of your website.

        -   **Image and Small File**: If you need to accelerate the delivery of small-size and static resources, such as small files, images, and web style sheets, we recommend that you select this option. For more information, see [Image and small file distribution](/intl.en-US/Product Introduction/Scenarios/Image and small file distribution.md).
        -   **Large File Download**: For downloads of static content whose size is greater than 20 MB, we recommend that you select this option. Large file downloads refer to game package installation, app updates, mobile ROM upgrades, and app downloads. For more information, see [Delivery of large files](/intl.en-US/Product Introduction/Scenarios/Delivery of large files.md).
        -   **VOD**: If you need to accelerate the delivery of audio or video files for VOD playback, we recommend that you select this option. For more information, see [ApsaraVideo for VOD](/intl.en-US/Product Introduction/Scenarios/ApsaraVideo for VOD.md).
        -   **DCDN**: If your website contains a large amount of dynamic and static content, and most of the requests are for dynamic resources, we recommend that you select this option. For more information, see [DCDN](/intl.en-US/Product Introduction/Scenarios/DCDN.md).
        **Image and Small File** is selected in this topic.

    -   **Origin Info**: Configure the origin information.

        Select **Site Domain** in this example, and enter the CNAME assigned to the GA instance. For more information, see [Step 2: Purchase a GA service bundle](#section_4f2_oon_4nc).

    -   **Port**: Select the port that is used to receive requests from clients. Valid values:

        -   **Port 80**: Select this option if your website provides services over HTTP.
        -   **Port 443**: Select this option if your website provides services over HTTPS.
        **Port 80** is selected in this topic.

    -   **Region**: Select the area to be accelerated. **Global \(Excluding Mainland China\)** is selected in this example.

        **Note:** If the acceleration area includes mainland China, your domain name must have an ICP number. For more information, see [What is an ICP filing?]().

4.  Click **Next** and then click **Return to Domain Names**.

    After you add a domain name for CDN, CDN assigns a CNAME to the domain name.

    ![cname](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p99749.png)


## Step 8: Configure DNS settings

After you add a domain name for CDN, you must modify the DNS record to resolve the domain name of your web service to CDN. Then, requests sent to the domain name can be forwarded to CDN nodes for acceleration. The following example shows how to modify the DNS record in the Alibaba Cloud DNS console.

**Note:** If you are using DNS resolution services provided by a third-party service provider, log on to the platform of the service provider and modify the DNS record for your web service.

To configure DNS settings, perform the following steps:

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com).

2.  On the **Manage DNS** page, find the target domain name, and click **Configure** in the **Actions** column.

3.  On the **Configure**page, find the DNS records, and click **Edit** in the **Actions** column.

4.  In the **Edit Record** panel, set **Type** to **CNAME** and set **Value** to the CNAME that is assigned to the accelerated domain name in Step 7. For more information, see [Step 7: Add a domain name for CDN](#section_vp5_tl2_t5h).

    ![Edit Record](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7203177951/p135152.png)

5.  Click **OK**.


## Step 9: Verify the settings

Use a computer that runs Windows in China \(Hong Kong\) to test how GA interacts with CDN to accelerate content delivery.

To test the acceleration performance, perform the following steps:

1.  Enter the domain name www.example.com into the address bar of the browser to access the web service that is deployed in the US \(Silicon Valley\) region.

    The test result shows that you can access the web service that is deployed in the US \(Silicon Valley\) region by using the domain name www.example.com.

    ![Verify the settings](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7203177951/p135008.png)

2.  Run the following command to test the latency of data transmission:

    `curl -o /dev/null -s -w "time_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" "http[s]://<Domain name of the web service>[:<Port>]"`

    In the request:

    -   time\_connect: The amount of time that it takes to establish a TCP connection.
    -   time\_starttransfer: The data transmission start time. It refers to the time period from when a client sends a request to when a backend server responds to the first byte.
    -   time\_total: The total connection time. It refers to the time period from when a client sends a connection request to when a backend server responds to the request.
    The test result shows that the latency of data transmission from China \(Hong Kong\) to US \(Silicon Valley\) is reduced after GA is set to interact with CDN.

    ![The latency of data transmission before GA is used](../images/p76785.png "The latency of data transmission before GA is used")

    ![Test the latency of data transmission](../images/p135011.png "The latency of data transmission after GA is used")

    **Note:** The test result varies based on the actual workloads.



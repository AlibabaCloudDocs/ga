---
keyword: [access multiple domain names, HTTPS listener, forwarding rule, virtual endpoint group, service delivery acceleration]
---

# Use only one GA instance to accelerate multiple domain names over HTTPS

This topic describes how to use only one Global Accelerator \(GA\) instance to accelerate multiple domain names over HTTPS.

Before you start, make sure that the following requirements are met:

-   Your website has an Internet Content Provider \(ICP\) number. A website must obtain an ICP number before the website is allowed to provide services in mainland China. For more information, see [What is an ICP filing?]()
-   A Secure Sockets Layer \(SSL\) certificate is purchased and an application is submitted to apply for the SSL certificate. For more information, see [Purchase a certificate](/intl.en-US/Buy Certificates/Select and purchase certificates.md) and [Apply for a certificate]().
-   You can create both HTTP and HTTPS listeners for GA if you are included in the whitelist.To apply to be added to the whitelist, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

The following scenario is used in this example. A company deployed two servers in the China \(Beijing\) region for its headquarters, and a web application is deployed on both servers. The web application provides Internal-facing services through two different domain names. Most employees of the company need to access the web application from the China \(Hangzhou\) region. They face the following challenges:

-   The network connections that are established over the Internet are unstable. Network issues, such as network latency, network jitter, and packet loss, may frequently occur.
-   Multiple servers provide Internet-facing services through two different domain names. The company must configure content delivery acceleration for both domain names. This increases the cost.

To resolve these issues, you can deploy the GA service and configure HTTPS listeners. HTTPS listeners support domain name-aware forwarding rules. HTTPS listeners can forward requests that are destined for different domain names to the corresponding backend servers. To ensure the security of data transmission, HTTPS listeners also encrypt the data that is carried in the received requests. This allows you to use only one GA instance to accelerate multiple domain names over HTTPS.

![Architecture](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0753614161/p223910.png)

The following table describes information about the web servers of the company and the forwarding rules that the HTTPS listeners use after the company uses GA to accelerate its web application.

|Domain name|Listener protocol|Listener port|Forwarding rule|Endpoint group|Server|Service protocol|Service port|Server public IP address|
|-----------|-----------------|-------------|---------------|--------------|------|----------------|------------|------------------------|
|www.xxxtest.icu|HTTPS|443|Custom forwarding rule|Virtual endpoint group|Server 1|HTTPS|443|182.XX.XX.248|
|xxxtest.icu|Default forwarding rule|Default endpoint group|Server 2|HTTP|8443|182.XX.XX.196|

## Procedure

![Procedure for accelerating multiple domain names](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0753614161/p210974.png)

## Step 1: Enter the required information

Before you use GA, you must purchase a GA instance and a basic bandwidth plan.

You can enter the information about your web application in the GA console. After you enter the information, the system generates a list of recommended services. The list includes a GA instance and a basic bandwidth plan.

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  In the upper-right corner of the **Instances** page, click **Purchase Guide**.

    **Note:** Skip the preceding step if you are a first-time user.

    ![Purchase Guide](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2367958951/p103054.png)

3.  In the **Enter the required information to generate a list of recommended services** section, enter the required information about your web application.

    -   **Acceleration Area**: Select the region where the clients are located. **China \(Hangzhou\)** is selected in this example.
    -   **Service Region**: Select the region where the backend servers are deployed. **China \(Beijing\)** is selected in this example.
    -   **ICP Filing**: If you want to accelerate web applications, specify whether you have obtained an ICP number. If the services that you want to accelerate are not web applications, select **No**. **Yes** is selected in this example.

        **Note:** A website must obtain an ICP number before the website is allowed to provide services in mainland China. For more information, see [What is an ICP filing?]()

    -   **Server Area**: Specify whether the backend servers are deployed on Alibaba Cloud or in an environment outside Alibaba Cloud. **On Alibaba Cloud** is selected in this example.
    -   **Peak Bandwidth Range**: Enter the maximum bandwidth that is required during peak hours. Unit: Mbit/s. The value is set to **10** in this example.
    -   **Maximum Concurrent Connections**: Specify the maximum number of concurrent connections that the GA instance supports. When the number of existing concurrent connections reaches the upper limit, new connection requests are dropped. The value is set to **5 thousand** in this example.
4.  Click **Generate Service List**.

    After a list is generated, you can check the recommended services in the list.

    ![Recommended services](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1213712161/p210793.png)


## Step 2: Purchase a GA service bundle

You can purchase a GA service bundle based on the list of recommended services. The list includes a GA instance and a basic bandwidth plan.

1.  Click **Generate Service List**.

2.  On the buy page, set the following parameters for the GA instance.

    -   **Term**: Select a subscription period.

        **Note:** The subscription period applies to the services in the recommended service bundle. For example, if you set Term to 1 Year,the subscription periods of the specified GA instance, basic bandwidth plan, and cross-border bandwidth plan are all set to one year.

    -   **Specification**: Select a specification for the GA instance that you want to create. **Small I \(Specification Unit\)** is selected in this example.

        GA supports the following types of instance specifications: Small I, Small II, Small III, Medium I, Medium II, and Medium III. The acceleration performance varies based on the instance specification. The following table describes the details.

        |Specification|Number of acceleration regions|Maximum bandwidth|Maximum number of concurrent connections|
        |-------------|------------------------------|-----------------|----------------------------------------|
        |Small I|1|20 Mbps|5000|
        |Small II|2|40 Mbps|10000|
        |Small III|3|60 Mbps|15000|
        |Medium I|5|100 Mbps|25000|
        |Medium II|8|160 Mbps|40000|
        |Medium III|10|200 Mbps|50000|

    -   **Bandwidth Type**: Select the type of basic bandwidth plan that you want to create. **Basic** is selected in this example.

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

    -   **Peak Bandwidth**: Specify the maximum bandwidth of the basic bandwidth plan. The value is set to **10 Mb** in this example.
3.  Click **Buy Now** and complete the payment.

4.  After you complete the payment, associate the basic bandwidth plan with the GA instance. For more information, see [Bind a basic bandwidth plan](/intl.en-US/User Guide/Basic bandwidth plans/Bind a basic bandwidth plan.md).

5.  Record the canonical name \(CNAME\) of the GA instance.

    To use GA to accelerate multiple domain names, you must log on to the DNS service platform and map the domain names that you want to accelerate to the CNAME of the GA instance. After you purchase a GA instance, the system automatically assigns a CNAME to the GA instance. We recommend that you record the CNAME. The CNAME is used when you modify the DNS record. You can check the CNAME on the **Instances** page.

    ![CNAME](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1213712161/p210811.png)


## Step 3: Add an acceleration area

After you purchase and configure a GA instance, you must add an acceleration area, specify the region where the clients are located, and then allocate bandwidth to the region. Then, you can use the GA instance to accelerate your services.

1.  On the **Instances** page, find the GA instance that you created in [Step 2: Purchase a GA service bundle](#section_4p1_rqj_37d) and click the instance ID.

2.  On the instance details page, click the **Acceleration Areas** tab. On the **China East** tab, click **Add Region**.

    For more information about acceleration areas and regions, see [Overview](/intl.en-US/User Guide/Acceleration areas/Overview.md).

3.  In the **Add Acceleration Area** dialog box, set the following parameters and click **OK**.

    -   **Regions**: Select the region where the clients that want to access the web application are located. **China \(Hangzhou\)** is selected in this example.
    -   **Bandwidth**: Specify the bandwidth to be allocated to the region. The value is set to **10** in this example. Unit: Mbit/s.
    -   **Internet Protocol**: Select the IP protocol that is used to connect the clients to GA. **IPv4** is selected in this example.

        After you add an acceleration region, GA assigns a public IPv4 address to the acceleration region. Clients can connect to this IP address for acceleration.


## Step 4: Add a listener

Listeners are used to monitor connection requests from clients. GA monitors connection requests received on the specified listener ports and forwards the requests to endpoints by using the specified protocol.

1.  On the instance details page, click the **Listeners** tab and then click **Add Listener**.

2.  On the **Configure Listener & Protocol** wizard page, set the following parameters for the listener:

    -   **Listener Name**: Enter a name for the listener.

        The name must be 2 to 128 characters in length, and can contain letters, digits, underscores \(\_\), and hyphens \(-\). The name must start with a letter.

    -   **Protocol**: Select a protocol for the listener. **HTTPS** is selected in this example.
    -   **Port Number**: Specify the listener port that is used to receive requests and forward the requests to endpoints. The value is set to **443** in this example.

        If you select the HTTP or HTTPS protocol, you can specify only one listener port. Valid values: 1 to 65499.

    -   **Client Affinity**: Select whether to enable client affinity. After client affinity is enabled, requests from the same client IP address are forwarded to the same endpoint if the web application is stateful. **Source IP Address** is selected in this example.
3.  Click **Next** to configure an SSL certificate.

4.  On the **Configure SSL Certificate** wizard page, set the following parameters for the SSL certificate:

    After you configure an SSL certificate, GA uses HTTPS to encrypt client requests and service data. This ensures the security of data transmission.

    **Note:** The SSL certificate is used to encrypt data that is transmitted from clients to GA. You can use the certificate that is installed on the backend servers to encrypt data that is transmitted from GA to the backend servers. The certificate that is used by the listener can be the same as the one that is installed on the backend servers.

    -   **Server Certificate**: Select the SSL certificate for which you applied.
    -   **Backend Port**: optional. Enter the port on which the backend servers provide services. This parameter is left empty in this example.
        -   If the listener port is the same as the port on which the backend servers provide services, we recommend that you specify the parameter.
        -   If the listener port is different from the port on which the backend servers provide services, we recommend that you leave this parameter empty. You can add a port mapping when you configure the endpoint group.
5.  Click **Next** to configure an endpoint group.


## Step 5: Configure an endpoint group

Each listener must be associated with an endpoint group. To associate an endpoint group with listeners, specify the regions to which you want to distribute requests. After you associate the listeners with an endpoint group, the listeners distribute requests to the optimal endpoints in the endpoint group based on forwarding rules.

You can configure default endpoint groups and virtual endpoint groups for HTTPS listeners. You can choose whether to use a default endpoint group or virtual endpoint group based on the following description.

-   Default endpoint group: You must configure a default endpoint group when you create a listener. The system automatically adds a default forwarding rule for the default endpoint group. Requests that do not meet the match conditions in custom forwarding rules are forwarded to the default endpoint group in the default forwarding rule.
-   Virtual endpoint group: After you create a listener, you can create a virtual endpoint group and add custom forwarding rules for the virtual endpoint group on the Configure Endpoint Group wizard page. GA forwards requests that meet the match conditions in the custom forwarding rules to the optimal endpoints in the associated endpoint group.

1.  Configure the default endpoint group.

    1.  On the **Configure Endpoint Group** wizard page, set the following parameters for the default endpoint group:

        ![Configure the default endpoint group](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1213712161/p210833.png)

        -   **Endpoint Group Name**: Enter a name for the endpoint group.

            The name must be 2 to 128 characters in length, and can contain letters, digits, underscores \(\_\), and hyphens \(-\). The name must start with a letter.

        -   **Region**: Select the region where you want to create the endpoint group. The region specifies where the backend servers are deployed.

            **China \(Beijing\)** is selected in this example.

        -   **Backend Service**: Specify whether the backend service is deployed on Alibaba Cloud.

            **Alibaba Cloud** is selected in this example.

        -   **Reserve Client IP**: Enable or disable the feature of client IP address preservation. By default, this feature is enabled for HTTPS listeners. For more information, see [Preserve client IP addresses](/intl.en-US/Deployment & Maintenance/Preserve client IP addresses.md).

            **Note:** You can enable the client IP address preservation feature if you are included in the whitelist. To apply to be added to the whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

        -   **Endpoint Configuration**
            -   **Backend Service Type**: **Alibaba Cloud Public IP Address** is selected in this example.
            -   **Backend Service**: Enter the IP address of the service that you want to accelerate. The public IP address of Server 2, 182.XX.XX.196, is entered in this example.
            -   **Weight**: Specify a weight for the endpoint. Valid values: 0 to 255. GA routes network traffic to each endpoint in proportion based on the weights of the endpoints.

                **Note:** If you change the weight of an endpoint to 0, GA stops distributing network traffic to the endpoint.

        -   **Backend Service Protocol**: Select the protocol that the backend servers use to provide web services. **HTTP** is selected in this example.
        -   **Port Mapping**: Add port mappings.

            The port that Server 2 uses to provide web services is different from the port on which GA listens. Therefore, you must add a port mapping to enable GA to forward requests that are received on port 443 to port 8443 on Server 2.

            -   **Listener Port**: Enter the port on which GA listens. The value is set to **443** in this example.
            -   **Endpoint Port**: Enter the port on which the backend servers provide web services. The value is set to **8443** in this example.
    2.  Click **Next** to check the configurations. After you confirm the configurations, click **Submit**.

2.  Configure a virtual endpoint group.

    1.  On the **Listeners** tab, find the listener that you want to manage and click the endpoint group ID in the **Default Endpoint Group ID/Name** column.

    2.  On the **Endpoint Group** page, click **Add Virtual Endpoint Group**.

    3.  In the **Add Virtual Endpoint Group** dialog box, set the following parameters and click **Create**.

        -   **Endpoint Group Name**: Enter a name for the endpoint group.

            The name must be 2 to 128 characters in length, and can contain letters, digits, underscores \(\_\), and hyphens \(-\). The name must start with a letter.

        -   **Region**: Select the region where you want to create the endpoint group. The region specifies where the backend servers are deployed.

            **China \(Beijing\)** is selected in this example.

        -   **Backend Service**: Specify whether the backend service is deployed on Alibaba Cloud.

            **Alibaba Cloud** is selected in this example.

        -   **Reserve Client IP**: Enable or disable the feature of client IP address preservation. By default, this feature is enabled for HTTPS listeners. For more information, see [Preserve client IP addresses](/intl.en-US/Deployment & Maintenance/Preserve client IP addresses.md).

            **Note:** You can enable the client IP address preservation feature if you are included in the whitelist. To apply to be added to the whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

        -   **Endpoint Configuration**
            -   **Backend Service Type**: **Alibaba Cloud Public IP Address** is selected in this example.
            -   **Backend Service**: Enter the IP address of the backend service that you want to accelerate. The public IP address of Server 1, 182.XX.XX.248, is entered in this example.
            -   **Weight**: Specify a weight for the endpoint. Valid values: 0 to 255. GA routes network traffic to each endpoint in proportion based on the weights of the endpoints.

                **Note:** If you change the weight of an endpoint to 0, GA stops distributing network traffic to the endpoint.

        -   **Backend Service Protocol**: Select the protocol that the backend servers use to provide web services. **HTTPS** is selected in this example.

            The port that Server 1 uses to provide web services is the same as the port on which GA listens. Therefore, GA forwards requests that are received on port 443 to port 443 that Server 1 uses. You do not need to add a port mapping in this case.


## Step 6: Add a forwarding rule

You can configure forwarding rules for HTTPS listeners. After you create an HTTPS listener, the system automatically creates a default forwarding rule that is used to forward requests to the default endpoint group. You can create a custom forwarding rule to forward requests to a virtual endpoint group.

GA forwards network traffic against forwarding rules based on domain names or paths. An HTTPS listener forwards requests that meet the match conditions in forwarding rules to the optimal endpoints in the associated endpoint groups. When an HTTPS listener receives requests, the HTTPS listener preferably forwards requests based on custom forwarding rules. If the requests do not match a custom forwarding rule, the HTTPS listener forwards the requests to the default endpoint group in the default forwarding rule.

To create a custom forwarding rule for the virtual endpoint group that is associated with Server 1, perform the following steps:

1.  On the listener details page, click **Forwarding Rule**.

2.  On the **Forwarding Rule** tab, click **Add Forwarding Rule**.

3.  In the **Add Forwarding Rule** section, set the following parameters to configure the forwarding rule:

    -   **Policy Name**: Enter a name for the forwarding rule.

        The name must be 2 to 128 characters in length, and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter.

    -   **If \(Matching All Conditions\)**: Select a match condition for the forwarding rule. **Domain Name** is selected in this example. After you select this option, enter the domain name to which you want to forward requests. www.xxxtest.icu is entered in this example.

        The domain name must be 3 to 128 characters in length and can contain letters, digits, underscores \(\_\), and periods \(.\). Supported wildcard characters are asterisks \(\*\) and question marks \(?\).

    -   **Forward to Virtual Endpoint Group**: Select an endpoint group. The virtual endpoint group that you created is selected in this example.
4.  Click **OK**.

    ![Forwarding rules](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1213712161/p210881.png)


## Step 7: Configure DNS settings

To forward requests from clients to GA, you must modify the DNS record to map the domain names that you want to accelerate to the CNAME of the GA instance. The following example shows how to modify the DNS record in the Alibaba Cloud DNS console.

**Note:** If you use the DNS resolution service that is provided by a third-party service provider, log on to the platform of the service provider and modify the DNS record for your web application.

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com).

2.  On the **Manage DNS** page, find the domain name that you want to manage, and click **Configure** in the **Actions** column.

3.  On the **Configure** page, find the DNS record that you want to modify, and click **Edit** in the **Actions** column.

4.  In the **Edit Record** dialog box, set **Type** to **CNAME** and set **Value** to the CNAME that is assigned to the GA instance in Step 2. For more information, see [Step 2: Purchase a GA service bundle](#section_4p1_rqj_37d).

    ![DNS](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1213712161/p210885.png)

5.  Click **OK**.


## Step 8: Verify the connectivity

Use both domain names to verify the connectivity to the web application that is deployed in the China \(Beijing\) region. In addition, check whether the service delivery is accelerated.

**Note:** The Linux operating system is used in this example. The command that is used to verify the connectivity varies based on the operating system that you use. For more information, see the user guide of your operating system.

1.  Use www.xxxtest.icu to access the web application and check whether the service delivery is accelerated.

    1.  To verify the connectivity to the web application, run the following command:

        ```
        curl https://<The domain name of the web application>
        ```

        ![Verify the connectivity to Server 1](../images/p210950.png "Verification result")

    2.  To verify data transmission, run the following command:

        ```
        curl -o /dev/null -s -w "time_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" "https://<The domain name of the web application>"
        ```

        In the request:

        -   time\_connect: The amount of time that it takes to establish a TCP connection.
        -   time\_starttransfer: The data transmission start time. It refers to the time period from when a client sends a request to when a backend server responds to the first byte.
        -   time\_total: The total connection time. It refers to the time period from when a client sends a connection request to when a backend server responds to the request.
        ![Before GA is used](../images/p212642.png "Data transmission before GA is used")

        ![After GA is used for Server 1](../images/p210954.png "Data transmission after GA is used")

        **Note:** The result varies based on the actual workloads.

2.  Use xxxtest.icu to access the web application and check whether the service delivery is accelerated.

    1.  To verify the connectivity to the web application, run the following command:

        ```
        curl https://<The domain name of the web application>
        ```

        ![Verify the connectivity to Server 2](../images/p210916.png "Verification result")

    2.  To verify data transmission, run the following command:

        ```
        curl -o /dev/null -s -w "time_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" "https://<The domain name of the web application>"
        ```

        In the request:

        -   time\_connect: The amount of time that it takes to establish a TCP connection.
        -   time\_starttransfer: The data transmission start time. It refers to the time period from when a client sends a request to when a backend server responds to the first byte.
        -   time\_total: The total connection time. It refers to the time period from when a client sends a connection request to when a backend server responds to the request.
        ![After GA is used for Server 2](../images/p210938.png "Data transmission before GA is used")

        ![Before GA is used for Server 2](../images/p210936.png "Data transmission after GA is used")

        **Note:** The result varies based on the actual workloads.



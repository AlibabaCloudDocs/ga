# GA interacts with WAF and GTM to accelerate ERP applications

Global Accelerator \(GA\) can interact with Web Application Firewall \(WAF\) and Global Traffic Manager \(GTM\) to accelerate enterprise resource planning \(ERP\) applications. Based on high-bandwidth BGP lines, and the global transmission network of Alibaba, GA allows you to deploy your workloads across regions. Users can connect to the nearest access point over the global network for content delivery acceleration. WAF, a security service empowered by big data technologies of Alibaba Cloud Security, allows you to ensure the security of content delivery. This is a highly-secure solution for a cross-region acceleration of enterprise ERP management systems.

You have created an Alibaba Cloud account. If you do not have an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).

A company deploys an ERP system on Alibaba Cloud in Germany \(Frankfurt\). The backend servers provide external services through two Elastic IP addresses \(EIPs\). The forwarding port is port 9000. Most of the ERP system users are in China \(Hong Kong\) and Singapore. Several issues such as data transmission latency or logon timeout may occur when users connect to the ERP system across regions. The existing ERP service architecture cannot be dynamically modified and is vulnerable to various web application attacks. These issues severely affect the security and availability of the ERP system. To solve these issues, you can use GA to interact with WAF and GTM. When the access point nearest to the users receives requests delivered across regions, GA uses WAF to filter out malicious network traffic and uses GTM to implement intelligent traffic distribution. This improves the security, availability, and communication efficiency between the users and the ERP system in different regions.

![ERP architecture 3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9311485951/p100872.png)

As shown in the preceding figure, you can create a GA instance, specify China \(Hong Kong\) and Singapore as the acceleration regions, and deploy WAF and GTM. WAF can detect and filter out malicious requests based on the specified protection policies, and allow only valid requests to reach the origin server. GTM can forward network traffic destined for the ERP system based on the specified access policy, perform real-time health checks on the origin server of the ERP system, and implement fault isolation or failover based on the health check results. When users in China \(Hong Kong\) and Singapore send requests to the ERP system, the access point nearest to the users receives the requests and distributes them to the GA network. WAF filters network traffic. GTM then forwards the network traffic to the origin server and performs fault isolation or traffic redirection based on the health check results. This solution ensures high security and availability of the ERP system and reduces the network latency.

## Procedure

![Configuration process](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9311485951/p100009.png)

## Step 1: Create a GTM instance

GTM allows you to balance a large number of concurrent workloads, perform health checks on application services, and implement fault isolation and failovers based on the health check results.

To create a GTM instance, follow these steps:

**Note:** If you are using GTM for the first time, you must authorize the GTM service to access your cloud resources. This allows GTM to access your alert groups that are created in CloudMonitor. For more information, see [Cloud resource access authorization](https://www.alibabacloud.com/help/doc-detail/87304.htm).

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com).

2.  In the left-side navigation pane, click **Global Traffic Manager**.

3.  On the **Global Traffic Manager** page, click **Create Instance**.

4.  On the buy page, set the following parameters for the GTM instance:

    1.  **Version**: By default, **Standard Edition** is selected and cannot be changed.

        GTM Standard Edition supports the following features:

        -   Health checks on IP addresses of application services: `ping`, `tcp`, and `http(s)`.
        -   DNS failover: switches your application workloads to the secondary server to avoid service interruption and implements fault isolation.
        -   GeoDNS: switches your application workloads to specified IP addresses based on geo-locations of the users.
        -   WRR: weighted round-robin load balancing policy.
    2.  **Quantity**: The number of GTM instances that you want to purchase.

    3.  **Service Time**: The service duration of the GTM instance.

5.  Click **Buy Now** to settle the payment.


## Step 2: Configure an access policy

An access policy defines address pools for which requests from different networks or regions are resolved. With the access policy, users can connect to the nearest access point and your workloads can be automatically switched between the primary and secondary servers for fast failover.

To configure an access policy for the GTM instance, follow these steps:

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com).

2.  In the left-side navigation pane, click **Global Traffic Manager**.

3.  On the **Global Traffic Manager** page, find the GTM instance that you want to manage, and click **Configure** in the **Actions** column.

4.  In the **Select Configuration Method** dialog box, select **Quick Start**.

5.  On the **Access Policy Configurations** wizard page, set the following parameters.

    1.  **Policy Name**: Enter the name of the access policy.

    2.  **DNS Request Sources**: Select a request source.

        After you specify a region as the request source, when users in this region send requests to the application, GMT distributes the requests to the specified origin server address pool. Select **Global** in this topic.

        **Note:**

        -   If you configure only one access policy, you must select **Global**.
        -   If you configure multiple access policies, you must specify **Global** as one of your DNS request sources. Otherwise, the application may not be accessible in some regions.
        -   You cannot select the options that have been used in other access policies. These options are not available.
        -   If multiple access policies exist, you can only specify **ISP** or **Mainland China** as DNS request source.
    3.  **Default Address Pool**: Select the default address pool.

        The default address pool is the origin server address pool to which GTM forwards normal network traffic.

        In this topic, click **+ Add Address Pool**, add the address of ERP Server A in Germany \(Frankfurt\) to the default address pool, enable HTTP health checks, and then select the default address pool. For more information about how to configure HTTP\(S\) health checks, see [HTTP\(S\) health check](https://www.alibabacloud.com/help/zh/doc-detail/87313.htm?spm=a2c63.p38356.b99.24.1db8579a8uvoSP). For more information about how to configure the address pool, see [Configure an address pool](https://www.alibabacloud.com/help/zh/doc-detail/87309.htm?spm=a2c63.p38356.b99.22.60314ffdDiBZB3).

    4.  **Alternative Address Pool**: Select an alternative address pool.

        An alternative address pool is an IP address pool of origin servers to which GTM directs requests if the servers in the default address pool are down.

        In this topic, click **+ Add Address Pool**, add the address of ERP Server B in Germany \(Frankfurt\) to the alternative address pool, enable HTTP health checks, and then select the alternative address pool. For more information about how to configure health checks, see [HTTP\(S\) health check](https://www.alibabacloud.com/help/zh/doc-detail/87313.htm?spm=a2c63.p38356.b99.24.1db8579a8uvoSP). For more information about how to configure the address pool, see [Configure an address pool](https://www.alibabacloud.com/help/zh/doc-detail/87309.htm?spm=a2c63.p38356.b99.22.60314ffdDiBZB3).

6.  Click **Next**.


## Step 3: Configure basic information

After you configure the access policy, you must specify the basic information of the GTM instance, including the primary domain, type of the Canonical Name \(CNAME\) address of your application, load balancing policies, global time-to-live \(TTL\), and alert groups.

1.  On the **Basic Information** wizard page, set the following parameters.

    1.  **Instance Name**: Enter an instance name.

        An instance name is used to identify the application service for which the instance is used.

    2.  **Primary Domain**: Enter the domain name of your application. Enter **www.example.de** in this topic.

    3.  **CNAME Access Domain Name**: Select the type of the CNAME address of your application.

        -   **Assigned Access Domain Name**: Select this option if the IP address pool only contains Alibaba Cloud IP addresses or IP addresses outside China.
        -   **Custom Access Domain Name**: Select this option if the IP address pool contains IP addresses of on-premises data centers.
        In this topic, the IP addresses of the origin servers are Elastic IP addresses. Select **Assigned Access Domain Name**.

    4.  **Balance Policy**: Select a load balancing policy for GTM.

        -   **Round Robin**: The default policy. If you select this policy, GTM distributes network traffic to IP addresses in the IP address pool on a rotation.
        -   **Weighted Round Robin**: If users are distributed across the country or around the world, you can select this policy to distribute network traffic based on the capacity of each origin server in the pool. This policy allows the system to distribute network traffic based on weights. You can set a weight for each IP address. Alibaba Cloud DNS returns query results based on the predefined weights.
        Select **Round Robin** in this topic.

    5.  **Global TTL**: The TTL value of the IP address that is mapped to the specified domain name. In this topic, select **1 minute\(s\)**.

        You can use GTM to manage network traffic based on domain names. The global TTL specifies the TTL of the IP address information cached in the DNS system of the Internet Service Provider \(ISP\). By default, the global TTL is set to 1 minute. If you use a custom domain name, the global TTL must be the same as the minimum TTL supported by the Cloud DNS plan of the custom domain name.

    6.  **Alert Group**: Specify a contact group to receive notifications when an error occurs.

        **Note:**

        -   If you have not configured an alert group, log on to the CloudMonitor console and add an alert group. For more information, see [t6224.md\#](/intl.en-US/Alarm service/Alert contacts/Delete an alert contact or alert group.md).
        -   If you have configured an alert group but want to configure the basic information as a RAM user, you must log on with your Alibaba Cloud account and authorize the RAM user. After authorization, you can log on as a RAM user to retrieve the alert group information.
2.  Click **Complete**.


After you configure the basic information, the system automatically allocates a CNAME address. Requests destined for the CNAME address are resolved to the IP address of the origin server.

![cname](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p99619.png)

## Step 4: Activate the WAF service

WAF is empowered by big data technologies of Alibaba Cloud Security. WAF helps you defend against common web attacks such as SQL injections, cross-site scripting \(XSS\), web shells, Trojans, and unauthorized downloads, and HTTP flood attacks. WAF protects your web resources from exposure and ensures the security and availability of your website.

1.  Enter the [WAF product page](https://www.alibabacloud.com/zh/product/waf) on the Alibaba Cloud official website, and then log on with your Alibaba Cloud account.

2.  Click **Buy Now**.

3.  On the buy page, set the following parameters.

    1.  **Region**: Select the region where the WAF instance is located.

        In this topic, network traffic is forwarded through WAF over the GA network. Select **Overseas Region**.

    2.  **Plan**: Select the version of WAF service to be activated.

        Different WAF instance types support different business scales and protection features. For more information, see [Editions and features](/intl.en-US/Product Introduction/Editions and features.md) Select **Enterprise** in this topic.

    3.  **Extra Domain**: Specify the number of additional domains to be activated.

        If you want to add multiple domains \(or more than 10 subdomains\) to WAF, you can activate additional domains. For more information, see [Additional domain](/intl.en-US/Billing and Service Activation/Subscription/Extra domain quota.md). Do not purchase any additional domains in this topic.

    4.  **Exclusive IP**: Specify the number of exclusive IP addresses to be purchased.

        You can purchase an exclusive WAF IP address if your domain name needs WAF protection through an exclusive IP address. For more information, see [Exclusive IP](/intl.en-US/Billing and Service Activation/Subscription/Exclusive IP addresses.md). You do not need to purchase exclusive IP addresses in this topic.

    5.  **Extra Traffic**: Specify the size of the bandwidth extension plan to be purchased. Unit: Mbit/s.

        If the total bandwidth of your websites exceeds the service bandwidth of WAF, you can purchase the bandwidth extension plan. For more information, see [Bandwidth extension plan](/intl.en-US/Billing and Service Activation/Subscription/Extra bandwidth.md). Do not purchase a bandwidth extension plan in this topic.

    6.  **GSLB**: Enable or disable Global Server Load Balancing \(GSLB\).

        GSLB uses the multi-node resilience technology. It distributes network traffic based on multiple nodes or lines to implement disaster recovery and improve service reliability. Select **No** in this topic.

    7.  **Log Service**: Enable or disable Log Service.

        Log Service retrieves log data from WAF in real time and then stores the data in Logstores. You can query and analyze the log data, and generate analytics reports online. Select **No** in this topic.

    8.  **Bot Manager**: Enable or disable the Bot Manager feature.

        To mitigate security threats caused by bot traffic, you can purchase Bot Manager. For more information, see [Set a bot threat intelligence rule](/intl.en-US/Website Protection Settings/Bot management/Set a bot threat intelligence rule.md) and [Configure the allowed crawlers function](/intl.en-US/Website Protection Settings/Bot management/Configure the allowed crawlers function.md). Select **No** in this topic.

    9.  **Mobile App Protection**: Enable or disable mobile application protection.

        You can enable the Mobile App Protection module if your business supports native applications and you have security needs for your business, such as trusted communications and prevention of abusing bot scripts. For more information, see [Configure application protection](/intl.en-US/Website Protection Settings/Bot management/Application protection/Configure application protection.md). Select **No** in this topic.

    10. **Service Time**: Select the validity period of the WAF service.

4.  Click **Buy Now** to settle the payment.


## Step 5: Add website configurations

After you activate the WAF service, you must configure the forwarding rule of websites protected by WAF.

To forward network traffic of the protected domain name to WAF in DNS proxy mode, follow these steps:

1.  Log on to [WAF console](https://yundun.console.aliyun.com/?p=waf).

2.  On the top of the page, select the region of the WAF instance that you want to manage. Select **International**.

3.  In the left-side navigation pane, choose **Asset Center** \> **Website Access**.

4.  On the **Website Access** page, click **Add Domain Name**.

5.  On the **Add Domain Name** page, click **Manually Add Other Websites**.

    **Note:** The **Add Domain Name** page appears only when a qualified domain name exists. If **Add Domain Name** does not appear, skip this step.

6.  On the **Fill in website information** page, set the following parameters.

    1.  **Domain Name**: Enter the domain name for which you want to enable WAF protection. Enter **www.example.de** in this topic.

        **Note:**

        -   Wildcard domain names are supported, such as `*.aliyun.com`. WAF automatically matches all subdomains against the specified wildcard domain.
        -   If you enter a wildcard domain and a precise domain name, such as `*.aliyun.com` and `www.aliyun.com`, the forwarding rules and protection policies of the exact domain name prevail over those of the wildcard domain.
        -   The .edu domain names are not supported. To use a .edu domain name, submit a ticket to request technical support.
    2.  **Protocol Type**: Select the protocol that your website supports. Select **HTTP** in this topic.

        **Note:**

        -   If your website supports HTTPS, select HTTPS, and upload the certificate and the private key file after you set website parameters. For more information, see [Upload HTTPS certificate files]().
        -   After you select HTTPS, click **Advanced Settings** to enable the HTTP force redirect and HTTP back-to-origin features to accelerate your applications. For more information, see [Enable HTTPS advanced settings]().
        -   To enable protection for **HTTP 2.0** requests, make sure the following conditions are met:
            -   You have upgraded your WAF instance to the Business or Enterprise edition.
            -   You have selected **HTTPS**.
    3.  **Server Address**: Select a server address type and enter the address of the origin server.

        Both **IP** and **Other address** formats are supported. After you connect your website to WAF, WAF redirects filtered requests to the specified address. Select **Other Addresses** and enter the CNAME address generated for the GTM instance. For more information, see [Step 3: Configure basic information](#section_dy5_qot_e61).

    4.  **Server Port**: Configure the protocol port of the website.

        WAF uses the specified ports to receive and forward user traffic for your website. The network traffic destined for the website domain name is only forwarded through the specified service ports. WAF does not forward traffic received on unspecified ports to the origin server. Therefore, no security threats are posed on the origin server if you enable these unspecified ports or these ports have vulnerabilities.

        **Note:** Make sure that the protocol and port that you have specified in WAF are the same as those of the origin server whose IP address is specified as the server address. Port mapping is not supported.

        Enter the custom port **9000** in this topic.

        **Note:** By default, WAF supports the following ports: HTTP ports 80 and 8080, and HTTPS ports 443 and 8443. WAF instances of the Business and Enterprise editions support more non-standard ports, and have limits on the total number of ports used by the protected domain name. For more information, see [View the ports supported by WAF](/intl.en-US/Website Access/View the ports supported by WAF.md).

    5.  **Whether a Layer 7 proxy, such as Anti-DDoS Pro and CDN, is enabled**: Select Yes or No based on the actual status of your website. Select **No** in this topic.

    6.  **Load Balancing Algorithm**: If multiple origin server IP addresses are specified, select **IP hash** or **Round-robin**. WAF distributes requests among these servers based on the specified algorithm for load balancing.

    7.  **Traffic Labeling**: Enter an unused **Header Field Name** and specify a **Header Field Value** to label the web requests that are redirected to the origin server through WAF. WAF adds the specified header field to the filtered requests. This enables your origin server to identify the requests redirected through WAF.

        **Note:** If a request already contains the specified header field, WAF overwrites the original field value with the specified value.

7.  Click **Next**. On the **Modify DNS Resolution Settings** page, click **Copy CNAME** to record the CNAME address allocated by WAF. This enables the WAF to receive inbound traffic.

    ![WebCNAME](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1553958951/p99553.png)

8.  Click **Next**. Click **Complete, and return to the website list**.

    **Note:** If you have enabled a third-party firewall for your server, disable the firewall or add the WAF IP address in the following figure to the whitelist of the enabled firewall. In this way, the firewall does not block traffic from WAF. If you are not using a third-party firewall, ignore the information in the following figure.

    ![WAF IP address](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0351995951/p99822.png)


## Step 6: Create a GA instance

GA is a high-availability and high-performance network acceleration service for global users. Based on the high-quality BGP bandwidth and global network infrastructure of Alibaba, GA allows service providers to deploy their applications across regions and users to connect to the nearest endpoints for content delivery acceleration. This can reduce network issues, such as network latency, network jitter, and packet loss.

To create a GA instance, follow these steps:

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, click **Create Instance**.

3.  On the buy page, set the required parameters, and click **Buy Now**.

    1.  Select the specification of the GA instance that you want to purchase. Select **Small Ⅱ** in this topic.

        GA supports the following types of instance specifications: Small I, Small II, Small III, Medium I, Medium II, and Medium III. The acceleration performance can vary based on the instance specification.

        |Instance specification|Number of acceleration regions|Peak bandwidth|Maximum number of concurrent connections|
        |----------------------|------------------------------|--------------|----------------------------------------|
        |Small I|1|20 Mbit/s|5,000|
        |Small II|2|40 Mbit/s|10,000|
        |Small III|3|60 Mbit/s|15,000|
        |Medium I|5|100 Mbit/s|25,000|
        |Medium II|8|160 Mbit/s|40,000|
        |Medium III|10|200 Mbit/s|50,000|

    2.  Set the subscription duration of the GA instance.

    After you create the instance, the system automatically allocates a CNAME address. User requests destined for the CNAME address are resolved to the IP address of the origin server. Record the CNAME address for DNS resolution use.

    ![CNAME](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9311485951/p100877.png)


## Step 7: Purchase and bind a basic bandwidth plan

A basic bandwidth plan provides bandwidth resources for data transmission over the global network and the internal network of Alibaba Cloud. To achieve global acceleration, you need to purchase a basic bandwidth plan and bind the basic bandwidth plan to a GA instance.

To purchase and bind a basic bandwidth plan to a GA instance, follow these steps:

1.  On the **Instances** page, click **Purchase Basic Bandwidth Plan**.

2.  On the buy page, configure the required parameters, and click **Buy Now** to settle the payment.

    1.  **Bandwidth Type**: Select the type of the basic bandwidth plan. Select **Premium** in this topic.

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

    2.  **Peak Bandwidth**: Select the peak bandwidth of the basic bandwidth plan. Select **20 Mb** in this topic.

    3.  **Duration**: Select the duration of the basic bandwidth plan.

3.  Return to the **Instances** page, and click the ID of the GA instance that you have created.

4.  On the page that appears, click the **Bandwidth Manage** tab.

5.  In the **Basic Bandwidth Plan** field, find the target plan that you want to manage, and click **Bind** in the **Actions** column.

    The basic bandwidth plan is now in the **Bound** state.

    ![Bandwidth plan of 20 Mbit/s](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9311485951/p100432.png)


## Step 8: Add an acceleration area

After you purchase a bandwidth plan, you must add one or more acceleration areas where end users are located, and allocate the acceleration bandwidth to these areas.

To add an acceleration area, follow these steps:

1.  On the **Instances** page, click the ID of the GA instance that you have created in step 6.

2.  On the instance details page, click the **Acceleration Areas** tab. Then, click **Add Acceleration Area**.

3.  In the **Add Acceleration Area** dialog box, set the required parameters as follows, and click **OK**.

    1.  **Acceleration Area**: Select the area where the GA service is deployed. In this topic, select **Asia Pacific**.

    2.  **Regions**: Select the regions where the end users are located. Select **Singapore**.

    3.  **Bandwidth**: Specify the amount of bandwidth that you want to allocate to the region. In this topic, select **10** Mbps.

    4.  Click **+ Add**, select **China \(Hong Kong\)** as the acceleration area, and assign 10 Mbit/s bandwidth to the China \(Hong Kong\) region.


After the acceleration area is added, Global Accelerator assigns an accelerated IP address to each region in the acceleration area for network acceleration purpose.

![Acceleration area 2.1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0411485951/p100880.png)

## Step 9: Create a listener

A listener monitors inbound connection requests from clients. GA forwards connection requests to the origin server based on the specified protocol and port.

To add a listener to a GA instance, follow these steps:

1.  On the **Instances** page, click the ID of the GA instance that is created in Step 1.

2.  On the instance details page, click the **Listeners** tab. Then, click **Add Listener**.

3.  On the **Configure Listener & Protocol** page, configure the listener:

    1.  **Listener Name**: Enter a name for the listener to be created. The name must be 2 to 128 characters in length and can contain letters, Chinese characters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter or a Chinese character.

    2.  **Protocol**: Select a protocol for the listener. Select **TCP** in this topic.

    3.  **Port Number**: Enter a port or port range for receiving and forwarding requests to the endpoints. Valid values: 1 to 65499. Enter **9000** in this topic.

    4.  **Client Affinity**: Select whether to enable client affinity. When client affinity is enabled, requests from a specific source \(client\) IP address are always routed to the same endpoint. Select **Source IP Address** in this topic.

    ![Listeners](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1615588951/p95540.png)

4.  Click **Next** to configure an endpoint group.


## Step 10: Configure an endpoint group

Each listener is associated with an endpoint group. You can associate an endpoint group with a listener by specifying the region to which you want to distribute network traffic. After the association is complete, traffic is distributed to the optimal endpoints in the associated endpoint group.

To create an endpoint group, follow these steps:

1.  **Endpoint Group Name**: Enter a name for the endpoint group.

2.  Select the region where the endpoint group is located, that is, the region where the target server is located.

    Select **Germany** in this topic.

3.  Select whether to deploy the backend service on Alibaba Cloud or non-Alibaba Cloud. Select **non-Alibaba Cloud**.

4.  Select whether to enable or disable client IP address reservation in the specified region. After this feature is enabled, backend servers can obtain the source IP addresses of clients. Disable this feature for the origin server in this topic.

    **Note:** To make client IP address reservation available for use in the whitelist, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

5.  Set the following parameters of endpoints:

    1.  **Backend Service Type**: Select **Custom Domain Name** from the drop-down list.

    2.  **Backend Service**: Enter the domain name of the backend server that you want to accelerate. Enter the domain name of CNAME that is generated by WAF in this topic. For more information, see [Step 5: Add website configurations](#section_m41_rbu_wk8).

    3.  **Weight**: Enter a number from 0 to 255 to set a weight for the endpoint. GA distributes network traffic to endpoints based on the predefined weights of the endpoints.

        **Note:** Caution: If the weight of an endpoint is set to 0, GA stops distributing traffic to the endpoint.

        ![The Endpoint Group in Germany (Frankfurt)](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0411485951/p99846.png)

6.  Click **Next** to view the configurations. After confirmation, click **Next**.


## Step 11: Connect workloads to GA

After you complete the GA configurations, you must modify the DNS resolution settings to map the website domain names to the CNAME assigned by GA, and redirect the inbound traffic to GA.

**Note:** If you use a third-party DNS service, log on to the system of the DNS service provider to modify the DNS record.

To connect your workloads to GA, follow these steps:

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com).

2.  On the **Manage DNS** page, find the target domain name, and click **Configure** in the **Actions** column.

3.  On the **Configure** page, find the DNS record, and click **Edit** in the **Actions** column.

4.  In the **Edit Record** dialog box, edit the host record.

    1.  **Type**: Select **CNAME**.

    2.  **Record Value**: Change the value to the CNAME address allocated by GA. For more information, see [Step 6: Create a GA instance](#section_t7m_w59_1kb).

    3.  Keep the other settings unchanged.

    ![Edit the record](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9197449951/p45868.png)

5.  Click **OK**.


## Step 12: Verify the settings

To verify the settings of acceleration and protection after Global Accelerator interacts with WAF and GTM, follow these steps:

1.  Open a web browser on a client located in the region of an access point, such as China \(Hong Kong\) or Singapore.

2.  Enter the domain name of the ERP system to access the ERP system services deployed in Germany \(Frankfurt\).

    After testing, you can access the ERP system services deployed in Germany \(Frankfurt\) with the domain name of the ERP management system.

    ![Verify the settings](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1615588951/p96014.png)

3.  Launch the Command Prompt on your computer in the Germany \(Frankfurt\) or Singapore region in this topic.

4.  Run the following commands to check the latency of data packet transmission.

    `curl -o /dev/null -s -w "time_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" "http[s]://<ERP system domain name>[:<port>]"`

    In the request:

    -   time\_connect: The amount of time that it takes to establish a TCP connection.
    -   time\_starttransfer: The data transmission start time. It refers to the time period from when a client sends a request to when a backend server responds to the first byte.
    -   time\_total: The total connection time. It refers to the time period from when a client sends a connection request to when a backend server responds to the request.
    The test result shows that GA has reduced the latency of data transmission between the ERP system in Germany \(Frankfurt\) and users in Hong Kong and Singapore.

    ![Data transmission before GA is used](../images/p100908.png "The latency of data transmission before GA is used")

    ![Data transmission after GA is used](../images/p100911.png "The latency of data transmission after GA is used")

    **Note:** The acceleration performance after GA interacts with WAF varies based on your workloads.



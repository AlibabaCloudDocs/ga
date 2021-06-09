# Accelerate domain names hosted outside mainland China.

Global Accelerator \(GA\) provides web service providers with a cross-border acceleration solution. GA is integrated with Anti-DDoS Pro and Web Application Firewall \(WAF\) to defend against distributed denial-of-service \(DDoS\) attacks and web attacks based on high-bandwidth BGP lines and the global transmission network of Alibaba Cloud. Global Traffic Manager \(GTM\) can interact with GA to conduct fault isolation or traffic failovers.

An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account,[create one](https://account.alibabacloud.com/register/intl_register.htm).

A web service is deployed on Alibaba Cloud in US \(Silicon Valley\). The origin servers are four Elastic Compute Service \(ECS\) instances associated with Alibaba Cloud elastic IP addresses \(EIPs\). The web service is deployed on the ECS instances with the domain name www.example.us that is registered outside mainland China. The forwarding port is TCP port 9000. The web service may face the following issue:

-   The domain name of the web service is registered outside mainland China and cannot be hosted on servers in mainland China. However, the majority of users are located in mainland China.
-   The web service frequently receives attacks and DDoS attacks, which severely affect the security and availability of the web service.
-   The cross-border network is unstable. Network issues, such as network latency, network jitter, and packet loss, may frequently occur and degrade the performance of the web service.
-   The origin servers are unstable and services may be interrupted.

![Cross-border acceleration](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1553958951/p99440.png)

The preceding figure shows how to deploy a GA service to interact with Anti-DDoS Pro, WAF, and GTM. This solution allows you to resolve the preceding issues.

-   Anti-DDoS Pro can defend against DDoS attacks.

    The Anti-DDoS Pro service is deployed in tap mode. Anti-DDoS Pro is triggered only in certain scenarios. This ensures service quality when no DDoS attack occurs and enhances protection when DDoS attacks are detected.

-   GA can speed up content delivery between the origin servers and users in accelerated areas.

    Users in mainland China send requests to the Alibaba Cloud acceleration network from the access points in the China \(Hong Kong\) region. The system forwards the requests to the origin servers in US \(Silicon Valley\) by using intelligent routing and automatic network traffic distribution.

-   WAF can protect your website against a variety of web attacks.

    WAF can detect and block malicious Internet traffic. Non-malicious network traffic is forwarded to the IP addresses of the origin servers. WAF ensures security, stability, and availability of the origin servers.

-   GTM can be used to isolate malfunctioned servers or switch network traffic among multiple origin servers.
    -   When the primary server group is working as expected, all user traffic is forwarded to the primary server group.
    -   When the primary server group is unavailable, traffic is directed to the secondary server group. After the primary server recovers, traffic is switched back to the primary server group.

## Configuration procedure

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1553958951/p99957.png)

## Step 1: Create a GTM instance

GTM is a traffic management service that allows you to manage network traffic from clients in a fine-grained way.

To create a GTM instance, perform the following steps:

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com).

2.  In the left-side navigation pane, click **Global Traffic Manager**.

3.  On the **Global Traffic Manager** page, click **Create Instance**.

4.  On the buy page, set the following parameters.

    1.  **Version**: By default, **Standard Edition** is selected and cannot be changed.

        The Standard Edition plan supports the following features:

        -   Health checks on IP addresses of application services.
        -   Intelligent DNS resolution of domain names based on areas.
        -   Disaster recovery policies to implement DNS resolution service failovers.
        -   Load balancing policies based on custom weights.
    2.  **Quantity**: The number of GTM instances that you want to purchase.

    3.  **Service Time**: The service duration of the GTM instance.

5.  Click **Buy Now** and complete the payment.


## Step 2: Configure an access policy

Access policies allow GA to forward requests from different access points to different origin servers. You can also specify secondary origin servers to meet your business demands.

To configure an access policy for GTM, perform the following steps:

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com).

2.  In the left-side navigation pane, click **Global Traffic Manager**.

3.  On the **Global Traffic Manager** page, find the GTM instance that you want to manage, click **Configure** in the **Actions** column.

4.  In the **Select Configuration Method** dialog box, select **Quick Start**.

5.  In the **Access Policy Configurations** wizard, set the following parameters:

    1.  **Policy Name**: Enter a name for the access policy.

    2.  **DNS Request Sources**: Select a request source.

        After you specify a region as the request source, when users in this region send requests to the service, GTM distributes the requests to the specified origin server address pool. **Global** is selected in this example.

    3.  **Default Address Pool**: Select the default address pool.

        By default, GTM forwards user traffic to the IP addresses of the origin servers in the default address pool.

        Click **+ New Address Pool** and add the IP addresses of Origin Server 1 and Origin Server 2 in the US \(Silicon Valley\) region to the address pool. Enable HTTP health checks, and specify the address pool as the default address pool. For more information about how to configure health checks,see [TCP health checks](https://www.alibabacloud.com/help/zh/doc-detail/87312.htm).

    4.  **Alternative Address Pool**: Select an alternative address pool.

        An alternative address pool is an IP address pool that contains IP addresses of secondary origin servers. GTM forwards requests to the secondary origin servers when the servers in the default address pool are unavailable.

        Click **+ New Address Pool** and add Origin Server 3 and Origin Server 4 in the US \(Silicon Valley\) region to the alternative address pool. Configure health checks, and specify the address pool as an alternative address pool. For more information about how to configure health checks,see [TCP health checks](https://www.alibabacloud.com/help/zh/doc-detail/87312.htm).

6.  Click **Next**.


## Step 3: Configure basic information

After you configure the access policies, you must specify the basic information of the GTM instance. The information includes the domain name, CNAME, load balancing policy, global time-to-live \(TTL\) value, and alert group. To configure the basic information for the GTM instance, perform the following steps:

To configure the basic information for GTM, perform the following steps:

1.  In the **Basic Information** wizard, set the following parameters.

    1.  **Instance Name**: Enter an instance name.

        The instance name is used to identify the application service that runs on the instance.

    2.  **Primary Domain**: Enter the domain name that clients need to access. **www.example.us** is used in this example.

    3.  **CNAME Access Domain Name**: Specify the type of the CNAME for the domain name.

        -   **Assigned Access Domain Name**: Select this option if the IP address pool contains only Alibaba Cloud IP addresses or IP addresses outside mainland China.
        -   **Custom Access Domain Name**: Select this option if the IP address pool contains IP addresses of data centers.
        In this example, the IP addresses of the origin servers are EIPs. Therefore, select Assigned Access Domain Name.

    4.  **Balance Policy**: Select a load balancing policy for GTM.

        -   **Round Robin**: Network traffic is equally distributed when the domain name is resolved to multiple IP addresses.
        -   **Weighted Round Robin**: Network traffic is distributed based on weights when the domain name is resolved to multiple IP addresses.
        **Round Robin** is selected in this example.

    5.  **Global TTL**: The validity period of the IP address to which the domain name is resolved. **1 minute\(s\)** is selected in this example.

        You can use GTM to manage network traffic based on domain names. Global TTL specifies the TTL of the IP address that is cached in the DNS system of the Internet service provider \(ISP\). By default, the global TTL is set to 1 minute. If you use a custom domain name, the global TTL must be the same as the minimum TTL supported by the Cloud DNS plan of the custom domain name.

    6.  **Alert Group**: the contact group to which a notification is sent when an exception is detected in your workloads.

        **Note:**

        -   If you have not configured an alert group, log on to the CloudMonitor console and add a contact group. For more information, see [t6224.md\#](/intl.en-US/Alarm service/Alert contacts/Delete an alert contact or alert group.md).
        -   If you have configured a contact group but want to configure the basic information as a Resource Access Management \(RAM\) user, you must first use your Alibaba Cloud account to authorize the RAM user. After the RAM user is authorized, you can log on as a RAM user to read messages sent to the alert group.
2.  Click **Complete**.


After you configure the basic information, the system automatically allocates a CNAME to the domain name. User requests destined for the CNAME are resolved to the IP address of the scheduled origin server.

![cname](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p99619.png)

## Step 4: Activate WAF

WAF provides security protection based on big data technologies of Alibaba Cloud Security. It defends against common attacks defined by Open Web Application Security Project \(OWASP\), including SQL injections, Cross-Site Scripting \(XSS\) attacks, exploits of vulnerabilities in web server plug-ins, Trojan uploads, and unauthorized access to core resources. WAF blocks volumetric HTTP flood attacks to prevent the exposure of website assets and data, and to ensure website security and availability.

This step describes how to purchase a subscription WAF instance.

1.  Go to the Alibaba Cloud International siteand log on to the [WAF page](https://www.alibabacloud.com/zh/product/waf) with your Alibaba Cloud account.

2.  Click **Buy Now**.

3.  On the **Web Application Firewall** page, set the following parameters:

    1.  **Region**: Select the region where the WAF instance is deployed.

        In this example, the WAF instance is located in the US \(Silicon Valley\) region. Therefore, **International** is selected.

    2.  **Plan**: Select the edition of WAF that you want to activate.

        Different WAF editions are applicable to various business scales and provide different protection features. For more information, see [Editions and features](/intl.en-US/Product Introduction/Editions and features.md). **Enterprise** is selected in this example.

    3.  **Extra Domain**: Specify the number of additional domain names.

        If you want to add multiple domains or more than 10 subdomains to WAF, you can purchase additional domain names. For more information, see [Additional domain names](/intl.en-US/Pricing/Subscription/Extra domain quota.md). Additional domain names are not purchased in this example.

    4.  **Exclusive IP**: Specify the number of exclusive IP addresses.

        You can purchase an exclusive IP address when your domain name needs WAF protection through an exclusive IP address. For more information, see [Exclusive IP addresses](/intl.en-US/Pricing/Subscription/Exclusive IP addresses.md). Exclusive IP addresses are not purchased in this example.

    5.  **Extra Traffic**: Specify the additional bandwidth value. Unit: Mbit/s.

        If you require additional bandwidth, you can purchase an additional bandwidth plan. For more information, see [additional bandwidth plans](/intl.en-US/Pricing/Subscription/Extra bandwidth.md). **100Mbps** is selected in this example.

    6.  **GSLB**: Select whether to enable Global Server Load Balancing \(GSLB\).

        GSLB uses the multi-node resilience technology. It supports automatic traffic distribution and disaster recovery based on multiple nodes and lines. You can use GSLB to improve the reliability of your service. **No** is selected in this example.

    7.  **Access Log Service**: Select whether to activate Log Service.

        Log Service retrieves log data from WAF in real time and stores the data. You can query and analyze the log data, and generate analytics reports online. **No** is selected in this example.

    8.  **Bot Manager**: Select whether to enable this feature.

        To mitigate security threats caused by bot traffic, you can enable this feature. For more information, see [Set a bot threat intelligence rule](/intl.en-US/Website Protection Settings/Bot management/Set a bot threat intelligence rule.md) and [Configure the allowed crawlers function](/intl.en-US/Website Protection Settings/Bot management/Configure the allowed crawlers function.md). **No** is selected in this example.

    9.  **Mobile App Protection**: Select whether to enable this feature.

        You can enable this feature if your business supports native applications and you have security requirements for your business, such as trusted communication and prevention of bot scripts. For more information, see [Configure application protection](/intl.en-US/Website Protection Settings/Bot management/Application protection/Configure application protection.md). **No** is selected in this example.

    10. **Validity Period**: Select the duration of the WAF service.

4.  Click **Buy Now** and pay for the order.


## Step 5: Add website configurations

After WAF is activated, you must configure the forwarding rules for the website protected by WAF.

Perform the following steps to route user traffic to WAF before it reaches the domain name protected by WAF:

1.  Log on to the [WAF console](https://yundun.console.aliyun.com/?p=waf).

2.  In the top navigation bar, select the region of your WAF instance. **International** is selected in this example.

3.  In the left-side navigation pane, choose **Asset Center** \> **Website Access**.

4.  On the **Website Access** page, click **Add Domain Name**.

5.  On the **Add Domain Name** page, click **Manually Add Other Websites**.

    **Note:** The **Add Domain Name** page appears only when a qualified domain name exists. If **Add Domain Name** does not appear, skip this step.

6.  Follow the Add Domain Name wizard to complete the configuration.

    1.  **Domain Name**: Enter the domain name that needs WAF protection. **www.example.us** is used in this example.

        **Note:**

        -   You can enter a specific domain name, such as `www.aliyun.com` or a wildcard domain name, such as `*.aliyun.com`.
            -   If you use a wildcard domain name, WAF automatically searches for domain names that match the specified wildcard domain name.
            -   If you configure both a wildcard domain name and a specific domain name for a website, forwarding rules and protection policies of the specific domain name prevail over those of the wildcard domain.
        -   Domain names suffixed with `.edu` are not supported. If you need to use a `.edu` domain name, submit a ticket to request technical support.
    2.  **Protocol Type**: Select the protocol supported by the website. **HTTP** is selected in this example.

        **Note:**

        -   If your website supports HTTPS, select HTTPS, and upload the certificate and the private key file after you set website parameters. For more information, see [Upload HTTPS certificate files]().
        -   After you select HTTPS, click **Advanced Settings** to enable the HTTP force redirect and HTTP back-to-origin features to ensure efficient access to your website. For more information, see [Enable HTTPS advanced settings]().
        -   To enable protection for **HTTP 2.0** requests, make sure that the following requirements are met:
            -   Your WAF is upgraded to Business or Enterprise Edition.
            -   **HTTPS** is selected.
    3.  **Destination Server \(IP Address\)**: Select a server address type and enter the address of the origin server.

        Both **IP** and **Destination Server \(Domain Name\)** formats are supported. After your website is connected to WAF, WAF filters and redirects requests to this IP address. In this example, **Destination Server \(Domain Name\)** is selected, and the CNAME domain name that is assigned to GTM after you configure the basic information in Step 3 is used. For more information, see [Step 3: Configure basic information](#section_mdc_09w_z8z).

    4.  **Destination Server Port**: Specify the service protocol and port of the website.

        WAF receives and forwards traffic for your website through the specified ports. The user traffic destined for the website domain name is only forwarded through the specified service ports. For unspecified ports, WAF does not forward traffic received on these ports to the origin servers. Therefore, no security threats are posed on the origin servers if you enable these ports or if these ports have vulnerabilities.

        **Note:** The protocol and port must be the same as those of the origin server IP address. You cannot change the port after it is specified.

        The custom port **9000** is specified in this topic.

        **Note:** By default, WAF supports the following ports: HTTP ports 80 and 8080, and HTTPS ports 443 and 8443. WAF instances of Business and Enterprise Edition support more non-standard ports, and have corresponding limits on the total number of ports used by the protected domain name. For more information, see [t15555.md\#](/intl.en-US/Website Access/View the ports supported by WAF.md).

    5.  **Load Balancing Algorithm**: If multiple origin server IP addresses are specified, select **IP hash** or **Round-robin**. WAF distributes requests to these servers based on the specified algorithm for load balancing.

    6.  **Does a layer 7 proxy \(DDoS Protection/CDN, etc.\) exist in front of WAF**: Select Yes or No based on the actual status of your website. **Yes** is selected in this example.

    7.  **Request Tag**: Enter an unused **Header Field Name** and specify a custom **Header Field Value** to label the requests that are redirected to the origin servers through WAF. WAF adds the specified header field to the filtered requests. This enables your origin server to identify the requests redirected by WAF.

        **Note:** If the requests to your website already contain a specified header field, WAF overwrites the original field value with the specified value.

7.  Click **Next**. On the **Add Domain Name** page, click **Copy CNAME** to record the CNAME of WAF.

    ![WebCNAME](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1553958951/p99553.png)


## Step 6: Create a GA instance

Each GA instance is an acceleration service running on a global scale.

Follow steps below to purchase a GA instance.

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, click **Create Instance**.

3.  On the buy page, set the required parameters, and click **Buy Now**.

    1.  Select an instance specification. Select **Medium Ⅰ** in this topic.

        GA supports the following types of instance specifications: Small I, Small II, Small III, Medium I, Medium II, and Medium III. The acceleration performance can vary based on the instance specification.

        |Instance specification|Number of acceleration regions|Peak bandwidth|Maximum number of concurrent connections|
        |----------------------|------------------------------|--------------|----------------------------------------|
        |Small I|1|20 Mbit/s|5,000|
        |Small II|2|40 Mbit/s|10,000|
        |Small III|3|60 Mbit/s|15,000|
        |Medium I|5|100 Mbit/s|25,000|
        |Medium II|8|160 Mbit/s|40,000|
        |Medium III|10|200 Mbit/s|50,000|

    2.  Select the subscription duration for the GA instance.


After the instance is created, the system automatically assigns a CNAME to the instance. The CNAME is used to resolve the domain name of the origin servers.

![CNAME](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p84125.png)

## Step 7: Purchase and associate with a basic bandwidth plan

A basic bandwidth plan provides bandwidth for data transmission over the Internet and inside Alibaba Cloud. To achieve global acceleration, you need to purchase a basic bandwidth plan and bind the basic bandwidth plan to a Global Accelerator instance.

To purchase and bind a basic bandwidth plan to a Global Accelerator instance, follow these steps:

1.  On the **Instances** page, click **Buy Basic Bandwidth Plan**.

2.  On the buy page, set the following parameters, click **Buy Now**, and then pay for the order.

    1.  **Bandwidth Type**: Select the type of the basic bandwidth plan.

        In this example, the domain name of the origin server is registered outside China and cannot be hosted on servers in mainland China. **Premium** is selected to allow users in mainland China to access the web services deployed in the US \(Silicon Valley\) region through the Premium Internet in Hong Kong.

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

        **Note:** You can specify an ECS or SLB instance as an endpoint only if your Alibaba Cloud account is included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

    2.  **Peak Bandwidth**: Specify the maximum bandwidth value of the basic bandwidth plan. **10Mb** is selected in this example.

    3.  **Duration**: Select the duration of the basic bandwidth plan.

3.  Return to the **Instances** page, and click Instance ID.

4.  On the page that appears, click the **Bandwidth Manage** tab.

5.  In the **Basic Bandwidth Package** section, find the plan that you want to manage, and click **Bind** in the **Actions** column.

    ![Premium bandwidth](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1553958951/p99189.png)

    The basic bandwidth plan is now in the **Bound** state.


## Step 8: Add an area that you want to accelerate

After you purchase a basic bandwidth plan, you must add one or more acceleration areas where end users are located, and allocate bandwidth to these areas.

To add an acceleration area, follow these steps:

1.  On the **Instances** page, click the ID of the GA instance that is created in Step 6.

2.  On the instance details page, click the **Acceleration Regions** tab and select the region where you want to accelerate access. In this example, **Asia Pacific** is selected.

3.  On the Acceleration Areas tab, click **Add Acceleration Area**.

4.  In the **Add Acceleration Area** dialog box, set the following parameters, and click **OK**:

    1.  **Regions**: Select the region where users are located. **China \(Hong Kong\)** is selected in this example.

    2.  **Bandwidth**: Select a bandwidth value for the acceleration service. **10** Mbit/s is selected in this topic.


After the acceleration area is added, GA assigns an accelerated IP address to each acceleration area to accelerate access to the domain name.

## Step 9: Create a listener

A listener monitors connection requests from clients. Clients can connect to the specified port of the origin server through the specified protocol.

To add a listener to a Global Accelerator instance, follow these steps:

1.  On the **Instances** page, click the ID of the GA instance that is created in Step 6.

2.  On the Basic Information page, click the **Listeners** tab. Then, click **Add Listener**.

3.  On the **Configure Listener & Protocol** page, configure the listener:

    1.  **Listener Name**: Enter a name for the listener to be created. The name must be 2 to 128 characters in length and can contain letters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter or Chinese character.

    2.  **Protocol**: Select a protocol for the listener. Select **TCP** in this topic.

    3.  **Port Number**: Enter a port or port range for receiving and forwarding requests to the endpoints. Valid values: 1 to 65499. Enter **9000** in this topic.

    4.  **Client Affinity**: Select whether to enable client affinity. If the Client Affinity feature is enabled, requests from a specific client are always routed to the same endpoint. Select **Source IP Address** in this topic.

    ![Listener](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1615588951/p95540.png)

4.  Click **Next** to configure an endpoint group.


## Step 10: Configure an endpoint group

Each listener is associated with an endpoint group. You can associate an endpoint group with listeners by specifying the regions to which you want to distribute network traffic. After the association is complete, traffic is distributed to the optimal endpoints in the associated endpoint groups.

To configure an endpoint group, follow these steps:

1.  **Endpoint Group Name**: Enter a name for the endpoint group.

2.  Select the region where you want to create the endpoint group. The region specifies where the origin servers are located.

    In this example, network traffic is forwarded to WAF. Therefore, **United States \(Silicon Valley\)** is selected.

3.  Specify whether the origin servers are deployed on Alibaba Cloud or in the environments outside Alibaba Cloud. **Off Alibaba Cloud** is selected in this example.

4.  Specify whether to reserve client IP addresses. After the feature is enabled, origin servers can reserve client IP addresses. This feature is disabled in this example.

    **Note:** This feature is available for only the Alibaba Cloud accounts that are included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

5.  Configure endpoints.

    1.  **Backend Service Type**: Select **Custom Domain Name** from the drop-down list.

    2.  **Backend Service**: Enter the IP address of the CNAME assigned by WAF after you set website parameters in Step 5. For more information, see [Step 5: Add website configurations](#section_jlx_hdy_zsf).

    3.  **Weight**: Specify a weight for the endpoint. Valid values: 0 to 255. GA routes network traffic to each endpoint in proportion to the weight of each endpoint.

        **Note:** If you set the weight of an endpoint to 0, GA stops routing network traffic to the endpoint. Proceed with caution.

    ![endpoint](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p99230.png)

6.  Click **Next** to confirm the configurations, and then click **Next**.


## Step 11: Activate the Anti-DDoS Premium service

You can use Anti-DDoS Premium to mitigate DDoS attacks against servers deployed outside mainland China. The Anti-DDoS Premium service filters out attack traffic in scrubbing centers that are deployed closest to visitors and forwards only normal network traffic back to the origin server. This ensures the stability of your workloads.

To purchase an Anti-DDoS Premium instance, perform the following steps:

1.  Log on to the [Anti-DDoS Pro console](https://yundun.console.aliyun.com/?p=ddoscoo).

2.  On the **Instances** page, click **Purchase Instances**.

3.  On the buy page, set the following parameters.

    1.  **Product Type**: Select **Anti-DDoS Premium**.

    2.  **Mitigation Plan**: Select a mitigation plan for the Anti-DDoS Premium instance that you want to purchase.

        -   For more information about Insurance and Unlimited mitigation plans, see [Billing methods of Insurance Plan and Unlimited Plan](/intl.en-US/Pricing/Anti-DDoS premium billing methods/Billing methods of Insurance Plan and Unlimited Plan.md).
        -   For more information about Mainland China Access \(MCA\), see [Mainland China Acceleration billing methods](/intl.en-US/Pricing/Anti-DDoS premium billing methods/Mainland China Acceleration billing methods.md).
        The **Unlimited** plan is selected in this example.

    3.  **Clean Bandwidth**: Select the bandwidth value of the Anti-DDoS Premium instance.

        The value specifies the maximum traffic load of an Anti-DDoS instance when the instance is not under attack. **100Mbps** is selected in this example.

    4.  **Function Plan**: Select a plan.

        You can select **Standard Function** or **Enhanced Function**. For more information about the differences between Standard Function and Enhanced Function, see [Function plan](/intl.en-US/Pricing/Function plan.md). **Enhanced Function** is selected in this example.

    5.  **Domains**: Select the number of HTTP/HTTPS domain names that can be protected by the instance.

        For more information about the number of protected domain names, see [Domains](). **10** is selected in this example.

    6.  **Clean QPS**: Set the queries per second \(QPS\).

        This parameter specifies the maximum number of concurrent HTTP or HTTPS requests that the instance can process when no attack occurs. **3000** is selected in this example.

    7.  **Ports**: Select the number of supported ports.

        The number of protected ports equals the maximum number of entries supported for TCP/UDP forwarding. **50** is selected in this example.

    8.  **Quantity**: Select the number of instances that you want to purchase.

    9.  **Subscription**: Select the subscription period of the Anti-DDoS Premium instance.

4.  Click **Buy Now** to complete the payment.


## Step 12: Add a website

The configurations of a website specified in the Anti-DDoS Pro console define how network traffic is transmitted between a website and an Anti-DDoS Pro instance.

Follow these steps to add the website that needs protection to Anti-DDoS Pro:

1.  Log on to the [Anti-DDoS Pro console](https://yundun.console.aliyun.com/?p=ddoscoo).

2.  In the top navigation bar, select the region where the service is deployed. **Outside Mainland China** is selected in this example.

3.  In the left-side navigation pane, choose **Provisioning** \> **Website Config**.

4.  On the **Website Config** page, click **Add Domain**.

5.  On the **Add Domain** page, enter the website information.

    1.  **Function Plan**: Select a plan for the Anti-DDoS Premium instance that you want to associate with your website.

        **Standard** and **Enhanced** are available. For more information, see [Function plan](/intl.en-US/Pricing/Function plan.md). **Enhanced** is selected in this example.

    2.  **Instance**: Select the Anti-DDoS Pro instance to be associated. You can select up to eight instances for one domain. The instances associated with a domain must use the same function plan.

    3.  **Domain**: Enter the website domain name that requires protection. **www.example.us** is used in this example.

    4.  **Protocol**: Select the protocols supported by the website. By default, **HTTP** and **HTTPS** are selected. This topic uses the default setting.

    5.  **Server IP**: Specify the address type and address of the origin server. In this example, **Origin Server IP** is selected, and the accelerated IP address is used. The accelerated IP address is the one that the GA instance assigns to the China \(Hong Kong\) region after you add the acceleration area in Step 8. For more information, see [Step 8: Add an area that you want to accelerate](#section_uoc_2zz_yqm).

    6.  **Server Port**: Specify a server port based on the protocol type. In this topic, **9000** is used.

6.  Click **Add**.


## Step 13: Set parameters of Sec-Traffic Manager

Anti-DDoS Pro provides Sec-Traffic Manager to set the interaction rules between Anti-DDoS Pro and other cloud resources. You can set rules to trigger and enable Anti-DDoS Pro in specific scenarios. This helps you keep workloads running smoothly if no DDoS attacks occur, and provides more effective protection when DDoS attacks occur.

To configure Sec-Traffic Manager, follow these steps:

1.  Log on to the [Anti-DDoS Pro console](https://yundun.console.aliyun.com/?p=ddoscoo).

2.  In the top navigation bar, select the region of the service. **Outside Mainland China** is selected in this example.

3.  In the left-side navigation pane, choose **Provisioning** \> **Sec-Traffic Manager**.

4.  On the **Cloud Service Interaction** tab, click **Create Rule**.

5.  In the **Create Rule** dialog box, set the following parameters:

    1.  **Interaction Scenario**: Select an interaction scenario for the rule. In this topic, select **Cloud Service Interaction**.

    2.  **Name**: Enter the rule name.

        The name can be 1 to 128 characters in length and can contain letters, digits, and underscores \(\_\).

    3.  **Anti-DDoS Instance IP**: Select the Anti-DDoS instance that you want to associate with. In this topic, the Anti-DDoS Premium instance that you create in Step 11 is selected.

    4.  **Cloud Service**: Select the region where the cloud resource is deployed, and then enter the IP address of the cloud resource.

        You can click **Add Cloud Resource IP** to add more cloud resources. You can add at most 20 IP addresses.

        **cn-hongkong** is selected and the accelerated IP address is used in this example. The accelerated IP address is the one that the GA instance assigns to the China \(Hong Kong\) region after you add the accelerated area in Step 8. For more information, see [Step 8: Add an area that you want to accelerate](#section_uoc_2zz_yqm).

    5.  **The waiting time of switching back**: The waiting time for triggering the switching back process after GA interacts with Anti-DDoS Pro.

        Black hole deactivation consumes a certain amount of time. Frequent switchback is not recommended. Therefore, the minimum value of this parameter is 30 minutes. The waiting time is set to 60 minutes in this example.

6.  Click **Next**.

7.  Click **Finished**.

    After a rule is created, Sec-Traffic Manager assigns a CNAME address to this rule.

    ![Sec-Traffic Manager](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2553958951/p95809.png)


## Step 14: Resolve the domain name to Sec-Traffic Manager

After you create a scheduling rule in Sec-Traffic Manager, you must update the CNAME record of the domain to redirect website traffic from mainland China to Sec-Traffic Manager. The rule takes effect only after you update the CNAME record.

**Note:** If you use a third-party DNS service, log on to the system of the DNS service provider to modify the DNS record of your website.

To resolve the domain name to Sec-Traffic Manager, follow these steps:

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com).

2.  On the **Manage DNS** page, find the target domain name, and click **Configure** in the **Actions** column.

3.  On the **DNS Settings** page, click **Add Record**.

4.  In the **Add Record** dialog box, configure the record, and click **Confirm**.

    1.  **Type**: Select a record type.

        In this example, the website domain name is mapped to another domain name. Therefore, **CNAME** is selected.

    2.  **Host**: Enter the prefix of the accelerated domain name.

        **www** is entered in this example.

    3.  **ISP Line**: Select **Default** from the drop-down list.

    4.  **Value**: Set this parameter to the CNAME assigned in Step 13. For more information, see [Step 13: Set parameters of Sec-Traffic Manager](#section_fez_igw_wil).

    5.  **TTL**: The TTL value of the IP address that is mapped to the specified domain name.

        **10 minute\(s\)** is selected in this example.

    ![Add a CNAME](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2553958951/p100157.png)

5.  Repeat the preceding steps to add CNAME records for ISP lines provided by **China Unicom**, **China Telecom**, **China Mobile**, and **China Education Network**.

    ![Add CNAME records](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2553958951/p100160.png)


## Step 15: Test the connectivity

In regions of mainland China, use a Windows operating system to test the performance of protection and acceleration provided by GA after GA interacts with CDN, Anti-DDoS Pro, WAF, and GTM.

1.  The domain name www.example.us is hosted outside mainland China. Enter this domain in the address bar of the browser to access the application deployed in the US \(Silicon Valley\) region.

    The result shows that the website services deployed in the US \(Silicon Valley\) region can be accessed through the domain name www.example.us.

    ![Test the connectivity](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1615588951/p96014.png)

2.  Open the command-line interface, and run the `nslookup <web service domain name>` command to check the DNS resolution result.

    -   When the origin server is not attacked, the IP address of the GA instance is returned.
    -   When the origin server is under attack, the IP address of the Anti-DDoS Premium instance is returned.
3.  Run the `nslookup <CNAME access domain name in GTM>` command to check the resolution result.

    -   If the primary server group is available: The domain name is resolved to the IP address of Server 1 or Server 2. In this topic, the primary server group contains Server 1 and Server 2 that are deployed in the US \(Silicon Valley\) region.
    -   If the primary server group is unavailable, the IP address of Server 3 or Server 4 is returned. In this topic, the primary server group contains Server 1 and Server 2 deployed in the US \(Silicon Valley\) region.
4.  Run the following command to test the latency of data transmission:

    `curl -o /dev/null -s -w "time_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" "http[s]://<Web service domain name>[:<Port>]"`

    In the request:

    -   time\_connect: The amount of time that it takes to establish a TCP connection.
    -   time\_starttransfer: The data transmission start time. It refers to the time period from when a client sends a request to when a backend server responds to the first byte.
    -   time\_total: The total connection time. It refers to the time period from when a client sends a connection request to when a backend server responds to the request.
    The test result shows that GA has reduced the network latency when users from mainland China access the web services deployed in the US \(Silicon Valley\) region.

    ![The network latency of data transmission before GA is used](../images/p76785.png "The network latency of data transmission before GA is used")

    ![The network latency of data transmission after GA is used](../images/p76786.png "The network latency of data transmission after GA is used")

    **Note:** The preceding example is for reference only. .The performance of the protection and acceleration services provided by GA varies based on the actual scenario.



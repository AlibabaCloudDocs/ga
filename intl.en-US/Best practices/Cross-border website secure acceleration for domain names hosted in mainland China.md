# Cross-border website secure acceleration for domain names hosted in mainland China

Global Accelerator \(GA\) provides web service providers a cross-border website secure acceleration solution. GA uses high-bandwidth BGP lines and the global transmission network of Alibaba Cloud to accelerate services. It can interact with Content Delivery Network \(CDN\), Anti-DDoS Pro, Web Application Firewall \(WAF\), and Global Traffic Manager \(GTM\) to ensure the security and efficiency of service delivery.

Before you start, make sure that the following requirements are met:

-   An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).
-   Your website has an ICP number.

A website service is deployed in the US \(Silicon Valley\) region of Alibaba Cloud. The origin servers are four Elastic Compute Service \(ECS\) instances associated with elastic IP addresses. Users in mainland China want to access the website service by visiting www.example.com, a domain name hosted in mainland China. The forwarding port is TCP port 9000. The website service provider meets the following challenges:

-   The website service frequently receives website attacks and DDoS attacks, which severely affect the security and availability of the website service.
-   The cross-border public network is unstable. Network issues, such as network latency, network jitter, and packet loss, may frequently occur and degrade the performance of the website service.
-   The origin servers are unstable. Service disruption may occur when users visit the website.

![Architecture (ICP filing acquired)](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2947958951/p99746.png)

As shown in the preceding figure, you can deploy GA to interact with the CDN, Anti-DDoS Pro, WAF, and GTM services. This solution helps you resolve the issues on visiting website services across borders.

-   Alibaba Cloud CDN can accelerate website content delivery to improve the user experience of the website visitors.

    Alibaba Cloud CDN retrieves resources from origins and caches them on CDN nodes deployed on a global scale. When the client requests a resource, the system does not need to send the request to the origin. Instead, the system automatically retrieves the cached resource from the CDN node that is nearest to the client.

-   Anti-DDoS Pro can help you defend against DDoS attacks.

    All traffic from the public network passes through Anti-DDoS Pro. Malicious traffic is scrubbed in the scrubbing center and only legitimate traffic is forwarded to the origin server through the port protocol.

-   WAF can protect your website against a variety of web attacks.

    All network traffic destined for the website must pass through WAF before reaching the origin servers. WAF detects and blocks malicious traffic, and reroutes only normal traffic to the origin servers to ensure the security, stability, and availability of the origin servers.

-   GA can speed up content delivery between the origin servers and users in acceleration areas.

    Users in China \(Shanghai\), China \(Hangzhou\), and China \(Shenzhen\) can connect to the nearest access point of the global transmission network by sending requests to accelerated IP addresses. Then, user requests are redirected to the origin servers deployed in US \(Silicon Valley\) through intelligent routing and automatic network traffic distribution.

-   GTM can be used to isolate malfunctioned servers or switch network traffic among multiple origin servers.
    -   When the primary server group is working normally, all user traffic is forwarded to the primary server group.
    -   When the primary server group becomes unavailable, user traffic is immediately switched to the secondary server group for failover. After the primary server group recovers, the traffic is switched back to the primary server group.

## Procedure

![Procedure for configuring cross-border website secure acceleration](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p99825.png)

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

        Click **+ New Address Pool** and add the IP addresses of Origin Server 1 and Origin Server 2 in the US \(Silicon Valley\) region to the address pool. Enable HTTP health checks, and specify the address pool as the default address pool. For more information about how to configure health checks, see [t15663.dita\#concept\_fph\_rzt\_vdb/section\_oc3\_ngw\_vdb](t15663.dita#concept_fph_rzt_vdb/section_oc3_ngw_vdb).

    4.  **Alternative Address Pool**: Select an alternative address pool.

        An alternative address pool is an IP address pool that contains IP addresses of secondary origin servers. GTM forwards requests to the secondary origin servers when the servers in the default address pool are unavailable.

        Click **+ New Address Pool** and add Origin Server 3 and Origin Server 4 in the US \(Silicon Valley\) region to the alternative address pool. Configure health checks, and specify the address pool as an alternative address pool. For more information about how to configure health checks, see [t15663.dita\#concept\_fph\_rzt\_vdb/section\_oc3\_ngw\_vdb](t15663.dita#concept_fph_rzt_vdb/section_oc3_ngw_vdb).

6.  Click **Next**.


## Step 3: Configure basic information

After you configure the access policies, you must specify the basic information of the GTM instance. The information includes the domain name, CNAME, load balancing policy, global time-to-live \(TTL\) value, and alert group. To configure the basic information for the GTM instance, perform the following steps:

To configure the basic information for GTM, perform the following steps:

1.  On the **Basic Information** page, follow the wizard to configure basic information.

    1.  **Instance Name**: Enter an instance name.

        The instance name is used to identify the application service that runs on the instance.

    2.  **Primary Domain**: Enter a base domain name. **www.example.com** is entered in this topic.

    3.  **CNAME Access Domain Name**: Specify the type of the CNAME for the base domain name.

        -   **Assigned Access Domain Name**: Select this option if the IP address pool only contains Alibaba Cloud IP addresses or IP addresses outside China.
        -   **Custom Access Domain Name**: Select this option if the IP address pool contains IP addresses of on-premises data centers.
        In this topic, the address pool of origin servers only contains Alibaba Cloud elastic IP addresses. Therefore, the Assigned Access Domain Name option is selected.

    4.  **Balance Policy**: Select a load balancing policy for GTM.

        -   **Round Robin**: distributes network traffic equally to multiple IP addresses in the IP address pool. This is the default policy.
        -   **Weighted Round Robin**: uses the pre-configured weighted round-robin policy to process DNS queries when the domain name is resolved to more than one IP address.
        **Round Robin** is selected in this topic.

    5.  **Global TTL**: The validity period of an IP address to which the domain name is resolved. **1 minute\(s\)** is selected in this topic.

        GTM provides traffic management services based on domain names. The Global TTL parameter specifies the validity period of the IP address cached in the DNS system of the service provider. By default, the parameter is set to 1 minute. If you use a custom domain name, the global TTL must be the same as the minimum TTL supported by the Alibaba Cloud DNS service plan of the custom domain name.

    6.  **Alert Group**: The contact group to which a notification is sent when an exception is detected in your workloads.

        **Note:**

        -   If you have not configured an alert group, log on to the Cloud Monitor console and add an alert group. For more information, see [Delete an alert contact or alert group](/intl.en-US/Alarm service/Alert contacts/Delete an alert contact or alert group.md).
        -   If you have configured a contact group but want to configure the basic information as a Resource Access Management \(RAM\) user, you must first use your Alibaba Cloud account to authorize the RAM user. After the RAM user is authorized, you can log on as a RAM user to read the alert group information.
2.  Click **Complete**.


After you configure the basic information, the system automatically allocates a CNAME address to the base domain name. User requests destined for the CNAME address are resolved to the IP address of the scheduled origin server.

![cname](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p99619.png)

## Step 4: Create a GA instance

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, click **Create Instance**.

3.  On the buy page, set the following parameters, click **Buy Now**, and then complete the payment.

    1.  Select a specification for the GA instance. **Medium Ⅰ** is selected in this example.

        GA supports the following types of instance specifications: Small I, Small II, Small III, Medium I, Medium II, and Medium III. The acceleration performance can vary based on the instance specification.

        |Instance specification|Number of acceleration regions|Peak bandwidth|Maximum number of concurrent connections|
        |----------------------|------------------------------|--------------|----------------------------------------|
        |Small I|1|20 Mbit/s|5,000|
        |Small II|2|40 Mbit/s|10,000|
        |Small III|3|60 Mbit/s|15,000|
        |Medium I|5|100 Mbit/s|25,000|
        |Medium II|8|160 Mbit/s|40,000|
        |Medium III|10|200 Mbit/s|50,000|

    2.  Select a duration for the GA instance.


After the instance is created, the system automatically assigns a CNAME to the instance. The CNAME is used to resolve the domain name of the origin servers.

![CNAME](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p84125.png)

## Step 5: Purchase and bind a basic bandwidth plan

A basic bandwidth plan provides bandwidth for data transfer over the Internet and within Alibaba Cloud. To achieve global acceleration, you must purchase a basic bandwidth plan and bind it to the GA instance.

1.  On the **Instances** page, click **Purchase Basic Bandwidth Plan**.

2.  On the buy page, set the required parameters, click **Buy Now**, and complete the payment.

    1.  **Bandwidth Type**: Select the type of the basic bandwidth plan. **Basic** is selected in this example.

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
    2.  **Peak Bandwidth**: Select the peak bandwidth of the basic bandwidth plan. **10Mb** is selected in this topic.

    3.  **Duration**: Select the duration of the basic bandwidth plan.

3.  Return to the **Instances** page, and click the ID of the GA instance that you created in Step 1.

4.  On the page that appears, click the **Bandwidth Manage** tab.

5.  In the **Basic Bandwidth Package** section, find the target plan, and then click **Bind** in the **Actions** column.

    ![Bind](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1615588951/p95529.png)

    The basic bandwidth plan is now in the **Bound** state.


## Step 6: Add an acceleration area

After you purchase a basic bandwidth plan, you can specify a region to be accelerated and allocate bandwidth resources used for acceleration.

1.  On the **Instances** page, click the ID of the GA instance that is created in Step 4.

2.  On the instance details page, click the **Acceleration Areas** tab. Then, click **Add Region**.

3.  In the **Add Acceleration Area** dialog box, set the following parameters and click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Regions**|Select the region from which requests are to be accelerated. In this example, **China \(Hangzhou\)** is selected.|
    |**Bandwidth**|Specify the bandwidth resources used for acceleration. In this example, **2** Mbit/s is used.|
    |**Internet Protocol**|You can select IPv4 or IPv6. After the accelerated region takes effect, you cannot change the protocol. However, you can delete the accelerated region, and add another region to be accelerated. This way, you can select the other protocol.|
    |**Actions**|The operations that you can perform on the region.|
    |**Add**|Click **Add**, specify China \(Shanghai\) as the region to be accelerated, and then allocate 2 Mbit/s of bandwidth to the China \(Shanghai\) region.|

4.  Repeat the preceding steps to specify China \(Shenzhen\) as the region to be accelerated, and allocate 2 Mbit/s of bandwidth to the China \(Shenzhen\) region.

    After you add a region to be accelerated, GA assigns an IP address to the region. The IP address is used to accelerate requests from the region.


## Step 7: Create a listener

A listener is used to check requests from clients. The system forwards requests based on the specified protocol and port.

1.  On the **Instances** page, click the ID of the GA instance that is created in Step 4.

2.  On the **Listeners** tab, click **Add Listener**.

3.  On the **Configure Listener & Protocol** page, set the following parameters. Then, click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Listener Name**|Enter a name for the listener. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.|
    |**Protocol**|Select a protocol for the listener. In this topic, **TCP** is selected.|
    |**Port Number**|Specify a port for the listener. The port is used to receive and forward requests to endpoints. Valid values: 1 to 65499. In this example, **9000** is used.|
    |**Client Affinity**|Specify whether to enable client affinity. If client affinity is enabled, requests from the same client can be directed to the same endpoint when the client accesses a stateful application. In this example, **Source IP Address** is selected.|

4.  On the **Configure Endpoint Group** page, set the following parameters and click **Next**.

    1.  Enter a name for the endpoint group in the **Endpoint Group Name** field.

    2.  Select the region to which the endpoint group and backend servers belong.

        In this example, **US \(Silicon Valley\)** is selected.

    3.  Specify whether to deploy the backend service on Alibaba Cloud. In this example, **Alibaba Cloud** is selected.

    4.  Specify whether to reserve client IP addresses. After the feature is enabled, backend servers can obtain source IP addresses of clients. In this example, this feature is disabled.

    5.  Configure endpoints.

        |Parameter|Description|
        |---------|-----------|
        |**Backend Service Type**|In this example, **Alibaba Cloud Public IP Address** is selected.|
        |**Backend Service**|Enter the EIP of the backend server. The EIP is used to provide services.|
        |**Weight**|Specify a weight for the endpoint. Valid values: 0 to 255. GA routes network traffic to each endpoint in proportion to the weight of each endpoint. **Note:** If you set the weight of an endpoint to 0, GA does not route network traffic to the endpoint. Proceed with caution. |
        |**+ Add Endpoint**|Click **+ Add Endpoint** to specify another server in the US \(Silicon Valley\) region as an endpoint, and set a weight.|


## Step 8: Configure an endpoint group

1.  Select the region where the endpoint group is deployed. The selected region is where the target server is deployed.

    **US \(Silicon Valley\)** is selected in this topic.

2.  Specify whether the backend service is deployed on Alibaba Cloud. **Off Alibaba Cloud** is selected in this topic.

3.  Enable or disable the feature of reserving client IP addresses. After the feature is enabled, origin servers can reserve client IP addresses. This feature is disabled in this topic.

    **Note:** The feature of reserving client IP addresses is available only to users in the whitelist. If you are not included in the whitelist and you want to use the feature, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

4.  Configure endpoints.

    1.  **Backend Service Type**: Select **Custom Domain Name** from the drop-down list.

    2.  **Backend Service**: Enter the CNAME address assigned by the system after you configure the basic information in Step 3. For more information, see [Step 3: Configure basic information](#section_fdd_3lq_0qt).

    3.  **Weight**: Enter a number from 0 to 255 to set a weight for the endpoint. GA routes traffic to endpoints based on the predefined weights.

        **Note:** If the weight of an endpoint is set to 0, GA stops distributing traffic to the endpoint. Proceed with caution.

    ![endpoint](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p99230.png)


## Step 9: Purchase and bind a cross-border bandwidth plan

A bandwidth plan for cross-border acceleration is used to accelerate data transfer between mainland China and regions outside mainland China. Perform the following steps to purchase a bandwidth plan for cross-border acceleration and bind it to the GA instance.

1.  On the **Instances** page, click **Purchase Cross-border Acceleration Bandwidth Plan**.

2.  On the buy page, set the parameters and click **Buy Now** to complete the payment.

    1.  **Area A**: Select the area where the bandwidth plan is used. In this example, **Mainland China** is selected.

    2.  **Area B**: Select the area where the bandwidth plan is used. By default, **Global** is selected.

        **Global**: Requests are forwarded to the optimal endpoint based on the region from which requests are initiated.

    3.  **Billing Method**: Select a metering method for the bandwidth plan. Only **Pay by Bandwidth** is supported.

    4.  **Bandwidth**: Select a bandwidth value for the bandwidth plan.

        We recommend that you specify the same bandwidth value for the basic bandwidth plan and the bandwidth plan for cross-border acceleration. In this example, **10Mb** is selected.

    5.  **Duration**: Select a subscription duration.

3.  Return to the **Instances** page, find the GA instance, and then click its ID.

4.  Click the **Bandwidth Manage** tab.

5.  In the **Cross-region Bandwidth Package** section, find the bandwidth plan for cross-border acceleration, and click **Bind** in the **Actions** column.

    ![Bind the bandwidth plan to the GA instance](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4246383261/p95548.png)

    After you bind the bandwidth plan to the GA instance, the bandwidth plan is in the **Bound** state.


## Step 10: Activate the WAF service

WAF is empowered by big data technologies of Alibaba Cloud Security. WAF allows you to defend against common web attacks such as SQL injections, cross-site scripting \(XSS\), web shells, Trojans, unauthorized downloads, and HTTP flood attacks. WAF protects your web resources from exposure and ensures the security and availability of your website.

This topic describes how to purchase a subscription WAF instance.

1.  Open the [WAF product page](https://www.alibabacloud.com/zh/product/waf) on the Alibaba Cloud official website, and then log on with your Alibaba Cloud account.

2.  Click **Buy Now**.

3.  On the **Web Application Firewall** page, set the following parameters:

    1.  **Region**: Select the region where the WAF instance is deployed.

        **China Mainland** is selected in this topic.

    2.  **Plan**: Select the version of the WAF service.

        Different WAF service plans are applicable to various business scales and provide different protection features. For more information, see [WAF deployment plans and editions](/intl.en-US/Product Introduction/WAF deployment plans and editions.md). **Enterprise** is selected in this topic.

    3.  **Extra Domain**: Specify the number of additional domains.

        If you want to add multiple domains or more than 10 subdomains to WAF, you can purchase additional domains. For more information, see [Additional domain](/intl.en-US/Pricing/Subscription/Extra domain quota.md). For this solution, you do not need to purchase additional domains.

    4.  **Exclusive IP**: Specify the number of exclusive IP addresses.

        You can purchase an exclusive IP address when your website domain name needs WAF protection through an exclusive IP address. For more information, see [Exclusive IP](/intl.en-US/Pricing/Subscription/Exclusive IP addresses.md). For this solution, you do not need to purchase a WAF exclusive IP.

    5.  **Extra Traffic**: Specify the size of the bandwidth extension plan to be purchased. Unit: Mbit/s.

        If the total bandwidth of your website exceeds the service bandwidth of WAF, you can purchase a bandwidth extension plan. For more information, see [Bandwidth extension plan](/intl.en-US/Pricing/Subscription/Extra bandwidth.md). **100Mbps** is selected in this topic.

    6.  **GSLB**: Select whether to enable Global Server Load Balancing \(GSLB\).

        GSLB uses the multi-node resilience technology. It supports automatic traffic distribution and disaster recovery based on multiple nodes and lines. You can use GSLB to improve the reliability of your service. **No** is selected in this topic.

    7.  **Access Log Service**: Specify whether to enable Log Service.

        Log Service retrieves log data from WAF in real time and then stores the data in Logstores. You can query and analyze the log data, and generate analytics reports online. **No** is selected in this topic.

    8.  **Bot Manager**: Select whether to enable the Bot Manager feature.

        To mitigate security threats caused by bot traffic, you can enable the Bot Manager feature. For more information, see [Set a bot threat intelligence rule](/intl.en-US/Website Protection Settings/Bot management/Set a bot threat intelligence rule.md) and [Configure the allowed crawlers function](/intl.en-US/Website Protection Settings/Bot management/Configure the allowed crawlers function.md). **No** is selected in this topic.

    9.  **Mobile App Protection**: Select whether to enable mobile application protection.

        You can enable the mobile app protection feature if your business supports native applications and you have security needs for your business, such as trusted communications and prevention of abusing bot scripts. For more information, see [Configure application protection](/intl.en-US/Website Protection Settings/Bot management/Application protection/Configure application protection.md). **No** is selected in this topic.

    10. **Service Time**: Select the validity period of the WAF service.


## Step 11: Add website configurations in WAF

Take the following steps to route user traffic to WAF before it reaches the domain name protected by WAF:

1.  In the status bar, select the region where your WAF instance is deployed. Select **Mainland China** in this topic.

2.  In the left-side navigation pane, choose **Asset Center** \> **Website Access**.

3.  On the **Website Access** page, click **Add Domain Name**.

4.  Follow the Add Domain Name wizard to complete the configuration.

    1.  **Domain Name**: Enter the domain name that needs WAF protection. **www.example.com** is entered in this topic.

        **Note:**

        -   This parameter supports precise domain names such as `www.aliyun.com` and wildcard domain names such as `*.aliyun.com`.
            -   WAF protects all subdomains that match the specified wildcard domain name.
            -   If you configure both a wildcard domain name and a precise domain name for a website, forwarding rules and protection policies of the precise domain name prevail over those of the wildcard domain.
        -   Domain names with the `.edu` suffix are not supported. If you want to use a `.edu` domain name, submit a ticket to request technical support.
    2.  **Destination Server \(IP Address\)**: Select a server address type and enter the address of the origin server.

        Both **IP** and **Destination Server \(Domain Name\)** formats are supported. After you connect your website to WAF, WAF redirects filtered requests to the specified address. Select **Destination Server \(Domain Name\)** in this topic, and then enter the CNAME address assigned to the GA instance that you create in Step 4. For more information, see [Step 4: Create a GA instance](#section_efv_yl1_8q1).

    3.  **Load Balancing Algorithm**: If you have specified one or more origin IP addresses, select **IP hash**, **Round Robin**, or **Least time**. WAF distributes requests to these servers based on the specified algorithm for load balancing. **Least time** is selected in this topic.

        **Note:** You can select **Least time** only when intelligent load balancing is enabled. For more information, see [Intelligent load balancing](/intl.en-US/Pricing/Subscription/Intelligent load balancing.md).


## Step 12: Purchase an Anti-DDoS Pro instance

Anti-DDoS Pro has the largest BGP bandwidth resources in mainland China. Up to 1.5 Tbit/s of bandwidth resources can be used to mitigate DDoS attacks.

1.  Log on to the [Anti-DDoS Pro console](https://yundun.console.aliyun.com/?p=ddoscoo).

2.  On the **Instances** page, click **Purchase Instances**.

3.  On the buy page, set the following parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Product Type**|**Anti-DDoS Pro \(Mainland China\)** is selected by default.|
    |**Mitigation Plan**|**Profession** is selected by default.|
    |**Basic Protection**|Specify the bandwidth resources used for basic protection. Basic protection is billed on a subscription basis. It takes effect only after you complete the payment. The total instance cost increases with the basic protection bandwidth that you select. |
    |**Burstable Protection**|Specify the maximum value of bandwidth used for protection. Burstable protection is billed on a pay-as-you-go basis.

    -   If you set **Burstable Protection** and **Basic Protection** to the same value, the maximum bandwidth value equals the value of **Basic Protection**. In this case, you are charged for only basic protection.
    -   If you set **Burstable Protection** to a value greater than **Basic Protection**, the value of bandwidth used for protection is between **Basic Protection** and **Burstable Protection**. If the peak bandwidth exceeds **Basic Protection**, a pay-as-you-go bill is generated based on the exceeded amount. |
    |**Business Scale**|Select the value of bandwidth that is used to process normal requests. Valid values: 100 to 5000. Unit: Mbit/s. Evaluate your business scale and estimate the maximum values of inbound bandwidth and outbound bandwidth based on your business requirements. Set **Business Scale** to the larger value that you estimated. For more information, see [Select the clean bandwidth](/intl.en-US/Anti-DDoS Pro & Premium User Guide/Purchase mitigation plans for Anti-DDoS Pro and Anti-DDoS Premium.md).

**Note:** If the bandwidth resources that you specify are insufficient to meet your business requirements, packet loss may occur and your business may be affected. In this case, we recommend that you purchase more bandwidth resources. |
    |**Function Plan**|Select a function plan for the instance. Options:     -   **Standard Function**
    -   **Enhanced Function**
For more information, see [Function plan](/intl.en-US/Pricing/Function plan.md). |
    |**Domains**|Specify the number of domain names that the instance can protect. Values must be multiples of 10. Valid values: 50 to 200. You can specify subdomains and wildcard domains. The number of unique domains that correspond to the subdomains and wildcard domains must not exceed **Domains**/10.

For example, the default value of the **Domains** parameter is 50. This means that the Anti-DDoS Pro instance can protect up to five different domains. The sum of subdomains and wildcard domains cannot exceed 50.

If you want to enable protection for example1.com and example2.com, you can specify their subdomains such as www.example1.com and abc.example2.com, or wildcard domain \*.example1.com.

If you want to specify more than 50 subdomains and wildcard domains, or enable protection for more than five domains, we recommend that you set **Domains** to a value based on your business requirements. |
    |**Clean QPS**|Specify the number of concurrent queries per second \(QPS\) that the instance can process. Non-attack requests that use HTTP or HTTPS are supported. Valid values: 3000 to 100000.|
    |**Ports**|Specify the number of TCP and UDP ports that are used to forward requests. Valid values: 50 to 400.|
    |**Resource Group**|Select a resource group to which the instance belongs. **Default Resource Group** is selected by default. **Note:** You can select a resource group only on the buy page of the early version. You can purchase an instance that does not belong to the **Default Resource Group** only in the Anti-DDoS Pro console of the early version. You can click **Early Version** in the upper-right corner to go to the Anti-DDoS Pro console of the early version. |
    |**Quantity**|Select the number of instances that you want to purchase.|
    |**Duration**|Select a subscription duration for the instance. If you select **Auto renewal**, the instance is automatically renewed upon expiration.

    -   Monthly subscription: The instance is automatically renewed for one month.
    -   Annual subscription: The instance is automatically renewed for one year. |

4.  Click **Buy Now** and complete the payment.


## Step 13: Add a domain to Anti-DDoS Pro

To set up Anti-DDoS Pro for a website, you must add the domain name of the website to Anti-DDoS Pro. The configurations specified in the Anti-DDoS Pro console define how network traffic is forwarded between a website and an Anti-DDoS Pro instance.

To add a domain name, take the following steps:

1.  Log on to the [Anti-DDoS Pro console](https://yundun.console.aliyun.com/?p=ddoscoo).

2.  In the top status bar, select the region of the service.

    In this topic, the traffic is scrubbed by Anti-DDoS Pro and then forwarded to WAF. Therefore, **Mainland China** is selected in this topic.

3.  In the left-side navigation pane, choose **Provisioning** \> **Website Config**.

4.  On the **Website Config** page, click **Add Domain**.

5.  On the **Add Domain** page, enter the website information.

    1.  **Function Plan**: Select a function plan for the Anti-DDoS Pro instance. You can select a **Standard** or **Enhanced** function plan.

        For more information, see [Function plan](/intl.en-US/Pricing/Function plan.md). **Enhanced** is selected in this topic.

    2.  **Instance**: Select the Anti-DDoS Pro instance to be associated with the domain name.

        You can associate up to eight Anti-DDoS Pro instances with each domain name. However, these instances must use the same function plan.

    3.  **Domain**: Enter the domain name to be protected.

        **Note:**

        -   Based on the naming convention of domain names, the domain name can contain uppercase and lowercase letters, digits, and hyphens \(-\). The domain name must start with a letter or digit.
        -   You can enter a wildcard domain name, such as `*.aliyun.com`. Anti-DDoS Pro protects all subdomains of the wildcard domain name.
        -   If you configure both a wildcard domain name such as `*.aliyun.com` and a precise domain name such as `www.aliyun.com` for a website, forwarding rules and protection policies of the precise domain name prevail over those of the wildcard domain.
        **www.example.com** is entered in this topic.

    4.  **Protocol**: Select the protocols supported by the website. By default, **HTTP** and **HTTPS** are selected. In this topic, the default setting is used.

    5.  **Enable HTTP/2**: Select whether to enable HTTP/2 when the domain name is associated with an enhanced Anti-DDoS Pro instance. After HTTP/2 is enabled, the protocol type is HTTP 2.0.

    6.  **Server IP**: Select the address type of the origin server, and specify the address of the origin server. Select **Origin Server Domain** in this topic, and then enter the CNAME address that is assigned in Step 11. For more information, see [Step 11: Add website configurations in WAF](#section_3z7_1w8_7lv).

    7.  **Server Port**: Specify the server port based on the protocol. In this topic, the server port is **9000**.

6.  Click **Add**.


After you add a domain name, Anti-DDoS Pro assigns a CNAME address to the domain name.

![cname](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p99747.png)

## Step 14: Activate the CDN service

CDN reduces the workload of the origin server and prevents network congestion. You can use CDN to accelerate content delivery in different regions and for different scenarios.

To activate the CDN service, take the following steps:

1.  Log on to the [Alibaba Cloud CDN product page](https://www.alibabacloud.com/en/product/cdn).

2.  Click **Buy Now**.

3.  On the **Enable Service** page, select a **billing method**.

    For more information about CDN billing methods, see [CDN Pricing](https://www.alibabacloud.com/zh/product/cdn/pricing).

4.  Select the **I Agree with IP Application Accelerator Agreement of Service** check box, and click **Enable Now**.


## Step 15: Add an accelerated domain name

CDN retrieves resources from origins and caches them on CDN nodes. When clients request the resources from the accelerated domain name, CDN directly retrieves the resources from the CDN nodes to the clients.

To add an accelerated domain name, take the following steps:

1.  Log on to the [CDN console](https://cdn.console.aliyun.com).

2.  In the left-side navigation pane, click **Domain Names**.

3.  On the **Domain Names** page, click **Add Domain Name**.

4.  On the **Add Domain Name** page, configure the domain name.

    1.  **Domain Name to Accelerate**: Enter a domain name. **www.example.com** is entered in this topic.

        **Note:**

        -   You can use a subdomain name or a wildcard domain name as the accelerated domain name. Example: `cdntest.example.com`.
        -   Wildcard domain names are supported but domain names in Chinese are not supported. Follow the instructions to enter a wildcard domain name. Example: `*.test.com`. For more information, see [Rules for adding wildcard domain names]().
        -   You can add a domain name to CDN only once. If the **Domain already exists** error occurs, [submit a ticket](https://selfservice.console.aliyun.com/ticket/createIndex).
        -   If a wildcard domain has been added to CDN for an Alibaba Cloud account, you are not allowed to add the subdomains of the wildcard domain to CDN for other Alibaba Cloud accounts.
        -   You can add up to 50 accelerated domains for each account. To add more domains, [submit a ticket](https://selfservice.console.aliyun.com/ticket/createIndex).
        -   Content that is delivered from the domain must comply with the limits of Alibaba Cloud CDN. For more information, see [Limits](/intl.en-US/Product Introduction/Limits.md).
    2.  **Business Type**: Select the business type of your website.

        -   **Images and Small Files**: If you want to accelerate the delivery of small-size and static resources, such as small files, images, and web style sheets, we recommend that you select this option. For more information, see [Image and small file distribution](/intl.en-US/Product Introduction/Scenarios.md).
        -   **Large File Download**: For game package installation, app updates, mobile read-only memory \(ROM\) upgrades, and app downloads, we recommend that you select this option. For more information, see [Large file distribution](/intl.en-US/Product Introduction/Scenarios.md).
        -   **VOD**: If you want to accelerate the delivery of audio or video files for VOD playback, we recommend that you select this option. For more information, see [On-demand audio and video streaming](/intl.en-US/Product Introduction/Scenarios.md).
        -   **DCDN**: If your website contains a large amount of dynamic and static content, and most of the requests are for dynamic resources, we recommend that you select this option. For more information, see [What is Dynamic Route for CDN?]().
        **Images and Small Files** is selected in this topic.

    3.  **Origin Info**: Configure the information of the origin site.

        Select **Site Domain** in this topic, and then enter the CNAME that is assigned in Step 13. For more information, see [Step 13: Add a domain to Anti-DDoS Pro](#section_4fz_7a3_e7e).

    4.  **Port**: Select the access port of the website. Valid values:

        -   **Port 80**: Select this option if your website provides services over HTTP.
        -   **Port 443**: Select this option if your website provides services over HTTPS.
        **Port 80** is selected in this topic.

    5.  **Region**: Select a region. **Mainland China Only** is selected in this topic.

5.  Click **Next**.

    After you add an accelerated domain name, Alibaba Cloud CDN assigns a CNAME address to the accelerated domain name.

    ![cname](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p99749.png)


## Step 16: Resolve the website domain name to CDN

After you add the domain name, you must modify the DNS record to resolve the website domain name to CDN. Then, requests sent to the accelerated domain name can be forwarded to CDN nodes for acceleration.

**Note:** If you use a third-party DNS service, log on to the system of the DNS service provider to modify the DNS record for your website.

To resolve the domain name to CDN, take the following steps:

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com).

2.  On the **Manage DNS** page, find the target domain name, and click **Configure** in the **Actions** column.

3.  On the **Configure**page, find the DNS records, and click **Edit** in the **Actions** column.

4.  In **Edit Record** dialog box, set **Type** to **CNAME**, and set **Value** to the CNAME address that is assigned in Step 15. For more information, see [Step 15: Add an accelerated domain name](#section_0se_ywl_xwa).

    ![Edit the record](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9197449951/p45868.png)

5.  Click **OK**.


## Step 17: Verify the settings

In the China \(Hangzhou\), China \(Shanghai\), or China \(Shenzhen\) region, use a computer that runs Windows to test how your website is accelerated and protected by GA and other integrated services including CDN, Anti-DDoS Pro, WAF, and GTM.

1.  Enter the domain name www.example.com \(hosted in mainland China\) into the address bar of the web browser to access the website service deployed in the US \(Silicon Valley\) region.

    You can access the website service hosted in the US \(Silicon Valley\) region by using the domain name \(www.example.com\) in mainland China.

    ![Verify the settings](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1615588951/p96014.png)

2.  Run the `nslookup <CNAME access domain name in GTM>` command to check the resolution result.

    -   If the primary server group is available: The domain name is resolved to the IP address of Server 1 or Server 2. In this topic, the primary server group contains Server 1 and Server 2 that are deployed in the US \(Silicon Valley\) region.
    -   If the primary server group is unavailable: The domain name is resolved to the IP address of Server 3 or Server 4. In this topic, the primary server group contains Server 1 and Server 2 that are deployed in the US \(Silicon Valley\) region.
3.  Run the following command to check the latency of data packet transmission.

    `curl -o /dev/null -s -w "time_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" "http[s]://<the domain name of the website service>[:<port>]"`

    where:

    -   time\_connect: the period of time that it takes to establish a TCP connection.
    -   time\_starttransfer: the period of time that it takes for the backend server to send the first byte after the client sends a request.
    -   time\_total: the period of time that it takes for the backend server to respond to the session after the client sends a request.
    The test result shows that GA reduces the network latency when users from China \(Shanghai\), China \(Hangzhou\), and China \(Shenzhen\) access the website service deployed in the US \(Silicon Valley\) region.

    ![Before Global Accelerator is enabled](../images/p76785.png "Before Global Accelerator is enabled")

    ![After Global Accelerator is enabled](../images/p76786.png "After Global Accelerator is enabled")

    **Note:** The actual performance of the protection and acceleration services provided by GA, CDN, Anti-DDoS Pro, WAF, and GTM varies based on your workloads.



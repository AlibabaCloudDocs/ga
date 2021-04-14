# Cross-border website secure acceleration for domain names hosted outside China

Global Accelerator \(GA\) provides web service providers with a cross-border acceleration solution. GA integrates with Anti-DDoS Pro and Web Application Firewall \(WAF\). This defends against distributed denial-of-service \(DDoS\) attacks and web attacks based on high-bandwidth BGP lines and the global transmission network of Alibaba Cloud. Global Traffic Manager \(GTM\) can interact with GA to conduct fault isolation or traffic failovers.

An Alibaba Cloud account is created.If you do not have an Alibaba Cloud account,click Create an Alibaba Cloud accountCreate an Alibaba Cloud account.

A web application is deployed on Alibaba Cloud in the US \(Silicon Valley\) region. The origin servers are four Elastic Compute Service \(ECS\) instances associated with Alibaba Cloud elastic IP addresses \(EIPs\). The web application is deployed on the ECS instances and the domain name of the application is www.example.us that is registered outside China. The forwarding port is TCP port 9000.The following issues may occur for the web application:

-   The domain name of the web application is registered outside China and cannot be hosted on servers in mainland China. However, most of the users are located in mainland China.
-   The origin servers frequently suffer from web and DDoS attacks. These attacks severely affect the security and availability of the web application.
-   The cross-border Internet network is unstable. Network issues, such as network latency, network jitter, and packet loss, may frequently occur and degrade the performance of the website service.
-   The stability of the origin servers is not guaranteed. This may cause service disruption.

![Cross-border acceleration](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1553958951/p99440.png)

The preceding figure shows how to deploy GA to interact with Anti-DDoS Pro, WAF, and GTM.This can help you resolve the issues in the scenario of cross-border web application acceleration.

-   Anti-DDoS Pro can defend against DDoS attacks.

    The Anti-DDoS Pro service is deployed in tap mode. Anti-DDoS Pro is triggered in only some scenarios. The deployment and triggering methods ensure service quality when no DDoS attack occurs. The deployment and triggering methods enhances protection when DDoS attacks are detected.

-   GA can speed up content delivery for users in acceleration areas.

    Users in mainland China send requests to the Alibaba Cloud acceleration network from the access point in the China \(Hong Kong\) region. The system forwards the requests to the origin servers in US \(Silicon Valley\) by using intelligent routing and automatic network traffic distribution.

-   WAF can defend against multiple web attacks.

    WAF can detect and block malicious traffic from the Internet. Only normal network traffic is forwarded to the IP addresses of the origin servers. WAF ensures the security, stability, and availability of the origin servers.

-   GTM can be used to implement fault isolation and traffic failovers.
    -   When the primary server group is running in a proper way, all the user traffic is forwarded to the primary server group.
    -   When the primary server group becomes unavailable, user traffic is immediately switched to the secondary server group for failover. After the primary server group recovers, the traffic is switched back to the primary server group.

## Procedure

![Steps for accelerating traffic that flows to the domain name that is outside China](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1553958951/p99957.png)

## Step 1: Create a GTM instance

GTM is a traffic management service that allows you to manage network traffic from clients.

To create a GTM instance, perform the following steps:

1.  Log on to the Alibaba Cloud DNS consoleAlibaba Cloud DNS console.

2.  In the left-side navigation pane, click Global Traffic Manager.

3.  On the Global Traffic Manager page, click Create Instance.

4.  On the buy page, specify the following parameters for the GTM instance:

    1.  Version: By default, Standard Edition is selected and cannot be changed.

        The Standard Edition plan supports the following features:

        -   Health checks on IP addresses of application services.
        -   GeoDNS: switches your application workload to specified IP addresses based on the geographic locations of users.
        -   Disaster recovery policies for implementing DNS resolution service failovers.
        -   WRR: weighted round-robin load balancing policy.
    2.  Quantity: The number of GTM instances that you want to purchase.

    3.  Service Time: The service duration of the GTM instance.

5.  Click Buy Now and pay for the order.


## Step 2: Configure an access policy

Access policies allow GA to forward requests from different access points to different origin servers. You can also configure secondary origin servers to meet your business demands.

To configure access policies for GTM, perform the following steps:

1.  Log on to the Alibaba Cloud DNS consoleAlibaba Cloud DNS console.

2.  In the left-side navigation pane, click Global Traffic Manager.

3.  On the Global Traffic Manager page, find the GTM instance that you want to manage, click Configure in the Actions column.

4.  In the Select Configuration Method dialog box, select Quick Start.

5.  In the Access Policy Configurations wizard, specify the following parameters:

    1.  Policy Name: Enter a name for the access policy.

    2.  DNS Request Sources: Select a request source.

        After you specify a region as the request source, the requests sent by users in the region are distributed by GMT to the specified origin server address pool.Global is selected in this topic.

    3.  Default Address Pool: Select the default address pool.

        By default, GTM forwards user traffic to the IP addresses of the origin servers in the default address pool.

        In this topic, click + New Address Pool, add the IP addresses of Origin Server 1 and Origin Server 2 in US \(Silicon Valley\) to the address pool, enable the HTTP health check feature, and then specify the address pool as the default address pool.For more information about how to configure health checks,see TCP health check.

    4.  Alternative Address Pool: Select an alternative address pool.

        An alternative address pool is an IP address pool that contains IP addresses of secondary origin servers. GTM forwards requests to the secondary origin servers when the servers in the default address pool are unavailable.

        In this topic, click + New Address Pool, add Origin Server 3 and Origin Server 4 in US \(Silicon Valley\) to the alternative address pool, and configure the health check feature. Then, specify the address pool as an alternative address pool.For more information about how to configure health checks,see TCP health check.

6.  Click Next.


## Step 3: Configure basic information

After you configure the access policy, you must specify the basic information of the GTM instance, including the base domain name, CNAME address, server load balancing policy, global time-to-live \(TTL\) value, and alert group.

To configure the basic information for GTM, perform the following steps:

1.  In the Basic Information wizard, set the following parameters:

    1.  Instance Name: Enter an instance name.

        The instance name is used to identify the application service that runs on the instance.

    2.  Primary Domain: Enter a base domain name.www.example.us is entered in this topic.

    3.  CNAME Access Domain Name: Specify the type of the CNAME for the base domain name.

        -   Assigned Access Domain Name: Select this option if the IP address pool contains Alibaba Cloud IP addresses or IP addresses outside China.
        -   Custom Access Domain Name: Select this option if the IP address pool contains IP addresses of on-premises data centers.
        In this topic, the address pool of origin servers contains only Alibaba Cloud elastic IP addresses. Therefore, the Assigned Access Domain Name option is selected.

    4.  Balance Policy: Select a load balancing policy for GTM.

        -   Round Robin: distributes network traffic equally to multiple IP addresses in the IP address pool. This is the default policy.
        -   Weighted Round Robin: uses the pre-configured weighted round-robin policy to process DNS queries when the domain name is resolved to more than one IP address.
        Round Robin is selected in this topic.

    5.  Global TTL: The validity period of an IP address to which the domain name is resolved.1 minute\(s\) is selected in this topic.

        GTM provides traffic management services based on domain names. The Global TTL parameter specifies the validity period of the IP address cached in the DNS system of the service provider. By default, the parameter is set to 1 minute.If you use a custom domain name, the global TTL must be the same as the minimum TTL supported by the Alibaba Cloud DNS service plan of the custom domain name.

    6.  Alert Group: The contact group to which a notification is sent when an exception is detected in your workloads.

        **Note:**

        -   If you have not configured an alert group, log on to the Cloud Monitor console and add an alert group.For more information, see .
        -   Assume that you configured a contact group, but need to configure the basic information as a Resource Access Management \(RAM\) user. In this case, you must first use your Alibaba Cloud account to authorize the RAM user.After the RAM user is authorized, you can log on as a RAM user to read the alert group information.
2.  Click Complete.


After you configure the basic information, the system automatically allocates a CNAME address. Requests destined for the CNAME address are resolved to the IP address of the origin server.

![cname](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p99619.png)

## Step 4: Activate the WAF service

WAF is empowered by big data technologies of Alibaba Cloud Security. WAF allows you to defend against common web attacks, such as SQL injections, cross-site scripting \(XSS\), web shells, Trojans, unauthorized downloads, and HTTP flood attacks. WAF protects your web resources from exposure and ensures the security and availability of your website.

This topic describes how to purchase a subscription WAF instance.

1.  Visit the International site \(alibabacloud.com\),go to the WAF product landing pageWAF product landing page, and then log on to the console with your Alibaba Cloud account.

2.  Click Buy Now.

3.  On the Web Application Firewall page, specify the following parameters:

    1.  Region: Select the region where the WAF instance is deployed.

        In this topic, the WAF instance is located in US \(Silicon Valley\). Therefore, select International.

    2.  Plan: Select the version of WAF service to be activated.

        Different WAF service plans are applicable to different business scales and provide different protection features.For more information, see .Enterprise is selected in this topic.

    3.  Extra Domain: Specify the number of additional domain names.

        If you need to add multiple domains or more than 10 subdomains to WAF, you can purchase additional domains.For more information, see Additional domain.For this solution, you do not need to purchase additional domains.

    4.  Exclusive IP: Specify the number of exclusive IP addresses.

        You can purchase an exclusive IP address when your website domain name needs WAF protection through an exclusive IP address.For more information, see Exclusive IP.For this solution, you do not need to purchase a WAF exclusive IP.

    5.  Extra Traffic: Specify the size of the bandwidth extension plan to be purchased. Unit: Mbit/s.

        If the total bandwidth of your websites exceeds the bandwidth provided by WAF, you can purchase a bandwidth extension plan.For more information, see Bandwidth extension plan.100Mbps is selected in this topic.

    6.  GSLB: Select whether to enable Global Server Load Balancing \(GSLB\).

        GSLB uses the multi-node resilience technology. It supports automatic traffic distribution and disaster recovery based on multiple nodes and lines. You can use GSLB to improve the reliability of your service.No is selected in this topic.

    7.  Access Log Service: Select whether to enable Log Service.

        Log Service retrieves log data from WAF in real time and then stores the data in Logstores. You can query and analyze the log data, and generate analytics reports online.No is selected in this topic.

    8.  Bot Manager: Select whether to enable the Bot Manager feature.

        To mitigate security threats caused by bot traffic, you can enable Bot Manager.For more information, see and .No is selected in this topic.

    9.  Mobile App Protection: Select whether to enable mobile application protection.

        Your business supports native applications and you have security needs for your business, such as trusted communications and prevention of bot traffic. In this case, you can enable the mobile app protection feature.For more information, see .No is selected in this topic.

    10. Validity Period: Select the duration of the WAF service.

4.  Click Buy Now and pay for the order.


## Step 5: Add website configurations

After WAF is activated, you must configure forwarding rules for the website protected by WAF.

Perform the following steps to route user traffic to WAF before it reaches the domain name protected by WAF:

1.  Log on to the WAF consoleWAF console.

2.  In the top status bar, select the region of your WAF instance.International is selected in this topic.

3.  In the left-side navigation pane, choose **Asset Center** \> **Website Access**.

4.  On the page, click .

5.  On the page, click .

    **Note:** The page appears only when a qualified domain name exists.If does not appear, skip this step.

6.  Follow the Add Domain Name wizard to complete the configuration.

    1.  Domain Name: Enter the domain name that needs WAF protection. www.example.us is entered in this topic.

        **Note:**

        -   WAF supports exact match domains, such as www.aliyun.com and wildcard domain names, such as \*.aliyun.com.
            -   WAF protects all subdomains that match the specified wildcard domain name.
            -   If you configure both a wildcard domain name and a precise domain name for a website, routing methods and protection policies of the precise domain name prevail over those of the wildcard domain.
        -   Domain names suffixed with .edu are not supported.If you need to use a .edu domain name, submit a ticket to request technical support.
    2.  Protocol Type: Select the protocol supported by the website.HTTP is selected in this topic.

        **Note:**

        -   If your website supports HTTPS, select HTTPS, and upload the certificate and the private key file after you add the website configuration.For more information, see .
        -   After you select HTTPS, click Advanced Settings to enable the HTTP force redirect and HTTP back-to-origin features to ensure efficient access to your website.For more information, see .
        -   To enable protection for HTTP 2.0 requests, make sure that the following requirements are met:
            -   Your WAF instance is upgraded to the Business or Enterprise edition.
            -   HTTPS is selected.
    3.  Destination Server \(IP Address\): Select a server address type and enter the address of the origin server.

        Both IP and Destination Server \(Domain Name\) formats are supported.After you enable WAF protection for the website, WAF filters and redirects the requests to the specified IP address.In this topic, select Destination Server \(Domain Name\) and enter the CNAME domain name that is assigned to GTM after you configure the basic information in Step 3.For more information, see .

    4.  Destination Server Port: Specify the service port of the website.

        WAF forwards only connection and service requests sent to the specified origin server ports. It does not forward requests to the origin servers if the requests are destined for unspecified ports. Therefore, no security threats are posed on the origin server if you enable these ports or these ports have vulnerabilities.

        **Note:** Make sure that the protocol and port that you have specified in WAF are the same as those of the origin server whose IP address is specified as the server address. Port mapping is not allowed.

        The custom port 9000 is specified in this topic.

        **Note:** By default, WAF supports the following ports: HTTP ports 80 and 8080, and HTTPS ports 443 and 8443.WAF instances of the Business and Enterprise editions support more non-standard ports, and have corresponding limits on the total number of ports used by the protected domain name.For more information, see .

    5.  Load Balancing Algorithm: If multiple origin server IP addresses are specified, select IP hash or Round-robin.WAF distributes requests to these servers based on the specified algorithm.

    6.  Does a layer 7 proxy \(DDoS Protection/CDN, etc.\) exist in front of WAF: Select Yes or No based on the actual status of your website.Yes is selected in this topic.

    7.  Request Tag: Enter an unused Header Field Name and specify a custom Header Field Value to label the web requests that are redirected to the origin server through WAF.WAF adds the specified header field to the filtered requests. This enables your origin server to identify the requests redirected by WAF.

        **Note:** If a request already contains the specified header field, WAF overwrites the original field value with the specified value.

7.  Click Next.On the Add Domain Name page, click Copy CNAME to record the CNAME of WAF.

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


After the instance is created, the system automatically assigns a CNAME address to the instance. The CNAME address is used to resolve the domain name of the origin servers.

![CNAME](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p84125.png)

## Step 7: Purchase and bind a basic bandwidth plan

A basic bandwidth plan provides bandwidth for data transmission over the Internet and inside Alibaba Cloud. To achieve global acceleration, you need to purchase a basic bandwidth plan and bind the basic bandwidth plan to a Global Accelerator instance.

To purchase and bind a basic bandwidth plan to a Global Accelerator instance, follow these steps:

1.  On the **Instances** page, click **Buy Basic Bandwidth Plan**.

2.  On the buy page, set the following parameters of the basic bandwidth plan, click Buy Now, and then pay for the order.

    1.  Bandwidth Type: Select the type of the basic bandwidth plan.

        In this topic, the domain name of the origin server is registered outside China and cannot be hosted on servers in mainland China. Select Premium to allow users in mainland China to access the web services deployed in US \(Silicon Valley\) through the Premium Internet in China \(Hong Kong\).

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

    2.  Peak Bandwidth: Specify a value as the peak bandwidth for the basic bandwidth plan.10Mb is selected in this topic.

    3.  Duration: Select the duration of the basic bandwidth plan.

3.  Return to the **Instances** page, and click Instance ID.

4.  On the page that appears, click the **Bandwidth Manage** tab.

5.  In the Basic Bandwidth Package section, find the plan that you want to manage, and click Bind in the Actions column for the plan.

    ![Premium bandwidth](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1553958951/p99189.png)

    The basic bandwidth plan is now in the Bound state.


## Step 8: Add an acceleration area

After you purchase a basic bandwidth plan, you must add one or more acceleration areas where end users are located, and allocate bandwidth to these areas.

To add an acceleration area, follow these steps:

1.  On the Instances page, click the ID of the GA instance that is created in Step 6.

2.  On the Basic Information page, click the **Acceleration Areas** tab, and then click **Add Acceleration Area**.

3.  In the Add Acceleration Area dialog box, set the following parameters, and click OK:

    1.  Acceleration Area: Select the area that requires acceleration.In this topic, Asia Pacific is selected.

    2.  Regions: Select the region where users are located.Hong Kong is selected in this topic.

    3.  Bandwidth: Specify the amount of bandwidth to be allocated to the region.10 Mbit/s is selected in this topic.


After the acceleration area is added, GA assigns an accelerated IP address to each acceleration area to accelerate network traffic.

![Add an acceleration area](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2553958951/p99981.png)

## Step 9: Create a listener

A listener monitors connection requests from clients. Clients can connect to the specified port of the origin server through the specified protocol.

To add a listener to a Global Accelerator instance, follow these steps:

1.  On the Instances page, click the ID of the GA instance that is created in Step 6.

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

2.  Select the region to be associated with the endpoint group. This region is also the place where the origin servers are located.

    In this topic, the network traffic is forwarded to WAF. Therefore, select United States \(Silicon Valley\).

3.  Specify whether the origin servers are deployed on Alibaba Cloud or in the environments outside Alibaba Cloud.Off Alibaba Cloud is selected in this topic.

4.  Enable or disable the origin servers to reserve client IP addresses in the specified region.After the feature is enabled, origin servers can reserve client IP addresses.This feature is disabled in this topic.

    **Note:** This feature is available to only the accounts that are added to the whitelist. To use this feature,submit a ticketsubmit a ticket.

5.  Configure endpoints.

    1.  Backend Service Type: Select Custom Domain Name from the drop-down list.

    2.  Backend Service: Enter the IP address of the CNAME address assigned by WAF after you set website parameters in Step 5.For more information, see.

    3.  Weight: Specify a weight for the endpoint. Valid values: 0 to 255.GA routes traffic to endpoints based on the predefined weights.

        **Note:** If you set the weight of an endpoint to 0, GA stops to distribute network traffic to the endpoint. Proceed with caution.

    ![endpoint](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3947958951/p99230.png)

6.  Click **Next** to confirm the configurations, and then click **Next**.


## Step 11: Activate the Anti-DDoS Premium service

You can use Anti-DDoS Premium to reduce DDoS attacks launched to servers deployed outside mainland China.The Anti-DDoS Premium service filters out attack traffic in scrubbing centers that are deployed closest to visitors and forwards only normal network traffic back to the origin servers. This ensures the stability of your workloads.

To purchase an Anti-DDoS Premium instance, perform the following steps:

1.  Log on to the [Anti-DDoS Pro console](https://yundun.console.aliyun.com/?p=ddoscoo).

2.  On the **Instances** page, click **Purchase Instances**.

3.  On the buy page, complete the configuration to purchase an Anti-DDoS Premium instance.

    1.  Product Type: Select Anti-DDoS Premium.

    2.  Mitigation Plan: Select a mitigation plan for the Anti-DDoS Premium instance that you want to purchase.

        -   For more information about Insurance and Unlimited mitigation plans, see .
        -   For more information about Mainland China Access \(MCA\), see .
        The Unlimited plan is selected in this topic.

    3.  Clean Bandwidth: Select the clean bandwidth of the Anti-DDoS Premium instance.

        The clean bandwidth is the maximum traffic load of an Anti-DDoS instance when the instance is not under attacks.100Mbps is selected in this topic.

    4.  Function Plan: Select a function plan.

        You can select Standard Function or Enhanced Function.For more information about the differences between Standard Function and Enhanced Function, see .Enhanced Function is selected in this topic.

    5.  Domains: Select the number of HTTP/HTTPS domain names that can be protected by the instance.

        For more information about the number of protected domain names, see .10 is selected in this topic.

    6.  Clean QPS: Set the clean queries per second \(QPS\).

        This parameter specifies the maximum number of concurrent HTTP or HTTPS requests that the instance can process when no attack occurs.3000 is selected in this topic.

    7.  Ports: Select the number of supported ports.

        The number of protected ports equals the maximum number of entries supported for TCP/UDP forwarding.50 is selected in this topic.

    8.  Quantity: Select the number of instances to be purchased with the specified configurations.

    9.  Subscription: Select the subscription period of the Anti-DDoS Premium instance.

4.  Click Buy Now and pay for the order.


## Step 12: Add website configurations

The configurations of a website specified in the Anti-DDoS Pro console define how network traffic is transmitted between a website and an Anti-DDoS Pro instance.

Follow these steps to add the website that needs protection to Anti-DDoS Pro:

1.  Log on to the [Anti-DDoS Pro console](https://yundun.console.aliyun.com/?p=ddoscoo).

2.  In the top status bar, select the region where the service is deployed.Outside Mainland China is selected in this topic.

3.  In the left-side navigation pane, choose **Provisioning** \> **Website Config**.

4.  On the **Website Config** page, click **Add Domain**.

5.  On the Add Domain page, enter the website information.

    1.  Function Plan: Select a function plan for the Anti-DDoS Premium instance that you want to associate with your website.

        Standard and Enhanced are available. For more information, see .Enhanced is selected in this topic.

    2.  **Instance**: Select the Anti-DDoS Pro instance to be associated. You can select up to eight instances for one domain. The instances associated with a domain must use the same function plan.

    3.  Domain: Enter the website domain name that requires protection. www.example.us is entered in this topic.

    4.  **Protocol**: Select the protocols supported by the website. By default, **HTTP** and **HTTPS** are selected. This topic uses the default setting.

    5.  Server IP: Select the address type of the origin server, and specify the address of the origin server.In this topic, select Origin Server IP and enter the accelerated IP address that the GA instance assigns to the China \(Hong Kong\) region after you add the acceleration area in Step 8.For more information, see .

    6.  Server Port: Specify a server port based on the protocol type. In this topic, the server port is 9000.

6.  Click Add.


## Step 13: Set parameters of Sec-Traffic Manager

Anti-DDoS Pro provides Sec-Traffic Manager to set the interaction rules between Anti-DDoS Pro and other cloud resources. You can set rules to trigger and enable Anti-DDoS Pro in specific scenarios. This helps you keep workloads running smoothly if no DDoS attacks occur, and provides more effective protection when DDoS attacks occur.

To configure Sec-Traffic Manager, follow these steps:

1.  Log on to the [Anti-DDoS Pro console](https://yundun.console.aliyun.com/?p=ddoscoo).

2.  In the top status bar, select the region of the service.Outside Mainland China is selected in this topic.

3.  In the left-side navigation pane, choose **Provisioning** \> **Sec-Traffic Manager**.

4.  On the **Cloud Service Interaction** tab, click **Create Rule**.

5.  In the Create Rule dialog box, specify the following parameters:

    1.  **Interaction Scenario**: Select an interaction scenario for the rule. In this topic, select **Cloud Service Interaction**.

    2.  **Name**: Enter the rule name.

        The name can be 1 to 128 characters in length and can contain letters, digits, and underscores \(\_\).

    3.  Anti-DDoS Instance IP: Select the Anti-DDoS instance that you want to associate with.In this topic, the Anti-DDoS Premium instance that you create in Step 11 is selected.

    4.  Cloud Service: Select the region where the cloud resource is deployed, and then enter the IP address of the cloud resource.

        You can click Add Cloud Resource IP to add more cloud resources.You can add up to 20 cloud resources.

        Select cn-hongkong, and enter the accelerated IP address that the GA instance assigns to the China \(Hong Kong\) region after you add the accelerated area in Step 8.For more information, see .

    5.  The waiting time of switching back: Set the waiting time before the switchback process is triggered.

        Black hole deactivation consumes some time. Frequent switchback is not recommended. Therefore, the minimum value of this parameter is 30 minutes.The waiting time is set to 60 minutes in this topic.

6.  Click Next.

7.  Click **Finished**.

    After a rule is created, Sec-Traffic Manager assigns a CNAME address to this rule.

    ![Sec-Traffic Manager](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2553958951/p95809.png)


## Step 14: Resolve the domain name to Sec-Traffic Manager

After you create a scheduling rule in Sec-Traffic Manager, you must update the CNAME record of the domain to redirect website traffic from mainland China to Sec-Traffic Manager. The rule takes effect only after you update the CNAME record.

**Note:** If you use a third-party DNS service, log on to the system of the DNS service provider to modify the DNS record of your website.

To resolve the domain name to Sec-Traffic Manager, follow these steps:

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com).

2.  On the **Manage DNS** page, find the target domain name, and click **Configure** in the **Actions** column.

3.  On the DNS Settings page, click Add Record.

4.  In the Add Record panel, configure the record, and click Confirm.

    1.  Type: Select a record type.

        In this topic, the website domain name is mapped to another domain name. Therefore, CNAME is selected.

    2.  Host: Enter the prefix of the accelerated domain name.

        www is entered in this topic.

    3.  ISP Line: Select Default from the drop-down list.

    4.  Value: Set this parameter to the CNAME address assigned in Step 13.For more information, see .

    5.  TTL: The TTL value of the IP address that is mapped to the specified domain name.

        10 minute\(s\) is selected in this topic.

    ![Add CNAME records](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2553958951/p100157.png)

5.  Repeat the preceding steps to add CNAME records for ISP lines provided by China Unicom, China Telecom, China Mobile, and China Education Network.

    ![Add CNAME records](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2553958951/p100160.png)


## Step 15: Verify the settings

In regions of mainland China, use a computer that runs Windows to verify the settings of the protection and acceleration services after GA interacts with CDN, Anti-DDoS Pro, WAF, and GTM.

1.  The domain name www.example.us is hosted outside mainland China. Enter the domain name into the address bar of the web browser to access the website application deployed in US \(Silicon Valley\).

    You can access the website services deployed in US \(Silicon Valley\) through the domain name www.example.us.

    ![Verify the settings](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1615588951/p96014.png)

2.  Open the Command Prompt, and run the nslookup <web service domain name\> command to check the DNS resolution result.

    -   When the origin server is not attacked, the IP address of the GA instance is returned.
    -   When the origin server is under attack, the IP address of Anti-DDoS Premium is returned.
3.  Run the nslookup <CNAME access domain name in GTM\> command to check the resolution result.

    -   If the primary server group is available: The domain name is resolved to the IP address of Server 1 or Server 2. In this topic, the primary server group contains Server 1 and Server 2 that are deployed in the US \(Silicon Valley\) region.
    -   If the primary server group is unavailable: The domain name is resolved to the IP address of Server 3 or Server 4. In this topic, the primary server group contains Server 1 and Server 2 that are deployed in the US \(Silicon Valley\) region.
4.  Run the following command to test the latency of data transmission:

    curl -o /dev/null -s -w "time\_connect: %\{time\_connect\}\\ntime\_starttransfer: %\{time\_starttransfer\}\\ntime\_total: %\{time\_total\}\\n" "http\[s\]://<the domain name of the web service\>\[:<port\>\]"

    In the request:

    -   time\_connect: The amount of time that it takes to establish a TCP connection.
    -   time\_starttransfer: The data transmission start time. It refers to the time period from when a client sends a request to when a backend server responds to the first byte.
    -   time\_total: The total connection time. It refers to the time period from when a client sends a connection request to when a backend server responds to the request.
    GA reduces the network latency when users from mainland China access the web application services deployed in US \(Silicon Valley\).

    ![The latency of data transmission before GA is used](../images/p76785.png "The latency of data transmission before GA is used")

    ![The latency of data transmission after GA is used](../images/p76786.png "The latency of data transmission after GA is used")

    **Note:** The actual performance of the protection and acceleration services provided by GA, Anti-DDoS Premium, WAF, and GTM varies based on your workloads.



# Integrate GA with Anti-DDoS Pro to accelerate applications

Global Accelerator \(GA\) allows you to accelerate cross-region access to your services by using high-quality Border Gateway Protocol \(BGP\) bandwidth and global networks provided by Alibaba Cloud. You can integrate GA with Anti-DDoS Pro to scrub requests before they are accelerated by GA. This prevents your servers from DDoS attacks and accelerates data transfer across regions for your services.

Before you start, make sure that the following requirements are met:

-   An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account,[create one](https://account.alibabacloud.com/register/intl_register.htm).
-   An Internet Content Provider \(ICP\) number is obtained.

A service is deployed on Alibaba Cloud in the US \(Silicon Valley\) region. The backend server uses two elastic IP addresses \(EIPs\) to provide services over the Internet. TCP port 9000 is used as the forwarding port. Most clients are from the China \(Shanghai\), China \(Hangzhou\), and China \(Shenzhen\) regions. The service frequently suffers large-scale DDoS attacks.

![Architecture](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0195616951/p95599.png)

You can create a GA instance, and specify China \(Shanghai\), China \(Hangzhou\), and China \(Shenzhen\) as the accelerated regions. Then, you can integrate GA with Anti-DDoS Pro, as shown in the preceding figure. After you complete the preceding steps, requests over the Internet are scrubbed by Anti-DDoS Pro. Malicious requests are blocked and normal requests are forwarded to backend servers based on the forwarding protocol. Requests from the China \(Shanghai\), China \(Hangzhou\), and China \(Shenzhen\) regions are accelerated in the nearest access points. Then, requests are forwarded to optimal endpoints based on intelligent routing and scheduling algorithms. This avoids network congestion and reduces network latency.

## Procedure

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0195616951/p95713.png)

## Step 1: Create a GA instance

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


## Step 2: Purchase and bind a basic bandwidth plan to the GA instance

A basic bandwidth plan provides bandwidth for data transfer over the Internet and within Alibaba Cloud. To achieve global acceleration, you must purchase a basic bandwidth plan and bind it to the GA instance.

1.  On the **Instances** page, click **Purchase Basic Bandwidth Plan**.

2.  On the buy page, set the parameters, click **Buy Now**, and then complete the payment.

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
    2.  **Peak Bandwidth**: Select a maximum bandwidth value for the basic bandwidth plan. **10Mb** is selected in this example.

    3.  **Duration**: Select the duration of the basic bandwidth plan.

3.  Return to the **Instances** page, and click the ID of the GA instance that you created in Step 1.

4.  On the page that appears, click the **Bandwidth Manage** tab.

5.  In the **Basic Bandwidth Package** section, find the basic bandwidth plan and click **Bind** in the **Actions** column.

    ![Bind the basic bandwidth plan to the GA instance](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1615588951/p95529.png)

    After the basic bandwidth plan is bound to the GA instance, the basic bandwidth plan is in the **Bound** state.


## Step 3: Specify a region to be accelerated

After you purchase a basic bandwidth plan, you can specify a region to be accelerated and allocate bandwidth resources used for acceleration.

1.  On the **Instances** page, click the ID of the GA instance that you created in [Step 1](#section_l1r_uk0_vfj).

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


## Step 4: Create a listener

A listener is used to check requests from clients. The system forwards requests based on the specified protocol and port.

1.  On the **Instances** page, click the ID of the GA instance that you created in [Step 1: Create a GA instance](#section_l1r_uk0_vfj).

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

5.  On the **Confirm** page, check the configurations of the listener and endpoint group. After you confirm the configurations, click **Submit**.


## Step 5: Purchase and bind a bandwidth plan for cross-border acceleration

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


## Step 6: Purchase an Anti-DDoS Pro instance

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


## Step 7: Create forwarding rules

Port configurations define Layer 4 forwarding rules for the Anti-DDoS Pro instance.

1.  Log on to the [Anti-DDoS Pro console](https://yundun.console.aliyun.com/?p=ddoscoo).

2.  In the left-side navigation pane, choose **Provisioning** \> **Port Config**.

3.  In the top navigation bar, select the region where the service is deployed.

    In this example, traffic is scrubbed by Anti-DDoS Pro and then forwarded to GA. Therefore, **Mainland China** is selected.

4.  On the **Port Config** page, select the Anti-DDoS Pro instance that you want to manage, and click **Create Rule**.

5.  In the **Create Rule** dialog box, set the parameters and click **OK**.

    1.  **Forwarding Protocol**: Select a protocol that is used to forward requests. In example, **TCP** is selected.

    2.  **Forwarding Port**: Enter the forwarding port used by the Anti-DDoS Pro instance. In this topic, **9000** is used.

    3.  **Origin Server Port**: Enter the port used by the origin server. In this example, **9000** is used.

    4.  **Origin Server IP**: Enter the IP address of the origin server. In this example, the IP addresses that are assigned to the China \(Shanghai\), China \(Hangzhou\), and China \(Shenzhen\) regions in Step 3 are used.

    ![Add a forwarding port](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1195616951/p95892.png)


## Step 8: Test the connectivity

Perform the following steps to test the protection and acceleration services provided by Anti-DDoS Pro and GA.

1.  Open a browser in an accelerated region. In this example, accelerated regions include China \(Hangzhou\), China \(Shanghai\), and China \(Shenzhen\)

2.  Enter the IP address and forwarding port of Anti-DDoS Pro to access the service that is deployed in the US \(Silicon Valley\) region.

    The result shows that you can access the service deployed in the US \(Silicon Valley\) region by using the IP address and forwarding port of Anti-DDoS Pro.

    ![Test the connectivity](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1195616951/p95861.png)

3.  Open Command Prompt on a computer in an accelerated region. In this example, accelerated regions include China \(Hangzhou\), China \(Shanghai\), and China \(Shenzhen\)

4.  Run the following command to query the network latency:

    `curl -o /dev/null -s -w "time_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" "http[s]://<IP address of Anti-DDoS Pro\>\[:<port\>\]"`

    where:

    -   time\_connect: the period of time that it takes to establish a TCP connection.
    -   time\_starttransfer: the period of time that it takes for the backend server to send the first byte after the client sends a request.
    -   time\_total: the period of time that it takes for the backend server to respond to the session after the client sends a request.
    The result shows that the network latency is reduced by GA when clients from the China \(Shanghai\), China \(Hangzhou\), and China \(Shenzhen\) regions access the service deployed in the US \(Silicon Valley\) region.

    ![The network latency of data transmission before GA is used](../images/p76785.png "The network latency of data transmission before GA is used")

    ![The network latency of data transmission after GA is used](../images/p76786.png "The network latency of data transmission after GA is used")

    **Note:** The preceding result is for reference only. The actual performance is based on the environment and workloads.



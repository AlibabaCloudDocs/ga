---
keyword: [configure the basic settings and protocol of listeners, configure SSL certificates, configure endpoint groups]
---

# Create a listener

After you create a Global Accelerator \(GA\) instance, you must configure listeners for the instance. A listener checks connection requests and distributes the requests to endpoints based on forwarding rules that are defined by the scheduling algorithm.

-   A GA instance is created. For more information, see [Create a GA instance](/intl.en-US/User Guide/Global Accelerator instances/Create a GA instance.md).
-   HTTP and HTTPS listeners are available for only Alibaba Cloud accounts that are included in the whitelist. To create HTTP or HTTPS listeners,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).
-   If you want to configure HTTPS listeners, make sure that a certificate signing request is submitted to CA and an SSL certificate is purchased. For more information, see[Select and purchase certificates](https://www.alibabacloud.com/help/zh/doc-detail/28542.htm?spm=a2c63.p38356.b99.28.34582356bpg5Lj) and [Apply for a certificate](/intl.en-US/Issue Certificates/Apply for a certificate.md).

## Create a TCP or UDP listener

1.  Configure the listener and protocol.

    1.  Log on to the [GA console](https://ga.console.aliyun.com/list).

    2.  On the **Instances** page, find the GA instance that you want to manage and click **Configure Listeners** in the **Actions** column.

    3.  On the **Listeners** tab, click **Add Listener**.

        **Note:** If this is your first time creating a listener, skip the step.

    4.  On the **Configure Listener & Protocol** wizard page, set the following parameters.

        |Parameter|Description|
        |---------|-----------|
        |**Listener Name**|Enter a name for the listener. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |
        |**Protocol**|Select a protocol for the listener. Valid values:         -   **TCP**: TCP has the following features:
            -   TCP is a connection-oriented protocol that provides high reliability. Before you start to transmit data, you must establish a stable connection with the peer.
            -   Session persistence is based on source IP addresses.
            -   Source IP addresses are visible at the network layer.
            -   Data is transmitted at a slow rate.
        -   **UDP**: UDP has the following features:
            -   UDP is unreliable and not connection-oriented. Three-way handshakes are not required before UDP packets are transmitted. UDP does not support fault tolerance and retransmission.
            -   Data is transmitted at a high rate. |
        |**Port Number**|Specify ports for the listener. The listener ports are used to receive requests and forward requests to endpoints. Valid values: **1 to 65499**. You can specify at most 30 listener ports for each listener. Separate multiple listener ports with commas \(,\). For example: 80,90,8080.

If you want to specify consecutive ports, you can use a tilde \(~\). For example: 80~85.

**Note:**

        -   If listeners that are added to the same GA instance use the same protocol, the listeners must be configured with different listener ports.
        -   You can specify more than 300 listener ports for a listener in specific regions. For more information, see [Listener ports](/intl.en-US/User Guide/Listeners/Overview.md). |
        |**Client Affinity**|Specify whether to enable client affinity.         -   If you select **Source IP Address** from the drop-down list, client affinity is enabled. After client affinity is enabled, requests from a specific client IP address are forwarded to the same endpoint.
        -   If you select **Disable**, client affinity is disabled. After client affinity is disabled, requests from a specific client IP address may be forwarded to different endpoints. |

    5.  Click **Next**.

2.  Configure an endpoint group.

    To associate a listener with an endpoint group, you can specify the region to which you want to distribute network traffic. After the listener forwards network traffic to the associated endpoint group based on association rules, GA distributes network traffic to the optimal endpoints of the endpoint group.

    1.  Set the following parameters to configure endpoints and an endpoint group.

        |Parameter|Description|
        |---------|-----------|
        |**Endpoint Group Name**|Enter a name for the endpoint group. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). The name must start with a letter. |
        |**Region**|Select the region where you want to deploy the endpoint group.|
        |**Backend Service**|Select the region where you want to deploy backend servers.         -   **Alibaba Cloud**: Backend servers are deployed on Alibaba Cloud.
        -   **Off Alibaba Cloud**: Backend servers are not deployed on Alibaba Cloud. |
        |**Reserve Client IP**|Specify whether to reserve client IP addresses. After this feature is enabled, backend servers can obtain client IP addresses. For more information, see [Preserve client IP addresses](/intl.en-US/Deployment & Maintenance/Preserve client IP addresses.md).

**Note:** This feature is available to only the Alibaba Cloud accounts that are included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex). |
        |**Endpoint**|An endpoint is a destination server to which client requests are forwarded. Set the following parameters to configure an endpoint:         -   **Backend Service Type**: If you set Backend Service to Alibaba Cloud, you can select **Alibaba Cloud Public IP Address**, **ECS**, or **SLB**. If you set Backend Service to Off Alibaba Cloud, you can select **Custom IP Address** or **Custom Domain Name**.

**Note:**

            -   You can specify Elastic Compute Service \(ECS\) or Server Load Balancer \(SLB\) as the backend service type only when your Alibaba Cloud account is included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).
            -   You can set the endpoint type to ECS or SLB. In this case, if no service-linked role is created, the system automatically creates the service-linked role AliyunServiceRoleForGaVpcEndpoint. For more information, see [AliyunServiceRoleForGaVpcEndpoint](/intl.en-US/User Guide/Service-linked role/AliyunServiceRoleForGaVpcEndpoint.md).
        -   **Backend Service**: Enter the IP address or domain name of the backend server.
        -   **Weight**: Enter a weight for the endpoint. Valid values: **0 to 255**. GA routes traffic to endpoints based on the specified weights.

**Note:** If you set the weight of an endpoint to 0, GA stops distributing network traffic to the endpoint. Proceed with caution.

You can click **+ Add Endpoint** to add more endpoints. You can create up to four endpoints in each endpoint group. |

    2.  Click **Next**.

3.  View configurations.

    1.  On the **Confirm** page, view configurations.

        If you want to modify a specific setting, click **Modify** that corresponds to the setting. Then, you are redirected to the configuration page.

    2.  After you confirm the configurations, click **Submit**.


## Create an HTTP or HTTPS listener

1.  Configure the listener and protocol.

    1.  Log on to the [GA console](https://ga.console.aliyun.com/list).

    2.  On the **Instances** page, find the GA instance that you want to manage and click **Configure Listeners** in the **Actions** column.

    3.  On the **Listeners** tab, click **Add Listener**.

        **Note:** If this is your first time creating a listener, skip the step.

    4.  On the **Configure Listener & Protocol** wizard page, set the following parameters.

        |Parameter|Description|
        |---------|-----------|
        |**Listener Name**|Enter a name for the listener. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |
        |**Protocol**|Select a network transmission protocol for the listener:         -   **HTTPS**: HTTPS has the following features:
            -   HTTPS is a connection-oriented protocol that provides high reliability. Before you start to transmit data, you must establish a stable connection with the peer.
            -   You can bind SSL certificates to servers. This ensures the high reliability of data.
            -   Data transmission is encrypted.
        -   **HTTP**: HTTP has the following features:
            -   HTTP is a connection-oriented protocol that provides high reliability. Before you start to transmit data, you must establish a stable connection with the peer.
            -   Data is transmitted at a fast rate.
            -   Data transmission is not encrypted. |
        |**Port Number**|Specify the listener port for the listener. The listener port is used to receive requests and forward requests to endpoints. Valid values: **1 to 65499**. You can configure only one listener port for each HTTP or HTTPS listener. |
        |**Client Affinity**|Specify whether to enable client affinity.         -   If you select **Source IP Address** from the drop-down list, client affinity is enabled. After client affinity is enabled, requests from a specific client IP address are forwarded to the same endpoint.
        -   If you select **Disable**, client affinity is disabled. After client affinity is disabled, requests from a specific client IP address may be forwarded to different endpoints. |

2.  Optional. Configure the SSL certificate

    You are required to add an SSL certificate only when you configure an HTTPS listener. SSL certificates ensure that data transmission over GA is encrypted.

    1.  On the **Configure SSL Certificate** page, select the SSL certificate that you have requested.

    2.  Click **Next** to configure the endpoint group.

3.  Configure the endpoint group.

    To associate a listener with an endpoint group, you can specify the region to which you want to distribute network traffic. After the listener forwards network traffic to the associated endpoint group based on association rules, GA distributes network traffic to the optimal endpoints of the endpoint group.

    1.  To configure an endpoint group, set the following parameters.

        |Parameter|Description|
        |---------|-----------|
        |**Endpoint Group Name**|Enter a name for the endpoint group. The name must be 2 to 128 characters in length, and can contain letters, digits, underscores \(\_\), and hyphens \(-\). The name must start with a letter. |
        |**Region**|Select the region where you want to deploy the endpoint group.|
        |**Backend Service**|Select whether backend services are deployed on Alibaba Cloud.         -   **Alibaba Cloud**: specifies that backend services are deployed on Alibaba Cloud.
        -   **Off Alibaba Cloud**: specifies that backend services are not deployed on Alibaba Cloud. |
        |**Reserve Client IP**|Specify whether to reserve client IP addresses. After this feature is enabled, backend servers can obtain client IP addresses. For more information, see [Preserve client IP addresses](/intl.en-US/Deployment & Maintenance/Preserve client IP addresses.md).

**Note:** This feature is available to only Alibaba Cloud accounts that are included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex). |
        |**Endpoint**|An endpoint serves as the destination that a client requests to access. Set the following parameters to configure an endpoint:         -   **Backend Service Type**: If you set Backend Service to Alibaba Cloud, you can select **Alibaba Cloud Public IP Address**, **ECS**, or **SLB**. If you set Backend Service to Off Alibaba Cloud, you can select **Custom IP Address** or **Custom Domain Name**.

**Note:**

            -   You can specify an Elastic Compute Service \(ECS\) or Server Load Balancer \(SLB\) instance as an endpoint only if your Alibaba Cloud account is included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).
            -   If no service-linked role exists when you specify an ECS or SLB instance as an endpoint, the system automatically creates the service-linked role AliyunServiceRoleForGaVpcEndpoint. For more information, see [AliyunServiceRoleForGaVpcEndpoint](/intl.en-US/User Guide/Service-linked role/AliyunServiceRoleForGaVpcEndpoint.md).
        -   **Backend Service**: Enter the IP address or domain name of the origin server.
        -   **Weight**: Enter a weight for the endpoint. Valid values: **0 to 255**. GA routes network traffic to each endpoint based on the proportion of each endpoint.

**Note:** If you set the weight of an endpoint to 0, GA stops routing network traffic to the endpoint. Proceed with caution.

You can click **+ Add Endpoint** to add more endpoints. You can create at most four endpoints for each endpoint group. |
        |**Backend Service Protocol**|Select the protocol that the backend server uses. Valid values:        -   **HTTP**
        -   **HTTPS**
**Note:**

        -   This is the default value. If the listener protocol is HTTP, this parameter is set to HTTP and cannot be modified.
        -   You can set **Backend Service Protocol** and **Port Mapping** only when you configure an endpoint group for an HTTP or HTTPS listener. |
        |**Port Mapping**|If the listener port is not the same port over which the endpoint provides services, you must set this parameter.         -   **Listener Port**: Enter the listener port.
        -   **Endpoint Port**: Enter the port over which the endpoint provides services.
If the listener port is the same port over which the endpoint provides services, ignore this parameter. GA automatically forwards requests to the listener port of the endpoint. |

    2.  Click **Next**.

4.  View configurations.

    1.  On the **Confirm** page, view configurations.

        If you want to modify a specific setting, click **Modify** that corresponds to the setting. Then, you are redirected to the configuration page.

    2.  After you confirm the configurations, click **Submit**.


**Note:** After you create an HTTP or HTTPS listener, you can configure a virtual endpoint group and a forwarding rule for the listener. Then, GA can simultaneously accelerate multiple domain names or paths to access your backend HTTP or HTTPS services. For more information, see [Create an endpoint group](/intl.en-US/User Guide/Endpoint groups and endpoints/Create an endpoint group.md) and [Manage forwarding rules](/intl.en-US/User Guide/Endpoint groups and endpoints/Manage forwarding rules.md).

For more information, see [Use only one GA instance to accelerate multiple domain names over HTTPS](/intl.en-US/Best practices/Use only one GA instance to accelerate multiple domain names over HTTPS.md).

**Related topics**  


[CreateListener](/intl.en-US/API reference/Listeners/CreateListener.md)


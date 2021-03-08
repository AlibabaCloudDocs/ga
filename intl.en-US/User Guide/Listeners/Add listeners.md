---
keyword: [configure the basic settings and protocol of listeners, configure SSL certificates, configure endpoint groups]
---

# Add listeners

After you create a Global Accelerator \(GA\) instance, you must configure listeners for the instance. A listener checks connection requests and distributes the requests to endpoints. These requests are distributed based on the forwarding rules that are defined by the scheduling algorithm.

-   A GA instance is created. For more information, see [Create a GA instance](/intl.en-US/User Guide/Global Accelerator instances/Create a GA instance.md).
-   To configure HTTPS listeners, make sure that the following conditions are met:
    -   HTTPS listeners are available to only the accounts that are included in the whitelist. If you want to create HTTPS listeners but you are not included in the whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).
    -   You have purchased an SSL certificate and have applied for the certificate. For more information, see [Select and purchase certificates](https://www.alibabacloud.com/help/zh/doc-detail/28542.htm?spm=a2c63.p38356.b99.28.34582356bpg5Lj) and [Apply for certificates](https://www.alibabacloud.com/help/zh/doc-detail/98574.htm?spm=a2c63.p38356.b99.31.401e1edbEf7oJN).

## Step 1: Configure the basic setting and protocol of a listener

A listener monitors connection requests from clients and forwards the connection requests to origin servers based on the specified protocol and ports.

To add a listener to a GA instance and configure the basic setting and protocol of the listener, perform the following steps:

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the GA instance that you want to manage and click **Configure Listeners** in the **Actions** column.

3.  On the **Listeners** tab, click **Add Listener**.

4.  On the **Configure Listener & Protocol** wizard page, set the required parameters to configure the basic settings and protocol of the listener.

    |Parameter|Description|
    |---------|-----------|
    |**Listener Name**|Enter a name for the listener. The name must be 2 to 128 characters in length, and can contain letters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |
    |**Protocol**|Select a protocol for the listener. Valid values:     -   **TCP**: TCP has the following features:
        -   TCP is a connection-oriented protocol that provides high reliability. Before you start to transmit data, you must establish a stable connection with the peer.
        -   Session persistence is based on source IP addresses.
        -   Source IP addresses are visible at the network layer.
        -   Data transmission is slow.
    -   **UDP**: UDP has the following features:
        -   UDP is connectionless and unreliable. Three-way handshake is not required before UDP packets are transmitted. UDP does not support fault tolerance and retransmission.
        -   Data transmission is fast.
    -   **HTTPS**: HTTPS has the following features:
        -   HTTPS is a connection-oriented protocol that provides high reliability. Before you start to transmit data, you must establish a stable connection with the peer.
        -   You can bind SSL certificates to servers. This ensures the high reliability of data.
        -   Data transmission is encrypted. |
    |**Port Number**|Specify ports for the listener. The listening ports are used to receive requests and forward requests to endpoints. Valid values: **1 to 65499**.You can specify a maximum of 30 listening ports for each listener. If you need to specify more than one listening port, separate the listening ports with commas \(,\), for example, 80,90,8080.

If you want to specify a range of ports, you can use a tilde \(~\), for example, 80~85.

**Note:**

    -   If listeners that are added to the same GA instance use the same protocol, the listeners must be configured with different listening ports.
    -   You can specify more than 300 listening ports for a listener in specific regions. For more information, see [Listening ports](/intl.en-US/User Guide/Listeners/Overview.md). |
    |**Client Affinity**|Enable or disable client affinity.     -   If you select **Source IP Address** from the drop-down list, client affinity is enabled. After client affinity is enabled, requests from a specific client IP address are forwarded to the same endpoint.
    -   If you select **Disable**, client affinity is disabled. After client affinity is disabled, requests from a specific client IP address may be forwarded to different endpoints. |

5.  Click **Next**.


## \(Optional\) Step 2: Configure an SSL certificate

You are required to add SSL certificates only when you create HTTPS listeners. SSL certificates ensure encrypted data transmission over HTTPS.

1.  On the **Configure SSL Certificate** wizard page, set the required parameters for the SSL certificate.

    |Parameter|Description|
    |---------|-----------|
    |**Server Certificate**|Select the SSL certificate for which you have applied.|
    |**Backend Port**|Enter a server port for the origin server. Valid values: **1 to 65499**. Example: 80.|

2.  Click **Next** to configure an endpoint group.


## Step 3: Configure an endpoint group

To associate a listener with an endpoint group, you can specify the region to which you want to distribute network traffic. After the listener forwards network traffic to the associated endpoint group based on association rules, GA distributes network traffic to the optimal endpoints of the endpoint group.

1.  To configure an endpoint group, set the following parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Endpoint Group Name**|Enter a name for the endpoint group. The name must be 2 to 128 characters in length, and can contain letters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |
    |**Region**|Select the region where you want to deploy the endpoint group.|
    |**Backend Service**|Select the region where you want to deploy backend servers.     -   **Alibaba Cloud**: specifies that backend servers are deployed on Alibaba Cloud.
    -   **Off Alibaba Cloud**: specifies that backend servers are not deployed on Alibaba Cloud. |
    |**Reserve Client IP**|Enable or disable backend servers to reserve client IP addresses. After this feature is enabled, backend servers can obtain client IP addresses. For more information, see [Preserve client IP addresses](/intl.en-US/Deployment & Maintenance/Preserve client IP addresses.md).

**Note:** This feature is available to only the accounts that are included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex). |
    |**Endpoint**|An endpoint is an origin server to which client requests are forwarded. Set the following parameters to configure an endpoint:     -   **Backend Service Type**: If you set Backend Service to Alibaba Cloud, you can select **Alibaba Cloud Public IP Address**, **ECS**, or **SLB**. If you set Backend Service to Off Alibaba Cloud, you can select **Custom IP Address** or **Custom Domain Name**.

**Note:**

        -   You can specify Elastic Compute Service \(ECS\) or Sever Load Balancer \(SLB\) as the backend service type only when your account is included in the whitelist of GA. If you want to use this feature but you are not included in the whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).
        -   You can set the endpoint type to ECS or SLB. In this case, if no service-linked role is created, the system automatically creates the service-linked role AliyunServiceRoleForGaVpcEndpoint. For more information, see [AliyunServiceRoleForGaVpcEndpoint](/intl.en-US/User Guide/Service-linked role/AliyunServiceRoleForGaVpcEndpoint.md).
    -   **Backend Service**: Enter the IP address or domain name of the origin server.
    -   **Weight**: Enter a weight for the endpoint. Valid values: **0 to 255**. GA routes traffic to endpoints based on the predefined weights.

**Note:** If you set the weight of an endpoint to 0, GA stops distributing network traffic to the endpoint. Proceed with caution.

You can click **+ Add Endpoint** to add more endpoints. You can create up to four endpoints in each endpoint group. |

2.  Click **Next**.


## Step 4: Verify the settings

To verify the settings, perform the following steps:

1.  On the **Confirm** wizard page, verify the basic settings, protocol, SSL certificate, and endpoint group of the listener.

    To modify the configurations, click **Modify** in the **Configure Listener & Protocol**, **SSL Certificate**, or **Endpoint Group** section.

2.  After you confirm the configurations, click **Next**. The listener is created for the GA instance.


**Related topics**  


[CreateListener](/intl.en-US/API reference/Listeners/CreateListener.md)


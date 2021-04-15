---
keyword: [default endpoint groups, virtual endpoint groups]
---

# Create an endpoint group

To associate a listener with an endpoint group, you can specify the region to which you want to distribute network traffic. Then, the system distributes network traffic to the optimal endpoint of the endpoint group.

A Global Accelerator \(GA\) instance is created. For more information, see [Create a GA instance](/intl.en-US/User Guide/Global Accelerator instances/Create a GA instance.md).

Listeners that use different listener protocols support different types of endpoint groups:

-   For a TCP or UDP listener, you can create only one default endpoint group.
-   For an HTTP or HTTPS listener, you can create one default endpoint group and one virtual endpoint group.

    -   A default endpoint group refers to the endpoint group that you configure when you create an HTTP or HTTPS listener.
    -   A virtual endpoint group refers to the endpoint group that you can manually create on the Endpoint Group page after you create a listener.
    **Note:** By default, you can create only one virtual endpoint group. To create multiple virtual endpoint groups,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

    After you create a virtual endpoint group for an HTTP or HTTPS listener, you can create a forwarding rule and associate the forwarding rule with the virtual endpoint group. Then, the HTTP or HTTPS listener can use the forwarding rule to forward requests with different destination domain names or paths to the default or virtual endpoint group. This way, you can use one Global Accelerator \(GA\) instance to accelerate access to multiple domain names or paths. For more information about how to create a forwarding rule, see [Manage forwarding rules](/intl.en-US/User Guide/Endpoint groups and endpoints/Manage forwarding rules.md).


## Create a default endpoint group

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the GA instance that you want to manage, and click **Configure Listeners** in the **Actions** column for the instance.

3.  On the **Listeners** tab, click **Add Listener**.

    **Note:** If this is your first time creating an endpoint group, skip the step.

4.  On the **Configure Listener & Protocol** wizard page, set the required parameters and click **Next**.

    If you create an endpoint group for an HTTPS listener, you must also configure SSL certificates. For more information, see [Create a listener](/intl.en-US/User Guide/Listeners/Add listeners.md).

5.  On the **Configure Endpoint Group** wizard page, set the following parameters and click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Endpoint Group Name**|Enter a name for the endpoint group. The name must be 2 to 128 characters in length, and can contain letters, digits, underscores \(\_\), and hyphens \(-\). The name must start with a letter. |
    |**Region**|Select the region where you want to deploy the endpoint group.|
    |**Backend Service**|Select whether backend services are deployed on Alibaba Cloud.     -   **Alibaba Cloud**: specifies that backend services are deployed on Alibaba Cloud.
    -   **Off Alibaba Cloud**: specifies that backend services are not deployed on Alibaba Cloud. |
    |**Reserve Client IP**|Specify whether to reserve client IP addresses. After this feature is enabled, backend servers can obtain client IP addresses. For more information, see [Preserve client IP addresses](/intl.en-US/Deployment & Maintenance/Preserve client IP addresses.md).

**Note:** This feature is available to only Alibaba Cloud accounts that are included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex). |
    |**Endpoint**|An endpoint serves as the destination that a client requests to access. Set the following parameters to configure an endpoint:     -   **Backend Service Type**: If you set Backend Service to Alibaba Cloud, you can select **Alibaba Cloud Public IP Address**, **ECS**, or **SLB**. If you set Backend Service to Off Alibaba Cloud, you can select **Custom IP Address** or **Custom Domain Name**.

**Note:**

        -   You can specify an Elastic Compute Service \(ECS\) or Server Load Balancer \(SLB\) instance as an endpoint only if your Alibaba Cloud account is included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).
        -   If no service-linked role exists when you specify an ECS or SLB instance as an endpoint, the system automatically creates the service-linked role AliyunServiceRoleForGaVpcEndpoint. For more information, see [AliyunServiceRoleForGaVpcEndpoint](/intl.en-US/User Guide/Service-linked role/AliyunServiceRoleForGaVpcEndpoint.md).
    -   **Backend Service**: Enter the IP address or domain name of the origin server.
    -   **Weight**: Enter a weight for the endpoint. Valid values: **0 to 255**. GA routes network traffic to each endpoint based on the proportion of each endpoint.

**Note:** If you set the weight of an endpoint to 0, GA stops routing network traffic to the endpoint. Proceed with caution.

You can click **+ Add Endpoint** to add more endpoints. You can create at most four endpoints for each endpoint group. |
    |**Backend Service Protocol**|Select the protocol that the backend server uses. Valid values:    -   **HTTP**
    -   **HTTPS**
**Note:**

    -   This is the default value. If the listener protocol is HTTP, this parameter is set to HTTP and cannot be modified.
    -   You can set **Backend Service Protocol** and **Port Mapping** only when you configure an endpoint group for an HTTP or HTTPS listener. |
    |**Port Mapping**|If the listener port is not the same port over which the endpoint provides services, you must set this parameter.     -   **Listener Port**: Enter the listener port.
    -   **Endpoint Port**: Enter the port over which the endpoint provides services.
If the listener port is the same port over which the endpoint provides services, ignore this parameter. GA automatically forwards requests to the listener port of the endpoint. |

6.  On the **Confirm** wizard page, review the configurations.

    To modify a specific setting, click **Modify** in the corresponding section.

7.  After you confirm the configurations, click **Submit**.


## Create a virtual endpoint group

Before you create a virtual endpoint group, take note of the following limits:

-   You can create a virtual endpoint group for only an HTTP or HTTPS listener.
-   Before you can create a virtual endpoint group, you must create a default endpoint group.

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the GA instance that you want to manage and click **Configure Listeners** in the **Actions** column.

3.  On the **Listeners** tab, find the listener that you want to manage and click the endpoint group ID in the **Default Endpoint Group ID/Name** column.

4.  On the **Endpoint Group** tab, click **Add Virtual Endpoint Group**.

5.  In the **Add Virtual Endpoint Group** dialog box, set the parameters and click **Create**.

    For more information, see [Create a default endpoint group](#section_3fg_g29_1xd).



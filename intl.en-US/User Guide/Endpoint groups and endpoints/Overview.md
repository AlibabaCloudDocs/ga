---
keyword: [endpoint groups, endpoints, weights, backend service types]
---

# Overview

Each listener is associated with one endpoint group, and each endpoint group contains one or more endpoints.

## Endpoint groups

Each endpoint group is associated with a region. You can specify the region to which you want to distribute network traffic and associate an endpoint group with a listener. Then, the system distributes network traffic to the optimal endpoint of the endpoint group.

Listeners that use different listener protocols support different types of endpoint groups:

-   For a TCP or UDP listener, you can create only one default endpoint group.
-   For an HTTP or HTTPS listener, you can create one default endpoint group and one virtual endpoint group.

    -   A default endpoint group refers to the endpoint group that you configure when you create an HTTP or HTTPS listener.
    -   A virtual endpoint group refers to the endpoint group that you can manually create on the Endpoint Group page after you create a listener.
    **Note:** By default, you can create only one virtual endpoint group. To create multiple virtual endpoint groups,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

    After you create a virtual endpoint group for an HTTP or HTTPS listener, you can create a forwarding rule and associate the forwarding rule with the virtual endpoint group. Then, the HTTP or HTTPS listener can use the forwarding rule to forward requests with different destination domain names or paths to the default or virtual endpoint group. This way, you can use one Global Accelerator \(GA\) instance to accelerate access to multiple domain names or paths. For more information about how to create a forwarding rule, see [Manage forwarding rules](/intl.en-US/User Guide/Endpoint groups and endpoints/Manage forwarding rules.md).


## Endpoints

An endpoint serves as the destination that a client requests to access. You can add one to four endpoints to an endpoint group. An endpoint can be an Elastic Compute Service \(ECS\) instance, a Server Load Balancer \(SLB\) instance, an Alibaba Cloud public IP address, a custom origin IP address, or a custom origin domain name.

**Note:** You can specify an ECS or SLB instance as an endpoint only if your Alibaba Cloud account is included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

You can set a weight for an endpoint. The weight specifies the proportion of network traffic that is forwarded to the endpoint. GA calculates the sum of all endpoint weights in an endpoint group. Then, traffic is forwarded to each endpoint based on the proportion of each endpoint.

## References

[Create an endpoint group](/intl.en-US/User Guide/Endpoint groups and endpoints/Configure an endpoint group.md)


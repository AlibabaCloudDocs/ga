# What is Global Accelerator?

Global Accelerator \(GA\) provides access points worldwide. It is designed to accelerate transmission of network traffic. The GA service ensures high-quality Border Gateway Protocol \(BGP\) bandwidth and high service reliability. This allows businesses to accelerate global connections to Internet-facing services. Backed by the reliable and congestion-free global network of Alibaba Cloud, GA provides a high-speed network experience and ultra-low transmission latency for users across different regions.

![GA overview–the Alibaba Cloud International site](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5323839951/p84077.png)

GA assigns an accelerated IP address to each acceleration region in an acceleration area. Clients from an acceleration region can connect to the access point that is closest to the clients through the accelerated IP address. The access point receives client requests and forwards the requests over the Alibaba Cloud global network. GA then automatically selects routes to distribute client requests to the optimal endpoints. This allows you to avoid network congestion and reduce network latency. Endpoints can be IP addresses or domain names of origin servers. These origin servers include Server Load Balancer \(SLB\) instances, Elastic Compute Service \(ECS\) instances, and custom origin servers. Alibaba Cloud public IP addresses are supported.

**Note:** You can specify an ECS or SLB instance as an endpoint only if your Alibaba Cloud account is included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

You can also purchase cross-border bandwidth plans. This allows you to implement cross-border network acceleration between mainland China and other areas.

## Components

GA consists of the following components:

|Component|Description|
|---------|-----------|
|**Acceleration area**|The area from which network traffic requires acceleration. Supported areas include mainland China, Asia Pacific, Europe, North America, and Australia. To accelerate transmission of network traffic for users in a specific area, specify the area as an acceleration area. You can also specify regions in an acceleration area as acceleration regions. For more information about areas and regions, see [Overview](/intl.en-US/User Guide/Acceleration areas/Overview.md). |
|**Accelerated IP address**|An accelerated IP address is a Global Accelerator IP address that is assigned to each acceleration region in an acceleration area. Clients in an acceleration region can connect to the access point that is closest to the clients through the accelerated IP address. The access point receives client requests and forwards the requests over the Alibaba Cloud global network.|
|**Access point**|An access point is a portal through which network traffic is routed to the Alibaba Cloud global network with the shortest transmission path. Access points are the points of presence \(PoPs\) of the Alibaba Cloud global network and these access points are deployed in acceleration regions.|
|**Listener**|A listener monitors connection requests from clients. It then redirects requests to Global Accelerator, based on the specified protocol and port. Each listener is associated with an endpoint group. You can associate an endpoint group with a listener by specifying the regions to which you want to distribute network traffic. After the association, network traffic is distributed to optimal endpoints within the endpoint group that is associated with a listener.|
|**Endpoint group**|An endpoint group must be associated with a listener. This way, network traffic can be redirected to the endpoint group. Each endpoint group is associated with a specific region. An endpoint group contains one or more endpoints in the associated region.|
|**Endpoint**|An endpoint is an origin server to which client requests are forwarded. Endpoints can be IP addresses or domain names of origin servers. These origin servers include SLB instances, ECS instances, and custom origin servers. Alibaba Cloud public IP addresses are supported.**Note:** You can specify an ECS or SLB instance as an endpoint only if your Alibaba Cloud account is included in the whitelist. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

You can set a weight for each endpoint. GA forwards network traffic to the endpoint based on the specified weight. |
|**Basic bandwidth plan**|A basic bandwidth plan provides bandwidth resources for data transmission worldwide over the Internet and the internal network of Alibaba Cloud. However, a basic bandwidth plan based on leased lines cannot be used for content delivery acceleration between mainland China and other areas. The basic bandwidth plans support the following types of bandwidth: basic, enhanced, and premium. The resources, acceleration type, and acceleration scope vary based on the bandwidth type. For more information, see [Overview](/intl.en-US/User Guide/Basic bandwidth plans/Overview.md). |
|**Cross-border acceleration bandwidth plans**|If your require traffic acceleration between mainland China and other areas, purchase a cross-border bandwidth plan.|

## Apply for a free trial

During the period from April 15, 2020 to April 1, 2021, if a first-time enterprise uses an Alibaba Cloud account \(that has passed real-name verification\) to purchase the GA service, a one-month free trial is provided. Click [here](https://page-intl.aliyun.com/form/act857014000/index.htm) to apply for the free trial.

For more information about the free trial and the supported instance types, see [GA free trials](/intl.en-US/Announcement/GA free trials.md).


# Overview

After you create a Global Accelerator \(GA\) instance, you must add an acceleration area. An acceleration area is the area where you want to accelerate your applications.

## Acceleration areas and regions

To accelerate transmission of network traffic for users in a specific area, you must specify the area as an acceleration area. You can select specific regions in the acceleration area.

An acceleration area is a collection of Alibaba Cloud regions. Each acceleration area contains one or more Alibaba Cloud regions. The following table shows the acceleration areas and regions that GA supports.

**Note:** If you want to specify the China \(Taiwan\) region as an acceleration region,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

|Area|Region|
|:---|:-----|
|China North|China \(Qingdao\) and China \(Beijing\)|
|China South|China \(Shenzhen\)|
|China East|China \(Hangzhou\) and China \(Shanghai\)|
|China Southwest|China \(Chengdu\)|
|North America|US \(Silicon Valley\) and US \(Virginia\)|
|Asia Pacific|China \(Hong Kong\), China \(Taiwan\), South Korea \(Seoul\), Singapore \(Singapore\), Malaysia \(Kuala Lumpur\), Japan \(Tokyo\), Indonesia \(Jakarta\), India \(Mumbai\), and Australia \(Sydney\)|
|Europe|Germany \(Frankfurt\) and UK \(London\)|

## Accelerated IP addresses

An accelerated IP address is a GA IP address that is assigned to each acceleration region in an acceleration area. Clients in an acceleration region can connect to the access point that is nearest to the clients through the accelerated IP address. The access point receives client requests and forwards the requests over the Alibaba Cloud global network.

When you add an acceleration area, you can select IPv4 addresses or IPv6 addresses.

**Note:** IPv6 clients can connect to GA instances that are deployed in only the China \(Beijing\), China \(Hangzhou\), China \(Shanghai\), China \(Shenzhen\), and China \(Hong Kong\) regions. If you want to connect IPv6 clients to GA instances in the listed regions,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

-   IPv4: After you add an acceleration area, GA assigns an accelerated IPv4 address to each acceleration region in the acceleration area. The IP address is used to accelerate the delivery of IPv4 services to IPv4 clients.
-   IPv6: After you add an acceleration area, GA assigns an accelerated IPv6 address to each acceleration region in the acceleration area. The IP address is used to accelerate the delivery of IPv4 services to IPv6 clients.

    **Note:** In the same acceleration region of a GA instance, you can select only one IP address type: IPv4 or IPv6.



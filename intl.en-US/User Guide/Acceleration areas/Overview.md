# Overview

After you create a Global Accelerator \(GA\) instance, you must add an acceleration area. An acceleration area is the area where you want to accelerate your applications.

## Acceleration areas and regions

To accelerate transmission of network traffic for users in a specific area, you must specify the area as an acceleration area. You can select regions in the acceleration area.

An acceleration area is a collection of Alibaba Cloud regions. Each acceleration area contains one or more Alibaba Cloud regions. The following table shows the acceleration areas and regions that GA supports.

**Note:** If you need to select Australia \(Sydney\), China \(Taiwan\), and South Korea \(Seoul\) as the acceleration areas,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

|Acceleration area|Region|
|:----------------|:-----|
|China North|China \(Qingdao\) and China \(Beijing\)|
|China South|China \(Shenzhen\)|
|China East|China \(Hangzhou\) and China \(Shanghai\)|
|China Southwest|China \(Chengdu\)|
|North America|US \(Silicon Valley\) and US \(Virginia\)|
|Asia Pacific|China \(Hong Kong\), China \(Taiwan\), South Korea \(Seoul\), Singapore, Malaysia \(Kuala Lumpur\), Japan \(Tokyo\), Indonesia \(Jakarta\), and India \(Mumbai\)|
|Europe|Germany \(Frankfurt\) and UK \(London\)|
|Australia|Australia \(Sydney\)|

## Accelerated IP address

An accelerated IP address is a GA IP address that is assigned to each acceleration region in an acceleration area. Clients in an acceleration region can connect to the access point that is the closest to the clients over the accelerated IP address. The access point receives client requests and forwards the requests over the Alibaba Cloud global network.

When you add an acceleration area, you can select an IPv4 address or an IPv6 address.

**Note:** IPv6 clients can connect to GA instances that are deployed in only the China \(Beijing\), China \(Hangzhou\), China \(Shanghai\), China \(Shenzhen\), and China \(Hong Kong\) regions. If you need to purchase GA instances of the listed types and you are not in the whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

-   IPv4 address: After you add an acceleration area, GA assigns a GA IPv4 address to each acceleration region in an acceleration area. This allows IPv4 clients to have fast access to IPv4 services.
-   IPv6 address: After you add an acceleration area, GA assigns a GA IPv6 address to each acceleration region in an acceleration area. This allows IPv6 clients to have fast access to IPv4 services.

    **Note:** In the same acceleration region for a GA instance, you can select only one IP address type: an IPv4 address or an IPv6 address.



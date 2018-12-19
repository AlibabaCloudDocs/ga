# What is Global Acceleration? {#concept_cq5_wmw_5db .concept}

Global Acceleration is a network acceleration product. Based on the Alibaba Cloud network, Global Acceleration uses access points worldwide to speed up Internet access to services hosted in one region for users located in other regions. It reduces the impact of network issues like latency, jitters, and packet loss on service, and provides a superior experience for global service users.

Before using Global Acceleration, you must buy and create a Global Acceleration instance. A Global Acceleration instance can accelerate the Internet access of your services for users worldwide. As shown in the following figure, you can create a Global Acceleration instance to accelerate the Internet access for applications deployed on an ECS instance or an SLB instance located in one region for users located in other regions. In this case, the services of applications deployed on instances in the China \(Beijing\) region are accelerated for users in the Western United States regions.

Currently, Global Acceleration only supports accelerating the access to applications deployed in ECS instances and SLB instances of the VPC network.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12626/15452160861354_en-US.png)

## Accelerated Area {#section_aw5_pnw_5db .section}

An accelerated area is an area that requires faster access over the Internet to your service. It consists of one or more Alibaba Cloud regions. Select an accelerated area to optimize service access for your customers there. After selecting an accelerated area, you must select the specific region within the acceleration area where the Global Acceleration instance is created. Users in the instance region will experience the greatest improvement to their service, and so we recommend selecting the region that has the greatest number of users.

Each accelerated area contains one or more Alibaba Cloud regions, as shown in the following table.

**Note:** If you want to select Asia and Europe as the accelerated area, contact your customer manager.

For example, if you want to accelerate the Internet access to your service for users in North America, then select North America as the accelerated area when you create a Global Acceleration instance. A public IP is allocated to the Global Acceleration instance in the selected region for users in North America to access your service.

|Accelerated area|Included regions|
|:---------------|:---------------|
|Mainland China| China \(Qingdao\) 

 China \(Beijing\)  

 China \(Zhangjiakou\)

 China \(Hangzhou\)

 China \(Hohhot\)

 China East 2 \(Shanghai\)

 China \(Shenzhen\)

 |
|Asia Pacific| China \(Hong Kong\)

 Singapore

 Japan \(Tokyo\)

 |
|North America| US \(Silicon Valley\)

 US \(Virginia\)

 |
|Europe| Germany \(Frankfurt\)

 UK \(London\)

 |
|Australia|Australia \(Sydney\)|
|Middle East|UAE \(Dubai\)|

## Service Area {#section_upj_d4w_5db .section}

A service area is an area where the ECS instance or the SLB instance that hosts the backend service to be accelerated, is located. You must specify a service area when creating a Global Acceleration instance, and you cannot change it after the instance is created.

A service area is a collection of Alibaba Cloud regions. Each service area contains one or more regions as shown in the following table.

For example, if the website to have accelerated access is deployed in an ECS instance in China \(Beijing\), then select China Mainland as the service area when you create a Global Acceleration instance.

|Accelerated area|Included regions|
|:---------------|:---------------|
|Mainland China| China \(Qingdao\) 

 China \(Beijing\)  

 China \(Zhangjiakou\)

 China \(Hangzhou\)

 China \(Hohhot\)

 China East 2 \(Shanghai\)

 China \(Shenzhen\)

 |
|Asia Pacific| China \(Hong Kong\)

 Singapore

 Japan \(Tokyo\)

 |
|North America| US \(Silicon Valley\)

 US \(Virginia\)

 |
|Europe| Germany \(Frankfurt\)

 UK \(London\)

 |
|Australia|Australia \(Sydney\)|
|Middle East|UAE \(Dubai\)|

## Backend service {#section_z33_d4w_5db .section}

A backend service is the service that you want to accelerate. You can bind an ECS instance or an SLB instance to a Global Acceleration instance. 

**Note:** The backend service must be located in the region of the selected service area.


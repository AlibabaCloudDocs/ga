# Limits

This topic describes the limits of Global Accelerator \(GA\). We recommend that you learn more about these limits before you use this service.

## Instance limits

|Item|Default limit|Quota increase supported|
|----|-------------|------------------------|
|The maximum number of GA instances that can be created for each account|5|[Submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).|
|The types of backend server that can be associated with a GA instance|Endpoints can be IP addresses or domain names of origin servers. These origin servers include Server Load Balancer \(SLB\) instances, Elastic Compute Service \(ECS\) instances, and custom origin servers. Alibaba Cloud public IP addresses are supported.**Note:** You can specify ECS or SLB as the backend service type only when your account is included in the whitelist of GA. If you want to specify ECS or SLB as the backend service type, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

|None.|
|Support for Transmission Control Protocol \(TCP\) and User Datagram Protocol \(UDP\) segmentation|Not supported|None.|

## Acceleration area limits

|Item|Default limit|Quota increase supported|
|----|-------------|------------------------|
|The minimum bandwidth that can be allocated to each region in an acceleration area|2 Mbit/s|None.|

## Listener limits

|Item|Default limit|Quota increase supported|
|----|-------------|------------------------|
|The maximum number of listeners that can be created for each GA instance|10|[Submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).|
|The maximum number of listening ports that can be specified for each listener|30|[Submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).|
|The range of ports that can be specified for TCP and UDP listeners|1 to 65499|None.|

## Endpoint group limits

|Item|Default limit|Quota increase supported|
|----|-------------|------------------------|
|The maximum number of endpoint groups that can be associated with each listener|1|None.|
|The maximum number of endpoints that can be added to each endpoint group|4|None.|


---
keyword: [listener protocols, listener ports]
---

# Overview

After you create a Global Accelerator \(GA\) instance, you must configure listeners for the GA instance. A listener checks connection requests and distributes the requests to endpoints based on forwarding rules that are defined by the scheduling algorithm.

## Listener protocol

You can create one or more listeners for each GA instance. Supported listener protocols include TCP, UDP, HTTP, and HTTPS. You can select a protocol based on the scenario.

|Protocol|Description|Scenario|
|--------|-----------|--------|
|TCP|-   TCP is a connection-oriented protocol that provides high reliability. Before you start to transmit data, you must establish a stable connection with the peer.
-   Session persistence is based on source IP addresses.
-   Source IP addresses are visible at the network layer.
-   Data is transmitted at a slow rate.

|-   Applicable to scenarios that require high reliability and high data accuracy but can withstand a low transmission speed. These scenarios include file transmission, email submission and reception, and remote logons.
-   Web applications that do not have custom requirements. |
|UDP|-   UDP is connectionless and unreliable. Three-way handshakes are not required before UDP packets are transmitted. UDP does not support fault tolerance and retransmission.
-   Data is transmitted at a fast rate.

|Applicable to scenarios where real-time transmission is more important than reliability. These scenarios include video chat and real-time pushes of financial news.|
|HTTP|-   HTTP is a connection-oriented protocol that provides high reliability. Before you start to transmit data, you must establish a stable connection with the peer.
-   Data is transmitted at a fast rate.
-   Data transmission is not encrypted.

|-   Applicable to scenarios where clients are required to accelerate access to HTTP websites.
-   Applicable to scenarios where clients are required to accelerate access to HTTP websites that contain specified domain names or paths. |
|HTTPS|-   HTTPS is a connection-oriented protocol that provides high reliability. Before you start to transmit data, you must establish a stable connection with the peer.
-   You can bind SSL certificates to servers. This ensures high reliability of data.

**Note:** For more information about SSL certificates, see [What is SSL Certificates Service?](/intl.en-US/Product Introduction/What is SSL Certificates Service?.md).

-   Data transmission is encrypted.

|-   Applicable to scenarios where clients are required to accelerate access to HTTP or HTTPS websites. This also ensures the network security when clients access HTTP or HTTPS websites.
-   Applicable to scenarios where clients are required to accelerate access to HTTP or HTTPS websites that contain specified domain names or paths. |

**Note:** HTTP and HTTPS listeners are available for Alibaba Cloud accounts that are included in the whitelist. To create HTTP or HTTPS listeners,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

## Listener ports

Listener ports are used to receive requests and forward the requests to endpoints. The following limits are imposed on listener ports based on different listener protocols.

|Listener protocol|Listener port range|Listener port quota|
|-----------------|-------------------|-------------------|
|TCP|1~65499|30. -   Separate multiple listener ports with commas \(,\). For example, you can enter 80,90,8080.
-   If you want to specify consecutive ports, you can use a tilde \(~\). For example, you can enter 80~83 to specify the ports 80, 81, 82, and 83. |
|UDP|1~65499|30. -   Separate multiple listener ports with commas \(,\). For example, you can enter 80,90,8080.
-   If you want to specify consecutive ports, you can use a tilde \(~\). For example, you can enter 80~83 to specify the ports 80, 81, 82, and 83. |
|HTTP|1~65499|1.|
|HTTPS|1~65499|1.|

**Note:** If listeners that are added to the same GA instance use the same protocol, the listeners must be configured with different listening ports.

You can specify more than 300 listener ports for a UDP or TCP listener in specific regions. If you specify more than 300 listener ports for a listener, take note of the following limits:

-   Only Alibaba Cloud accounts that are included in the whitelist can specify more than 300 listener ports for a listener. To use this feature,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).
-   You can specify more than 300 listener ports for only one listener per GA instance. If a listener has more than 300 listener ports specified, the total number of TCP, UDP, HTTP, and HTTPS ports that are specified for other listeners must not exceed 300.
-   The maximum number of listener ports that can be specified for a listener is determined by the listener protocol:
    -   You can specify at most 2,000 listener ports for a TCP listener.
    -   You can specify at most 200 listener ports for a UDP listener.
-   For more information about regions in which you can specify more than 300 listener ports for a listener, see the following table.

    |Area|Region|
    |:---|:-----|
    |China Southwest|China \(Chengdu\)|
    |North America|US \(Silicon Valley\) and US \(Virginia\)|
    |Asia Pacific|China \(Hong Kong\), China \(Taiwan\), South Korea \(Seoul\), Singapore \(Singapore\), Malaysia \(Kuala Lumpur\), Japan \(Tokyo\), Indonesia \(Jakarta\), India \(Mumbai\), and Australia \(Sydney\)|
    |Europe|Germany \(Frankfurt\) and UK \(London\)|



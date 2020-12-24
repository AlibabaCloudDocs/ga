---
keyword: [listener protocols, listening ports]
---

# Overview

After you create a Global Accelerator \(GA\) instance, you must configure listeners for the instance. A listener checks connection requests and distributes the requests to endpoints. These requests are distributed based on the forwarding rules that are defined by the scheduling algorithm.

## Listener protocols

You can create one or more listeners for each GA instance. Supported listener protocols include TCP, UDP, and HTTPS. You can select a protocol based on the scenario.

|Protocol|Description|Scenario|
|--------|-----------|--------|
|TCP|-   TCP is a connection-oriented protocol that provides high reliability. Before you start to transmit data, you must establish a stable connection with the peer.
-   Session persistence is based on source IP addresses.
-   Source IP addresses are visible at the network layer.
-   Data transmission over TCP is slow.

|-   Applicable to scenarios that require high reliability and high data accuracy but can withstand a low transmission speed. These scenarios include file transmission, email submission and reception, and remote logons.
-   Web applications that do not have custom requirements. |
|UDP|-   UDP is connectionless and unreliable. Three-way handshake is not required before UDP packets are transmitted. UDP does not support fault tolerance and retransmission.
-   Data transmission over UDP is fast.

|Applicable to scenarios where real-time transmission is more important than reliability. These scenarios include video chat and real-time pushes of finance news.|
|HTTPS|-   HTTPS is a connection-oriented protocol that provides high reliability. Before you start to transmit data, you must establish a stable connection with the peer.
-   You can bind SSL certificates to servers. This ensures the high reliability of data.

**Note:** For more information about SSL certificates, see [What is SSL Certificates Service?](/intl.en-US/Product Introduction/What is SSL Certificates Service?.md).

-   Data transmission is encrypted.

|Applicable to scenarios when acceleration of HTTP website access is required for clients. This improves the speed and security.|

**Note:** Acceleration of HTTPS traffic is available to only accounts that are included in the whitelist. If you want to use the feature but you are not included in the whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

## Listening ports

Listening ports are used to receive requests and forward the requests to endpoints. Listening ports have the following limits:

-   You can create a maximum of 30 listening ports for a listener. Use a tilde \(~\) to specify a range of port numbers. Valid values: **1 to 65499**.
-   If listeners that are added to the same GA instance use the same protocol, the listeners must be configured with different listening ports.
-   Some acceleration regions allow you to configure more than 300 listening ports for a listener. For more information about the regions, see the following table.

    **Note:** The feature to configure more than 300 listening ports for a listener is available to only accounts that are included in the whitelist. If you want to use the feature but you are not included in the whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

    When you specify more than 300 listening ports for a listener, take note of the following limits:

    -   Each GA instance supports only one listener with more than 300 listening ports. If a listener of a GA instance has more than 300 listening ports, the total number of TCP, UDP, and HTTPS ports for the remaining listeners must not exceed 300.
    -   The maximum number of listening ports that can be specified for a listener is determined by the listener protocol.
        -   For TCP listeners, you can specify up to 2,000 listening ports.
        -   For UDP listeners, you can specify up to 200 listening ports.
        -   For HTTPS listeners, you can set the listening port to only port 443.
    |Area|Region|
    |:---|:-----|
    |China Southwest|China \(Chengdu\)|
    |North America|US \(Silicon Valley\) and US \(Virginia\)|
    |Asia Pacific|China \(Hong Kong\), China \(Taiwan\), South Korea \(Seoul\), Singapore \(Singapore\), Malaysia \(Kuala Lumpur\), Japan \(Tokyo\), Indonesia \(Jakarta\), India \(Mumbai\), and Australia \(Sydney\)|
    |Europe|Germany \(Frankfurt\) and UK \(London\)|



# ListListeners

Queries the listeners that are configured for a Global Accelerator \(GA\) instance.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=ListListeners&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListListeners|The operation that you want to perform. Set the value to **ListListeners**. |
|AcceleratorId|String|Yes|ga-bp1odcab8tmno0hdq\*\*\*\*|The ID of the GA instance to which the listener will be added. |
|PageNumber|Integer|Yes|1|The number of the page to return. Default value: **1**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the GA instance belongs. Set the value to **cn-hangzhou**. |
|PageSize|Integer|No|10|The number of entries to return on each page. Valid values: 1 to **50**. Default value: **10**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Listeners|Array of Listeners| |The information about the listeners. |
|BackendPorts|Array of BackendPort| |The information of the origin server. |
|FromPort|String|80|The first listening port of the port range that is specified for receiving and forwarding requests to endpoints. |
|ToPort|String|80|The last listening port of the port range that is specified for receiving and forwarding requests to endpoints. |
|Certificates|Array of Certificate| |The information about the SSL certificate. |
|Id|String|44983xxxx-cn-hangzhou|The ID of the SSL certificate. |
|Type|String|Server|The type of certificate.

 Only a value of **Server** is returned to indicate a server certificate. |
|ClientAffinity|String|SOURCE\_IP|Indicates whether client affinity is enabled for the listener. Valid values:

 -   Null: disables client affinity. When client affinity is disabled, the connections from the specific source IP address of a client are not routed to the same endpoint. This is the default value.
-   **SOURCE\_IP**: enables client affinity. When client affinity is enabled, the connections from the specific source IP address of a client are routed to the same endpoint. |
|CreateTime|Long|1577786252000|The time when the listener was created. |
|Description|String|Listener|The description of the listener. |
|ListenerId|String|lsr-bp1bpn0kn908w4nbw\*\*\*\*|The ID of the listener. |
|Name|String|Listener|The name of the listener. |
|PortRanges|Array of PortRanges| |The information about the listener ports. |
|FromPort|Integer|20|The first listening port of the port range that is specified for receiving and forwarding requests to endpoints. |
|ToPort|Integer|20|The last listening port of the port range that is specified for receiving and forwarding requests to endpoints. |
|Protocol|String|TCP|The network transmission protocol of the listener.

 -   **TCP**: TCP protocol
-   **UDP**: UDP protocol |
|ProxyProtocol|Boolean|true|Indicates whether client IP addresses are preserved. A client IP address is regarded as a source IP address. Valid values:

 -   **true**: Client IP addresses are preserved. In this case, you can view the client IP addresses that are preserved by the backend service.
-   **false**: Client IP addresses are not preserved. |
|State|String|active|The status of the listener.

 -   **active**: The listener is working as expected.
-   **creating**: The listener is being created.
-   **configuring**: The listener is being configured. |
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|10|The number of entries returned per page. |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|The ID of the request. |
|TotalCount|Integer|1|The total number of entries returned. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=ListListeners
&AcceleratorId=ga-bp1odcab8tmno0hdq****
&PageNumber=1
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListListenersResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <Listeners>
        <ClientAffinity></ClientAffinity>
        <Name>dede</Name>
        <PortRanges>
              <ToPort>80</ToPort>
              <FromPort>80</FromPort>
        </PortRanges>
        <State>active</State>
        <CreateTime>1581669998000</CreateTime>
        <Protocol>TCP</Protocol>
        <ListenerId>lsr-bp12tl35dpsilnsb1****</ListenerId>
  </Listeners>
  <RequestId>4150E70A-E6FB-4707-BF71-39483DF85C74</RequestId>
</ListListenersResponse>
```

`JSON` format

```
{
  "PageNumber": 1,
  "TotalCount": 1,
  "PageSize": 10,
  "Listeners": [
    {
      "ClientAffinity": "",
      "Name": "dede",
      "PortRanges": [
        {
          "ToPort": 80,
          "FromPort": 80
        }
      ],
      "State": "active",
      "CreateTime": 1581669998000,
      "Protocol": "TCP",
      "ListenerId": "lsr-bp12tl35dpsilnsb1****"
    }
  ],
  "RequestId": "4150E70A-E6FB-4707-BF71-39483DF85C74"
}
```

## Error codes

For a list of error codes, visit the API Error Center[https://error-center.alibabacloud.com/status/product/Ga](https://error-center.alibabacloud.com/status/product/Ga).


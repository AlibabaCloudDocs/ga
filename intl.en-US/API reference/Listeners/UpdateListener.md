# UpdateListener

Modifies a listener.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ga&api=UpdateListener&type=RPC&version=2019-11-20)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|UpdateListener|The operation that you want to perform. Set the value to **UpdateListener**. |
|ListenerId|String|Yes|lsr-bp1bpn0kn908w4nbw\*\*\*\*|The ID of the listener associated with the endpoint groups that you want to query. |
|PortRanges.N.FromPort|Integer|Yes|20|The initial listener port used to receive and forward requests to endpoints.

 **Note:** You can configure only one listener port for an HTTP or HTTPS listener. In this case, the initial port also serves as the ending port. |
|PortRanges.N.ToPort|Integer|Yes|21|The ending listener port used to receive and forward requests to endpoints. |
|RegionId|String|No|cn-hangzhou|The ID of the region where the GA instance is deployed. Set the value to **cn-hangzhou**. |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000|The client token that is used to ensure the idempotency of the request.

 You can use the client to generate the value, but you must ensure that it is unique among different requests. The token can contain only ASCII characters and cannot exceed 64 characters in length. |
|Name|String|No|Listener|The name of the listener.

 The name must be 2 to 128 characters in length, and can contain letters, digits, underscores \(\_\), and hyphens \(-\). The name must start with a letter. |
|Description|String|No|Listener|The description of the listener. |
|ClientAffinity|String|No|SOURCE\_IP|Specifies whether to enable client affinity for the listener.

 -   If this parameter is left empty, client affinity is disabled, In this case, requests from the same client are not always forwarded to the same endpoint.
-   If you set the value to **SOURCE\_IP**, client affinity is enabled. In this case, when a client accesses stateful applications, requests from the same client are always forwarded to the same endpoint regardless of the source port or protocol. |
|Protocol|String|No|tcp|The network transmission protocol of the listener. Valid values:

 -   **tcp**: TCP
-   **udp**: UDP protocol
-   **HTTP**: HTTP
-   **HTTPS**: HTTPS

 **Note:** You can create HTTP and HTTPS listeners only if your Alibaba Cloud account is included in the whitelist. To use this feature, submit a ticket. |
|ProxyProtocol|String|No|false|Specifies whether to reserve client IP addresses. Valid values:

 -   **true**: Client IP addresses are reserved. In this case, you can view the source IP addresses of clients over backend services.
-   **false**: Client IP addresses are not reserved. This is the default value. |
|Certificates.N.Id|String|No|449\*\*\*\*-cn-hangzhou|The ID of the SSL certificate.

 **Note:** This parameter is required only when you configure an HTTPS listener. |
|BackendPorts.N.FromPort|Integer|No|80|The initial port used by the backend server to receive requests.

 **Note:** This parameter is required only when you configure an HTTPS listener and the listener port is the same port over which the backend server provide services. In this case, the initial port that is used to receive requests for the backend server must serve as the ending port. |
|BackendPorts.N.ToPort|Integer|No|80|The ending port that is used to receive requests for the backend server. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=UpdateListener
&ListenerId=lsr-bp1bpn0kn908w4nbw****
&PortRanges.1.FromPort=20
&PortRanges.1.ToPort=20
&<Common request parameters>
```

Sample success responses

`XML` format

```
<UpdateListenerResponse>
     <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</UpdateListenerResponse>
```

`JSON` format

```
{
   "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NotExist.Listener|The listener does not exist.|The error message returned because the specified listener does not exist.|
|400|NotActive.Listener|The state of the listener is not active.|The error message returned because the state of the specified listener is unstable.|
|400|PortRangeIllegal.Listener|The specified listener port range is invalid.|The error message returned because the specified port range is invalid.|
|400|PortConflict.Listener|The listener port configuration is in conflict.|The error message returned because the configuration of the specified listener port conflicts with that of another listener port.|
|400|QuotaExceeded.ListenerPort|The maximum number of listener ports is exceeded.|The error message returned because the number of listener ports has reached the upper limit.|
|400|NotExist.Accelerator|The accelerated instance does not exist.|The error message returned because the specified Global Accelerator instance does not exist.|
|400|StateError.Accelerator|The state of the accelerated instance is invalid.|The error message returned because the state of the specified GA instance in invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ga).


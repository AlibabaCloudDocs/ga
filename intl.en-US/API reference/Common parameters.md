# Common parameters

This topic describes the request and response parameters that each API operation uses.

## Common request parameters

|Parameter|Type|Required?|Description|
|:--------|:---|:--------|:----------|
|Format|String|No|The format in which the response is returned. Valid values: JSON and XML. Default value: JSON. |
|Version|String|Yes|The API version in a date format of YYYY-MM-DD. Set this value to 2019-11-20. |
|AccessKeyId|String|Yes|The AccessKey ID provided to you by Alibaba Cloud.|
|Signature|String|Yes|The signature string of the current request.|
|SignatureMethod|String|Yes|The algorithm that is used to calculate the request signature. Set the value to HMAC-SHA1. |
|Timestamp|String|Yes|The time at which the quest is signed. Specify the time in the ISO 8601 standard in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC. For example, the time can be 2013-01-10T12:00:00Z. The time indicates 20:00:00 on January 10, 2013 \(UTC+08:00\). |
|SignatureVersion|String|Yes|The version of the signature algorithm. Set the value to 1.0. |
|SignatureNonce|String|Yes|A unique, random number that is used to prevent replay attacks. You must use different random numbers for different requests. |
|ResourceOwnerAccount|String|No|The account that owns the resource to be accessed by this API request.|

Examples

```
http://ga.aliyuncs.com/?Action=DescribeListener
&TimeStamp=2014-05-19T10%3A33%3A56Z
&Format=xml
&AccessKeyId=testid
&SignatureMethod=Hmac-SHA1
&SignatureNonce=NwDAxvLU6tFE0DVb
&Version=2019-11-20
&SignatureVersion=1.0
&Signature=*Signature*
```

## Common response parameters

Responses can be returned in the JSON or XML format. You can specify the response format in the request. The default response format is XML. Every response returns a unique RequestId regardless of whether the call is successful.

-   A `2xx` HTTP status code indicates a successful call.
-   A `4xx` or `5xx` HTTP status code indicates a failed call.

Sample responses

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? > 
        <!-The root node of the result-->
        <Operation name+Response>
            <!-Return request tag-->
            <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
            <!-Return result data-->
        </Operation name+Response>
                            
    ```

-   JSON f format

    ```
    {
        "RequestId":"4C467B38-3910-447D-87BC-AC049166F216",
        /*Return result data*/
        }
    ```



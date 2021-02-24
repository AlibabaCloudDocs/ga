# Preserve client IP addresses

Global Accelerator \(GA\) supports the client IP address preservation feature. After you enable this feature, you can view preserved client IP addresses on backend servers. This topic describes how to enable client IP address preservation in different scenarios and view preserved client IP addresses on backend servers.

-   A listener is created for your GA instance. For more information, see [Add listeners](/intl.en-US/User Guide/Listeners/Add listeners.md).
-   The client IP address preservation feature is available for users whose accounts are added to the whitelist.
    -   To enable client IP address preservation for an existing GA instance,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex). Make sure that you include the ID of the GA instance in the ticket. After your application is approved, you must create a new listener for the GA instance and then enable client IP address preservation.
    -   To enable client IP address preservation for a new GA instance,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

## Background information

By default, when GA forwards a request to a backend server, the backend server can obtain only the IP address of the endpoint group to which the backend server belongs. The backend server cannot obtain the IP address of the client that sends the request. If you want the backend server to obtain the IP address of the client, you must enable client IP address preservation for the GA instance. Whether a GA instance supports client IP address preservation depends on the protocol that is used by the listener of the GA instance.

-   **HTTP** and **HTTPS**: support client IP address preservation. The IP address of a client is preserved in the X-Forwarded-For HTTP header field. A backend server retrieves the IP address of the client from the X-Forwarded-For HTTP header field.

    **Note:** HTTP and HTTPS listeners are available for accounts that are added to the whitelist. If you want to create HTTP or HTTPS listeners but you are not included in the whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

-   **UDP**: does not support client IP address preservation.
-   **TCP**: supports client IP address preservation. For specific types of backend servers, you may need to modify the configurations of the backend servers. Otherwise, the backend servers cannot obtain client IP addresses. The following table describes the supported types of backend servers and whether you need to modify the configurations of the backend servers.

    |Location where the backend servers are deployed|Type of backend server|Client IP address preservation|Whether you need to modify the configurations of the backend servers|
    |-----------------------------------------------|----------------------|------------------------------|--------------------------------------------------------------------|
    |Alibaba Cloud|Public IP addresses|Supported|No.After you enable client IP address preservation, the backend servers can obtain the IP addresses of clients. You do not need to modify the configurations of the backend servers. |
    |Elastic Compute Service \(ECS\) instances|Supported|
    |Server Load Balancer \(SLB\) instances|SupportedIn the following scenarios, the backend servers cannot obtain the IP addresses of clients:

    -   The backend servers of your SLB instance are ECS instances that are deployed in a classic network.
    -   The listener of the SLB instance uses the HTTP or HTTPS protocol.
    -   The SLB instance is an Application Load Balancer \(ALB\) instance. |
    |Outside Alibaba Cloud|Custom IP addresses|Supported|Yes.After you enable client IP address preservation, GA uses Proxy Protocol to preserve client IP addresses. Therefore, the backend servers must support Proxy Protocol.

**Note:** If the backend servers do not support Proxy Protocol, they cannot parse the Proxy Protocol headers in the requests. |
    |Custom domain names|Supported|


**Note:**

Proxy Protocol is an Internet protocol that allows you to add a Proxy Protocol header to a TCP packet and include the client IP address in the request.

When Proxy Protocol is used, a backend server starts to process data only after it receives a complete and valid Proxy Protocol header. Therefore, a listener cannot forward both requests that contain the Proxy Protocol header and requests that do not contain the Proxy Protocol header to the same backend server port. If the first data packet that arrives at the backend server does not comply with the Proxy Protocol format, the backend server closes the connection to the client.

## Enable client IP address preservation when an HTTP or HTTPS listener is used to distribute requests

After you enable client IP address preservation for an HTTP or HTTPS listener, backend servers can retrieve client IP addresses from the X-Forwarded-For HTTP header field.

1.  Enable client IP address preservation.

    By default, client IP address preservation is enabled for HTTP and HTTPS listeners. GA preserves the IP address of a client in the X-Forwarded-For HTTP header field before GA forwards the request to a backend server. After the backend server receives the request, you can retrieve the client IP address from the X-Forwarded-For HTTP header field.

2.  Obtain the IP address of a client.

    The following example shows the format of the X-Forwarded-For HTTP header field. The first IP address is the IP address of a client.

    ```
    X-Forwarded-For: IP address of the client, IP address of Proxy Server 1, IP address of Proxy Server 2,...
    ```


## Enable client IP address preservation when a TCP listener is used to distribute requests to backend servers on Alibaba Cloud

If your GA instance uses a TCP listener and the backend servers are deployed on Alibaba Cloud, you can enable client IP address preservation without making additional changes.

1.  Enable client IP address preservation.

    1.  Log on to the [GA console](https://ga.console.aliyun.com/list).

    2.  On the **Instances** page, find the GA instance that you want to manage and click **Configure Listeners** in the **Actions** column.

    3.  On the **Listeners** tab, find the listener for which you want to enable client IP address preservation and click **Configure** in the **Actions** column.

    4.  On the **Configure Listener & Protocol** wizard page, click **Next**.

    5.  On the **Configure Endpoint Group** wizard page, turn on **Preserve Client IP** and click **Next**.

        ![Enable client IP address preservation](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7117672161/p127320.png)

    6.  On the **Confirm** wizard page, confirm the information and click **Submit**.

2.  Obtain the IP address of a client.

    This example shows how to view a preserved client IP address on an ECS instance that runs Linux.

    1.  Log on to the ECS instance that runs Linux.

    2.  Run the following command to capture an HTTP request:

        `tcpdump tcp port [Listening port] -n -X -s 0`

    3.  Check the client IP address in the captured request.

        The result shows that the client IP address is preserved and can be viewed on the backend server.

        ![Check whether the backend server has obtained the client IP address after you enable client IP address preservation](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2230274951/p127315.png)

        If client IP address preservation is disabled, you can view only the IP address of the endpoint group to which the backend server belongs.

        ![Client IP address preservation is disabled](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3230274951/p127316.png)


## Enable client IP address preservation when a TCP listener is used to distribute requests to backend servers outside Alibaba Cloud

To enable client IP address preservation for a TCP listener that is associated with backend servers deployed outside Alibaba Cloud, you must ensure that the backend servers support Proxy Protocol. In this section, an NGINX server is used as an example to describe how to parse the Proxy Protocol header and then retrieve a client IP address.

1.  Enable client IP address preservation.

    1.  Log on to the [GA console](https://ga.console.aliyun.com/list).

    2.  On the **Instances** page, find the GA instance that you want to manage and click **Configure Listeners** in the **Actions** column.

    3.  On the **Listeners** tab, find the listener for which you want to enable client IP address preservation and click **Configure** in the **Actions** column.

    4.  On the **Configure Listener & Protocol** wizard page, click **Next**.

    5.  On the **Configure Endpoint Group** wizard page, turn on **Preserve Client IP** and click **Next**.

        ![Enable client IP address preservation](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7117672161/p127320.png)

    6.  On the **Confirm** wizard page, confirm the information and click **Submit**.

2.  Configure the NGINX server to accept the Proxy Protocol header.

    Both the `http{}` and `stream{}` modules of NGINX can accept the Proxy Protocol header. You can specify a port to accept the Proxy Protocol header in the `http{}` or `stream{}` module.

    ```
    http {
        #...
        server {
            listen 8080 proxy_protocol;    # Accept and parse the Proxy Protocol header on port 8080.
            #...
        }
    }
       
    stream {
        #...
        server {
            listen 1235 proxy_protocol;    # Accept and parse the Proxy Protocol header on port 1235.
            #...
        }
    }
    ```

3.  Obtain the IP address of a client.

    After a request is received on the specified port, NGINX parses the Proxy Protocol header in the request and preserves the client IP address in the proxy\_protocol\_addr variable. Therefore, you can use one of the following methods to obtain the IP address of the client:

    -   If an HTTP request is received, you can preserve the client IP address in the following HTTP request header:

        ```
        http {
            proxy_set_header X-Real-IP       $proxy_protocol_addr;
            proxy_set_header X-Forwarded-For $proxy_protocol_addr;
        }
        ```

        The backend server can retrieve the client IP address from the X-Forwarded-For HTTP header field. The first IP address in the HTTP header field is the IP address of the client.

        ```
        X-Forwarded-For: IP address of the client, IP address of Proxy Server 1, IP address of Proxy Server 2,...
        ```

    -   If an HTTP request or a TCP packet is received, you can preserve the client IP address in a flow log. The backend server can retrieve the client IP address from the flow log.
        1.  Modify log\_format in the `http{}` or `stream{}` module to preserve the client IP address in a flow log.

            ```
            
            http {
                #...
                log_format combined '$proxy_protocol_addr - $remote_user [$time_local] ' ## Add the proxy\_protocol\_addr variable to log_format in the `http{}` module. The client IP address is preserved in the proxy_protocol_addr variable.
                                    '"$request" $status $body_bytes_sent '
                                    '"$http_referer" "$http_user_agent"';
            }
            #...
            stream {
                #...
                log_format basic '$proxy_protocol_addr - [$time_local] '                 ## Add the proxy\_protocol\_addr variable to log_format in the `stream{}` module. The client IP address is preserved in the proxy_protocol_addr variable.
                                  '$protocol $status $bytes_sent $bytes_received '
                                  '$session_time';
            }
                            
            ```

        2.  Run the following command to query the flow log and retrieve the client IP address:

            `tail -n -5 <Path of the flow log>`

    The following code block is a complete example on how to use Proxy Protocol to preserve client IP addresses:

    ```
    worker_processes  4;
    events {
        worker_connections  1024;
    }
    
    http {
        include       mime.types;
        default_type  application/octet-stream;
        log_format  main  '$proxy_protocol_addr $remote_addr - $remote_user [$time_local] "$request" '## Add the proxy\_protocol\_addr variable to log_format in the `http{}` module. The client IP address is preserved in the proxy_protocol_addr variable.
                          '$status $body_bytes_sent "$http_referer" '
                          '"$http_user_agent" "$http_x_forwarded_for"';
    
        sendfile        on;
        keepalive_timeout  65;
    
        upstream backend {
            server 192.XX.XX.36:8080;
            server 192.XX.XX.37:8080;
            keepalive 2000;
        }
    
        server {
            listen       80 proxy_protocol;                          ## Accept and parse the Proxy Protocol header on port 80.
            server_name  example.com;
    
            proxy_set_header X-Real-IP       $proxy_protocol_addr;   ## Preserve the client IP address in the HTTP header field before the request is sent to a backend server.
            proxy_set_header X-Forwarded-For $proxy_protocol_addr;   
    
            access_log  /var/log/nginx/access.log  main;
    
            location / {
                proxy_pass http://backend;
                proxy_http_version 1.1;
                proxy_set_header Connection "";
            }
        }
    }
    
    stream {
        log_format tcp_basic '$proxy_protocol_addr - [$time_local] '  ## Add the proxy\_protocol\_addr variable to log_format in the `stream{}` module. The client IP address is preserved in the proxy_protocol_addr variable.
                          '$protocol $status $bytes_sent $bytes_received '
                          '$session_time';
        upstream stream_backend {
            server 192.XX.XX.36:2003;
            server 192.XX.XX.37:2003;
        }
    
        server {
            listen 1234 proxy_protocol;                               ## Accept and parse the Proxy Protocol header on port 1234.
            access_log  /var/log/nginx/access_tcp.log  tcp_basic;   
            proxy_pass stream_backend;
        }
    }
    ```

    Query the flow log. The first IP address in the flow log is the IP address of the client.

    ![Preserve client IP addresses-View the flow log](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7117672161/p188555.png)



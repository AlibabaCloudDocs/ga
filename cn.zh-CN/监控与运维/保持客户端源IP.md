# 保持客户端源IP

全球加速GA（Global Accelerator）支持保持客户端源IP功能，后端服务器可以通过该功能获取发起访问的客户端源IP。本文为您介绍在不同场景中如何开启保持客户端源IP功能以及后端服务器如何获取客户端源IP。

-   您已经在全球加速实例中配置了监听。具体操作，请参见[添加监听](/cn.zh-CN/用户指南/监听/添加监听.md)。
-   目前，保持客户端源IP功能白名单开放：
    -   如果您希望为已创建的全球加速实例开启保持客户端源IP功能，请[提交工单](https://selfservice.console.aliyun.com/ticket/category/ga/today)并注明想要开启保持客户端源IP功能的实例ID。申请开通后，您需要为全球加速实例重新创建监听并开启保持客户端源IP功能。
    -   如果您希望为新创建的全球加速实例开启保持客户端源IP功能，请直接[提交工单](https://selfservice.console.aliyun.com/ticket/category/ga/today)。

## 背景信息

通过全球加速服务加速客户端访问后端服务器，默认情况下后端服务器只能获取到客户端通过全球加速访问后端服务器的终端节点组IP，不能获取客户端的源IP。如果您需要后端服务器能获取客户端的源IP，您可以开启全球加速的保持客户端源IP功能。全球加速保持客户端源IP功能根据监听协议的不同，支持的情况也不同：

-   **HTTP**和**HTTPS**：支持保持客户端源IP功能。全球加速将客户端源IP保存在HTTP请求头的X-Forwarded-For字段中，后端服务器可以通过X-Forwarded-For字段获取客户端源IP。

    **说明：** 目前，HTTP和HTTPS监听协议白名单开放。如需使用，请[提交工单](https://selfservice.console.aliyun.com/ticket/category/ga/today)。

-   **UDP**：不支持保持客户端源IP功能。
-   **TCP**：支持保持客户端源IP功能。但根据后端服务类型不同，需要后端服务器做相应适配以获取客户端源IP。关于适配说明，请参见下表：

    |后端服务部署地|后端服务类型|是否支持获取客户端源IP|是否需要后端服务器适配|
    |-------|------|------------|-----------|
    |阿里云|阿里云公网IP|支持|不需要在您开启保持客户端源IP功能后，后端服务器可直接获取发起访问的客户端源IP，无需添加任何配置。 |
    |阿里云云服务器ECS（Elastic Compute Service）实例|支持|
    |阿里云负载均衡SLB（Server Load Balancer）实例|支持请注意在以下情形中，后端服务器无法获取客户端源IP：

    -   您的SLB实例的后端服务器为经典网络类型的ECS实例。
    -   您的SLB实例的监听协议为HTTP或HTTPS。
    -   您的SLB实例为应用型负载均衡ALB（Application Load Balancer） |
    |非阿里云|自定义IP|支持|需要在您开启保持客户端源IP功能的情况下，全球加速会使用Proxy Protocol保持客户端源IP，此时需要后端服务器支持解析Proxy Protocol，才能获取到客户端源IP信息。

**说明：** 如果您的后端服务器不支持解析Proxy Protocol，则会导致后端服务器无法正确解析加速流量。 |
    |自定义域名|支持|


**说明：**

Proxy Protocol是一种Internet协议，通过为TCP报文添加Proxy Protocol报头来获取客户端源IP。

Proxy Protocol的接收端必须在接收到完整有效的Proxy Protocol头部后才能开始处理连接数据，因此对于服务器中的同一个监听端口，不能同时接收携带Proxy Protocol和未携带Proxy Protocol的连接请求。如果接收到的第一个数据包不符合Proxy Protocol格式，那么服务器会直接终止连接。

## 通过HTTP或HTTPS监听协议加速访问后端服务

如果您通过HTTP或HTTPS监听协议加速您后端服务的访问，在您开启保持客户端源IP功能后，后端服务器可直接通过HTTP请求头的X-Forwarded-For字段获取客户端源IP。

1.  开启保持客户端源IP。

    HTTP和HTTPS监听协议默认开启保持客户端源IP功能，并将客户端源IP保存在HTTP请求头的X-Forwarded-For字段中，您可以通过X-Forwarded-For获取客户端源IP。

2.  获取客户端源IP。

    后端服务器收到的HTTP请求头中的X-Forwarded-For字段如下，其中第一个IP即为客户端源IP。

    ```
    X-Forwarded-For: 客户端源IP, 代理服务器1-IP， 代理服务器2-IP，...
    ```


## 通过TCP监听协议加速访问阿里云后端服务

如果您通过TCP监听协议加速您的后端服务访问，且您的后端服务部署在阿里云上，那么您开启保持客户端源IP功能后，后端服务器可直接获取客户端源IP信息。

1.  开启保持客户端源IP。

    1.  登录[全球加速管理控制台](https://ga.console.aliyun.com/list)。

    2.  在**实例列表**页面，找到目标全球加速实例，单击**操作**列下的**配置监听**。

    3.  在**监听**页签下，找到目标监听，单击**操作**列下的**配置**。

    4.  在**配置监听和协议**页面，单击**下一步**。

    5.  在**配置终端节点**页面，打开**保持客户端源IP**开关，然后单击**下一步**。

        ![开启保持客户端源IP](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3310860161/p127320.png)

    6.  在**配置审核**页面，确认无误后，单击**提交**。

2.  获取的客户端源IP。

    本部分以后端服务类型为阿里云Linux ECS实例为例，介绍如何查看已获取的客户端源IP。

    1.  登录后端Linux ECS服务器。

    2.  执行以下命令，抓取HTTP流量。

        `tcpdump tcp port [监听端口] -n -X -s 0`

    3.  从抓取的数据包中筛选信息，查看客户端源IP。

        经测试，开启保持客户端源IP功能后，可以在后端服务器查看客户端源IP。

        ![开启保持客户端源IP功能后，后端服务器获取到客户端源IP](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7130274951/p127315.png)

        未开启保持客户端源IP功能，只能在后端服务器上查看到客户端通过全球加速访问后端服务器的终端节点组IP。

        ![未开启保持客户端源IP](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7130274951/p127316.png)


## 通过TCP监听协议加速访问非阿里云后端服务

如果您通过TCP监听协议加速您的后端服务访问，且您的后端服务部署在非阿里云上，那么您的后端服务需要支持解析Proxy Protocol，才能获取到客户端源IP。本部分以Nginx为例，为您说明后端服务如何支持解析Proxy Protocol以及如何获取客户端源IP。

1.  开启保持客户端源IP。

    1.  登录[全球加速管理控制台](https://ga.console.aliyun.com/list)。

    2.  在**实例列表**页面，找到目标全球加速实例，单击**操作**列下的**配置监听**。

    3.  在**监听**页签下，找到目标监听，单击**操作**列下的**配置**。

    4.  在**配置监听和协议**页面，单击**下一步**。

    5.  在**配置终端节点**页面，打开**保持客户端源IP**开关，然后单击**下一步**。

        ![开启保持客户端源IP](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3310860161/p127320.png)

    6.  在**配置审核**页面，确认无误后，单击**提交**。

2.  配置Nginx使其支持解析Proxy Protocol。

    Nginx的`http{}`和`stream{}`模块均可以接收Proxy Protocol，在`http{}`模块或`stream{}`模块中添加相应处理Proxy Protocol的端口即可。

    ```
    http {
        #...
        server {
            listen 8080 proxy_protocol;    #在8080端口，开启解析proxy protocol。
            #...
        }
    }
       
    stream {
        #...
        server {
            listen 1235 proxy_protocol;    #在1235端口，开启解析proxy protocol。
            #...
        }
    }
    ```

3.  获取客户端源IP。

    在开始解析Proxy Protocol后，Nginx会将客户端源IP保存在变量proxy\_protocol\_addr中。因此，您可以通过以下两种方式获取客户端源IP：

    -   对于HTTP流量，您可以将客户端源IP保存在HTTP请求头字段中：

        ```
        http {
            proxy_set_header X-Real-IP       $proxy_protocol_addr;
            proxy_set_header X-Forwarded-For $proxy_protocol_addr;
        }
        ```

        后端服务器通过HTTP请求头中的X-Forwarded-For字段获取源IP，其中第一个IP即为客户端源IP。

        ```
        X-Forwarded-For: 客户端源IP, 代理服务器1-IP， 代理服务器2-IP，...
        ```

    -   对于HTTP流量或TCP流量，您也可以将客户端源IP保存在日志中，然后通过日志信息获取客户端源IP。
        1.  设置`http{}`模块和`stream{}`模块的日志格式，将客户端源IP信息保存到日志中。

            ```
            
            http {
                #...
                log_format combined '$proxy_protocol_addr - $remote_user [$time_local] ' ##在`http{}`模块的日志格式中添加保存客户端源IP的变量proxy\_protocol\_addr。
                                    '"$request" $status $body_bytes_sent '
                                    '"$http_referer" "$http_user_agent"';
            }
            #...
            stream {
                #...
                log_format basic '$proxy_protocol_addr - [$time_local] '                 ##在`stream{}`模块的日志格式中添加保存客户端源IP的变量proxy\_protocol\_addr。
                                  '$protocol $status $bytes_sent $bytes_received '
                                  '$session_time';
            }
                            
            ```

        2.  通过以下命令查看日志信息，获取客户端源IP。

            `tail -n -5 <日志路径>`

    以下内容为您展示一个完整的配置示例：

    ```
    worker_processes  4;
    events {
        worker_connections  1024;
    }
    
    http {
        include       mime.types;
        default_type  application/octet-stream;
        log_format  main  '$proxy_protocol_addr $remote_addr - $remote_user [$time_local] "$request" '##在`http{}`模块日志格式中添加保存客户端源IP的变量proxy\_protocol\_addr。
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
            listen       80 proxy_protocol;                          ##在80端口，开启解析proxy protocol。
            server_name  example.com;
    
            proxy_set_header X-Real-IP       $proxy_protocol_addr;   ##在发给后端服务时，将客户端源IP信息插入到HTTP中。
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
        log_format tcp_basic '$proxy_protocol_addr - [$time_local] '  ##在`stream{}`模块的日志格式中添加保存客户端源IP的变量proxy\_protocol\_addr。
                          '$protocol $status $bytes_sent $bytes_received '
                          '$session_time';
        upstream stream_backend {
            server 192.XX.XX.36:2003;
            server 192.XX.XX.37:2003;
        }
    
        server {
            listen 1234 proxy_protocol;                               ##在1234端口，开启解析proxy protocol。
            access_log  /var/log/nginx/access_tcp.log  tcp_basic;   
            proxy_pass stream_backend;
        }
    }
    ```

    查看日志信息，其中日志信息中的第一个IP地址即为客户端源IP。

    ![保持源IP-查看日志](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3310860161/p188555.png)



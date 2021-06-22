# 配置CNAME

如果您是通过域名方式加速，则您需要配置源站的智能DNS，将加速域名指向CNAME地址。

## 步骤1：获取加速域名的CNAME地址

完成以下操作，在全球加速中获取加速域名的CNAME地址。

1.  登录[全球加速管理控制台](https://ga.console.aliyun.com/list)。

2.  在**实例列表**页面，找到目标全球加速实例，单击实例ID链接。

3.  在**基本信息**区域，找到**CNAME**，然后单击CNAME值右侧的**复制**。

    ![cname](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1011724261/p83352.png)


## 步骤2：添加CNAME记录

完成以下操作，添加CNAME记录。

1.  登录 [域名解析控制台](https://dns.console.aliyun.com/#/dns/domainList)。

2.  在域名解析页面，找到目标域名，单击**操作**列下的**解析设置**。

3.  在**解析设置**页面，单击**添加记录**。

4.  在**添加记录**对话框，根据以下信息配置CNAME记录，然后单击**确认**。

    |配置|说明|
    |--|--|
    |**记录类型**|选择`CNAME`。|
    |**主机记录**|加速域名的前缀。     -   如果您的加速域名为`testcdn.aliyun.com`，主机记录为`testcdn`。
    -   如果您的加速域名为`www.aliyun.com`，主机记录为`www`。
    -   如果您的加速域名为`aliyun.com`，主机记录为`@`。
    -   如果您的加速域名为`*.aliyun.com`，主机记录为`*`。 |
    |**解析线路**|选择**默认**。|
    |**记录值**|粘贴在[步骤1：获取加速域名的CNAME地址](#section_3hx_e4l_3t7)中复制的CNAME值。|
    |**TTL**|选择**10分钟**。|

    **说明：**

    -   新增CNAME记录会实时生效，修改CNAME记录72小时之内生效。
    -   配置完CNAME后，由于状态更新约有10分钟延迟，控制台的域名列表页可能仍提示“未配置CNAME”，请您暂时忽略。

## 步骤3：验证CNAME配置

该步骤以Windows系统为例，验证CNAME配置是否生效。

1.  打开Windows的CMD命令行程序。

2.  执行`ping`命令，`ping`加速域名。

    如果回显信息包括`*.*kunlun*.com`，则表示CNAME配置已经生效。

    ![CNAME生效验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9618134161/p66693.png)



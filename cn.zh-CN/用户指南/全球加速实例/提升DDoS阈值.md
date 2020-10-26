# 提升DDoS阈值

您可以为全球加速提升DDoS阈值，提升DDoS阈值后，全球加速与DDoS高防实例并联部署，仅在特定场景下触发并切换启用DDoS高防实例，保证无DDoS攻击时日常业务的流畅体验以及发生DDoS攻击时达到更好的防护效果。

## 配置场景

本教程以下图场景为例。

![配置场景](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5422443061/p176056.png)

某公司的Web服务部署在美国（硅谷），终端用户主要集中在中国（香港）。因跨国公网不稳定，中国（香港）终端用户访问美国（硅谷）的Web服务经常出现延迟、抖动、丢包等网络问题。针对以上问题，该公司使用阿里云全球加速减少了延迟、抖动、丢包等网络问题的出现。但Web服务经常受到DDoS攻击，严重影响Web服务的安全性和可用性。

您可以为全球加速提升DDoS阈值，提升DDoS阈值后，全球加速将与DDoS高防实例并联部署，部署完成后：

-   Web服务在无攻击时，中国（香港）地域终端用户的访问请求通过加速IP就近从接入点进入阿里云加速网络，然后通过智能选择路由和自动网络调度，把终端用户的网络访问请求送达至终端节点。
-   Web服务在受到攻击时，触发并切换启用DDoS高防实例，清洗过滤流量后再通过就近的接入点进入阿里云加速网络，然后通过智能选择路由和自动网络调度，把终端用户的网络访问请求送达至终端节点。

## 前提条件

开始前，请确保满足以下条件：

-   您已经注册了阿里云账号。如未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm)。
-   您已经提交了提升DDoS阈值功能的使用申请。如未提交，请[提交工单](https://selfservice.console.aliyun.com/ticket/category/ga/today)。
-   您已经购买了DDoS高防实例，并添加了转发规则。详细信息，请参见[开通DDoS高防（新BGP&国际）](/cn.zh-CN/DDoS高防（新BGP&国际）用户指南/开通DDoS高防（新BGP&国际）.md)和[添加转发规则](/cn.zh-CN/DDoS高防（新BGP&国际）用户指南/快速入门/防护网站业务/步骤1：添加网站业务转发规则.md)。

## 配置步骤

![配置步骤](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6284963061/p176347.png)

## 步骤一：提升DDoS阈值

提升DDoS阈值后，全球加速和DDoS高防实例并联部署，保证无DDoS攻击时日常业务的流畅体验以及发生DDoS攻击时达到更好的防护效果。

**说明：** 为全球加速提升DDoS阈值时，系统会判断全球加速是否拥有服务关联角色AliyunServiceRoleForGaAntiDdos：

-   如果全球加速不存在服务关联角色AliyunServiceRoleForGaAntiDdos，系统会自动创建该服务关联角色，并为该服务关联角色添加名称为AliyunServiceRolePolicyForGaAntiDdos的权限策略，授予全球加速拥有访问DDoS高防实例的权限。
-   如果全球加速已经拥有服务关联角色AliyunServiceRoleForGaAntiDdos，则不会重复创建该服务关联角色。

详细信息，请参见[AliyunServiceRoleForGaAntiDdos]()。

1.  登录[全球加速管理控制台](https://ga.console.aliyun.com/list)。

2.  在**实例列表**页面，找到目标全球加速实例，单击其**操作**列下的**![更多图标](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/1089063061/p176188.png)** \> **提升DDoS阈值**。

3.  在**提升DDoS阀值**对话框，根据以下信息选择要联动的DDoS高防实例。

    -   **DDoS联动产品**：选择要联动的DDoS高防实例类型。本教程选择**DDoS高防（国际）**。
    -   **DDoS高防实例**：选择要联动的DDoS高防实例。
4.  单击**确定**。


提升DDoS阈值后，系统会分配一个全球加速联动DDoS高防的CNAME，用于全球加速和DDoS高防的联动。

**说明：** CNAME名称中含有**-1**即为全球加速联动DDoS高防的CNAME，例如ga-bp1f609c76zg6\*\*\*\*zuna-1.aliyungaxxxx.com。

![GA联动DDoS CNAME](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/4527863061/p176319.png)

## 步骤二：修改DNS解析

您需要将DNS解析到全球加速联动DDoS高防CNAME，才能实现按需防护，即Web服务在无攻击时，终端用户访问Web服务通过全球加速服务进行加速；Web服务在受到攻击时，访问Web服务的流量切换到DDoS高防节点，流量清洗后再送到全球加速的加速节点。本教程以阿里云云解析DNS为例，为您介绍如何配置DNS解析。

**说明：** 如果您使用的DNS解析服务为非阿里云云解析DNS，请登录您的DNS服务商系统修改网站域名的解析记录。

完成以下操作，修改DNS解析。

1.  登录[阿里云云解析DNS控制台](https://dns.console.aliyun.com)。

2.  在**域名解析**页面，找到目标域名，单击**操作**列下的**解析设置**。

3.  在**解析设置**页面，找到要修改的解析记录，单击**操作**列下的**修改**。

4.  在**修改记录**对话框，选择**记录类型**为**CNAME**，并将**记录值**修改为步骤一提升DDoS阈值后系统分配的全球加速联动DDoS高防CNAME地址。详细信息，请参见[步骤一：提升DDoS阈值](#section_896_4vs_whu)。

    ![修改记录](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9472029951/p135152.png)

5.  单击**确认**。


## 步骤三：访问测试

提升DDoS阈值后，您可以测试全球加速联动DDoS高防的防护效果。

1.  在接入地域（本教程为中国香港）的电脑中打开浏览器。

2.  使用网站域名访问美国（硅谷）地域部署的Web服务。

    经测试，可以通过网站域名访问美国（硅谷）地域部署的Web服务。

    ![访问测试](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/4405588951/p96014.png)

3.  执行`dig <网站域名>`查看解析结果。

    -   源站未被攻击时：解析结果为配置的全球加速的IP。
    -   源站被攻击时：解析结果为DDoS高防实例的IP。

**相关文档**  


[AttachDdosToAccelerator](/cn.zh-CN/API参考/全球加速实例/AttachDdosToAccelerator.md)


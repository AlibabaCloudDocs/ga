# 获取AccessKey

您可以为阿里云账号或RAM用户创建一个访问密钥（AccessKey）。在调用阿里云API时您需要使用AccessKey完成身份验证。

AccessKey包括AccessKey ID和AccessKey Secret。

-   AccessKey ID：用于标识用户。
-   AccessKey Secret：用于验证用户的密钥。AccessKey Secret必须保密。

**警告：** 阿里云账号AccessKey泄露会威胁您所有资源的安全。建议您使用RAM用户AccessKey进行操作，可以有效降低AccessKey泄露的风险。

1.  以阿里云账号登录[阿里云管理控制台](https://home.console.aliyun.com/new?spm=a2c4g.11186623.2.13.b22b5f81PaDcNA#/)。

2.  将鼠标置于页面右上方的账号图标，单击**AccessKey管理**。

3.  在**安全提示**页面，选择获取阿里云账号还是RAM用户的AccessKey。

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3675425061/p48002.png)

4.  获取账号AccessKey。

    -   获取阿里云账号AccessKey
        1.  单击**继续使用AccessKey**。
        2.  在AccessKey管理页面，单击**创建AccessKey**。
        3.  在手机验证对话框，获取验证码，完成手机验证，然后单击**确定**。
        4.  在创建AccessKey对话框，查看AccessKey ID和AccessKey Secret。您可以单击**下载CSV文件**，下载AccessKey信息或者单击**复制**，复制AccessKey信息。

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8947359951/p48003.png)

    -   获取RAM用户AccessKey
        1.  单击**开始使用子用户AccessKey**。
        2.  如果您未创建RAM用户，请在系统跳转的[RAM访问控制台](https://ram.console.aliyun.com/users/new)的用户页面，创建RAM用户。如果您需要获取已有RAM用户的AccessKey，则跳过此步骤。
        3.  在[RAM访问控制台](https://ram.console.aliyun.com/users/new)的左侧导航栏，选择**人员管理** \> **用户**，搜索需要获取AccessKey的RAM用户。
        4.  单击RAM用户登录名称，在RAM用户详情页面的认证管理页签下的用户AccessKey区域，单击**创建AccessKey**。
        5.  在手机验证对话框，获取验证码，完成手机验证，然后单击**确定**。
        6.  在创建AccessKey对话框，查看AccessKey ID和AccessKey Secret。您可以单击**下载CSV文件**，下载AccessKey信息或者单击**复制**，复制AccessKey信息。

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7037906061/p48004.png)



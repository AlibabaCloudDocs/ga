# Obtain an AccessKey pair

You can create an AccessKey pair for an Alibaba Cloud account or a RAM user. When you call API operations, you must use the AccessKey pair to complete identity verification.

An AccessKey pair consists of an AccessKey ID and an AccessKey secret.

-   AccessKey ID: verifies the identity of a user.
-   AccessKey secret: verifies the password of a user. You must keep your AccessKey secret strictly confidential.

**Warning:** If the AccessKey pair of your Alibaba Cloud account is leaked, your resources are exposed to risks. We recommend that you use the AccessKey pair of a RAM user. This minimizes the possibility of AccessKey pair leaks.

1.  Log on to the [Alibaba Cloud Management Console](https://home.console.aliyun.com/new?spm=a2c4g.11186623.2.13.b22b5f81PaDcNA#/) with your Alibaba Cloud account.

2.  Move the pointer over the profile picture in the upper-right corner of the page and click **AccessKey Management**.

3.  In the **Note** dialog box, select Use Current AccessKey Pair or Use AccessKey Pair of RAM User.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6415559951/p48002.png)

4.  Obtain an AccessKey pair.

    -   Obtain the AccessKey pair of your Alibaba Cloud account
        1.  Click **Use Current AccessKey Pair**.
        2.  On the AccessKey Management page, click **Create AccessKey**.
        3.  In the MFA Verification dialog box, enter the verification code in the Verification Code field and click **OK**.
        4.  After you create an AccessKey pair, you can view the AccessKey ID and AccessKey secret in the Create AccessKey dialog box. You can also click **Download CSV File** or **Copy** to download or copy the AccessKey pair.

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6415559951/p48003.png)

    -   Obtain the AccessKey pair of a RAM user
        1.  Click **Use AccessKey Pair of RAM User**.
        2.  If you have not created a RAM user, you are automatically redirected to the Users page of the [RAM console](https://ram.console.aliyun.com/users/new). On this page, create a RAM user. If a RAM user is already created, skip this step.
        3.  In the left-side navigation pane of the [RAM console](https://ram.console.aliyun.com/users/new), choose **Identities** \> **Users**, and find the RAM user whose AccessKey pair you want to obtain.
        4.  Click the username of the RAM user. In the User AccessKeys section of the Authentication tab, click **Create AccessKey**.
        5.  In the MFA Verification dialog box, enter the verification code and click **OK**.
        6.  After you create an AccessKey pair, you can view the AccessKey ID and AccessKey Secret in the Create AccessKey dialog box. You can also click **Download CSV File** or **Copy** to download or copy the AccessKey pair.

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6415559951/p48004.png)



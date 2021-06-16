# Create a CNAME record

If you are implementing network acceleration by using an accelerated domain, you need to configure intelligent DNS resolution for the origin server. You must map the accelerated domain name to the canonical name \(CNAME\) that has been allocated to the accelerated domain.

## Step 1: Obtain the CNAME of the accelerated domain

To obtain the CNAME of the accelerated domain in Global Acceleration \(GA\), follow these steps:

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the target GA instance, and click the instance ID.

3.  In the **Basic Information** section, find the **CNAME** field, move the mouse pointer to the CNAME value, and then click the ![Copy the CNAME](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7423839951/p76499.png) icon next to the value.

    ![CNAME](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7423839951/p83352.png)


## Step 2: Create a CNAME record

To create a CNAME record, follow these steps:

1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com/#/dns/domainList).

2.  On the Manage DNS page, find the target domain name, and click **Configure** in the **Actions** column.

3.  On the **DNS Settings** page that appears, click **Add Record**.

4.  In the **Add Record** dialog box, set the required parameters as follows, and click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Type**|Select `CNAME` from the drop-down list.|
    |**Host**|Enter the prefix of the accelerated domain name.     -   If the accelerated domain name is `testcdn.aliyun.com`, set the host to `testcdn`.
    -   If the accelerated domain name is `www.aliyun.com`, set the host to `www`.
    -   If the accelerated domain name is `aliyun.com`, set the host to `@`.
    -   If the accelerated domain name is `*.aliyun.com`, set the host to `*`. |
    |**ISP Line**|Select **Default** from the drop-down list.|
    |**Value**|Paste the CNAME value that was copied in step 1.|
    |**TTL**|Select **10 minute\(s\)**.from the drop-down list.|

    **Note:**

    -   A newly created CNAME record takes effect immediately. If you modify the CNAME record, the record takes effect within 72 hours after the modification.
    -   After you create a CNAME record, it takes approximately 10 minutes to update the status in the console. The message "You must add the CNAME record" may still appear on the Domains page. Please ignore this message.

## Step 3: Verify the CNAME configuration

To verify the CNAME configuration, follow these steps:

1.  Open the Command Prompt in Windows.

2.  Run the `ping` command to `ping` the accelerated domain.

    If the output includes `*.*kunlun*.com`, the CNAME record has taken effect.

    ![Check whether the new CNAME record has taken effect](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7423839951/p66693.png)



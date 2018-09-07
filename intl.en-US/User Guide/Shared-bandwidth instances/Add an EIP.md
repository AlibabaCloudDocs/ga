# Add an EIP {#task_tgq_s5y_5db .task}

After creating a shared-bandwidth instance, you need to add an EIP to it to accelerate the Internet access to the backend service.

You have created a shared-bandwidth Global Acceleration instance.

After being added to a shared-bandwidth instance, the EIP can accelerate Internet access for the backend service. After an EIP is added to a shared-bandwidth instance:

-   The added EIP shares the bandwidth of the shared-bandwidth instance and the original bandwidth of the EIP is disabled.
-   The original billing method of the EIP is also disabled. The EIP becomes a public IP and no additional traffic or bandwidth fee is charged.

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com). 
2.  On the Global Acceleration page, click **Shared Bandwidth**. 
3.  Find the target instance and click **Add IP Address**. 
4.  On the Add IP Address page, complete these steps: 
    -   If there is no unused EIP under your account, click **Buy EIP and add to Global Acceleration**, enter the number of EIPs to buy and click **OK**.

        After the EIPs are created, they are automatically added to the shared-bandwidth instance.

    -   If there is an unused EIP in your account, click **Select from EIP list**, select the EIP to bind and click **OK**.

        **Note:** The EIP instance and the Global Acceleration instance must be in the same region.



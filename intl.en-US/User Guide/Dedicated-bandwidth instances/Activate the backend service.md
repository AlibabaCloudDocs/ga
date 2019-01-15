# Activate the backend service {#concept_rdz_k4y_5db .concept}

After binding an ECS instance to a dedicated-bandwidth instance, you must activate the backend service. By adding a sub interface to the ECS Network Interface Card \(NIC\), the ECS instance then can receive packets sent from the dedicated-bandwidth instance.

To avoid network conflicts between Global Acceleration and the Internet configurations of ECS instances such as EIP and NAT Gateway, the system uses the public IP of the Global Acceleration instance and the IP address of the backend service \(not the private IP of the ECS\) to establish a connection.

An ECS instance of the VPC network has only one private NIC and one private IP address. It cannot receive packets sent from Global Acceleration. Activating the backend service adds the IP address of the backend service as a sub interface to the ECS NIC. In this way, the ECS instance can receive packets sent from Global Acceleration.

## Prerequisites {#section_ezk_y4y_5db .section}

-   Create a dedicated-bandwidth Global Acceleration instance
-   Bind an ECS instance

## Step 1 Obtain the IP address of the backend service {#section_g3m_bpy_5db .section}

To obtain the IP address of the backend service, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc) .
2.  In the left-side navigation pane, click **Global Acceleration**.
3.  Click **Dedicated Bandwidth** and find the target instance.
4.  In the **Backend Service Instance** column, view the backend service IP.

    The backend service IP is an unused private IP randomly allocated from the VSwitch to which the ECS instance belongs.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12638/15475260301534_en-US.png)


## Step 2 Add a NIC sub interface {#section_c4t_kry_5db .section}

You need to add a subnet interface to activate the acceleration service.

**Note:** You need to add a sub interface to the NIC of the ECS instance, instead of adding a new NIC.

-   Configure a Linux ECS instance

    The following procedure takes the Ubuntu 16.04 64 operating system as an example:

    1.  Log on to the ECS instance and run the following command to open the NIC configuration file:

        ```
        sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0:1
        ```

    2.  Add the following configurations to the configuration file:

        ```
        
        DEVICE=eth0:1
        IPADDR=172.16.1.209
        NETMASK=255.255.255.255
        ONBOOT=yes
        ```

        where:

        -   DEVICE is the name of the sub interface.
        -   IPADDR is the IP address of the backend service.
    3.  Run the following command to enable the NIC sub interface:

        ```
        ifup eth0:1
        ```

-   Configure a Windows ECS instance

    Complete the following steps to configure a Windows ECS instance:

    1.  Log on to the ECS instance and run the ipconfig command to view the IP address of the instance.
    2.  Run the following command to create an Ethernet interface:

        ```
        
        netsh interface ipv4 set address name=<Ethernet adapter name> source=static address= mask=<Subnet mask> gateway=<Default gateway>
        ```

        Example:

        ```
        
        netsh interface ipv4 set address name="Local connection 4" source=static address=172.16.x.xxx mask=255.255.255.255 gateway=172.16.x.xxx
        ```

    3.  Run the following command to add a sub interface:

        ```
        netsh interface ipv4 add address <Ethernet adapter name> <Backend service IP address> <Subnet mask>
        ```

        Example:

        ```
        netsh interface ipv4 add address "Local connection 4" 172.16.x.xxx 255.255.255.255
        ```

        If you do not want to use the Global Acceleration backend service IP address as the default IP, you must set the SkipAsSource to True.

        Example:

        ```
        netsh interface ipv4 add address "Local connection 4" 172.16.x.xxx 255.255.255.255
        ```



---
keyword: [forwarding rules, paths, domain names, virtual endpoint groups]
---

# Manage forwarding rules

Only HTTP and HTTPS listeners support domain-based or path-based forwarding rules. After an HTTP or HTTPS listener receives a request, the system forwards the request to a specific endpoint group if the destination domain name or path of the request matches a forwarding rule.

-   Only HTTP and HTTPS listeners support forwarding rules. Make sure that you have created an HTTP or HTTPS listener. For more information, see [Create a listener](/intl.en-US/User Guide/Listeners/Add listeners.md).
-   A virtual endpoint group is created. For more information, see [Create a virtual endpoint group](/intl.en-US/User Guide/Endpoint groups and endpoints/Configure an endpoint group.md).

Forwarding rules are classified into default forwarding rules and custom forwarding rules:

-   Default forwarding rules: After you create an HTTP or HTTPS listener, the system automatically creates a default forwarding rule and associates it with the default endpoint group. A listener contains only one default forwarding rule. You cannot modify or delete the default forwarding rule.
-   Custom forwarding rules: After you create an HTTP or HTTPS listener, you can manually create custom forwarding rules based on your business requirements. You can create multiple custom forwarding rules for a listener.

Each forwarding rule consists of the following components:

-   Forwarding conditions: Only after a request matches a forwarding condition, the request is forwarded to the specified endpoint group. You can configure a forwarding condition in the following ways:
    -   Specify only a domain name. You can specify only one domain name as the forwarding condition in a forwarding rule. If a request matches the specified domain name, the request is forwarded to the specified endpoint group.
    -   Specify only paths. You can specify multiple paths as the forwarding condition in a forwarding rule. If a request matches one of the specified paths, the request is forwarded to the specified endpoint group.
    -   Specify both a domain name and paths. If a request matches the specified domain name or one of the specified paths, the request is forwarded to the specified endpoint group.
-   Forwarding action: forwards the request that matches the forwarding condition to a specific endpoint group. Each forwarding rule can point to only one endpoint group.

A listener can contain only one default forwarding rule and multiple custom forwarding rules. The system attempts to match a request with a forwarding rule in the following ways:

-   Method 1: If the request contains a domain name, the system attempts to match the request with a forwarding rule based on the domain name.
    -   If the domain name matches a forwarding rule, the system attempts to match the path of the request with the forwarding rule.

        If the path also matches the forwarding rule, the request is forwarded to the specified endpoint group. If the path does not match the forwarding rule, the request is forwarded based on a domain-based forwarding rule. The domain name of the request is specified as the forwarding condition of the domain-based forwarding rule and no path is specified.

        If such a domain-based forwarding rule is not configured for the listener, an HTTP 404 status code is returned to the client.

    -   If no forwarding rule matches the domain name, the system uses Method 2.
-   Method 2: If a request does not contain a domain name or the listener does not contain a forwarding rule that matches the domain name, the system attempts to match the request with a path-based forwarding rule. Only paths are specified as the forwarding condition of the path-based forwarding rule and no domain names are specified.

If the system matches a request by using one of the preceding methods, the request is forwarded to the specified endpoint group. If no forwarding rule matches the request, the request is matched with the default forwarding rule and forwarded to the default endpoint group.

![Procedure of matching domain names and paths](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0036848161/p235742.png)

## Create a forwarding rule

After you create an HTTP or HTTPS listener, the system automatically creates a default forwarding rule and associates it with the default endpoint group. You cannot modify or delete the default forwarding rule. You can perform the following steps to create, modify, or delete a custom forwarding rule.

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the GA instance that you want to manage and click **Configure Listeners** in the **Actions** column.

3.  On the **Listeners** tab, find the listener that you want to manage and click the ID of the listener.

4.  On the listener details page, click the **Forwarding Rule** tab.

5.  On the **Forwarding Rule** tab, click **Add Forwarding Rule** and set the following parameters.

    |Parameter|Description|
    |---------|-----------|
    |**If \(Matching All Conditions\)**|Configure the forwarding condition.     -   **Domain Name**

The domain name must be 3 to 128 characters in length and can contain letters, digits, hyphens \(-\), and periods \(.\).Supported wildcard characters are asterisks \(\*\) and question marks \(?\).

    -   **Path**

The path must be 1 to 128 characters in length and must start with a forward slash \(/\). The path can contain letters, digits, dollar signs \($\), hyphens \(-\), underscores \(\_\), periods \(.\), plus signs \(+\), forward slashes \(/\), ampersands \(&\), tildes \(~\), at signs \(@\), colons \(:\), and apostrophes \('\).Supported wildcard characters are asterisks \(\*\) and question marks \(?\). |
    |**Forward to Virtual Endpoint Group**|Select the virtual endpoint group to which a matched request is forwarded.|

6.  Click **OK**.


## Modify a forwarding rule

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the GA instance that you want to manage and click **Configure Listeners** in the **Actions** column.

3.  On the **Listeners** tab, find the listener that you want to manage and click the ID of the listener.

4.  On the listener details page, click the **Forwarding Rule** tab.

5.  On the **Forwarding Rule** tab, find the forwarding rule that you want to modify, click ![The Edit icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0036848161/p235154.png) in the upper-right corner, modify the forwarding rule, and then click **Save**.


## Delete a forwarding rule

1.  Log on to the [Global Accelerator console](https://ga.console.aliyun.com/list).

2.  On the **Instances** page, find the GA instance that you want to manage and click **Configure Listeners** in the **Actions** column.

3.  On the **Listeners** tab, find the listener that you want to manage and click the ID of the listener.

4.  On the listener details page, click the **Forwarding Rule** tab.

5.  On the **Forwarding Rule** tab, find the forwarding rule that you want to delete and click ![The Delete icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0036848161/p235318.png) in the upper-right corner.

6.  In the dialog box that appears, confirm the ID of the forwarding rule and click **OK**.



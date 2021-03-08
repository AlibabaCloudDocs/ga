# Subscription

Global Accelerator \(GA\) supports only the subscription billing method. You must pay upfront fees to use subscription resources. The billing cycle is 30 days.

**Note:** During the period from April 15, 2020 to April 1, 2021, if a first-time user uses an Alibaba Cloud account to purchase the GA service, a one-month free trial is provided. Note that this account must pass real-name verification as enterprise identities. Submit an application for a free trial. To apply for a free trial, visit the [GA Free Trial Application](https://page-intl.aliyun.com/form/act857014000/index.htm) page. For more information about the free trial and the instance types that support the free trial, see [GA free trials](/intl.en-US/Announcement/GA free trials.md).

## Billing items

GA fee = Instance fee + Specification fee + Bandwidth fee

## Instance fee

Instance fee = Instance unit price \(USD/Month\) × Duration

For more information about the unit price of a GA instance,visit the [buy page](https://common-buy-intl.aliyun.com/?commodityCode=ga_pluspre_public_intl#/buy).

## Specification fee

Specification fee = Specification unit price \(USD/Month\) × Duration

GA supports the following types of instance specifications: Small I, Small II, Small III, Medium I, Medium II, and Medium III. The acceleration performance can vary based on the instance specification.

|Instance specification|Number of acceleration regions|Peak bandwidth|Maximum number of concurrent connections|
|----------------------|------------------------------|--------------|----------------------------------------|
|Small I|1|20 Mbit/s|5,000|
|Small II|2|40 Mbit/s|10,000|
|Small III|3|60 Mbit/s|15,000|
|Medium I|5|100 Mbit/s|25,000|
|Medium II|8|160 Mbit/s|40,000|
|Medium III|10|200 Mbit/s|50,000|

The unit price varies based on GA instance specifications.For more information about the pricing of GA specifications, visit the [buy page](https://common-buy-intl.aliyun.com/?commodityCode=ga_pluspre_public_intl#/buy).

## Bandwidth usage fee

Bandwidth fee = Basic bandwidth plan fee + Cross-border bandwidth plan fee. The cross-border bandwidth plan fee is not charge if it is not purchased.

-   Basic bandwidth plan

    Basic bandwidth plan fee = Unit price of the basic bandwidth plan \(USD/Month\) × Peak bandwidth \(MB\) × Duration

    Basic bandwidth plans support the following types of bandwidth: basic, enhanced, and premium. The following table shows that the acceleration type, acceleration backend service, and acceleration scope of a basic bandwidth plan can vary based on the bandwidth type.

    |Bandwidth type|Workload type|Accelerated object|Acceleration scope|
    |--------------|-------------|------------------|------------------|
    |Basic bandwidth|Applications that are deployed on Alibaba Cloud|    -   Elastic Compute Service \(ECS\)
    -   Server Load Balancer \(SLB\)
    -   Alibaba Cloud public IP address

**Note:** If ECS instances and SLB instances run in classic networks, both types of instances are not supported.

|By default, networking within mainland China is accelerated.You can also purchase a cross-border bandwidth plan. This allows you to optimize the acceleration of networking between mainland China and other areas.|
    |Enhanced bandwidth|    -   Applications that are deployed on Alibaba Cloud
    -   Applications that are not deployed on Alibaba Cloud
|    -   ECS
    -   SLB
    -   Alibaba Cloud public IP address
    -   Custom IP address
    -   Custom domain name
|By default, networking within mainland China is accelerated.You can also purchase a cross-border bandwidth plan. This allows you to optimize the acceleration of networking between mainland China and other areas.|
    |Premium bandwidth|    -   Applications that are deployed on Alibaba Cloud
    -   Applications that are not deployed on Alibaba Cloud
|    -   ECS
    -   SLB
    -   Alibaba Cloud public IP address
    -   Custom IP address
    -   Custom domain name
|By default, network connections are accelerated on a global scale. Network traffic transmitted from mainland China to areas outside China is accelerated in the China \(Hong Kong\) region.If you also purchase a cross-border bandwidth plan, the acceleration of network connections between mainland China and areas outside China are reinforced.|

    **Note:** You can specify ECS or SLB as the backend service type only when your account is included in the whitelist of GA. If you want to specify ECS or SLB as the backend service type, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

    The unit price of the basic bandwidth plan varies based on bandwidth types. For more information about the pricing of basic bandwidth plans, visit the [buypage](https://common-buy-intl.aliyun.com/?commodityCode=ga_bwppreintl_public_intl#/buy).

-   Cross-border bandwidth plan

    Cross-border bandwidth plan fee = Unit price of the cross-border bandwidth plan \(USD/Month\) × Peak bandwidth \(MB\) × Duration

    You can specify only Mainland China and Global as the interconnected areas when you purchase a cross-border bandwidth plan. For more information about the pricing of cross-border bandwidth plans, visit the [buy page](https://common-buy-intl.aliyun.com/?commodityCode=ga_cbbwp_public_intl#/buy).



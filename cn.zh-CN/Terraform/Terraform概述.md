# Terraform概述

Terraform是一种开源工具，用于安全高效地预览，配置和管理云基础架构和资源。

## 概览

[HashiCorp Terraform](https://www.terraform.io/?spm=a2c4g.11186623.2.11.55e267a38YzsUB) 是一个IT基础架构自动化编排工具，可以用代码来管理维护 IT 资源。Terraform的命令行接口（CLI）提供一种简单机制，用于将配置文件部署到阿里云或其他任意支持的云上，并对其进行版本控制。它编写了描述云资源拓扑的配置文件中的基础结构，例如虚拟机、存储帐户和网络接口。

Terraform是一个高度可扩展的工具，通过 Provider 来支持新的基础架构。Terraform能够让您在阿里云上轻松使用 [简单模板语言](https://www.terraform.io/docs/configuration/syntax.html) 来定义、预览和部署云基础结构。您可以使用Terraform来创建、修改、删除ECS、VPC、RDS、SLB等多种资源。

阿里云作为国内第一家与 Terraform 集成的云厂商，[terraform-provider-alicloud](https://www.terraform.io/docs/providers/alicloud/index.html)目前已经提供了超过 163 个 Resource 和 113 个 Data Source，覆盖计算，存储，网络，负载均衡，CDN，容器服务，中间件，访问控制，数据库等超过35款产品，已经满足了大量大客户的自动化上云需求。

从 Terraform 0.12.2 版本开始，阿里云支持将对象存储服务 OSS 作为标准的[Remote State Backend](https://www.terraform.io/docs/backends/types/oss.html)，开始提供远端存储 State 的能力，在提高 state 安全性的同时，提升多人协作效率。

为了给开发者提供“开箱即用”的使用体验，阿里云提供了丰富多样的[Modules](https://registry.terraform.io/browse/modules?provider=alicloud) 和[Examples](https://github.com/terraform-providers/terraform-provider-alicloud/tree/master/examples)，覆盖计算，存储，网络，中间件，数据库等多个产品和使用场景，欢迎大家使用和贡献自己的Module。

## 优势

-   将基础结构部署到多个云

    Terraform适用于多云方案，将类似的基础结构部署到阿里云、其他云提供商或者本地数据中心。开发人员能够使用相同的工具和相似的配置文件同时管理不同云提供商的资源。

-   自动化管理基础结构

    Terraform能够创建配置文件的模板，以可重复、可预测的方式定义、预配和配置ECS资源，减少因人为因素导致的部署和管理错误。能够多次部署同一模板，创建相同的开发、测试和生产环境。

-   基础架构即代码（Infrastructure as Code）

    可以用代码来管理维护资源。允许保存基础设施状态，从而使您能够跟踪对系统（基础设施即代码）中不同组件所做的更改，并与其他人共享这些配置 。

-   降低开发成本

    您通过按需创建开发和部署环境来降低成本。并且，您可以在系统更改之前进行评估。


## 应用场景

Terraform的应用场景，请参见[应用场景]()。


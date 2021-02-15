---
solution: Campaign Classic
product: campaign
title: Hosting models
description: Discover Campaign hosting models
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
---

# Campaign Classic hosting models{#hosting-models}

Adobe Campaign offers a choice of three hosting models, providing flexibility and freedom to choose the best model, or models to suit business needs.

>[!NOTE]
>
>To learn more about the main differences between deployment modes, refer to [this page](../../installation/using/capability-matrix.md).

## Managed Services (Hosted)

  Adobe Campaign can be deployed as a Managed Service: all components of Adobe Campaign, including the user interface, the execution management engine, and the customer's Campaign database are fully hosted by Adobe, including email execution, mirror pages, tracking server, and externally-facing web components such as unsubscribe page/preference center and landing pages. Adobe allocates up to three instances in the Cloud---Development, Test/Stage, and Production.

  ![](assets/deployment_hosted.png)

As a hosted customer, most of the installation and configuration steps are performed by Adobe. You can access the following sections to customize your implementation:

* Configure tracking and mirror page URLs per brand. For transactional messages, refer [to this section](../../message-center/using/configuring-multibranding.md).
* Install the client console: refer [to this section](../../installation/using/installing-the-client-console.md).
* Learn more on the deliverability tools and best practices by reading the [getting started guide](../../delivery/using/deliverability-key-points.md) and [detailed documentation](../../delivery/using/about-deliverability.md).
* Configure Campaign options: refer [to this section](../../installation/using/configuring-campaign-options.md).
* Configure CRM connectors: refer [to this section](../../platform/using/crm-connectors.md).


## Hybrid

  When deployed as a hybrid model, the Adobe Campaign solution software resides on-premise at the customer site, and execution management is delivered as a cloud service by Adobe. Adobe Campaign marketing instance is installed inside a customer's firewall, so personally identifiable information (PII) remains in-house and only data required to personalize emails is sent to the Cloud for email execution. The execution instance, hosted in the Cloud, receives the requests from the On-Premise instance to deliver emails. This instance personalizes all the emails and delivers them. No data of any kind is permanently stored in the cloud. 

  ![](assets/deployment_hybrid.png)

As a hosted customer, most of the installation and configuration steps are performed by Adobe. You can access the following sections to customize your implementation:

* Configure transactional messages: refer [to this section](../../message-center/using/transactional-messaging-architecture.md).
* Configure tracking and mirror page URLs per brand. For transactional messages, refer [to this section](../../message-center/using/configuring-multibranding.md).
* Install the client console: refer [to this section](../../installation/using/installing-the-client-console.md).
* Install built-in packages: refer [to this section](../../installation/using/installing-campaign-standard-packages.md).
* Deliverability: configure [MX rules](../../installation/using/email-deliverability.md#mx-configuration) and [email formats](../../installation/using/email-deliverability.md#managing-email-formats). Learn more on the deliverability tools and best practices by reading the [getting started guide](../../delivery/using/deliverability-key-points.md) and [detailed documentation](../../delivery/using/about-deliverability.md).
* Configure Campaign options: refer [to this section](../../installation/using/configuring-campaign-options.md).
* Configure an external database (Federated Data Access): refer [to this section](../../installation/using/about-fda.md).
* Configuring CRM connectors: refer [to this section](../../platform/using/crm-connectors.md).
* To learn more on mid-sourcing deployment principles, refer [to this section](../../installation/using/mid-sourcing-deployment.md).



## On-premise

  Adobe Campaign can be deployed on-premise: all components of Adobe Campaign, including the user interface, execution management engine and database reside on-site in the customer's data center. In this deployment model, the customer manages all software and hardware updates and upgrades, and a dedicated database administrator needs to perform maintenance and optimization tasks to ensure Campaign instance management. 

  ![](assets/deployment_onpremise.png)

As an on-premise customer, before starting deploying Campaign Classic, take care of the following prerequisites and recommentations.

* Refer to the [Adobe Campaign Classic Compatibility matrix](../../rn/using/compatibility-matrix.md) which lists all versions of the systems and components supported for Adobe Campaign.

  >[!NOTE]
  >
  >This matrix is updated regularly for the latest build of Adobe Campaign. We therefore recommend you systematically check compatibility before implementing or migrating your systems and components.

* Depending on your environment, read out the [prerequisites for Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) and [prerequisites for Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) installations.
* Learn recommendations related to database engines [in this section](../../installation/using/database.md).
* Check the required database access layers are installed on the server and accessible from the Adobe Campaign account. For more information, refer to [this section](../../installation/using/application-server.md).
* Configure your networks as certain processes of the application need to communicate with others or to access the LAN and internet. This means that some TCP ports need to be open for these processes. Refer to [this section](../../installation/using/network-configuration.md) to learn more about Network configuration requirements.
* Read out Campaign Security and Privacy checklist [in this article](https://helpx.adobe.com/campaign/kb/acc-security.html).
* Check general guidelines for estimating hardware requirements for on-premis deployment [in this article](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html).

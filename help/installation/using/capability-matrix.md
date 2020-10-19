---
title: Campaign On-premise, Hybrid and Hosted capability matrix
description: Learn main differences between hosted and on-premise deployments
page-status-flag: never-activated
uuid: d1c786a1-2691-4966-9108-059004050464
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 582f7ac6-cebe-4b47-8730-bbc16fd6b1bd
---

# Capability matrix per hosting model {#capability-matrix}

Adobe Campaign Classic comes with a set of modules and options. The availability of these modules and their use can depend on the type of deployment of your installation. This article shares some details about the main differences for certain features between fully hosted (Managed Services) and on-premise deployments.

This page shows the main differences between hosted (Managed Services) and on-premise deployments. Hybrid deployments specificities depend on the elements hosted by Adobe and hosted in your premises.

The different hosting models are introduced [in this section](../../installation/using/hosting-models.md).

## Capability matrix

| Capability                                    | Hosted | Hybrid    | On-premise    | Details                                                                                                                                                                                                              |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configure Campaign server                   | On-demand        | Available | Available     | The [server configuration file](../../installation/using/the-server-configuration-file.md) can only be modified by Adobe for hosted customers. |
| Email BCC                              | On-demand        | On-demand | Available     | For hosted and hybrid architectures, contact your account executive to activate email BCC. For on-premise installations, follow the guidelines from documentation. [Learn more](../../installation/using/email-archiving.md)                                       |
| Manage Message Center execution instance    | On-demand        | On-demand | Available     | For hosted deployments, certain settings, such as creating users on execution instance, can only be performed by Adobe. [Learn more](../../message-center/using/about-transactional-messaging.md)                                                                            |
| Managing Mid-sourcing platform                | On-demand        | On-demand | Available     | Mid-sourcing platforms hosted by Adobe can only be configured by Adobe.                                                                                                                                               |
| Inbox rendering via Litmus                    | On-demand        | On-demand | Available     | You need a Litmus account. You need to reach out to Adobe to get the necessary details or perform the Inbox rendering configuration. [Learn more](../../delivery/using/inbox-rendering.md)                                              |
| Integrating with IMS (Adobe ID)               | On-demand        | On-demand | On-demand     | IMS provisioning is performed by Adobe. This integration is a prerequisite for Adobe Experience Cloud integrations. [Learn more](../../integrations/using/about-adobe-id.md)                    |
| Encrypting/Decrypting data for file transfers | On-demand        | Available | Available     | Enabling file pre- or post-processing requires installing the necessary utility on the Adobe Campaign server. Hosted customers can use Campaign Control Panel. [Learn more](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)                                                                                 |
| Zipping/Unzipping files                       | On-demand        | Available | Available     | Enabling file pre- or post-processing requires installing the necessary utility on the Adobe Campaign server. Hosted customers can use Campaign Control Panel. [Learn more](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)                                                                                      |
| Domain Name Delegation                        | On-demand        | On-demand | Not available | [Learn more](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)                                                                                                                                                                                                                      |
| Installing SpamAssassin                       | On-demand        | Available | Available     | Installing SpamAssassin requires editing the server configuration file. [Learn more](../../delivery/using/spamassassin.md)                                                                                                                                               |
| Accessing deliverability reports              | Available        | On-demand | Available     | In certain cases of hybrid deployments, deliverability reports cannot be accessed from the marketing instance.                                                                                                        |
| Configuring LDAP authentication               | Not Available    | Available | Available     | The LDAP configuration is only possible for on-premise or hybrid installations. [Learn more](../../installation/using/connecting-through-ldap.md)                                                                                                                                 
                                                                                      |
## Federated Data Access

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data. [Learn more](../../platform/using/about-fda.md)

>[!CAUTION]
>
>Accessing an external database via FDA is only possible for on-premise or hybrid installations, except with the [Snowflake connector](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).


**See also**

* [Compatibility matrix](../../rn/using/compatibility-matrix.md)
* [Release notes](../../rn/using/latest-release.md)
* [Campaign Classic upgrades](../../rn/using/rn-overview.md)
* [Deprecated and removed features](../../rn/using/deprecated-features.md)
* [Gold Standard releases](../../rn/using/gold-standard.md)
* [Gold Standard program](https://helpx.adobe.com/campaign/kb/gold-standard.html).

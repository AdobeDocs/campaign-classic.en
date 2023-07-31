---
product: campaign
title: Campaign On-premise, Hybrid and Hosted capability matrix
description: Learn main differences between hosted and on-premise deployments
feature: Installation, Architecture
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
---
# Capability matrix per model{#capability-matrix-per-model}



Adobe Campaign Classic comes with a set of modules and options. The availability of these modules and their use can depend on the type of deployment of your installation. This article shares some details about the main differences for certain features between fully hosted (Managed Services) and on-premise deployments.

This page shows the main differences between hosted (Managed Services) and on-premise deployments. Hybrid deployments specificities depend on the elements hosted by Adobe and hosted in your premises.

The different hosting models are introduced [in this section](../../installation/using/hosting-models.md).

## Availability per deployment model {#capability-matrix}

| Capability | Hosted | Hybrid | On-premise |  Details                                                                                                                                                                                                              |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configure Campaign server | On-demand | Available | Available | [Learn more](../../installation/using/the-server-configuration-file.md) |
| Email BCC | On-demand | On-demand | Available |  [Learn more](../../installation/using/email-archiving.md)|
| Manage Message Center execution instance | On-demand | On-demand | Available | [Learn more](../../message-center/using/about-transactional-messaging.md) | 
| Managing Mid-sourcing platform | On-demand | On-demand | Available | [Learn more](../../installation/using/mid-sourcing-server.md) |
| Inbox rendering via Litmus | On-demand | On-demand | Available | [Learn more](../../delivery/using/inbox-rendering.md) |
| Integrating with IMS (Adobe ID) | On-demand | On-demand | On-demand | [Learn more](../../integrations/using/about-adobe-id.md)                    |
| Encrypting/Decrypting data for file transfers | On-demand | Available | Available | [Learn more](../../platform/using/unzip-decrypt.md) |
| Zipping/Unzipping files | On-demand | Available | Available | [Learn more](../../platform/using/unzip-decrypt.md) |
| Domain Name Delegation | On-demand | On-demand | Not available | [Learn more](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html) |
| Installing SpamAssassin | On-demand | Available | Available | [Learn more](../../delivery/using/spamassassin.md) |
| Accessing deliverability reports | Available | On-demand | Available | [Learn more](../../delivery/using/monitoring-deliverability.md)|
| Configuring LDAP authentication | Not Available | Available | Available | [Learn more](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data. [Learn more](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Compatible external database systems depend on your hosting model. Learn more in [Campaign Compatibility Matrix](../../rn/using/compatibility-matrix.md).
>

**See also**

* [Compatibility matrix](../../rn/using/compatibility-matrix.md)
* [Release notes](../../rn/using/latest-release.md)
* [Campaign Classic upgrades](../../rn/using/rn-overview.md)
* [Deprecated and removed features](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard] releases](../../rn/using/gold-standard.md)

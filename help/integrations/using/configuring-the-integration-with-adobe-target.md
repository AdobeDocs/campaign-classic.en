---
product: campaign
title: Configure the integration with Adobe Target
description: Learn how to configure the integration with Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
---
# Configure the integration with Adobe Target{#configuring-the-integration-with-adobe-target}

![](../../assets/v7-only.svg)


>[!CAUTION]
>
> As a hosted or hybrid customer, reach out to your Adobe representative to configure this integration. Steps below apply to on-premise customers only.

This integration requires:

* Adobe Experience Cloud and Adobe Target organizations
* An Adobe Target rawbox specified to establish the connection with Adobe Campaign

To configure this integration in Adobe Campaign, follow the steps below:

1. Install the **[!UICONTROL Integration with the Adobe Experience Cloud]** built-in package. [Learn more](../../platform/using/working-with-data-packages.md#importing-packages)
    
    This package gives you access to the shared assets via Digital Asset Manager.

1. Enable connection via IMS (Adobe ID connection service) to use images shared via Adobe Experience Cloud in your emails. [Learn more](../../integrations/using/about-adobe-id.md)
1. Browse to **[!UICONTROL Administration > Platform > Options]** to configure the server and organization (Tenant) options for Adobe Target:

   ![](assets/tar_options.png)

    * **[!UICONTROL TNT_EdgeServer]** : Adobe Target server used for the integration. This option is already selected by default. This value corresponds to the Adobe Target **[!UICONTROL Domain Server]**, followed by the value **/m2**. For example: **tt.omtrdc.net/m2**.
    * **[!UICONTROL TNT_TenantName]** : Adobe Target Organization name. This value corresponds to the name of the Adobe Target **[!UICONTROL Client]**.


>[!CAUTION]
>
>For hybrid and hosted architectures, these options must be set on all servers, including the [mid-sourcing server](../../installation/using/mid-sourcing-server.md) and the [execution instance](../../message-center/using/configuring-instances.md#execution-instance).
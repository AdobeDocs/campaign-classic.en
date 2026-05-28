---
product: campaign
title: Configure the integration with Adobe Target
description: Learn how to configure the integration with Adobe Target
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
TQID: https://experienceleague.adobe.com/k6TljRgymSefOITPaogJdR7HOrl1BnnZm9jbkemrcyg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Adobe Analytics integration (Campaign)
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Adobe Experience Manager integration (Campaign)
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Adobe Experience Platform integration (Campaign)
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Adobe Target integration (Campaign)
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Configure the integration with Adobe Target{#configuring-the-integration-with-adobe-target}




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
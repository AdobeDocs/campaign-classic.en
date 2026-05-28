---
product: campaign
title: Sharing audiences with Adobe Experience Cloud
description: Sharing audiences with Adobe Experience Cloud
feature: Audiences
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
TQID: https://experienceleague.adobe.com/MGzMyGtmzaVGZy6oWHcirPPdSSpu9YYcuR30KIVZ9bc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
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
---
# Sharing audiences with Adobe Experience Cloud {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>To share audiences with Adobe Experience Cloud solutions, you need to implement Adobe Identity Management System. [Learn more about IMS](../../integrations/using/about-adobe-id.md).

With Adobe Campaign, you can share audiences and segments with Adobe Experience Cloud services. Two options are available:

1. Send Adobe Experience Platform segment data to Adobe Campaign. To implement this integration, you need to connect your Real-Time Customer Data Platform to Campaign (RTCDP). [Learn more in this section](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html){target="_blank"}.

1. Integrate **Adobe Campaign** with  **Experience Cloud Audiences** or **Adobe Audience Manager**. You will then be able to:

    * Import shared audiences/segments from different Adobe Experience Cloud solutions into Adobe Campaign. Audiences can be imported via lists in Adobe Campaign.

    * Export lists in the form of Adobe Experience Cloud shared audiences. These audiences can be used in the different Adobe Experience Cloud solutions that you use. Audiences can be exported after targeting in a workflow, using a dedicated **[!UICONTROL Update shared audience]** activity.

This integration supports two types of Adobe Experience Cloud IDs:

* **Visitor ID**: this type of identifier reconciles Adobe Experience Cloud visitors with Adobe Campaign recipients.
* **Declared ID**: this type of identifier reconciles all types of data with elements from the Adobe Campaign database. It is represented in Adobe Campaign as a predefined reconciliation key.

    >[!NOTE]
    >
    > Declared ID data source can now also be used with Experience Cloud Assets integration.
    >

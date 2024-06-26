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

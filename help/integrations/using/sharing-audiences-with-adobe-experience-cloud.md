---
solution: Campaign Classic
product: campaign
title: Sharing audiences with Adobe Experience Cloud
description: Sharing audiences with Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
---

# Share audiences with Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>To share audiences with Adobe Experience Cloud solutions, you need to implement Adobe Identity Management System. [Learn more about IMS](../../integrations/using/about-adobe-id.md).

With Adobe Campaign, you can share audiences and segments with Adobe Experience Cloud solutions and core services. Two options are available:

1. Send Adobe Experience Platform segment data to Adobe Campaign. To implement this integration, you need to connect your Real-Time Customer Data Platform to Campaign (RTCDP). [Learn more in this section](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integrate **Adobe Campaign** with **People core service** (also known as **Profiles & Audiences core service**) or Adobe Audience Manager. You will then be able to:

    * Import shared audiences/segments from different Adobe Experience Cloud solutions into Adobe Campaign. Audiences can be imported via lists in Adobe Campaign.

    * Export lists in the form of Adobe Experience Cloud shared audiences. These audiences can be used in the different Adobe Experience Cloud solutions that you use. Audiences can be exported after targeting in a workflow, using a dedicated **[!UICONTROL Update shared audience]** activity.

This integration supports two types of Adobe Experience Cloud IDs:

* **Visitor ID**: this type of identifier reconciliates Adobe Experience Cloud visitors with Adobe Campaign recipients.
* **Declared ID**: this type of identifier reconciliates all types of data with elements from the Adobe Campaign database. It is represented in Adobe Campaign as a predefined reconciliation key.

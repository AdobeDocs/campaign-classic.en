---
title: Sharing audiences with Adobe Experience Cloud
seo-title: Sharing audiences with Adobe Experience Cloud
description: Sharing audiences with Adobe Experience Cloud
seo-description: 
page-status-flag: never-activated
uuid: 6a026dd8-83f5-4da6-bba8-3a55a03e9324
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 145461c0-8c5c-44bb-9b37-84bff6dec00b
index: y
internal: n
snippet: y
---

# Sharing audiences with Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>Using this integration requires having IMS implemented. Consult the section about [IMS](../../integrations/using/about-adobe-id.md).

Adobe Campaign allows you to exchange and share audiences/segments with Adobe Experience Cloud solutions and core services. To do this, you need to integrate **Adobe Campaign** with **People core service** (also known as **Profiles & Audiences core service**) or Adobe Audience Manager. You will then be able to:

* Import shared audiences/segments from different Adobe Experience Cloud solutions into Adobe Campaign. Audiences can be imported via lists in Adobe Campaign.
* Export lists in the form of Adobe Experience Cloud shared audiences. These audiences can be used in the different Adobe Experience Cloud solutions that you use. Audiences can be exported after targeting in a workflow, using a dedicated **Update shared audience** activity.

>[!CAUTION]
>
>Depending on the type of data, importing audiences in Adobe Campaign may be subject to legal restrictions.

The integration supports two types of Adobe Experience Cloud IDs:

* **Visitor ID**: this type of identifier reconciliates Adobe Experience Cloud visitors with Adobe Campaign recipients.
* **Declared ID**: this type of identifier reconciliates all types of data with elements from the Adobe Campaign database. It is represented in Adobe Campaign as a predefined reconciliation key.


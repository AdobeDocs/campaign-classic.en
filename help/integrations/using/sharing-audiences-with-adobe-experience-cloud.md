---
title: Sharing audiences with Adobe Experience Cloud
seo-title: Sharing audiences with Adobe Experience Cloud
description: Sharing audiences with Adobe Experience Cloud
seo-description: 
page-status-flag: never-activated
uuid: 0686f414-bd50-4773-946c-22faac7391b1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: a644577f-6dbb-469c-9498-1b6f9c3a56a2
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


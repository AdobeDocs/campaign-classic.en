---
product: campaign
title: Get started with Sources and Destinations
description: Learn more about Adobe Experience Platform Sources and Destinations
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
TQID: https://experienceleague.adobe.com/xPpBR6NrQ315FIw1beLnw4c0gyLzEoYWzIXDljDg9H4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0
    internal-label: Triggers
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Experience Platform integration
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
---
# Work with Sources and Destinations {#rtcdp}



## About Sources and Destinations

With Adobe Experience Platform, you can share data between Campaign Classic and Adobe Real-time Customer Data Platform (RTCDP). This allows you to target Adobe Experience Platform audiences in your Campaign workflows, then send back to Adobe Real-time Customer Data Platform data related to these audiences like sends, opens, and clicks.

* With **Destinations**, ingest audiences from Adobe Experience Platform into Campaign Classic. This allows you to activate your known and unknown data for your marketing campaigns.
* With **Sources**, export Campaign Classic data (e.g. sends, opens, clicks) into Adobe Experience Platform. This allows you to centralize data you collect from disparate sources into one single place, and use the insights gained from it to do more.

>[!IMPORTANT]
>
>Please keep in mind the SFTP storage limits, database storage limits, and active profile limits as per your Adobe Campaign contract while performing this integration.

For a more detailed overview of Adobe Real-time Customer Data Platform, Destinations and Sources, refer to these pages:

* [Adobe Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
* [Destinations documentation](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html)
* [Sources documentation](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

## Connect Campaign Classic with Adobe Experience Platform

To be able to share data between Adobe Experience Platform and Campaign Classic, you first need to connect Adobe Campaign as a **Destination**, and connect your AWS S3 or Azure blob storage location as a **Source** in Adobe experience Platform.

Once the connectors have been configured, you can set up a data import or export into Campaign Classic using workflows.

![](assets/rtcdp-schema.png) 

For more details on how to setup these import and export processes, refer to these sections:

* [Ingest Adobe Experience Platform segments into Campaign](../../integrations/using/ingest-aep-data.md)
* [Export data from Campaign to Adobe Experience Platform](../../integrations/using/export-campaign-data.md)

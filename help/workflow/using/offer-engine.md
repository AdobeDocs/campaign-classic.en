---
title: Offer engine
seo-title: Offer engine
description: Offer engine
seo-description: 
page-status-flag: never-activated
uuid: 6f2f57f8-7df8-437d-b7cf-7d8b2eb4cb49
contentOwner: sauviat
topic-tags: targeting-activities
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 9cdf0aa1-b242-4e72-98fe-732a6c5ad62f
index: y
internal: n
snippet: y
---

# Offer engine{#offer-engine}

The **Offer engine** activity lets you define a call to the offer engine prior to a delivery.

This activity works on the same principle as the enrichment activity with an engine call, by enriching the inbound population data with an offer calculated by the engine, before a delivery.

![](assets/int_offerengine_activity2.png)

After configuring your query (refer to this [section](../../workflow/using/query.md)):

1. Add and open an **Offer engine** activity.
1. Complete the various available fields to specify the call to offer engine parameters (offer space, category or theme(s), contact date, number of offers to keep). The engine will automatically calculate the offer(s) to add according to these parameters.

   >[!CAUTION]
   >
   >If you use this activity, only the offer propositions used in the delivery will be stored.

   ![](assets/int_offerengine_activity1.png)

1. Then configure a delivery activity that corresponds to your chosen channel. Refer to [Cross-channel deliveries](../../workflow/using/cross-channel-deliveries.md).


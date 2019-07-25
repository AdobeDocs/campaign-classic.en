---
title: Offers by cell
seo-title: Offers by cell
description: Offers by cell
seo-description: 
page-status-flag: never-activated
uuid: 78af5ab2-d684-42b8-affe-738e51a781a2
contentOwner: sauviat
topic-tags: targeting-activities
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 127407bc-a88e-45cb-a6fd-3860facda7ba
index: y
internal: n
snippet: y
---

# Offers by cell{#offers-by-cell}

The **Offers by cell** activity lets you distribute the inbound population (from a query for example) into several segments and to specify an offer to present for each of these segments.

This activity can only be used with **Interaction**. For more information, refer to this [section](../../interaction/using/about-outbound-channels.md).

To do this:

1. Add the **Offers by cell** activity once you have specified the target population, then open it.
1. In the **General** tab, select the offer space on which you want to present the offers.
1. In the **Cells** tab, specify the different sub-sets using the **Add** button:

    * Specify the subset population using the available filtering and limiting rules.
    * Next, select the offer that you want to present to the sub-set. The available offers are those that are eligible on the offer space that was selected at the previous step.
    
      ![](assets/int_offer_per_cell1.png)

1. Then configure a delivery activity that corresponds to your chosen channel. Refer to [Cross-channel deliveries](../../workflow/using/cross-channel-deliveries.md).


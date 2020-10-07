---
title: Offers by cell
seo-title: Offers by cell
description: Offers by cell
seo-description: 
page-status-flag: never-activated
uuid: 731bfdde-abd2-400e-9e22-3dbaad37c5b9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: d90594bb-e3ba-4fb1-9e11-83d519c1ca7d
---

# Offers by cell{#offers-by-cell}

The **[!UICONTROL Offers by cell]** activity lets you distribute the inbound population (from a query for example) into several segments and to specify an offer to present for each of these segments.

This activity can only be used with **Interaction**. For more information, refer to this [section](../../interaction/using/about-outbound-channels.md).

To do this:

1. Add the **[!UICONTROL Offers by cell]** activity once you have specified the target population, then open it.
1. In the **[!UICONTROL General]** tab, select the offer space on which you want to present the offers.
1. In the **[!UICONTROL Cells]** tab, specify the different sub-sets using the **[!UICONTROL Add]** button:

    * Specify the subset population using the available filtering and limiting rules.
    * Next, select the offer that you want to present to the sub-set. The available offers are those that are eligible on the offer space that was selected at the previous step.
    
      ![](assets/int_offer_per_cell1.png)

1. Then configure a delivery activity that corresponds to your chosen channel. Refer to [Cross-channel deliveries](../../workflow/using/cross-channel-deliveries.md).


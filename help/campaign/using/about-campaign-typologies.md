---
solution: Campaign Classic
product: campaign
title: About campaign typologies
description: About campaign typologies
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
---
# About campaign typologies{#about-campaign-typologies}

Campaign Optimization is the Adobe Campaign module which lets you control, filter and monitor the sending of deliveries. To avoid conflicts between campaigns, Adobe Campaign can test various combinations by applying specific constraint rules. This guarantees that the messages sent meet the needs and expectations of customers and company communication policies.

![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](#typologies-video)

>[!NOTE]
>
>Depending on your offering, Campaign Optimization can be included or an add-on. Please check your license agreement.

## Typology rules {#typology-rules}

With Adobe Campaign you can design and apply four types of typology rules:

* **Filtering** rules which let you exclude part of the target based on criteria. For more on this, refer to [Filtering rules](../../campaign/using/filtering-rules.md).
* **Pressure** rules which let you control marketing fatigue. For more on this, refer to [Pressure rules](../../campaign/using/pressure-rules.md).
* **Capacity** rules which let you limit loads to guarantee optimal processing conditions. For more on this, refer to [Controlling capacity](../../campaign/using/consistency-rules.md#controlling-capacity).
* **Control** rules which let you check the validity of messages before they are sent. For more on this, refer to [Control rules](../../campaign/using/control-rules.md).

Once they have been created, typology rules are grouped in campaign typologies which are referenced in deliveries. See [Applying typologies](#applying-typologies).

## Typologies {#typologies}

A campaign typology can contain several [typology rules](#typology-rules), but a delivery can only reference one typology.

The **[!UICONTROL Rules]** tab lets you add, delete or view the typology rules to apply.

![](assets/campaign_opt_rules_tab.png)

## Applying typologies {#applying-typologies}

Steps to create and apply a typology to your deliveries are listed below:

1. Create typology rules.

   Typology rules are found in the **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** node.

   Different rules available in Campaign are described in the following sections: [sales pressure rules](../../campaign/using/pressure-rules.md), [capacity rules](../../campaign/using/consistency-rules.md#controlling-capacity), [control rules](../../campaign/using/control-rules.md) and [filtering rules](../../campaign/using/filtering-rules.md).

1. Create a typology and reference the rules you created into it.

   Typologies are accessed via the **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** node. 

1. Configure your delivery to use the typology you created. For more on this, refer to [this section](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Test and control the behavior through campaign simulations. For more on campaign simulations, refer to [this section](../../campaign/using/campaign-simulations.md).

During delivery preparation, recipients are excluded when criterion is met. You can check logs to monitor exclusions. Sample use cases on pressure typology rules are available in [this page](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

## Tutorial videos {#typologies-video}

### How to set up fatigue management using typology rules

This video explains how to implement fatigue management in Adobe Campaign by leveraging typology rules.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### How to set up fatigue management using predefined filters

Fatigue management controls frequency and quantity of messaging to avoid over-solicitation of recipients. If you do not have the campaign optimization module in your campaign instance, you may configure a predefined filter that will filter the target population by the number of messages received
This video explains how to implement fatigue management in Adobe Campaign Classic by using filters.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Additional Campaign how-to videos are available [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).

**Related topic**

* [Apply automatic business rules to deliveries on any channel](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [About campaign typologies](../../campaign/using/pressure-rules.md)

* [Managing marketing fatigue with pressure rules](https://docs.adobe.com/content/help/en/campaign-classic/using/orchestrating-campaigns/campaign-optimization/pressure-rules.html)

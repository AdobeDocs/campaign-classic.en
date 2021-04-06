---
solution: Campaign Classic
product: campaign
title: Recurring delivery
description: Learn more about the Recurring delivery workflow activity
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
---
# Recurring delivery{#recurring-delivery}

A **[!UICONTROL Recurring delivery]** activity lets you configure a delivery template occurrence that is specific to a campaign.

![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](#recurring-delivery-video)

This activity is only available from the **[!UICONTROL Targeting and workflows]** tab found in a campaign.

To do this:

1. Select the delivery template that the activity will be based on.

   ![](assets/recurring_delivery_001.png)

1. Configure the delivery template.

The configuration process for this activity is similar to that of creating a delivery template in terms of the options available. For more on this, refer to this [section](../../delivery/using/about-templates.md).

For an example of this activity being used, refer to this [section](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## How to set up recurring delivery

A **recurring delivery** will create a new delivery instance each time it executes. For example, if the workflow is scheduled to run once a week, that would result in 52 Deliveries after one year. This also means that the broad log and tracking logs will be separated by each delivery instance.

![Recurring Delivery](assets/delivery_recurring.jpg)

>[!NOTE]
>
>It is not possible to send a proof from a **[!UICONTROL Recurring delivery]** type activity.   
>To directly create a delivery via a campaign workflow, use the channel specific activities that are preconfigured (e.g. **[!UICONTROL Email delivery]**).

## Tutorial video (#recurring-delivery-video)

This video explains how to configure a recurring delivery and a scheduler activity.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

Additional Campaign Classic how-to videos are available [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).

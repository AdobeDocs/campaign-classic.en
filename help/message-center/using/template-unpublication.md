---
title: Template publication
seo-title: Template publication
description: Template publication
seo-description: 
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
index: y
internal: n
snippet: y
---

# Template unpublication{#template-unpublication}

Once a message template is published on the execution instances, it can be unpublished.

Indeed, a published template can still be called. Therefore, if you are no longer using a message template, it is recommended to unpublish it. This is to avoid sending an unwanted transactional message by mistake.

For example, you published a message template that you only use for Christmas campaigns. You may want to unpublish it after the Christmas period is over, and publish it again next year.

To unpublish a transactional message template, follow the steps below.

1. In the control instance, go to the **[!UICONTROL Message Center > Transactional message templates]** folder of the tree.
1. Select the template you want to unpublish from your execution instances.
1. Click **[!UICONTROL Unpublish]**.
1. Fill in the **[!UICONTROL Log of the process]** field.///
1. Click **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

The transactional message template status changes from **[!UICONTROL Published]** to **[!UICONTROL Unpublished]**.///

Once unpublication is complete:

* Both message templates (applied to batch and real-time type events) are updated in each execution instance, in the **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** folder. Their status changes from **[!UICONTROL In production]** to **[!UICONTROL Unpublished]**.///

* Once a template is unpublished, you can delete it from the control instance if needed. To do so, select it from the list and click the **[!UICONTROL Delete]** button on top right of the screen.///
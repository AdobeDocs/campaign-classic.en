---
title: Delivery control
seo-title: Delivery control
description: Delivery control
seo-description: 
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
index: y
internal: n
snippet: y
---

# Delivery control{#delivery-control}

A **Delivery control**-type action lets you start, pause, or stop a delivery.

This can be the delivery specified in the transition, a delivery selected explicitly, or a delivery calculated by a script. For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

If you select **[!UICONTROL Start]** , the activity will perform all the steps required to start the delivery (target calculation, content preparation, delivery). If some of these steps have already been performed by a previous workflow activity they won't be performed again. For instance, if the target estimation was already performed by a **[!UICONTROL Delivery]** type activity (refer to [Delivery](../../workflow/using/delivery.md)), the **[!UICONTROL Act on the delivery]** activity will launch the remaining steps (content preparation and delivery).

The following options are available:

* **[!UICONTROL Generate an outbound transition]**

  Creates an outbound transition that will be activated at the end of execution. You can choose whether or not to retrieve the target of the outbound delivery.

* **[!UICONTROL Processing errors]**

  Refer to [Processing errors](../../workflow/using/executing-a-workflow.md#processing-errors).

## Input parameters {#input-parameters}

* deliveryId

Delivery identifier, if the selected action is **[!UICONTROL Specified in the transition]** .

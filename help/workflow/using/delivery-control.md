---
title: Delivery control
seo-title: Delivery control
description: Delivery control
seo-description: 
page-status-flag: never-activated
uuid: 790d9258-5c41-4705-bcba-2ed8c98dfb9d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: d847b7bd-7f93-46b0-bab2-a8bed3202eb6
index: y
internal: n
snippet: y
---

# Delivery control{#delivery-control}

A **Delivery control**-type action lets you start, pause, or stop a delivery.

This can be the delivery specified in the transition, a delivery selected explicitly, or a delivery calculated by a script. For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

If you select **Start**, the activity will perform all the steps required to start the delivery (target calculation, content preparation, delivery). If some of these steps have already been performed by a previous workflow activity they won't be performed again. For instance, if the target estimation was already performed by a **Delivery** type activity (refer to [Delivery](../../workflow/using/delivery.md)), the **Act on the delivery** activity will launch the remaining steps (content preparation and delivery).

The following options are available:

* **Generate an outbound transition**

  Creates an outbound transition that will be activated at the end of execution. You can choose whether or not to retrieve the target of the outbound delivery.

* **Processing errors**

  Refer to [Processing errors](../../workflow/using/delivery-control.md#processing-errors).

## Input parameters {#input-parameters}

* deliveryId

Delivery identifier, if the selected action is **Specified in the transition**.

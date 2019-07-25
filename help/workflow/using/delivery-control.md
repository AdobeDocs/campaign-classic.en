---
title: Delivery control
seo-title: Delivery control
description: Delivery control
seo-description: 
page-status-flag: never-activated
uuid: fbf32368-437a-4251-adf5-e5d493c65df8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 515e3da9-afc3-4dab-8d4a-61471b943d1e
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

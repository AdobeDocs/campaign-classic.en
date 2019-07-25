---
title: External signal
seo-title: External signal
description: External signal
seo-description: 
page-status-flag: never-activated
uuid: b9e4b66f-7a26-4fd0-b25c-42a61f8ca4d4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 575ebcfd-e46a-4e4d-8938-c646e951b6ea
index: y
internal: n
snippet: y
---

# External signal{#external-signal}

The **External signal** activity lets you trigger execution of a set of tasks in a workflow to a schedule.

When an 'External signal' task is activated, it is paused indefinitely or until the end of the specified time period. Its transition is activated by the SOAP call **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** The **complete** parameter allows the task to be finished, so it will not react to subsequent calls.

Refer to the online documentation concerning SOAP calls for further information on the PostEvent function.

You can configure this activity in order to define events if no signal is received. To do this, edit the activity and click the **Expiration** tab. Click the **Insert** button to create and configure an event.

![](assets/edit_signal.png)

The configuration of expirations is detailed in [Expirations](../../workflow/using/external-signal.md#expirations).

The **Delay** field lets you specify an expiration delay in the units of your choice. See [Wait](../../workflow/using/wait.md).

Each line represents a type of expiration and coincides with a transition.

![](assets/external_sign_diag.png)


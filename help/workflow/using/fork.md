---
solution: Campaign Classic
product: campaign
title: Fork
description: Learn more about the Fork workflow activity
audience: workflow
content-type: reference
topic-tags: flow-control-activities
---

# Fork{#fork}

The **[!UICONTROL Fork]** activity allows you to create multiple outbound transitions, in order to carry out several activities independently within the same workflow.

For example, you can use the activity after a query, in order to perform two actions in parallel:

* Save the result of the query into an audience,
* Execute a segmentation on the result in order to send multiple deliveries.

You can also use the activity in the context of content creation and delivery sending automation, in order to launch the target calculation and the content creation in parallel. A dedicated use case is available in [this section](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!IMPORTANT]
>
>Keep in mind that the outbound transitions added after a Fork activity will not execute simultaneously.
>
>The activity should therefore not be used in order to improve the workflow's performances, but rather to execute multiple activities independentely, and eventually join them together before executing the rest of the worklow.

To configure the activity, open it then define the number and label of the desired outbound transitions.

![](assets/s_user_segmentation_fork.png)

You can then configure each outbound transitions, then join them together using an [AND-join](../../workflow/using/and-join.md) activity, if necessary. This way, the rest of the workflow will execute only once the **[!UICONTROL Fork]** activity's outbound transitions have finished.

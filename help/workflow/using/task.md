---
product: campaign
title: Task
description: Learn more about the Task workflow activity
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 8549bf8c-ba23-44cb-95f2-c50f2d0f5479
---
# Task{#task}

>[!AVAILABILITY]
>
>:warning: This capability is only available in Campaign Classic v7. [Learn more](../../mrm/using/creating-and-managing-tasks.md)

In a campaign workflow, the **[!UICONTROL Task]** activity lets you specify two scenarios: the first if the task is completed and a second if the task is not completed (if it is manually marked as incomplete or if it expires).

![](assets/mrm_task_in_workflow.png)

How to configure and operate a task is detailed in [Campaign Classic v7 documentation](../../mrm/using/creating-and-managing-tasks.md).

![](assets/wkf_task_activity.png)

The **[!UICONTROL Resources]** option lets you define several operators as well as an approval schedule for the task. If the person approving rejects, this does not lead to the task itself being rejected.

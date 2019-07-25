---
title: Start and end
seo-title: Start and end
description: Start and end
seo-description: 
page-status-flag: never-activated
uuid: e4378d97-c3a9-4f7e-bd8e-53912e08daf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: bb68e46e-aa59-415c-bf0d-5dc6ba6d9c93
index: y
internal: n
snippet: y
---

# Start and end{#start-and-end}

The **Start** and **End** activities allow you to graphically mark the start and end of a workflow. These activities have no functional impact and are therefore optional.

* **Start**

  Executing a workflow starts with activities without an inbound transition and Start-type activities.

  ![](assets/s_user_segmentation_start_stop.png)

* **End**

  You can configure the **End** activity to interrupt all tasks that are in progress. To do this, double-click the activity to display its properties, and check the appropriate option.

  ![](assets/s_user_segmentation_end.png)

  The data in the worktable is deleted automatically when the end activity is enabled. If this isn't necessary, and to avoid unnecessary loads, you can choose to disable the transition at the last activity output. For example, at a delivery output, if no process is scheduled, uncheck the relevant option as shown below:

  ![](assets/s_advuser_delivery_option_no_output.png)


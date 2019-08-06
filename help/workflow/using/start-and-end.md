---
title: Start and end
seo-title: Start and end
description: Start and end
seo-description: 
page-status-flag: never-activated
uuid: 23411a0d-74ce-4238-a5de-e8a47f24b3e6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: fc58247c-2d88-4225-bf54-6b40bed507d0
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


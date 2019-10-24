---
title: Key steps when creating a delivery
seo-title: Key steps when creating a delivery
description: Key steps when creating a delivery
seo-description: 
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
---

# Analysis priority {#analysis-priority-}


When the delivery is part of a campaign, the **[!UICONTROL Advanced]** tab offers an additional option. This lets you organize the processing order for deliveries in the same campaign. 


Before sending, each delivery is analyzed. The analysis duration depends on the delivery extraction file. The more significant the size of the file, the longer the analysis takes, making the following deliveries wait.

The options for the **[!UICONTROL Message preparation by the scheduler]** let you prioritize the delivery analysis in a campaign workflow.

![](assets/delivery_analysis_priority.png)

If a delivery is too large, it is better to assign a low priority to it in order to avoid slowing down the analysis of other workflow deliveries.

>[!NOTE]
>
>To ensure that the larger delivery analyses do not slow down the progress of your workflows, you can schedule their executions by ticking the **[!UICONTROL Schedule execution for a time of low activity]**.

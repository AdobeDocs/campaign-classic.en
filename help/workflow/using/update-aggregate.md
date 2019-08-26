---
title: Update aggregate
seo-title: Update aggregate
description: Update aggregate
seo-description: 
page-status-flag: never-activated
uuid: 34ae42e1-da34-43be-b219-0b3b872177b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 031f8d5d-940c-4a4c-97e7-ad4ef61983c1
index: y
internal: n
snippet: y
---

# Update aggregate{#update-aggregate}

Aggregates are defined at cube level for reporting purposes. A **[!UICONTROL Workflow]** tab is available when configuring an aggregate.

For more information on cubes and using aggregates in Adobe Campaign, refer to the dedicated [section](https://helpx.adobe.com/campaign/classic/reporting/using/concepts-and-methodology.html#calculating-and-using-aggregates).

The **[!UICONTROL Update aggregate]** activity lets you select the update mode to apply: full or partial.

By default, a full update is carried out during each calculation. To enable a partial update, select the relevant option and define the update conditions.

![](assets/s_advuser_cube_agregate_05.png)

**Good practice**: a **[!UICONTROL Scheduler]** activity can be used to specify the frequency of calculation updates.

![](assets/s_advuser_cube_agregate_04.png)


---
product: campaign
title: Update aggregate
description: Learn more about the Update aggregate workflow activity
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
---
# Update aggregate{#update-aggregate}

![](../../assets/v7-only.svg)

Aggregates are defined at cube level for reporting purposes. A **[!UICONTROL Workflow]** tab is available when configuring an aggregate.
  
Aggregates are useful when manipulating large volumes of data. They are updated automatically based on settings defined in the dedicated workflow box, to integrate the data collect most recently into the indicators

Aggregates are defined in the relevant tab of each cube.

![](assets/s_advuser_cube_agregate_01.png)


The **[!UICONTROL Update aggregate]** activity lets you select the update mode to apply: full or partial.

By default, a full update is carried out during each calculation. To enable a partial update, select the relevant option and define the update conditions.

![](assets/s_advuser_cube_agregate_05.png)

**Good practice**: a **[!UICONTROL Scheduler]** activity can be used to specify the frequency of calculation updates.

![](assets/s_advuser_cube_agregate_04.png)

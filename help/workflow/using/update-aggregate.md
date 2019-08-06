---
title: Update aggregate
seo-title: Update aggregate
description: Update aggregate
seo-description: 
page-status-flag: never-activated
uuid: c420ce39-9d85-4d8e-a20f-4535fc777b01
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: aca470c5-75d9-485e-96ed-b9e0c6f61424
index: y
internal: n
snippet: y
---

# Update aggregate{#update-aggregate}

Aggregates are defined at cube level for reporting purposes. A **Workflow** tab is available when configuring an aggregate.

For more information on cubes and using aggregates in Adobe Campaign, refer to the dedicated [section](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

The **Update aggregate** activity lets you select the update mode to apply: full or partial.

By default, a full update is carried out during each calculation. To enable a partial update, select the relevant option and define the update conditions.

![](assets/s_advuser_cube_agregate_05.png)

**Good practice**: a **Scheduler** activity can be used to specify the frequency of calculation updates.

![](assets/s_advuser_cube_agregate_04.png)


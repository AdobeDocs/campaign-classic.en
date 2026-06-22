---
product: campaign
title: Update aggregate
description: Learn more about the Update aggregate workflow activity
feature: Workflows
hide: true
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
TQID: https://experienceleague.adobe.com/YnOd1mT0WQqXHVeFUXFoumzDHxSSlKE2tgGSQFrjBzQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: Workflow HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
---
# Update aggregate{#update-aggregate}



Aggregates are defined at cube level for reporting purposes. A **[!UICONTROL Workflow]** tab is available when configuring an aggregate.
  
Aggregates are useful when manipulating large volumes of data. They are updated automatically based on settings defined in the dedicated workflow box, to integrate the data collect most recently into the indicators

Aggregates are defined in the relevant tab of each cube.

![](assets/s_advuser_cube_agregate_01.png)


The **[!UICONTROL Update aggregate]** activity lets you select the update mode to apply: full or partial.

By default, a full update is carried out during each calculation. To enable a partial update, select the relevant option and define the update conditions.

![](assets/s_advuser_cube_agregate_05.png)

**Good practice**: a **[!UICONTROL Scheduler]** activity can be used to specify the frequency of calculation updates.

![](assets/s_advuser_cube_agregate_04.png)


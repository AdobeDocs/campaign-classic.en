---
product: campaign
title: Wait
description: Learn more about the Wait workflow activity
feature: Workflows
hide: true
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
TQID: https://experienceleague.adobe.com/sQ3GwMFQnhy6eOmFSfMUwT8Z3UE0p4cHLAjr8CjS2FM
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: Workflow HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
---
# Wait{#wait}



A **Wait** activity activates its transition after a time delay of anywhere between a few seconds and several months. A wait task does not block the execution of other tasks; the workflow can execute tasks in parallel while this task is pending.

You can enter the label and wait time using the editor, as in the example below:

![](assets/edit_wait.png)

In the **[!UICONTROL Duration]** field, the value can be expressed in the unit of your choice: (according to the operator's regional settings):

* If regional settings are not specified: **s** for seconds, **m** for minutes, **h** for hours, **d** for days, **y** for years. At the time of approval, the value is automatically converted to the most readable unit.

  The default unit is the day (**d**).

* Whereas if, for example, the regional settings are set to 'Français': **s** for seconds, **mn** for minutes, **h** for hours, **j** for days, **m** for months, **a** for years. At the time of approval, the value is automatically converted to the most readable unit, as in the example above **90s** was converted to **1mn 30s**.

  The default unit is the day (**d**).


---
product: campaign
title: Edit schema
description: Learn more about the Edit schema workflow activity
feature: Workflows, Targeting Activity
hide: true
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
TQID: https://experienceleague.adobe.com/cxBDJJXifg7C4vtB5MPBYSluRpgnbsBkDiuSsnIHDYo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: Workflow HeatMap (Campaign)
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities (Campaign)
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities (Campaign)
---
# Edit schema{#edit-schema}



Data can be transformed, normalized and, if necessary, enriched in the workflow using the **[!UICONTROL Edit schema]** activity. It is generally used to normalize the data structure: you can rename the output columns or modify their content, by calculating the average values of a field or aggregate for example.

This activity does not change the data in the work table, it changes only its schema, i.e. the logical view of the data.

![](assets/wf_manipulation_box.png)

You can also create joins with other worktables, via the **[!UICONTROL Links]** tab.

![](assets/wf_manipulation_box_link_tab.png)

The lower section lets you configure the list of joining conditions, i.e. the criteria used for reconciling the data from the two tables.

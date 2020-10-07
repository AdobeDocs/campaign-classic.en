---
title: Edit schema
seo-title: Edit schema
description: Edit schema
seo-description: 
page-status-flag: never-activated
uuid: abd77902-98b7-4ab7-a240-dd6b3bb247bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 733576d2-505f-4598-89eb-a10e7331bf7e
---

# Edit schema{#edit-schema}

Data can be transformed, normalized and, if necessary, enriched in the workflow using the **[!UICONTROL Edit schema]** activity. It is generally used to normalize the data structure: you can rename the output columns or modify their content, by calculating the average values of a field or aggregate for example.

This activity does not change the data in the work table, it changes only its schema, i.e. the logical view of the data.

![](assets/wf_manipulation_box.png)

You can also create joins with other worktables, via the **[!UICONTROL Links]** tab.

![](assets/wf_manipulation_box_link_tab.png)

The lower section lets you configure the list of joining conditions, i.e. the criteria used for reconciling the data from the two tables.

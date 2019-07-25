---
title: Edit schema
seo-title: Edit schema
description: Edit schema
seo-description: 
page-status-flag: never-activated
uuid: 50b7491b-d7ff-42e2-af18-2f0bf8a0132f
contentOwner: sauviat
topic-tags: targeting-activities
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 1832fe32-75f1-4aaf-a796-226635961549
index: y
internal: n
snippet: y
---

# Edit schema{#edit-schema}

Data can be transformed, normalized and, if necessary, enriched in the workflow using the **Edit schema** activity. It is generally used to normalize the data structure: you can rename the output columns or modify their content, by calculating the average values of a field or aggregate for example.

This activity does not change the data in the work table, it changes only its schema, i.e. the logical view of the data.

![](assets/wf_manipulation_box.png)

You can also create joins with other worktables, via the **Links** tab.

![](assets/wf_manipulation_box_link_tab.png)

The lower section lets you configure the list of joining conditions, i.e. the criteria used for reconciling the data from the two tables.

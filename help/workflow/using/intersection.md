---
product: campaign
title: Intersection
description: Intersection
feature: Workflows, Targeting Activity
hide: true
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
TQID: https://experienceleague.adobe.com/mc1GRKb345bJX0ConrlwvLbPeeFK8YLDQIhs2Gp7h68
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
# Intersection{#intersection}

>[!CONTEXTUALHELP]
>id="ac_workflow_intersection"
>title="Intersection activity"
>abstract="An Intersection type activity creates a target from the intersection of the targets received. An intersection lets you extract only the population that is common to all inbound activity results."

An **Intersection**-type activity creates a target from the intersection of the targets received.

An intersection lets you extract only the population that is common to all inbound activity results. The target is created with all results received: all prior activities must therefore be finished before the intersection can be executed. To configure this activity, you need to enter a label for it as well as the options concerning the result.

![](assets/s_user_segmentation_inter.png)

For more on configuring and using the intersection activity, refer to [Extracting joint data (Intersection)](targeting-data.md#extracting-joint-data--intersection-).

Check the **[!UICONTROL Generate complement]** option if you wish to process the remaining population. The complement will contain the union of the results of all inbound activities minus the intersection. An additional outbound transition will then be added to the activity, as follows:

![](assets/s_user_segmentation_inter_compl.png)

## Intersection example {#intersection-example}

In the following example, the aim of the intersection is to calculate the recipients common to three simple queries in order to create a list.

1. After three simple queries, insert an **[!UICONTROL Intersection]** -type activity.

   In this example; the queries respectively target men, recipients living in Paris and recipients aged between 18 and 30 years old.

1. Configure the intersection. To do this, select the **[!UICONTROL Keys only]** reconciliation method since the populations resulting from the queries contain consistent data.
1. If you have inputted additional data for the queries, you may choose to keep only those that are shared by recipients by checking the relevant box.
1. If you wish to use the rest of the data (in regard to the queries but not their intersection), check the **[!UICONTROL Generate complement]** box.
1. Add a list update activity after the intersection result. You can also add a list update to the complement should you wish to use this too.
1. Execute the workflow. Here, two recipients apply to all three inputted queries at the same time. The complement is made up of five recipients who only apply to one or two of the three queries.

   The intersection result is sent to the first list update. If you have chosen to use the complement, it is also sent to the second list update.

   ![](assets/intersection_example.png)

## Input parameters {#input-parameters}

* tableName
* schema

Each inbound event must specify a target defined by these parameters.

## Output parameters {#output-parameters}

* tableName
* schema
* recCount

This set of three values identifies the target resulting from the intersection. **[!UICONTROL tableName]** is the name of the table that records the target identifiers, **[!UICONTROL schema]** is the schema of the population (usually **[!UICONTROL nms:recipient]**) and **[!UICONTROL recCount]** is the number of elements in the table.


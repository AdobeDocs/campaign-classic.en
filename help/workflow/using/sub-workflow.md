---
title: Sub-workflow
seo-title: Sub-workflow
description: Sub-workflow
seo-description: 
page-status-flag: never-activated
uuid: d7322472-2e17-4bea-bff7-f2456e5ac682
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: bd1a2185-001d-43ab-bf01-d3c34cdaf9da
index: y
internal: n
snippet: y
---

# Sub-workflow{#sub-workflow}

The **Sub-workflow** activity lets you trigger the execution of another workflow and recover the result. This activity lets you use complex workflows while using a simplified interface.

You can call multiple sub-workflows in a single workflow. Sub-workflows are executed synchronously.

>[!NOTE]
>
>For the sub-workflow to be run correctly, you must have only one "arrival" type jump with the lowest number, and only one "start" type jump with the highest number. For example, if you have "start" type jumps with a priority of 1, 2, and 3, you should have only one "start" type jump with a priority of 3.

1. Create a workflow that you will use as a sub-workflow in another workflow.
1. Insert a **Jump (end point)** activity with a priority of 1 at the beginning of the workflow. If you have multiple "arrival" type jumps, Adobe Campaign will use the "arrival" jump with the lowest number.

   Insert a **Jump (start point)** activity with a priority of 2 at the end of the workflow. If you have multiple "start" type jumps, Adobe Campaign will use the "starting" jump with the highest number.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >If the sub-workflow activity references a workflow with several **Jump** activities, the sub-workflow is executed between the "arrival" type jump with the lowest number and the "start" type jump with the highest number.

1. Complete and save this "sub-workflow".
1. Create a "master" workflow.
1. Insert a **Sub-workflow** activity and open it.
1. Select the workflow that you want to use from the **Workflow template** drop-down list.

   ![](assets/subworkflow_selection.png)

1. You can also add a configuration script to alter the referenced workflow.
1. Click **Ok**. It will automatically create an outbound transition with the label of the **Jump (start point)** activity from the selected workflow.

   ![](assets/subworkflow_outbound.png)

1. Run the workflow.

Once run, the workflow that was called as a sub-workflow is still in **Being edited** status, which means the following:

* You cannot right-click the transitions to display the target.
* The count of intermediate populations cannot be displayed.
* The logs are aggregated in the "master" workflow and they are only labelled as "subworkflow".

Indeed, this workflow is only a template. A new sub-workflow based on this template is created when called from the "master" workflow.

## Input parameters (optional) {#input-parameters--optional-}

* tableName
* schema

Each inbound event must specify a target defined by these parameters.

## Output parameters {#output-parameters}

* tableName
* schema
* recCount

This set of three values identifies the population targeted by the query. **tableName** is the name of the table that records the target identifiers, **schema** is the schema of the population (usually nms:recipient) and **recCount** is the number of elements in the table.

* targetSchema

This value is the schema of the work table. This parameter is valid for all transitions with **tableName** and **schema**.

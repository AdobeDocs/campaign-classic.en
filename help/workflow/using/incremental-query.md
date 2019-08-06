---
title: Incremental query
seo-title: Incremental query
description: Incremental query
seo-description: 
page-status-flag: never-activated
uuid: fc21a9e3-a118-48fa-9b79-f09fb4d3a0d9
contentOwner: sauviat
topic-tags: targeting-activities
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 3125d4ed-e753-4e2c-91cb-6812022da4e2
index: y
internal: n
snippet: y
---

# Incremental query{#incremental-query}

An incremental query lets you periodically select a target based on a criterion, while excluding the people already targeted for this criterion.

The population already targeted is stored in the memory by workflow instance and by activity, i.e. two workflows started from the same template do not share the same log. On the other hand, two tasks based on the same incremental query for the same workflow instance will use the same log.

The query is defined in the same way as for standard queries (refer to [Creating a query](../../workflow/using/incremental-query.md#creating-a-query)), but its execution is scheduled.

>[!CAUTION]
>
>If the result of an incremental query is equal to **0** during one of its executions, the workflow is paused until the query's next programmed execution. The transitions and activities that follow the incremental query are therefore not processed before the following execution.

To do this:

1. In the **Scheduling & History** tab, select the **Schedule execution** option. The task remains active once it has been created and will only be triggered at the times specified by the schedule for executing the query. However, if the option is disabled, the query is executed immediately **and in one go**.
1. Click the **Change** button.

   In the **Schedule editing wizard** window, you can configure the type of frequency, event recurrence and event validity period.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Click **Finish** to save the schedule.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. The lower section of the **Scheduling & History** tab allows you to select the number of days to be taken into account in the history.

   ![](assets/edit_request_inc.png)

    * **History in days**

      Recipients already targeted can be logged a maximum number of days from the day they were targeted. If this value is zero, the recipients are never purged from the log.
    
    * **Keep history when starting**

      This option lets you not purge the log when the activity is enabled.
    
    * **SQL table name**

      This parameter lets you overload the default SQL table containing the history data.

## Example of an incremental query: quarterly list update {#example-of-an-incremental-query--quarterly-list-update}

In the following example, an incremental query is used to automatically update a recipient list. These recipients are targeted as part of seasonal marketing campaigns.

As these campaigns are launched at the beginning of every season in order to offer relevant sports activities, these lists are updated every quarter. However, a recipient here must only be targeted once every 9 months by this campaign. This allows you to space out the recipient's eligibility frequency and to offer activities for different seasons over the years.

![](assets/incremental_query_example.png)

1. Add an incremental query as well as a list update activity into a new workflow.
1. Configure the **Incremental query** tab of the activity as specified in [Creating a query](../../workflow/using/incremental-query.md#creating-a-query).
1. Select the **Scheduling & History** tab and then specify a 270-day history. A recipient that has already been targeted will no longer be targeted for a period of 270 days, or roughly 9 months.

   Then click the **Change...** button.

1. To ensure the list is updated before the start of each season, select **Monthly**.
1. On the next screen, select March, June, September and December. Choose the 20th of the month and choose what time you would like to launch the workflow.
1. Next select the validity period for the query. For example, if you want this activity to be permanently active, select **Permanent validity**.

   ![](assets/incremental_query_example_2.png)

1. After approving the incremental query, configure the list update activity as explained in [List update](../../workflow/using/list-update.md).

The workflow will therefore be automatically launched just before the start of each season. The list will be updated with new, eligible recipients to receive the offers.

## Output parameters {#output-parameters}

* tableName
* schema
* recCount

This set of three values identifies the population targeted by the query. **tableName** is the name of the table that records the target identifiers, **schema** is the schema of the population (usually nms:recipient) and **recCount** is the number of elements in the table.

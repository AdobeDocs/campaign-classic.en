---
title: Quarterly list update using an incremental query
description: In this use case, an incremental query is used to automatically update a recipient list.
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
index: y
internal: n
snippet: y
---

# Quarterly list update using an incremental query {#quarterly-list-update}

In the following example, an [incremental query](../../workflow/using/incremental-query.md) is used to automatically update a recipient list. These recipients are targeted as part of seasonal marketing campaigns.

As these campaigns are launched at the beginning of every season in order to offer relevant sports activities, these lists are updated every quarter. However, a recipient here must only be targeted once every 9 months by this campaign. This allows you to space out the recipient's eligibility frequency and to offer activities for different seasons over the years.

![](assets/incremental_query_example.png)

1. Add an incremental query as well as a list update activity into a new workflow.
1. Configure the **[!UICONTROL Incremental query]** tab of the activity as specified in [Creating a query](../../workflow/using/query.md#creating-a-query).
1. Select the **[!UICONTROL Scheduling & History]** tab and then specify a 270-day history. A recipient that has already been targeted will no longer be targeted for a period of 270 days, or roughly 9 months.

   Then click the **[!UICONTROL Change...]** button.

1. To ensure the list is updated before the start of each season, select **[!UICONTROL Monthly]**.
1. On the next screen, select March, June, September and December. Choose the 20th of the month and choose what time you would like to launch the workflow.
1. Next select the validity period for the query. For example, if you want this activity to be permanently active, select **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. After approving the incremental query, configure the list update activity as explained in [List update](../../workflow/using/list-update.md).

The workflow will therefore be automatically launched just before the start of each season. The list will be updated with new, eligible recipients to receive the offers.

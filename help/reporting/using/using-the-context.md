---
title: Using the context
seo-title: Using the context
description: Using the context
seo-description: 
page-status-flag: never-activated
uuid: 4125f5f6-f1ac-4a8e-9c1a-a876ccc762d3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
audience: reporting
discoiquuid: e120d375-b01c-4e67-9858-1d57e22145a5
index: y
internal: n
snippet: y
---

# Using the context{#using-the-context}

When you want to represent data in the form of **tables** or **charts**, it can be taken from two sources: a new query (refer to [Defining a direct filter on data](../../reporting/using/using-the-context.md#defining-a-direct-filter-on-data)) or the report context (refer to [Using context data](../../reporting/using/using-the-context.md#using-context-data)).

## Defining a direct filter on data {#defining-a-direct-filter-on-data}

### Filtering data {#filtering-data}

Using a **Query** type activity isn't mandatory when building a report. Data can be filtered directly in the tables and charts that make up the report.

This enables you to select the data to display in the report directly via the **Page** activity of the report.

To do this, click the **Filter data...** link in the **Data** tab: this link lets you access the expressions editor to define a query on the data to be analyzed.

![](assets/reporting_filter_data_from_page.png)

### Example: use a filter in a chart {#example--use-a-filter-in-a-chart}

In the following example, we want the chart to show only recipient profiles who live in France and who made a purchase during the year.

To define this filter, place a page in the chart and edit it. Click the **Filter data** link and create the filter that matches the data you want to display. For more on building queries in Adobe Campaign, refer to [this section](/platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

Here, we want to display the breakdown by city of selected recipients.

![](assets/reporting_graph_with_2vars.png)

The rendering will look like this: 

![](assets/reporting_graph_with_2vars_preview.png)

### Example: use a filter in a pivot table {#example--use-a-filter-in-a-pivot-table}

In this example, the filter lets you display only non-Parisian customers in the pivot table, without using another query beforehand.

Apply the following steps:

1. Place a page in the chart and edit it.
1. Create a pivot table.
1. Go to the **Data** tab and select the cube to be used.
1. Click the **Filter data...** link and define the following query to remove Adobe from the list of companies.

   ![](assets/s_ncs_advuser_report_display_03.png)

Only recipients that meet the filtering criteria will appear in the report.

![](assets/s_ncs_advuser_report_display_04.png)

## Using context data {#using-context-data}

To represent data in the form of a **table** or a **chart**, the data can come from the report context.

In the page that contains the table or the chart, the **Data** tab lets you select the data source. 

![](assets/s_ncs_advuser_report_datasource_3.png)

* The **New query** option lets you build a query to collect data. For more on this, refer to [Defining a direct filter on data](../../reporting/using/using-the-context.md#defining-a-direct-filter-on-data).
* The **Context data** option lets you use the input data: the context of the report coincides with the information contained in the inbound transition of the page that contains the chart or the table. This context may, for instance, contain data collected via a **Query** activity placed before the **Page** activity and for which you need to specify the table and the fields that the report concerns.

For instance, in a query box, build the following query for the recipients:

![](assets/s_ncs_advuser_report_datasource_2.png)

Then indicate the source of the data in your report, in this case: **Data from the context**.

The data location is inferred automatically. If necessary, you can force the data path.

![](assets/s_ncs_advuser_report_datasource_4.png)

When you select the data which the statistics will concern, the available fields coincide with the data specified in the query.

![](assets/s_ncs_advuser_report_datasource_1.png)


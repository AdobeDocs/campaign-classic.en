---
product: campaign
title: Best practices for reporting
description: Campaign reporting best practices
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
---
# Reporting best practices{#best-practices-reporting}

## Analyzing needs{#analyzing-needs}

Using a reporting tool depends on the volume of data to manipulate, its complexity, and on the type of reporting to be set up.

To optimize the creation, use and durability of a report, you need to take a close look at the needs which you want to meet. This first analysis will enable you to identify the type of report to create and the best creation mode. To create the report, apply the following steps:

1. Identify the need

   The first step is to clearly identify the need: what you want to show in your report and what its goal is (monitoring, analysis, data export, etc.).

   Adobe Campaign offers a wide range of reporting capacities. It is important to analyze your need to identify the most suitable functionality.

   For instance, you can:

    * Explore the data in the database and define measurements. Learn more [in this section](../../reporting/using/about-cubes.md)
    * Add indicators to an existing report. Learn more [in this section](../../reporting/using/about-reports-creation-in-campaign.md)
    * View the data in the database. Learn more [in this section](../../reporting/using/about-descriptive-analysis.md)
    * Create a new delivery report. Learn more [in this section](../../reporting/using/about-reports-creation-in-campaign.md)),
    * Export data from the Adobe Campaign database (via a workflow, refer to [this section](../../workflow/using/about-workflows.md)
    * Create a pivot table. Learn more [in this section](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
    * Explore aggregated data. Learn more [in this section](../../reporting/using/about-cubes.md)
    * Use a wizard to analyze data. Learn more [in this section](../../reporting/using/about-descriptive-analysis.md)
    * Analyze large volumes of data. Learn more [in this section](../../reporting/using/about-reports-creation-in-campaign.md)

1. Identify the target population

   Then you need to find out who the report you want to create will target, know the kind of public who will view it and the report display mode (in a browser, in Adobe Campaign, for a specific object, for the entire platform, etc.).

   You can also create reports for:

    * All Adobe Campaign operators,
    * Operators with the rights to access a marketing campaign only,
    * A single operator for temporary use,
    * All operators in Web access, etc.

   These considerations also need to take into account the issues linked to access rights and security.

1. Define the content

   Then you need to find out what type of data you want to display: delivery indicators, reports on the database profiles, etc.

   You also need to know the nature of this data (simple, resulting from a calculation, significant, etc.), its location (in Adobe Campaign, in a third-party system), its update frequency to define the calculation periodicity (daily, weekly, on-the-fly), as well as its volume.

   The issues linked to data volumes and updates need to be looked into carefully to avoid report display problems, especially in terms of time. We therefore recommend creating aggregates to pre-calculate some data outside of the report. Tables that contain the tracking and delivery logs can include millions of records: this means the data needs to be aggregated via a workflow to be used in a report.

## Optimizing report creation{#optimizing-report-creation}

### Data volume {#data-volume}

To guarantee optimal performances, the volume of manipulated data mustn't be too large.

Namely:

* Calculation time for a report must never exceed 5 minutes.

  Likewise, during the design phase, with a small volume of data, if report calculation exceeds 60 seconds, the calculation methods needs to be changed.

* When using Marketing Analytics module, reporting data must not exceed 10 million lines.

We also recommend calculating aggregates at night and using this aggregated data directly in the reports. These aggregates must be created via dedicated Data Management workflows (SQL queries).

You can also calculate reports during the night and automatically create a history that can be viewed at any time without overloading the database.

### Queries {#queries}

We recommend using SQL queries whenever possible and avoiding JavaScript post-processing. If necessary, use a Script activity in a workflow and delete the data used for calculation. You can also use archived data to accelerate the processing time.

In this case, the following syntax should be used:

```
if(string(ctx@_historyId)!==""))
```

Queries that enable you to collect the data displayed in the reports must not be too complex, especially if applied to all the data in the database. To improve performances, it can be useful to filter the data before executing these queries: this means the calculation will only concern part of the data.

### Performances {#performances}

The recommendations above enable you to optimize report calculation.

In addition to this, Adobe Campaign recommends the following improvements:

* Work on your datamodel: indexed fields must be used mainly to improve calculation formulas.

  To find an indexed field quickly, look at the name of the column in the Adobe Campaign interface: the sorting arrow is underlined in red if the field is indexed.

  For more on indexes, refer to [this section](../../configuration/using/data-model-best-practices.md#indexes).

* Make sure the report is scalable: data volume may increase significantly over time.

  Likewise, the volume of data manipulated during the test phases may differ from the actual data volume in production. This is why test phases are important.

  Finally, data purge delays need to be known and adapted when necessary for easy data manipulation.

  For more on cleanup and data retention, refer to [this section](../../configuration/using/data-model-best-practices.md#data-retention).

### Exporting reports {#exporting-reports}

Recommendations specific to exporting reports are detailed in [this section](../../reporting/using/actions-on-reports.md#exporting-a-report).

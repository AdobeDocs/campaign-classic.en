---
title: Optimizing report creation
seo-title: Optimizing report creation
description: Optimizing report creation
seo-description: 
page-status-flag: never-activated
uuid: 975b0a9a-b88d-4555-baed-e3d43f68ce3a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
audience: reporting
discoiquuid: bd9a0072-699a-4837-8cb7-790db95f2d7c
index: y
internal: n
snippet: y
---

# Optimizing report creation{#optimizing-report-creation}

## Data volume {#data-volume}

To guarantee optimal performances, the volume of manipulated data mustn't be too large.

Namely:

* Calculation time for a report must never exceed 5 minutes.

  Likewise, during the design phase, with a small volume of data, if report calculation exceeds 60 seconds, the calculation methods needs to be changed.

* When using Marketing Analytics, the manipulated data must not exceed 10 million lines.

We also recommend calculating aggregates at night and using this aggregated data directly in the reports. These aggregates must be created via dedicated Data Management workflows (SQL queries).

You can also calculate reports during the night and automatically create a history that can be viewed at any time without overloading the database.

## Queries {#queries}

We recommend using SQL queries whenever possible and avoiding JavaScript post-processing. If necessary, use a Script activity in a workflow and delete the data used for calculation. You can also use archived data to accelerate the processing time.

In this case, the following syntax should be used:

```
if(string(ctx@_historyId)!==""))
```

Queries that enable you to collect the data displayed in the reports must not be too complex, especially if applied to all the data in the database. To improve performances, it can be useful to filter the data before executing these queries: this means the calculation will only concern part of the data.

## Performances {#performances}

The recommendations above enable you to optimize report calculation.

In addition to this, Adobe Campaign recommends the following improvements:

* Study the datamodel: indexed fields must be used mainly to improve calculation formulas.

  To find an indexed field quickly, look at the name of the column in the Adobe Campaign interface: the sorting arrow is underlined in red if the field is indexed.

* Make sure the report is valid in the long run: data volume may increase significantly over time.

  Likewise, the volume of data manipulated during the test phases may differ from the actual data volume in production. This is why test phases are important.

  Finally, data purge delays need to be known and adapted when necessary for easy data manipulation.

## Exporting reports {#exporting-reports}

Recommendations specific to exporting reports are detailed in [this section](../../reporting/using/actions-on-reports.md#exporting-a-report).

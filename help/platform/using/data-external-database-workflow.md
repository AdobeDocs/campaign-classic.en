---
title: Accessing an external database
seo-title: Accessing an external database
description: Accessing an external database
seo-description: 
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
---

# Using data from an external database in a workflow {#using-data-from-an-external-database-in-a-workflow}

In several Adobe Campaign workflow activities, you can use the data stored in an external database.

## Filtering on external data {#filtering-on-external-data}

The query activity allows you to add external data and use it in the defined filter configurations.

For more on this, refer to the [Query](../../workflow/using/targeting-data.md#selecting-data) section.

## Creating sub-sets {#creating-sub-sets}

The split activity allows you to create sub-sets. You can use external data to define the filtering criteria to use.

For more on this, refer to the [Split](../../workflow/using/split.md) section.

## Loading external database {#loading-external-database}

You can use the external data in the Data loading (RDBMS). This activity is presented in the [Data loading](../../workflow/using/data-loading--rdbms-.md) section.

## Adding information and links {#adding-information-and-links}

The enrichment activity allows you to add additional data to the workflow's worktable as well as links to an external table. For this reason, it can exploit the data from an external database. This activity is presented in the [Enrichment](../../workflow/using/enrichment.md) section.

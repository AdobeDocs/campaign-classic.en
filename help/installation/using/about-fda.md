---
title: Accessing an external database
description: Learn how to access and process data in an external database
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
---

# Get Started with Federated Data Access {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

## Prerequisites {#operating-principle}

The FDA option allows you to extend your data model in a third-party database. It will automatically detect the structure of the targeted tables and use data from the SQL sources.

In order to use this capability, prerequisites are listed below:

* **Configuration**: except for Snowflake, you need an **on-premise** or **hybrid** hosting model to set up Federated Data Access. [Learn more](../../installation/using/hosting-models.md)
* **External database version**: you need to have an external database that is compatible with the Adobe Campaign FDA module. The list of database systems and compatible versions is detailed in the [compatibility matrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA). 
* **Permissions**: users must also have the [necessary permissions](../../installation/using/remote-database-access-rights.md) in Adobe Campaign and on the external database.

## Limitations {#limitations}

The FDA option is made to manipulate the data in external databases in batch mode in workflows. To avoid performance issues, it is not recommended to use the FDA module in the context of unitary operations, such as: personalization, interaction, real-time messaging, etc.

Avoid the operations that need to use both the Adobe Campaign and the external database as much as possible. To do this, you can:

* Export the Adobe Campaign database to the external database and execute the operations only from the external database before re-importing the results into Adobe Campaign.

* Collect the data from the external Adobe Campaign database and execute the operations locally.

If you want to carry out personalization in your deliveries using data from the external database, collect the data to use in a workflow to make it available in a temporary table. Then use the data from the temporary table to personalize your delivery.

The FDA option is subject to the limitations of the external database system that you use.

## Recommendations {#recommendations}

### Create temporary schemas {#create-temporary-schemas}

You can manage several accesses to Greenplum external database throuhgh FDA. A dedicated option lets you create a working schema directly when configuring the external account.

![](assets/fda_work_table.png)

>[!NOTE]
>
>This option is only available with PostgreSQL Greenplum.

### Optimize email personalization with external data {#optimizing-email-personalization-with-external-data}

You can pre-process message personalization in a dedicated workflow. To perform this, use the **[!UICONTROL Prepare the personalization data with a workflow]** option, available in the **[!UICONTROL Analysis]** tab of the delivery properties.

During the delivery analysis, this option automatically creates and executes a workflow that stores all of the data linked to the target in a temporary table, including data from tables linked in an external database.

This option significantly improves performances when executing the personalization step.

### Use data from an external database in a workflow {#using-data-from-an-external-database-in-a-workflow}

In multiple Adobe Campaign workflow activities, you can use the data stored in an external database.

* **Filter on external data** -  The [Query](../../workflow/using/targeting-data.md#selecting-data) activity allows you to add external data and use it in the defined filter configurations. For more on this, refer to [this page](../../workflow/using/targeting-data.md#selecting-data).

* **Create sub-sets** - The [Split](../../workflow/using/split.md) activity allows you to create sub-sets. You can use external data to define the filtering criteria to use. For more on this, refer to [this page](../../workflow/using/split.md).

* **Load external database** - You can use the external data in the [Data loading](../../workflow/using/data-loading--rdbms-.md) (RDBMS) activity. Learn more in [this page](../../workflow/using/data-loading--rdbms-.md).

* **Adding information and links** - The [Enrichment](../../workflow/using/enrichment.md) activity lets you to add additional data to the worktable of the workflow, and links to an external table. In this context, it can use data from an external database. Learn more in [this page](../../workflow/using/enrichment.md).

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

# About Federated Data Access {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

>[!CAUTION]
>
>Accessing an external database via FDA is only possible for on-premise or hybrid installations, except with the Snowflake connectors. For more on this, refer to this [page](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Operating principle {#operating-principle}

The FDA option allows you to extend your data model in a third-party database. It will automatically detect the structure of the targeted tables and use data from the SQL sources.


In order to use this functionality, you have to:

1. Have an external database that is compatible with the Adobe Campaign FDA module. The list of database systems and compatible versions is detailed in the [compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). Users must also have the [necessary permissions](#remote-database-access-rights) in Adobe Campaign and on the external database.
1. [Install the drivers](#specific-configurations-by-database-type) that correspond to your database on the Adobe Campaign server.
1. [Create and configure an external account](#connecting-to-the-database) that allows you to establish the connection between Adobe Campaign and the external database. For more information on available external accounts, refer to this [page](../../platform/using/external-accounts.md).
1. [Create the schema](#creating-the-data-schema) of the external database in Adobe Campaign. This allows you to recognize the data structure of the external database.
1. Eventually, [Create a new target mapping](#defining-data-mapping) from the previously created schema, in the case where the recipients of your deliveries come from the external database. This presents certain limitations, particularly in regard to personalizing the deliveries.

Once the data schema is created, data can be processed in Adobe Campaign workflows. For more on this, refer to [this section](../../workflow/using/executing-a-workflow.md#architecture).

## Best practices and recommendations {#best-practices-and-recommendations}

The FDA option is made to manipulate the data in external databases in batch mode in workflows. Using the FDA in another context, for example for unitary operations, must be carried out with precaution (Personalization, Interaction, real-time deliveries, etc.).

Avoid the operations that need to use both the Adobe Campaign and the external database as much as possible. To do this, you can:

* Export the Adobe Campaign database to the external database and execute the operations only from the external database before re-importing the results into Adobe Campaign.
* Collect the data from the external Adobe Campaign database and execute the operations locally.

If you want to carry out personalization in your deliveries using data from the external database, collect the data to use in a workflow to make it available in a temporary table. Then use the data from the temporary table to personalize your delivery.

## Limitations {#limitations}

The FDA option is subjected to the limitation soft the external database system that you use.

For performance reasons, we do not advise using this functionality for carrying out unitary operations (delivery personalization, Interaction module, real time).

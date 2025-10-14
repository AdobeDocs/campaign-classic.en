---
product: campaign
title: Campaign FDA best practices and limitations
description: Learn best practices and limitations when working with an external database (FDA)
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
---
# Best practices and limitations 



## Optimize email personalization with external data {#optimizing-email-personalization-with-external-data}

You can pre-process message personalization in a dedicated workflow. To perform this, use the **[!UICONTROL Prepare the personalization data with a workflow]** option, available in the **[!UICONTROL Analysis]** tab of the delivery properties.

During the delivery analysis, this option automatically creates and executes a workflow that stores all of the data linked to the target in a temporary table, including data from tables linked in an external database.

This option significantly improves performances when executing the personalization step.

## Use data from an external database in a workflow {#using-data-from-an-external-database-in-a-workflow}

In multiple Adobe Campaign workflow activities, you can use the data stored in an external database.

* **Filter on external data** -  The  Query activity allows you to add external data and use it in the defined filter configurations. For more on this, refer to the [Campaign v8 documentation]https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html){target="_blank"}.

* **Create sub-sets** - The Split activity allows you to create sub-sets. You can use external data to define the filtering criteria to use. Refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}.

* **Load external database** - You can use the external data in the Data loading (RDBMS) activity. Learn more in the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-rdbms.html){target="_blank"}.

* **Adding information and links** - The Enrichment activity lets you to add additional data to the worktable of the workflow, and links to an external table. In this context, it can use data from an external database. Refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}.

## Guardrails and limitations {#fda-limitations}

The FDA option is designed to manipulate the data in external databases in batch mode in workflows. To avoid performance issues, it is not recommended to use the FDA module in the context of unitary operations, such as: personalization, interaction, real-time messaging, etc.

Targeting data from one database and filering the results using a filtering dimension that belongs to another database is not supported. You cannot join tables that are on different data sources in one query. You can overcome this limitation using other workflow activities such as Change dimension.

Avoid the operations that need to use both the Adobe Campaign and the external database as much as possible. Best practice is to:

* Export the Adobe Campaign database to the external database and execute the operations only from the external database before re-importing the results into Adobe Campaign.

* Collect the data from the external Adobe Campaign database and execute the operations locally.

If you want to carry out personalization in your deliveries using data from the external database, collect the data to use in a workflow to make it available in a temporary table. Then use the data from the temporary table to personalize your delivery.

The FDA option is subject to the limitations of the external database system that you use.

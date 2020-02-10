---
title: Using the Adobe Campaign Classic Recipient table
description: Learn how to use the out-of-the-box recipient table in Adobe Campaign Classic when designing your data model.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
---

# Data model best practices{#data-model-best-practices}

This document outlines key recommendations while designing your Adobe Campaign data model.

Below are a few best practices that should be followed when designing your data model using large tables and complex joins.

* When using additional custom recipient tables, make sure you have a dedicated log table for each delivery mapping.
* Reduce the number of columns, particularly by identifying those that are unused.
* Optimize the data model relations by avoiding complex joins, such as joins on several conditions and/or several columns.
* For join keys, always use numeric data rather than character strings.
* Reduce as much as you can the depth of log retention. If your need deeper history, you can aggregate computation and/or handle custom log tables to store larger history.

For more detailed best practices on how to optimize the database design for larger volumes, see [Campaign Classic Data model Best practices](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).

## Overview {#overview}

Adobe Campaign system is extremely flexible and can be extended beyond the initial implementation. However, while possibilities are infinite, it is critical to make wise decisions and build strong foundations to start designing your data model.

This document provides common use cases and best practices to learn how to architect properly you Adobe Campaign tool.

## Data model architecture {data-model-architecture}

Adobe Campaign Standard is a powerful cross-channel campaign management system that can help you align your online and offline strategies to create personalized customer experiences.

### Customer-centric approach {#customer-centric-approach}

While most email service providers are communicating to customers via a list-centric approach, Adobe Campaign relies on a relational database in order to leverage a broader view of the customers and their attributes.

This customer-centric approach is shown on the chart below. The **Recipient** table in grey represents the main customer table around which everything is being built:

![](assets/customer-centric-data-model.png)

To access the description of each table, go to **[!UICONTROL Admin > Configuration > Data schemas]**, select a resource from the list and click the **[!UICONTROL Documentation]** tab.

The Adobe Campaign default data model is presented in this [document](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html).

<!--You can find a datamodel representation for the out-of-the-box resources [here](../../developing/using/datamodel-introduction.md).-->

<!--### What is a customer? {#customer-definition}

If you have customer data in more than one system, you need to determine which solution will allow you to identify records as one person. This work might require rules, eventually a match and merge processes to determine the master record. This master record should be the one sent to Adobe Campaign.

While some of this data cleansing might be performed in Adobe Campaign, the recommendation is to run these processes outside and only import clean data in Adobe Campaign. You should keep Campaign as a marketing solution more than a data cleansing tool.

Be able to provide a master customer record which will be sent to Adobe Campaign.-->

### Data for Adobe Campaign {#data-for-campaign}

What data should be sent to Adobe Campaign? It is critical to determine the data required for your marketing activities.

>[!NOTE]
>
>Adobe Campaign is neither a data warehouse or a reporting tool. Therefore, do not try to import all possible customers and their associated information into Adobe Campaign, or import data which will only be used to build reports.

To make the decision whether an attribute would be needed or not in Adobe Campaign, determine whether it would fall under one of these categories:
* Attribute used for **segmentation**
* Attribute used for **data management processes** (aggregate calculation for example)
* Attribute used for **personalization**

If not falling into any of these, you are most likely not going to need this attribute in Adobe Campaign.

### Data types {#data-types}

To ensure good architecture and performance of your system, follow the best practices below to set up data in Adobe Campaign:
* The *expr* attribute  allows to define a schema attribute as a calculated field rather than a physical set value in a table. This can enable to access information in a different format (as for age and birth date for example) without the need to store both values. However, when the expression calculation is complex, it is not recommended to use the *expr* attribute as on-the-fly calculation may impact the performance of your queries.

* The length for a *string* field should always be defined with the column. By default, the maximum length in Adobe Campaign is 255, but Adobe recommends keeping the field shorter if you already know that the size will not exceed a shorter length.
* It is acceptable to have a field shorter in Adobe Campaign than it is in the source system if you are certain that the size in the source system was overestimated and would not be reached. This could mean a shorter string or smaller integer in Adobe Campaign.

## Configuring data structure {#configuring-data-structure}

This section outlines best practices when configuring a resource's data structure.

### Identifiers {identifiers}

Adobe Campaign resources have three identifiers, and it is possible to add an additional identifier.

The following table describe these identifiers and their purpose.

| Identifier | Description | Best practices |
|--- |--- |--- |--- |
| ID | <ul><li>The PKey is the physical primary key of an Adobe Campaign table.</li><li>This identifier is usually unique to a specific Adobe Campaign instance.</li><li>An auto-generated ID can be visible in a schema definition. Search the autopk="true" attribute. | <ul><li>Via the API system, it is possible to retrieve a PKey value (which is a generated/hashed value, not the physical key).</li><li>It is not recommended to use it for anything else than retrieving, updating, or deleting records via API.</li><li>For more on this, see the [API documentation](../../api/using/about-campaign-standard-apis.md).</li></ul> |
| Name (or internal name) | <ul><li>This information is a unique identifier of a record in a table. This value can be manually updated.</li><li>This identifier keeps its value when deployed in a different instance of Adobe Campaign. It must have a different name than the generated value to be exportable via a package.</li><li>This is not the actual primary key of the table.</li></ul> | <ul><li>Do not use special characters such as space “ “, semi-column “:” or hyphen “-“.</li><li>All these characters would be replaced by an underscore “_” (allowed character). For example, “abc-def” and “abc:def” would be stored as “abc_def” and overwrite each other. |
| Label | <ul><li>The label is the business identifier of an object or record in Adobe Campaign.</li><li>This object allows spaces and special characters.</li><li>It does not guarantee the uniqueness of a record.</li></ul>| <ul><li>It is recommended to determine a structure for your object labels.</li><li>This is the most user-friendly solution to identify a record or object for an Adobe Campaign user.</li></ul> |

### Identification keys {#keys}

Each resource created in Adobe Campaign must have at least one unique identification key.

<!--Most organizations are importing records from external systems. While the physical key of a resource lies behind the PKey attribute, it is possible to determine a custom key in addition.

This custom key is the actual record primary key in the external system feeding Adobe Campaign.

When an out-of-the-box resource has both an internal auto-generated and an internal custom key, the internal key will be set as a unique index in the physical database table.-->

When creating a custom resource, you have two options:
* A combination of auto-generated key and internal custom key. This option is interesting if your system key is a composite key or not an integer. Integers will provide higher performances in big tables and joining with other tables.
* Using the primary key as the external system primary key. This solution is usually preferred as it simplifies the approach to import and export data, with a consistent key between different systems.

Identification keys should not be used as a reference in workflows.

### Indexes {#indexes}

Adobe Campaign automatically adds an index to all primary and internal keys defined in a resource.

* Adobe recommends defining additional indexes as it may improve performance.
* However, do not add too many indexes as they use space on the database. Numerous indexes may also have a negative performance impact.
* Carefully select the indexes that need to be defined.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

### Links {#links}

* While it is possible to join any table in a workflow, Adobe recommends defining common links between resources directly in the data structure definition.
* Link should be defined in alignment with the actual data in your tables. A wrong definition could impact data retrieved via links, for example unexpectedly duplicating records.
* Name your link consistently with the resource name: the link name should help understand what the distant table is.
* Do not name a link with “id” as a suffix. For example, name it “transaction” rather than “transactionId”.

<!--## Operational best practices {#operational-best-practices}

In order to make sure better performance all the time, below practices could be handy
* Avoid using operations like “CONTAINS” in queries, if we know what is expected and want to be filtered for, apply the same condition with an “EQUAL TO” or other specific filter operators
* Avoid joining with non-indexed fields while building data in workflows
* Try and make sure the processes like import and export happens during off business hours
* Make sure there is a schedule for all the daily activities and stick to the schedule
* If one or few of the daily process fails and if it is mandatory to run it that day itself, make sure there are no conflicting processes running during the manual process is kicked off, this can affect the sys-tem performance
* Make sure none of the Daily campaign run during the import process or any manual process is executed
* One-to-many relationships
    * Data design will impact usability and functionality. If you design your data model with lots of one-to-many relationships, it makes it more difficult for users to construct meaningful logic in the application. One-to-many filter logic can be difficult for non-technical marketers to cor-rectly construct and understand.
    * It's good to have all the essential fields in one table because it makes it easier for users to build queries. Sometimes it's also good for performance to duplicate some fields across tables if it can avoid a join.
    * Certain built-in functionalities will not be able to reference one-to-many relationships, e.g. Of-fer Weighting formula and Deliveries
* Use one or several reference tables rather than duplicating a field in every row. When using key/value pairs, it is preferred to choose a numerical key
* A short string remains acceptable. In case references tables are already in place in an external sys-tem, reusing the same will facilitate the data integration with Adobe Campaign.-->
---
solution: Campaign Classic
product: campaign
title: Get started with Campaign Classic data model
description: Learn how to extend Campaign data model, edit schemas, use APIs, and more
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
---
# Get started with Campaign data model{#about-data-model}

The conceptual data model of the Adobe Campaign database consists in a set of built-in tables and their interaction. Main tables and concepts are listed in this page.

## Overview {#data-model-overview}

Adobe Campaign relies on a relational database containing tables that are linked together. The basic structure of the Adobe Campaign data model can be described as follows.

### Recipient table {#recipient-table}

The data model relies on a main table which is by default the Recipient table (**NmsRecipient**). This table enables to store all the marketing profiles.

For more on the Recipient table, see [this section](#default-recipient-table).

### Delivery table {#delivery-table}

The data model also includes a part dedicated to store all the marketing activities. Usually it is the Delivery table (**NmsDelivery**). Each record in this table represents a delivery action or a delivery template. It contains all the necessary parameters for performing deliveries such as target, content, etc.

### Logs tables {#log-tables}

Another part of the data model enables to temporarily store all the logs associated with the execution of the campaigns.

Delivery logs are all messages sent to recipients or devices across all channels. The main Delivery logs table (**NmsBroadLog**) contains the delivery logs for all recipients.
The main Tracking logs table (**NmsTrackingLog**) stores the tracking logs for all recipients. The tracking logs refer to reactions of recipients, such as email openings and clicks. Each reaction corresponds to a tracking log.
Delivery logs and tracking logs are deleted after a certain period, which is specified in Adobe Campaign and can be modified. Therefore, it is highly recommended to export the logs on a regular basis.

### Technical tables {#technical-tables}

Finally, part of the data model consists in technical data used for the applicative process, including operators and user rights (**NmsGroup**), folders (**XtkFolder**).

## Using the default Recipient table {#default-recipient-table}

The out-of-the-box Recipient table in Adobe Campaign provides a good starting point for building your data model. It has a number of predefined fields and table links that can be easily extended. This is particularly useful when you are mainly targeting recipients, because it fits a simple recipient-centric data model.

The benefits of using the standard Recipient table are as follows:

* Working out-of-the-box with functionalities such as subscriptions, seed lists, surveys, social, and so on.
* Providing a marketing database with a recipient-centric data model.
* Faster implementation.
* Easy maintainance by support and partners.

However, it is possible to extend the Recipient table, but not to reduce the number of fields or links in the table.

>[!IMPORTANT]
>
>It is recommended not to delete fields (even if they are useless) in the recipient table as this may lead to errors in the built-in modules.

Also, as the Recipient table is part of the product, both the table and its associated form evolve as the product changes. Therefore extra maintenance is needed to check that any extensions are still valid upon upgrade.

## Extending the data model {#extending-data-model}

When starting with Adobe Campaign, you need to assess the default data model to check which table is the best suited to store your marketing data.

If relevant, you can use the default Recipient table with the out-of-the-box fields, such as described in [this section](#default-recipient-table).

If needed, you can extend it with two mechanisms:

* Extend an existing table with new fields. For example, you can add a new "Loyalty" field to the Recipient table.
* Create a new table, for example a "Purchase" table listing all the purchases made by each profile of the database, and link it to the Recipient table.

For more on configuring extension schemas to extend the conceptual data model, see [About schema edition](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Extending the data model is reserved for advanced users.

## Using a custom recipient table {#custom-recipient-table}

When designing your Adobe Campaign data model, you can use the [out-of-the-box Recipient table](#default-recipient-table), or decide to create a [custom recipient table](../../configuration/using/about-custom-recipient-table.md) table to store you marketing profiles.

Indeed, if your data model does not fit the recipient-centric structure, you can set up other tables as the targeting dimension within Adobe Campaign. For example, this can be relevant when you need to target households, accounts (like mobile phones) and companies/sites rather than simply recipients.

>[!NOTE]
>
>In this case, you will need to create a new [target mapping](../../configuration/using/target-mapping.md).

All the principles and steps needed when using a custom recipient table are detailed in [this section](../../configuration/using/about-custom-recipient-table.md).

The benefits of using a custom Recipient table are as follows:

* **Flexible data model** - The out-of-the-box Recipient table is useless if you do not need most of the Recipient table fields, or if the data model is not recipient-centric.

* **Scalability** - Large volumes require a streamlined table with few fields for an efficient design. The out-of-the-box Recipient table would have too many useless fields, which could impact performance and lack efficiency.

* **Data location** - If data resides on an external existing marketing database, it may require too much effort to use the out-of-the-box Recipient table. Creating a new one based on an existing structure is simpler.

* **Easy migration** - No maintenance is needed to check that all extensions are still valid upon upgrade.

>[!IMPORTANT]
>
>Using a custom recipient table is reserved for advanced users and is subject to some limitations. For more on this, see [this section](../../configuration/using/about-custom-recipient-table.md).

## Related topics

Learn more about Campaign data model in these sections:

* **Description of the main tables** - For more on the default Campaign Classic data model description, refer to [this section](../../configuration/using/data-model-description.md).

* **Full description of each table** -  To access the complete description of each table, go to **[!UICONTROL Admin > Configuration > Data schemas]**, select a resource from the list and click the **[!UICONTROL Documentation]** tab.

    ![](assets/data-model_documentation-tab.png)


* **Campaign schemas** - The physical and logical structure of the data carried in the application is described in XML. It obeys a grammar specific to Adobe Campaign, called a schema. For more on Adobe Campaign schemas, read out [this section](../../configuration/using/about-schema-reference.md).

* **Data model best practices** - Learn Campaign data model architecture and related best practices, in [this section](../../configuration/using/data-model-best-practices.md#data-model-architecture).

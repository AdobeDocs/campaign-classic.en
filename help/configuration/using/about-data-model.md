---
title: About the Adobe Campaign Classic data model
description: This document describes the basics of the Adobe Campaign Classic data model.
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

# About the Campaign Classic data model{#about-data-model}

This section describes the basics of the Adobe Campaign Classic data model, for a better understanding of Campaign built-in tables and their interaction.

The conceptual data model of the Adobe Campaign database consists in a set of built-in tables and their interaction.

To access the description of each table, go to **[!UICONTROL Admin > Configuration > Data schemas]**, select a resource from the list and click the **[!UICONTROL Documentation]** tab.

![](assets/data-model_documentation-tab.png)

For more on the default Campaign Classic data model description, refer to this [document](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html).

The physical and logical structure of the data carried in the application is described in XML. It obeys a grammar specific to Adobe Campaign, called a schema. For more on Adobe Campaign schemas, read out this [section](../../configuration/using/about-schema-reference.md).

## Overview {#data-model-overview}

Adobe Campaign relies on a relational database containing tables that are linked together.

The basic structure of the Adobe Campaign data model can be described as follows.

## Recipient table {#recipient-table}

The data model relies on a main table which is by default the Recipient table (**NmsRecipient**). This table enables to store all the marketing profiles.

For more on the Recipient table, see this [section](../../configuration/using/default-recipient-table.md).

## Delivery table {#delivery-table}

The data model also includes a part dedicated to store all the marketing activities. Usually it is the Delivery table (**NmsDelivery**). Each record in this table represents a delivery action or a delivery template. It contains all the necessary parameters for performing deliveries such as target, content, etc.

## Logs tables {#log-tables}

Another part of the data model enables to temporarily store all the logs associated with the execution of the campaigns.

Delivery logs are all messages sent to recipients or devices across all channels. The main Delivery logs table (**NmsBroadLog**) contains the delivery logs for all recipients.
The main Tracking logs table (**NmsTrackingLog**) stores the tracking logs for all recipients. The tracking logs refer to reactions of recipients, such as email openings and clicks. Each reaction corresponds to a tracking log.
Delivery logs and tracking logs are deleted after a certain period, which is specified in Adobe Campaign and can be modified. Therefore, it is highly recommended to export the logs on a regular basis.

## Technical tables {#technical-tables}

Finally, part of the data model consists in technical data used for the applicative process, including operators and user rights (**NmsGroup**), folders (**XtkFolder**).
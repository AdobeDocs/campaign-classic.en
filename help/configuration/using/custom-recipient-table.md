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

# Using a custom recipient table{#custom-recipient-table}

You can also decide to create a non-standard recipient table to store you marketing profiles.

Indeed, if your data model does not fit the recipient-centric structure, you can set up other tables as the targeting dimension within Adobe Campaign. For example, this can be relevant when you need to target households, accounts (like mobile phones) and companies/sites rather than simply recipients.

Note:

In this case, you will need to create a new target mapping.

For more on using a custom recipient table, see this section.

The benefits of using a custom Recipient table are as follows:


## Flexible data model {#flexible-data-model}


The out-of-the-box Recipient table is useless if you do not need most of the Recipient table fields, or if the data model is not recipient-centric.

Scalability
Large volumes require a streamlined table with few fields for an efficient design. The out-of-the-box Recipient table would have too many useless fields, which could impact performance and lack efficiency.

Data location
If data resides on an external existing marketing database, it may require too much effort to use the out-of-the-box Recipient table. Creating a new one based on an existing structure is simpler.

Easy migration
No maintenance is needed to check that all extensions are still valid upon upgrade.


## Recipient table {#recipient-table}

The data model relies on a main table which is by default the Recipient table (**NmsRecipient**). This table enables to store all the marketing profiles.

For more on the Recipient table, see this section.

## Delivery table {#delivery-table}

The data model also includes a part dedicated to store all the marketing activities. Usually it is the Delivery table (**NmsDelivery**). Each record in this table represents a delivery action or a delivery template. It contains all the necessary parameters for performing deliveries such as target, content, etc.

## Logs tables {#log-tables}

Another part of the data model enables to temporarily store all the logs associated with the execution of the campaigns.

Delivery logs are all messages sent to recipients or devices across all channels. The main Delivery logs table (**NmsBroadLog**) contains the delivery logs for all recipients.
The main Tracking logs table (**NmsTrackingLog**) stores the tracking logs for all recipients. The tracking logs refer to reactions of recipients, such as email openings and clicks. Each reaction corresponds to a tracking log.
Delivery logs and tracking logs are deleted after a certain period, which is specified in Adobe Campaign and can be modified. Therefore, it is highly recommended to export the logs on a regular basis.

## Technical tables {#technical-tables}

Finally, part of the data model consists in technical data used for the applicative process, including operators and user rights (**NmsGroup**), folders (**XtkFolder**).

>[!CAUTION]
>
>Using a custom recipient table is reserved for advanced users and is subject to some limitations. For more on this, see this section.
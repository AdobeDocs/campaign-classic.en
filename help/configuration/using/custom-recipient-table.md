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

When designing your Adobe Campaign data model, you can use the [out-of-the-box Recipient table](../../configuration/using/default-recipient-table.md), or decide to create a non-standard recipient table to store you marketing profiles.

Indeed, if your data model does not fit the recipient-centric structure, you can set up other tables as the targeting dimension within Adobe Campaign. For example, this can be relevant when you need to target households, accounts (like mobile phones) and companies/sites rather than simply recipients.

>[!NOTE]
>
>In this case, you will need to create a new [target mapping](../../configuration/using/target-mapping.md).

All the principles and steps needed when using a custom recipient table are detailed in this [section](../../configuration/using/about-custom-recipient-table.md).

The benefits of using a custom Recipient table are as follows:

## Flexible data model {#flexible-data-model}

The out-of-the-box Recipient table is useless if you do not need most of the Recipient table fields, or if the data model is not recipient-centric.

## Scalability {#scalability}

Large volumes require a streamlined table with few fields for an efficient design. The out-of-the-box Recipient table would have too many useless fields, which could impact performance and lack efficiency.

## Data location {#data-location}

If data resides on an external existing marketing database, it may require too much effort to use the out-of-the-box Recipient table. Creating a new one based on an existing structure is simpler.

## Easy migration {#easy-migration}

No maintenance is needed to check that all extensions are still valid upon upgrade.

>[!IMPORTANT]
>
>Using a custom recipient table is reserved for advanced users and is subject to some limitations. For more on this, see this section.

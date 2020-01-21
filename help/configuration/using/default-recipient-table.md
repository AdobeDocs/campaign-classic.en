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

# Using the default Recipient table{#default-recipient-table}

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

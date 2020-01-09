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

# Extending the data model{#extending-data-model}

When starting with Adobe Campaign, you need to assess the default data model to check which table is the best suited to store your marketing data.

If relevant, you can use the default Recipient table with the out-of-the-box fields, such as described in this [section](../../configuration/using/default-recipient-table.md).

If needed, you can extend it with two mechanisms:

* Extend an existing table with new fields. For example, you can add a new "Loyalty" field to the Recipient table.
* Create a new table, for example a "Purchase" table listing all the purchases made by each profile of the database, and link it to the Recipient table.

For more on configuring extension schemas to extend the conceptual data model, see [About schema edition](../../configuration/using/about-schema-edition.md).

>[!CAUTION]
>
>Extending the data model is reserved for advanced users.

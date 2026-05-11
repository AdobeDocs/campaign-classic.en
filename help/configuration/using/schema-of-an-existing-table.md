---
product: campaign
title: Schema of an existing table
description: Schema of an existing table
feature: Custom Resources
role: Developer
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
TQID: https://experienceleague.adobe.com/Vi1DhgY8tGIhq1TtMOGKeGMrqFgGecfJQHrKyFXTSgg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Schema of an existing table{#schema-of-an-existing-table}

## Overview {#overview}

When the application needs to access the data of an existing table, an SQL view, or data from a remote database, create its schema in Adobe Campaign with the following data:

* Name of table: enter the name of the table (with its alias when a dblink is used) with the "sqltable" attribute, 
* schema key: reference the reconciliation field(s),
* indexes: used to generate queries,
* The fields and their location in the XML structure: fill in only the fields used in the application,
* links: if there are joins with the other tables of the base.

## Implementation {#implementation}

To create the corresponding schema, apply the following stages:

1. Edit the **[!UICONTROL Administration>Configuration>Data schemas]** node of the Adobe Campaign tree and click **[!UICONTROL New]** .
1. Select the **[!UICONTROL Access data from an existing table or an SQL view]** option and click **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Choose the table or the existing view:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adapt the schema content to suit your needs.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   The schema must be populated with the view="true" attribute on the `<srcSchema>` root element in order not to generate a table creation SQL script.

**Example** :

```
<srcSchema name="recipient" namespace="cus" view="true">
  <element name="recipient" sqltable="dbsrv.recipient">
    <key name="email">
      <keyfield xpath="@email"/>
    </key>   
    <attribute name="email" type="string" length="80" sqlname="email"/>
  </element>
</srcSchema>
```

## Accessing an external database {#accessing-an-external-database}

The **Federated Data Access - FDA** option give you access to the data stored in an external database.

The configuration to be carried on the schemas to access data in an external database is detailed in [this page](../../installation/using/creating-data-schema.md).

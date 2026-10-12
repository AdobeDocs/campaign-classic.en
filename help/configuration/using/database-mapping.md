---
product: campaign
title: Database mapping
description: Database mapping
feature: Configuration, Instance Settings
role: Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
TQID: 'https://experienceleague.adobe.com/d3oQ8zJVsjVdj9PZ30rQ8hEuern1l3ZlMAWrbymhnvs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---
# Database mapping{#database-mapping}

This page describes how to declare indexes on the fields of a schema.

As part of the transition from Campaign v7 to v8, the Campaign Classic documentation set has been streamlined and reorganized. Common features are now available exclusively in the Campaign v8 documentation set. To learn more about the SQL mapping of schemas, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}.

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}

## Indexed fields {#indexed-fields}

Indexes let you optimize the performance of the SQL queries used in the application.

An index is declared from the main element of the data schema.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Indexes obey the following rules:

* An index can reference one or more fields in the table
* An index can be unique (to avoid duplicates) in all of the fields if the **unique** attribute contains the value "true"
* The SQL name of the index is determined from the SQL name of the table and the name of the index

>[!NOTE]
>
>* As a standard, indexes are the first elements declared from the main element of the schema.
>
>* Indexes are created automatically during table mapping (standard or FDA).

**Example**:

* Adding an index to the email address and city:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* Adding a unique index to the "id" name field:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## Learn more

Browse the following links to learn more:

* [Get started with schemas](about-schema-reference.md)
* [Schema structure](schema-structure.md)
* [Key management](database-keys.md)
* [Link management](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"} (Campaign v8 documentation)

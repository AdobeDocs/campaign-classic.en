---
product: campaign
title: Database mapping
description: Database mapping
feature: Configuration, Instance Settings
role: Developer
exl-id: e05dcd81-bbca-4767-8da3-ea064f7f6c8e
---
# Link management {#links--relation-between-tables}

A link describes the association between one table and another.

Types of associations, also known as cardinalities, are listed below.

* Cardinality 1-1: one occurrence of the source table can have at most one corresponding occurrence of the target table.
* Cardinality 1-N: one occurrence of the source table can have several corresponding occurrences of the target table, but one occurrence of the target table can have at most one corresponding occurrence of the source table.
* Cardinality N-N: one occurrence of the source table can have several corresponding occurrences of the target table, and vice-versa.

In the use interface, cardinalities are represented with a specific icon.

For join relations with a campaign table/database:

* ![](assets/join_with_campaign11.png) : Cardinality 1-1. For example, between a recipient and a current order. A recipient can be related to only one occurrence of the current order table at a time. 
* ![](assets/externaljoin11.png) : Cardinality 1-1, external join. For example, between a recipient and their country. A recipient can be related to only one occurrence of the table country. The content of the country table will not be saved. 
* ![](assets/join_with_campaign1n.png) : Cardinality 1-N. For example, between a recipient and the subscriptions table. A recipient can be related to several occurrences on the subscriptions table.

For join relations using Federated Database Access (FDA):

* ![](assets/join_fda_11.png) : Cardinality 1-1
* ![](assets/join_fda_1m.png) : Cardinality 1-N

For more information on FDA tables, refer to [Accessing an external database](../../installation/using/about-fda.md).

A link must be declared in the schema containing the foreign key of the table linked via the main element:

```sql
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Links obey the following rules:

* The definition of a link is entered on a **link**-type **`<element>`** with the following attributes:

    * **name**: name of link from the source table
    * **target**: name of target schema
    * **label**: label of link
    * **revLink** (optional): name of reverse link from the target schema (deduced automatically by default)
    * **integrity** (optional): referential integrity of the occurrence of the source table to the occurrence of the target table. 
        Possible values are:

        * **define**: it is possible to delete the source occurrence if it is no longer referenced by a target occurrence
        * **normal**: deleting the source occurrence initializes the keys of the link to the target occurrence (default mode), this type of integrity initializes all foreign keys
        * **own**: deleting the source occurrence leads to the deletion of the target occurrence
        * **owncopy**: the same as **own** (in case of deletion) or duplicates the occurrences (in case of duplication)
        * **neutral**: no specific behavior

    * **revIntegrity** (optional): integrity on the target schema (optional, "normal" by default)
    * **revCardinality** (optional): with value "single" populates cardinality with type 1-1 (1-N by default)
    * **externalJoin** (optional): forces the outer join
    * **revExternalJoin** (optional): forces the outer join on the reverse link

* A link references one or more fields from the source table to the destination table. The fields making up the join ( `<join>`  element) need not be populated because they are automatically deduced by default using the internal key of the target schema.
* An index is automatically added to the foreign key of the link in the extended schema.
* A link consists of two half-links, where the first is declared from the source schema and the second is created automatically in the extended schema of the target schema.
* A join can be an outer join if the **externalJoin** attribute is added, with the value "true" (supported in PostgreSQL).

>[!NOTE]
>
>As a standard, links are the elements declared at the end of the schema.

## Example: reverse link {#example-1}

In the example below, we declare a 1-N relation to the "cus:company" schema table:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

The schema generated:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

The link definition is supplemented by the fields making up the join, i.e. the primary key with its XPath ("@id") in the destination schema, and the foreign key with its XPath ("@company-id") in the schema.

The foreign key is added automatically in an element that uses the same characteristics as the associated field in the destination table, with the following naming convention: name of target schema followed by name of associated field ("company-id" in our example).

Extended schema of the target ("cus:company"):

```sql
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

A reverse link to the "cus:recipient" table was added with the following parameters:

* **name**: automatically deduced from the name of the source schema (can be forced with the "revLink" attribute in the link definition on the source schema)
* **revLink**: name of reverse link
* **target**: key of linked schema ("cus:recipient" schema)
* **unbound**: the link is declared as a collection element for a 1-N cardinality (by default)
* **integrity**: "define" by default (can be forced with the "revIntegrity" attribute in the link definition on the source schema).

## Example: simple link {#example-2}

In this example, we declare a link towards the "nms:address" schema table. The join is an outer join and is populated explicitly with the recipient's email address and the "@address" field of the linked table ("nms:address").

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

## Example: unique cardinality {#example-3}

In this example, we create a 1-1 relation to the "cus:extension" schema table:

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

## Example: link to a folder {#example-4}

In this example, we declare a link to a folder ("xtk:folder" schema):

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

The default value returns the identifier of the first eligible parameter type file entered in the "DefaultFolder('nmsFolder')" function.

## Example: create a key on a link {#example-5}

In this example, we create a key on a link ("company" to "cus:company" schema) with the **xlink** attribute and a field of the ("email") table:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

The schema generated:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

The definition of the "companyEmail" name key was extended with the foreign key of the "company" link. This key generates a unique index on both fields.

## Learn more

Browse the following links to learn more:

* [Get started with schemas](about-schema-reference.md)
* [Schema structure](schema-structure.md)
* [Database mapping](database-mapping.md)
* [Key management](database-keys.md)
* [Campaign data model](about-data-model.md)

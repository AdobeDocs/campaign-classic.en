---
product: campaign
title: Database mapping
description: Database mapping
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 728b509f-2755-48df-8b12-449b7044e317
---
# Database mapping{#database-mapping}

The SQL mapping of the sample schema described [in this page](schema-structure.md) generates the following XML document:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient email address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

The root element of the schema changed to **`<srcschema>`** to **`<schema>`**.

This other type of document is generated automatically from the source schema, and simply referred to as the schema.

The SQL names are determined automatically based on element name and type.

The SQL naming rules are as follows:

* **table**: concatenation of the schema namespace and name

  In our example, the name of the table is entered via the main element of the schema in the **sqltable** attribute:

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **field**: name of the element preceded by a prefix defined according to type: 'i' for integer, 'd' for double, 's' for string, 'ts' for dates, etc.

  The field name is entered via the **sqlname** attribute for each typed **`<attribute>`** and **`<element>`**:

  ```sql
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>SQL names can be overloaded from the source schema. To do this, populate the "sqltable" or "sqlname" attributes on the element concerned.

The SQL script to create the table generated from the extended schema is as follows:

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

The SQL field constraints are as follows:

* no null values in numeric and date fields
* numeric fields are initialized to 0

## XML fields {#xml-fields}

By default, any  **`<attribute>`** and **`<element>`** -typed element is mapped onto an SQL field of the data schema table. You can, however, reference this field in XML instead of SQL, which means that the data is stored in a memo field ("mData") of the table containing the values of all XML fields. The storage of these data is an XML document that observes the schema structure.

To populate a field in XML, you must add the **xml** attribute with the value "true" to the element concerned.

**Example**: here are two examples of XML field use.

* Multi-line comment field:

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* Description of data in HTML format:

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  The "html" type lets you store the HTML content in a CDATA tag and display a special HTML edit check in the Adobe Campaign client interface.

Use XML fields to add new fields without modifying the physical structure of the database. Another advantage is that you use less resources (size allocated to SQL fields, limit on the number of fields per table, etc.). However, note that you cannot index or filter an XML field.

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
* [Link management](database-links.md)
* [Campaign datamodel](about-data-model.md)
---
product: campaign
title: Database mapping
description: Database mapping
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 728b509f-2755-48df-8b12-449b7044e317
---
# Database mapping{#database-mapping}

The SQL mapping of our example schema gives the following XML document:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient e-mail address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## Description {#description}

The root element of the schema is no longer **`<srcschema>`**, but **`<schema>`**.

This takes us to another type of document, which is generated automatically from the source schema, simply referred to as the schema. This schema will be used by the Adobe Campaign application.

The SQL names are determined automatically based on element name and type.

The SQL naming rules are as follows:

* table: concatenation of the schema namespace and name

  In our example, the name of the table is entered via the main element of the schema in the **sqltable** attribute:

  ```
  <element name="recipient" sqltable="CusRecipient">
  ```

* field: name of the element preceded by a prefix defined according to type ('i' for integer, 'd' for double, 's' for string, 'ts' for dates, etc.)

  The field name is entered via the **sqlname** attribute for each typed **`<attribute>`** and **`<element>`**:

  ```
  <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>SQL names can be overloaded from the source schema. To do this, populate the "sqltable" or "sqlname" attributes on the element concerned.

The SQL script to create the table generated from the extended schema is as follows:

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

The SQL field constraints are as follows:

* no null values in numeric and date fields,
* numeric fields are initialized to 0.

## XML fields {#xml-fields}

By default, any typed **`<attribute>`** and **`<element>`** element is mapped onto an SQL field of the data schema table. You can, however, reference this field in XML instead of SQL, which means that the data is stored in a memo field ("mData") of the table containing the values of all XML fields. The storage of these data is an XML document that observes the schema structure.

To populate a field in XML, you must add the **xml** attribute with the value "true" to the element concerned.

**Example**: here are two examples of XML field use.

* Multi-line comment field:

  ```
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* Description of data in HTML format:

  ```
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  The "html" type lets you store the HTML content in a CDATA tag and display a special HTML edit check in the Adobe Campaign client interface.

The use of XML fields lets you add fields without needing to modify the physical structure of the database. Another advantage is that you use less resources (size allocated to SQL fields, limit on the number of fields per table, etc.).

The main disadvantage is that it is impossible to index or filter an XML field.

## Indexed fields {#indexed-fields}

Indexes let you optimize the performance of the SQL queries used in the application.

An index is declared from the main element of the data schema.

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Indexes obey the following rules:

* An index can reference one or more fields in the table.
* An index can be unique (to avoid duplicates) in all of the fields if the **unique** attribute contains the value "true".
* The SQL name of the index is determined from the SQL name of the table and the name of the index.

>[!NOTE]
>
>As a standard, indexes are the first elements declared from the main element of the schema.

>[!NOTE]
>
>Indexes are created automatically during table mapping (standard or FDA).

**Example**:

* Adding an index to the e-mail address and city:

  ```
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* Adding a unique index to the "id" name field:

  ```
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
    </element>
  </srcSchema>
  ```

## Management of keys {#management-of-keys}

A table must have at least one key for identifying a record in the table.

A key is declared from the main element of the data schema.

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Keys obey the following rules:

* A key can reference one or more fields in the table.
* A key is known as 'primary' (or 'priority') when it is the first in the schema to be populated or if it contains the **internal** attribute with the value "true".
* A unique index is declared implicitly for each key definition. The creation of an index on the key can be prevented by adding the **noDbIndex** attribute with the value "true".

>[!NOTE]
>
>As a standard, keys are the elements declared from the main element of the schema after indexes have been defined.

>[!NOTE]
>
>Keys are created during table mapping (standard or FDA), Adobe Campaign finds unique indexes.

**Example**:

* Adding a key to the e-mail address and city:

  ```
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  The schema generated:

  ```
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
     <dbindex name="email" unique="true">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
     </dbindex>    
  
     <key name="email">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="location/@city"/>    
     </key>    
  
     <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* Adding a primary or internal key on the "id" name field:

  ```
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email" noDbIndex="true">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
    </element>
  </srcSchema>
  ```

  The schema generated:

  ```
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
      <key name="email">      
        <keyfield xpath="@email"/>    
      </key>    
  
      <dbindex name="id" unique="true">      
        <keyfield xpath="@id"/>    
      </dbindex>    
  
      <key internal="true" name="id">      
       <keyfield xpath="@id"/>    
      </key>    
  
      <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
      <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

### Auto-incremental key {#auto-incremental-key}

The primary key of most Adobe Campaign tables is a 32-bit long integer auto-generated by the database engine. The calculation of the key value depends on a sequence (by default, the **XtkNewId** SQL function) generating a number that is unique in the entire database. The content of the key is automatically entered on insertion of the record.

The advantage of an incremental key is that it provides a non-modifiable technical key for the joins between tables. In addition, this key does not occupy much memory because it uses a double-byte integer.

You can specify in the source schema the name of the sequence to be used with the **pkSequence** attribute. If this attribute is not given in the source schema, the **XtkNewId** default sequence will be used. The application uses dedicated sequences for the **nms:broadLog** and **nms:trackingLog** schemas (**NmsBroadLogId** and **NmsTrackingLogId** respectively) because these are the tables that contain the most records.

From ACC 18.10, **XtkNewId** is no more the default value for the sequence in the out-of-the-box schemas. You are now able to build schema or to extend existing schema with a dedicated sequence.

>[!IMPORTANT]
>
>When creating a new schema or during a schema extension, you need to keep the same primary key sequence value (@pkSequence) for the whole schema.

>[!NOTE]
>
>A sequence referenced in an Adobe Campaign schema (**NmsTrackingLogId** for example) must be associated to a SQL function that returns the number of IDs in the parameters, separated by commas. This function must be called **GetNew**XXX**Ids**, where **XXX** is the name of the sequence (**GetNewNmsTrackingLogIds** for example). View the **postgres-nms.sql**, **mssql-nms.sql** or **oracle-nms.sql** files provided with the appliation in the **datakit/nms/eng/sql/** directory to recover the example of a 'NmsTrackingLogId' sequence creation for each database engine.

To declare a unique key, populate the **autopk** attribute (with value "true") on the main element of the data schema.

**Example**:

Declaring an incremental key in the source schema:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

The schema generated:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

In addition to the definition of the key and its index, a numeric field called "id" has been added to the extended schema in order to contain the auto-generated primary key.

>[!IMPORTANT]
>
>A record with a primary key set to 0 is automatically inserted on creation of the table. This record is used to avoid outer joins, which are not effective on volume tables. By default, all foreign keys are initialized with value 0 so that a result can always be returned on the join when the data item is not populated.

## Links: relation between tables {#links--relation-between-tables}

A link describes the association between one table and another.

The various types of associations (known as "cardinalities") are as follows:

* Cardinality 1-1: one occurrence of the source table can have at most one corresponding occurrence of the target table.
* Cardinality 1-N: one occurrence of the source table can have several corresponding occurrences of the target table, but one occurrence of the target table can have at most one corresponding occurrence of the source table.
* Cardinality N-N: one occurrence of the source table can have several corresponding occurrences of the target table, and vice-versa.

In the interface, you can distinguish the different types of relations easily thanks to their icons.

For join relations with a campaign table/database:

* ![](assets/join_with_campaign11.png) : Cardinality 1-1. For example, between a recipient and a current order. A recipient can be related to only one occurrence of the current order table at a time. 
* ![](assets/externaljoin11.png) : Cardinality 1-1, external join. For example, between a recipient and their country. A recipient can be related to only one occurrence of the table country. The content of the country table will not be saved. 
* ![](assets/join_with_campaign1n.png) : Cardinality 1-N. For example, between a recipient and the subscriptions table. A recipient can be related to several occurences on the subscriptions table.

For join relations using Federated Database Access:

* ![](assets/join_fda_11.png) : Cardinality 1-1
* ![](assets/join_fda_1m.png) : Cardinality 1-N

For more information on FDA tables, refer to [Accessing an external database](../../installation/using/about-fda.md).

A link must be declared in the schema containing the foreign key of the table linked via the main element:

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Links obey the following rules:

* The definition of a link is entered on a **link**-type **`<element>`** with the following attributes:

    * **name**: name of link from the source table,
    * **target**: name of target schema,
    * **label**: label of link,
    * **revLink** (optional): name of reverse link from the target schema (deduced automatically by default),
    * **integrity** (optional): referential integrity of the occurrence of the source table to the occurrence of the target table. Possible values are as follows:

        * **define**: it is possible to delete the source occurrence if it is no longer referenced by a target occurrence,
        * **normal**: deleting the source occurrence initializes the keys of the link to the target occurrence (default mode), this type of integrity initializes all foreign keys,
        * **own**: deleting the source occurrence leads to the deletion of the target occurrence,
        * **owncopy**: the same as **own** (in case of deletion) or duplicates the occurrences (in case of duplication),
        * **neutral**: does nothing.

    * **revIntegrity** (optional): integrity on the target schema (optional, "normal" by default),
    * **revCardinality** (optional): with value "single" populates cardinality with type 1-1 (1-N by default).
    * **externalJoin** (optional): forces the outer join
    * **revExternalJoin** (optional): forces the outer join on the reverse link

* A link references one or more fields from the source table to the destination table. The fields making up the join ( `<join>`  element) need not be populated because they are automatically deduced by default using the internal key of the target schema.
* An index is automatically added to the foreign key of the link in the extended schema.
* A link consists of two half-links, where the first is declared from the source schema and the second is created automatically in the extended schema of the target schema.
* A join can be an outer join if the **externalJoin** attribute is added, with the value "true" (supported in PostgreSQL).

>[!NOTE]
>
>As a standard, links are the elements declared at the end of the schema.

### Example 1 {#example-1}

1-N relation to the "cus:company" schema table:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

The schema generated:

```
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

```
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

### Example 2 {#example-2}

In this example, we will declare a link towards the "nms:address" schema table. The join is an outer join and is populated explicitly with the recipient's e-mail address and the "@address" field of the linked table ("nms:address").

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

### Example 3 {#example-3}

1-1 relation to the "cus:extension" schema table:

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### Example 4 {#example-4}

Link to a folder ("xtk:folder" schema):

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

The default value returns the identifier of the first eligible parameter type file entered in the "DefaultFolder('nmsFolder')" function.

### Example 5 {#example-5}

In this example, we wish to create a key on a link ("company" to "cus:company" schema) with the **xlink** attribute and a field of the ("email") table:

```
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

```
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

    <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

The definition of the "companyEmail" name key was extended with the foreign key of the "company" link. This key generates a unique index on both fields.

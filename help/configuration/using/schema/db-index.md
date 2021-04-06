---
solution: Campaign Classic
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
---
# dbindex element {#dbindex--element}

## Content model {#content-model-3}

dbindex:==keyfield

## Attributes {#attributes-3}

* @_operation (string)
* @applicableIf (string)
* @label (string)
* @name (MNTOKEN)
* @unique (boolean)

## Parents {#parents-3}

`<element>`

## Children {#children-3}

`<keyfield>`

## Description {#description-3}

This element lets you define an index linked to a table.

## Use and context of use {#use-and-context-of-use-3}

It's possible to define several indexes. One index can reference one or more fields of the table. Index declaration usually follows the definition of the main schema element.

The order of the `<keyfield>` elements defined in a `<dbindex>` is very important. The first `<keyfield>` must be the indexation criterion which the queries are mainly based on.

The name of the index in the database is calculated by concatenating the name of the table and the name of the index. For example: Table name "Sample", Namespace "Cus", index name "MyIndex"-> name of the index field during index creation querying: "CusSample_myIndex".

## Attribute description {#attribute-description-3}

* **_operation (string)**: defines the type of writing in the database.

  This attribute is mainly used when extending out-of-the-box schemas.

  Accessible values are:

  * "none": reconciliation alone. This means that Adobe Campaign will recover the element without updating it or generating an error if it doesn't exist.
  * "insertOrUpdate": update with insertion. This means that Adobe Campaign will update the element or create it if it doesn't exist.
  * "insert": insertion. This means that Adobe Campaign will insert the element without checking whether it exists.
  * "update": update. This means that Adobe Campaign will update the element or generate an error if it doesn't exist.
  * "delete": deletion. This means that Adobe Campaign will recover and delete elements.

* **applicableIf (string)**: condition for taking the index into account - receives an XTK expression.
* **label (string)**: index label.
* **name (MNTOKEN)**: unique index name.
* **unique (boolean)**: if this option is activated (@unique="true"), the attribute guarantees the uniqueness of the index throughout its fields.

## Examples {#examples-3}

Creation of an index on the "id" field. (the "@unique" attribute on the `<dbindex>` element triggers adding of the "UNIQUE" SQL key word when the index is created in the database (query)).

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

Creation of a composite index on the "@mail" and "@phoneNumber" fields:

```    
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```

---
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
---
# key element {#key--element}

![](../../assets/v7-only.svg)

## Content model {#content-model-8}

key:==keyfield

## Attributes {#attributes-8}

* @allowEmptyPart (boolean)
* @applicableIf (string)
* @internal (boolean)
* @label (string)
* @name (MNTOKEN)
* @noDbIndex (boolean)

## Parents {#parents-8}

`<element>`

## Children {#children-8}

`<keyfield>`

## Description {#description-8}

This element lets you define a key for identifying a record in the table.

A table must have at least one key.

## Use and context of use {#use-and-context-of-use-6}

As a rule, keys are declared after the main element of the schema and the indexes.

A key is known as composite if it includes several fields (i.e. several `<keyfield>` children). Do not use a composite key to define a primary key.

If the main element of the schema contains the "@autopk=true" attribute, the primary key is unique. We can only have one primary key per schema.

The first 1000 identifiers are reserved, so if a range of values needs to be defined for keys, start at 1000.

## Attribute description {#attribute-description-8}

* **allowEmptyPart (boolean)**: in the case of a composite key, if this attribute is activated, they key is considered valid if at least one of its keys isn't empty. If this is the case, the empty notion value is "0" (boolean or for all types of numerical data). By default, all the keys that make up a composite key need to be entered.
* **applicableIf (string)**: this attribute lets you make the key optional. It defines the condition according to which the key definition will be applied. This attribute receives an XTK expression.
* **internal (boolean)**: if it is activated, this attribute lets Adobe Campaign know that the key is primary.
* **label (string)**: label of the key.
* **name (MNTOKEN)**: internal name of the key.
* **noDbIndex (boolean)**: if it is activated (noDbIndex="true"), the field matching the key will not be indexed.

## Examples {#examples-------}

Declaration of a composite key which authorizes either the "@expr" or the "alias" field to be empty:

```

<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Declaration of a primary key on the "Name" field of STRING type in an `<srcschema>`  and the matching SQL query:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

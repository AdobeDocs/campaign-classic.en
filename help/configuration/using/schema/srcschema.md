---
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
---
# srcschema element {#srcschema--element}

![](../../assets/v7-only.svg)

## Content model {#content-model-14}

srcSchema:==(attribute | createdBy | data | element | enumeration | help | interface | methods | modifiedBy)

## Attributes {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string), namespace (string), useRecycleBin (boolean), view (boolean), xtkschema (string)

## Parents {#parents-14}

None

## Children {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## Description {#description-14}

The `<srcschema>` is the root element of a schema. It is the input point for the definition of the schema.

## Use and context of use {#use-and-context-of-use-9}

Schema presentation is available in [About schema reference](../../../configuration/using/about-schema-reference.md) and [Schema structure](../../../configuration/using/schema-structure.md).

## Attribute description {#attribute-description-14}

* **created (datetime)**: this attribute provides information on the date and time of schema creation. It has a "Date Time" form. The values displayed are taken from the server. The time is shown in UTC format. 
* **createdBy-id (long)**: is the identifier of the operator who created the schema. 
* **desc (string)**: schema description
* **entitySchema (string)**: basic schema which syntax and approval are based on (by default for Adobe Campaign: xtk:srcSchema). When you save the current schema, Adobe Campaign will approve its grammar with the schema declared in the @xtkschema attribute.
* **extendedSchema (string)**: receives the name of the out-of-the-box schema which the current schema extension is based on. The form is "namespace:name". 
* **img (string)**: icon linked to the schema (may be defined in the schema creation wizard). 
* **label (string)**: schema label.
* **labelSingular (string)**: label (singular) for display in the interface. 
* **lastModified (datetime)**: this attribute provides information on the date and time of the last modification. It has a "Date Time" form. The values displayed are taken from the server. The time is shown in UTC format. 
* **library (boolean)**: use of the schema as a library and not an entity. This schema may therefore be referenced by other schemas thanks to the "@ref" and "@template" attributes.
* **mappingType (string)**:

    * "sql": database mapping
    * "textFile": text file mapping
    * "xmlFile": XML format text file mapping
    * "binaryFile": binary file mapping

* **modifiedBy-id (long)**: matches the identifier of the operator who changed the schema. 
* **name (string)**: unique schema name.
* **namespace (string)**: namespace of the schema (default: nms, xtk, nl). When creating a new schema for a project, we recommend that you use a dedicated namespace.
* **useRecycleBin (boolean)**: activates the trash feature in the application. Deleted records will be placed in the trash before final deletion. This function is only available in "Delivery" mode.
* **view (boolean)**: if it is activated (@view="true"), the schema will be used as a view. The database structure update wizard will not take the schema into account. This option is mainly used for referencing external tables.
* **xtkschema (string)**: name of the schema which defines schema grammar (xtk:srcSchema by default).

## Examples {#examples-11}

`<srcschema>` element of the "nms:delivery" out of the box schema

```

<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

---
solution: Campaign Classic
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
---
# enumeration element {#enumeration--element}

## Content model {#content-model-5}

enumeration:==(help| value)

## Attributes {#attributes-5}

* @basetype (string)
* @default (string)
* @desc (string)
* @label (string)
* @name (string)
* @template (string)

## Parents {#parents-5}

`<srcschema>`

## Children {#children-5}

* `<help>`
* `<value>`

## Description {#description-5}

This element enables us to define a value enumeration. An enumeration belongs to the schema which it is defined in, but it is accessible via another schema.

## Use and context of use {#use-and-context-of-use-4}

Enumerations are defined at the start of a schema (before the main element is defined).

## Attribute description {#attribute-description-5}

* **basetype (string)**: type of the values stored in the enumeration.

  List of available types:

    * ANY
    * bin
    * blob
    * boolean
    * byte
    * CDATA
    * datetime
    * datetimetz
    * datetimenotz
    * date
    * DOMDocument
    * DOMElement
    * double
    * enum
    * float
    * html
    * int64
    * link
    * long
    * memo
    * MNTOKEN
    * percent
    * primarykey
    * short
    * string
    * time
    * timespan
    * uuid

* **default (string)**: Default value. The default value may also be one of the values defined in the enumeration. 
* **desc (string)**: enumeration description. 
* **label (string)**: enumeration label.
* **name (string)**: internal name of the enumeration. 
* **template (string)**: this attribute defines a reference to an `<enumeration>` element shared by several schemas. The definition is automatically copied into the current schema.

## Examples {#examples-4}

Example of enumeration values whose values are stored in the database:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Definition of an enumeration with a default value:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

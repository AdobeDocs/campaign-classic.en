---
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
---
# join element {#join--element}

![](../../assets/v7-only.svg)

## Content model {#content-model-7}

join:==EMPTY

## Attributes {#attributes-7}

* @dstFilterExpr (string)
* @xpath-dst (string)
* @xpath-src (string)

## Parents {#parents-7}

`<element>`

## Children {#children-7}

None

## Description {#description-7}

Lets you define the fields that create a join between SQL tables.

## Use and context of use {#use-and-context-of-use-5}

A `<join>`  element can only be used if the parent  `<element>`  element is of 'link' type. This means that the parent element must have the "@type=link" attribute declared.

It is not necessary to specify the name and namespace of the remote table in the `<join>`  element. They need to be specified in the parent  `<element>`.

By convention, links are defined at the end of the schema.

If the `<join>` element isn't specified when the link type element is defined, the link will automatically be placed on the primary keys of both tables.

## Attribute description {#attribute-description-7}

* **dstFilterExpr (string)**: this attribute lets you restrict the number of eligible values in the remote table.
* **xpath-dst (string)**: this attribute receives an Xpath (@name attribute of the remote table).
* **xpath-src (string)**: this attribute receives an Xpath (@name attribute in the current schema).

## Examples {#examples-6}

Link between the 'email' field of the current table and the "@compagny-id" field of the remote table:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Filtered link towards the "cus:Country" table based on the content of the "@country" field which must contain the 'EN' value:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```

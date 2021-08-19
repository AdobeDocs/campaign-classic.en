---
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
---
# keyfield element {#keyfield--element}

![](../../assets/v7-only.svg)

## Content model {#content-model-9}

keyfield:==EMPTY

## Attributes {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Parents {#parents-9}

`<key>`  ,  `<dbindex />`

## Children {#children-9}

None

## Description {#description-9}

This element defines the fields to be integrated into an index or a key.

## Attribute description {#attribute-description-9}

* **xlink (MNTOKEN)**: lets you automatically reference foreign keys defined in the join for a relation table (N-N link).
* **xpath (MNTOKEN)**: definition of an index or a key on an `<attribute>`  element. This attribute receives an Xpath which defines the path to the schema attribute that defines the key or the index.

## Examples {#examples-}

Selection of the "sName" field in an index with an Xpath on "@name":

```
<keyfield xpath="@name"/>
```

---
product: campaign
title: Schema elements and attributes - keyfield element
description: keyfield element
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
TQID: 'https://experienceleague.adobe.com/tVWLlgg97dREZZHvUW81FhDVhS-uNvUHlbhH0YBrAdY'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
---
# keyfield element {#keyfield--element}


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

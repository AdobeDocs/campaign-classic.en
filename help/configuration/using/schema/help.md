---
product: campaign
title: Schema elements and attributes - help element
description: help element
feature: Schema Extension
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
TQID: 'https://experienceleague.adobe.com/R-Oa0H6l19qOU9KamHyVFrOWqBOw9uB2ISm2OYdQDrM'
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
# help element {#help--element}


## Content model {#content-model-6}

help:==EMPTY

## Attributes {#attributes-6}

None

## Parents {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />` 

## Children {#children-6}

None

## Description {#description-6}

This element lets you describe an `<element>`  or  `<attribute>`   element. It may only contain text, and is stored in XML in the database.

## Attribute description {#attribute-description-6}

This element has no attributes.

## Examples {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```

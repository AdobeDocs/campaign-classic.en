---
product: campaign
title: Schema elements and attributes - condition element
description: condition element
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
TQID: 'https://experienceleague.adobe.com/Jx8bLCt1UEqAZDm0cSuexx25js-e5xTsvkeSMzVCUHw'
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
# condition element {#condition--element}


## Content model {#content-model-2}

condition:==EMPTY

## Attributes {#attributes-2}

* @boolOperator (string)
* @enabledIf (string)
* @expr (string)

## Parents {#parents-2}

`<sysfilter>`

## Children {#children-2}

None

## Description {#description-2}

This element lets you define a filtering condition.

## Use and context of use {#use-and-context-of-use-2}

One `<sysfiler>`  element can contain several filtering conditions.

## Attribute description {#attribute-description-2}

* **boolOperator (string)**: if several `<conditions>` are defined within the same  `<sysfilter>` element, this attribute lets you combine them. By default, the logical link is between `<condition>` elements is "AND". The "@boolOperator" attribute lets you combine "OR" and "AND" type links.
* **enabledIf (string)**: condition activation test.
* **expr (string)**: an XTK expression.

## Examples {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

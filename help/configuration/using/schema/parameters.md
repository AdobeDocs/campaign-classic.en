---
product: campaign
title: Schema elements and attributes - parameters element
description: parameters element
feature: Schema Extension
exl-id: 54538c3e-3232-4bf7-a09c-dacf0f072be5
TQID: 'https://experienceleague.adobe.com/tZyI-rIbEifWdgcO80ni6lSHinH0IEeM8UrHFAUpnFs'
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
# parameters element {#parameters--element}


## Content model {#content-model-13}

parameters:==param

## Attributes {#attributes-13}

None

## Parents {#parents-13}

`<method>`

## Children {#children-13}

`<param>`

## Description {#description-13}

This element defines a group of `<parameter>`  elements.

## Use and context of use {#use-and-context-of-use-8}

This element is mandatory, even for a single `<param>` child element of the `<method>`  element.

## Attribute description {#attribute-description-13}

None

## Examples {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

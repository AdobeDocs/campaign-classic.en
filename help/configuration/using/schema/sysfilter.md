---
product: campaign
title: Elements and attributes - sysfilter element
description: Elements and attributes
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
TQID: 'https://experienceleague.adobe.com/hjsD-JSGBPnwyj1IsLDo-tUy-63apy0-6kT9vngaaQk'
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
# sysfilter element {#sysfilter--element}


## Content model {#content-model-15}

sysFilter:==condition

## Attributes {#attributes-15}

None

## Parents {#parents-15}

`<element>`

## Children {#children-15}

`<condition>`

## Description {#description-15}

This element lets you define a filter.

## Attribute description {#attribute-description-15}

This element has no attributes.

## Examples {#examples-12}

Definition of a filter with a condition on the @name attribute:

```

<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

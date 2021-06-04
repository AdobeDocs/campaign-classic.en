---
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
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

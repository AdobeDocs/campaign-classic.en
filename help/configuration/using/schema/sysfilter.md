---
solution: Campaign Classic
product: campaign
title: sysfilter element
description: sysfilter element in Campaign schemas
audience: configuration
content-type: reference
topic-tags: schema-reference
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

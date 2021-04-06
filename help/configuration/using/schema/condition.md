---
solution: Campaign Classic
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
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

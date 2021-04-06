---
solution: Campaign Classic
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 54538c3e-3232-4bf7-a09c-dacf0f072be5
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

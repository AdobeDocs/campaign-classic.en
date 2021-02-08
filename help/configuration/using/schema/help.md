---
solution: Campaign Classic
product: campaign
title: Help element
description: Campaign Help element
audience: configuration
content-type: reference
topic-tags: schema-reference
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

---
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
---
# value element {#value--element}

![](../../assets/v7-only.svg)

## Content model {#content-model-16}

value:==help

## Attributes {#attributes-16}

* @applicableIf (string)
* @desc (string)
* @enabledIf (string)
* @img (string)
* @label (string)
* @name (string)
* @value (string)

## Parents {#parents-16}

`<enumeration>`

## Children {#children-16}

`<help>`

## Description {#description-16}

This element lets you define the values stored in an enumeration.

## Attribute description {#attribute-description-16}

* **applicableIf (string)**: this attribute lets you make an enumeration value optional. It receives an XTK expression.
* **desc (string)**: description of the enumeration value.
* **enabledIf (string)**: condition for activating the enumeration value.
* **img (string)**: image linked to the enumeration in the "namespace:image_name" form. The image must be imported onto the application server. 
* **label (string)**: label of the enumeration value. 
* **name (string)**: internal name of the enumeration value. 
* **value (string)**: value of the enumeration value. The type of value is defined based on the type of enumeration. If the enumeration is of character string type, it may only contain character string type values.

## Examples {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```

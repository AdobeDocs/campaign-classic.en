---
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
---
# compute-string element {#compute-string--element}

## Content model {#content-model-1}

compute-string:==EMPTY

## Attributes {#attributes-1}

@expr

## Parents {#parents-1}

`<element>`

## Children {#children-1}

None

## Description {#description-1}

The `<compute-string>` element enables you to generate a string based on an XTK expression to display a "built" label in the interface based on several values.

## Use and context of use {#use-and-context-of-use-1}

When no `<compute-string>` is defined, a `<compute-string>` element is entered by default with the values of the primary key in the schema.

## Attribute description {#attribute-description-1}

* **expr (string)**: XTK and/or Xpath expression

## Examples {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Result of the string calculated on a recipient: "John Doe (john.doe@aol.com)":

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

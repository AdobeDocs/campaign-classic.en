---
product: campaign
title: Elements and attributes - compute-string element
description: compute-string element
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
TQID: 'https://experienceleague.adobe.com/vLSA9oDdBg-0sElc6QlusY-YviNyRU8Fq6yXRrFrN1g'
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

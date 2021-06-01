---
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
---
# param element {#param--element}

## Content model {#content-model-12}

param:==help

## Attributes {#attributes-12}

* @_operation (string)
* @desc (string)
* @enum (string)
* @inout (string)
* @label (string)
* @localizable (string)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (string)

## Parents {#parents-12}

`<parameters>`

## Children {#children-12}

`<help>`

## Description {#description-12}

This element lets you define a parameter for calling up a SOAP method.

## Attribute description {#attribute-description-12}

* **desc (string)**: description which concerns the `<param>` element.
* **inout (string)**: this attribute defines whether or not the parameter is at the input (in) or output (out) of the SOAP call. If this attribute isn't specified, the default parameter is input ("@inout=in").
* **label (string)**: `<param>` label 
* **localizable (string)**: if it is activated, this attribute tells the collection tool to recover the value of the "@label" attribute for translation (internal use).
* **name (MNTOKEN)**: internal name of the `<param>` 
* **type (string)**: this attribute defines the type of `<param>` element

  List of available types:

    * ANY
    * bin
    * blob
    * boolean
    * byte
    * CDATA
    * datetime
    * datetimetz
    * datetimenotz
    * date
    * DOMDocument
    * DOMElement
    * double
    * enum
    * float
    * html
    * int64
    * link
    * long
    * memo
    * MNTOKEN
    * percent
    * primarykey
    * short
    * string
    * time
    * timespan
    * uuid

## Examples {#examples-9}

Definition of the "serviceName" inbound setting of character string type:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

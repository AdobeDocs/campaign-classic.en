---
product: campaign
title: Elements and attributes
description: Elements and attributes
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
---
# method element {#method--element}

![](../../assets/v7-only.svg)

## Content model {#content-model-10}

method:==( help | parameters)

## Attributes {#attributes-10}

* @_operation (string)
* @access (string)
* @const (boolean)
* @hidden (boolean)
* @label (string)
* @library (string)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolean)

## Parents {#parents-10}

`<methods>`  ,  `<interface />`

## Children {#children-10}

* `<help>`
* `<parameters>`

## Description {#description-10}

This element lets you define a SOAP method.

## Use and context of use {#use-and-context-of-use-7}

SOAP methods enable application processes.

The "@library" is necessary for declaring a new method (non-native): the namespace and the name used for the library are independent from the namespace and name of the schema where the declaration is.

## Attribute description {#attribute-description-10}

* **access (string)**: this attribute defines access control for using the method. If this attribute is missing, identification is mandatory. Available values are: 'anonymous', 'admin' and 'sql'. 
* **const (boolean)**: if it is activated, this attribute means that the declared method will alter the entity
* **label (string)**: label of the method.
* **library (string)**: this method isn't native to the application. This attribute takes the value of the method library where the method definition is found (nms:mylibrary.js).
* **name (MNTOKEN)**: unique method name.
* **static (boolean)**: if this attribute is activated, the method is considered to be autonomous, all parameters must be specified to the method when it is called up.

## Examples {#examples-7}

Definition of the "Subscribe" out of the box method:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>

```

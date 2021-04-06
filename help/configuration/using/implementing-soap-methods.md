---
solution: Campaign Classic
product: campaign
title: Implementing SOAP methods
description: Implementing SOAP methods
audience: configuration
content-type: reference
topic-tags: api
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
---
# Implementing SOAP methods{#implementing-soap-methods}

## Introduction {#introduction}

It is possible to create SOAP methods in JavaScript. This function simply enables applicative processes, it can avoid developing JSPs and their calling in the forms.

These SOAP methods behave in the same way as those defined natively in the application. The same attributes are supported: static, key only and const.

## Defining a method library {#defining-a-method-library}

Creating a method library involves two stages:

* The SOAP method declaration,
* Definition (or implementation) in JavaScript.

### Declaration {#declaration}

Start by declaring the methods in the schemas (for more on how to create and edit schemas, refer to [this section](../../configuration/using/about-schema-edition.md)).

Their declaration is similar to that of native methods, except that you need to add the 'library' attribute specifying the name of the method library where the definition is located.

This name coincides with the name (with the namespace) of the 'JavaScript Code' type entity.

Example:

The testLog(msg) method is declared in an nms:recipient extension

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>

```

>[!NOTE]
>
>The namespace and the name used for the library are independent from the namespace and schema name where the declaration is found.

### Definition {#definition}

SOAP methods are implemented in the form of JavaScript function grouped in a script representing a library.

>[!NOTE]
>
>A method library can group functions for various schemas or vice versa, the functions of one schema can be defined in separate libraries.

The script can contain code to be executed during initial library loading.

**1. Name**

The name of the function must comply with the following format:

```

 <schema-namespace>_<schema-name>_<method-name>

```

Example:

The following JavaScript function is the implementation of the method described above. It shall be defined in the 'JavaScript Code' type entity using the 'cus:test' name.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Signature**

The function's signature must include an argument for each 'in' or 'inout' parameter of the declaration.

Specific cases:

* **non-static methods**: the function must include an additional argument first, coinciding with the XML entity passed in the form of an 'xml' (E4X) type object.
* **"key only" type methods**: the function must include an additional argument first, coinciding with the key passed in the form of character strings.

**3. Returned values**

The function must return a value for each 'out' or 'inout' type parameter. Specific case: If the method is declared without any of the 'static', 'key only' or 'const' attributes, the first returned value must coincide with the modified entity. It is possible to return a new object or to return the first modified parameter.

For example:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

When several values are to be returned, they must be displayed in a table.

Example:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

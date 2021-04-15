---
solution: Campaign Classic
product: campaign
title: SOAP methods in JavaScript
description: SOAP methods in JavaScript
audience: configuration
content-type: reference
topic-tags: api
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
---
# SOAP methods in JavaScript{#soap-methods-in-javascript}

This is the JavaScript executed on the Adobe Campaign server.

## Static methods {#static-methods}

Static SOAP methods are accessed by invoking a method on the object representing the schema. Schemas are properties of 'namespace' objects. These namespaces are global variables, thus, for example, xtk or nms variables represent the corresponding namespaces

The following example invokes the static PostEvent method of the xtk:workflow schema:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 

```

## Non-static methods {#non-static-methods}

To use non-static SOAP methods, it is necessary first to retrieve an entity using the "get" or "create" methods on the corresponding schemas.

The following example invokes the ExecuteQuery method of the "xtk:queryDef" schema:

```
var query = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
    </select>
  </queryDef>
)

var res = query.ExecuteQuery()

for each (var w in res.workflow) 
  logInfo(w.@internalName)

```

## Examples {#examples}

* Query on the recipient table with a "get" operation:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="get">    
      <select>      
        <node expr="@firstName"/>      
        <node expr="@lastName"/>      
        <node expr="@email"/>    
      </select>    
      <where>      
        <condition expr="@email = 'peter.martinez@adobe.com'"/>    
      </where>  
    </queryDef>)
  
  var recipient = query.ExecuteQuery()
  
  logInfo(recipient.@firstName)
  logInfo(recipient.@lastName)
  
  ```

* Query on the recipient table with a "select" operation:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="select">    
      <select>      
        <node expr="@email"/>      
        <node expr="@lastName"/>      
        <node expr="@firstName"/>    
      </select>    
      <where>      
        <condition expr="@age > 25"/>    
      </where>    
    </queryDef>)
  
  var res = query.ExecuteQuery()
  
  for each (var recipient in res.recipient) 
  {  
    logInfo(recipient.@email)  
    logInfo(recipient.@firstName)  
    logInfo(recipient.@lastName)
  }
  ```

* Writing data to the recipient table:

  ```
  xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
  ```

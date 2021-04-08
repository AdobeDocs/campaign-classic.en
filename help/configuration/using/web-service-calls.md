---
solution: Campaign Classic
product: campaign
title: Web service calls
description: Web service calls
audience: configuration
content-type: reference
topic-tags: api
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
---
# Web service calls{#web-service-calls}

## General information {#general-information}

All API methods are presented in the form of Web services. This enables you to manage all Adobe Campaign functions via SOAP calls, which are the native entry point of the Adobe Campaign application server. The Adobe Campaign console itself only uses SOAP calls.

Web services let you create many applications from a third-party system:

* Synchronous alerts, notification, and real-time delivery template execution from a back office or transaction system,
* Development of special interfaces with simplified functionality (Web interfaces, etc.),
* Feeding and lookup of data in the database while observing trade rules and remaining isolated from the underlying physical model.

## Definition of Web services {#definition-of-web-services}

The definition of the Web services implemented on the Adobe Campaign application server is available from the data schemas.

A Web service is described in the grammar of the data schemas and is available from the **`<methods>`** element.

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>

```

Here we have an example of the definition of the method called **GenerateForm**.

The description of the service starts with the `<method>` element. The list of parameters of the method is completed from the  `<parameters>` element. Each parameter is specified by a name, a type (Boolean, string, DOMElement, etc.) and a description. The "inout" attribute with the "out" value lets you specify that the "result" parameter is at the SOAP call output.

The presence of the "static" attribute (with the value "true") describes this method as static, which means that all parameters of the method must be declared.

A "const" method implicitly has an XML document in the format of its associated schema as its input.

A full description of the `<method>` element of an Adobe Campaign schema is available in the "Schema references" chapter under [Method](../../configuration/using/schema/method.md)

Example of the "const"-type "ExecuteQuery" method from the "xtk:queryDef" schema:

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>

```

The input parameter of this method is an XML document in the format of the "xtk:queryDef" schema.

## Web service description: WSDL {#web-service-description--wsdl}

A WSDL (Web Service Description Library) file is available for each service. This XML file uses a metalanguage to describe the service and to specify the available methods, parameters, and the server to contact for executing the service.

### WSDL file generation {#wsdl-file-generation}

To generate a WSDL file, you must enter the following URL from a Web browser:

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

With:

* **`<server>`**: the Adobe Campaign application server (nlserver web)
* **`<schema>`**: schema identification key (namespace:schema_name)

### Example on the 'ExecuteQuery' method of schema 'xtk:queryDef' {#example-on-the--executequery--method-of-schema--xtk-querydef-}

The WSDL file is generated from the URL:

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

A WSDL description starts by defining the types used to form messages, associated in "ports", connected to a protocol by "bindings" forming Web services.

#### Types {#types}

Type definitions are based on XML schemas. In our example, the "ExecuteQuery" method takes an "s:string" string and an XML document (`<s:complextype>`) as parameters. The return value of the method ("ExecuteQueryResponse") is an XML document (  `<s:complextype>`).

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>

```

#### Messages {#messages}

The `<message>` describes the names and types of a set of fields to be sent. The method uses two messages to pass as a parameter ("ExecuteQueryIn") and the return value ("ExecuteQueryOut").

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 

```

#### PortType {#porttype}

The `<porttype>` associates the messages on the "ExecuteQuery" operation triggered by the query ("input") generating a response ("output").

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>

```

#### Binding {#binding}

The `<binding>` part specifies the SOAP communication protocol ( `<soap:binding>` ), data transport in HTTP (value of the "transport" attribute) and the data format for the "ExecuteQuery" operation. The body of the SOAP envelope contains the message segments directly without transformation. 

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>

```

#### Service {#service}

The `<service>` part describes the "XtkQueryDef" service with its URI on the URL of the Adobe Campaign application server.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>

```

## Connectivity {#connectivity}

Adobe Campaign has increased security for authentication mechanisms by introducing [security zones](../../installation/using/security-zones.md) and session management settings.

There are two authentication modes available:

* **via a call to logon method()**. This mode generates a session token and a security token. It is the most secure mode and therefore the most recommended.

or

* **via the Adobe Campaign login + password** that creates a session token. The session token automatically expires after a set period. This mode is not recommended and requires reducing the application security settings for some zone settings (allowUserPassword="true" and sessionTokenOnly="true").

### Session token characteristics {#session-token-characteristics}

The session token has the following characteristics:

* a X hour life cycle (the life cycle is configurable in the 'serverConf.xml' file, the default period is 24 hours)
* a random construction (it no longer contains the user login and password)
* when accessed via the Web:

    * the session token becomes a permanent token, it is not destroyed once the browser closes
    * it is placed in an HTTP-ONLY cookie (cookies must be activated for operators)

### Security token characteristics {#security-token-characteristics}

The security token has the following characteristics:

* it is generated from the session token
* it has a 24 hour life cycle (configurable in the 'serverConf.xml' file, the default period is 24 hours)
* it is stored in the Adobe Campaign console
* when accessed via the Web:

    * it is stored in a document.__securityToken property
    * the page URLs are updated to update the security token
    * the forms are also updated via a hidden field containing the token

#### Security token movement {#security-token-movement}

When accessed via console, it is:

* transmitted in the logon response (in the HTTP header)
* used in each query (in the HTTP header)

From a POST and GET HTTP:

* the server completes the links with the token
* the server adds a hidden field to forms

From an SOAP call:

* it is added to call headers

### Call examples {#call-examples}

* Using **HttpSoapConnection/SoapService**:

```
  
    var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
  var session = new SoapService(cnx, 'urn:xtk:session');
  session.addMethod("Logon", "xtk:session#Logon",
                      ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                      ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
  
  var res = session.Logon("", "admin", "pwd", <param/>);
  var sessionToken = res[0];
  var securityToken = res[2];
  
  cnx.addTokens(sessionToken, securityToken);
  var query = new SoapService(cnx, 'urn:xtk:queryDef');
  query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                      ["sessiontoken", "string", "entity", "NLElement"],
                      ["res", "NLElement"]);
  
  var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@email = 'joe.doe@aol.com'"/>
            </where>
          </queryDef>);
  logInfo(queryRes[0].toXMLString())

```

* Using **HttpServletRequest**:

>[!NOTE]
>
>The URLs used in the following **HttpServletRequest** calls need to be on allowed list in the url permissions section of the **serverConf.xml** file. This is also true for the URL of the server itself.

Logon execution():

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
    '<soapenv:Header/>' +
    '<soapenv:Body>' +
        '<urn:Logon>' +
            '<urn:sessiontoken></urn:sessiontoken>' +
            '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
            '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
            '<urn:elemParameters></urn:elemParameters>' +
        '</urn:Logon>' +
    '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
           
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

Query execution:

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
             '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
                '<queryDef operation="select" schema="nms:recipient">' +
                  '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                  '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
                '</queryDef>' +
           '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```

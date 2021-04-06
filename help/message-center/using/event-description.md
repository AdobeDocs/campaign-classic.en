---
solution: Campaign Classic
product: campaign
title: Message center event description
description: Learn more about transactional messaging event
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: 9f7f4b6c-2ee8-4091-847d-f616d6abeb6b
---
# Event description{#event-description}

## About the transactional messaging data model {#about-transactional-messaging-datamodel}

Transactional messaging relies on the Adobe Campaign data model, and uses two additional separate tables. These [tables](../../configuration/using/data-model-description.md#message-center-module), **NmsRtEvent** and **NmsBatchEvent**, contain the same fields and let you manage real time events on the one hand and batch events on the other.

## SOAP methods {#soap-methods}

This section details the SOAP methods associated with the transactional messages module schemas.

Two **PushEvent** or **PushEvents** SOAP methods are linked to the two **nms:rtEvent** and **nms:BatchEvent** dataschemas. It is the information system that determines whether an event is a "batch" or "real time" type.

* **PushEvent** lets you insert a single event into the message,
* **PushEvents** lets you insert a series of events into the message.

The WSDL path for accessing both methods is:

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent** to access the real-time type schema.
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent** to access the batch type schema.

Both methods contain an **`<urn:sessiontoken>`** element for logging on to the transactional messaging module. We recommend using an identification method via trusted IP addresses. To retrieve the session token, perform a logon SOAP call, then a get token followed by a logoff. Use the same token for several RT calls. The examples included in this section are using the session token method which is the recommended one.

In case you're using a loadbalanced server, you can use the User/Password authentication (at the level of the RT message). Example:

```
<PushEvent xmlns="urn:nms:rtEvent">
<sessiontoken>mc/PASSWORD</sessiontoken>
<domEvent>
<rtEvent wishedChannel="41" type="rt_MobileJourney_iOS_Push" registrationToken="c3ddc8aaecc24822df25d0f49865cca61ea3f86c61bfa53ae4d37294e37f4a1c" hashlpId="27EE7571EC14DBA23B9B5CC0EF79BB782DAECF4C03C88E5D92CC9B9DAC4E5DDA" correlationId="415b7593-4f6f-e911-811f-00505691247c" xmlns="">
<mobileApp uuid="236B24DC-C073-412F-8BCB-AC7207096258" _operation="none"/>
<ctx>...</ctx>
</rtEvent>
</domEvent>
</PushEvent>
```

The **PushEvent** method is made up of a **`<urn:domevent>`** parameter which contains the event.

The **PushEvents** method is made up of a **`<urn:domeventcollection>`** parameter which contains events.

Example using PushEvent:

```
<urn:PushEvent>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEvent>
 
   <rtEvent>
   
   ...
   
   </rtEvent>
 
 </urn:domEvent>

</urn:PushEvent>
```

>[!NOTE]
>
>In case of a call to the **PushEvents** method, we need to add a parent XML element to comply with standard XML. This XML element will frame the various **`<rtevent>`** elements contained in the event.

Example using PushEvents:

```
<urn:PushEvents>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEventCollection>
 
   <Events>
   
     <rtEvent>... </rtEvent>
     
     <rtEvent>... </rtEvent>
     
     ...
   
   </Events>
 
 </urn:domEventCollection>

</urn:PushEvents>
```

The **`<rtevent>`** and **`<batchevent>`** elements have a set of attributes as well as a mandatory child element: **`<ctx>`** for integrating message data.

>[!NOTE]
>
>The **`<batchevent>`** element lets you add the event to the "batch" queue. The **`<rtevent>`** adds the event to the "real time" queue.

The mandatory attributes of the **`<rtevent>`** and **`<batchevent>`** elements are @type and @email. The value of @type must be the same as the itemized list value defined when configuring the execution instance. This value lets you define the template to be linked to the content of the event during the delivery.

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

In this example, two channels are provided: the email address and the mobile phone number. The **wishedChannel** lets you select the channel you wish to use when transforming the event into a message. The "0" value corresponds to the email channel, the "1" value to the mobile channel, etc.

If you wish to postpone an event delivery, add the **[!UICONTROL scheduled]** field followed by the preferred date. The event will be transformed into a message on this date.

We recommend filling in the @wishedChannel and @emailFormat attributes with numeric values. The function table which links numeric values and labels is found in the data schema description.

>[!NOTE]
>
>A detailed description of all authorized attributes as well as their values is available in the description of the **nms:rtEvent** and **nms:BatchEvent** dataschema.

The **`<ctx>`** element contains the message data. Its XML content is open, which means it can be configured depending on the content to be delivered.

>[!NOTE]
>
>It is important to optimize the number and size of XML nodes contained in the message to avoid overloading the servers during delivery.

Data example:

```
   <ctx>
               <client>
                        <firstname>John</firstname>
                        <lastname>Doe</lastname>
               </client>
               <action>
                         <type>Order confirmation</type>
                          <number>CN23453</number>
               </action>
               <orderdetails>
                          <article num="1">
                                   <name>Generic USB key</name>
                                   <price>20</price>
                           </article>
               </orderdetails>
    </ctx>
```

## Information returned by the SOAP call {#information-returned-by-the-soap-call}

When it receives an event, Adobe Campaign generates a unique return ID. This is the ID of the archived version of the event.

>[!IMPORTANT]
>
>When receiving SOAP calls, Adobe Campaign verifies the email address format. If an email address is incorrectly formatted, an error is returned.

* Example of an identifier returned by the method when event processing is successful:

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
           <plId xsi:type="xsd:long">72057594037935966</plId>
        </urn:PushEventResponse>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>

  ```

If the value of the return identifier is strictly greater than zero, this means the event has been successfully archived in Adobe Campaign.

However, if the event fails to be processed, the method returns an error message or a value equal to zero.

* Processing example of an event that failed when the query does not contain a login or the specified operator doesn't have the required rights:

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <SOAP-ENV:Fault>
           <faultcode>SOAP-ENV:Client</faultcode>
           <faultstring xsi:type="xsd:string">Error while reading parameters of method 'PushEvent' of service 'nms:rtEvent'.</faultstring>
           <detail xsi:type="xsd:string">Invalid login or password. Connection denied.</detail>
        </SOAP-ENV:Fault>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Example of an event that failed due to an error in the query (the XML classification isn't complied with):

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <SOAP-ENV:Fault>
           <faultcode>SOAP-ENV:Client</faultcode>
           <faultstring xsi:type="xsd:string">The XML SOAP message is invalid (service 'PushEvent', method 'nms:rtEvent').</faultstring>
           <detail xsi:type="xsd:string"><![CDATA[(16:8) : Expected end of tag 'rtevent'
  Error while parsing XML string '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
     <soapenv:Header/>
     <soapenv:Body>
        <urn:PushEvent>
           <urn:sessiontoken>mc/</urn:sessiontoken>
           <urn:domEvent>
  <rtevent type="create_account" email="esther.hall@adobe.com" origin="eCommerce" wishedChannel="email" 
        externalId="1596" language="english" country="EN" emailFormat="2"
        mobilePhone="+447700123123">
    <ctx>
     <website name="eCommerce" url="http://www.eCo']]></detail>
        </SOAP-ENV:Fault>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Example of an event that failed and returned a zero identifier (wrong method name):

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">0</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

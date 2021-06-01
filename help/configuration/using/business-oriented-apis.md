---
product: campaign
title: Business oriented APIs
description: Business oriented APIs
audience: configuration
content-type: reference
topic-tags: api
exl-id: e6638870-3141-4f12-b904-db436127c0d1
---
# Business oriented APIs{#business-oriented-apis}

Business API are specific to each type of object. They have an effect on:

* Deliveries:

    * Creating a delivery action, refer to [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
    * sending a campaign (start, pause, stop, send proof),
    * recovering delivery logs.

* Workflows:

    * starting a workflow,
    * verifying processes, etc.

      Refer to [SOAP methods in JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Content management
* Subscription management, refer to [Subscribe (nms:subscription)](#subscribe--nms-subscription-) and [Unsubscribe (nms:subscription)](#unsubscribe--nms-subscription-).
* Data processes: imports, exports.

This section details the use of the "Subscribe", "Unsubscribe" and "SubmitDelivery" services.

>[!IMPORTANT]
>
>[Campaign JSAPI documentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) contains additional information on SOAP calls and using Javascript in Adobe Campaign, as well as a full reference to all methods and functions used in the application.

## Subscribe (nms:subscription) {#subscribe--nms-subscription-}

This service lets you subscribe a recipient to an information service and update the recipient profile.

The following parameters are required in order to call the service:

* an authentication,
* internal name of the subscription service,
* an XML document containing the recipient information (from the "nms:recipient" schema),
* a Boolean for recipient creation if there isn't already one.

Description of the "subscribe" method in the "nms:subscription" schema:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>

```

The definition of the reconciliation key must be entered via the _**key** attribute on the `<recipient>` element of the XML document. The content of this attribute is a comma-separated XPath list.

This call does not return any data, except errors.

### Examples {#examples}

Subscription with recipient reconciliation key on the e-mail address: the input XML document must reference the email address and the definition of the key on this field.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Updating the recipient as well as the subscription.

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### Example of SOAP messages {#example-of-soap-messages}

* Query:

  ```
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <m:Subscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <sessiontoken xsi:type='xsd:string'/>
        <service xsi:type='xsd:string'>SVC1</service>
        <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <recipient _key="@email" email= "john.doe@adobe.com/>
        </content>
        <create xsi:type='xsd:boolean'>true</create>
      </m:Subscribe>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  
  ```

* Response:

  ```
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
      </m:SubscribeResponse>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  
  ```

## Unsubscribe (nms:subscription) {#unsubscribe--nms-subscription-}

This service lets you unsubscribe a recipient from an information service and update the recipient profile.

The following parameters are required in order to call the service:

* an authentication,
* Internal name of the service to unsubscribe from,
* an XML document containing the recipient information (from the "nms:recipient" schema),

Description of the "Unsubscribe" method in the "nms:subscription" schema:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>

```

The definition of the reconciliation key must be entered via the _key attribute on the `<recipient>` element of the XML document. The content of this attribute is a comma-separated XPath list.

If the recipient is not present in the database or is not subscribed to the concerned information service, the service performs no action and does not generate an error.

>[!NOTE]
>
>If the service name is not specified as a parameter, the recipient is then automatically on denylist(@blackList="1").

This call does not return any data, except errors.

### Example of SOAP messages {#example-of-soap-messages-1}

Query:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:Unsubscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    <sessiontoken xsi:type='xsd:string'/>
    <service xsi:type='xsd:string'>SVC1</service>
    <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
      <recipient _key="@email" email= "john.doe@adobe.com/>
    </content>
  </m:Unsubscribe>
</SOAP-ENV:Body>

```

Response:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

```

## SubmitDelivery (nms:delivery) {#submitdelivery--nms-delivery-}

This service lets you create and submit a delivery action.

The following parameters are required in order to call the service:

* an authentication,
* internal name of the delivery template,
* an optional XML document containing additional delivery data.

This API should not be called in volume as you may encounter of performance issues.

Description of the method in its schema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>

```

A delivery template must be created from the Adobe Campaign client console. It contains the parameters common to all deliveries (sender address or duration of validity of the message).

The input XML document is a delivery template fragment that obeys the structure of the "nms:delivery" schema. It will contain all additional data that could not be defined statically in the delivery template (e.g., list of recipients to target).

This call does not return any data, except errors.

### XML document example {#xml-document-example}

This example is based on a custom delivery template from an external data source (a file in this case). The configuration is fully described in the delivery template, so all that remains to be sent when the call occurs is the content of the file from the `<externalsource>` element.

```
<delivery>
  <targets fromExternalSource="true">
    <externalSource>
      MsgId|ClientId|Title|Name|FirstName| Mobile|Email| Market_segment|Product_affinity1 |Product_affinity2|Product_affinity3| Product_affinity4| Support_Number|Amount|Threshold1|000001234|M.| Doe|John|0650201020| john.doe@adobe.com
|1| A1|A2|A3|A4|E12|120000|100000
    </externalSource>
  </target>
</delivery>

```

If you do not have a delivery template, you can use the following sample:

```
<delivery>
<targets fromExternalSource="true" targetMode="1" noReconciliation="true" addressField="Email" >  
    <fileFormat active="true">  
      <source format="text" type="text">  
        <dataSourceConfig >  
          <dataSourceColumn label="Email" name="Email" type="string"/>  
        </dataSourceConfig>  
      </source>  
      <destination type="xtkDataStore"/>  
    </fileFormat>  
    <externalSource><![CDATA[not-a-repicipient@domain.com]]></externalSource>  
  </targets> 
</delivery> 
```

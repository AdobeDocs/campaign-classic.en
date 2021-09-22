---
product: campaign
title: Integration via SOAP (server side)
description: Integration via SOAP (server side)
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
---
# Integration via SOAP (server-side){#integration-via-soap-server-side}

![](../../assets/v7-only.svg)

The SOAP web services provided for offer management are different from those usually used in Adobe Campaign. They can be accessed via the interaction URL described in the previous section and let you present or update offers for a given contact.

## Offer proposition {#offer-proposition}

For an offer proposition via SOAP, add the **nms:proposition#Propose** command followed by the following parameters:

* **targetId**: primary key of the recipient (can be a composite key). 
* **maxCount**: specifies the number of offer propositions for the contact.
* **context**: lets you add context information in the space schema. If the schema used is **nms:interaction**, **`<empty>`** should be added.
* **categories**: specifies the category/ies that the offers must belong to.
* **themes**: specifies the theme(s) that the offer(s) must belong to.
* **uuid**: value of the Adobe Campaign permanent cookie ("uuid230").
* **nli**: value of the Adobe Campaign session cookie ("nlid").
* **noProp**: use the "true" value to deactivate proposal insertion.

>[!NOTE]
>
>The **targetId** and **maxCount** settings are compulsory. The others are optional.

In response to the query, the SOAP service will return the following parameters:

* **interactionId**: ID of the interaction.
* **propositions**: XML element, contains the list of propositions, each with their own ID and HTML representation.

## Offer update {#offer-update}

Add the **nms:interaction#UpdateStatus** command to the URL, followed by these parameters:

* **proposition**: string of characters, it contains the proposition ID given as an output during an offer proposition. Refer to [Offer proposition](#offer-proposition).
* **status**: string type, it specifies the new status of the offer. The possible values are listed in the **propositionStatus** enumeration, in the **nms:common** schema. For example, out-of-the-box, the number 3 corresponds to the **Accepted** status.
* **context**: XML element, lets you add context information in the space schema. If the schema used is **nms:interaction**, **`<empty>`** should be added.

## Example using a SOAP call {#example-using-a-soap-call}

Here is an example of code for a SOAP call:

```
<%
  var space = request.parameters.sp
  var cnx = new HttpSoapConnection(
    "https://" + request.serverName + ":" + request.serverPort + "/interaction/" + env + "/" + space,
    "utf-8",
    HttpSoapConnection.SOAP_12)
  var session = new SoapService(cnx, "nms:interaction")
  var action = request.parameters.a
  if( action == undefined )
    action = 'propose'

  try
  {
    switch( action )
    {
    case "update":
      var proposition = request.parameters.p
      var status      = request.parameters.st
      session.addMethod("UpdateStatus", "nms:interaction#UpdateStatus",
       ["proposition", "string",
        "status",      "string",
        "context",     "NLElement"],
       [])
      session.UpdateStatus(proposition, status, <undef/>)
      var redirect = request.parameters.r
      if( redirect != undefined )
        response.sendRedirect(redirect)
      break;

    case "propose":
      var count = request.parameters.n
      var target = request.parameters.t
      var categorie = request.parameters.c
      var theme = request.parameters.th
      var layout = request.parameters.l
      if( count == undefined )
        count = 1
      session.addMethod("Propose", "nms:proposition#Propose",
       ["targetId",      "string",
        "maxCount",      "string",
         "categories",    "string",
         "themes",        "string",
        "context",       "NLElement"],
       ["interactionId", "string",
        "propositions",  "NLElement"])
      response.setContentType("text/html")
      var result = session.Propose(target, count, category, theme, <empty/>)
      var props = result[1]
  %><table><tr><%
      for each( var propHtml in props.proposition.*.mdSource )
      {
        %><td><%=propHtml%></td><%
      }
  %></tr></table><%
      break;
    }
  }
  catch( e )
  {
  }
  %>
```

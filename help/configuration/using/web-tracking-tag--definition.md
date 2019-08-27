---
title: "Web tracking tag: definition"
seo-title: "Web tracking tag: definition"
description: "Web tracking tag: definition"
seo-description: 
page-status-flag: never-activated
uuid: 915ddfd8-ad1b-41ac-96ed-f7fae687c09f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: b8996508-7173-4225-95e7-b51209aae1f1
index: y
internal: n
snippet: y
---

# Web tracking tag: definition{#web-tracking-tag-definition}

A web tracking tag is simply a URL constructed with the appropriate parameters, sent to the redirection server via an HTTP query.

## Format of the data to be sent {#format-of-the-data-to-be-sent}

The format of a web-tracking URL is as follows: **https://**

>[!NOTE]
>
>The random number added to the URL avoids problems caused by browsers caching web pages.

The following table gives a list of special parameters supported by the redirection server.

Name Type Description ID  
Session cookie  
Delivery identifier and recipient identifier.  
uuid230  
Permanent cookie  
Recipient identifier (useful if session cookie is absent).  
tagid  
URL parameter  
Identifier of tracked web page: this is the only mandatory parameter.  
jobid  
URL parameter  
Delivery identifier to be used if there is no session cookie. This value is to be expressed in hexadecimal.  
rcpid  
URL parameter  
Parameter used to identify the internet user. The format of this parameter is "name=value", where the name is a field of the recipient schema. This parameter takes priority over the identifier contained in the session cookie.

**A few web tracking URLs**

* Visit to a 'home' identifier page

  **https://myserver.adobe.com/r/9862?tagid=home**

* Collecting business volume data

  **https://myserver.adobe.com/r/4567?tagid=command&amount=100&article=2l**

* Specifying a field to find the recipient

  **https://myserver.adobe.com/r/2353?tagid=home&rcpid=saccount%3D10**

  A recipient whose account number is 10 is sent to the home page.

* Using a default delivery

  **https://myserver.adobe.com/r/2456?tagid=home&jobid=e6**

  A recipient is sent to the home page. This information will be stored in the delivery with identifier 230 (e6 in database 16) unless a session cookie containing a delivery identifier is sent with this query.

>[!NOTE]
>
>All values sent to the redirection server via URL parameters must be URL encoded. In the examples given, note that the characters '=' and '|' are encoded as '%3D' and '%7C' respectively.

## Data transmission methods {#data-transmission-methods}

The following methods are possible:

* Inserting the URL in the **"src"** attribute of an HTML ** ![]()

  ** tag incorporated in the web page you wish to track.
* Direct call to the redirection server when the web page you wish to track is generated.


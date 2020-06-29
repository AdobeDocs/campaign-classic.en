---
title: Integrating with Adobe Target
seo-title: Integrating with Adobe Target
description: Integrating with Adobe Target
seo-description: 
page-status-flag: never-activated
uuid: de482b31-0b7b-4669-8a00-28da48c6c5a9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 44c7acdd-6b7a-4e88-b2a7-3e9bf8a6eab5
index: y
internal: n
snippet: y
---

# Integrating with Adobe Target{#integrating-with-adobe-target}

Integration between Adobe Campaign and Adobe Target (Classic and Standard) within Adobe Experience Cloud allows you to include an offer from Adobe Target in an Adobe Campaign email delivery.

The operating principle is as follows: when a recipient opens an email sent via Adobe Campaign, a call to Adobe Target allows you to display a dynamic version of the content. This dynamic version is computed depending on the rules specified beforehand when creating the email.

Learn more about Adobe Campaign and Adobe Target integration with [this four tips and tricks](https://www.adobe.com/content/dam/www/us/en/marketing/campaign/pdfs/Adobe_Campaign_for_Target_Tips_and_Tricks.pdf).
>[!NOTE]
>
>The integration only supports static images. The rest of the content cannot be personalized.

Several types of data can be utilized by Adobe Target:

* Data from the Adobe Campaign datamart
* Segments linked to the visitor ID in Adobe Target, if the data used is not subject to legal limitations
* Adobe Target data: user agent, IP address, geolocalization data

>[!NOTE]
>
>You can also find information regarding integration between Adobe Campaign and Adobe Target on the [Adobe Target help pages](https://docs.adobe.com/content/help/en/target/using/integrate/campaign-and-target.html).

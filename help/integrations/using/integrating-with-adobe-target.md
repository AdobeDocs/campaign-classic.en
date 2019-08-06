---
title: Integrating with Adobe Target
seo-title: Integrating with Adobe Target
description: Integrating with Adobe Target
seo-description: 
page-status-flag: never-activated
uuid: 02605316-24b0-49da-9f50-8f2816627d28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 2f3a292b-6c23-42c6-910f-f4d02408d7cb
index: y
internal: n
snippet: y
---

# Integrating with Adobe Target{#integrating-with-adobe-target}

Integration between Adobe Campaign and Adobe Target (Classic and Standard) within Adobe Experience Cloud allows you to include an offer from Adobe Target in an Adobe Campaign email delivery.

The operating principle is as follows: when a recipient opens an email sent via Adobe Campaign, a call to Adobe Target allows you to display a dynamic version of the content. This dynamic version is computed depending on the rules specified beforehand when creating the email.

>[!NOTE]
>
>The integration only supports static images. The rest of the content cannot be personalized.

Several types of data can be utilized by Adobe Target:

* Data from the Adobe Campaign datamart
* Segments linked to the visitor ID in Adobe Target, if the data used is not subject to legal limitations
* Adobe Target data: user agent, IP address, geolocalization data

>[!NOTE]
>
>You can also find information regarding integration between Adobe Campaign and Adobe Target on the [Adobe Target help pages](https://marketing.adobe.com/resources/help/en_US/target/a4t/c_campaign_and_target.html).


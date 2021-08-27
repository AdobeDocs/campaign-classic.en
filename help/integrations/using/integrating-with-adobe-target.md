---
product: campaign
title: Integrating with Adobe Target
description: Integrating with Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
---
# Integrating with Adobe Target{#integrating-with-adobe-target}

![](../../assets/common.svg)

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
>You can also find information regarding integration between Adobe Campaign and Adobe Target on the [Adobe Target help pages](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html).

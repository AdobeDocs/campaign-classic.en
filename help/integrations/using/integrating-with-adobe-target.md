---
product: campaign
title: Work with Adobe Campaign and Adobe Target
description: Learn how to integrate Adobe Campaign with Adobe Target
feature: Target Integration
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
---
# Work with Campaign and Target{#integrating-with-adobe-target}

 

Use Adobe Campaign with Adobe Target to optimize email content.

To optimize your email content, you can create a redirect offer in Adobe Target, then use Adobe Campaign to manage the email offers. For example, you can display different offers for male and female recipients.

The integration takes place when the email is opened. When the customer opens the email, a call is made to Target and a dynamic version of the content appears. The content consists of a static image supported by all browsers. Target tracks the reaction to the offer at the audience or session level and that data is available in Target reports. [Learn more in Adobe Target documentation](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html).
 

>[!NOTE]
>
>The integration only supports static images. The rest of the content cannot be personalized.

Several types of data can be utilized by Adobe Target:

* Data from the Adobe Campaign datamart
* Segments linked to the visitor ID in Adobe Target, if the data used is not subject to legal limitations
* Adobe Target data: user agent, IP address, geolocation data

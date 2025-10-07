---
product: campaign
title: Get started with personalization
description: Learn how to personalize messages and use conditional content in Campaign
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
---
# Get started with personalization{#about-personalization}

Messages delivered by Adobe Campaign can be personalized in several different ways, concerning the content or the appearance of messages. These ways can be combined according to criteria taken particularly from the recipient profiles. For email deliveries, you can define the elements and personalization conditions of a delivery directly in JavaScript from the **[!UICONTROL Source]** tab of the message. In general, Adobe Campaign allows you to:

* Personalize the message format. See [Message content](defining-the-email-content.md#message-content).
* Insert dynamic personalization fields. See [Personalization fields](personalization-fields.md).
* Insert predefined personalization blocks. See [Personalization blocks](personalization-blocks.md).
* Create conditional content. Refer to the [Conditional content](conditional-content.md) section.

>[!CAUTION]
>
>The following variables are internal variables that can be used for personalization but must not be modified: **delivery**, **message**, **dataSource**, **targetData**, **provider**, **coupon**, **couponValue**, **proposition**.


With Adobe Campaign, personalize your deliveries to send messages that match each recipient’s profile and interests.

Personalization helps you make your messages more relevant and engaging. You can use recipient data to adapt content, add dynamic fields, or display different information based on conditions. Learn how to set up and use personalization features in your deliveries in [Adobe Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html){target=_blank}.

As part of the Campaign v8 promotion initiative, the Campaign Classic documentation has been reorganized. Common features are now only available in the Campaign v8 documentation set.

>[!BEGINTABS]

>[!TAB Content personalization documentation] 

To learn more about content personalization, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html){target=_blank}.


[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html){target=_blank}


>[!TAB Email delivery creation]

Learn the key steps related to email delivery creation in the Campaign v8 documentation:

* [Create an email delivery](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html){target="_blank"}: Learn about the different steps needed to create an email delivery.
* [Define the email content](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html){target="_blank"}: Define what your email will include: sender, subject, content, images.
* [Define interactive content](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html){target="_blank"}: Use the interactive AMP for Email format to send dynamic emails.
* [Send emails on Japanese mobiles](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html){target="_blank"}: Use one of the three specific Japanese formats for email on mobiles.
* [Attach files to an email](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html){target="_blank"}: Learn the different ways to attach one or more files to an email.


>[!TAB Email parameters]

Refer to these pages to learn about email parameters in the Campaign v8 documentation:

* [Link to the mirror page](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/mirror-page.html){target="_blank"}: Configure the mirror page to make sure your clients always get the best rendering experience.
* [Add a BCC address](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-bcc.html){target="_blank"}: Configure Adobe Campaign to keep a copy of emails sent from your platform. 
* [Define additional email parameters](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-parameters.html){target="_blank"}: Learn more about the options and parameters available from the delivery properties.

Also refer to this [page](sending-with-enhanced-mta.md) to learn about the Enhanced MTA.

>[!ENDTABS]





<!--
Adobe Campaign lets you mass deliver personalized electronic messages to a target population.

Before starting sending emails:

* Make sure recipient profiles contain at least an email address.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).
* Read out these sections to learn more about Deliverability: [Deliverability management in Campaign](about-deliverability.md) and [Deliverability best practices guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).

The key steps to send an email are as follows:

* [Create an email delivery](creating-an-email-delivery.md)
* [Define the target population](steps-defining-the-target-population.md)
* [Define the email content](defining-the-email-content.md)
* [Send the email](sending-messages.md)
* [Monitor the delivery](about-delivery-monitoring.md)

The sections below provide information that is specific to the email channel. For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).
-->
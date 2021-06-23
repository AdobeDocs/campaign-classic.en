---
product: campaign
title: About deliverability in Adobe Campaign Classic
description: Learn more about managing deliverability in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
---
# Controlling your message content{#control-message-content}

To make sure that your emails reach your recipients and improve your email deliverability rate, they must respect a number of rules. Otherwise, the content of certain messages may be detected as spam. Adobe Campaign provides you with several tools to make your content comply with these rules.

Follow the principles listed below when designing your message content:

* [Sender address](#sender-address): the address has to explicitly identify the sender. The domain has to be owned by and registered to the sender. The domain registry must not be privatized.
* [Personalization](#personalization): personalizing content and defining a sending time per recipient increase the chances of your message being opened.
* Images and text: respect a decent text/image ratio (for example 60% text and 40% images).
* [Unsubscription link](#opt-out) and landing page: the unsubscription link is essential. It must be visible and valid, and the form must be functional.
* Preview: use the tools offered by Adobe Campaign to check and optimize the content of your email ([Inbox rendering](#message-responsiveness), [SpamAssassin](#spamassassin)).

For additional tips to optimize deliverability when designing content, see the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html).

>[!NOTE]
>
>For more information on editing email content, see [Defining the email content](defining-the-email-content.md) and [Build personalized content](design-and-personalize.md).

## Sender address {#sender-address}

Certain ISPs check the validity of the sender address (**[!UICONTROL From]**) before accepting messages. A badly formed address may result in it being rejected by the receiving server.

You must make sure a correct address is given at the instance level (menu **[!UICONTROL Tools > Advanced > Deployment wizard...]**) or in the most frequently-used scenarios.

For more on this, see [Defining the sender](defining-the-email-content.md).

## Personalization {#personalization}

To improve your recipients’ experience and make them open your email, Adobe Campaign enables you to personalize your messages.

For more on using personalization fields in Adobe Campaign, see [this section](personalization-fields.md).

Some tips to optimize personalization when building your content are presented in [this section](design-and-personalize.md#optimize-personalization).

## Opt-out link and form {#opt-out}

By default, when the message is analyzed, a [typology rule](steps-validating-the-delivery.md#validation-process-with-typologies) checks whether an opt-out link has been included and generates a warning if it is missing. You can change this rule so that an error is raised rather than a simple warning and stop a delivery from going out without this link.

You must check that the opt-out link works correctly before each time you send. For example, when sending the proof, make sure the link is valid, that the form is on-line and that validating this changes the value of the **[!UICONTROL No longer contact this recipient]** field to **[!UICONTROL Yes]**. You should make this check systematically because human error is always possible when entering the link or when changing the form.

Learn how to insert an opt-out link [in this section](personalization-blocks.md#personalization-blocks-example).

If a problem is detected concerning unsubscription after the delivery is started, it is still possible to perform an unsubscription manually (using the mass-update function, for example) for those recipients who click the opt-out link even if they were not able to confirm their choice.

As a general rule, do not try to get in the way of recipients who want to opt-out by requiring them to fill out fields such as their email address or name, for example. The form should have one validation button only, and reconciliation should be performed on the encrypted identifier only.

Requesting additional confirmation is not reliable: a user may have two email addresses redirected to the same box (for example: firstname.lastname@club.com and firstname.lastname@internet-club.com). If the recipient is able to remember the first address only and wishes to unsubscribe via a message sent to the other one, the form will refuse this because the encrypted identifier and the email address entered will not match.

## Inbox rendering {#message-responsiveness}

Before sending your message, you can test your message responsiveness by checking what your message is going to look like on different devices. This is to make sure that it will be displayed in an optimal way on a variety of web clients, web mails and devices.

To allow this, Adobe Campaign captures the rendering and makes it available in a dedicated report. This enables you to preview the sent message in the different contexts in which it may be received.

For more on this, see [Inbox rendering](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign can be configured to work with SpamAssassin. This makes it possible to score emails to determine whether a message runs the risk of being considered as spam by the anti-spam tools used upon receipt.

Before starting a delivery, the **[!UICONTROL Preview]** tab enables you to evaluate the risks. A warning message gives the result of the test.

Learn more in this [section](spamassassin.md).

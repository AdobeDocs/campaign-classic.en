---
title: About deliverability in Adobe Campaign Classic
description: Learn more about managing deliverability in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
---

# Controlling your message content{#control-message-content}

To improve your email deliverability rate and make sure that your emails reach your recipients, the email must respect a certain number of rules detailed below.

## Sender address {#sender-address}

Certain ISPs check the validity of the sender address (From) before accepting messages. A badly formed address may result in it being rejected by the receiving server. You must make sure a correct address is given at the instance level (menu **[!UICONTROL Tools > Advanced > Deployment wizard...]**) or in the most frequently-used scenarios.

## Opt-out link and form {#opt-out}

By default, when the message is analyzed, a typology rule checks whether an opt-out link has been included and generates a warning if it is missing. You can change this rule so that an error is raised rather than a simple warning and stop a delivery from going out without this link.

You must check that the opt-out link works correctly before each time you send. For example, when sending the proof, make sure the link is valid, that the form is on-line and that validating this changes the value of the **[!UICONTROL No longer contact this recipient]** field to **[!UICONTROL Yes]**. You should make this check systematically because human error is always possible when entering the link or when changing the form.

If a problem is detected concerning unsubscription after the delivery is started, it is still possible to perform an unsubscription manually (using the mass-update function, for example) for those recipients who click the opt-out link even if they were not able to confirm their choice.

As a general rule, do not try to get in the way of recipients who want to opt-out by requiring them to fill out fields such as their email address or name, for example. The form should have one validation button only, and reconciliation should be performed on the encrypted identifier only. Requesting additional confirmation is not reliable: a user may have two email addresses redirected to the same box (for example: firstname.lastname@club.com and firstname.lastname@internet-club.com). If the recipient is able to remember the first address only and wishes to unsubscribe via a message sent to the other one, the form will refuse this because the encrypted identifier and the email address entered will not match.

## SpamAssassin {#spamassassin}

Adobe Campaign can be configured to work with SpamAssassin. This makes it possible to score emails to determine whether a message runs the risk of being considered as spam by the anti-spam tools used upon receipt.

Before starting a delivery, the Preview tab enables you to evaluate the risks. A warning message gives the result of the test. 

Learn more in this [section](../../delivery/using/spamassassin.md).
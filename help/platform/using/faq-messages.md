---
solution: Campaign Classic
product: campaign
title: Test and Send FAQ
description: Campaign Classic FAQ
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7fc24ef2-b021-440b-b1f2-8c77e2425328
---
# Validate, send and track messages {#validate-send-track}

## Testing and validation {#test-and-validate-before-sending}

Learn how to perform testing and validation steps before sending messages within Adobe Campaign.

### What is the delivery analysis? {#what-is-the-delivery-analysis-}

The delivery analysis is the phase during which the target population is calculated and the delivery content prepared. Once it is complete, the delivery is ready to send. Consult logs to make sure everything is correct.

[Click here to learn more](../../delivery/using/steps-validating-the-delivery.md).

### Why should I create proofs? {#why-should-i-create-proofs-}

Adobe highly recommends creating proof messages to test your delivery on an approval group before sending it to the main target. You can then validate message content, personalization and delivery parameters.

[Click here to learn more](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof). 

### How to use seed addresses in Adobe Campaign? {#how-to-use-seed-addresses-in-adobe-campaign-}

Seed addresses are used to target recipients who do not match the defined target criteria. These recipients are added to the target: they can be imported or created directly in the delivery or the campaign. For direct mail deliveries, they are added during extraction and mixed in the output document.

This has the following benefits:

* Random substitution of fields with data from recipient profiles: this lets you enter only the email address, for instance in the seed address section.
* When using a workflow with data management functionalities, the additional data processed in deliveries can be entered at seed address level to force values: this sidesteps random value substitution.

[Click here to learn more on seed addresses](../../delivery/using/about-seed-addresses.md).

### How can I set up an approval process before sending messages? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

To detect possible errors in message configuration, Adobe highly recommend setting up a delivery validation cycle. Make sure content is approved as often as necessary by sending proofs to test recipients. A proof should be sent each time a change is made, to approve content.

[Click here to learn more](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### What is a typology rule? {#what-is-a-typology-rule-}

To avoid conflicts between campaigns, Adobe Campaign can test various combinations by applying specific constraint rules. This guarantees that the messages sent best meet the needs and expectations of customers, in keeping with company communication policies.

[Click here to learn more](../../campaign/using/about-campaign-typologies.md).

## Send your messages {#send-your-messages}

Learn how to send messages in various channels with Adobe Campaign.

### How can I send emails in waves? {#how-can-i-send-emails-in-waves-}

Before sending a delivery to a large population, you can [configure waves](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) to divide messages into several batches and balance the load.

### Which are the key steps to create an email in Campaign? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

Once the email delivery is created and validated, you can send it. You can decide to send the email to the main target immediately or schedule a delivery for a later date. If needed, before that, you can also estimate the target population.

[Click here to learn more](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### How to schedule a delivery? {#how-to-schedule-a-delivery-}

You can defer the delivery of messages in order to schedule the delivery or to manage sales pressure and avoid over-soliciting a population.

[Click here to learn more](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

### Can I add an attachment to emails? {#can-i-add-an-attachment-to-emails-}

With Campaign Classic, you can add personalized attachments to your emails.

[Click here to learn more about email attachments](../../delivery/using/attaching-files.md).

## Track your messages and measure their impact {#track-your-messages-and-measure-their-impact}

Once your messages are sent, learn how to track and measure their impact with Adobe Campaign.

### How can I configure tracked links in an email delivery? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

For each delivery, you can track the reception of messages and the activation of the links inserted in the message content. This lets you track the behavior of recipients following the delivery actions which they were targeted by.

For each URL of the message, you can choose whether or not to activate tracking, change the link label, group links by categories for reporting purpose for example.

[Click here to learn more](../../delivery/using/about-message-tracking.md) about how to track your messages in Campaign Classic.

### Where can I access delivery and tracking logs? {#where-can-i-access-delivery-and-tracking-logs-}

Learn how to track your deliveries and understand the recipients' behaviour [from this page](../../delivery/using/delivery-dashboard.md).

### Where can I get delivery reports? {#where-can-i-get-delivery-reports-}

Adobe Campaign comes with a set of reports to monitor your deliveries and track your messages.

[Click here to learn more on built-in reports](../../reporting/using/delivery-reports.md).

### How does Adobe Campaign qualify and manage quarantine addresses? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign manages a list of quarantined addresses. Recipients whose address is quarantined are excluded by default during delivery analysis, and will not be targeted. An email address can be quarantined, for example, when the mailbox is full or if the address does not exist.

[Click here to learn more about quarantine management](../../delivery/using/understanding-quarantine-management.md).

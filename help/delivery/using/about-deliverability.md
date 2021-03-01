---
solution: Campaign Classic
product: campaign
title: About deliverability in Campaign
description: Learn deliverability best practices
audience: delivery
content-type: reference
topic-tags: deliverability-management
---

# What is deliverability{#about-deliverability}

Deliverability allows to measure the success of your campaigns reaching your recipients' inbox without bouncing, or being marked as spam. [Learn why deliverability matters](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

More precisely, email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format.

For a deeper dive on what deliverability is and to learn more on key deliverability terms, concepts, and approaches, refer to the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).

Adobe Campaign offers a certain number of tools to track the deliverability performance of your platform. This section also highlights the main principles you should have in mind when managing and optimizing deliverability.

## How to improve deliverability {#deliverability-key-points}

Deliverability problems are usually linked to measures of protection against spam implemented by internet service providers and mail server administrators.

* For general recommendations on how to design successful email marketing campaigns, refer to [Deliverability strategy and definition](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* For more specific recommendations on how to optimize the deliverability of your Adobe Campaign emails, we recommend using the best practices listed in this section.

>[!NOTE]
>
>Because ISPs are obliged to continuously develop new sophisticated filtering techniques to protect their customers from spammers, email deliverability is characterized by ever-changing criteria and rules. Make sure you refer to the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html) which is regularly updated.

### Deliverability rate

The deliverability rate is the number of messages that hit the recipients’ inboxes compared to the number of messages that were delivered. To improve deliverability, you may work on increasing this rate.

With Adobe Campaign, the deliverability rate depends on numerous factors, particularly:

* Correct configuration of your instances: contact your Adobe representative for assistance.
* Legitimate network configuration: see [this section](../../delivery/using/optimize-delivery.md#network-config) and [Domain setup and strategy](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* Your IP address reputation: see [IP strategy](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Quality of the addresses targeted: see [Quarantine management](../../delivery/using/optimize-delivery.md#quarantine-management).
* Low [complaints](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) and [hard bounce](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces) rates.
* Your message content: see [Controlling email content](../../delivery/using/control-message-content.md).
* Message authentication (SPF, DKIM, DMARC): see [this section](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* Sender reputation: to learn how main ISPs evaluate a sender reputation, see [this section](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Campaign deliverability tools {#deliverability-tools}

Adobe Campaign provides a number of tools designed to ensure optimal deliverability.

### Carefully build your message

When configuring, designing and testing your message, make sure you follow the best practices mentioned in the sections listed below. Leveraging all the features provided by Adobe Campaign will help you improve deliverability.

* [Delivery best practices](../../sending/using/delivery-best-practices.md)
* [Controlling email content](../../sending/using/control-email-content.md)
* [Previewing messages](../../sending/using/previewing-messages.md)
* [Sending proofs](../../sending/using/sending-proofs.md)

### Verify consent through double opt-in {#double-opt-in}

To avoid sending messages to invalid addresses, limit improper communications and improve sender reputation, Adobe recommends implementing a double opt-in mechanism. This enables you to ensure that your recipients subscribed intentionally.

For more on this, see [About opt-in and opt-out in Campaign](../../audiences/using/about-opt-in-and-opt-out-in-campaign.md).

For more on best practices when collecting data from your customers, refer to the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### Leverage quarantine management

Adobe Campaign manages a list that gathers spam complaints, hard bounces, and soft bounces that occur consistently.

To protect your deliverability, the recipients whose addresses are on that list are excluded by default from all future deliveries, because sending to these contacts could hurt your sending reputation.

Some internet access providers automatically consider emails to be spam if the rate of invalid addresses is too high. Quarantine therefore allows you to avoid being added to denylist by these providers.

For more on this, refer to the following sections:

* [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md)
* [Understanding quarantine management](../../delivery/using/understanding-quarantine-management.md)
* [Quarantine vs denylist](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

### Use monitoring and reporting tools

Use the features offered by Adobe Campaign to monitor your deliverability.

Adobe Campaign allows you to check how your deliveries are performing through a set of built-in real-time indicators. <!--For example, you can check the number of messages that are successfully executed, sent and delivered. You can also verify the number of messages that have been opened and the number of messages/links that have been clicked.-->You can also build fully customizable and real-time reports for improved insight on your deliveries.

For more on this, refer to the following sections:

* [Monitoring deliverability](../../sending/using/monitor-deliverability.md)
    <!--[Monitoring a delivery](../../sending/using/monitoring-a-delivery.md)-->
* [Receiving alerts when failures happen](../../sending/using/receiving-alerts-when-failures-happen.md)
* [Dynamic reports](../../reporting/using/about-dynamic-reports.md)

<!--TO REMOVE
## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)-->

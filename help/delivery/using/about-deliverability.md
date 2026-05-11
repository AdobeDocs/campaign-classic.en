---
product: campaign
title: Get started with deliverability in Campaign
description: Learn deliverability best practices
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
role: User
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
TQID: https://experienceleague.adobe.com/UuHzMhIx2zL3VxZXxnKM3UHBlN4Mkr7qy47Ttk-43d0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: beb7a3c1-66ab-4786-b879-7621375b3c40
    internal-label: Email marketing
---
# What is deliverability{#about-deliverability}

Deliverability allows you to measure the success of your campaigns reaching your recipients' inbox without bouncing, or being marked as spam. [Learn why deliverability matters](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters). 

More precisely, email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal email address, within a short time, and with the expected quality in terms of content and format.

For a deeper dive on what deliverability is and to learn more on key deliverability terms, concepts, and approaches, refer to the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).

## How to improve deliverability {#deliverability-key-points}

Deliverability problems are usually linked to measures of protection against spam implemented by internet service providers and mail server administrators.

* For general recommendations on how to design successful email marketing campaigns, refer to [Deliverability strategy and definition](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* For more specific recommendations on how to optimize the deliverability of your Adobe Campaign emails, Adobe recommends using the best practices listed in this section.

>[!NOTE]
>
>Because ISPs are obliged to continuously develop new sophisticated filtering techniques to protect their customers from spammers, email deliverability is characterized by ever-changing criteria and rules. Make sure you refer to the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html) which is regularly updated.

### Deliverability rate

The deliverability rate is the number of messages that hit the recipients' inboxes compared to the number of messages that were delivered. To improve deliverability, you may work on increasing this rate.

With Adobe Campaign, the deliverability rate depends on numerous factors, particularly:

* Correct configuration of your instances: contact your Adobe representative for assistance.
* Legitimate network configuration: see [Domain setup and strategy](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* Your IP address reputation: see [IP strategy](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Low [complaints](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) and [hard bounce](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces) rates.
* Your message content: see [Control the email content](control-message-content.md).
* Message authentication (SPF, DKIM, DMARC): see [this section](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* Sender reputation: to learn how main ISPs evaluate a sender reputation, see [this section](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Campaign deliverability tools {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign provides several tools to track and improve the deliverability performance of your platform. This page also highlights the main principles you should have in mind to optimize deliverability when using Campaign.

### Carefully build your message

When configuring, designing, and testing your message, make sure you follow the best practices mentioned in the sections listed below. Leveraging all the features provided by Adobe Campaign helps you improve deliverability.

* [Delivery best practices](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html){target="_blank"}.
* [Control the email content](control-message-content.md)
* [Inbox rendering](inbox-rendering.md)
* [Sending a proof](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html){target="_blank"}

### Verify consent through double opt-in {#double-opt-in}

To avoid sending messages to invalid addresses, limit improper communications and improve sender reputation, Adobe recommends implementing a double opt-in mechanism. This method enables you to ensure that your recipients subscribed intentionally.

For more on this, see [Create a subscription form with double opt-in](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).

For more on best practices when collecting data from your customers, refer to the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### Leverage quarantine management

Adobe Campaign manages a list that gathers spam complaints, hard bounces, and soft bounces that occur consistently.

To protect your deliverability, the recipients whose addresses are on that list are excluded by default from all future deliveries, because sending to these contacts could hurt your sending reputation.

Some internet access providers automatically consider emails to be spam if the rate of invalid addresses is too high. Quarantine therefore allows you to avoid being added to denylist by these providers.

For more on this, refer to the following sections:

* [Understand delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Campaign v8 documentation - comprehensive guide)
* [Understand quarantine management](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8 documentation - comprehensive guide)

### Use monitoring and reporting tools

Use the features offered by Adobe Campaign to monitor your deliverability.

Adobe Campaign allows you to check how your deliveries are performing through a set of built-in real-time indicators and reports for improved insight on your deliveries.

For more on this, refer to the following sections:

* [Get started with delivery monitoring](about-delivery-monitoring.md)
* [Get started with Campaign built-in reports](../../reporting/using/about-campaign-built-in-reports.md)

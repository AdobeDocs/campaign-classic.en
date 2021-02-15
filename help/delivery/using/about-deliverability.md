---
solution: Campaign Classic
product: campaign
title: About deliverability in Campaign
description: Learn deliverability best practices
audience: delivery
content-type: reference
topic-tags: deliverability-management
---

# About deliverability{#about-deliverability}

**Deliverability** consists in measuring the success of your campaigns reaching your recipients' inbox without bouncing, or being marked as spam.

Adobe Campaign offers a certain number of tools to track the deliverability performance of your platform. This section also highlights the main principles you should have in mind when managing and optimizing deliverability.

## Configuration {#configuration}

This feature is available through a dedicated package in Adobe Campaign. To use it, this package must be installed. Once done, restart the server for the package to be taken into account.
* For hosted and hybrid clients, **Deliverability monitoring** is configured on your instance by Adobe technical support and consultants. For more information, contact your Adobe Account executive.
 
* For on-premise installations, you must install the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package via the **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. For more on this, see [Install Campaign Classic standard packages](../../installation/using/installing-campaign-standard-packages.md).
 
In Adobe Campaign Classic, **Deliverability monitoring** is managed by the **[!UICONTROL Refresh for deliverability]** workflow. It is installed by default on all instances and lets you initialize the list of bounce mail qualification rules, the list of domains and the list of MXs. Once the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package is installed, this workflow runs nightly to regularly update the list of rules and enables you to actively manage platform deliverability.

## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

<!--![](assets/deliverability_overview_2.png)-->

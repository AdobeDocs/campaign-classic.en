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
index: y
internal: n
snippet: y
---

# About deliverability {#about-deliverability}

Adobe Campaign offers a certain number of tools to track the deliverability performance of your platform. This section also highlights the main principles you should have in mind when managing and optimizing deliverability.

## Configuration {#configuration}

This feature is available through a dedicated package in Adobe Campaign. To use it, this package must be installed. Once done, restart the server for the package to be taken into account.
* For hosted and hybrid clients, **Deliverability monitoring** is configured on your instance by Adobe technical support and consultants. For more information, contact your Adobe Account executive.
 
* For on-premise installations, you must install the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package via the **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. For more on this, see [Installing Campaign Classic standard packages](../../installation/using/installing-campaign-standard-packages.md).
 
In Adobe Campaign Classic, **Deliverability monitoring** is managed by the **[!UICONTROL Refresh for deliverability]** workflow. It is installed by default on all instances and lets you initialize the list of bounce mail qualification rules, the list of domains and the list of MXs. Once the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package is installed, this workflow runs nightly to regularly update the list of rules and enables you to actively manage platform deliverability.

## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)


### IP Certification {#ip-certification}

IP Certification is a whitelisting and sending practices program that helps ensuring that emails are received without being blocked by antispam filters or other email blocking systems.

Currently two providers offer IP Certification: Return Path and Certified Senders Alliance.

Certified senders are added to email whitelists which are used by global mailbox providers and email security companies. These commercial whitelists are based on a system that allows the sender to bypass antispam filters altogether or be assigned incremental points as they enter the system.

The [Return Path Certification](https://www.validity.com/products/returnpath/certification/) program offers a number of benefits, including the following:

* A measurable increase in inbox placement at top mailbox providers like Microsoft, AOL, Yahoo, Gmail, Comcast, Orange, Mail.ru, and more
* Favorable reputation and treatment at critical filters like Cloudmark, SpamAssassin, and Cisco Ironport
* A compliance team dedicated to 24/7 monitoring, providing with security alerts and working with you through the resolution of any compromises
* Mailbox provider data delivering detailed information about KPIs, placement, and Certification performance
* Simplified and faster IP warming, including stronger reputation and recognition when migrating or obtaining a new IP address

The [Certified Senders Alliance](https://certified-senders.org/certification-process/) Certification offers amongst other benefits:

* Certification of senders of commercial emails who can comply with high quality standards
* Improved delivery and deliverability of commercial emails to increase the inbox placement rate and reduce spam filtering
* Protection from legal and financial risks by fully complying with legal standards
* Protecting reputation by means of early warnings from the CSA Complaints Office and daily spam trap reports

ISPs are free to use these services and the number of ISPs can vary depending on the whitelist.

However, because more and more ISPs build their antispam filters based on each inbox owner's behavior rather than analyzing the message content itself, using IP Certification cannot be a guarantee of inbox placement or even delivery.

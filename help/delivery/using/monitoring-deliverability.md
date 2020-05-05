---
title: Monitoring deliverability in Adobe Campaign Classic
description: Learn about tools and guidelines on deliverability monitoring in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 0b5c5dbd-f532-4d8a-a255-9e6d88357d8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 0baef937-f00b-4fc4-8608-a870997be684
index: y
internal: n
snippet: y
---

# Monitoring deliverability {#monitoring-deliverability}

Below you will find details on the different monitoring tools offered by Adobe Campaign as well as some additional guidelines on deliverability monitoring.

## Monitoring tools {monitoring-tools}

Use the tools offered by Adobe Campaign to monitor your platform's deliverability:

* The **[!UICONTROL Delivery throughput]** report gives you an overview of the entire platform's throughput for a given period. For more on this, see [this section](../../reporting/using/global-reports.md#delivery-throughput).
* The **[!UICONTROL Technical deliverability monitoring]** report includes a number of deliverability quality indicators for your platform. For more on this, see [this section](#technical-deliverability-monitoring).
* The [Inbox rendering report](../../delivery/using/inbox-rendering.md) enables you to preview your messages on major email clients in order to scan content and reputation.
    <!--Overview of message quality: inbox, spam, [SpamAssassin](../../installation/using/configuring-spamassassin.md), etc.-->
* The [delivery dashboard](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) gives you access to the [Delivery summary](../../delivery/using/monitoring-a-delivery.md#delivery-summary), the [Delivery logs and history](../..delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) and the [Tracking logs](../../delivery/using/monitoring-a-delivery.md#tracking-logs). They show the detail of the sending, which target has been excluded and why, as well as the tracking information such as opens and clicks. <!--For more on this, see [Monitoring a delivery](../../delivery/using/monitoring-a-delivery.md).-->
* You can also check the number of messages to send, processed and sent with success. For more on this, see [this section](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent)

## Monitoring guidelines {monitoring-guidelines}

Here are some additional guidelines on deliverability monitoring:

* Regularly check the [delivery throughput](../../reporting/using/global-reports.md#delivery-throughput) for the whole platform to verify whether it is consistent with the original set-up.
* Check that [retries](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) are set up correctly (30 minutes for retry period and more than 20 retries) in delivery templates.
* Regularly verify that the [bounce](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) mailbox is accessible and that the account is not about to expire.
* Check each delivery throughput to make sure that it is consistent with the delivery content's validity (e.g. 'flash sales' should be delivered in minutes, not days).
* When using [waves](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), verify that each wave has enough time to finish before the next one is triggered.
* Check that the number of errors and new [quarantines](../../delivery/using/understanding-quarantine-management.md) are consistent with other deliveries.
* Carefully consult the [delivery logs](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) in detail to check the kind of errors that are highlighted (grey or black-listing, DNS issues, anti-spam rules, etc…).

## Signal Spam

Signal Spam is a French service which offers anonymized feedback loop reporting for French ISPs (Orange, SFR).

* This service allows you to follow the reputation of the French ISPs and track customers' activity evolution.

* Signal Spam also provides direct complaints that end users log through a dedicated interface. Those complaints are then quarantined from the email address database.

## 250ok

[250ok](https://250ok.com/) is a a complementary monitoring solution to the Adobe deliverability internal tools which provides IP, domain blacklisting and reputation indicators.

The information provided is real-time, which allows for a pro-active assistance.

## Technical Deliverability Monitoring Report {#technical-deliverability-monitoring}

The technical deliverability monitoring report is updated daily and available by navigating to **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** and clicking the **[!UICONTROL Technical monitoring]** link from the Adobe Campaign **[!UICONTROL Home]** tab. It includes a number of deliverability quality indicators for your platform.

These indicators are updated daily at 9 AM.

>[!NOTE]
>
>In addition, you are able to receive a daily report by email at a specified address. Let us know the requested email address by email or via the Adobe Campaign Extranet.

![](assets/s_tn_del_monitoring.png)

The following indicators are used in the report:

* **[!UICONTROL Reverse DNS]** : Adobe Campaign checks whether a reverse DNS is given for an IP address and that this correctly points back to the IP.

* **[!UICONTROL SPF]** (Sender Policy Framework): An authentication mechanism that enables ISPs and mailbox providers to check whether the email sender is authorized on the sending domain.
    
* **[!UICONTROL DomainKeys]** : A service developed by Yahoo and intended to certify the identity of an email sender.

* **[!UICONTROL IP and RBL domain]** (Real-time Blackhole List): A list of IP addresses and domains that have been flagged by blocklist organizations for poor sending reputation. These lists are maintained by dedicated organizations such as Spamhaus,Spamcop, SURBL/URIBL, etc. Adobe Campaign currently processes checks against RBLs that have a significant deliverability impact. These RBLs reflect sending reputation, and may be referenced by ISPs before accepting to receive your emails.

* **[!UICONTROL SNDS]** (Smart Network Data Services): A [Windows Live Hotmail anti-spam service](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). Hotmail is the only ISP that provides this type of information. Benchmark scores are a green filter result, a complaint rate of less than 0.1%, and zero spam traps.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->

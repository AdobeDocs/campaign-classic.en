---
title: Inbox monitoring
description: Inbox monitoring
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

Below you will find details on the **Delivery throughput** report as well as the different monitoring tools offered by Adobe Campaign. Here are some additional guidelines on deliverability monitoring.

## Monitoring tools

Use the tools offered by Adobe Campaign to monitor your platform's deliverability.

* Overview of message quality (inbox, spam)
* What are the tools available apart from the Campaign basic reports?

You can also use:

* The **[!UICONTROL Delivery throughput]** report which gives you an overview of the entire platform's throughput for a given period. For more information on this report, refer to this page.
* The **[!UICONTROL Technical deliverability monitoring]** report which includes a number of deliverability quality indicators for your platform. Learn more about this report in this page.

## Monitoring guidelines

Here are some additional guidelines on deliverability monitoring:

* Regularly check the delivery throughput for the whole platform to verify whether it is consistent with the original set-up.
* Check that retries are set up correctly (30 minutes for retry period and more than 20 retries) in delivery templates.
* Regularly verify that the bounce mailbox is accessible and that the account is not about to expire.
* Check each delivery throughput to make sure that it is consistent with the delivery content's validity (e.g. 'flash sales' should be delivered in minutes, not days).
* When using waves, verify that each wave has enough time to finish before the next one is triggered.
* Check that the number of errors and new quarantines are consistent with other deliveries.
* Carefully consult the delivery logs in detail to check the kind of errors that are highlighted (grey or black-listing, DNS issues, anti-spam rules, etc…).

## Signal Spam

Signal Spam is a French service which offers anonymized feedback loop reporting for French ISPs (Orange, SFR).

This service allows you to follow the reputation of the French ISPs and track customers' activity evolution.

Signal Spam also provides direct complaints that end users log through a dedicated interface. Those complaints are then quarantined from the email address database.

## 250ok

250ok is a monitoring solution which provides IP, domain blacklisting and reputation indicators.

The information provided is real-time, which allows for a pro-active assistance. 250ok a complementary solution to the Adobe deliverability internal tools.
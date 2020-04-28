---
title: Technical monitoring
seo-title: Technical monitoring
description: Technical monitoring
seo-description: 
page-status-flag: never-activated
uuid: 44ac7cf0-1d44-4656-b137-f3008be32e1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 008d6a63-68cd-4e87-8adb-9642e2f9bb2a
index: y
internal: n
snippet: y
---

# Monitoring deliverability{#technical-monitoring}

## Monitoring tools {monitoring-tools}

Use the tools offered by Adobe Campaign to monitor your platform's deliverability.

The Deliverability package gives you access to:

Technical tracking report for day-to-day deliverability performance (technical monitoring)
ISP inbox rendering report
Overview of message quality (inbox, spam)
You can also use:
* The Delivery throughput report which gives you an overview of the entire platform's throughput for a given period. For more information on this report, refer to this page. 
* the technical monitoring report which includes a number of deliverability quality indicators for your platform. Learn more about this report in [this page](../../reporting/using/global-reports.md).

## Monitoring guidelines {monitoring-guidelines}

Here are some additional guidelines on deliverability monitoring:

Regularly check the delivery throughput for the whole platform to verify whether it is consistent with the original set-up.
Check that retries are set up correctly (30 minutes for retry period and more than 20 retries) in delivery templates.
Regularly verify that the bounce mailbox is accessible and that the account is not about to expire.
Check each delivery throughput to make sure that it is consistent with the delivery content's validity (e.g. 'flash sales' should be delivered in minutes, not days).
When using waves, verify that each wave has enough time to finish before the next one is triggered.
Check that the number of errors and new quarantines are consistent with other deliveries.
Carefully consult the delivery logs in detail to check the kind of errors that are highlighted (grey or black-listing, DNS issues, anti-spam rules, etc…).

## 250ok {deliverability-250ok}
250ok is a monitoring solution which provides IP, domain blacklisting and reputation indicators.
The information provided is real-time, which allows for a pro-active assistance. 250ok a complementary solution to the Adobe deliverability internal tools.

## Signal Spam {signal-spam}

Signal Spam is a French service which offers anonymized feedback loop reporting for French ISPs (Orange, SFR).
This service allows you to follow the reputation of the French ISPs and track customers' activity evolution.
Signal Spam also provides direct complaints that end users log through a dedicated interface. Those complaints are then quarantined from the email address database.

## Technical Deliverability Monitoring Report {#technical-deliverability-monitoring}

The technical deliverability monitoring report is updated daily and available by navigating to **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** and clicking the **[!UICONTROL Technical monitoring]** link from the Adobe Campaign **[!UICONTROL Home]** tab. It includes a number of deliverability quality indicators for your platform.

These indicators are updated daily at 9 AM.

>[!NOTE]
>
>In addition, you are able to receive a daily report by email at a specified address. Please let us know the requested email address by email or via the Adobe Campaign Extranet.

![](assets/s_tn_del_monitoring.png)

The following indicators are used in the report:

* **[!UICONTROL Reverse DNS]** : Adobe Campaign checks whether a reverse DNS is given for an IP address and that this correctly points back to the IP.

* **[!UICONTROL SPF]** (Sender Policy Framework): An authentication mechanism that enables ISPs and mailbox providers to check whether the email sender is authorized on the sending domain.

    <!--
    >[!NOTE]
    >
    >The SPF may look **[!UICONTROL Acceptable]** (instead of **[!UICONTROL Good]**) since the report is currently unable to detect the presence of a “redirect” or “include” mechanism. This bug has been submitted to Adobe Campaign R&D to be fixed. In the meantime, please feel free to add 15 points to your global score to obtain your real rating (a **[!UICONTROL Good]** one corresponds to 96 points or higher).
    -->
    
* **[!UICONTROL DomainKeys]** : A service developed by Yahoo and intended to certify the identity of an email sender.

* **[!UICONTROL IP and RBL domain]** (Real-time Blackhole List): A list of IP addresses and domains that have been flagged by blocklist organizations for poor sending reputation. These lists are maintained by dedicated organizations such as Spamhaus,Spamcop, SURBL/URIBL, etc. Adobe Campaign currently processes checks against RBLs that have a significant deliverability impact. These RBLs reflect sending reputation, and may be referenced by ISPs before accepting to receive your emails.

* **[!UICONTROL SNDS]** (Smart Network Data Services): A [Windows Live Hotmail anti-spam service](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). Hotmail is the only ISP that provides this type of information. Benchmark scores are a green filter result, a complaint rate of less than 0.1%, and zero spam traps.

<!--
* **[!UICONTROL Reputation Authority]**: This WatchGuard’s score is calculated in real time according to the feedback received from their network worldwide, and also from the different users who use their software.

    Administrators can use such tools to apply a first level filter on their messaging servers.
    If you click on the IP link within the technical report, it will lead you to reputationauthority.org, where you will have the possibility to clean the IP history and get a neutral score again.
    Nevertheless, this action is limited to a number of times per month.
    Please also be aware there is no support provided by WatchGuard‘s Reputation Authority (sending delisting requests is therefore useless). Otherwise, this scoring is based on the following: 
    * Message content (for example: presence of spam words). 
    * IP/Domains reputation (for example: your IPs are listed on an RBL). 
    * IP configuration (for example: IPs associated to different domains). 
    * Volumes sent by IP (for example: presence of peaks or significant variations).
    
    * **[!UICONTROL Sender Score]** : A database of reputed servers ([https://www.senderscore.org/](https://www.senderscore.org/)) issuing a score created by Return Path about your reputation. Think of it like a credit score, but for email senders.-->

<!--## Delivery Reports - Broadcast Statistics {#delivery-reports-broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability:

![](assets/s_tn_del_monitoring.png)-->

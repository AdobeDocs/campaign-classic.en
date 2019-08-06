---
title: Message Center processing time
seo-title: Message Center processing time
description: Message Center processing time
seo-description: 
page-status-flag: never-activated
uuid: 6f21dd78-6434-4af8-af4b-23ecdff73247
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: ede64fd6-742f-4ee0-9de4-5b92b4557698
index: y
internal: n
snippet: y
---

# Message Center processing time{#message-center-processing-time}

This report displays the main indicators related to the real time queue. This report, aimed at technical administrators, can also be accessed via the **Monitoring** universe in the control instance.

![](assets/mc_reports_2.png)

Just like for the **Message Center service level** report, you can choose to display the overall statistics or those relative to a particular execution instance. You can also filter the data by channel and over a specific period. The indicators displayed in the **Indicators over the period** section are calculated over the period selected:

* **Average queuing time**: the average time that successfully processed events spent in Message Center. Only the processing time is taken into account.
* **Average message sending time (s)**: the average time that successfully processed events spent in Message Center. Only the mta delivery time is taken into account.
* **Average processing time (s)**: the average time that successfully processed events spent in Message Center. The calculation takes the processing time and the mta sending time into account.
* **Maximum number of queued events**: maximum number of events present in the Message Center queue at any given moment.
* **Minimum number of queued events**: minimum number of events present in the Message Center queue at any given moment.
* **Average number of queued events**: average number of events present in the Message Center queue at any given moment.

>[!NOTE]
>
>The warning (orange) and alert (red) indicator thresholds can be configured in Adobe Campaign deployment wizard. Refer to [Monitoring thresholds](../../message-center/using/monitoring-thresholds.md).


---
title: Message Center service level
seo-title: Message Center service level
description: Message Center service level
seo-description: 
page-status-flag: never-activated
uuid: 0a12e25e-dd50-4c2d-a8c5-af95d05ffdc2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 4307b58e-d00f-49f0-8195-bbe3d7566f94
index: y
internal: n
snippet: y
---

# Message Center service level{#message-center-service-level}

This report displays the delivery statistics related to transactional messages as well as the error breakdown. You can click on an error type to display its details. This report, aimed at technical administrators, can also be accessed via the **Monitoring** universe in the control instance.

![](assets/mc_reports_1.png)

In this report, you can choose to display the overall statistics or those relative to a particular execution instance. You can also filter the data by channel and over a specific period. The indicators displayed in the **Indicators over the period** section are calculated over the period selected:

* **Incoming (throughput event/h)**: average hourly number of events entered in the Message Center queue.
* **Incoming (event vol)**: number of events entered in the Message Center queue.
* **Outgoing (throughput msg/h)**: average hourly number of successful outgoing Message Center events (sent by a delivery).
* **Outgoing (msg vol)**: number of successful outgoing Message Center events (sent by a delivery).
* **Average sending time (seconds)**: average time spent in Message Center for successfully processed events. The calculation takes the processing time and the mta sending time into account.
* **Error rate**: number of events with errors compared to the number of events that have entered the Message Center queue. The following errors are taken into account: routing error, expired event (event that has been in the queue too long), delivery error, ignored by the delivery (quarantine, etc.).

>[!NOTE]
>
>The warning (orange) and alert (red) indicator thresholds can be configured in the deployment wizard. Refer to [Monitoring thresholds](../../message-center/using/monitoring-thresholds.md).


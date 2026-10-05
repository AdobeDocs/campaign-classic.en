---
product: campaign
title: Message Center processing time
description: Learn more on the Message Center processing time report
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
TQID: 'https://experienceleague.adobe.com/nESBoEHC7YU0SO4yJ0rscDa3E-ePk6yNbPKzusER7C4'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
---
# Message Center processing time {#message-center-processing-time}



This report displays the main indicators related to the real time queue.

This report, aimed at technical administrators, can also be accessed via the **[!UICONTROL Monitoring]** tab on the control instance.

![](assets/mc_reports_2.png)

Just like for the **[!UICONTROL Message Center service level]** report, you can choose to display the overall statistics or those relative to a particular execution instance. You can also filter the data by channel and over a specific period.

The indicators displayed in the **[!UICONTROL Indicators over the period]** section are calculated over the period selected:

* **[!UICONTROL Average queuing time]** : the average time that successfully processed events spent in Message Center. Only the processing time is taken into account.
* **[!UICONTROL Average message sending time (s)]** : the average time that successfully processed events spent in Message Center. Only the mta delivery time is taken into account.
* **[!UICONTROL Average processing time (s)]** : the average time that successfully processed events spent in Message Center. The calculation takes the processing time and the mta sending time into account.
* **[!UICONTROL Maximum number of queued events]** : maximum number of events present in the Message Center queue at any given moment.
* **[!UICONTROL Minimum number of queued events]** : minimum number of events present in the Message Center queue at any given moment.
* **[!UICONTROL Average number of queued events]** : average number of events present in the Message Center queue at any given moment.

>[!NOTE]
>
>The warning (orange) and alert (red) indicator thresholds can be configured in Adobe Campaign deployment wizard. Refer to [Monitor thresholds](../../message-center/using/additional-configurations.md#monitoring-thresholds).

---
product: campaign
title: Delivery execution
description: Learn more about transactional messages delivery execution and monitoring.
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 930c6395-0c00-40ee-a925-3e0cae67c55f
---
# Delivery execution {#delivery-execution}

## Transactional message sending {#transactional-message-send}

On the execution instance, once the enrichment stage is complete and a delivery template has been linked to the event, the delivery is sent.

>[!NOTE]
>
>The MTA prioritizes processing the transactional messages over any other delivery.

All deliveries are grouped in the **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** folder.

![](assets/messagecenter_deliveries_execinstances_001.png)

By default, they are sorted into sub-folders by delivery month. This sort can be changed in the message template properties as shown below.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>For hosted or hybrid installations, if you have upgraded to the [Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md), all transactional messages may also be sent with the Adobe Campaign Enhanced MTA for improved deliverability, throughput, and bounce handling. All impacts are the same as for standard marketing messages.

## Transactional message monitoring {#transactional-message-monitoring}

To monitor your transactional messages, check the [delivery logs](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

The transactional deliveries sent from the execution instance are synchronized back to the control instance through a technical workflow (**[!UICONTROL Message Center execution instance]**) that runs every hour.
 
>[!NOTE]
>
>The deliveries weekly accumulate the events based on the latest event update, and not on the event creation date. Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID may change over time as the log is updated (for example, when an inbound bounce is received for the event).

<!--The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

Let's take a [delivery template](../../message-center/using/introduction.md) labelled *Template_1*.

1. An event corresponding to *Template_1* is received on the execution instance.
1. The **Processing real time events** (rtEventsProcessing) workflow processes the event and searches for an existing delivery for the current month.

    >[!NOTE]
    >
    >If not found, a new delivery is created and the event is assigned to the new delivery.

1. The transactional email is sent and the delivery status changes to **[!UICONTROL Sent]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and updates the delivery logs on the control instance.
1. The control instance searches for an existing delivery for week 40 (2020-09-28_Template_1).

    >[!NOTE]
    >
    >If not found, a new delivery is created.

1. The week after, an inbound bounce is received for the event.
1. The status of the event changes to **[!UICONTROL Delivery failed]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and searches for a delivery for week 41 (2020-10-05_Template_1) to update the delivery logs. The delivery logs are then linked to a new delivery for the current week.

To summarize, the deliveries weekly accumulate the events based on the latest event update, and not on the event creation date.

Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID changes every week.-->

To monitor the activity and running of the execution instance(s), see [Transactional messaging reports](../../message-center/using/about-transactional-messaging-reports.md).

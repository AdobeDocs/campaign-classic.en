---
title: Delivery execution
seo-title: Delivery execution
description: Delivery execution
seo-description: 
page-status-flag: never-activated
uuid: d4f4cea7-783b-45d3-b004-297104f0a906
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: afb375de-2de3-47ad-8b37-664cc04864e8
index: y
internal: n
snippet: y
---

# Delivery execution{#delivery-execution}

>[!NOTE]
>
>The MTA prioritizes processing the transactional messages over any other delivery.

On the execution instance, once the enrichment stage is complete and a delivery template has been linked to the event, the delivery is sent. All deliveries are grouped in the **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** folder.

![](assets/messagecenter_deliveries_execinstances_001.png)

By default, they are sorted into sub-folders by delivery month.

This sort can be changed in the message template properties as shown below.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>For hosted or hybrid installations, if you have upgraded to the Enhanced MTA, all transactional messages may also be sent with the Adobe Campaign Enhanced MTA for improved deliverability, throughput, and bounce handling. All impacts are the same as for standard marketing messages and they are detailed in the [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html) document.
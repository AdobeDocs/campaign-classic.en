---
title: Accessing deliveries information
seo-title: Accessing deliveries information
description: Accessing deliveries information
seo-description: 
page-status-flag: never-activated
uuid: dc8f0267-1884-4a39-9a7d-d5ef21932928
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: d2631c67-7781-4baa-b24e-e7921353d131
index: y
internal: n
snippet: y
---

# Accessing deliveries information{#accessing-deliveries-information}

## Accessing the list of deliveries {#accessing-the-list-of-deliveries}

To access the list of deliveries, go to the **[!UICONTROL Campaigns]** universe and click the **[!UICONTROL Deliveries]** link.

If you use [the Explorer view](https://helpx.adobe.com/campaign/classic/platform/using/adobe-campaign-workspace.html#about-adobe-campaign-explorer), you can access all deliveries via the **[!UICONTROL Campaign management > Deliveries]** node in the tree.

>[!NOTE]
>
>Adobe Campaign workspace is presented in [this section](https://helpx.adobe.com/campaign/classic/platform/using/adobe-campaign-workspace.html).

This page lets you access an overall view of your deliveries: it displays all the deliveries in your database. You can view their status, success rate, and modification dates.

![](assets/d_ncs_user_filter_interface_delivery01.png)

>[!NOTE]
>
>Information filtering is presented in [this section](https://helpx.adobe.com/campaign/classic/platform/using/filtering-options.html).

The delivery wizard lets you configure your deliveries, launch the approval process, and send. The content of the wizard depends on the communication channel (email, mobile, push, direct mail) and the operator rights.

To manipulate the deliveries in the list, click a delivery. It opens in a new window and you can confirm its delivery or to pause it, for example. 

![](assets/s_ncs_user_interface_delivery02.png)

Depending on the stage of the delivery cycle, the main possible statuses are:

* Cancelled
* Failed
* Pending 
* Finished
* Paused
* Retry pending
* In progress
* Ready for delivery
* Preparation in progress
* Target calculation
* Being edited

Each status has its own color and label. 

![](assets/s_ncs_user_status_campaigns_120.png)

The drop-down list next to the **[!UICONTROL Create]** button enables you to filter deliveries based on their status.

![](assets/delivery_filter_status.png)

## Accessing the delivery calendar {#accessing-the-delivery-calendar}

To access the delivery calendar, go to the **[!UICONTROL Campaign]** universe and click the **[!UICONTROL Campaign calendar]** link. This calendar displays the breakdown of campaigns over time. You can personalize the display by month, week, or day.

![](assets/s_ncs_user_interface_delivery04.png)

Click the name of a delivery to display the main information about it. You can also open the campaign if necessary by clicking **[!UICONTROL Open]** .

![](assets/s_ncs_user_interface_delivery05.png)

## Accessing deliveries throughput information {#accessing-deliveries-throughput-information}

The information on the **[!UICONTROL Delivery throughput]** page concerns all the deliveries of the platform. To measure the speed at which the messages are delivered, the criteria are the number of messages sent per hour and the size of the messages (in bits per second). In the example below, the first graph shows the successful deliveries in blue, and the number of erroneous deliveries in orange.

You can choose the time slot for which the throughput is calculated. To do this, select the value from the drop-down list, and then click **[!UICONTROL Refresh]** .

![](assets/s_ncs_user_interface_delivery06.png)


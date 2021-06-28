---
product: campaign
title: Cross-channel deliveries
description: Learn more about cross-channel deliveries
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
---
# Cross-channel deliveries{#cross-channel-deliveries}

Cross-channel deliveries are available in the **[!UICONTROL Deliveries]** tab of campaign workflow activities.

The various channels available are:

* [Email](../../delivery/using/about-email-channel.md)
* [Direct Mail](../../delivery/using/about-direct-mail-channel.md)
* [Mobile](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md) (Campaign Classic v7 only)
* [Facebook](../../social/using/publishing-on-facebook.md) (Campaign Classic v7 only)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Select the template on which you want to base your delivery and define its content.

You can specify a target for your delivery upstream of the workflow using the different targeting activities.

In the example below, we will create a workflow to send an email or an SMS for push notification subscribers then a push notification one week later. To do this:

1. Create a campaign.
1. In the **[!UICONTROL Targeting and workflows]** tab of your campaign, add a **[!UICONTROL Query]** to your workflow.
1. Configure your query. For example, here we select the recipients who are subscribed to push notifications as the target dimension.

   >[!NOTE]
   >
   >For the push notifications, use the **subscriber applications** target dimension.

   ![](assets/cross_channel_delivery_1.png)

1. Add the filter conditions to your query. In this case, we will select recipients who have a mobile number or email address.

   ![](assets/cross_channel_delivery_2.png)

1. Add a **[!UICONTROL Split]** activity to your workflow to divide recipients who have a mobile number and those who have an email address.
1. In the **[!UICONTROL Delivery]** tab, select a delivery for each of your targets.

   Create your delivery in the same way as with a classic delivery wizard by double-clicking the delivery activity in your workflow. For more on this, refer to this [page](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Add and configure a **[!UICONTROL Wait]** activity in order for the recipients not to receive too many deliveries at once.
1. Add a **[!UICONTROL Split]** activity to divide subscribers of an iOS or Android mobile applications.

   Select a service for each of the operating systems. For more on service creation, refer to this [page](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Select and configure a mobile application delivery for each of the operating systems.

   ![](assets/cross_channel_delivery_5.png)

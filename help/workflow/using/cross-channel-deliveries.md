---
product: campaign
title: Cross-channel deliveries
description: Learn more about cross-channel deliveries
feature: Workflows, Channels Activity
hide: true
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
TQID: https://experienceleague.adobe.com/BXn5nJkGD-NL8Rh5kYtltXfGJiWlYQqbyzcdZ1SleJA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: Workflow HeatMap (Campaign)
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities (Campaign)
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities (Campaign)
---
# Cross-channel deliveries{#cross-channel-deliveries}



Cross-channel deliveries are available in the **[!UICONTROL Deliveries]** tab of campaign workflow activities.

The various channels available are:

* [Email](../../delivery/using/about-email-channel.md)
* [Direct Mail](../../delivery/using/about-direct-mail-channel.md)
* [Mobile](../../delivery/using/sms-channel.md)
* [X (formerly known as Twitter)](../../social/using/about-social-marketing.md)
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

   Create your delivery in the same way as with a classic delivery assistant by double-clicking the delivery activity in your workflow. For more on this, refer to this [page](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Add and configure a **[!UICONTROL Wait]** activity in order for the recipients not to receive too many deliveries at once.
1. Add a **[!UICONTROL Split]** activity to divide subscribers of an iOS or Android mobile applications.

   Select a service for each of the operating systems. For more on service creation, refer to this [page](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Select and configure a mobile application delivery for each of the operating systems.

   ![](assets/cross_channel_delivery_5.png)

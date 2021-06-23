---
product: campaign
title: Create a push notification for Android devices
description: Learn how to create push notifications for Android
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
---
# Create notifications for Android{#create-notificaations-android}

Use Adobe Campaign to send push notifications on Android devices. Global concepts on delivery creation are presented in [this section](steps-about-delivery-creation-steps.md).

Start by creating a new delivery.

![](assets/nmac_delivery_1.png)

With Firebase Cloud Messaging, you can choose between two types of messages:

* **[!UICONTROL Data message]**, handled by the client app.
   <br>Messages are sent directly to the mobile application which will generate and display the android notification to the device. Data messages contain only your custom application variables.

* **[!UICONTROL Notification message]**, handled automatically by the FCM SDK.
   <br> FCM automatically displays the message on your users' devices on behalf of the client app. Notification messages contain a predefined set of parameters and options but can still be further personalized with custom application variables.

For more information on Firebase Cloud Messaging messages types, refer to [FCM documentation](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages
).

## Create a data message {#creating-data-message}

1. Go to **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Click **[!UICONTROL New]**.

    ![](assets/nmac_android_3.png)

1. Select **[!UICONTROL Deliver on Android (android)]** in the **[!UICONTROL Delivery template]** drop-down. Add a **[!UICONTROL Label]** to your delivery.

1. Click **[!UICONTROL To]** to define the population to target. By default, the **[!UICONTROL Subscriber application]** target mapping is applied. Click **[!UICONTROL Add]** to select your service.

    ![](assets/nmac_android_7.png)

1. In the **[!UICONTROL Target type]** window, select **[!UICONTROL Subscribers of an Android mobile application]** and click **[!UICONTROL Next]**.

1. In the **[!UICONTROL Service]** drop-down, select your previously created service then application and click **[!UICONTROL Finish]**.
    The **[!UICONTROL Application variables]** are automatically added depending on what was added during the configuration steps.

    ![](assets/nmac_android_6.png)

1. Select **[!UICONTROL data message]** as **[!UICONTROL Message Type]**.

1. Edit your rich notification.

    ![](assets/nmac_android_5.png)

1. You can add information in your previously configured **[!UICONTROL Application variables]** if needed. **[!UICONTROL Application variables]** needs to be configured in the Android service and are a part of the message payload sent to the mobile device.

1. Click **[!UICONTROL Save]** and send your delivery.

The image and web page should be displayed in the push notification when received on the subscribers' mobile Android devices.

![](assets/nmac_android_4.png)

## Create a notification message {#creating-notification-message}

   >[!NOTE]
   >
   >Additional options for notification message are only available with HTTP v1 API configuration. For more on this, refer to this [section](configuring-the-mobile-application-android.md#android-service-httpv1).

![](assets/do-not-localize/how-to-video.png) [Learn how to create an Android push notification in video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. Go to **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Click **[!UICONTROL New]**.

    ![](assets/nmac_android_3.png)

1. Select **[!UICONTROL Deliver on Android (android)]** in the **[!UICONTROL Delivery template]** drop-down. Add a **[!UICONTROL Label]** to your delivery.

1. Click **[!UICONTROL To]** to define the population to target. By default, the **[!UICONTROL Subscriber application]** target mapping is applied. Click **[!UICONTROL Add]** to select your service.

    ![](assets/nmac_android_7.png)

1. In the **[!UICONTROL Target type]** window, select **[!UICONTROL Subscribers of an Android mobile application]** and click **[!UICONTROL Next]**.

1. In the **[!UICONTROL Service]** drop-down, select your previously created service then application and click **[!UICONTROL Finish]**.

    ![](assets/nmac_android_6.png)

1. Select **[!UICONTROL notification message]** as **[!UICONTROL Message Type]**.

1. Add a title and edit your message. Personalize your push notification with the **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: Set your notification's channel ID. The app must create a channel with this channel ID before any notification with this channel ID is received.
   * **[!UICONTROL Sound]**: Set the sound to play when the device receives your notification.
   * **[!UICONTROL Color]**: Set your notification's icon color.
   * **[!UICONTROL Icon]**: Set the notification's icon to display on your profiles' devices.
   * **[!UICONTROL Tag]**: Set the identifier used to replace existing notifications in the notification drawer.
   * **[!UICONTROL Click action]**: Set the action associated with a user click on your notification.

   For more on the **[!UICONTROL Notification options]** and how to fill these fields, refer to [FCM documentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_8.png)

1. If your application is configured with HTTP v1 API protocol, you can further personalize your push notification with the following **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: Set the ticker text of your notification. Only available for devices set to Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: Set the image's URL to be displayed in your notification.
   * **[!UICONTROL Notification Count]**: Set the number of new unread information to display directly on the application icon.
   * **[!UICONTROL Sticky]**: Set to true or false. If set to false, the notification is automatically dismissed when the user clicks it. If set to true, the notification is still displayed even when the user clicks it.
   * **[!UICONTROL Notification Priority]**: Set the priority levels of your notification to default, minimum, low or high. For more on this, refer to [FCM documentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: Set the visibility levels of your notification to public, private or secret. For more on this, refer to [FCM documentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   For more on the **[!UICONTROL HTTP v1 additional options]** and how to fill these fields, refer to [FCM documentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_9.png)

1. You can add information in your previously configured **[!UICONTROL Application variables]** if needed. **[!UICONTROL Application variables]** needs to be configured in the Android service and are a part of the message payload sent to the mobile device.

1. Click **[!UICONTROL Save]** and send your delivery.

The image and web page should be displayed in the push notification when received on the subscribers' mobile Android devices.

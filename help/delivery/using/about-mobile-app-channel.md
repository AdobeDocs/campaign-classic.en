---
product: campaign
title: About mobile app channel in Adobe Campaign Classic
description: This section provides general information specific to the mobile app channel in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
---
# Get started with mobile app channel{#about-mobile-app-channel}

The **Mobile App Channel** lets you use the Adobe Campaign platform to send personalized push notifications to iOS and Android terminals via apps. 

>[!CAUTION]
>
>This document details the process for integrating your mobile application with the Adobe Campaign platform. It does not provide information on how to create the mobile application or how to configure it for managing notifications. If you would like further information on this, refer to the official Apple [documentation](https://developer.apple.com/) and Android [documentation](https://developer.android.com/index.html).

Two delivery channels are available:

* An iOS channel that enables you to send notifications to Apple mobile devices.

  ![](assets/nmac_intro_2.png)

* An Android channel that enables you to send data messages to Android mobile devices.

  ![](assets/nmac_intro_1.png)

Corresponding to those two channels there are two delivery activities in the campaign workflows:

![](assets/nmac_intro_3.png)


>[!NOTE]
>
>Two transactional message templates are also available for transactional messaging.

You can define the application behavior for when the user activates the notification to display the screen that matches the application context. For example:

* A notification is sent to the customer to let them know their parcel has exited the warehouse. Activating the notification opens a page with delivery-related information on it.
* The user has added items to the cart, but left the application without completing the purchase. A notification is sent, telling them that their cart has been abandoned. When they activate the notification, the item is displayed on the screen.

>[!CAUTION]
>
>* You need to make sure the notifications sent to a mobile application are compliant with the prerequisites and conditions specified by Apple (Apple Push Notification Service) and Google (Firebase Cloud Messaging).
>* Warning: in some countries, the law requires that you inform users of your collected data type mobile applications and the purpose of their processing. You must check the legislation.

The **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) workflow updates notification unsubscriptions on mobile devices. For more information on this workflow, refer to the [list of technical workflows](../../workflow/using/about-technical-workflows.md).

Adobe Campaign is compatible with HTTP/2 APNs. For more details on the configuration steps, refer to the [this section](configuring-the-mobile-application.md) section.

For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).

## Data path {#data-path}

The following schemas detail the steps that enable a mobile application to exchange data with Adobe Campaign. This process involves three entities:

* the mobile application
* the notification service: APNs (Apple Push Notification Service) for Apple and FCM (Firebase Cloud Messaging) for Android
* Adobe Campaign

The three main steps of the notification process are: registration of the application in Adobe Campaign (subscription collection), deliveries, and tracking.

### Step 1: Subscription collection {#step-1--subscription-collection}

The mobile application is downloaded by the user from the App Store or from Google Play. This application contains the connection settings (iOS certificate and project key for Android) and the integration key. The first time the application is opened, (depending on configuration), the user can be asked to enter registration information (@userKey: email or account number for instance). At the same time, the application questions the notification service to collect a notification ID (push ID). All this information (connection settings, integration key, notification identifier, userKey) is sent to Adobe Campaign.

![](assets/nmac_register_view.png)

### Step 2: Delivery {#step-2--delivery}

Marketers target application subscribers. The delivery process sends the connection settings to the notification service (iOS certificate and project key for Android), the notification ID (push ID) and the content of the notification. The notification service sends notifications to the targeted terminals.

The following information is available in Adobe Campaign:

* Android only: number of devices that have displayed the notification (impressions)
* Android and iOS: number of clicks on the notification

![](assets/nmac_delivery_view.png)

The Adobe Campaign server must be able to contact the APNs server on the 443 port for iOS HTTP/2 connector.

To check that it works correctly, use the following commands:

* For tests:

  ```
  telnet gateway.sandbox.push.apple.com
  ```

* In production:

  ```
  telnet gateway.push.apple.com
  ```

With the iOS HTTP/2 connector, the MTA, web server and workflow server must be able to contact the APNs on port 443.

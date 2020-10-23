---
title: Configuring the mobile application in Adobe Campaign 
description: Learn how to start with the mobile application configuration
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
---

# Get started with the app configuration

You can find in this section a configuration sample based on a company which sells online holiday packages. His mobile application (Neotrips) is available to its customers in two versions: Neotrips for Android and Neotrips for iOS.

To send push notifications in Adobe Campaign, you need to:

* Create a **[!UICONTROL Mobile application]** type information service for the Neotrips mobile application. Refer to [this section for iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). and [this section for Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Add the iOS and Android versions of the application to this service.
* Create a delivery for both iOS and Android. [Refer to this page](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Go to the **[!UICONTROL Subscriptions]** tab of the service to view the list of subscribers to the service, i.e. all people who have installed the application on their mobile and agreed to receive notifications.

## Installing the package {#installing-package-ios}

As a hybrid/hosted customer, contact Adobe Customer Care team to access push notification channel in Campaign. 

As an on-premise customer, you need to perform the following installation steps:

1. Access the package import wizard from **[!UICONTROL Tools > Advanced > Package import...]** in the Adobe Campaign client console.

   ![](assets/package_ios.png)

1. Select **[!UICONTROL Install a standard package]**.

1. In the list that appears, check **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Click **[!UICONTROL Next]**, then **[!UICONTROL Start]** to start the package installation.

   Once the packages are installed, the progress bar shows **100%** and you can see the following message in the installation logs: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** the installation window.

Once this step is done, you can configure your Android and iOS apps.
Refer to these sections:

* [Configuration steps for iOS](../../delivery/using/configuring-the-mobile-application.md)

* [Configuration steps for Android](../../delivery/using/configuring-the-mobile-application-android.md)

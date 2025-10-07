---
product: campaign
title: Get started with mobile app channel 
description: Get started with mobile app channel in Adobe Campaign
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
---
# Get started with mobile app channel{#about-mobile-app-channel}

With Adobe Campaign, create push notification deliveries to send personalized messages to your mobile app users.

Push notifications let you engage users on iOS and Android in real time. Whether sending updates, announcements, or promotions, you can control content, timing, and targeting. Learn how to set up and use the push channel, managing subscriptions, integrating with APNs and FCM, and personalizing messages in [Adobe Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/emails/email){target=_blank}.

As part of the Campaign v8 promotion initiative, the Campaign Classic documentation has been reorganized. Common features are now only available in the Campaign v8 documentation set.

>[!BEGINTABS]

>[!TAB Push channel documentation] 

To learn more about push notification channel, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}.

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}


>[!TAB Push delivery creation]

Learn the key steps related to push delivery creation in the Campaign v8 documentation:

* [Create a push notification](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-create){target="_blank"}: Learn about the different steps needed to create a push delivery.
* [Send and monitor the push notification](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-test){target="_blank"}: Learn how to validate, send and track your deliveries. 
* [Design an Android rich push delivery](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html){target="_blank"}: Learn how to create and configure rich push notifications for Android devices.
* [Design an iOS rich push delivery](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html){target="_blank"}: Learn how to design and configure rich push notifications for iOS devices in Adobe Campaign v8.


>[!TAB Push parameters]

Refer to these pages to learn about push parameters in the Campaign v8 documentation:

* [Configuration prerequisites](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#before-starting){target="_blank"}: Learn how to set up permissions and configure your app.
* [Configure the launch property](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#launch-property){target="_blank"}: Learn how to set up a mobile tag property in Adobe Experience Platform Data Collection to enable push notifications.
* [Configure push services mobile services](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#push-service){target="_blank"}: Set up iOS and Android push services in Adobe to enable targeted push notifications for your mobile app users.
* [Configure the extension in your mobile property](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#configure-extension){target="_blank"}: Integrate the Campaign extension into your mobile property to enable push notifications and manage user interactions effectively.

>[!ENDTABS]


The following information is specific to Campaign Classic.

+++ **Package installation**

![](assets/do-not-localize/how-to-video.png) [Learn how to install the mobile app package in video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html#sending-messages)

As a hybrid/hosted customer, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team to access push notification channel in Campaign. 

As an on-premise customer, you need to install a built-in package.

>[!CAUTION]
>
>Learn more about Campaign built-in packages, best practices and recommendations in [this page](../../installation/using/installing-campaign-standard-packages.md).

Installation steps are:

1. Access the package import assistant from **[!UICONTROL Tools > Advanced > Import package]** in the Adobe Campaign client console.

   ![](assets/package_ios.png)

1. Select **[!UICONTROL Install a standard package]**.

1. In the list that appears, check **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Click **[!UICONTROL Next]**, then **[!UICONTROL Start]** to start the package installation.

   Once the packages are installed, the progress bar shows **100%** and you can see the following message in the installation logs: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** the installation window.

Once this step is done, you can configure your Android and iOS apps. Refer to the Campaign v8 [documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target="_blank"}.

+++

+++ **Troubleshooting**

If your mobile device is connected to Wi-Fi and you are not receiving notifications, check that the FCM/APNs ports are not being blocked by your firewall.

**Android**: The mobile device connects to the FCM servers on ports 5228 to 5230. You therefore must configure your firewall so that it authorizes connection with FCM. The ports to open are: 5228 (the most frequently used), 5229 and 5230.

**iOS**:

HTTP/2 connector: you must allow communication to and from the following servers:

* api.push.apple.com: port 443
* api.development.push.apple.com: port 443

>[!NOTE]
>
>For more information on the two connectors, refer to the Campaign v8 [documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html){target="_blank"}.

+++

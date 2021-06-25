---
product: campaign
title: Configuring the Android mobile application in Adobe Campaign
description: Learn how to set up your mobile application for Android
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
index: y
internal: n
snippet: y
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
---
# Configuration steps for Android

Once the package is installed, you can define your Android app settings in Adobe Campaign Classic.

>[!NOTE]
>
>To learn how to configure your app for iOS and how to create a delivery for iOS, refer to this [section](configuring-the-mobile-application.md).

Key steps are:

1. [Configure the Android external account](#configuring-external-account-android)
1. [Configure the Android service](#configuring-android-service)
1. [Create the mobile app in Campaign](#creating-android-app)
1. [Extend the app schema with additional data](#extend-subscription-schema)

You will then be able to [create an Android rich notification](create-notifications-android.md).

## Configure Android external account {#configuring-external-account-android}

For Android, two connectors are available:

* The V1 connector which allows one connection per MTA child. 
* The V2 connector which allows simultaneous connections to the FCM server to improve throughput.

To choose which connector you want to use, follow these steps:

1. Go to **[!UICONTROL Administration > Platform > External accounts]**.
1. Select the **[!UICONTROL Android routing]** external account.
1. In the **[!UICONTROL Connector]** tab, fill in the **[!UICONTROL JavaScript used in the connector]** field:

   For Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > You can also configure it as follow https://localhost:8080/nms/jsp/androidPushConnector.js but we advise you to use version 2 of the connector.

   ![](assets/nmac_connectors3.png)

1. For Android V2, one additional parameter is available in the Adobe Server configuration file (serverConf.xml):

    * **maxGCMConnectPerChild**: Maximum limit of parallel HTTP requests to the FCM initiated by each child server (8 by default).

## Configure an Android service {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Learn how to configure an Android service in video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. Go to the **[!UICONTROL Profiles and Targets > Services and subscriptions]** node and click **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Define a **[!UICONTROL Label]** and an **[!UICONTROL Internal name]**.
1. Go to the **[!UICONTROL Type]** field and select **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >The default **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** target mapping is linked to the recipients table. If you want to use a different target mapping, you need to create a new target mapping and enter it in the **[!UICONTROL Target mapping]** field of the service. For more on creating target mapping, refer to the [this section](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Then click the **[!UICONTROL Add]** button to select the application type.

   ![](assets/nmac_service_2.png)

1. Create your Android application. For more on this, refer to [this section](configuring-the-mobile-application-android.md#creating-android-app).

## Create the Android mobile application {#creating-android-app}

After creating your service, you now need to create your Android application:

1. From your newly created service, click the **[!UICONTROL Add]** button to select the application type.

   ![](assets/nmac_service_2.png)

1. Select **[!UICONTROL Create an Android application]** and enter a **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Make sure the same **[!UICONTROL Integration key]** is defined in Adobe Campaign and in the application code via the SDK. For more on this, refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).

    >[!NOTE]
    >
    > The **[!UICONTROL Integration key]** is fully customizable with string value but needs to be exactly the same as the one specified in the SDK.

1. Select the **[!UICONTROL API version]**: HTTP v1 or HTTP (legacy). These configurations are detailed in [this section](#select-api-version)

1. Fill in the **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** fields.

1. Click **[!UICONTROL Finish]** then **[!UICONTROL Save]**. Your Android application is now ready to be used in Campaign Classic.

By default, Adobe Campaign saves a key in the **[!UICONTROL User identifier]** (@userKey) field of the **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** table. This key enables you to link a subscription to a recipient. To collect additional data (such as a complex reconciliation key), you need to apply the following configuration:

### Select the API version{#select-api-version}

After creating service and a new mobile application, you need to configure your mobile application depending on the chosen API version.

* **HTTP v1** configuration is detailed in [this section](configuring-the-mobile-application-android.md#android-service-httpv1).
* **HTTP (legacy)** configuration is detailed in [this section](configuring-the-mobile-application-android.md#android-service-http).

#### Configure HTTP v1 API{#android-service-httpv1}

To configure the HTTP v1 API version, follow the steps below:

1. In your **[!UICONTROL Mobile application creation wizard]** window, select **[!UICONTROL HTTPV1]** in the **[!UICONTROL API version]** drop-down.

1. Click **[!UICONTROL Load project json file to extract projet details...]** to load directly your JSON key file. For more information on how to extract your JSON file, refer to [this page](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   You can also enter manually the following details:
      * **[!UICONTROL Project Id]**
      * **[!UICONTROL Private Key]**
      * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Click **[!UICONTROL Test the connection]** to check that your configuration is correct and that the marketing server has access to the FCM.

   >[!CAUTION]
   >
   >For Mid-Sourcing Deployment, the **[!UICONTROL Test connection]** button will not check if the MID server has access to the FCM server.

   ![](assets/nmac_android_11.png)

1. As an option, you can enrich a push message content with some **[!UICONTROL Application variables]** if needed. These are fully customizable and a part of the message payload sent to the mobile device.

1. Click **[!UICONTROL Finish]** then **[!UICONTROL Save]**. Your Android application is now ready to be used in Campaign Classic.

Below are the FCM payload names to further personalize your push notification:

| Message type | Configurable message element (FCM payload name) |  Configurable options (FCM payload name) |
|:-:|:-:|:-:|
| data message  | N/A  | validate_only  |
| notification message |  title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

<br>
<br>

#### Configure HTTP (legacy) API{#android-service-http}

To configure the HTTP (legacy) API version, follow the steps below:

1. In your **[!UICONTROL Mobile application creation wizard]** window, select **[!UICONTROL HTTP (legacy)]** in the **[!UICONTROL API version]** drop-down.

1. Enter the **[!UICONTROL Project key]** that was provided by the developer of the mobile application.

1. As an option, you can enrich a push message content with some **[!UICONTROL Application variables]** if needed. These are fully customizable and a part of the message payload sent to the mobile device.

   In the following example, we add **title**, **imageURL** and **iconURL** to create rich push notification and then provides the application with the image, title and icon to display within the notification.

   ![](assets/nmac_android_2.png)

1. Click **[!UICONTROL Finish]** then **[!UICONTROL Save]**. Your Android application is now ready to be used in Campaign Classic.

Below are the FCM payload names to further personalize your push notification:

| Message type | Configurable message element (FCM payload name) |  Configurable options (FCM payload name) |
|:-:|:-:|:-:|
| data message  | N/A  | dryRun  |
| notification message |  title, body, android_channel_id, icon, sound, tag, color, click_action <br> | dryRun |

<br>

## Extend the appsubscriptionRcp schema {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Learn how to extend the appsubscriptionRcp schema in video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

You need to extend the **appsubscriptionRcp** to define new additional fields to store parameters from the app in Campaign database . These fields will be used for personalization for example. To do this:

1. Create an extension of the **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schema and define the new fields. Learn more about schema extension in [this page](../../configuration/using/about-schema-edition.md)

1. Define the mapping in the **[!UICONTROL Subscription parameters]** tab.

   >[!CAUTION]
   >
   >Make sure the configuration names in the **[!UICONTROL Subscription parameters]** tab are the same as those in the mobile application code. Refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).

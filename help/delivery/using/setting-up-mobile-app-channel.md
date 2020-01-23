---
title: Setting up mobile app channel
seo-title: Setting up mobile app channel
description: Setting up mobile app channel
seo-description: 
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
index: y
internal: n
snippet: y
---

# Setting up mobile app channel{#setting-up-mobile-app-channel}

## Introduction {#introduction}

>[!CAUTION]
>
>Mobile App Channel implementation has to be performed by expert users. If you need to be assisted, contact your Adobe Account executive or Professional services partner.

You can create several versions of your mobile application (iOS, Android): the Mobile App channel option enables you to send notifications to terminals which the application is installed on.

To use the functionalities of the Adobe Campaign Mobile App Channel, you need to change/adapt your mobile application to integrate it into the Adobe Campaign platform.

Two Campaign Classic SDKs are available, one for Android and one for iOS, for an easy integration of your mobile application with Adobe Campaign. A deep technical knowledge of Java and Objective-C is required. A detailed description of Campaign SDK is found in [Integrating Campaign SDK into the mobile application](#integrating-campaign-sdk-into-the-mobile-application).

>[!NOTE]
>
>Libraries provided by Adobe Campaign are designed to be used with Xcode (iOS) and Android Studio (Android).

## Configuration steps {#configuration-steps}

### Creating the application {#creating-the-application}

If you don't have a mobile application (app), the application developer needs to create it and integrate the SDK. If the mobile application exists, the developer needs to adapt it by integrating the Adobe Campaign SDK and adding the settings specific to the service. For a description of the SDK, refer to [Integrating Campaign SDK into the mobile application](#integrating-campaign-sdk-into-the-mobile-application).

>[!CAUTION]
>
>The application must have been configured for Push actions BEFORE any integration to Adobe Campaign SDK.
>
>If this is not the case, please refer to [this page](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/).

### Collecting information {#collecting-information-}

To configure the application, you have to collect the technical specifications which define the set of parameters that enable Adobe Campaign and the mobile application to communicate. These parameters are:

* **the integration key**: each application has a unique key. This key lets you link the Adobe Campaign service and the mobile application. Refer to [Configuring a mobile application in Adobe Campaign](../../delivery/using/configuring-the-mobile-application-in-adobe-campaign.md).
* **the variables**: define the behavior of the application when you activate the notification. Refer to [Configuring a mobile application in Adobe Campaign](../../delivery/using/configuring-the-mobile-application-in-adobe-campaign.md).
* **the subscription settings**: by default, Adobe Campaign recovers the **@userKey** field that enables you to reconcile mobile devices with the recipients in the database. If you want to collect additional data (such as a complex reconciliation key), you can define subscription settings. Refer to [Configuring a mobile application in Adobe Campaign](../../delivery/using/configuring-the-mobile-application-in-adobe-campaign.md).
* **the sounds** (iOS only): if the selected sound isn't a system sound, the sound file must be embedded into the mobile application. Refer to [Configuring iOS external account](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios).
* **the URL of the marketing server and the tracking server**: the Adobe Campaign administrator must provide the application developer with the URLs of the marketing server and the URLs of the tracking server. For more on this, refer to: [Integrating Campaign SDK into the mobile application](#integrating-campaign-sdk-into-the-mobile-application).

### Creating the service {#creating-the-service}

The Adobe Campaign administrator needs to create and configure a service linked to the mobile application. For more on this, refer to [Configuring the mobile application in Adobe Campaign](#configuring-the-mobile-application-in-adobe-campaign).

### Testing the application {#testing-the-application}

On iOS, you need to create an application that uses the sandbox mode for tests and approvals. Then, within the same Adobe Campaign service, create a new production type application and enter the relevant certificate. For more on this, refer to the documentation on the Apple notifications service.

On Android, you only need to create one application. Test the full subscription and delivery collection process on your application before making it public.

## Data path {#data-path}

The following schemas detail the steps that enable a mobile application to exchange data with Adobe Campaign. This process involves three entities:

* the mobile application
* the notification service: APNS (Apple Push Notification Service) for Apple and FCM (Firebase Cloud Messaging) for Android
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

The Adobe Campaign server must be able to contact the APNS server on the following ports:

* 2195 (sending) and 2186 (feedback service) for iOS binary connector
* 443 for iOS HTTP/2 connector

To check that it works correctly, use the following commands:

* For tests:

  ```
  telnet gateway.sandbox.push.apple.com
  ```

* In production:

  ```
  telnet gateway.push.apple.com
  ```

If an iOS binary connector is used, the MTA and web server must be able to contact the APNS on port 2195 (sending), the workflow server must be able to contact the APNS on port 2196 (feedback service).

If an iOS HTTP/2 connector is used, the MTA, web server and workflow server must be able to contact the APNS on port 443.

## Integrating Campaign SDK into the mobile application {#integrating-campaign-sdk-into-the-mobile-application}

Campaign SDKs for iOS and Android are one of the components of the Mobile App Channel module.

>[!NOTE]
>
>To get Campaign SDK (previously known as Neolane SDK), contact Adobe Customer Care.

The goal of the SDK is to facilitate the integration of a mobile application into the Adobe Campaign platform.

To learn more on the different Android and iOS versions supported, refer to the [Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#MobileSDK) .

### Loading Campaign SDK {#loading-campaign-sdk}

* **In Android**: the **neolane_sdk-release.aar** file must be linked to the project.

  The following permission grants access to the Adobe Campaign server:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
  ```

  The following permission allows you to recover a telephone's unique ID:

  ```
  <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
  ```

  From version 1.0.24 of the SDK, this permission is only used for versions older than Android 6.0.

  From version 1.0.26 of the SDK, this permission is no longer used.

* **In iOS**: the **libNeolaneSDK.a** and **Neolane_SDK.h** files must be linked to the project. From version 1.0.24 of the SDK, the option **ENABLE_BITCODE** is activated.

  >[!NOTE]
  >
  >For version 1.0.25 of the SDK, the four architectures are available in the **Neolane_SDK.h** file.

### Declaring integration settings {#declaring-integration-settings}

To integrate Campaign SDK into the mobile application, the functional administrator must provide the following information to the developer:

* **An integration key**: to enable the Adobe Campaign platform to identify the mobile application.

  >[!NOTE]
  >
  >This integration key is entered in the Adobe Campaign console, in the **[!UICONTROL Information]** tab of service dedicated to the mobile application. Refer to [Configuring a mobile application in Adobe Campaign](../../delivery/using/configuring-the-mobile-application-in-adobe-campaign.md).

* **A tracking URL**: that matches the address of the Adobe Campaign tracking server.
* **A marketing URL**: to enable the collection of subscriptions.

* **In Android**:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
  ```

* **In iOS**:

  ```
  Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl setMarketingHost:strMktHost];
  [nl setTrackingHost:strTckHost];
  [nl setIntegrationKey:strIntegrationKey];
  ```

### Registration function {#registration-function}

The registration function enables you to:

* send the notification ID or push ID (deviceToken for iOS and registrationID for Android) to Adobe Campaign.
* recover the reconciliation key or userKey (email or account number, for instance)

* **In Android**:

  ```
  void registerInNeolane(String registrationId, String userKey, Context context)
  {
   try{
    Neolane.getInstance().registerDevice(registrationToken, userKey, null, context);
   } catch (NeolaneException e){
    //...
   } catch (IOException e){
    //...
   }
  }
  ```

  If you use FCM (Firebase Cloud Messaging), we advise you use the **registerDevice** function when calling the **onTokenRefresh** function to notify Adobe Campaign of the change in the user's mobile device token.

  ```
  public class NeoTripFirebaseInstanceIDService extends FirebaseInstanceIdService {
    @Override
    public void onTokenRefresh() {
      String registrationToken = FirebaseInstanceId.getInstance().getToken();
      NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
      ...
      ...
      // Neolane Registration
      neolaneAs.registerDevice(registrationToken, userKey, additionnalParam, this, new NeolaneAsyncRunner.RequestListener() {
      public void onComplete(String e, Object state) { ... }
      public void onNeolaneException(NeolaneException e, Object state) { ... }
      public void onIOException(IOException e, Object state) { ... }
      });
      ...
      ...
    }
  }
  ```

* **In iOS**:

  ```
  // Callback called on successful registration to the APNS
  - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
  {
      // Pass the token to Adobe Campaign
      Neolane_SDK *nl = [Neolane_SDK getInstance];
      [nl registerDevice:tokenString:self.userKey:dic];
  }
  ```

### Tracking function {#tracking-function}

* **In Android**:

  Tracking functions allow you to track notification activations (opens) and notification displays (screenshot).

  To track the notification display (done by calling the **notifyReceive** function of the SDK), follow the implementation below. Note that if you use FCM (Firebase Cloud Messaging), we advise you to use the **notifyReceive** function when the **onMessageReceived** function is called by the Android system.

  ```
  package com.android.YourApplication;

  import android.content.Context;
  import android.content.SharedPreferences;
  import android.os.Bundle;
  import android.util.Log;

  import com.google.firebase.messaging.FirebaseMessagingService;
  import com.google.firebase.messaging.RemoteMessage;

  import java.util.Iterator;
  import java.util.Map;
  import java.util.Map.Entry;

  public class YourApplicationFirebaseMessagingService extends FirebaseMessagingService {
    private static final String TAG = "MyFirebaseMsgService";

    @Override
    public void onMessageReceived(RemoteMessage message) {
      Log.d(TAG, "Receive message from: " + message.getFrom());
      Map<String,String> payloadData = message.getData();
      final Bundle extras = new Bundle();
      final Iterator<Entry<String, String>> iter = payloadData.entrySet().iterator();
      while(iter.hasNext())
      {
        final Entry<String, String>  entry =iter.next();
        extras.putString(entry.getKey(), entry.getValue());
      }

      SharedPreferences settings = this.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      String mesg = payloadData.get("_msg");
      String title = payloadData.get("title");
      String url = payloadData.get("url");
      String messageId = payloadData.get("_mId");
      String deliveryId = payloadData.get("_dId");
      YourApplicationActivity.handleNotification(this, mesg, title, url, messageId, deliveryId, extras);
    }
  }
  ```

  ```
  public static void handleNotification(Context context, String message, String title, String url, String messageId, String deliveryId, Bundle extras){
      if( message == null ) message = "No Content";
      if( title == null )   title = "No title";
      if( url == null )     url = "https://www.tripadvisor.fr";
      int iconId = R.drawable.notif_neotrip;

      // notify Neolane that a notification just arrived
      NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
      nas.notifyReceive(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
        public void onNeolaneException(NeolaneException arg0, Object arg1) {}
        public void onIOException(IOException arg0, Object arg1) {}
        public void onComplete(String arg0, Object arg1){}
      });
      if (yourApplication.isActivityVisible())
      {
        Log.i("INFO", "The application has the focus" );
        ...
      }
      else
      {
        // notification creation :
        NotificationManager notificationManager = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);
        Notification notification;

        // Activity to start :
        Intent notifIntent = new Intent(context.getApplicationContext(), NotificationActivity.class);
        notifIntent.putExtra("notificationText", message);
        notifIntent.putExtra(NotificationActivity.NOTIFICATION_URL_KEYNAME, url);
        notifIntent.putExtra("_dId", deliveryId);
        notifIntent.putExtra("_mId", messageId);
        notifIntent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
        PendingIntent contentIntent = PendingIntent.getActivity(context, 1, notifIntent, PendingIntent.FLAG_UPDATE_CURRENT);

        notification = new Notification.Builder(context)
                .setContentTitle(title)
                .setContentText(message)
                .setSmallIcon(iconId)
                .setContentIntent(contentIntent)
                .build();

        // launch the notification :
        notification.flags |= Notification.FLAG_AUTO_CANCEL;
        notificationManager.notify(Integer.valueOf(messageId), notification);
      }
  }
  ```

  Here is an implementation example for tracking a notification open (executed by calling the **notifyOpening** function of the SDK). The **NotificationActivity** class corresponds to the one used to create the **notifIntent** object in the previous example.

  ```
  public class NotificationActivity extends Activity {
   public static final String NOTIFICATION_URL_KEYNAME = "NotificationUrl";
   .....
   public void onCreate(Bundle savedBundle) {
    super.onCreate(savedBundle);
    setContentView(R.layout.notification_viewer);  
    .....  
    Bundle extra = getIntent().getExtras();  
    .....  
    //get the messageId and the deliveryId to do the tracking  
    String deliveryId = extra.getString("_dId");
    String messageId = extra.getString("_mId");
    if (deliveryId != null && messageId != null) {
     NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
     neolaneAs.notifyOpening(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
      public void onNeolaneException(NeolaneException arg0, Object arg1) {}
      public void onIOException(IOException arg0, Object arg1) {}
      public void onComplete(String arg0, Object arg1) {}
      });
    }
   }
  }
  ```

* **In iOS**:

  The tracking function allows you to track when notifications are activated (opens).

  ```
  (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
  {
  if( launchOptions ) { // Retrieve notification parameters here ... // Track application opening Neolane_SDK
  *nl = [Neolane_SDK getInstance]; [nl track:launchOptions:NL_TRACK_CLICK]; } 
  ...  
  completionHandler(UIBackgroundFetchResultNoData);
  }
  ```

  >[!NOTE]
  >
  >From version 7.0, once the **application:didReceiveRemoteNotification:fetchCompletionHandler** function is implemented, the operating system only calls this function. The **application:didReceiveRemoteNotification** function is therefore not called.

### Silent notification tracking {#silent-notification-tracking}

iOS lets you send silent notifications, a notification or data which will be directly sent to a mobile application without displaying it. Adobe Campaign allows you to track them.

To track your silent notification, follow the example below:

```
// AppDelegate.m
...
...
#import "AppDelegate.h"
#import "Neolane_SDK.h"
...
...
// Callback called when the application is already launched (whether the application is running foreground or background)
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
{
 NSLog(@"IN didReceiveRemoteNotification:fetchCompletionHandler");
 if (launchOptions) NSLog(@"IN launchOptions: %@", [launchOptions description]);
 NSLog(@"Application state: %ld", (long)application.applicationState);

 // Silent Notification (specific case, can use NL_TRACK_RECEIVE as the user doesn't have click/open the notification)
 if ([launchOptions[@"aps"][@"content-available"] intValue] == 1 )
       {
  NSLog(@"Silent Push Notification");
  ...  
  ...
  //Call receive tracking
        Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl track:launchOptions:NL_TRACK_RECEIVE];

  completionHandler(UIBackgroundFetchResultNoData); //Do not show notification
  return;
 }  
 ...
 ...
        completionHandler(UIBackgroundFetchResultNoData);
}
```

### RegisterDeviceStatus delegate {#registerdevicestatus-delegate}

>[!NOTE]
>
>Please note that this is exclusive to iOS.

In iOS, the delegate protocol allows you to get the result of the **registerDevice** call and can be used to know if an error occured during registration.

The **registerDeviceStatus** prototype is:

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**Status** allows you to know if a registration succeeded or if an error occured.

**ErrorReason** provides you with more information on the errors that occurred. For more information on available errors and their descriptions, refer to the table below.

<table> 
 <thead>
  <tr>
   <th> Status<br /> </th>
   <th> Description<br /> </th>
   <th> ErrorReason<br /> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td> ACCRegisterDeviceStatusSuccess <br /> </td>
   <td> Registration Succeeded<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty <br /> </td>
   <td> The ACC marketing server hostname is empty or not set.<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureIntegrationKeyEmpty <br /> </td>
   <td> The integration key is empty or not set.<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureConnectionIssue<br /> </td>
   <td> Connection issue with ACC<br /> </td>
   <td> More information (in OS current language)<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnknownUUID<br /> </td>
   <td> The provided UUID (integration key) is unknown.<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnexpectedError<br /> </td>
   <td> Unexpected error returned to ACC server.<br /> </td>
   <td> The error message returned to ACC.<br /> </td>
  </tr>
 </tbody>
</table>

**Neolane_SDKDelegate** protocol and **registerDeviceStatus** delegate definition is as follows:

```
//  Neolane_SDK.h
//  Neolane SDK
..
.. 
// Register Device Status Enum
typedef NS_ENUM(NSUInteger, ACCRegisterDeviceStatus) {
 ACCRegisterDeviceStatusSuccess,                               // Resistration Succeed
 ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty,   // The ACC marketing server hostname is Empty or not set
 ACCRegisterDeviceStatusFailureIntegrationKeyEmpty,            // The integration key is empty or not set
 ACCRegisterDeviceStatusFailureConnectionIssue,                // Connection issue with ACC, more information in errorReason
 ACCRegisterDeviceStatusFailureUnknownUUID,                    // The provided UUID (integration key) is unknown
 ACCRegisterDeviceStatusFailureUnexpectedError                 // Unexpected error returned by ACC server, more information in errorReason
};
// define the protocol for the registerDeviceStatus delegate
@protocol Neolane_SDKDelegate <NSObject>
@optional
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason;
@end
@interface Neolane_SDK: NSObject {
} 
...
...
// registerDeviceStatus delegate
@property (nonatomic, weak) id <Neolane_SDKDelegate> delegate;
...
...
@end
```

To implement **registerDeviceStatus** delegate, follow these steps:

1. Implement the **setDelegate** during the SDK initialization.

   ```
   // AppDelegate.m
   ...
   ... 
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
   {
   ...
   ...
    // Get the stored settings

    NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
    NSString *strMktHost = [defaults objectForKey:@"mktHost"];
    NSString *strTckHost = [defaults objectForKey:@"tckHost"];
    NSString *strIntegrationKey = [defaults objectForKey:@"integrationKey"];
    userKey = [defaults objectForKey:@"userKey"];

    // Configure Neolane SDK on first launch
    Neolane_SDK *nl = [Neolane_SDK getInstance];
    [nl setMarketingHost:strMktHost];
    [nl setTrackingHost:strTckHost];
    [nl setIntegrationKey:strIntegrationKey];
    [nl setDelegate:self];    // HERE
   ...
   ...
   }
   ```

1. Add the protocol in the **@interface** of your class.

   ```
   //  AppDelegate.h

   #import <UIKit/UIKit.h>
   #import <CoreLocation/CoreLocation.h>
   #import "Neolane_SDK.h"

   @class LandingPageViewController;

   @interface AppDelegate : UIResponder <UIApplicationDelegate, CLLocationManagerDelegate, Neolane_SDKDelegate> {
       CLLocationManager *locationManager;
       NSString *userKey;
       NSString *mktServerUrl;
       NSString *tckServerUrl;
       NSString *homeURL;
       NSString *strLandingPageUrl;
       NSTimer *timer;
   }
   ```

1. Implement the delegate in the **AppDelegate**.

   ```
   //  AppDelegate.m

   #import "AppDelegate.h"
   #import "Neolane_SDK.h"
   #import "LandingPageViewController.h"
   #import "RootViewController.h"
   ...
   ...
   - (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason
   {
       NSLog(@"registerStatus: %lu",status);

       if ( errorReason != nil )
           NSLog(@"errorReason: %@",errorReason);

       if( status == ACCRegisterDeviceStatusSuccess )
       {
           // Registration successful
           ...
           ...
       }
       else { // An error occurred
           NSString *message;
           switch ( status ){
               case ACCRegisterDeviceStatusFailureUnknownUUID:
                   message = @"Unkown IntegrationKey (UUID)";
                   break;
               case ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty:
                   message = @"Marketing URL not set or Empty";
                   break;
               case ACCRegisterDeviceStatusFailureIntegrationKeyEmpty:
                   message = @"Integration Key not set or empty";
                   break;
               case ACCRegisterDeviceStatusFailureConnectionIssue:
                   message = [NSString stringWithFormat:@"%@ %@",@"Connection issue:",errorReason];
                   break;
               case ACCRegisterDeviceStatusFailureUnexpectedError:
               default:
                   message = [NSString stringWithFormat:@"%@ %@",@"Unexpected Error",errorReason];
                   break;
           }
    ...
    ...
       }
   }
   @end
   ```

### Variables {#variables}

The variables let you define mobile application behavior after receiving a notification. These variables must be defined in the mobile application code and in the Adobe Campaign console, in the **[!UICONTROL Variables]** tab in the dedicated mobile application service (see [Configuring a mobile application in Adobe Campaign](../../delivery/using/configuring-the-mobile-application-in-adobe-campaign.md)). Here is an example of a code that allows a mobile application to collect any added variables in a notification. In our example, we are using the "VAR" variable.

* **In Android**:

  ```
  public void onReceive(Context context, Intent intent) {
       ...
      String event = intent.getStringExtra("VAR");
       ...
  }
  ```

* **In iOS**:

  ```
  - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
  {
      ....
      if( launchOptions )
      {
          // When application is not already launched, the notification data if any are stored in the key 'UIApplicationLaunchOptionsRemoteNotificationKey'
          NSDictionary *localLaunchOptions = [launchOptions objectForKey:@"UIApplicationLaunchOptionsRemoteNotificationKey"];
          if( localLaunchOptions )
          {
           ...
           [localLaunchOptions objectForKey:@"VAR"];
          ...
          }
     }
  }

  // Callback called when the application is already launched (whether the application is running foreground or background)
  - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  {
      if( launchOptions )
      {
       ...
          [launchOptions objectForKey:@"VAR"];
      }
  }
  ```

>[!CAUTION]
>
>Adobe recommends choosing short variable names because notification size is limited to 4kB for iOS and Android.

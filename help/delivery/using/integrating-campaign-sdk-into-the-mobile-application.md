---
product: campaign
title: Integrate Campaign SDK
description: Learn how to integrate Campaign SDK to your mobile app
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
version: Classic v7
exl-id: a5f6b82d-5561-4e56-b2ed-7fd6fd8c2b55
---
# Integrating Campaign SDK with your app {#integrating-campaign-sdk-into-the-mobile-application}

Campaign SDKs for iOS and Android are one of the components of the Mobile App Channel module.

>[!NOTE]
>
>To get Campaign SDK (previously known as Neolane SDK), contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

The goal of the SDK is to facilitate the integration of a mobile application into the Adobe Campaign platform.

To learn more on the different Android and iOS versions supported, refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md#MobileSDK) .

## Loading Campaign SDK {#loading-campaign-sdk}

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

## Declaring integration settings {#declaring-integration-settings}

To integrate Campaign SDK into the mobile application, the functional administrator must provide the following information to the developer:

* **An integration key**: to enable the Adobe Campaign platform to identify the mobile application.

  >[!NOTE]
  >
  >This integration key is entered in the Adobe Campaign console, in the **[!UICONTROL Information]** tab of service dedicated to the mobile application. Refer to [Configuring a mobile application in Adobe Campaign](configuring-the-mobile-application.md).

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

## Registration function {#registration-function}

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
  // Callback called on successful registration to the APNs
  - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
  {
      // Pass the token to Adobe Campaign
      Neolane_SDK *nl = [Neolane_SDK getInstance];
      [nl registerDevice:tokenString:self.userKey:dic];
  }
  ```

## Tracking function {#tracking-function}

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
    SharedPreferences settings = context.getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
    Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
    Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));
    Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
 
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
  public void onCreate(Bundle savedBundle) {
    [...]
    Bundle extra = getIntent().getExtras();
    if (extra != null) {
      // reinit the acc sdk
      SharedPreferences settings = getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
      Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));               
      Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
 
      // Get the messageId and the deliveryId to do the tracking
      String deliveryId = extra.getString("_dId");
      String messageId = extra.getString("_mId");
      if (deliveryId != null && messageId != null) {
        try {
          Neolane.getInstance().notifyOpening(Integer.valueOf(messageId), Integer.valueOf(deliveryId));
        } catch (NeolaneException e) {
          // ...
        } catch (IOException e) {
          // ...
        }
      }
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

## Silent notification tracking {#silent-notification-tracking}

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

## Variables {#variables}

The variables let you define mobile application behavior after receiving a notification. These variables must be defined in the mobile application code and in the Adobe Campaign console, in the **[!UICONTROL Variables]** tab in the dedicated mobile application service (see [Configuring a mobile application in Adobe Campaign](configuring-the-mobile-application.md)). Here is an example of a code that allows a mobile application to collect any added variables in a notification. In our example, we are using the "VAR" variable.

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

## Notification Service Extension {#notification-service-extension}

**For iOS**

The media has to be downloaded at the notification service extension level.

```

#import "NotificationService.h"

@interface NotificationService ()

@property (nonatomic, strong) void (^contentHandler)(UNNotificationContent *contentToDeliver);
@property (nonatomic, strong) UNMutableNotificationContent *bestAttemptContent;

@end

@implementation NotificationService

- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
    NSDictionary *userInfo = nil;
    NSString *url = nil;

    self.contentHandler = contentHandler;
    self.bestAttemptContent = [request.content mutableCopy];

    userInfo = request.content.userInfo;
    if ( userInfo != nil )
    {
        url = userInfo[@"mediaUrl"];  // Get the url of the media to download (Adobe Campaign additional variable)
    }
    ...
    // Perform the download to local storage

```

## Notification Content Extension {#notification-content-extension}

**For iOS**

At this level, you need to:

* Associate your content extension to the category sent by Adobe Campaign:

  If you want your mobile application to display an image, you can set the category value to "image" in Adobe Campaign and in your mobile application, you create a notification extension with the **UNNotificationExtensionCategory** parameter set to "image". When the push notification is received on the device, the extension is called according to the defined category value.

* Define your notification layout

  You need to define a layout with the relevant widgets. For an image, the widget is named **UIImageView**.

* Display your media

  You need to add code to feed the media data to the widget. Here is an example of code for an image:

  ```

  #import "NotificationViewController.h"
  #import <UserNotifications/UserNotifications.h>
  #import <UserNotificationsUI/UserNotificationsUI.h>

  @interface NotificationViewController () <UNNotificationContentExtension>
  
  @property (strong, nonatomic) IBOutlet UIImageView *imageView;
  @property (strong, nonatomic) IBOutlet UILabel *notifContent;
  @property (strong, nonatomic) IBOutlet UILabel *label;
  
  @end

  @implementation NotificationViewController

  - (void)viewDidLoad {
      [super viewDidLoad];
      // Do any required interface initialization here.
  }

  - (void)didReceiveNotification:(UNNotification *)notification {
      self.label.text = notification.request.content.title;
      self.notifContent.text = notification.request.content.body;
      UNNotificationAttachment *attachment = [notification.request.content.attachments objectAtIndex:0];
      if ([attachment.URL startAccessingSecurityScopedResource])
      {
        NSData * imageData = [[NSData alloc] initWithContentsOfURL:attachment.URL];
        self.imageView.image =[UIImage imageWithData: imageData];
        [attachment.URL stopAccessingSecurityScopedResource];
      }
  }
  @end
  
  ```

---
product: campaign
title: 整合Campaign SDK
description: 了解如何將Campaign SDK整合至您的行動應用程式
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Mobile SDK Integration, Push
exl-id: a5f6b82d-5561-4e56-b2ed-7fd6fd8c2b55
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 1%

---

# 將Campaign SDK與您的應用程式整合 {#integrating-campaign-sdk-into-the-mobile-application}



>[!CAUTION]
>
>Adobe強烈建議您在資料收集UI中設定Adobe Campaign擴充功能，以使用Adobe Experience Platform Mobile SDK。 Adobe Experience Platform Mobile SDK可協助您在行動應用程式中支援Adobe的Experience Cloud解決方案和服務。 SDK設定可透過資料收集UI管理，以進行彈性的設定和可擴充的規則型整合。 [進一步了解Adobe Developer檔案](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic){target="_blank"}.

若要取得Campaign SDK（先前稱為Neolane SDK），請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.

若要進一步了解支援的不同Android和iOS版本，請參閱 [相容性矩陣](../../rn/using/compatibility-matrix.md#MobileSDK).

您可以在Campaign SDK整合步驟的下方找到。

+++**載入Campaign SDK**

* **在Android中**:the **neolane_sdk-release.aar** 檔案必須連結至專案。

   下列權限會授予Adobe Campaign伺服器的存取權：

   ```
   Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
   Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
   Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
   ```

   下列權限可讓您復原電話的唯一ID:

   ```
   <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   ```

   從SDK 1.0.24版開始，此權限僅用於Android 6.0以前的版本。

   從SDK 1.0.26版開始，將不再使用此權限。

* **在iOS**:the **libNeolaneSDK.a** 和 **Neolane_SDK.h** 檔案必須連結至專案。 從SDK 1.0.24版開始， **ENABLE_BITCODE** 已啟用。

   >[!NOTE]
   >
   >若為SDK 1.0.25版，可在 **Neolane_SDK.h** 檔案。

+++

+++**聲明整合設定**

若要將Campaign SDK整合至行動應用程式，功能管理員必須向開發人員提供下列資訊：

* **整合金鑰**:讓Adobe Campaign平台識別行動應用程式。

   >[!NOTE]
   >
   >此整合金鑰會在Adobe Campaign主控台中，於 **[!UICONTROL Information]** 行動應用程式專用的服務索引標籤。 請參閱 [在Adobe Campaign中設定行動應用程式](configuring-the-mobile-application.md).

* **追蹤URL**:符合Adobe Campaign追蹤伺服器的位址。
* **行銷URL**:啟用訂閱集合。

* **在Android中**:

   ```
   Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
   Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
   Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
   ```

* **在iOS**:

   ```
   Neolane_SDK *nl = [Neolane_SDK getInstance];
   [nl setMarketingHost:strMktHost];
   [nl setTrackingHost:strTckHost];
   [nl setIntegrationKey:strIntegrationKey];
   ```

+++

+++**註冊功能**

註冊功能允許您：

* 傳送通知ID或推播ID(iOS的deviceToken和Android的registrationID)至Adobe Campaign。
* 恢復調解金鑰或userKey（例如，電子郵件或帳號）

* **在Android中**:

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

   若您使用FCM（Firebase雲端訊息），我們建議您使用 **registerDevice** 函式 **onTokenRefresh** 函式，通知Adobe Campaign使用者行動裝置代號的變更。

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

* **在iOS**:

   ```
   // Callback called on successful registration to the APNs
   - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
   {
       // Pass the token to Adobe Campaign
       Neolane_SDK *nl = [Neolane_SDK getInstance];
       [nl registerDevice:tokenString:self.userKey:dic];
   }
   ```

+++

+++**追蹤函式**

* **在Android中**:

   追蹤函式可讓您追蹤通知啟動（開啟）和通知顯示（螢幕擷取）。

   若要追蹤通知顯示(透過呼叫 **notifyReceive** 函式)，請遵循下列實作。 請注意，若您使用FCM（Firebase雲端傳訊），我們建議您使用 **notifyReceive** 函式 **onMessageReceived** 函式由Android系統呼叫。

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

   以下是追蹤已開啟通知的實作範例(透過呼叫 **notifyOpening** 函式)。 此 **NotificationActivity** 類與用來建立 **notifIntent** 物件。

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

* **在iOS**:

   追蹤函式可讓您追蹤通知啟動（開啟）的時間。

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
   >從7.0版開始， **應用程式:didReceiveRemoteNotification:fetchCompletionHandler** 函式已實現，作業系統僅調用此函式。 此 **application:didReceiveRemoteNotification** 因此不會呼叫函式。

+++

+++**無提示通知追蹤**

iOS可讓您傳送無提示通知、通知或資料，這些通知或資料將直接傳送至行動應用程式，而不會顯示。 Adobe Campaign可讓您追蹤。

若要追蹤無提示通知，請遵循下列範例：

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

+++

+++**RegisterDeviceStatus委派**

>[!NOTE]
>
>請注意，此為iOS專屬。

在iOS中，委派通訊協定可讓您取得 **registerDevice** 呼叫和，可用來知道註冊期間是否發生錯誤。

此 **registerDeviceStatus** 原型為：

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**狀態** 可讓您知道註冊是否成功或是否發生錯誤。

**ErrorReason** 提供您所發生錯誤的詳細資訊。 有關可用錯誤及其說明的詳細資訊，請參閱下表。

<table> 
 <thead>
  <tr>
   <th> 狀態<br /> </th>
   <th> 說明<br /> </th>
   <th> ErrorReason<br /> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td> ACCRegisterDeviceStatusSuccess <br /> </td>
   <td> 註冊成功<br /> </td>
   <td> 空白<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty <br /> </td>
   <td> ACC行銷伺服器主機名稱空白或未設定。<br /> </td>
   <td> 空白<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureIntegrationKeyEmpty <br /> </td>
   <td> 整合金鑰為空或未設定。<br /> </td>
   <td> 空白<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureConnectionIssue<br /> </td>
   <td> ACC的連線問題<br /> </td>
   <td> 更多資訊（使用作業系統當前語言）<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnknownUUID<br /> </td>
   <td> 提供的UUID（整合金鑰）未知。<br /> </td>
   <td> 空白<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnexcipedError<br /> </td>
   <td> 傳回到ACC伺服器的錯誤。<br /> </td>
   <td> 傳回至ACC的錯誤訊息。<br /> </td>
  </tr>
 </tbody>
</table>

**Neolane_SDKDelegate** 協定和 **registerDeviceStatus** 委派定義如下：

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

實作 **registerDeviceStatus** 委派，請遵循下列步驟：

1. 實作 **setDelegate** 在SDK初始化期間。

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

1. 在 **@interface** 你班的。

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

1. 在 **AppDelegate**.

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

+++

+++**變數**

變數可讓您在收到通知後定義行動應用程式行為。 這些變數必須在行動應用程式程式碼和Adobe Campaign主控台中，於 **[!UICONTROL Variables]** 標籤(請參閱 [在Adobe Campaign中設定行動應用程式](configuring-the-mobile-application.md))。 以下是程式碼的範例，可讓行動應用程式收集通知中任何新增的變數。 在範例中，我們使用「VAR」變數。

* **在Android中**:

   ```
   public void onReceive(Context context, Intent intent) {
        ...
       String event = intent.getStringExtra("VAR");
        ...
   }
   ```

* **在iOS**:

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
>Adobe建議選擇短變數名稱，因為iOS和Android的通知大小限制為4kB。

+++

+++**通知服務擴充功能**

**針對iOS**

必須在通知服務擴充層級下載媒體。

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

+++

+++**通知內容擴充功能**

**針對iOS**

在此層級，您需要：

* 將內容擴充功能與Adobe Campaign傳送的類別建立關聯：

   如果您希望行動應用程式顯示影像，您可以在Adobe Campaign中將類別值設為「image」，並在行動應用程式中，使用建立通知擴充功能 **UNNotificationExtensionCategory** 參數設為「影像」。 在裝置上收到推播通知時，會根據定義的類別值呼叫擴充功能。

* 定義通知配置

   您需要使用相關介面工具集來定義配置。 對於影像，介面工具集的名稱為 **UIImageView**.

* 顯示您的媒體

   您需要新增程式碼，將媒體資料饋送至介面工具集。 以下是影像的程式碼範例：

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

+++

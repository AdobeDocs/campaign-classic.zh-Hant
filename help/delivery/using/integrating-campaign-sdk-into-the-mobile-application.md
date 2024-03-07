---
product: campaign
title: 整合Campaign SDK
description: 瞭解如何將Campaign SDK整合至您的行動應用程式
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Mobile SDK Integration, Push
role: User, Developer
exl-id: a5f6b82d-5561-4e56-b2ed-7fd6fd8c2b55
source-git-commit: 209ccbcac20052826dad0c55b35173be20b10114
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 0%

---

# 將Campaign SDK與您的應用程式整合 {#integrating-campaign-sdk-into-the-mobile-application}



>[!CAUTION]
>
>Adobe強烈建議您在資料收集UI中設定Adobe Campaign擴充功能，以使用Adobe Experience Platform Mobile SDK。 Adobe Experience Platform Mobile SDK有助於在行動應用程式中強化Adobe的Experience Cloud解決方案和服務。 SDK的設定可透過資料收集UI進行管理，以進行靈活設定和可擴充的規則型整合。 [在Adobe Developer檔案中進一步瞭解](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic){target="_blank"}.

若要取得Campaign SDK （先前稱為Neolane SDK），請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.

如需瞭解支援的不同Android和iOS版本的詳細資訊，請參閱 [相容性矩陣](../../rn/using/compatibility-matrix.md#MobileSDK).

您可以在下方找到Campaign SDK的整合步驟。

+++**正在載入Campaign SDK**

* **在Android中**：此 **neolane_sdk-release.aar** 檔案必須連結至專案。

  下列許可權會授予Adobe Campaign伺服器的存取權：

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
  ```

  下列許可權可讓您復原電話的唯一ID：

  ```
  <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
  ```

  自SDK 1.0.24版開始，此許可權僅適用於Android 6.0之前的版本。

  自SDK 1.0.26版起，即不再使用此許可權。

* **在iOS中**：此 **libNeolaneSDK.a** 和 **Neolane_SDK.h** 檔案必須連結至專案。 從SDK 1.0.24版開始，選項 **ENABLE_BITCODE** 已啟用。

  >[!NOTE]
  >
  >對於1.0.25版的SDK，以下提供四種架構： **Neolane_SDK.h** 檔案。

+++

+++**宣告整合設定**

若要將Campaign SDK整合至行動應用程式，功能管理員必須向開發人員提供下列資訊：

* **整合索引鍵**：啟用Adobe Campaign平台以識別行動應用程式。

  >[!NOTE]
  >
  >此整合索引鍵需在Adobe Campaign主控台的 **[!UICONTROL Information]** 行動應用程式專屬服務的標籤。 請參閱 [在Adobe Campaign中設定行動應用程式](configuring-the-mobile-application.md).

* **追蹤URL**：此專案符合Adobe Campaign追蹤伺服器的位址。
* **行銷URL**：啟用訂閱集合。

* **在Android中**：

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
  ```

* **在iOS中**：

  ```
  Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl setMarketingHost:strMktHost];
  [nl setTrackingHost:strTckHost];
  [nl setIntegrationKey:strIntegrationKey];
  ```

+++

+++**註冊功能**

註冊功能可讓您：

* 將通知ID或推播ID (iOS的deviceToken和Android的註冊ID)傳送至Adobe Campaign。
* 復原調解金鑰或userKey （例如，電子郵件或帳號）

* **在Android中**：

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

  如果您使用FCM (Firebase Cloud Messaging)，我們建議您使用 **registerDevice** 函式呼叫 **onTokenRefresh** 此函式會在使用者的行動裝置Token變更時通知Adobe Campaign。

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

* **在iOS中**：

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

* **在Android中**：

  追蹤函式可讓您追蹤通知啟用（開啟）和通知顯示（熒幕擷圖）。

  追蹤通知顯示(透過呼叫 **notifyreceive** 函式)，請遵循以下實作。 請注意，如果您使用FCM （Firebase雲端通訊），我們建議您使用 **notifyreceive** 函式當 **onMessageReceived** 函式由Android系統呼叫。

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

  以下為追蹤通知開啟的實作範例(透過呼叫 **notifyOpening** 函式)。 此 **通知活動** 類別對應於用來建立 **notifIntent** 物件。

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

* **在iOS中**：

  追蹤函式可讓您追蹤何時啟動（開啟）通知。

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
  >從7.0版開始，只要 **`application:didReceiveRemoteNotification:fetchCompletionHandler`** 函式已實作，作業系統只會呼叫此函式。 此 **`application:didReceiveRemoteNotification`** 因此不會呼叫函式。

+++

+++**靜音通知追蹤**

iOS可讓您傳送無訊息通知、通知或資料，以便直接傳送至行動應用程式而不顯示。 Adobe Campaign可讓您追蹤這些事件。

若要追蹤您的無訊息通知，請遵循以下範例：

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
>請注意，這是iOS的專屬專案。

在iOS中，委派通訊協定可讓您取得 **registerDevice** 呼叫，並可用於瞭解註冊期間是否發生錯誤。

此 **registerDeviceStatus** 原型為：

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**狀態** 可讓您知道註冊是否成功或是否發生錯誤。

**ErrorReason** 會提供發生錯誤的詳細資訊。 有關可用錯誤及其說明的詳細資訊，請參閱下表。

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
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty <br /> </td>
   <td> ACC行銷伺服器主機名稱是空的或未設定。<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureIntegrationKeyEmpty <br /> </td>
   <td> 整合金鑰為空白或未設定。<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureConnectionIssue<br /> </td>
   <td> ACC的連線問題<br /> </td>
   <td> 更多資訊（以作業系統目前的語言顯示）<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnknownUUID<br /> </td>
   <td> 提供的UUID （整合金鑰）不明。<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnexpectedError<br /> </td>
   <td> 傳回給ACC伺服器的意外錯誤。<br /> </td>
   <td> 錯誤訊息傳回ACC。<br /> </td>
  </tr>
 </tbody>
</table>

**Neolane_SDKDelegate** 通訊協定和 **registerDeviceStatus** 委派定義如下：

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

1. 實作 **setDelegate** 於SDK初始化期間。

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

1. 在中新增通訊協定 **@interface** 您班級的。

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

1. 在中實作委派 **AppDelegate**.

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

變數可讓您定義在收到通知後的行動應用程式行為。 這些變數必須在行動應用程式的程式碼中，以及在Adobe Campaign主控台的 **[!UICONTROL Variables]** 標籤中列出的應用程式(請參閱 [在Adobe Campaign中設定行動應用程式](configuring-the-mobile-application.md))。 以下是程式碼範例，此程式碼可讓行動應用程式收集通知中新增的任何變數。 在範例中，我們使用「VAR」變數。

* **在Android中**：

  ```
  public void onReceive(Context context, Intent intent) {
       ...
      String event = intent.getStringExtra("VAR");
       ...
  }
  ```

* **在iOS中**：

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
>Adobe建議您選擇短變數名稱，因為通知大小在iOS和Android上限製為4kB。

+++

+++**通知服務延伸模組**

**適用於iOS**

媒體必須在通知服務延伸層級下載。

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

+++**通知內容延伸**

**適用於iOS**

在此層級，您需要：

* 將您的內容擴充功能與Adobe Campaign傳送的類別建立關聯：

  如果您希望行動應用程式顯示影像，可以在Adobe Campaign中將類別值設為「影像」，並在行動應用程式中，使用建立通知擴充功能 **UNNotificationExtensionCategory** 引數設為&quot;image&quot;。 在裝置上收到推播通知時，會根據定義的類別值呼叫擴充功能。

* 定義您的通知配置

  您必須使用相關Widget來定義版面。 若為影像，Widget的名稱為 **UImageView**.

* 顯示您的媒體

  您需要新增程式碼，以將媒體資料摘要至Widget。 以下是影像的程式碼範例：

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

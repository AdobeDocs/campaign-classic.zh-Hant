---
product: campaign
title: 為iOS裝置建立推播通知
description: 了解如何建立iOS的推播通知
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Push
exl-id: 4520504a-0d9f-4ea7-a5a8-0c07948af4f0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 6%

---

# 建立iOS通知{#create-notifications-ios}



本節詳細說明傳送iOS通知的特定元素。 傳遞建立的全域概念，在 [本節](steps-about-delivery-creation-steps.md).

首先，建立新的傳送。

![](assets/nmac_delivery_1.png)

若要建立iOS裝置的推播通知，請遵循下列步驟：

1. 選取 **[!UICONTROL Deliver on iOS]** 傳遞範本。

   ![](assets/nmac_delivery_ios_1.png)

1. 若要定義通知的目標，請按一下 **[!UICONTROL To]** 連結，然後按一下 **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >選取傳送的目標母體時的詳細程式會顯示在 [本節](steps-defining-the-target-population.md).
   >
   >有關個人化欄位使用的詳細資訊，請參閱 [本節](about-personalization.md).
   >
   >有關包含種子清單的詳細資訊，請參閱 [關於種子地址](about-seed-addresses.md).

1. 選擇 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**，請選取與行動應用程式相關的服務（在此例中為Neotrips），然後選取應用程式的iOS版本。

   ![](assets/nmac_delivery_ios_3.png)

1. 選擇您的 **[!UICONTROL Notification type]** 介於 **[!UICONTROL General notification (Alert, Sound, Badge)]** 或 **[!UICONTROL Silent notification]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >此 **靜默推** 模式可將「靜默」通知傳送至行動應用程式。 使用者未得知通知的到達。 會直接轉送至應用程式。

1. 在 **[!UICONTROL Title]** 欄位中，輸入要在通知中心可用通知清單中顯示的標題標籤。

   此欄位可讓您定義 **標題** iOS通知裝載的參數。

1. 您可以新增 **[!UICONTROL Subtitle]**,iOS通知裝載的字幕參數值。 請參閱 [本節](configuring-the-mobile-application.md).

1. 在 **[!UICONTROL Message content]** 的子句。 個人化欄位的使用會顯示在 [關於個人化](about-personalization.md) 區段。

   ![](assets/nmac_delivery_ios_5.png)

1. 按一下 **[!UICONTROL Insert emoticon]** 圖示將表情符號插入推播通知。 若要自訂表情符號清單，請參閱 [本節](customizing-emoticon-list.md)

1. 從 **[!UICONTROL Sound and Badge]** 頁簽，您可以編輯下列選項：

   * **[!UICONTROL Clean Badge]**:啟用此選項可刷新徽章值。

   * **[!UICONTROL Value]**:設定一個數字，該數字將用於直接在應用程式表徵圖上顯示新未讀資訊的數量。

   * **[!UICONTROL Critical alert mode]**:啟用此選項，即使使用者的手機設定為焦點模式或iPhone已靜音，仍可將音效新增至通知。

   * **[!UICONTROL Name]**:在收到通知時，選擇要由移動終端播放的聲音。

   * **[!UICONTROL Volume]**:音量從0到100。
   >[!NOTE]
   >
   >應用程式中必須包含聲音，並在建立服務時定義聲音。 請參閱[本節](configuring-the-mobile-application.md#configuring-external-account-ios)。

   ![](assets/nmac_delivery_ios_6.png)

1. 從 **[!UICONTROL Application variables]** 標籤 **[!UICONTROL Application variables]** 會自動新增。 它們可讓您定義通知行為，例如，您可以設定當使用者啟動通知時顯示的特定應用程式畫面。

   如需詳細資訊，請參閱[本章節](configuring-the-mobile-application.md)。

1. 從 **[!UICONTROL Advanced]** 頁簽中，可以編輯以下常規選項：

   * **[!UICONTROL Mutable content]**:啟用此選項可允許行動應用程式下載媒體內容。

   * **[!UICONTROL Thread-id]**:用於將相關通知分組的標識符。

   * **[!UICONTROL Category]**:將顯示動作按鈕的類別ID名稱。 這些通知可讓使用者以更快的方式回應通知，執行不同的工作，而不需在應用程式中開啟或導覽。

   ![](assets/nmac_delivery_ios_7.png)

1. 對於時間敏感通知，您可以指定下列選項：

   * **[!UICONTROL Target content ID]**:用於定位在開啟通知時要前進的應用程式視窗的識別碼。

   * **[!UICONTROL Launch image]**:要顯示的launch影像檔案名稱。 如果使用者選擇啟動您的應用程式，則會顯示選取的影像，而非您應用程式的啟動畫面。

   * **[!UICONTROL Interruption level]**:

      * **[!UICONTROL Active]**:預設設定後，系統會立即顯示通知、點亮螢幕並播放聲音。 通知不會中斷焦點模式。

      * **[!UICONTROL Passive]**:系統將通知添加到通知清單中，而不用點亮螢幕或播放聲音。 通知不會中斷焦點模式。

      * **[!UICONTROL Time sensitive]**:系統會立即顯示通知，將螢幕燈亮起，可以播放聲音並突破焦點模式。 此層級不需要Apple的特殊許可。

      * **[!UICONTROL Critical]**:系統會立即顯示通知、點亮螢幕，並繞過靜音開關或聚焦模式。 請注意，此層級需要Apple的特殊權限。
   * **[!UICONTROL Relevance score]**:將關聯分數從0設定為100。 系統會使用此功能來排序通知摘要中的通知。

   ![](assets/nmac_delivery_ios_8.png)

1. 設定通知後，按一下 **[!UICONTROL Preview]** 標籤來預覽通知。

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >通知樣式（橫幅或警報）未在Adobe Campaign中定義。 這取決於使用者在其iOS設定中選取的設定。 不過，Adobe Campaign可讓您預覽每種通知樣式。 按一下右下方的箭頭，以從一個樣式切換為另一個樣式。
   >
   >預覽使用iOS 10的外觀和風格。

若要傳送校樣並傳送最終傳送，請使用與電子郵件傳送相同的程式。 [了解更多](steps-validating-the-delivery.md)

傳送訊息後，您可以監控及追蹤您的傳送。 如需詳細資訊，請參閱下列區段。

* [推播通知隔離](understanding-quarantine-management.md#push-notification-quarantines)
* [監視傳遞](about-delivery-monitoring.md)
* [瞭解傳遞故障](understanding-delivery-failures.md)

## 建立iOS豐富通知 {#creating-ios-delivery}

有了iOS 10或更新版本，便可產生豐富通知。 Adobe Campaign可使用變數傳送通知，讓裝置顯示豐富通知。

您現在需要建立新的傳送，並將其連結至您建立的行動應用程式。

1. 前往 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. 按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 選擇 **[!UICONTROL Deliver on iOS (ios)]** 在 **[!UICONTROL Delivery template]** 下拉式清單。 新增 **[!UICONTROL Label]** 傳送給您。

1. 按一下 **[!UICONTROL To]** 定義要定位的母體。 依預設， **[!UICONTROL Subscriber application]** 已套用目標對應。 按一下 **[!UICONTROL Add]** 來選取先前建立的服務。

   ![](assets/nmac_ios_9.png)

1. 在 **[!UICONTROL Target type]** 窗口，選擇 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** 按一下 **[!UICONTROL Next]**.

1. 在 **[!UICONTROL Service]** 下拉式清單，依序選取您先前建立的服務，然後選取您要定位的應用程式，然後按一下 **[!UICONTROL Finish]**.

   ![](assets/nmac_ios_6.png)

1. 編輯豐富通知。

   ![](assets/nmac_ios_7.png)

1. 從 **[!UICONTROL Application variables]** 標籤 **[!UICONTROL Application variables]** 會根據設定步驟中新增的內容自動新增。

   >[!NOTE]
   >
   >應用程式變數必須在行動應用程式的程式碼中定義，並在服務建立期間輸入。 如需詳細資訊，請參閱[本章節](configuring-the-mobile-application.md)。

   ![](assets/nmac_ios_10.png)

1. 從 **[!UICONTROL Advanced]** 頁簽，檢查 **[!UICONTROL Mutable content]** 方塊來允許行動應用程式下載媒體內容。

1. 按一下 **[!UICONTROL Save]** 並傳送您的傳遞。

在訂閱者的行動iOS裝置上收到影像和網頁時，應顯示在推播通知中。

![](assets/nmac_ios_8.png)





---
product: campaign
title: 為iOS設備建立推送通知
description: 瞭解如何為iOS建立推送通知
feature: Push
exl-id: 4520504a-0d9f-4ea7-a5a8-0c07948af4f0
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 3%

---

# 為iOS建立通知{#create-notifications-ios}

![](../../assets/common.svg)

本節詳細說明了iOS通知的具體交付要素。 有關交付建立的全球概念，請參閱 [此部分](steps-about-delivery-creation-steps.md)。

首先建立新交貨。

![](assets/nmac_delivery_1.png)

要為iOS設備建立推送通知，請執行以下步驟：

1. 選擇 **[!UICONTROL Deliver on iOS]** 交貨模板。

   ![](assets/nmac_delivery_ios_1.png)

1. 要定義通知的目標，請按一下 **[!UICONTROL To]** 連結，然後按一下 **[!UICONTROL Add]**。

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >選擇交貨的目標總量時的詳細過程，請參見 [此部分](steps-defining-the-target-population.md)。
   >
   >有關使用個性化欄位的詳細資訊，請參閱 [此部分](about-personalization.md)。
   >
   >有關包含種子清單的詳細資訊，請參閱 [關於種子地址](about-seed-addresses.md)。

1. 選擇 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**，選擇與您的移動應用程式相關的服務（本例中為Neotrips），然後選擇應用程式的iOS版本。

   ![](assets/nmac_delivery_ios_3.png)

1. 選擇通知類型： **[!UICONTROL Alert]**。 **[!UICONTROL Badge]**&#x200B;或 **[!UICONTROL Alert and badge]** 或 **[!UICONTROL Silent Push]**。

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >的 **靜默推送** 模式允許將「靜默」通知發送到移動應用程式。 用戶未意識到通知的到達。 直接轉給申請。

1. 在 **[!UICONTROL Title]** 欄位中，輸入要在通知中顯示的標題的標籤。 它將只出現在通知中心提供的通知清單中。 此欄位允許您定義 **標題** iOS通知負載的參數。

1. 如果使用HTTP/2連接器，則可以添加子標題( **字幕** iOS通知負載的參數)。 請參閱 [此部分](configuring-the-mobile-application.md)。

1. 然後輸入 **[!UICONTROL Message]** 和 **[!UICONTROL Value of the badge]** 基於所選通知類型。

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** 和 **[!UICONTROL Alert and badge]** 鍵入通知使您能夠修改徽章的值（移動應用程式徽標上方的編號）。 要刷新徽章，您只需輸入0作為值。 如果欄位為空，則標籤值不會更改。

1. 按一下 **[!UICONTROL Insert emoticon]** 表徵圖，將圖釋插入推送通知。 要自定義表情清單，請參閱 [此部分](customizing-emoticon-list.md)

1. 的 **[!UICONTROL Action button]** 允許您為出現在警報通知中的操作按鈕定義標籤(**操作_loc_key** 有效負載欄位)。 如果您的iOS應用程式管理可本地化的字串(**Localizabled.strings**)，在此欄位中輸入相應的鍵。 如果應用程式不管理可本地化文本，請輸入要在操作按鈕上顯示的標籤。 有關可本地化字串的詳細資訊，請參閱 [Apple文檔](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) 。
1. 在 **[!UICONTROL Play a sound]** 欄位中，選擇當收到通知時由移動終端播放的聲音。

   >[!NOTE]
   >
   >聲音必須包括在應用程式中並在建立服務時定義。 請參閱[本節](configuring-the-mobile-application.md#configuring-external-account-ios)。

1. 在 **[!UICONTROL Application variables]** 欄位，輸入每個變數的值。 應用程式變數允許您定義通知行為：例如，您可以配置特定應用程式螢幕以在用戶激活通知時顯示。

   >[!NOTE]
   >
   >應用程式變數必須在移動應用程式的代碼中定義，並在建立服務期間輸入。 如需詳細資訊，請參閱[本章節](configuring-the-mobile-application.md)。

1. 配置通知後，按一下 **[!UICONTROL Preview]** 的子菜單。

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >通知樣式（橫幅或警報）在Adobe Campaign未定義。 它取決於用戶在其iOS設定中選擇的配置。 但是，Adobe Campaign允許您預覽每種通知樣式。 按一下右下角的箭頭，從一種樣式切換到另一種樣式。
   >
   >預覽使用iOS10外觀。

要發送證據併發送最終交貨，請使用與電子郵件交貨相同的流程。

發送消息後，您可以監視和跟蹤交貨。 如需詳細資訊，請參閱下列區段。

* [推送通知隔離](understanding-quarantine-management.md#push-notification-quarantines)
* [監視傳遞](about-delivery-monitoring.md)
* [瞭解傳遞故障](understanding-delivery-failures.md)


## 建立iOS富通通知 {#creating-ios-delivery}

在iOS10或更高版本中，可以生成豐富的通知。 Adobe Campaign可以使用允許設備顯示豐富通知的變數發送通知。

現在，您需要建立新的交付內容並將其連結到您建立的移動應用程式。

1. 轉到 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 選擇 **[!UICONTROL Deliver on iOS (ios)]** 的 **[!UICONTROL Delivery template]** 下拉。 添加 **[!UICONTROL Label]** 送到你的快遞。

1. 按一下 **[!UICONTROL To]** 來定義目標的人口。 預設情況下， **[!UICONTROL Subscriber application]** 應用了目標映射。 按一下 **[!UICONTROL Add]** 來選擇以前建立的服務。

   ![](assets/nmac_ios_9.png)

1. 在 **[!UICONTROL Target type]** 窗口，選擇 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** 按一下 **[!UICONTROL Next]**。

1. 在 **[!UICONTROL Service]** 下拉，選擇先前建立的服務，然後選擇要目標的應用程式，然後按一下 **[!UICONTROL Finish]**。
的 **[!UICONTROL Application variables]** 根據在配置步驟中添加的內容自動添加。

   ![](assets/nmac_ios_6.png)

1. 編輯您的富通知。

   ![](assets/nmac_ios_7.png)

1. 檢查 **[!UICONTROL Mutable content]** 框，以允許移動應用程式下載媒體內容。

1. 按一下 **[!UICONTROL Save]** 然後把你的快遞寄出去。

當在用戶的移動iOS設備上接收到該影像和網頁時，該影像和網頁應該顯示在推送通知中。

![](assets/nmac_ios_8.png)

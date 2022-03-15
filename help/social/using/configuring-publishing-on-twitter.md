---
product: campaign
title: 在 Twitter 上設定發佈
description: 在 Twitter 上設定發佈
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2d2a6e32-587d-4a7b-ba1c-d9140da53f64
source-git-commit: d891a235002d465f3b00fafa375d87d42ebafaa6
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 6%

---

# 要在Twitter上發佈的配置步驟{#configuring-publishing-on-twitter}

![](../../assets/v7-only.svg)

為了讓Adobe Campaign能夠向你的Twitter帳戶發送推文，你需要為這些帳戶委派對Adobe Campaign的寫權限。 為此，請應用以下配置步驟：

* 建立Twitter帳戶。
* 建立testTwitter帳戶以發送校樣。
* 為每個Twitter帳戶建立一個Twitter應用程式。
* 對於每個Twitter應用程式，建立一個 **[!UICONTROL Twitter]** 類型服務。

![](assets/social_diagram_twitter_service.png)

## 必要條件 {#prerequisites}

首先建立一個或多個Twitter帳戶，將您的推文發送到。

要建立Twitter帳戶，請轉到 [https://twitter.com](https://twitter.com){target=&quot;_blank&quot;}。

## 在Twitter建立test帳戶 {#creating-a-test-account-on-twitter}

建立可用於發送的專用Twitter帳戶 [推特證明](../../social/using/publishing-on-twitter.md#sending-the-proof)。 要建立私人Twitter帳戶，請執行以下步驟：

1. 新建Twitter帳戶。
1. 訪問帳戶  **[!UICONTROL Settings]**。
1. 瀏覽到 **[!UICONTROL Privacy & Safety]** 和 **[!UICONTROL Audience and Tagging]** 檢查 **[!UICONTROL Protect your Tweets]** 的雙曲餘切值。 您的Tweets和其他帳戶資訊僅對關注您的人可見。

![](assets/social_twitter_test_page.png)

## 在Twitter建立應用程式 {#creating-an-application-on-twitter}

為了讓Adobe Campaign能夠向Twitter帳戶發送推文，你需要為每個Twitter帳戶建立一個Twitter應用程式。 若要這麼做，請套用下列步驟：

1. 登錄你的Twitter帳戶。
1. 在Internet瀏覽器中輸入以下地址： [https://developer.twitter.com/en/apps](https://developer.twitter.com/en/apps)。
1. 然後按一下 **[!UICONTROL Create an App]** 按鈕。

   ![](assets/social_create_twitter_app_001.png)

1. 讓嚮導指導您完成該過程。

   為了使此應用程式允許Adobe Campaign將推文發送到您的帳戶，請轉到 **[!UICONTROL Permissions]** 頁籤，然後選擇 **[!UICONTROL Read and Write]** 為 **[!UICONTROL Access]** 的子菜單。 在 **[!UICONTROL Settings]** 的 **[!UICONTROL Callback URL]** 欄位為空。

   ![](assets/social_create_twitter_app_002.png)

## 委託對Adobe Campaign的寫訪問 {#delegating-write-access-to-adobe-campaign}

對於每個Twitter應用程式，您需要建立不同的 **[!UICONTROL Twitter]** 鍵入包含應用程式設定的服務。

此步驟要求同時訪問您的Adobe Campaign控制台和登錄到您的Twitter帳戶的Internet瀏覽器：

* 在 **Twitter**:從 [此頁](https://developer.twitter.com/en/portal/projects-and-apps)，選擇以前建立的應用並編輯 **應用權限**。

   ![](assets/social_twitter_service_002.png)

   編輯 **密鑰和令牌** 頁籤以訪問您的應用詳細資訊。

* 在 **Adobe Campaign**:轉到 **[!UICONTROL Profiles and targets]** 頁籤 **[!UICONTROL Services and Subscriptions]** 連結，然後按一下 **[!UICONTROL Create]** 按鈕

   ![](assets/social_twitter_service_007.png)

1. 選擇 **[!UICONTROL Twitter]** 的雙曲餘切值。

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >的 **[!UICONTROL Synchronize subscriptions]** 選項。 選中該框後，Twitter帳戶同步工作流(請參閱 [同步Twitter帳戶](#synchronizing-twitter-accounts))恢復Twitter關注者清單，以便您可以向他們發送直接消息(請參閱 [向訂閱者發送直接消息](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers))。 如果不想恢復關注者清單，請取消選中此框。

1. 輸入服務的標籤和內部名稱。

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >的 **[!UICONTROL Internal name]** 必須與Twitter帳戶的名稱相同。 要確保沒有輸入錯誤，請應用以下步驟。

   * 按一下 **[!UICONTROL Save]** 按鈕。
   * 在服務概述中，按一下您剛剛建立的Twitter服務。

   <!-- * Select the **[!UICONTROL Twitter page]** tab. The Twitter account should be displayed. 
    
      ![](assets/social_twitter_service_010.png)-->

1. 在 **[!UICONTROL Visitor folder]** 欄位中，選擇將在其中建立追隨者的資料夾。 如需詳細資訊，請參閱[本章節](../../social/using/publishing-on-twitter.md#operating-principle)。預設情況下，跟隨者將保存在 **[!UICONTROL Visitors]** 的子菜單。

   ![](assets/social_twitter_service_010_b.png)

1. 在Twitter，複製 **[!UICONTROL Consumer Key (API Key)]** 和 **[!UICONTROL Consumer Secret (API Secret)]** 將其貼上到 **[!UICONTROL Consumer key]** 和 **[!UICONTROL Consumer secret]** 市場活動客戶端控制台的欄位。

   ![](assets/social_twitter_service_012.png)

1. 在Twitter，複製 **[!UICONTROL Access Token]** 和 **[!UICONTROL Access Token Secret]** 將其貼上到 **[!UICONTROL Access token]** 和 **[!UICONTROL Access token secret]** 市場活動客戶端控制台的欄位。

   ![](assets/social_twitter_service_013.png)

1. 在市場活動客戶端控制台中，按一下 **[!UICONTROL Save]**。 您現在已將寫權限授予Adobe Campaign。

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>必須建立 **[!UICONTROL Twitter]** 每個Twitter應用程式的服務。

的 **[!UICONTROL Twitter account Synchronization]** 工作流將同步TwitterAdobe Campaign帳戶。

## 同步Twitter帳戶 {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>為使工作流恢復Twitter訂戶清單， **[!UICONTROL Twitter account synchronization]** 複選框。 如需詳細資訊，請參閱[本章節](#delegating-write-access-to-adobe-campaign)。

的 **[!UICONTROL Twitter account synchronization]** 工作流，通過 **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** 節點，用於同步以前與Adobe Campaign配置的Twitter帳戶。 預設情況下，此工作流會在每週四的早上7:30觸發。

>[!NOTE]
>
>您可以通過運行預期的任務處理隨時啟動工作流。 您還可以編輯調度程式以更改工作流觸發頻率。 有關計畫程式的詳細資訊，請參閱 [此部分](../../workflow/using/scheduler.md)。

現在，你可以向你的Twitter賬戶發送推文，並將消息直接發送給你的追隨者。 如需詳細資訊，請參閱[此頁面](../../social/using/publishing-on-twitter.md)。

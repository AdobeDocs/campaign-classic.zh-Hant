---
product: campaign
title: 在 Twitter 上設定發佈
description: 在 Twitter 上設定發佈
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2d2a6e32-587d-4a7b-ba1c-d9140da53f64
source-git-commit: d11c918213e72fe4bf6adb464e516fac19b63d54
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 7%

---

# 配置在Twitter上發佈的步驟{#configuring-publishing-on-twitter}

![](../../assets/v7-only.svg)

為了讓Adobe Campaign能夠傳送推文至您的Twitter帳戶，您需要為這些帳戶委派對Adobe Campaign的寫入存取權。 要執行此操作，請套用下列設定步驟：

* 建立Twitter帳戶。
* 建立用於傳送校樣的測試Twitter帳戶。
* 為每個Twitter帳戶建立一個Twitter應用程式。
* 為每個Twitter應用程式建立新 **[!UICONTROL Twitter]** 類型服務。

![](assets/social_diagram_twitter_service.png)

## 先決條件 {#prerequisites}

首先，建立一或多個Twitter帳戶，將您的推文傳送至。

若要建立Twitter帳戶，請前往 [https://twitter.com](https://twitter.com){target=&quot;_blank&quot;}。

## 在Twitter上建立測試帳戶 {#creating-a-test-account-on-twitter}

建立可用於傳送的私人Twitter帳戶 [推文校樣](../../social/using/publishing-on-twitter.md#sending-the-proof). 若要建立私人Twitter帳戶，請遵循下列步驟：

1. 建立新的Twitter帳戶。
1. 存取帳戶  **[!UICONTROL Settings]**.
1. 瀏覽至 **[!UICONTROL Privacy & Safety]** 和 **[!UICONTROL Audience and Tagging]** 並檢查 **[!UICONTROL Protect your Tweets]** 選項。 您的推文和其他帳戶資訊只會顯示給追隨您的人。

![](assets/social_twitter_test_page.png)

## 在Twitter上建立應用程式 {#creating-an-application-on-twitter}

為了讓Adobe Campaign能夠將推文傳送至您的Twitter帳戶，您需要為每個Twitter帳戶建立一個Twitter應用程式。 若要這麼做，請套用下列步驟：

1. 登入您的Twitter帳戶。
1. 在網際網路瀏覽器中輸入以下地址： [https://developer.twitter.com/en/apps](https://developer.twitter.com/en/apps).
1. 然後按一下 **[!UICONTROL Create an App]** 按鈕。

   ![](assets/social_create_twitter_app_001.png)

1. 讓精靈引導您完成此程式。

   若要讓此應用程式允許Adobe Campaign將推文傳送至您的帳戶，請前往 **[!UICONTROL Permissions]** 頁簽，然後選擇 **[!UICONTROL Read and Write]** 針對 **[!UICONTROL Access]** 區段。 在 **[!UICONTROL Settings]** 頁簽，您也需要離開 **[!UICONTROL Callback URL]** 欄位空白。

   ![](assets/social_create_twitter_app_002.png)

## 委派寫入存取權至Adobe Campaign {#delegating-write-access-to-adobe-campaign}

針對每個Twitter應用程式，您需要建立不同的 **[!UICONTROL Twitter]** 鍵入將包括應用程式設定的服務。

此步驟需要同時存取您的Adobe Campaign主控台和登入您Twitter帳戶的網際網路瀏覽器：

* in **Twitter**:從 [本頁](https://developer.twitter.com/en/portal/projects-and-apps)，選取先前建立的應用程式並編輯 **應用程式權限**.

   ![](assets/social_twitter_service_002.png)

   編輯 **金鑰和代號** 標籤來存取您的應用程式詳細資訊。

* in **Adobe Campaign**:前往 **[!UICONTROL Profiles and targets]** ，按一下 **[!UICONTROL Services and Subscriptions]** 連結，然後按一下 **[!UICONTROL Create]** 按鈕。

   ![](assets/social_twitter_service_007.png)

1. 選取 **[!UICONTROL Twitter]** 類型。

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >此 **[!UICONTROL Synchronize subscriptions]** 選項。 核取方塊後，Twitter帳戶同步工作流程(請參閱 [同步Twitter帳戶](#synchronizing-twitter-accounts))會復原Twitter追隨者的清單，以便您可以傳送他們直接訊息(請參閱 [傳送直接訊息給訂閱者](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers))。 如果您不想恢復跟隨者清單，請取消選中此框。

1. 輸入服務的標籤和內部名稱。

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >此 **[!UICONTROL Internal name]** 的名稱必須與Twitter帳戶的名稱相同。 若要確定沒有登入錯誤，請套用下列步驟。

   * 按一下 **[!UICONTROL Save]** 按鈕。
   * 在服務概觀中，按一下您剛建立的Twitter服務。

   <!-- * Select the **[!UICONTROL Twitter page]** tab. The Twitter account should be displayed. 
    
      ![](assets/social_twitter_service_010.png)-->

1. 在 **[!UICONTROL Visitor folder]** 欄位中，選擇將在其中建立追隨者的資料夾。 如需詳細資訊，請參閱[本章節](../../social/using/publishing-on-twitter.md#operating-principle)。依預設，追隨者會儲存在 **[!UICONTROL Visitors]** 檔案夾。

   ![](assets/social_twitter_service_010_b.png)

1. 在Twitter上，複製 **[!UICONTROL Consumer Key (API Key)]** 和 **[!UICONTROL Consumer Secret (API Secret)]** 欄位並貼入 **[!UICONTROL Consumer key]** 和 **[!UICONTROL Consumer secret]** 行銷活動用戶端主控台的欄位。

   ![](assets/social_twitter_service_012.png)

1. 在Twitter上，複製 **[!UICONTROL Access Token]** 和 **[!UICONTROL Access Token Secret]** 欄位並貼入 **[!UICONTROL Access token]** 和 **[!UICONTROL Access token secret]** 行銷活動用戶端主控台的欄位。

   ![](assets/social_twitter_service_013.png)

1. 在Campaign用戶端主控台中，按一下 **[!UICONTROL Save]**. 您現在已委派寫入存取權給Adobe Campaign。

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>您必須建立 **[!UICONTROL Twitter]** 每個Twitter應用程式的服務。

此 **[!UICONTROL Twitter account Synchronization]** 工作流程會同步Adobe Campaign中的Twitter帳戶。 如需詳細資訊，請參閱[此頁面](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages)。

## 同步Twitter帳戶 {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>為了讓工作流程恢復Twitter訂閱者的清單， **[!UICONTROL Twitter account synchronization]** 框中，選擇「 CSV文本」。 如需詳細資訊，請參閱[本章節](#delegating-write-access-to-adobe-campaign)。

此 **[!UICONTROL Twitter account synchronization]** 工作流程，可透過 **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** 節點，可讓您同步先前設定給Adobe Campaign的Twitter帳戶。 依預設，此工作流程會在每星期四早上7:30觸發。

>[!NOTE]
>
>您可以隨時執行預期的任務處理，以啟動工作流程。 您也可以編輯排程器以變更工作流程觸發頻率。 有關調度程式的詳細資訊，請參閱 [本節](../../workflow/using/scheduler.md).

您現在可以傳送推文至您的Twitter帳戶，並將訊息導向至您的追隨者。 如需詳細資訊，請參閱[此頁面](../../social/using/publishing-on-twitter.md)。

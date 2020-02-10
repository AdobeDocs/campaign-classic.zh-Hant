---
title: 在Twitter上設定發佈
seo-title: 在Twitter上設定發佈
description: 在Twitter上設定發佈
seo-description: null
page-status-flag: never-activated
uuid: 88867881-fb59-4f0d-862e-537d498e9aef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 9d74ed9c-0055-4556-a205-6e5fea11816b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 在Twitter上設定發佈{#configuring-publishing-on-twitter}

為了讓Adobe Campaign能夠傳送推文至您的Twitter帳戶，您必須為這些帳戶委派Adobe Campaign的寫入存取權。 若要這麼做，請套用下列設定步驟：

* 建立Twitter帳戶。
* 建立測試Twitter帳戶以傳送校樣。
* 為每個Twitter帳戶建立一個Twitter應用程式。
* 針對每個Twitter應用程式，建立新的類 **[!UICONTROL Twitter]** 型服務。

![](assets/social_diagram_twitter_service.png)

## 必要條件 {#prerequisites}

首先，建立一或多個Twitter帳戶，以傳送您的推文至。

若要建立Twitter帳戶，請前往 [http://twitter.com](http://twitter.com)。

## 在Twitter上建立測試帳戶 {#creating-a-test-account-on-twitter}

我們也建議建立私人Twitter帳戶，以便用來傳送推文校樣(如需詳細資訊，請參 [閱傳送證明](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* 建立新的Twitter帳戶。
* 按一下右上角的功能表，然後選取 **[!UICONTROL Settings]**。
* 選擇選 **[!UICONTROL Security and privacy]** 項卡，並選中該 **[!UICONTROL Protect my Tweets]** 框。
* 按一 **[!UICONTROL Save Changes]** 下頁面底部的按鈕。

![](assets/social_twitter_test_page.png)

## 在Twitter上建立應用程式 {#creating-an-application-on-twitter}

為了讓Adobe Campaign能夠傳送推文至您的Twitter帳戶，您必須為每個Twitter帳戶建立一個Twitter應用程式。 若要這麼做，請套用下列步驟：

1. 登入您的Twitter帳戶。
1. 在您的網際網路瀏覽器中輸入下列位址： [https://apps.twitter.com/](https://apps.twitter.com/)。
1. 然後按一 **[!UICONTROL Create New App]** 下右邊的按鈕。

   ![](assets/social_create_twitter_app_001.png)

1. 讓精靈引導您完成整個程式。

   為了讓此應用程式允許Adobe Campaign傳送推文至您的帳戶，請至應用程式的標 **[!UICONTROL Permissions]** 簽並選取 **[!UICONTROL Read and Write]** 該 **[!UICONTROL Access]** 區段。 在標 **[!UICONTROL Settings]** 簽中，您也需要將欄位留 **[!UICONTROL Callback URL]** 空。

   ![](assets/social_create_twitter_app_002.png)

## 委派Adobe Campaign的寫入存取權 {#delegating-write-access-to-adobe-campaign}

對於每個Twitter應用程式，您需要建立不同的類 **[!UICONTROL Twitter]** 型服務，其中包含應用程式設定。

此步驟需要同時存取您的Adobe Campaign主控台和登入您Twitter帳戶的網際網路瀏覽器：

* **Twitter**:選取先前建立的應用程式([https://dev.twitter.com/apps](https://dev.twitter.com/apps))，然後按一下 **[!UICONTROL Keys and Access Tokens]** 標籤。

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**:前往宇宙 **[!UICONTROL Profiles and targets]** ，按一下連結 **[!UICONTROL Services and Subscriptions]** 並按一下 **[!UICONTROL Create]** 按鈕。

   ![](assets/social_twitter_service_007.png)

1. Select the **[!UICONTROL Twitter]** type.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >預 **[!UICONTROL Synchronize subscriptions]** 設會啟用選項。 勾選此方塊後，Twitter帳戶同步工作流程(請參閱「同步 [Twitter帳戶](#synchronizing-twitter-accounts)」)會恢復Twitter追隨者的清單，以便您能夠傳送他們的直接訊息(請參閱傳送直接訊息給訂閱者 [](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers))。 如果您不想要恢復追隨者清單，請取消勾選此方塊。

1. 輸入服務的標籤和內部名稱。

   ![](assets/social_twitter_service_009.png)

   >[!CAUTION]
   >
   >服 **[!UICONTROL Internal name]** 務的名稱必須與Twitter帳戶的名稱相同。 要確保沒有輸入錯誤，請應用以下步驟。

   * Click the **[!UICONTROL Save]** button.
   * 在服務的概述中，按一下您剛建立的Twitter類型服務。
   * 選擇選 **[!UICONTROL Twitter page]** 項卡。 應顯示Twitter帳戶。

      ![](assets/social_twitter_service_010.png)

1. 在欄位 **[!UICONTROL Visitor folder]** 中，選取將建立追隨者的訪客資料夾。 For more on this, refer to [Operating principle](../../social/using/publishing-on-twitter.md#operating-principle). 依預設，追隨者會建立在資料夾的根 **[!UICONTROL Visitors]** 部。

   ![](assets/social_twitter_service_010_b.png)

1. 在Twitter上，複製和欄位 **[!UICONTROL Consumer Key (API Key)]** 的內 **[!UICONTROL Consumer Secret (API Secret)]** 容，並貼入 **[!UICONTROL Consumer key]** 主控台的和 **[!UICONTROL Consumer secret]** 欄位中。

   ![](assets/social_twitter_service_012.png)

1. 在Twitter上，複製和欄位 **[!UICONTROL Access Token]** 的內 **[!UICONTROL Access Token Secret]** 容，並貼入 **[!UICONTROL Access token]** 主控台的和 **[!UICONTROL Access token secret]** 欄位中。

   ![](assets/social_twitter_service_013.png)

1. 在Adobe Campaign主控台中，按一下 **[!UICONTROL Save]**。 Adobe Campaign的寫入存取權已完成。

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>您必須為每個Twitter應 **[!UICONTROL Twitter]** 用程式建立一個類型服務。

工作 **[!UICONTROL Twitter account Synchronization]** 流程會同步Adobe Campaign中的Twitter帳戶。 如需詳細資訊，請參閱「同 [步Facebook頁面」](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages)。

## 同步Twitter帳戶 {#synchronizing-twitter-accounts}

>[!CAUTION]
>
>為了讓工作流程恢復Twitter訂閱者的清單， **[!UICONTROL Twitter account synchronization]** 必須在連結至帳戶之服務的編輯區段中勾選方塊。 如需詳細資訊，請參閱 [委派Adobe Campaign的寫入存取權](#delegating-write-access-to-adobe-campaign)。

透過 **[!UICONTROL Twitter account synchronization]** 節點存取的工作流程可讓您 **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** 將先前設定的Twitter帳戶與Adobe Campaign同步。 依預設，此工作流程會在每週四的早上7:30觸發。

>[!NOTE]
>
>您可以隨時執行預期的任務處理來啟動工作流程。 您也可以編輯排程器以變更工作流程觸發頻率。 For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

您現在可以傳送推文至您的Twitter帳戶，並將訊息直接傳送給您的追隨者。 有關詳情，請參閱：在 [Twitter上發佈](../../social/using/publishing-on-twitter.md)。

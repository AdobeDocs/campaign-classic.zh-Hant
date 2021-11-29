---
product: campaign
title: 在 Twitter 上發佈
description: 在 Twitter 上發佈
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: e030c029-d1ee-4749-94e3-6bdfc8d89a34
source-git-commit: d11c918213e72fe4bf6adb464e516fac19b63d54
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 6%

---

# 在 Twitter 上發佈{#publishing-on-twitter}

![](../../assets/v7-only.svg)

## 在您的Twitter帳戶上發佈 {#publishing-on-your-twitter-accounts}

完成設定後， Social Marketing可讓您傳送推文至您的Twitter帳戶。

### 限制 {#limitations}

下列為Twitter固有的限制。

* 訊息不得超過140個字元。
* 不支援HTML格式。

### 建立傳送 {#creating-the-delivery}

根據 **[!UICONTROL Tweet (twitter)]** 傳遞範本。

![](assets/social_twitter_delivery_001.png)

### 選取主要目標 {#selecting-the-main-target}

選取您要傳送推文的帳戶。

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;連結。

   ![](assets/social_twitter_delivery_002.png)

1. 按一下 **[!UICONTROL Add]** 按鈕。

   ![](assets/social_twitter_delivery_006.png)

1. 選取 **[!UICONTROL A Twitter account]**。

   ![](assets/social_twitter_delivery_007.png)

1. 在 **[!UICONTROL Folder]** 欄位，選取包含Twitter帳戶的服務資料夾。 然後選取您要將推文傳送至的Twitter帳戶。

   ![](assets/social_twitter_delivery_011.png)

### 選取校樣的目標 {#selecting-the-target-of-the-proof}

此 **[!UICONTROL Target of the proofs]** 標籤可讓您定義Twitter帳戶，以在最終傳送之前測試傳送。 因此，我們建議您建立專用於傳送證明的私人Twitter帳戶。 如需如何建立私人Twitter帳戶的詳細資訊，請參閱 [本節](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). 選取校樣目標的步驟與選取主要目標的步驟相同。 請參閱[本節](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>如果您的所有傳送都使用相同的Twitter測試帳戶，您可以在 **[!UICONTROL Tweet]** 傳遞範本，透過 **[!UICONTROL Resources > Templates > Delivery templates]** 節點。 之後，系統會預設為每個新傳送輸入校樣目標。

### 定義訊息內容 {#defining-the-message-content}

在 **[!UICONTROL Content]** 標籤。

![](assets/social_twitter_delivery_005.png)

### 預覽訊息 {#viewing-the-preview}

此 **[!UICONTROL Preview]** 標籤可讓您檢視推文的呈現。

1. 按一下 **[!UICONTROL Preview]** 標籤。
1. 按一下 **[!UICONTROL Test personalization]** 下拉式功能表，然後選取 **[!UICONTROL Service]**.
1. 在 **[!UICONTROL Folder]** 欄位，選取包含您Twitter帳戶的服務資料夾。
1. 選擇您要用來測試預覽的Twitter帳戶。

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>預覽可能與最終推文稍有不同。 我們強烈建議在最終傳遞前傳送校樣，以檢視推文的確切轉譯。 請參閱[本節](#sending-the-proof)。

### 設定追蹤 {#configuring-tracking}

追蹤可在傳送報表和 **[!UICONTROL Edit > Tracking]** 標籤。

追蹤設定與電子郵件傳送的相同。 如需詳細資訊，請參閱[本章節](../../delivery/using/about-delivery-monitoring.md)。

>[!NOTE]
>
>在 **[!UICONTROL Tweet]** 傳送範本，預設會啟用追蹤。

>[!CAUTION]
>
>我們無法區分分析推文的機器人和實際點擊的用戶。

### 傳送校樣 {#sending-the-proof}

我們強烈建議您在最終傳送前先傳送出版物的證明，以在私人Twitter測試頁面上取得出版物的確切轉譯。 如需建立私人Twitter帳戶的詳細資訊，請參閱 [本節](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). 選取校樣目標的步驟在 [本節](#selecting-the-target-of-the-proof).

校樣傳送與電子郵件傳送相同。 請參閱[本節](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### 傳送訊息 {#sending-the-message}

1. 內容核准後，按一下 **[!UICONTROL Send]** 按鈕。
1. 選擇 **[!UICONTROL Deliver as soon as possible]** 並按一下 **[!UICONTROL Analyze]** 按鈕。

   >[!NOTE]
   >
   >此 **[!UICONTROL Postpone the delivery]** 選項可讓您將傳送延遲至之後的日期。

   ![](assets/social_twitter_delivery_012.png)

1. 分析完成後，檢查結果。
1. 按一下 **[!UICONTROL Confirm delivery]**，然後按一下 **[!UICONTROL Yes]**.

![](assets/social_facebook_delivery_016.png)

## 傳送直接訊息給訂閱者 {#sending-direct-messages-to-subscribers}

### 操作原則 {#operating-principle}

此 **[!UICONTROL Synchronize Twitter accounts]** 工作流程(請參閱 [深入了解](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts))會復原Twitter訂閱者的清單，以便您傳送直接訊息給他們。 恢復的跟隨者儲存在特定表中：訪客表格。 若要顯示Twitter追隨者清單，請前往 **[!UICONTROL Profiles and Targets > Visitors]** 節點。

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>為了工作流程恢復Twitter追隨者清單， **[!UICONTROL Synchronize Twitter accounts]** 框中，選擇「 CSV文本」。 有關詳細資訊，請參閱： [委派寫入存取權至Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign).

對於每個追隨者，Adobe Campaign會復原下列資訊：

* **[!UICONTROL Origin]**:社交網路的名稱(**Twitter** 在本例中)
* **[!UICONTROL External ID]**:使用者識別碼
* **[!UICONTROL User name]**:使用者的帳戶名稱
* **[!UICONTROL Full name]**:用戶名
* **[!UICONTROL Language]**:使用者語言
* **[!UICONTROL Number of friends]**:跟隨者數
* **[!UICONTROL Time zone]**:使用者時區
* **[!UICONTROL Verified]**:此欄位指出使用者是否擁有已驗證的Twitter帳戶

### 限制 {#limitations-1}

下列為Twitter固有的限制。

* 訊息不得超過140個字元。
* 不支援HTML。
* 您每天不能傳送超過250個直接訊息。 若要避免超過此臨界值，您可以分幾波傳送。 批次傳送的設定方式與電子郵件傳送相同。 如需詳細資訊，請參閱[本章節](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。

### 建立傳送 {#creating-the-delivery-}

根據 **[!UICONTROL Tweet (Direct Message)]** 傳遞範本。

![](assets/social_twitter_delivery_010.png)

### 選取主要目標 {#selecting-the-main-target-1}

選擇要向其發送直接消息的追隨者。

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;連結。

   ![](assets/social_twitter_delivery_016.png)

1. 按一下 **[!UICONTROL Add]** 按鈕。

   ![](assets/social_twitter_delivery_006.png)

1. 選取目標類型。

   ![](assets/social_twitter_delivery_017.png)

   * 選擇 **[!UICONTROL Twitter subscribers]** 傳送直接訊息給所有帳戶追隨者。

      >[!IMPORTANT]
      >
      >您每天不能傳送超過250則訊息。 如果您的Twitter帳戶有250多個追隨者，我們強烈建議分批傳送。 這與電子郵件傳送的程式相同。 請參閱[本節](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。

   * 選擇 **[!UICONTROL Filter conditions]** 定義查詢並查看其結果。 此選項與電子郵件傳送的選項相同。 請參閱 [本節](../../platform/using/defining-filter-conditions.md) 以取得更多資訊。

      ![](assets/social_twitter_delivery_018.png)

### 選取校樣的目標 {#selecting-the-target-of-the-proof-1}

此 **[!UICONTROL Target of the proofs]** 索引標籤可讓您選取將接收直接訊息校樣的追隨者。 選擇過程與主目標的選擇過程相同。 請參閱 [選取主要目標](#selecting-the-main-target).

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>如果您想要將所有直接訊息校樣傳送至相同的Twitter追隨者，可以在 **[!UICONTROL Tweet (Direct Message)]** 傳遞範本，透過 **[!UICONTROL Resources > Templates > Delivery templates]** 節點。 之後，系統會預設為每個新傳送輸入校樣目標。

### 定義訊息內容 {#defining-message-content-}

在 **[!UICONTROL Content]** 標籤。

![](assets/social_twitter_delivery_015.png)

個人化欄位的使用方式與電子郵件傳送相同，例如在訊息內文中新增追隨者的名稱。 內容個人化在 [本節](../../delivery/using/about-personalization.md).

![](assets/social_twitter_delivery_021.png)

下列步驟與傳送推文至Twitter帳戶的步驟相同。 請參閱 [在Twitter帳戶上發佈](#publishing-on-your-twitter-accounts).

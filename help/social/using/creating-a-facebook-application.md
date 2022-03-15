---
product: campaign
title: 建立 Facebook 應用程式
description: 建立 Facebook 應用程式
audience: social
content-type: reference
topic-tags: configuration
exl-id: 5c11bd0f-2df7-4c7f-b682-955fedf8e664
source-git-commit: d891a235002d465f3b00fafa375d87d42ebafaa6
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 5%

---

# 建立 Facebook 應用程式{#creating-a-facebook-application}

![](../../assets/v7-only.svg)

使用Web應用程式，「營銷活動社交營銷」模組可以在Facebook應用程式中顯示個性化內容，從而更輕鬆地通過此社交媒體獲取潛在客戶。 有關Facebook類型Web應用程式的更多示例，請參閱 [此頁](../../social/using/examples-of-facebook-apps.md)。

>[!NOTE]
>
>您還可以將Adobe Campaign與合作夥伴開發的Facebook應用程式整合。 在這種情況下，不需要使用Adobe CampaignWeb應用程式來獲取Facebook配置檔案。 [了解更多資訊](#configuring-external-accounts)。

![](assets/social_webapp_fb_000.png)

配置步驟包括：

1. 建立一個或多個Facebook應用程式。
1. 輸入 **[!UICONTROL terms of service]** 和 **[!UICONTROL Privacy policy]** 將在Facebook權限請求螢幕上顯示的連結。 [了解更多](#entering-the-terms-of-service-and-privacy-policy-links)
1. 對於每個Facebook應用程式，建立 **[!UICONTROL Facebook Connect]** 鍵入外部帳戶。 [了解更多](#configuring-external-accounts)
1. 對於每個Facebook應用程式，在Adobe Campaign建立一個Facebook類型的Web應用程式。 [了解更多](#creating-a-facebook-type-web-application)
1. 配置您的Facebook應用程式，以便它們顯示為您的Facebook頁面上的頁籤。 [了解更多](#configuring-facebook-tabs)

## 設定外部帳戶 {#configuring-external-accounts}

對於每個Facebook應用程式，您需要建立 **[!UICONTROL Facebook Connect]** 鍵入外部帳戶。

此步驟需要訪問您的Adobe Campaign控制台和Facebook管理員帳戶：

* 開 **Facebook**:選擇以前建立的應用程式( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然後選擇 **[!UICONTROL Settings]** > **[!UICONTROL Basic]** 頁籤。

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Facebook Web Games]** 中，按一下 **[!UICONTROL Add Platform]** 按鈕，然後選擇 **[!UICONTROL Facebook Web Games]**。

* 開 **Adobe Campaign**:瀏覽 **[!UICONTROL Administration > Platform > External accounts]** 按一下 **[!UICONTROL New]**。

   ![](assets/social_webapp_fb_005.png)

1. 輸入標籤和內部名稱，然後選擇 **[!UICONTROL Facebook Connect]** 的雙曲餘切值。

   ![](assets/social_webapp_fb_006.png)

1. 選擇應用程式托管模式： **[!UICONTROL hosted by a partner]** 或 **[!UICONTROL hosted by this instance]**。

   ![](assets/social_webapp_fb_012.png)

   **由合作夥伴托管的應用程式**

   有可能將Adobe Campaign與合作夥伴開發的Facebook應用程式整合。 在這種情況下，不需要使用Adobe CampaignWeb應用程式來獲取Facebook簡檔。 當Facebook用戶安裝該應用程式時，將生成密鑰（訪問令牌）。 合作夥伴通過調用Web服務將此訪問令牌轉發給Adobe Campaign。 Adobe Campaign隨後使用此令牌登錄Facebook資料庫並收集用戶通過應用程式共用的資料。

   >[!NOTE]
   >
   >WSDL檔案中詳細介紹了Web服務的參數： **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   要將第三方應用程式整合到Adobe Campaign，您需要複製 **[!UICONTROL App ID]** 和 **[!UICONTROL App Secret]** Facebook田地，然後貼上到 **[!UICONTROL Application ID]** 和 **[!UICONTROL Application secret]** 對話框。

   ![](assets/social_facebook_external_account_013.png)

   **由此實例承載的應用程式**

   如果要在此實例上托管應用程式（如果沒有第三方應用程式），則需要使用Adobe CampaignWeb應用程式來獲取Facebook配置檔案。 如需詳細資訊，請參閱[此頁面](../../social/using/examples-of-facebook-apps.md)。

   在Adobe Campaign控制台中，複製包含在 **[!UICONTROL Secure Canvas URL]** 然後貼上到 **[!UICONTROL Facebook Web games (https)]** 在Facebook(在 **[!UICONTROL Facebook Web Games]** )的正平方根。

   ![](assets/social_facebook_external_account_009.png)

   >[!CAUTION]
   >
   >不要使用任何不安全的URL。

   在Facebook，複製 **[!UICONTROL App ID]** 和 **[!UICONTROL App Secret]** 將其貼上到 **[!UICONTROL Application ID]** 和 **[!UICONTROL Application secret]** 的子菜單。

   ![](assets/social_facebook_external_account_008.png)

1. 在Facebook上，按一下 **[!UICONTROL Save Changes]** 按鈕。
1. 在Adobe Campaign控制台中，按一下 **[!UICONTROL Subscribe]** 按鈕，使Adobe Campaign能夠在每次風扇通過此應用程式簽入時即時恢復資料。  [了解更多](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_fb_013.png)

## 輸入服務條款和隱私策略連結 {#entering-the-terms-of-service-and-privacy-policy-links}

強烈建議將 **[!UICONTROL Terms of service]** 和 **[!UICONTROL Privacy policy]** 連結，顯示在Facebook權限請求螢幕上。

![](assets/social_fb_terms_of_services_001.png)

配置階段如下：

1. 輸入以下地址： [https://developers.facebook.com/apps](https://developers.facebook.com/apps)，然後選擇Facebook應用程式。
1. 選擇 **[!UICONTROL Settings > Basic]** ，然後輸入 **[!UICONTROL Privacy Policy URL]** 和 **[!UICONTROL Terms of Service URL]** 的子菜單。

   ![](assets/social_fb_terms_of_services.png)

## 建立Facebook類型Web應用程式 {#creating-a-facebook-type-web-application}

Adobe CampaignFacebook應用程式允許您在Facebook應用程式中顯示個性化內容。 對於每個Facebook應用程式，您需要在Adobe Campaign建立一個Web應用程式。 要建立FacebookWeb應用程式，請按如下步驟操作：

1. 轉到 **[!UICONTROL Social networks]** 頁籤 **[!UICONTROL Applications]** 連結，然後 **[!UICONTROL Create]** 按鈕

   ![](assets/social_webapp_001.png)

1. 從清單中選擇一個FacebookWeb應用程式模板並輸入標籤。

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >預設提供四個FacebookWeb應用程式模板：
   >
   >* **[!UICONTROL New Facebook application]**:如果要從空白應用程式開始，請選擇此模板。
   >* **[!UICONTROL Pre-entered form]**:Facebook應用程式，帶有表單和「Facebook登錄」按鈕，用戶可以使用其配置檔案中的資料自動填充表單的欄位。 這樣用戶就可以更快地完成表格，讓品牌獲得更優質的資訊。
   >* **[!UICONTROL "Canvas page" competition]**:Facebook應用程式，該應用程式在螢幕上顯示，為用戶提供更好的視覺體驗。
   >* **[!UICONTROL "Page Tab" competition]**:Facebook應用程式完全整合到品牌頁面頁籤中。


1. 在 **[!UICONTROL Application]** 欄位中，輸入連結到Facebook應用程式的外部帳戶。 [了解更多](#configuring-external-accounts)

   ![](assets/social_webapp_005.png)

1. 選擇 **[!UICONTROL Edit]** ，然後編輯Web應用程式。 [了解更多](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_003.png)

1. 完成Web應用程式後，選擇 **[!UICONTROL Dashboard]** ，然後按一下 **[!UICONTROL Publish]** 線上發佈。

   ![](assets/social_webapp_004.png)

## 配置Facebook頁籤 {#configuring-facebook-tabs}

您可以將Facebook應用程式配置為Facebook頁上的頁籤。 若要這麼做，請套用下列步驟：

1. 選擇Facebook應用程式([https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然後選擇 **[!UICONTROL Settings > Basic]** 頁籤。

   ![](assets/social_webapp_fb_008.png)

1. 在頁面底部，按一下 **[!UICONTROL Add Platform]** ，然後選擇 **[!UICONTROL Page Tab]**。

   ![](assets/social_webapp_fb_008bis.png)

1. 在 **[!UICONTROL Page Tab Name]** 的 **[!UICONTROL Page Tab]** 部分，輸入要在Facebook頁上顯示的標籤。

   ![](assets/social_webapp_fb_001.png)

1. 在 **[!UICONTROL Secure Page Tab URL]** 欄位，輸入Web應用程式的公共URL，該URL可通過 **[!UICONTROL Dashboard]** 頁籤。 有關建立Facebook類型Web應用程式的詳細資訊，請參閱 [此部分](#creating-a-facebook-type-web-application)。

   ![](assets/social_webapp_fb_002.png)

1. 在 **[!UICONTROL Dashboard]** ，按一下 **[!UICONTROL Add a page tab]** 的子菜單。

   ![](assets/social_webapp_fb_0010.png)

1. 選擇要將頁籤添加到的Facebook頁，然後按一下 **[!UICONTROL Add Page Tab]**。

   ![](assets/social_webapp_fb_0011.png)

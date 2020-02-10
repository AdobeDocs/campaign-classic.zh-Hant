---
title: 建立Facebook應用程式
seo-title: 建立Facebook應用程式
description: 建立Facebook應用程式
seo-description: null
page-status-flag: never-activated
uuid: f02129b9-6f64-41ee-8b56-d85211a58f69
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: c1d880bb-256e-451c-8c52-198711907f8e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 建立Facebook應用程式{#creating-a-facebook-application}

由於有了網路應用程式，Social Marketing可讓您在Facebook應用程式中顯示個人化內容，讓透過此社交網路取得潛在客戶變得更容易。 如需Facebook類型網頁應用程式的更多範例，請參閱 [Facebook應用程式範例](../../social/using/examples-of-facebook-apps.md)。

>[!NOTE]
>
>您也可以將Adobe Campaign與合作夥伴開發的Facebook應用程式整合。 在這種情況下，您不需要使用Adobe Campaign網頁應用程式來取得Facebook設定檔。 有關詳細資訊，請參閱 [配置外部帳戶](#configuring-external-accounts)。

![](assets/social_webapp_fb_000.png)

套用下列設定步驟：

1. 建立一或多個Facebook應用程式。 有關詳情，請參閱：建 [立Facebook應用程式](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)。
1. 輸入要 **[!UICONTROL terms of service]** 在 **[!UICONTROL Privacy policy]** Facebook權限請求畫面上顯示的和連結。 有關詳情，請參閱：輸 [入服務條款和隱私權政策連結](#entering-the-terms-of-service-and-privacy-policy-links)。
1. 針對每個Facebook應用程式，建立 **[!UICONTROL Facebook Connect]** 類型外部帳戶。 有關詳情，請參閱：設 [定外部帳戶](#configuring-external-accounts)。
1. 針對每個Facebook應用程式，在Adobe Campaign中建立Facebook類型的網路應用程式。 有關詳情，請參閱：建 [立Facebook類型的Web應用程式](#creating-a-facebook-type-web-application)。
1. 設定您的Facebook應用程式，讓這些應用程式在您的Facebook頁面上顯示為標籤。 有關詳情，請參閱：設 [定Facebook標籤](#configuring-facebook-tabs)。

## 設定外部帳戶 {#configuring-external-accounts}

對於每個Facebook應用程式，您都需要建立類 **[!UICONTROL Facebook Connect]** 型外部帳戶。

此步驟需要存取您的Adobe Campaign主控台和登入您用於頁面管理的Facebook帳戶的網際網路瀏覽器：

* **Facebook**:選取先前建立的應用程式( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然後選取 **[!UICONTROL Settings]** >標籤 **[!UICONTROL Basic]** 。

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >如果未 **[!UICONTROL Facebook Web Games]** 出現區段，請按一 **[!UICONTROL Add Platform]** 下頁面底部的按鈕，然後選取 **[!UICONTROL Facebook Web Games]**。

* **Adobe Campaign**:轉到樹 **[!UICONTROL Administration > Platform > External accounts]** 的節點並按一下 **[!UICONTROL New]**。

   ![](assets/social_webapp_fb_005.png)

1. 輸入標籤和內部名稱，然後選擇類 **[!UICONTROL Facebook Connect]** 型。

   ![](assets/social_webapp_fb_006.png)

1. 為應用程式選擇代管模式：或 **[!UICONTROL hosted by a partner]** 者 **[!UICONTROL hosted by this instance]**。

   ![](assets/social_webapp_fb_012.png)

   **合作夥伴代管的應用程式**

   您可將Adobe Campaign與合作夥伴開發的Facebook應用程式整合。 在這種情況下，您不需要使用Adobe Campaign網頁應用程式來取得Facebook設定檔。 當Facebook使用者安裝應用程式時，會產生金鑰（存取Token）。 合作夥伴會呼叫web services，將此存取Token轉送至Adobe Campaign。 然後，Adobe Campaign會使用此Token登入Facebook資料庫，並收集使用者透過應用程式分享的資料。

   >[!NOTE]
   >
   >Web服務的參數在以下網址提供的WSDL檔案中有詳細說明： **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   若要將協力廠商應用程式整合至Adobe Campaign，您必須複製和 **[!UICONTROL App ID]****[!UICONTROL App Secret]** Facebook欄位的內容，並貼到主控台 **[!UICONTROL Application ID]** 的和 **[!UICONTROL Application secret]** 欄位中。

   ![](assets/social_facebook_external_account_013.png)

   **由此實例托管的應用程式**

   如果您想要在此例項上代管應用程式（如果您沒有協力廠商應用程式），則需要使用Adobe Campaign網頁應用程式來取得Facebook設定檔。 如需詳細資訊，請參閱Facebook應 [用程式範例](../../social/using/examples-of-facebook-apps.md)。

   在Adobe Campaign主控台中，複製欄位中包含的位 **[!UICONTROL Secure Canvas URL]** 址並貼入Facebook( **[!UICONTROL Facebook Web games (https)]** 區段中)的 **[!UICONTROL Facebook Web Games]** 欄位。

   ![](assets/social_facebook_external_account_009.png)

   >[!CAUTION]
   >
   >您不得在任何情況下使用不安全的URL。

   在Facebook上，複製和欄位 **[!UICONTROL App ID]** 的內 **[!UICONTROL App Secret]** 容，並貼入 **[!UICONTROL Application ID]** 主控台的和 **[!UICONTROL Application secret]** 欄位中。

   ![](assets/social_facebook_external_account_008.png)

1. 在Facebook上，按一 **[!UICONTROL Save Changes]** 下頁面底部的按鈕。
1. 在Adobe Campaign主控台中，按一 **[!UICONTROL Subscribe]** 下按鈕，讓Adobe Campaign在粉絲每次透過此應用程式簽入時即時復原資料。 有關詳情，請參閱：Facebook [應用程式範例](../../social/using/examples-of-facebook-apps.md)。

   ![](assets/social_webapp_fb_013.png)

## 輸入服務條款和隱私權政策連結 {#entering-the-terms-of-service-and-privacy-policy-links}

我們強烈建議新增 **[!UICONTROL Terms of service]** 和連 **[!UICONTROL Privacy policy]** 結，以便顯示在Facebook權限要求畫面上。

![](assets/social_fb_terms_of_services_001.png)

配置階段如下：

1. 輸入以下地址： [https://developers.facebook.com/apps](https://developers.facebook.com/apps)，然後選取Facebook應用程式。
1. 選擇標 **[!UICONTROL Settings > Basic]** 簽並輸入 **[!UICONTROL Privacy Policy URL]** 和字 **[!UICONTROL Terms of Service URL]** 段。

   ![](assets/social_fb_terms_of_services.png)

## 建立Facebook類型網頁應用程式 {#creating-a-facebook-type-web-application}

Adobe Campaign facebook應用程式可讓您在Facebook應用程式中顯示個人化內容。 對於每個Facebook應用程式，您都需要在Adobe Campaign中建立網頁應用程式。 若要建立Facebook網路應用程式，請依照下列步驟進行：

1. 前往宇宙 **[!UICONTROL Social networks]** ，按一下連結 **[!UICONTROL Applications]** ，然後按一下 **[!UICONTROL Create]** 按鈕。

   ![](assets/social_webapp_001.png)

1. 從清單中選取Facebook網頁應用程式範本，然後輸入標籤。

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >預設提供4個Facebook網頁應用程式範本：
   >
   >* **[!UICONTROL New Facebook application]**:如果要從空白應用程式啟動，請選擇此模板。
   >* **[!UICONTROL Pre-entered form]**:Facebook應用程式包含表單和「Facebook登入」按鈕，可讓使用者使用其個人資料中的資料自動填寫表單的欄位。 這可讓使用者更快完成表單，讓品牌獲得更優質的資訊。
   >* **[!UICONTROL "Canvas page" competition]**:螢幕上顯示的Facebook應用程式，為使用者提供更佳的視覺體驗。
   >* **[!UICONTROL "Page Tab" competition]**:Facebook應用程式已完全整合至品牌頁面標籤。


1. 在欄位 **[!UICONTROL Application]** 中，輸入連結至Facebook應用程式的外部帳戶。 有關詳情，請參閱：設 [定外部帳戶](#configuring-external-accounts)。

   ![](assets/social_webapp_005.png)

1. 選取標 **[!UICONTROL Edit]** 簽，然後編輯Web應用程式。 有關詳情，請參閱：Facebook [應用程式範例](../../social/using/examples-of-facebook-apps.md)。

   ![](assets/social_webapp_003.png)

1. Web應用程式完成後，請選取標 **[!UICONTROL Dashboard]** 簽，然後按一 **[!UICONTROL Publish]** 下以線上發佈。

   ![](assets/social_webapp_004.png)

## 設定Facebook標籤 {#configuring-facebook-tabs}

您可以設定您的Facebook應用程式，使其顯示為Facebook頁面上的標籤。 若要這麼做，請套用下列步驟：

1. 選取Facebook應用程式([https://developers.facebook.com/apps](https://developers.facebook.com/apps))，並選取 **[!UICONTROL Settings > Basic]** 標籤。

   ![](assets/social_webapp_fb_008.png)

1. 在頁面底部，按一下按鈕 **[!UICONTROL Add Platform]** 並選取 **[!UICONTROL Page Tab]**。

   ![](assets/social_webapp_fb_008bis.png)

1. 在區 **[!UICONTROL Page Tab Name]** 段的欄 **[!UICONTROL Page Tab]** 位中，輸入您要在Facebook頁面上顯示的標籤。

   ![](assets/social_webapp_fb_001.png)

1. 在欄位 **[!UICONTROL Secure Page Tab URL]** 中，輸入Web應用程式的公用URL，此URL可透過Web應用程式的 **[!UICONTROL Dashboard]** 標籤存取。 如需建立Facebook類型網頁應用程式的詳細資訊，請參 [閱建立Facebook類型網頁應用程式](#creating-a-facebook-type-web-application)。

   ![](assets/social_webapp_fb_002.png)

1. 在Web應 **[!UICONTROL Dashboard]** 用程式上，按一下連 **[!UICONTROL Add a page tab]** 結。

   ![](assets/social_webapp_fb_0010.png)

1. 選取您要新增標籤至的Facebook頁面，然後按一下 **[!UICONTROL Add Page Tab]**。

   ![](assets/social_webapp_fb_0011.png)


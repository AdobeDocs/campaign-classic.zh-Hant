---
solution: Campaign Classic
product: campaign
title: 建立 Facebook 應用程式
description: 建立 Facebook 應用程式
audience: social
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 1%

---


# 建立 Facebook 應用程式{#creating-a-facebook-application}

由於有了網路應用程式，Social Marketing可讓您在Facebook應用程式中顯示個人化內容，讓透過此社交網路取得潛在客戶變得更容易。 如需Facebook類型網頁應用程式的更多範例，請參閱[ Facebook應用程式範例](../../social/using/examples-of-facebook-apps.md)。

>[!NOTE]
>
>您也可以將Adobe Campaign與合作夥伴開發的Facebook應用程式整合。 在這種情況下，不需要使用Adobe Campaign網頁應用程式來取得Facebook個人檔案。 有關詳細資訊，請參閱[配置外部帳戶](#configuring-external-accounts)。

![](assets/social_webapp_fb_000.png)

套用下列設定步驟：

1. 建立一或多個Facebook應用程式。 有關詳情，請參閱：[建立Facebook應用程式](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)。
1. 輸入要顯示在Facebook權限請求畫面上的&#x200B;**[!UICONTROL terms of service]**&#x200B;和&#x200B;**[!UICONTROL Privacy policy]**&#x200B;連結。 有關詳情，請參閱：[輸入服務條款和隱私權政策連結](#entering-the-terms-of-service-and-privacy-policy-links)。
1. 針對每個Facebook應用程式，建立&#x200B;**[!UICONTROL Facebook Connect]**&#x200B;類型的外部帳戶。 有關詳情，請參閱：[設定外部帳戶](#configuring-external-accounts)。
1. 針對每個Facebook應用程式，在Adobe Campaign建立Facebook類型的網頁應用程式。 有關詳情，請參閱：[建立Facebook類型的網路應用程式](#creating-a-facebook-type-web-application)。
1. 設定您的Facebook應用程式，讓這些應用程式在您的Facebook頁面上顯示為標籤。 有關詳情，請參閱：[設定Facebook標籤](#configuring-facebook-tabs)。

## 設定外部帳戶 {#configuring-external-accounts}

對於每個Facebook應用程式，您必須建立&#x200B;**[!UICONTROL Facebook Connect]**&#x200B;類型的外部帳戶。

此步驟需要存取您的Adobe Campaign主控台和登入您用於頁面管理的Facebook帳戶的網際網路瀏覽器：

* **Facebook**:選擇先前建立的應用程式( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然後選擇 **[!UICONTROL Settings]** >選 **[!UICONTROL Basic]** 項卡。

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >如果未顯示&#x200B;**[!UICONTROL Facebook Web Games]**&#x200B;部分，請按一下頁面底部的&#x200B;**[!UICONTROL Add Platform]**&#x200B;按鈕，然後選擇&#x200B;**[!UICONTROL Facebook Web Games]**。

* **Adobe Campaign**:轉到樹 **[!UICONTROL Administration > Platform > External accounts]** 的節點並按一下 **[!UICONTROL New]**。

   ![](assets/social_webapp_fb_005.png)

1. 輸入標籤和內部名稱，然後選擇&#x200B;**[!UICONTROL Facebook Connect]**&#x200B;類型。

   ![](assets/social_webapp_fb_006.png)

1. 為應用程式選擇代管模式：**[!UICONTROL hosted by a partner]**&#x200B;或&#x200B;**[!UICONTROL hosted by this instance]**。

   ![](assets/social_webapp_fb_012.png)

   **合作夥伴代管的應用程式**

   將Adobe Campaign與合作夥伴開發的Facebook應用程式整合是可能的。 在這種情況下，不需要使用Adobe Campaign網頁應用程式來取得Facebook個人檔案。 當Facebook使用者安裝應用程式時，會產生金鑰（存取Token）。 合作夥伴呼叫web service，將此存取Token轉送給Adobe Campaign。 Adobe Campaign接著使用此Token登入Facebook資料庫，並收集使用者透過應用程式分享的資料。

   >[!NOTE]
   >
   >Web服務的參數在以下網址提供的WSDL檔案中有詳細說明：**`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   若要將協力廠商應用程式整合至Adobe Campaign，您必須複製&#x200B;**[!UICONTROL App ID]**&#x200B;和&#x200B;**[!UICONTROL App Secret]** Facebook欄位的內容，並貼入主控台的&#x200B;**[!UICONTROL Application ID]**&#x200B;和&#x200B;**[!UICONTROL Application secret]**&#x200B;欄位。

   ![](assets/social_facebook_external_account_013.png)

   **由此實例托管的應用程式**

   如果您想要在此例項上代管應用程式（如果您沒有協力廠商應用程式），則需要使用Adobe Campaign網頁應用程式來取得Facebook設定檔。 如需詳細資訊，請參閱[ Examples of Facebook apps](../../social/using/examples-of-facebook-apps.md)。

   在Adobe Campaign控制台中，複製&#x200B;**[!UICONTROL Secure Canvas URL]**&#x200B;欄位中包含的位址，並貼入Facebook上的&#x200B;**[!UICONTROL Facebook Web games (https)]**&#x200B;欄位（在&#x200B;**[!UICONTROL Facebook Web Games]**&#x200B;區段中）。

   ![](assets/social_facebook_external_account_009.png)

   >[!IMPORTANT]
   >
   >您不得在任何情況下使用不安全的URL。

   在Facebook上，複製&#x200B;**[!UICONTROL App ID]**&#x200B;和&#x200B;**[!UICONTROL App Secret]**&#x200B;欄位的內容，並貼入主控台的&#x200B;**[!UICONTROL Application ID]**&#x200B;和&#x200B;**[!UICONTROL Application secret]**&#x200B;欄位。

   ![](assets/social_facebook_external_account_008.png)

1. 在Facebook上，按一下頁面底部的&#x200B;**[!UICONTROL Save Changes]**&#x200B;按鈕。
1. 在Adobe Campaign控制台中，按一下&#x200B;**[!UICONTROL Subscribe]**&#x200B;按鈕，使Adobe Campaign能夠在風扇每次通過此應用程式簽入時即時恢復資料。 有關詳情，請參閱：[Facebook應用程式範例](../../social/using/examples-of-facebook-apps.md)。

   ![](assets/social_webapp_fb_013.png)

## 輸入服務條款和隱私權政策連結{#entering-the-terms-of-service-and-privacy-policy-links}

我們強烈建議新增&#x200B;**[!UICONTROL Terms of service]**&#x200B;和&#x200B;**[!UICONTROL Privacy policy]**&#x200B;連結，以便顯示在Facebook權限要求畫面上。

![](assets/social_fb_terms_of_services_001.png)

配置階段如下：

1. 輸入以下地址：[https://developers.facebook.com/apps](https://developers.facebook.com/apps)，然後選取Facebook應用程式。
1. 選擇&#x200B;**[!UICONTROL Settings > Basic]**&#x200B;頁籤，然後輸入&#x200B;**[!UICONTROL Privacy Policy URL]**&#x200B;和&#x200B;**[!UICONTROL Terms of Service URL]**&#x200B;欄位。

   ![](assets/social_fb_terms_of_services.png)

## 建立Facebook類型的Web應用程式{#creating-a-facebook-type-web-application}

Adobe CampaignFacebook應用程式可讓您在Facebook應用程式中顯示個人化內容。 對於每個Facebook應用程式，您都需要在Adobe Campaign建立Web應用程式。 若要建立Facebook網路應用程式，請依照下列步驟進行：

1. 前往&#x200B;**[!UICONTROL Social networks]**&#x200B;標籤，按一下&#x200B;**[!UICONTROL Applications]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Create]**&#x200B;按鈕。

   ![](assets/social_webapp_001.png)

1. 從清單中選取Facebook網頁應用程式範本，然後輸入標籤。

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >預設提供4個Facebook網頁應用程式範本：
   >
   >* **[!UICONTROL New Facebook application]**:如果要從空白應用程式啟動，請選擇此模板。
   >* **[!UICONTROL Pre-entered form]**:Facebook應用程式包含表單和「Facebook登入」按鈕，可讓使用者使用其個人資料中的資料自動填寫表單的欄位。這可讓使用者更快完成表單，讓品牌獲得更優質的資訊。
   >* **[!UICONTROL "Canvas page" competition]**:螢幕上顯示的Facebook應用程式，為使用者提供更佳的視覺體驗。
   >* **[!UICONTROL "Page Tab" competition]**:Facebook應用程式已完全整合至品牌頁面標籤。


1. 在&#x200B;**[!UICONTROL Application]**&#x200B;欄位中，輸入連結至Facebook應用程式的外部帳戶。 有關詳情，請參閱：[設定外部帳戶](#configuring-external-accounts)。

   ![](assets/social_webapp_005.png)

1. 選擇&#x200B;**[!UICONTROL Edit]**&#x200B;標籤，然後編輯Web應用程式。 有關詳情，請參閱：[Facebook應用程式範例](../../social/using/examples-of-facebook-apps.md)。

   ![](assets/social_webapp_003.png)

1. Web應用程式完成後，選取&#x200B;**[!UICONTROL Dashboard]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Publish]**&#x200B;以線上發佈。

   ![](assets/social_webapp_004.png)

## 設定Facebook標籤{#configuring-facebook-tabs}

您可以設定您的Facebook應用程式，使其顯示為Facebook頁面上的標籤。 若要這麼做，請套用下列步驟：

1. 選取Facebook應用程式([https://developers.facebook.com/apps](https://developers.facebook.com/apps))，並選取&#x200B;**[!UICONTROL Settings > Basic]**&#x200B;標籤。

   ![](assets/social_webapp_fb_008.png)

1. 在頁面底部，按一下&#x200B;**[!UICONTROL Add Platform]**&#x200B;按鈕，然後選擇&#x200B;**[!UICONTROL Page Tab]**。

   ![](assets/social_webapp_fb_008bis.png)

1. 在&#x200B;**[!UICONTROL Page Tab]**&#x200B;區段的&#x200B;**[!UICONTROL Page Tab Name]**&#x200B;欄位中，輸入您要在Facebook頁面上顯示的標籤。

   ![](assets/social_webapp_fb_001.png)

1. 在&#x200B;**[!UICONTROL Secure Page Tab URL]**&#x200B;欄位中，輸入Web應用程式的公用URL，此URL可透過Web應用程式的&#x200B;**[!UICONTROL Dashboard]**&#x200B;標籤存取。 如需建立Facebook類型網頁應用程式的詳細資訊，請參閱「建立Facebook類型網頁應用程式」](#creating-a-facebook-type-web-application)。[

   ![](assets/social_webapp_fb_002.png)

1. 在Web應用程式的&#x200B;**[!UICONTROL Dashboard]**&#x200B;上，按一下&#x200B;**[!UICONTROL Add a page tab]**&#x200B;連結。

   ![](assets/social_webapp_fb_0010.png)

1. 選取您要新增標籤至的Facebook頁面，然後按一下&#x200B;**[!UICONTROL Add Page Tab]**。

   ![](assets/social_webapp_fb_0011.png)


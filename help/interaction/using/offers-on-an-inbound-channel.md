---
solution: Campaign Classic
product: campaign
title: 傳入頻道上的優惠方案
description: 傳入頻道上的優惠方案
audience: interaction
content-type: reference
topic-tags: case-study
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2088'
ht-degree: 1%

---


# 傳入頻道上的優惠方案{#offers-on-an-inbound-channel}

## 向匿名訪客呈現選件{#presenting-an-offer-to-an-anonymous-visitor}

Neobank網站想在其網站上顯示選件，以針對瀏覽該頁面的未識別訪客。

若要設定此互動，我們將：

1. [建立匿名環境](#creating-an-anonymous-environment)
1. [建立匿名選件空間](#creating-anonymous-offer-spaces)
1. [建立選件類別和主題](#creating-an-offer-category-and-a-theme)
1. [建立匿名選件。](#creating-anonymous-offers)
1. [在網站上設定Web選件空間](#configure-the-web-offer-space-on-the-website)

### 建立匿名環境{#creating-an-anonymous-environment}

請依照[建立選件環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)中詳述的程式，根據&#x200B;**訪客**&#x200B;維度建立匿名環境。

您將得到包含新環境的樹結構：

![](assets/offer_env_anonymous_003.png)

### 建立匿名選件空格{#creating-anonymous-offer-spaces}

1. 在您的匿名環境中（**訪客**），前往&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Spaces]**&#x200B;節點。
1. 按一下&#x200B;**[!UICONTROL New]**&#x200B;以建立呼叫通道。

   ![](assets/offer_inbound_anonymous_example_010.png)

   >[!NOTE]
   >
   >空間會自動連結到匿名環境。

1. 更改標籤並選擇&#x200B;**[!UICONTROL Inbound Web]**&#x200B;通道。 您也必須勾選&#x200B;**[!UICONTROL Enable unitary mode]**&#x200B;方塊。

   ![](assets/offer_inbound_anonymous_example_006.png)

1. 選取空間使用的選件內容欄位，並勾選相關方塊以視需要指定這些欄位。

   如此一來，任何遺失下列元素之一的選件都不符合此空間的資格：

   * 標題
   * HTML內容
   * 影像URL
   * 目標URL

   ![](assets/offer_inbound_anonymous_example_030.png)

1. 編輯HTML轉換函式，例如：

   ```
   function (imageUrl, targetUrl, shortContent, htmlSource){
         var html = "<p><b>" + shortContent + "</b></p>";
         html += "<p>" + htmlSource + "</p>";
         html += "<a _urlType='11' href='" + targetUrl + "'><img src='" + encodeURI(imageUrl) + "'/></a>";
         return html;
       }   
   ```

   >[!IMPORTANT]
   >
   >轉換函式必須依照先前選取的順序為空間所用的欄位命名，如此選件才能正確顯示。

   ![](assets/offer_inbound_anonymous_example_031.png)

1. 儲存選件空間。

### 建立選件類別和主題{#creating-an-offer-category-and-a-theme}

1. 轉到剛建立的環境中的&#x200B;**[!UICONTROL Offer catalog]**&#x200B;節點。
1. 按一下右鍵&#x200B;**[!UICONTROL Offer catalog]**&#x200B;節點，然後選擇&#x200B;**[!UICONTROL Create a new 'Offer category' folder]**。

   例如，為新類別命名&#x200B;**Financial products**。

1. 轉至類別的&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，然後輸入&#x200B;**financing**&#x200B;作為主題，然後儲存變更。

   ![](assets/offer_inbound_anonymous_example_023.png)

### 建立匿名選件{#creating-anonymous-offers}

1. 前往您剛建立的類別。
1. 按一下 **[!UICONTROL New]**。

   ![](assets/offer_inbound_anonymous_example_013.png)

1. 選取現成可用的匿名選件範本或先前建立的範本。

   ![](assets/offer_inbound_anonymous_example_014.png)

1. 變更標籤並儲存選件。

   ![](assets/offer_inbound_anonymous_example_015.png)

1. 前往&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並根據選件的應用程式內容指定選件的權重。

   在此範例中，選件設定為以優先順序顯示在網站的首頁上，直到年底為止。

   ![](assets/offer_inbound_anonymous_example_016.png)

1. 前往&#x200B;**[!UICONTROL Content]**&#x200B;標籤，並定義選件的內容。

   >[!NOTE]
   >
   >您可以選擇&#x200B;**[!UICONTROL Content definitions]**&#x200B;以顯示Web空間所需的元素清單。

   ![](assets/offer_inbound_anonymous_example_017.png)

1. 建立第二個選件。

   ![](assets/offer_inbound_anonymous_example_018.png)

1. 前往&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並套用與第一個選件相同的重量。
1. 執行每個選件的審批週期，以便線上上環境中提供它們及其批准的選件空間。

### 在網站{#configure-the-web-offer-space-on-the-website}上設定Web選件空間

若要讓您剛剛設定的選件在網站上顯示，請將JavaScript程式碼插入網站的HTML頁面，以呼叫互動引擎（如需詳細資訊，請參閱[關於傳入頻道](../../interaction/using/about-inbound-channels.md)）。

1. 前往HTML頁面並插入@id屬性，其值與先前建立之匿名選件空間的內部名稱相符（請參閱[建立匿名選件空間](#creating-anonymous-offer-spaces)），前面有&#x200B;**i_**。

   ![](assets/offer_inbound_anonymous_example_019.png)

1. 插入呼叫URL。

   ![](assets/offer_inbound_anonymous_example_020.png)

   上述藍色URL框對應於實例名稱、環境的內部名稱（請參閱[建立匿名環境](#creating-an-anonymous-environment)）和連結到類別的主題（[建立選件類別和主題](#creating-an-offer-category-and-a-theme)）。 後者是可選的。

當訪客存取網站首頁時，具有&#x200B;**financing**&#x200B;主題的選件會顯示為HTML頁面上的設定。

![](assets/offer_inbound_anonymous_example_022.png)

多次瀏覽頁面的使用者將會看到類別中的其中一個或其他選件，因為這兩個選件都已指派相同的權重。

## 在未識別聯繫人{#switching-to-an-anonymous-environment-in-case-of-unidentified-contacts}時切換到匿名環境

Neobank公司想要為兩個不同的目標建立行銷選件。 它想要針對其匿名網站瀏覽器顯示一般選件。 如果這些用戶中的一位是Neobank提供的識別碼的客戶，公司希望他們在登錄後立即收到個人化優惠。

此案例研究基於以下情形：

1. 訪客瀏覽Neobank網站時未登入。

   ![](assets/offer_inbound_fallback_example_050.png)

   頁面上會顯示三個匿名選件：Neobank產品提供2個&#x200B;**最佳優惠**,Neobank合作夥伴提供1個優惠。

   ![](assets/offer_inbound_fallback_example_051.png)

1. Neobank客戶用戶使用他的憑據登錄。

   ![](assets/offer_inbound_fallback_example_052.png)

   展示3個個人化優惠。

   ![](assets/offer_inbound_fallback_example_053.png)

若要實作此案例研究，您必須有兩個選件環境：一個用於匿名互動，另一個用於特別針對識別的聯絡人設定選件。 已識別的選件環境將配置為在聯繫人未登錄且因此未識別時自動切換到匿名的選件環境。

應用以下步驟：

* 使用下列步驟建立匿名傳入互動專屬的選件目錄：

   1. [為匿名聯繫人建立環境](#creating-an-environment-for-anonymous-contacts)
   1. [為匿名環境配置選件空間](#configuring-offer-spaces-for-the-anonymous-environment)
   1. [在匿名環境中建立選件類別](#creating-offer-categories-in-an-anonymous-environment)
   1. [建立匿名訪客的選件](#creating-offers-for-anonymous-visitors)

* 使用下列步驟建立特定於已識別傳入互動的選件目錄：

   1. [在識別的環境中設定選件空間](#configure-the-offer-spaces-in-the-identified-environment)
   1. [在已識別的環境中建立選件類別](#creating-offer-categories-in-an-identified-environment)
   1. [建立個人化優惠](#creating-personalized-offers)

* 設定對選件引擎的呼叫：

   1. [在網頁上設定選件空間](#configuring-offer-spaces-on-the-web-page)
   1. [指定已識別選件空間的進階設定](#specifying-the-advanced-settings-of-the-identified-offer-spaces)

### 為匿名聯繫人建立環境{#creating-an-environment-for-anonymous-contacts}

1. 透過傳送對應精靈（**訪客**&#x200B;對應），建立匿名傳入互動的選件環境。 有關詳細資訊，請參閱[建立選件環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

   ![](assets/offer_env_anonymous_003.png)

### 為匿名環境{#configuring-offer-spaces-for-the-anonymous-environment}配置選件空間

必須在網站上顯示的選件屬於兩個不同類別：**最佳優惠**&#x200B;和&#x200B;**合作夥伴**。 在此範例中，我們將為每個類別建立特定的選件空間。

若要建立符合&#x200B;**最佳選件**&#x200B;類別的選件空間，請套用下列程式：

1. 在Adobe Campaign樹狀結構中，前往您剛建立的匿名環境，並新增選件空間。

   ![](assets/offer_inbound_fallback_example_023.png)

1. 建立新的&#x200B;**[!UICONTROL Inbound web]**&#x200B;類型空間。

   ![](assets/offer_inbound_fallback_example_024.png)

1. 輸入標籤：例如&#x200B;**Web最佳匿名選件**。
1. 新增用於此選件空間的選件內容欄位，並設定轉換函式。

   ![](assets/offer_inbound_fallback_example_025.png)

   >[!IMPORTANT]
   >
   >轉換函式必須依照先前選取的順序為空間所用的欄位命名，如此選件才能正確顯示。

1. 使用相同的流程建立入站Web渠道選件空間，以匹配&#x200B;**Partner**&#x200B;類別。

   ![](assets/offer_inbound_fallback_example_026.png)

### 在匿名環境{#creating-offer-categories-in-an-anonymous-environment}中建立選件類別

首先，請建立兩個選件類別：**最佳優惠**&#x200B;類別和&#x200B;**合作夥伴**&#x200B;類別。 每個類別都會包含兩個匿名聯絡人的選件。

1. 前往您剛建立之匿名環境中的&#x200B;**[!UICONTROL Offer catalog]**。
1. 新增&#x200B;**[!UICONTROL Offer category]**&#x200B;資料夾，其中&#x200B;**最佳選件**&#x200B;為標籤。

   ![](assets/offer_inbound_fallback_example_027.png)

1. 以&#x200B;**Partner**&#x200B;作為標籤建立第二個類別。

   ![](assets/offer_inbound_fallback_example_028.png)

### 建立匿名訪客的選件{#creating-offers-for-anonymous-visitors}

現在，我們將在上述每個類別中建立兩個選件。

1. 前往&#x200B;**最佳選件**&#x200B;類別並建立匿名選件。

   ![](assets/offer_inbound_fallback_example_029.png)

1. 前往&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並根據選件的應用程式內容指定選件的權重。

   ![](assets/offer_inbound_fallback_example_030.png)

1. 前往&#x200B;**[!UICONTROL Content]**&#x200B;標籤，並定義選件的內容。

   ![](assets/offer_inbound_fallback_example_032.png)

1. 在&#x200B;**最佳選件**&#x200B;類別中建立第二個選件。

   ![](assets/offer_inbound_fallback_example_031.png)

1. 前往&#x200B;**Partner**&#x200B;類別並建立匿名選件。
1. 前往&#x200B;**[!UICONTROL Content]**&#x200B;標籤，並定義選件的內容。

   ![](assets/offer_inbound_fallback_example_033.png)

1. 前往&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並根據選件的應用程式內容指定選件的權重。

   ![](assets/offer_inbound_fallback_example_034.png)

1. 為&#x200B;**Partner**&#x200B;類別建立第二個選件。

   ![](assets/offer_inbound_fallback_example_035.png)

1. 前往&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並套用您套用至此類別第一個選件的相同權重，如此，選件就會連續顯示在網站上。

   ![](assets/offer_inbound_fallback_example_036.png)

1. 執行每個選件的核准週期，以開始上線。 在核准內容時，請根據選件啟用&#x200B;**合作夥伴**&#x200B;或&#x200B;**最佳選件**&#x200B;選件空間。

### 在識別的環境{#configure-the-offer-spaces-in-the-identified-environment}中配置選件空間

您要在網站上展示的選件來自兩個不同的類別：**最佳優惠**&#x200B;和&#x200B;**合作夥伴**。 在此範例中，我們想為每個類別建立特定的空間。

若要建立兩個選件空間，請套用與匿名選件空間相同的程式。 請參閱[為匿名環境配置選件空間](#configuring-offer-spaces-for-the-anonymous-environment)。

1. 在Adobe Campaign樹狀結構中，前往您剛建立的環境，並新增&#x200B;**最佳選件**&#x200B;和&#x200B;**合作夥伴**&#x200B;選件空間。
1. 應用[為匿名環境配置選件空間中詳細說明的過程](#configuring-offer-spaces-for-the-anonymous-environment)。

   ![](assets/offer_inbound_fallback_example_005.png)

1. 選擇&#x200B;**[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**&#x200B;選項。

   ![](assets/offer_inbound_fallback_example_006.png)

1. 使用下拉式清單，選取先前建立的匿名Web選件空間（請參閱[為匿名環境設定選件空間](#configuring-offer-spaces-for-the-anonymous-environment)）。

   ![](assets/offer_inbound_fallback_example_007.png)

### 指定已識別選件空間{#specifying-the-advanced-settings-of-the-identified-offer-spaces}的進階設定

在此範例中，由於Adobe Campaign資料庫中的電子郵件地址，所以會發生連絡人識別。 若要將收件者電子郵件新增至空間，請套用下列程式：

1. 在已識別的環境中，移至選件空間檔案夾。
1. 選擇&#x200B;**最佳選件**&#x200B;選件空間，然後按一下&#x200B;**[!UICONTROL Advanced parameters]**。

   ![](assets/offer_inbound_fallback_example_044.png)

1. 在 **[!UICONTROL Target identification]** 索引標籤中，按一下 **[!UICONTROL Add]**。

   ![](assets/offer_inbound_fallback_example_046.png)

1. 按一下&#x200B;**[!UICONTROL Edit expression]** ，轉到收件人表並選擇&#x200B;**[!UICONTROL Email]**&#x200B;欄位。

   ![](assets/offer_inbound_fallback_example_047.png)

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;關閉&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;窗口並完成&#x200B;**最佳選件**&#x200B;選件空間的配置。
1. 對&#x200B;**Partner**&#x200B;選件空間應用相同的流程。

   ![](assets/offer_inbound_fallback_example_048.png)

### 在已識別的環境{#creating-offer-categories-in-an-identified-environment}中建立選件類別

我們將建立兩個不同的類別：**最佳優惠**&#x200B;類別和&#x200B;**合作夥伴**&#x200B;類別，每個類別都包含兩個個人化優惠。

1. 轉到所標識環境中的&#x200B;**[!UICONTROL Offer catalogs]**&#x200B;節點。
1. 在匿名環境中，添加兩個&#x200B;**[!UICONTROL Offer category]**&#x200B;資料夾作為標籤，其中&#x200B;**最佳選件**&#x200B;和&#x200B;**合作夥伴**。

   ![](assets/offer_inbound_fallback_example_009.png)

### 建立個人化優惠{#creating-personalized-offers}

我們想要為每個類別建立兩個個人化優惠，即四個優惠。

1. 前往&#x200B;**最佳優惠**&#x200B;類別並建立第一個個人化優惠。

   ![](assets/offer_inbound_fallback_example_011.png)

1. 前往&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並根據選件的應用程式內容指定選件的權重。

   ![](assets/offer_inbound_fallback_example_012.png)

1. 前往&#x200B;**[!UICONTROL Content]**&#x200B;標籤，並定義選件的內容。

   ![](assets/offer_inbound_fallback_example_013.png)

1. 在&#x200B;**最佳選件**&#x200B;類別中建立第二個選件。

   ![](assets/offer_inbound_fallback_example_014.png)

1. 前往&#x200B;**Partner**&#x200B;類別並建立個人化優惠。

   ![](assets/offer_inbound_fallback_example_015.png)

1. 前往&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並根據選件的應用程式內容指定選件的權重。

   ![](assets/offer_inbound_fallback_example_016.png)

1. 為&#x200B;**Partner**&#x200B;類別建立第二個選件。

   ![](assets/offer_inbound_fallback_example_017.png)

1. 前往&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並套用您套用至此類別第一個選件的相同權重，如此，選件就會連續顯示在網站上。
1. 執行每個選件的核准週期，以開始更新選件。 在內容核准期間，啟動&#x200B;**合作夥伴**&#x200B;或&#x200B;**最佳優惠**&#x200B;優惠空間。

### 在網頁{#configuring-offer-spaces-on-the-web-page}上設定選件空間

Neobank公司的網站有3個選件空間：2個用於&#x200B;**最佳優惠**&#x200B;類別的銀行相關優惠，1個用於&#x200B;**合作夥伴**&#x200B;類別的優惠。

![](assets/offer_inbound_fallback_example_038.png)

若要在網站的HTML頁面上設定這些選件空格，請套用下列程式：

1. 在HTML頁面的內容中，插入三個

   具有@id屬性的元素，其值可讓我們在網站的各種選件空間中呼叫選件。

   ![](assets/offer_inbound_fallback_example_039.png)

1. 然後插入用於定義屬性值的指令碼。

   ![](assets/offer_inbound_fallback_example_040.png)

   在此示例中，**ContBO1**&#x200B;和&#x200B;**ContBO2**&#x200B;接收值&#x200B;**OsWebBestOfferIdentified**，即先前在所識別環境中建立的&#x200B;**最佳選件**&#x200B;選件空間的內部名稱。 **CatBestOffer**&#x200B;和&#x200B;**CatBestOfferAnomy**&#x200B;值與&#x200B;**Best Offer**&#x200B;類別的內部名稱相符，適用於匿名和已識別環境。

   ![](assets/offer_inbound_fallback_example_041.png)

   同樣地，**ContPtn**&#x200B;接收&#x200B;**OSWebPartnerInfied**&#x200B;值，該值與在識別環境中建立的&#x200B;**Partner**&#x200B;選件空間的內部名稱相匹配。 **CatPartner和** CatPartnerAnnoyment會為匿名和已識別的環境 ****  **** 比對Partnercategories的內部名稱。

   ![](assets/offer_inbound_fallback_example_042.png)

1. 將可讓您識別登入Neobank網站的人員的資訊指派給&#x200B;**interactionTarget**&#x200B;變數。

   ![](assets/offer_inbound_fallback_example_043.png)

   該人員的識別碼可以是以瀏覽器Cookie、URL中的讀取參數、電子郵件或該人員的識別碼為基礎。 如果使用主鍵以外的收件者表欄位，則需在空間的高級參數中定義該欄位（請參閱[指定所標識選件空間的高級設定](#specifying-the-advanced-settings-of-the-identified-offer-spaces)）。

1. 插入呼叫URL。

   ![](assets/offer_inbound_fallback_example_049.png)

   該URL包含&#x200B;**EnvNeobankRecip**，標識環境的內部名稱。

當您開啟網頁時；此指令碼可讓您呼叫互動引擎，以在網頁的相關空間中顯示選件的內容。 在對Adobe Campaign伺服器的單一呼叫中，引擎會決定環境、選件空間和要選取的類別。

在此示例中，引擎識別所識別的環境(**EnvNeobankIdnRecip**)。 它識別網頁上第一個和第二個選件空間的選件空間(**OSWebBestOfferIdentified**)和&#x200B;**最佳選件**&#x200B;類別(**CatBestOffer**)，以及(**OSWebpartnerInsified**)為站點上的第三個選件空間提供空間和&#x200B;**Partner**&#x200B;類別(**CatPartner**)。

如果引擎無法識別收件者，則會切換至已識別的選件空間中參考的匿名選件空間，並切換至指令碼中指定的匿名類別（**CatPartner**&#x200B;和&#x200B;**CatPartnerAnomy**）。

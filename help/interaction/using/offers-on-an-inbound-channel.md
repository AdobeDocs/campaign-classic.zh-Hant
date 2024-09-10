---
product: campaign
title: 傳入頻道上的優惠
description: 傳入頻道上的優惠
feature: Interaction, Offers
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: 90afced3-465d-4370-8a33-51a7e4356135
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '2097'
ht-degree: 1%

---

# 傳入頻道上的優惠{#offers-on-an-inbound-channel}



## 向匿名訪客展示優惠方案 {#presenting-an-offer-to-an-anonymous-visitor}

Neobank網站想要在其網站上針對瀏覽頁面的未識別訪客顯示選件。

若要設定此互動，我們將：

1. [建立匿名環境](#creating-an-anonymous-environment)
1. [建立匿名優惠方案空間](#creating-anonymous-offer-spaces)
1. [建立優惠方案類別和主題](#creating-an-offer-category-and-a-theme)
1. [建立匿名優惠方案。](#creating-anonymous-offers)
1. [在網站上設定網站優惠方案空間](#configure-the-web-offer-space-on-the-website)

### 建立匿名環境 {#creating-an-anonymous-environment}

請依照[建立優惠方案環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)中詳述的程式，根據&#x200B;**訪客**&#39;維度建立您的匿名環境。

您會獲得包含新環境的樹狀結構：

![](assets/offer_env_anonymous_003.png)

### 建立匿名優惠方案空間 {#creating-anonymous-offer-spaces}

1. 在您的匿名環境中（**訪客**）前往&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Spaces]**&#x200B;節點。
1. 按一下&#x200B;**[!UICONTROL New]**&#x200B;以建立通話管道。

   ![](assets/offer_inbound_anonymous_example_010.png)

   >[!NOTE]
   >
   >空間會自動連結至匿名環境。

1. 變更標籤並選取&#x200B;**[!UICONTROL Inbound Web]**&#x200B;管道。 您也必須勾選&#x200B;**[!UICONTROL Enable unitary mode]**&#x200B;方塊。

   ![](assets/offer_inbound_anonymous_example_006.png)

1. 選取用於空間的選件內容欄位，並核取相關方塊，視需要指定這些欄位。

   如此一來，遺失下列其中一項元素的任何優惠方案都將不符合此空間的資格：

   * 標題
   * HTML 內容
   * 影像 URL
   * 目的地 URL

   ![](assets/offer_inbound_anonymous_example_030.png)

1. 編輯HTML演算函式，例如：

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
   >轉譯函式必須依先前選取的順序命名用於空間的欄位，以便正確顯示選件。

   ![](assets/offer_inbound_anonymous_example_031.png)

1. 儲存優惠方案空間。

### 建立優惠方案類別和主題 {#creating-an-offer-category-and-a-theme}

1. 前往您剛建立之環境中的&#x200B;**[!UICONTROL Offer catalog]**&#x200B;節點。
1. 用滑鼠右鍵按一下&#x200B;**[!UICONTROL Offer catalog]**&#x200B;節點並選取&#x200B;**[!UICONTROL Create a new 'Offer category' folder]**。

   為新類別命名，例如&#x200B;**金融產品**。

1. 移至類別的&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並輸入&#x200B;**financing**&#x200B;作為主題，然後儲存變更。

   ![](assets/offer_inbound_anonymous_example_023.png)

### 建立匿名優惠方案 {#creating-anonymous-offers}

1. 前往您剛才建立的類別。
1. 按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/offer_inbound_anonymous_example_013.png)

1. 選取現成可用的匿名優惠方案範本或先前建立的範本。

   ![](assets/offer_inbound_anonymous_example_014.png)

1. 變更標籤並儲存您的選件。

   ![](assets/offer_inbound_anonymous_example_015.png)

1. 移至&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並根據其應用程式內容指定優惠方案的權重。

   在此範例中，選件會設定為優先顯示在網站首頁上，直到年底為止。

   ![](assets/offer_inbound_anonymous_example_016.png)

1. 前往&#x200B;**[!UICONTROL Content]**&#x200B;標籤並定義優惠方案的內容。

   >[!NOTE]
   >
   >您可以選取&#x200B;**[!UICONTROL Content definitions]**&#x200B;以顯示網頁空間所需的元素清單。

   ![](assets/offer_inbound_anonymous_example_017.png)

1. 建立第二個選件。

   ![](assets/offer_inbound_anonymous_example_018.png)

1. 移至&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並套用與第一個優惠方案相同的權重。
1. 執行每個優惠方案的核准週期，以便線上上環境中提供這些優惠方案及其已核准的優惠方案空間。

### 設定網站上的Web優惠方案空間 {#configure-the-web-offer-space-on-the-website}

若要將您剛設定的優惠方案顯示在網站上，請在網站的HTML頁面中插入JavaScript程式碼，以呼叫互動引擎（如需詳細資訊，請參閱[關於傳入頻道](../../interaction/using/about-inbound-channels.md)）。

1. 前往HTML頁面，插入一個與先前建立的匿名優惠方案空間內部名稱相符的@id屬性（請參閱[建立匿名優惠方案空間](#creating-anonymous-offer-spaces)），前面加上&#x200B;**i_**。

   ![](assets/offer_inbound_anonymous_example_019.png)

1. 插入呼叫URL

   ![](assets/offer_inbound_anonymous_example_020.png)

   上方的藍色URL方塊對應到執行個體名稱、環境的內部名稱（請參閱[建立匿名環境](#creating-an-anonymous-environment)）以及連結到類別的主題（[建立優惠類別和主題](#creating-an-offer-category-and-a-theme)）。 後者是選擇性的。

當訪客存取網站的首頁時，具有&#x200B;**financing**&#x200B;主題的優惠方案會依設定顯示在HTML頁面上。

![](assets/offer_inbound_anonymous_example_022.png)

多次造訪頁面的使用者會在類別中看到一個或其他選件，因為它們都被指派了相同的權重。

## 切換到匿名環境，以防未識別的連絡人 {#switching-to-an-anonymous-environment-in-case-of-unidentified-contacts}

Neobank公司想要針對兩個不同的目標建立行銷優惠方案。 想要為其匿名網站瀏覽器顯示一般優惠方案。 如果其中一位使用者是具有Neobank所提供識別碼的客戶，公司希望他們登入後能立即收到個人化優惠方案。

此案例研究是根據下列情境：

1. 訪客無需登入即可瀏覽Neobank網站。

   ![](assets/offer_inbound_fallback_example_050.png)

   頁面上會顯示三個匿名選件：兩個Neobank產品的&#x200B;**最佳選件**&#x200B;選件，以及一個Neobank合作夥伴的選件。

   ![](assets/offer_inbound_fallback_example_051.png)

1. 該使用者（Neobank客戶）會使用其憑證登入。

   ![](assets/offer_inbound_fallback_example_052.png)

   接著會顯示三個個人化優惠方案。

   ![](assets/offer_inbound_fallback_example_053.png)

若要實作此案例研究，您需要有兩個優惠方案環境：一個用於匿名互動，另一個具有專為已識別聯絡人設定的優惠方案。 如果連絡人未登入，系統就會將已識別的優惠方案環境設定為自動切換至匿名優惠方案環境，因此也無法識別。

應用以下步驟：

* 使用下列步驟，建立匿名傳入互動專屬的優惠方案目錄：

   1. [建立匿名連絡人的環境](#creating-an-environment-for-anonymous-contacts)
   1. [為匿名環境設定優惠方案空間](#configuring-offer-spaces-for-the-anonymous-environment)
   1. [在匿名環境中建立優惠方案類別](#creating-offer-categories-in-an-anonymous-environment)
   1. [建立匿名訪客的優惠](#creating-offers-for-anonymous-visitors)

* 使用下列步驟，建立已識別之入站互動專屬的優惠方案目錄：

   1. [在已識別的環境中設定優惠方案空間](#configure-the-offer-spaces-in-the-identified-environment)
   1. [在已識別的環境中建立優惠方案類別](#creating-offer-categories-in-an-identified-environment)
   1. [建立個人化優惠方案](#creating-personalized-offers)

* 設定對優惠方案引擎的呼叫：

   1. [在網頁上設定優惠方案空間](#configuring-offer-spaces-on-the-web-page)
   1. [指定已識別優惠方案空間的進階設定](#specifying-the-advanced-settings-of-the-identified-offer-spaces)

### 建立匿名連絡人的環境 {#creating-an-environment-for-anonymous-contacts}

1. 透過傳遞對應助理（**訪客**&#x200B;對應），為匿名傳入互動建立優惠方案環境。 如需詳細資訊，請參閱[建立優惠方案環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

   ![](assets/offer_env_anonymous_003.png)

### 為匿名環境設定優惠方案空間 {#configuring-offer-spaces-for-the-anonymous-environment}

必須顯示在網站上的優惠方案屬於兩個不同的類別： **最佳優惠方案**&#x200B;和&#x200B;**合作夥伴**。 在此範例中，我們將為每個類別建立特定的優惠方案空間。

若要建立優惠方案空間以符合&#x200B;**最佳優惠方案**&#x200B;類別，請套用下列程式：

1. 在Adobe Campaign樹中，前往您剛才建立的匿名環境，並新增優惠方案空間。

   ![](assets/offer_inbound_fallback_example_023.png)

1. 建立新的&#x200B;**[!UICONTROL Inbound web]**&#x200B;型別空間。

   ![](assets/offer_inbound_fallback_example_024.png)

1. 輸入它的標籤：執行個體的&#x200B;**網頁最佳匿名優惠**。
1. 新增用於此選件空間的選件內容欄位，並設定轉譯函式。

   ![](assets/offer_inbound_fallback_example_025.png)

   >[!IMPORTANT]
   >
   >轉譯函式必須依先前選取的順序命名用於空間的欄位，以便正確顯示選件。

1. 使用相同的程式來建立傳入的Web Channel優惠方案空間，以符合&#x200B;**合作夥伴**&#x200B;類別。

   ![](assets/offer_inbound_fallback_example_026.png)

### 在匿名環境中建立優惠方案類別 {#creating-offer-categories-in-an-anonymous-environment}

首先，請建立兩個優惠方案類別： **最佳優惠方案**&#x200B;類別和&#x200B;**合作夥伴**&#x200B;類別。 每個類別都會包含匿名聯絡人的兩個優惠方案。

1. 前往您剛建立的匿名環境中的&#x200B;**[!UICONTROL Offer catalog]**。
1. 新增具有&#x200B;**最佳選件**&#x200B;的&#x200B;**[!UICONTROL Offer category]**&#x200B;資料夾作為標籤。

   ![](assets/offer_inbound_fallback_example_027.png)

1. 建立以&#x200B;**合作夥伴**&#x200B;為標籤的第二個類別。

   ![](assets/offer_inbound_fallback_example_028.png)

### 建立匿名訪客的優惠 {#creating-offers-for-anonymous-visitors}

現在，我們將在上述建立的每個類別中建立兩個優惠方案。

1. 移至&#x200B;**最佳優惠**&#x200B;類別並建立匿名優惠。

   ![](assets/offer_inbound_fallback_example_029.png)

1. 移至&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並根據其應用程式內容指定優惠方案的權重。

   ![](assets/offer_inbound_fallback_example_030.png)

1. 前往&#x200B;**[!UICONTROL Content]**&#x200B;標籤並定義優惠方案的內容。

   ![](assets/offer_inbound_fallback_example_032.png)

1. 在&#x200B;**最佳選件**&#x200B;類別中建立第二個選件。

   ![](assets/offer_inbound_fallback_example_031.png)

1. 移至&#x200B;**合作夥伴**&#x200B;類別並建立匿名優惠方案。
1. 前往&#x200B;**[!UICONTROL Content]**&#x200B;標籤並定義優惠方案的內容。

   ![](assets/offer_inbound_fallback_example_033.png)

1. 移至&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並根據其應用程式內容指定優惠方案的權重。

   ![](assets/offer_inbound_fallback_example_034.png)

1. 建立&#x200B;**合作夥伴**&#x200B;類別的第二個優惠方案。

   ![](assets/offer_inbound_fallback_example_035.png)

1. 移至&#x200B;**[!UICONTROL Eligibility]**&#x200B;索引標籤，並套用您套用至此類別中第一個優惠方案的相同權重，讓優惠方案可依序顯示在網站上。

   ![](assets/offer_inbound_fallback_example_036.png)

1. 對每個優惠方案執行核准週期，以開始讓優惠方案上線。 核准內容時，請根據優惠方案啟動&#x200B;**合作夥伴**&#x200B;或&#x200B;**最佳優惠方案**&#x200B;優惠方案空間。

### 在已識別的環境中設定優惠方案空間 {#configure-the-offer-spaces-in-the-identified-environment}

您即將出現在網站上的優惠方案來自兩個不同的類別： **最佳優惠方案**&#x200B;和&#x200B;**合作夥伴**。 在此範例中，我們要為每個類別建立特定空間。

若要建立兩個優惠方案空間，請套用與匿名優惠方案空間相同的程式。 請參閱[為匿名環境設定優惠方案空間](#configuring-offer-spaces-for-the-anonymous-environment)。

1. 在Adobe Campaign樹狀結構中，移至您剛才建立的環境，並新增&#x200B;**最佳優惠方案**&#x200B;和&#x200B;**合作夥伴**&#x200B;優惠方案空間。
1. 套用[設定匿名環境的優惠方案空間](#configuring-offer-spaces-for-the-anonymous-environment)中詳述的處理程式。

   ![](assets/offer_inbound_fallback_example_005.png)

1. 選取&#x200B;**[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**&#x200B;選項。

   ![](assets/offer_inbound_fallback_example_006.png)

1. 使用下拉式清單，選取先前建立的匿名Web優惠方案空間（請參閱[設定匿名環境的優惠方案空間](#configuring-offer-spaces-for-the-anonymous-environment)）。

   ![](assets/offer_inbound_fallback_example_007.png)

### 指定已識別優惠方案空間的進階設定 {#specifying-the-advanced-settings-of-the-identified-offer-spaces}

在此範例中，聯絡人識別是因為Adobe Campaign資料庫中的電子郵件地址。 若要將收件者電子郵件新增至空間，請套用下列程式：

1. 在已識別的環境中，前往優惠方案空間資料夾。
1. 選取&#x200B;**最佳選件**&#x200B;選件空間，然後按一下&#x200B;**[!UICONTROL Advanced parameters]**。

   ![](assets/offer_inbound_fallback_example_044.png)

1. 在 **[!UICONTROL Target identification]** 索引標籤中，按一下 **[!UICONTROL Add]**。

   ![](assets/offer_inbound_fallback_example_046.png)

1. 按一下&#x200B;**[!UICONTROL Edit expression]**，前往收件者表格並選取&#x200B;**[!UICONTROL Email]**&#x200B;欄位。

   ![](assets/offer_inbound_fallback_example_047.png)

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;以關閉&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;視窗，並完成設定&#x200B;**最佳選件**&#x200B;選件空間。
1. 為&#x200B;**合作夥伴**&#x200B;優惠方案空間套用相同的處理序。

   ![](assets/offer_inbound_fallback_example_048.png)

### 在已識別的環境中建立優惠方案類別 {#creating-offer-categories-in-an-identified-environment}

我們將建立兩個個別的類別： **最佳優惠**&#x200B;類別和&#x200B;**合作夥伴**&#x200B;類別，每個類別都有兩個個人化優惠。

1. 前往已識別環境中的&#x200B;**[!UICONTROL Offer catalogs]**&#x200B;節點。
1. 如同匿名環境，新增兩個具有&#x200B;**最佳選件**&#x200B;和&#x200B;**合作夥伴**&#x200B;的&#x200B;**[!UICONTROL Offer category]**&#x200B;資料夾作為標籤。

   ![](assets/offer_inbound_fallback_example_009.png)

### 建立個人化優惠方案 {#creating-personalized-offers}

我們希望為每個類別建立兩個個人化優惠方案，即四個優惠方案。

1. 移至&#x200B;**最佳優惠**&#x200B;類別並建立第一個個人化優惠。

   ![](assets/offer_inbound_fallback_example_011.png)

1. 移至&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並根據其應用程式內容指定優惠方案的權重。

   ![](assets/offer_inbound_fallback_example_012.png)

1. 前往&#x200B;**[!UICONTROL Content]**&#x200B;標籤並定義優惠方案的內容。

   ![](assets/offer_inbound_fallback_example_013.png)

1. 在&#x200B;**最佳選件**&#x200B;類別中建立第二個選件。

   ![](assets/offer_inbound_fallback_example_014.png)

1. 移至&#x200B;**合作夥伴**&#x200B;類別並建立個人化優惠方案。

   ![](assets/offer_inbound_fallback_example_015.png)

1. 移至&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤，並根據其應用程式內容指定優惠方案的權重。

   ![](assets/offer_inbound_fallback_example_016.png)

1. 建立&#x200B;**合作夥伴**&#x200B;類別的第二個優惠方案。

   ![](assets/offer_inbound_fallback_example_017.png)

1. 移至&#x200B;**[!UICONTROL Eligibility]**&#x200B;索引標籤，並套用您套用至此類別中第一個優惠方案的相同權重，讓優惠方案可依序顯示在網站上。
1. 執行每個優惠方案的核准週期，以開始更新它們。 在內容核准期間，啟用&#x200B;**合作夥伴**&#x200B;或&#x200B;**最佳優惠**&#x200B;優惠空間。

### 在網頁上設定優惠方案空間 {#configuring-offer-spaces-on-the-web-page}

Neobank公司的網站有三個優惠方案空間：兩個適用於&#x200B;**最佳優惠方案**&#x200B;類別中的銀行相關優惠方案，另一個適用於&#x200B;**合作夥伴**&#x200B;類別中的優惠方案。

![](assets/offer_inbound_fallback_example_038.png)

若要在網站的HTML頁面上設定這些優惠方案空間，請套用下列程式：

1. 在HTML頁面的內容中，插入三個

   具有@id屬性的元素，其值可讓我們在網站的各種優惠方案空間中呼叫優惠方案。

   ![](assets/offer_inbound_fallback_example_039.png)

1. 然後插入用於定義屬性值的指令碼。

   ![](assets/offer_inbound_fallback_example_040.png)

   在此範例中，**ContBO1**&#x200B;和&#x200B;**ContBO2**&#x200B;會收到值&#x200B;**OsWebBestOfferIdentified**，也就是先前在已識別環境中建立的&#x200B;**最佳選件**&#x200B;選件空間的內部名稱。 **CatBestOffer**&#x200B;和&#x200B;**CatBestOfferAnonym**&#x200B;值符合匿名與已識別環境之&#x200B;**最佳選件**&#x200B;類別的內部名稱。

   ![](assets/offer_inbound_fallback_example_041.png)

   同樣地，**ContPtn**&#x200B;會收到&#x200B;**OSWebPartnerIdentified**&#x200B;值，該值符合在已識別環境中建立的&#x200B;**合作夥伴**&#x200B;優惠空間的內部名稱。 **CatPartner**&#x200B;與&#x200B;**CatPartnerAnonym**&#x200B;符合匿名與已識別環境之&#x200B;**Partner**&#x200B;類別的內部名稱。

   ![](assets/offer_inbound_fallback_example_042.png)

1. 將可讓您識別登入Neobank網站之人員的資訊指派給&#x200B;**interactionTarget**&#x200B;變數。

   ![](assets/offer_inbound_fallback_example_043.png)

   個人的身分識別可以根據瀏覽器Cookie、URL中的閱讀引數、電子郵件或個人的識別碼。 如果使用主索引鍵以外的收件者表格欄位，則必須在空間的進階引數中定義該欄位（請參閱[指定已識別之優惠方案的進階設定](#specifying-the-advanced-settings-of-the-identified-offer-spaces)）。

1. 插入呼叫URL

   ![](assets/offer_inbound_fallback_example_049.png)

   URL包含&#x200B;**EnvNeobankRecip**，已識別環境的內部名稱。

當您開啟網頁時，指令碼可讓您呼叫互動引擎，以在網頁的相關空間中顯示選件的內容。 在對Adobe Campaign伺服器的單一呼叫中，引擎會決定環境、選件空間和要選取的類別。

在此範例中，引擎會辨識已識別的環境(**EnvNeobankIdnRecip**)。 它可識別網頁上第一個和第二個優惠方案空間的優惠方案空間(**OSWebBestOfferIdentified**)和&#x200B;**最佳優惠方案**&#x200B;類別(**CatBestOffer**)，以及網站上的第三個優惠方案空間的(**OSWebPartnerIdentified**)優惠方案空間和&#x200B;**合作夥伴**&#x200B;類別(**CatPartner**)。

如果引擎無法識別收件者，它會切換到已識別之優惠方案空間中所參考的匿名優惠方案空間，並依照指令碼中的指定，切換到匿名類別（**CatPartner**&#x200B;和&#x200B;**CatPartnerAnonym**）。

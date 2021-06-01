---
product: campaign
title: Facebook 應用程式範例
description: Facebook 應用程式範例
audience: social
content-type: reference
topic-tags: annexes
exl-id: 3b8c7db4-9c55-42f6-8e09-e5ab781efe8f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 1%

---

# Facebook 應用程式範例{#examples-of-facebook-apps}

使用者按一下Facebook應用程式的標籤時，該標籤會以810像素寬的空間顯示。 Adobe Campaign使用Facebook類型的網頁應用程式，讓您定義及個人化Facebook應用程式中顯示的內容，以便更輕鬆取得設定檔。

>[!NOTE]
>
>您也可以將Adobe Campaign與合作夥伴開發的Facebook應用程式整合。 在此情況下，不需要使用Adobe Campaign Web應用程式來取得Facebook設定檔。 有關詳細資訊，請參閱[設定外部帳戶](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

![](assets/social_webapp_fb_000.png)

>[!IMPORTANT]
>
>請遵循[建立Facebook應用程式](../../social/using/creating-a-facebook-application.md)中所述的配置步驟。

>[!NOTE]
>
>本節詳細說明連結至Facebook類型Web應用程式的元素。 與標準Web應用程式共用的所有元素在[本節](../../web/using/about-web-applications.md)中有詳細說明。

以下是Facebook類型Web應用程式的詳細範例：

* 如何在7個步驟中建立Facebook應用程式。 請參閱[快速入門：在7個步驟中建立Facebook應用程式](#quick-start--creating-a-facebook-application-in-7-steps)。
* 如何將設定轉送至Facebook應用程式。 請參閱[如何將設定轉送至Facebook應用程式？](#how-to-forward-settings-to-a-facebook-application-)。
* 如何獲取風扇資料。 請參閱[如何獲取風扇資料？](#how-to-acquire-fan-data-)。

>[!IMPORTANT]
>
>以下簡單使用案例舉例說明Facebook類型Web應用程式的功能。

## 建議 {#recommendations}

下列限制會直接連結至Facebook:

* 您必須使用HTTPS建置所有Web應用程式。
* 透過索引標籤顯示的Facebook應用程式寬度為810像素。

## 快速入門：在7個步驟中建立Facebook應用程式{#quick-start--creating-a-facebook-application-in-7-steps}

此範例提供如何在Facebook中顯示Adobe Campaign內建應用程式的逐步程式。 在此情況下，我們想建立一個應用程式，讓您在使用者按一下應用程式索引標籤(**App01**)時顯示&#x200B;**歡迎**&#x200B;訊息。

要建立此應用程式，請應用以下步驟：

1. 在Facebook上建立應用程式([https://developers.facebook.com/apps](https://developers.facebook.com/apps))。 有關詳細資訊，請參閱：[建立Facebook應用程式](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)。

   ![](assets/social_create_facebook_app_002.png)

1. 建立&#x200B;**[!UICONTROL Facebook Connect]**&#x200B;類型外部帳戶，並輸入Facebook應用程式的參數。 有關詳細資訊，請參閱：[配置外部帳戶](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

   ![](assets/social_quick_start_2.png)

1. 輸入要在Facebook權限請求畫面上顯示的&#x200B;**[!UICONTROL Terms of service]**&#x200B;和&#x200B;**[!UICONTROL Privacy policy]**&#x200B;連結。 有關詳細資訊，請參閱：[輸入服務條款和隱私權政策連結](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links)。

   ![](assets/social_quick_start_1.png)

1. 在Adobe Campaign中建立Facebook類型的Web應用程式。 有關詳細資訊，請參閱：[建立Facebook類型web應用程式](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)。

   ![](assets/social_webapp_005.png)

1. 編輯您的Web應用程式。 在此範例中，我們已新增&#x200B;**[!UICONTROL Page]**&#x200B;活動並為其定義標題。

   ![](assets/social_quick_start_4.png)

1. 部署應用程式。

   ![](assets/social_webapp_004.png)

1. 設定您的Facebook應用程式，使其在Facebook頁面上顯示為索引標籤。 有關詳細資訊，請參閱：[設定Facebook標籤](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs)。

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

檢查您的Facebook頁面上是否顯示&#x200B;**App01**&#x200B;應用程式的標籤。 按一下它應會呼叫&#x200B;**歡迎**&#x200B;訊息。

![](assets/social_webapp_042.png)

## 如何將設定轉送至Facebook應用程式？{#how-to-forward-settings-to-a-facebook-application-}

>[!IMPORTANT]
>
>遵循[建立Facebook應用程式](../../social/using/creating-a-facebook-application.md)中詳述的設定步驟。

在範例1中，我們根據&#x200B;**[!UICONTROL Fan of the page]**&#x200B;欄位中的值個人化Facebook頁面的顯示。 也可以處理&#x200B;**[!UICONTROL Application settings]**&#x200B;欄位。 此欄位可讓您透過Facebook，復原Adobe Campaign產生之連結中所包含的資料。

讓我們以決定傳送電子郵件促銷活動的公司為例。 在傳送中，會有指向Facebook應用程式的連結。 此連結會因URL結尾新增的&#x200B;**[!UICONTROL app_data]**&#x200B;參數而個人化。 此參數的值可以是反映客戶重要性的指標。 在我們的範例中，**[!UICONTROL app_data]**&#x200B;參數的值為&#x200B;**[!UICONTROL big]**（重要客戶）和&#x200B;**[!UICONTROL small]**（不重要客戶）。

個人化後，URL會如下所示：

* `http://<path of the Facebook application>&app_data=big` （針對重要客戶）
* `http://<path of the Facebook application>&app_data=small` （針對不重要客戶）

在Facebook轉送至Adobe Campaign的匿名資料中，會收集&#x200B;**[!UICONTROL Application parameters]**&#x200B;欄位的值，讓Adobe Campaign能夠根據此參數個人化應用程式顯示。

如果使用者是重要客戶（**[!UICONTROL app_data]**&#x200B;參數的值為&#x200B;**[!UICONTROL big]**），則會顯示下列影像：

![](assets/social_webapp_017.png)

如果使用者不太重要（**[!UICONTROL app_data]**&#x200B;參數的值為&#x200B;**[!UICONTROL small]**），則會顯示下列影像：

![](assets/social_webapp_016.png)

為重新建立此使用案例，我們建立了由以下元素組成的Web應用程式：

* 根據&#x200B;**[!UICONTROL Application parameter]**&#x200B;欄位的&#x200B;**[!UICONTROL Test]**&#x200B;活動。
* 包含要根據&#x200B;**[!UICONTROL Application parameter]**&#x200B;欄位值顯示的影像的兩頁。

![](assets/social_webapp_018.png)

## 如何獲取風扇資料？{#how-to-acquire-fan-data-}

>[!IMPORTANT]
>
>遵循[建立Facebook應用程式](../../social/using/creating-a-facebook-application.md)中詳述的設定步驟。

此範例說明如何與Facebook使用者取得聯絡，並提供給他們以共用其設定檔資訊。 讓我們舉一個公司的例子，它想要獲得潛在客戶，並在其Facebook頁面上組織競賽以吸引他們。

每當使用者按一下&#x200B;**[!UICONTROL App03]**&#x200B;標籤時，就會詢問他們是否要參加競爭。

![](assets/social_webapp_fb_000.png)

如果他們決定參加競賽，我們會提供他們分享個人資訊。

![](assets/social_webapp_021.png)

如果使用者同意共用其資訊，會顯示下列畫面。

![](assets/social_webapp_022.png)

為了建立此使用案例，我們建立了包含下列元素的Web應用程式：

* **[!UICONTROL Test]** 活動
* 三頁
* **[!UICONTROL Access control]**&#x200B;活動
* **[!UICONTROL Pre-loading]** 活動
* **[!UICONTROL Save]** 活動
* **[!UICONTROL End]**&#x200B;活動

![](assets/social_webapp_019.png)

### 測試活動{#test-activity}

**[!UICONTROL Test]**&#x200B;活動以&#x200B;**[!UICONTROL ID]**&#x200B;和&#x200B;**[!UICONTROL Application parameters]**&#x200B;欄位為基礎。

![](assets/social_webapp_023.png)

它由三個分支組成：

* **[!UICONTROL identifier (UID) is empty]** :只有在使用者已同意共用其資訊時，Facebook才會轉送識別碼。**[!UICONTROL Test]**&#x200B;活動的第一個分支可讓您讓競爭僅供從未輸入的使用者使用，亦即ID空白的使用者使用。
* **[!UICONTROL application parameter equals 'thanks']** :若要避開連結至Facebook的顯示錯誤，Web應用程式結束頁面會指向使用值新 **[!UICONTROL app_data]** 增參數的Facebook應用程 **[!UICONTROL thanks]** 式的URL(如需詳細資訊，請參閱： [結束活動](#end-activity))。第二個分支可讓您了解使用者是否來自第一個分支的&#x200B;**[!UICONTROL End]**&#x200B;活動（且剛進入競爭對手），以顯示感謝訊息。 如需使用其他URL參數的詳細資訊，請參閱：[如何將設定轉送至Facebook應用程式？](#how-to-forward-settings-to-a-facebook-application-)。
* **[!UICONTROL Default branch]** :如果使用者在前一個日期(應用程式參數與 **[!UICONTROL thanks]**&#x200B;不同)已輸入競爭（ID已輸入），我們會顯示一個頁面，指出他們已輸入。

### 競爭頁面{#competition-page}

若要避開連結至Facebook的顯示錯誤，您還需要在競爭頁面的&#x200B;**[!UICONTROL Window]**&#x200B;欄位中選取&#x200B;**[!UICONTROL Parent window]**&#x200B;或&#x200B;**[!UICONTROL In the top window]**。

![](assets/social_webapp_028.png)

### 訪問控制活動{#access-control-activity}

**[!UICONTROL Access control]**&#x200B;活動可讓您在使用者進入競爭時顯示Facebook權限請求頁面。 如果他們同意共用其資訊，則會在預先載入期間恢復資訊。 有關詳細資訊，請參閱：[預先載入活動](#pre-loading-activity)。

如果您先前在建立Web應用程式時輸入了外部帳戶(請參閱[建立Facebook類型Web應用程式](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application))，則不需要編輯活動。 若未包含，請前往&#x200B;**[!UICONTROL Application]**&#x200B;欄位，並選取連結至Facebook應用程式的外部帳戶。

![](assets/social_webapp_024.png)

### 預先載入活動{#pre-loading-activity}

選取要用於預先載入的資料來源：

* **[!UICONTROL Marketing database]** :此選項可讓您透過Adobe Campaign資料庫預先載入資料。
* **[!UICONTROL Facebook]** :此選項可讓您使用Facebook預先載入資料。

![](assets/social_webapp_029.png)

**行銷資料庫**

此選項可讓您復原訪客表格中存在之設定檔的資料。 驗證是根據使用者按一下Facebook應用程式標籤時復原的外部Facebook ID執行。 如果您在&#x200B;**[!UICONTROL Pre-loading]**&#x200B;活動後新增表單，則會預先載入包含資料庫資訊的欄位。

![](assets/social_webapp_030.png)

>[!NOTE]
>
>如需透過Adobe Campaign資料庫預先載入資料的詳細資訊，請參閱[此區段](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)。

**Facebook**

此選項可讓您定義要收集的Facebook設定檔資訊（其中包括使用者同意共用的資訊），以便儲存該資訊。

![](assets/social_webapp_025.png)

**[!UICONTROL Database information]**&#x200B;選項可讓您收集下列資料：

* **[!UICONTROL External ID]**:使用者ID
* **[!UICONTROL Gender]**:使用者性別
* **[!UICONTROL Verified]** :此欄位會指定使用者是否擁有已驗證的Facebook帳戶。
* **[!UICONTROL Full name]**:使用者的全名
* **[!UICONTROL First name]**:使用者的名字
* **[!UICONTROL Last name]**:使用者姓氏
* **[!UICONTROL Language]**:使用者語言

您也可以核取適當的方塊，以決定收集個人資料像片、朋友清單、電子郵件地址、出生日期、興趣和位置。

按一下&#x200B;**[!UICONTROL Ok]**&#x200B;之前，請核取&#x200B;**[!UICONTROL I agree to comply with Facebook conditions of use]**&#x200B;方塊。

>[!NOTE]
>
>如果您勾選&#x200B;**[!UICONTROL Private information]**&#x200B;區段中的一或多個方塊，Facebook權限請求畫面會自動顯示此資料的存取請求。
>
>若要收集選取的資訊，使用者必須同意共用該資訊。
>
>如果您想要兩種預先載入類型(透過Adobe Campaign和透過Facebook)，請逐一新增兩個預先載入方塊。

### 保存活動{#save-activity}

**[!UICONTROL Save]**&#x200B;活動可讓您將先前階段期間收集的資訊儲存在訪客的表格中。

如果訪客的表格中已存在設定檔，則會以收集到的新資料更新其資料。

如果資料庫中不存在設定檔，且已收集Facebook使用者的電子郵件地址，則訪客表格中會建立訪客。

![](assets/social_webapp_026.png)

1. 在&#x200B;**[!UICONTROL Visitor creation folder]**&#x200B;欄位中，選取要建立設定檔的資料夾。 若為Facebook類型的Web應用程式，預設的建立資料夾為&#x200B;**[!UICONTROL Visitors]**。
1. 在&#x200B;**[!UICONTROL Reconciliation mode]**&#x200B;欄位中，選取您要使用的調解模式：

   * **[!UICONTROL Automatic]** :調解是根據電子郵件、姓氏、名字和出生日期執行。
   * **[!UICONTROL Manual]** :請選擇一個或多個調解密鑰。
   * **[!UICONTROL None]** :不會進行和解。

1. 在&#x200B;**[!UICONTROL Mapping]**&#x200B;欄位中，選取要對其進行調解的架構。

   >[!IMPORTANT]
   >
   >請確定在傳送對應中已正確輸入&#x200B;**[!UICONTROL Social networks]**&#x200B;標籤的欄位。 傳遞對應可透過&#x200B;**[!UICONTROL Administration > Campaign management > Target mappings]**&#x200B;節點存取。

1. 您可以選取要協調的搜尋資料夾，以及新設定檔的建立資料夾。 如果欄位為空，則會搜尋設定檔，並在對應架構的預設資料夾中建立。

### 結束活動 {#end-activity}

若要避開連結至Facebook的顯示錯誤，您需要核取&#x200B;**[!UICONTROL Use an external URL]**&#x200B;方塊並輸入Facebook應用程式的URL，後面接著&#x200B;**[!UICONTROL app_data]**&#x200B;參數和值。 此值將用於&#x200B;**[!UICONTROL Test]**&#x200B;活動，以偵測使用者是否剛進入競爭，並顯示感謝訊息（若適用）。 有關詳細資訊，請參閱：[測試活動](#test-activity)。

在我們的範例中，使用的值為&#x200B;**thanks**。

![](assets/social_webapp_027.png)

### 訪客{#details-screen-of-a-visitor}的詳細資訊畫面

就像Twitter追隨者(請參閱：[操作原則](../../social/using/publishing-on-twitter.md#operating-principle))，已復原的Facebook設定檔會儲存在訪客的表格中。 若要顯示訪客清單，請前往&#x200B;**[!UICONTROL Profiles and Targets > Visitors]**&#x200B;節點。

同意共用其設定檔資訊的每個Facebook潛在客戶都會新增至訪客清單中。 如果在&#x200B;**[!UICONTROL Pre-load]**&#x200B;活動中勾選了&#x200B;**[!UICONTROL Friends]**&#x200B;方塊(請參閱：[預先載入活動](#pre-loading-activity))，也會新增朋友。

![](assets/social_webapp_037.png)

在訪客詳細資料視窗的&#x200B;**[!UICONTROL Summary]**&#x200B;區段中，**[!UICONTROL New Contact]**&#x200B;指標有兩個可能的狀態：

![](assets/social_webapp_038.png)

如果顯示綠色核取記號，表示訪客未與任何收件者調解。 在此情況下，收件者清單中會建立新的設定檔。

![](assets/social_webapp_039.png)

紅十字表示訪客已與收件者調解。 您可以按一下&#x200B;**[!UICONTROL Recipient]**&#x200B;欄位右側的放大鏡，以顯示相符的收件者。

![](assets/social_webapp_040.png)

前往收件者的詳細資料視窗，以顯示相符的訪客（如果適用）。 選取&#x200B;**[!UICONTROL Others]**&#x200B;標籤，然後在&#x200B;**[!UICONTROL Web identities]**&#x200B;區段中連按兩下訪客的名稱。

![](assets/social_webapp_041.png)

訪客詳細資料頁面的&#x200B;**[!UICONTROL Activities]**&#x200B;畫麵包含下列資訊：

* 「開啟圖」類型風扇活動：播放的音樂、觀看的視頻、閱讀的文章以及安裝的應用程式（Deezer、Spotify、Dailymotion、Yahoo News等）的不詳

   ![](assets/social_facebook_activities.png)

* 粉絲在Adobe Campaign傳送後新增的「按贊次數」和留言
* 粉絲贊的頁面
* 風扇的簽入

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >為了讓Adobe Campaign收集風扇的簽入，您需要按一下服務配置螢幕上的&#x200B;**[!UICONTROL Subscribe]**&#x200B;按鈕。 有關詳細資訊，請參閱[設定外部帳戶](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

## 如何使用Facebook設定檔資料{#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}預先載入表單的欄位

**[!UICONTROL Social Marketing]**&#x200B;應用程式也可讓您將按鈕新增至表單，以使用Facebook設定檔資訊預先載入欄位。 在[此部分](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)中詳細介紹了此選項，該選項可用於所有Web應用程式模板（**[!UICONTROL Page]**&#x200B;類型活動）。

![](assets/social_webapp_035.png)

>[!NOTE]
>
>開始使用此函式之前，您需要建立Facebook應用程式，並輸入外部帳戶&#x200B;**[!UICONTROL Facebook Connect]**。 有關詳細資訊，請參閱[設定外部帳戶](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

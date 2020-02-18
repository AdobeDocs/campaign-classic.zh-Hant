---
title: Facebook應用程式範例
seo-title: Facebook應用程式範例
description: Facebook應用程式範例
seo-description: null
page-status-flag: never-activated
uuid: 336f4006-3545-4b04-959d-61cd0446af27
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: annexes
discoiquuid: 07be1d3c-b038-48ca-be37-a33adb8e0fc0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Facebook應用程式範例{#examples-of-facebook-apps}

當使用者按一下Facebook應用程式的標籤時，會以810像素寬的空間顯示。 Adobe Campaign使用Facebook類型的網路應用程式，讓您定義並個人化Facebook應用程式中顯示的內容，因此更容易取得個人檔案。

>[!NOTE]
>
>您也可以將Adobe Campaign與合作夥伴開發的Facebook應用程式整合。 在這種情況下，您不需要使用Adobe Campaign網頁應用程式來取得Facebook設定檔。 有關詳細資訊，請參閱 [配置外部帳戶](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

![](assets/social_webapp_fb_000.png)

>[!IMPORTANT]
>
>請遵循「建立Facebook應用程式」中 [所述的設定步驟](../../social/using/creating-a-facebook-application.md)。

>[!NOTE]
>
>本節詳細說明連結至Facebook類型網頁應用程式的元素。 與標準Web應用程式共用的所有元素在本節中 [有詳細說明](../../web/using/about-web-applications.md)。

Facebook類型網頁應用程式的範例如下：

* 如何透過7個步驟建立Facebook應用程式。 請參閱快 [速入門：以7個步驟建立Facebook應用程式](#quick-start--creating-a-facebook-application-in-7-steps)。
* 如何將設定轉送至Facebook應用程式。 請參閱 [如何將設定轉送至Facebook應用程式](#how-to-forward-settings-to-a-facebook-application-)。
* 如何獲取風扇資料。 請參閱 [如何獲取風扇資料](#how-to-acquire-fan-data-)。

>[!IMPORTANT]
>
>這些簡單的使用案例為範例，說明Facebook類型網頁應用程式的功能。

## 建議 {#recommendations}

下列限制會直接連結至Facebook:

* 您必須使用HTTPS來建立所有的Web應用程式。
* 透過標籤顯示的Facebook應用程式寬度為810像素。

## 快速入門：以7個步驟建立Facebook應用程式 {#quick-start--creating-a-facebook-application-in-7-steps}

此範例提供如何在Facebook中顯示Adobe Campaign建立應用程式的逐步程式。 在這種情況下，我們想要建立應用程式，讓您在使用者按一下應用程式標籤( **App01******)時，顯示「歡迎」訊息。

若要建立此應用程式，請套用下列步驟：

1. 在Facebook上建立應用程式( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))。 有關詳情，請參閱：建 [立Facebook應用程式](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)。

   ![](assets/social_create_facebook_app_002.png)

1. 建立類 **[!UICONTROL Facebook Connect]** 型外部帳戶，並輸入Facebook應用程式的參數。 有關詳情，請參閱：設 [定外部帳戶](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

   ![](assets/social_quick_start_2.png)

1. 輸入要 **[!UICONTROL Terms of service]** 在 **[!UICONTROL Privacy policy]** Facebook權限請求畫面上顯示的和連結。 有關詳情，請參閱：輸 [入服務條款和隱私權政策連結](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links)。

   ![](assets/social_quick_start_1.png)

1. 在Adobe Campaign中建立Facebook類型的網頁應用程式。 有關詳情，請參閱：建 [立Facebook類型的Web應用程式](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)。

   ![](assets/social_webapp_005.png)

1. 編輯您的Web應用程式。 在此範例中，我們新增了活 **[!UICONTROL Page]** 動並定義了活動標題。

   ![](assets/social_quick_start_4.png)

1. 部署您的應用程式。

   ![](assets/social_webapp_004.png)

1. 設定您的Facebook應用程式，使其在您的Facebook頁面上顯示為標籤。 有關詳情，請參閱：設 [定Facebook標籤](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs)。

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

檢查 **App01應用程式的標籤** ，是否顯示在您的Facebook頁面上。 按一下它應該會呼叫歡 **迎訊息** 。

![](assets/social_webapp_042.png)

## 如何將設定轉送至Facebook應用程式？ {#how-to-forward-settings-to-a-facebook-application-}

>[!IMPORTANT]
>
>遵循建立Facebook應用程式中詳 [細的設定步驟](../../social/using/creating-a-facebook-application.md)。

在範例1中，我們根據欄位中的值個人化Facebook頁面的顯 **[!UICONTROL Fan of the page]** 示。 您也可以處理欄 **[!UICONTROL Application settings]** 位。 此欄位可讓您透過Facebook恢復Adobe Campaign產生之連結中所含的資料。

讓我們以決定傳送電子郵件促銷活動的公司為例。 在傳送中，會指向Facebook應用程式的連結。 由於URL結尾已新增 **[!UICONTROL app_data]** 參數，因此此連結會個人化。 此參數的值可以是反映客戶重要性的指標。 在我們的範例中，參數的值 **[!UICONTROL app_data]** 是 **[!UICONTROL big]** （重要客戶） **[!UICONTROL small]** 和（較不重要客戶）。

一旦個人化後，URL會如下所示：

* `http://<path of the Facebook application>&app_data=big` （對於重要客戶）
* `http://<path of the Facebook application>&app_data=small` （對於不那麼重要的客戶）

在Facebook轉送至Adobe Campaign的匿名資料中，會收集欄位的值，讓 **[!UICONTROL Application parameters]** Adobe Campaign能夠根據此參數個人化應用程式顯示。

如果使用者是重要客戶(參數的值 **[!UICONTROL app_data]** 為 **[!UICONTROL big]**)，則會顯示下列影像：

![](assets/social_webapp_017.png)

如果使用者是較不重要的客戶(參 **[!UICONTROL app_data]** 數的 **[!UICONTROL small]**&#x200B;值)，則會顯示下列影像：

![](assets/social_webapp_016.png)

為重新建立此使用案例，我們建立了由以下元素組成的Web應用程式：

* 基於 **[!UICONTROL Test]** 欄位的活動 **[!UICONTROL Application parameter]** 。
* 兩個頁面，其中包含要根據欄位值顯示的影 **[!UICONTROL Application parameter]** 像。

![](assets/social_webapp_018.png)

## 如何獲取風扇資料？ {#how-to-acquire-fan-data-}

>[!CAUTION]
>
>遵循建立Facebook應用程式中詳 [細的設定步驟](../../social/using/creating-a-facebook-application.md)。

此範例說明如何與Facebook使用者聯絡，並提供他們分享個人檔案資訊的選件。 讓我們舉一個公司想要收購潛在客戶，並在其Facebook頁面上組織競賽以吸引他們的例子。

每當使用者按一 **[!UICONTROL App03]** 下標籤時，我們會詢問他們是否想參加競賽。

![](assets/social_webapp_fb_000.png)

如果他們決定參加競賽，我們會提供他們個人檔案資訊。

![](assets/social_webapp_021.png)

如果他們同意分享其資訊，會顯示下列畫面。

![](assets/social_webapp_022.png)

為建立此使用案例，我們建立了包含下列元素的Web應用程式：

* 活 **[!UICONTROL Test]** 動
* 三頁
* 活 **[!UICONTROL Access control]** 動
* 活 **[!UICONTROL Pre-loading]** 動
* 活 **[!UICONTROL Save]** 動
* 活 **[!UICONTROL End]** 動

![](assets/social_webapp_019.png)

### 測試活動 {#test-activity}

活 **[!UICONTROL Test]** 動是以和欄 **[!UICONTROL ID]** 位為 **[!UICONTROL Application parameters]** 基礎。

![](assets/social_webapp_023.png)

它由三個分支組成：

* **[!UICONTROL identifier (UID) is empty]** :只有當使用者已同意分享其資訊時，Facebook才會轉送識別碼。 活動的第一個分支 **[!UICONTROL Test]** 可讓您讓競爭對手只提供給從未輸入的使用者（即具有空ID的使用者）使用。
* **[!UICONTROL application parameter equals 'thanks']** :若要避免連結至Facebook的顯示錯誤，網頁應用程式結束頁面會指向Facebook應用程式的URL, **[!UICONTROL app_data]** 而參數會被新增至使用 **[!UICONTROL thanks]** 值(如需詳細資訊，請參閱：結 [束活動](#end-activity))。 第二個分支可讓您瞭解使用者是否來自第 **[!UICONTROL End]** 一個分支的活動（且剛進入競爭對手），以顯示感謝訊息。 有關使用其他URL參數的詳細資訊，請參閱：如 [何將設定轉送至Facebook應用程式](#how-to-forward-settings-to-a-facebook-application-)。
* **[!UICONTROL Default branch]** :如果使用者已在上一日(應用程式參數與 **[!UICONTROL thanks]**)輸入競賽（ID已輸入），我們會顯示一個頁面，指出他們已輸入。

### 競爭頁面 {#competition-page}

若要迴避連結至Facebook的顯示錯誤，您也需要在競 **[!UICONTROL Parent window]** 賽頁 **[!UICONTROL In the top window]** 面 **[!UICONTROL Window]** 的欄位中選取或。

![](assets/social_webapp_028.png)

### 存取控制活動 {#access-control-activity}

當使 **[!UICONTROL Access control]** 用者進入競賽時，此活動可讓您顯示Facebook權限請求頁面。 如果他們同意分享其資訊，則會在預先載入時加以復原。 For more on this, refer to: [Pre-loading activity](#pre-loading-activity).

如果您先前在建立Web應用程式時輸入外部帳戶(請參閱「建立 [Facebook類型的Web應用程式](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)」)，則不需要編輯活動。 如果沒有，請前往欄位， **[!UICONTROL Application]** 並選取連結至Facebook應用程式的外部帳戶。

![](assets/social_webapp_024.png)

### 預載活動 {#pre-loading-activity}

選擇要用於預載入的資料源：

* **[!UICONTROL Marketing database]** :此選項可讓您透過Adobe Campaign資料庫預先載入資料。
* **[!UICONTROL Facebook]** :此選項可讓您使用Facebook預先載入資料。

![](assets/social_webapp_029.png)

**行銷資料庫**

此選項可讓您復原訪客表格中的描述檔資料。 驗證是根據使用者點按Facebook應用程式標籤時所復原的外部Facebook ID來執行。 如果在活動後添加表 **[!UICONTROL Pre-loading]** 單，則會預先載入資料庫中包含資訊的欄位。

![](assets/social_webapp_030.png)

>[!NOTE]
>
>如需透過Adobe Campaign資料庫預先載入資料的詳細資訊，請參 [閱本節](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)。

**Facebook**

此選項可讓您定義要收集的Facebook設定檔資訊，其中使用者同意分享，以便儲存。

![](assets/social_webapp_025.png)

選 **[!UICONTROL Database information]** 項可讓您收集下列資料：

* **[!UICONTROL External ID]**:使用者ID
* **[!UICONTROL Gender]**:使用者性別
* **[!UICONTROL Verified]** :此欄位會指定使用者是否擁有已驗證的Facebook帳戶。
* **[!UICONTROL Full name]**:用戶的全名
* **[!UICONTROL First name]**:使用者的名字
* **[!UICONTROL Last name]**:使用者姓氏
* **[!UICONTROL Language]**:使用者語言

您也可以選取適當的方塊，決定收集個人檔案像片、朋友名單、電子郵件地址、出生日期、興趣和地點。

按一下前 **[!UICONTROL Ok]**，請勾選方 **[!UICONTROL I agree to comply with Facebook conditions of use]** 塊。

>[!NOTE]
>
>如果您勾選區段中的一或多個方 **[!UICONTROL Private information]** 塊，Facebook權限要求畫面會自動顯示此資料的存取要求。
>
>若要收集選取的資訊，使用者必須同意分享。
>
>如果您想要兩種預先載入類型（透過Adobe Campaign和Facebook），會逐一新增兩個預先載入方塊。

### 儲存活動 {#save-activity}

此活 **[!UICONTROL Save]** 動可讓您將先前階段收集到的資訊儲存在訪客的表格中。

如果訪客的表格中已有描述檔，則會以收集到的新資料更新其資料。

如果資料庫中不存在描述檔，且已收集Facebook使用者的電子郵件地址，則訪客表格中會建立訪客。

![](assets/social_webapp_026.png)

1. 在欄位 **[!UICONTROL Visitor creation folder]** 中，選擇將在中建立配置檔案的資料夾。 如果是Facebook類型的Web應用程式，預設的建立資料夾為 **[!UICONTROL Visitors]**。
1. 在欄位 **[!UICONTROL Reconciliation mode]** 中，選擇要使用的協調模式：

   * **[!UICONTROL Automatic]** :對賬是根據電子郵件、姓氏、名字和出生日期進行的。
   * **[!UICONTROL Manual]** :請選擇一個或多個協調密鑰。
   * **[!UICONTROL None]** :不會進行和解。

1. 在字 **[!UICONTROL Mapping]** 段中，選擇要執行協調的方案。

   >[!CAUTION]
   >
   >請確定標籤的欄位 **[!UICONTROL Social networks]** 在傳送對應中已正確輸入。 傳送對應可透過節點 **[!UICONTROL Administration > Campaign management > Target mappings]** 存取。

1. 您可以選擇協調的搜索資料夾和新配置檔案的建立資料夾。 如果欄位為空，則在映射方案的預設資料夾中搜索並建立配置檔案。

### 結束活動 {#end-activity}

若要迴避連結至Facebook的顯示錯誤，您必須勾選方塊並輸 **[!UICONTROL Use an external URL]** 入Facebook應用程式的URL，後面接著參 **[!UICONTROL app_data]** 數和值。 此值將用於活動中， **[!UICONTROL Test]** 以偵測使用者是否剛進入競賽，並顯示感謝訊息（如果適用）。 For more on this, refer to: [Test activity](#test-activity).

在我們的範例中，所使用的值 **是感謝**。

![](assets/social_webapp_027.png)

### 訪客的詳細資料畫面 {#details-screen-of-a-visitor}

就像Twitter追隨者(請參閱：原 [則](../../social/using/publishing-on-twitter.md#operating-principle))，則已復原的Facebook設定檔會儲存在訪客的表格中。 若要顯示訪客清單，請前往節 **[!UICONTROL Profiles and Targets > Visitors]** 點。

同意分享其個人資料的每位Facebook潛在客戶都會新增至訪客清單。 如果此 **[!UICONTROL Friends]** 框已選中活動 **[!UICONTROL Pre-load]** (請參閱：預 [載活動](#pre-loading-activity))，也會新增朋友。

![](assets/social_webapp_037.png)

在訪客 **[!UICONTROL Summary]** 詳細資料視窗的區段中，指標有兩種可能的狀 **[!UICONTROL New Contact]** 態：

![](assets/social_webapp_038.png)

如果顯示綠色核取標籤，表示訪客未與任何收件者協調。 在這種情況下，會在收件者清單中建立新的描述檔。

![](assets/social_webapp_039.png)

紅叉表示訪客與收件者已協調。 您可以按一下欄位右側的放大鏡， **[!UICONTROL Recipient]** 以顯示相符的收件者。

![](assets/social_webapp_040.png)

前往收件者的詳細資料視窗，以顯示符合的訪客（如果適用）。 選取標 **[!UICONTROL Others]** 簽，然後按兩下區段中訪客的名 **[!UICONTROL Web identities]** 稱。

![](assets/social_webapp_041.png)

訪 **[!UICONTROL Activities]** 客詳細資料頁面的畫麵包含下列資訊：

* 「Open Graph」類型的粉絲活動：播放的音樂、觀看的視訊、閱讀文章及不詳的已安裝應用程式（Deezer、Spotify、Dailymotion、Yahoo News等）

   ![](assets/social_facebook_activities.png)

* 「按贊次數」和粉絲在Adobe Campaign傳送後新增的留言
* 粉絲喜歡的頁面
* 風扇的登記

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >為了讓Adobe Campaign收集粉絲的登入資訊，您必須按一下服務設 **[!UICONTROL Subscribe]** 定畫面上的按鈕。 有關詳細資訊，請參閱 [配置外部帳戶](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

## 如何使用Facebook設定檔資料預先載入表單的欄位 {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

應用 **[!UICONTROL Social Marketing]** 程式也可讓您新增按鈕至表單，以利用Facebook設定檔資訊預先載入欄位。 此選項可用於所有Web應用程式模板(類型活&#x200B;**[!UICONTROL Page]** 動)，在本節中有 [詳細說明](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)。

![](assets/social_webapp_035.png)

>[!NOTE]
>
>開始使用此函式之前，您必須建立Facebook應用程式和類型 **[!UICONTROL Facebook Connect]** 外部帳戶。 有關詳細資訊，請參閱 [配置外部帳戶](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。


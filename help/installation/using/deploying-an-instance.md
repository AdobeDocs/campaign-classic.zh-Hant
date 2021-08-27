---
product: campaign
title: 部署執行個體
description: 深入了解Campaign部署精靈
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 8b07447c-9a86-4b56-8d29-e0b01357a6ec
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '3048'
ht-degree: 1%

---

# 部署執行個體{#deploying-an-instance}

![](../../assets/v7-only.svg)

>[!NOTE]
>
>伺服器端設定只能由Adobe執行，以供Adobe托管的部署使用。 若要進一步了解不同部署，請參閱[托管模型](../../installation/using/hosting-models.md)區段或[此頁面](../../installation/using/capability-matrix.md)。

## 部署嚮導 {#deployment-wizard}

Adobe Campaign用戶端主控台中提供的圖形精靈可讓您定義要連線的執行個體的參數。

要啟動部署嚮導，請選擇&#x200B;**工具>高級>部署嚮導**。

![](assets/s_ncs_install_deployment_wiz_01.png)

配置步驟如下：

1. [一般參數](#general-parameters)
1. [電子郵件通道參數](#email-channel-parameters)
1. [管理退信的電子郵件](#managing-bounced-emails)
1. [追蹤設定](#tracking-configuration)
1. [行動通道參數](#mobile-channel-parameters)
1. [地區設定](#regional-settings)
1. [從Internet訪問](#access-from-the-internet)
1. [管理公共資源](#managing-public-resources)
1. [清除資料](#purging-data)

## 一般參數 {#general-parameters}

部署精靈的第一步可讓您輸入執行個體的一般資訊。

![](assets/s_ncs_install_deployment_wiz_02.png)

### 一般資訊 {#general-information}

窗口的下半部分允許您選擇要激活的選項。

* **[!UICONTROL Customer identifier used in billing]** :這可以是例項的名稱和版本號碼。
* **[!UICONTROL Common name of the customer]** :輸入公司名稱的字元字串。此資訊可用於取消訂閱連結。
* **[!UICONTROL Namespace]** :輸入小寫的簡短標識符。目的是在升級時區分您的特定配置和工廠配置。 客戶的預設命名空間為&#x200B;**cus** -。

### 技術選項 {#technical-options}

窗口的下半部分允許您選擇要激活的選項。

可以使用以下選項：

* **[!UICONTROL Email channel]** :啟用電子郵件傳送。請參閱[電子郵件通道參數](#email-channel-parameters)。
* **[!UICONTROL Tracking]** :啟用目標母體（開啟和點按）的追蹤。請參閱[追蹤組態](#tracking-configuration)。
* **[!UICONTROL Managing bounced emails]** :定義用於接收傳入電子郵件的POP帳戶。請參閱[管理退信電子郵件](#managing-bounced-emails)。
* **[!UICONTROL LDAP integration]** :通過LDAP目錄配置用戶身份驗證。請參閱[通過LDAP](../../installation/using/connecting-through-ldap.md)連接。

## 電子郵件通道參數 {#email-channel-parameters}

下列步驟可讓您定義要顯示在訊息標題中的資訊。

這些參數可能會在傳送範本中多載，且會針對每個傳送個別執行（如果使用者具有必要的權限）。

### 傳遞電子郵件的參數 {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

指定下列參數：

* **[!UICONTROL Sender name]** :發件人的姓名，
* **[!UICONTROL Sender address]** :發件人的地址，
* **[!UICONTROL Reply address text]** :該名稱可自定義，當收件者按一下其電子郵件客戶端軟 **[!UICONTROL Reply]** 體中的按鈕時，將使用。
* **[!UICONTROL Reply address]** :收件者按一下其電子郵件用戶端軟 **[!UICONTROL Reply]** 體中的按鈕時要使用的電子郵件地址，
* **[!UICONTROL Error address]** :錯誤訊息的電子郵件地址。這是用於處理退信的技術地址，包括Adobe Campaign伺服器因不存在的目標地址而收到的電子郵件。

除此之外，還可以指定為發件人地址和錯誤地址授權的&#x200B;**masks**。 如有必要，這些遮罩可以使用逗號加以區隔。 此設定為選用。 輸入欄位時，Adobe Campaign會在傳送時（分析期間，如果位址不包含任何變數）檢查位址是否有效。 此作業模式可確保未使用任何可能觸發傳送問題的地址。 傳遞地址必須在傳遞伺服器上配置。

### 地址中授權的字元 {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

在Adobe Campaign資料庫中，必須依下列方式建立所有電子郵件地址：`x@y.z`。 **x**、**y**&#x200B;和&#x200B;**z**&#x200B;字元不得空白，且不得包含未授權的字元。

您可以在此處在資料庫的電子郵件欄位中定義授權的字元（「資料原則」）。 清單中未包含的字元將被禁止，因此，當通過介面、Web表單以及導入資料在資料庫中輸入資訊時，將被拒絕。

有兩份清單可供使用：**僅限歐洲**&#x200B;或&#x200B;**僅限美國**。 如有需要，可新增其他字元。

### 傳送參數 {#delivery-parameters}

**高級參數……**&#x200B;連結可讓您存取傳送選項、連結至重試的參數和隔離。

![](assets/s_ncs_install_deployment_wiz_05.png)

此視窗可讓您為所有電子郵件促銷活動定義傳送和地址品質管理選項。

可以使用以下選項：

* **[!UICONTROL Delivery duration of messages]** :此後，傳送會停止（預設為5天）,
* **[!UICONTROL Online resources validity duration]** :保留收件者設定檔資訊以產生鏡像頁面的時間，
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** :選取此選項時，將不會聯絡封鎖清單上的收件者，
* **[!UICONTROL Automatically ignore doubles]** :選取此選項時，不會傳送至重複的位址。

### 重試參數 {#retry-parameters}

有關恢復的資訊在&#x200B;**恢復期**&#x200B;和&#x200B;**恢複數**&#x200B;欄位中提供：當收件者無法連線時（例如，如果收件匣已滿），依預設，程式會嘗試與他們連絡5次，每次嘗試之間間隔一小時（在最長傳送時間內）。 您可以變更這些值以符合您的需求。

### 隔離參數 {#quarantine-parameters}

隔離的設定選項如下：

* **[!UICONTROL Duration between two significant errors]** :預設情況下，輸入值(&quot;1d&quot;):1天)，定義應用程式在發生故障時增加錯誤計數器之前等待的時間，
* **[!UICONTROL Maximum number of errors before quarantine]** :達到此值後，會隔離電子郵件地址(依預設為「5」：第六個錯誤時將隔離該地址)。這表示該在後續傳送時將自動排除該聯絡人。

## 管理退信的電子郵件 {#managing-bounced-emails}

退回郵件對於確認傳送錯誤非常重要。 一旦規則確定其原因，就會在NP@I中分類這些錯誤。

只有在部署嚮導的第一階段中選擇了&#x200B;**電子郵件通道**&#x200B;和&#x200B;**退回郵件**&#x200B;管理選項時，此步驟才可用。 請參閱[一般參數](#general-parameters)。

此階段可讓您定義管理退信郵件的設定。

![](assets/s_ncs_install_deployment_wiz_06.png)

### 用於檢索傳入郵件的POP帳戶 {#pop-account-used-to-retrieve-incoming-mails}

指定要連接到用於檢索傳入電子郵件的帳戶的參數。

* **[!UICONTROL Label]** :名稱，包括下面提供的所有參數，
* **[!UICONTROL Server]** :用於檢索退回郵件（傳入郵件）的伺服器，
* **[!UICONTROL Security]** :如有必要， **[!UICONTROL SSL]** 請從下拉式清單中選取，
* **[!UICONTROL Port]** :伺服器埠（通常為110）,
* **[!UICONTROL Account]** :用於退信的帳戶名稱，
* **[!UICONTROL Password]** :與帳戶相關聯的密碼。

指定POP設定後，按一下&#x200B;**Test**&#x200B;以確保它們正確。

### 未處理的退回郵件 {#unprocessed-bounce-mails}

退信由Adobe Campaign自動處理，套用&#x200B;**管理>促銷活動管理>非交付項目管理>傳送記錄資格**&#x200B;節點中列出的規則。 有關詳細資訊，請參閱[退信管理](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management)。

未處理的退信不會顯示在Adobe Campaign介面中。 除非使用下列欄位將它們傳輸到第三方信箱，否則會自動刪除它們：

* **[!UICONTROL Forwarding address]** :填入此欄位，將Adobe Campaign平台收集的所有錯誤訊息（已處理或未處理）傳輸至協力廠商位址。
* **[!UICONTROL Address for errors]** :填入此欄位，只將inMail程式無法符合的錯誤訊息傳輸至第三方地址。
* **[!UICONTROL SMTP server]** :用於傳送未處理之退信電子郵件的伺服器。

>[!IMPORTANT]
>
>若要轉送未處理的退信電子郵件，Adobe建議僅填入&#x200B;**[!UICONTROL Address for errors]**&#x200B;欄位。 但是，請確保定期檢查所使用的地址，因為這可能會給郵件伺服器帶來大量負載。 如需詳細資訊，請連絡您的帳戶主管。

## 追蹤設定 {#tracking-configuration}

下一個步驟可讓您設定例項的追蹤。 例項必須向追蹤伺服器宣告及註冊。

只有在部署精靈的第一頁中選取&#x200B;**電子郵件通道**&#x200B;和&#x200B;**追蹤**&#x200B;選項時，才會提供此步驟。 請參閱[一般參數](#general-parameters)。

有關Web跟蹤（跟蹤模式、建立和插入標籤……）的詳細資訊，請參閱[本文檔](../../configuration/using/about-web-tracking.md)。

### 操作原則 {#operating-principle}

當您對例項啟用追蹤時，傳送期間的URL會變更，以啟用追蹤。

* 在部署精靈的這個頁面上輸入的外部URL（無論是否安全）相關資訊可用來建置新URL。 除了此資訊外，修改的連結還包含：傳送、收件者和URL的識別碼。

   追蹤資訊由Adobe Campaign在追蹤伺服器上收集，以豐富收件者設定檔及連結至傳送的資料（**[!UICONTROL Tracking]**&#x200B;標籤）。

   有關內部URL的資訊僅供Adobe Campaign應用程式伺服器用於聯絡追蹤伺服器。

   有關詳細資訊，請參閱[追蹤伺服器](#tracking-server)。

* 設定URL後，您需要啟用追蹤。 若要這麼做，必須在追蹤伺服器上註冊例項。

   如需詳細資訊，請參閱[儲存追蹤](#saving-tracking)。

### 追蹤伺服器 {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

為了保證在此例項上追蹤的效率，必須顯示下列資訊：
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** 和/或 **[!UICONTROL Secure external URL]** :輸入要在要發送的電子郵件中使用的重定向URL。
* **[!UICONTROL Internal URL(s)]** :僅由Adobe Campaign伺服器用來聯絡追蹤伺服器以收集記錄檔和上傳URL的URL。不需要將其與例項建立關聯。

   如果您未指定URL，預設會使用追蹤URL。

使用中間來源架構，您可以將追蹤管理外部化。 操作步驟：

1. 選取選項&#x200B;**[!UICONTROL Externalize tracking management]** :這可讓您使用中間來源伺服器作為追蹤伺服器。
1. 填入&#x200B;**[!UICONTROL External account]**&#x200B;和&#x200B;**[!UICONTROL Instance name]**&#x200B;欄位，以便能夠連接到中間來源伺服器。

   如需詳細資訊，請參閱[中間來源伺服器](../../installation/using/mid-sourcing-server.md)。

1. 按一下&#x200B;**[!UICONTROL Enable the tracking instance]**&#x200B;按鈕以核准與伺服器的連線。

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### 儲存追蹤 {#saving-tracking}

填入URL後，您必須註冊追蹤伺服器。

按一下追蹤伺服器上的連結&#x200B;**註冊**，然後選取可用選項之一。

![](assets/s_ncs_install_deployment_wiz_09.png)

實作追蹤有三種可能的架構類型：

1. **新增對現有例項中追蹤的支援**

   如果已根據其他需求（MTA伺服器等）建立例項，則此選項適用 用於追蹤伺服器的伺服器上。

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   輸入重定向伺服器上&#x200B;**內部**&#x200B;帳戶的密碼，以配置跟蹤實例。

   >[!NOTE]
   >
   >如果使用了多個追蹤伺服器，則它們必須使用相同的名稱和密碼。

   指定執行個體的名稱和密碼。

1. **建立專用於追蹤的新例項**

   在保留追蹤例項以供追蹤，且沒有任何其他應用程式模組時，此選項很實用。

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   輸入重定向伺服器上&#x200B;**內部**&#x200B;帳戶的密碼，以配置跟蹤實例。

   >[!NOTE]
   >
   >如果已設定多個追蹤伺服器，則必須使用相同的密碼。

   指定實例的名稱、密碼和任何相關的DNS掩碼，如&#x200B;**[!UICONTROL Campaign*]**。

1. **驗證已為您預先設定的追蹤例項**

   當您沒有&#x200B;**internal**&#x200B;帳戶的密碼時，會使用此選項；在此情況下，追蹤帳戶會在追蹤伺服器上預先設定給您。 輸入重定向伺服器的跟蹤帳戶的密碼以驗證跟蹤實例。

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   指定要驗證的例項名稱。

按一下&#x200B;**核准**&#x200B;以開始追蹤伺服器的記錄程式。

返回上一個視窗時，訊息會確認在追蹤伺服器層級進行註冊：

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

連結到URL搜索&#x200B;**的參數不得在標準安裝中修改**。 有關所有其他參數，請聯繫Adobe。

## 行動通道參數 {#mobile-channel-parameters}

下一個步驟可讓您定義傳送至行動裝置（SMS和WAP推播）的預設設定。

>[!NOTE]
>
>行動裝置頻道為選用：此階段只有在已購買時才會顯示。 請檢查您的授權合約。

![](assets/s_ncs_install_deployment_wiz_12.png)

### SMS傳送的預設帳戶 {#default-account-for-sms-delivery}

輸入以下資訊：

* **[!UICONTROL Label]** :輸入此SMS/Wap推播帳戶的名稱。例如，您可能希望使用路由器的名稱。
* 對於&#x200B;**[!UICONTROL Server]**、**[!UICONTROL Port]**、**[!UICONTROL Account]**、**[!UICONTROL Password]**、**[!UICONTROL Connector]**、**[!UICONTROL Send Endpoint]**、**[!UICONTROL Reception Endpoint]**、**[!UICONTROL Notification Endpoint]**&#x200B;欄位：如需所需設定，請連絡您的服務提供者。

### 傳送的簡訊參數 {#parameters-of-sms-sent}

在&#x200B;**優先順序**&#x200B;下拉式清單中：選取「一般」、「高」或「緊急」，將其套用至要傳送的訊息。

### 高級參數 {#advanced-parameters}

**高級參數……**&#x200B;連結可讓您存取重試和隔離選項。

![](assets/s_ncs_install_deployment_wiz_13.png)

**重試週期**&#x200B;和&#x200B;**重試次數**&#x200B;欄位中提供重試資訊：當行動裝置無法連線時，依預設，程式會以至少15分鐘的間隔（最長傳送期間）重試5次。 這些值可以調整以符合您的需求。

隔離的設定選項如下：

* **[!UICONTROL Time between two significant errors]** :輸入預設值(預設為「1d」：日)，定義應用程式在增加錯誤計數器以備發生錯誤之前等待的時間。
* **[!UICONTROL Maximum number of errors before quarantine]** :達到此值後，系統會隔離行動號碼(依預設為「5」：第六個錯誤時，將隔離該號碼)。這表示該連絡人將自動排除在未來傳送之外。

## 地區設定 {#regional-settings}

此階段允許您包含資料策略首選項。

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** :選中此選項時，應用程式將國際格式應用於電話號碼（國家/地區前置詞隨後是強制性的，因為在應用格式之前將不會檢查位數）。如果未選擇此選項，您必須在國際電話號碼前置詞「+」或「00」。
* **[!UICONTROL Store all phone numbers using the international format]** :此選項只涉及 **** 匯入或編輯的國內電話號碼。定義您是要使用國內格式（例如425 555 0150）還是國際格式(例如+1 425 555 0150)

## 從Internet訪問 {#access-from-the-internet}

>[!IMPORTANT]
>
>基於隱私權考量，我們建議對所有外部資源使用HTTPS。

此步驟可讓您定義網際網路上公開之Adobe Campaign頁面的存取URL。

您也必須在此處指定連結至網路表單的發佈選項。

![](assets/s_ncs_install_deployment_wiz_15.png)

### Web上公開的伺服器 {#servers-exposed-on-the-web}

使用此頁可將伺服器URL填充到：

1. 訪問Internet上公開的應用程式伺服器：訂閱/取消訂閱表單、外聯網等
1. 訪問應用程式伺服器，以查找Web上未公開的資源：表單、內部網、確認頁面。
1. 存取傳遞的鏡像頁面。

   鏡像頁面是顯示電子郵件內容的動態頁面。 它可透過插入傳送給收件者之訊息的連結來存取，且可包含個人化元素。 鏡像頁面使收件人能夠在網際網路瀏覽器中而不是電子郵件軟體中讀取郵件，而不考慮傳送格式（文本或HTML）。 不過，只有在已定義必要的HTML內容時，才會為指定傳送產生鏡像頁面。

Adobe Campaign可讓您區分這三個URL，以將負載分散到多個平台。

## 管理公共資源 {#managing-public-resources}

>[!IMPORTANT]
>
>基於隱私權考量，我們建議對所有外部資源使用HTTPS。

若要從外部查看，連結至促銷活動的電子郵件和公共資源中使用的影像必須存在於可外部存取的伺服器上。 然後，外部收件者或運算子就能使用這些ID。

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

在此步驟中，您需要輸入：

1. 新的公用資源URL。 如需詳細資訊，請參閱[公用資源URL](#public-resources-url)區段。
1. 傳送中的影像偵測模式。 如需詳細資訊，請參閱[傳送影像偵測](#delivery-image-detection)區段。
1. 發佈選項。 如需詳細資訊，請參閱[發佈模式](#publication-modes)區段。

可通過Adobe Campaign樹的&#x200B;**Administration > Resources > Online > Public resources**&#x200B;節點訪問公共資源。 它們會收集在資料庫中，並可包含在電子郵件中，但也可用於行銷活動或工作，以及內容管理中。

![](assets/install_pub_resources_view.png)

### 公用資源URL {#public-resources-url}

第一個欄位可讓您指定上傳後，用於資源的URL的開頭。 上傳後，即可透過這個新URL存取資源。

在傳遞中，您可以使用儲存在公共資源庫中的影像，或儲存在伺服器上的任何其他本地影像或影像。

* 對於電子郵件影像，**https://** server **/res/img** URL。

   可以針對每個傳送覆寫此值。

* 對於公共資源，URL **https://** server **/res/** instance ****，其中&#x200B;**instance**為追蹤例項的名稱。

### 傳送影像偵測 {#delivery-image-detection}

在傳遞中，您可以使用儲存在公共資源庫中的影像，或儲存在伺服器上的任何其他本地影像或影像。

欄位&#x200B;**URL遮罩**&#x200B;可讓您指定自動上傳影像時要略過的URL遮罩清單。 例如，如果您使用儲存在可從外部存取的網站（尤其是網際網路網站）上的影像，則可以在此欄位中輸入網站URL。

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

您可以使用逗號來分隔多個URL遮罩，

* 有關在電子郵件中使用和管理影像的資訊，請參閱[此部分](../../delivery/using/defining-the-email-content.md#adding-images)。
* 在傳送精靈中，從這些URL呼叫的影像將狀態為「已忽略」。

### 發佈模式 {#publication-modes}

嚮導的下半部分允許您選擇公共資源和影像的發佈選項。

可使用下列發佈模式：

* 追蹤伺服器

   資源會自動複製到不同的追蹤伺服器。 這些設定在步驟[追蹤設定](#tracking-configuration)中設定。

* 其他Adobe Campaign伺服器

   您可以使用其他一個Adobe Campaign伺服器來複製資源。

   在伺服器端，若要使用專用的Adobe Campaign伺服器，您必須使用下列命令建立新執行個體：

   ```
   nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
   ```

   然後輸入密碼。

   專用伺服器的參數在&#x200B;**[!UICONTROL Media URL(s)]**、**[!UICONTROL Password]**&#x200B;和&#x200B;**[!UICONTROL Instance name]**&#x200B;欄位中給出。

   ![](assets/s_ncs_install_images_upload_b.png)

* 手動發佈指令碼（僅用於公共資源）

   ![](assets/s_ncs_install_images_upload_c.png)

   您可以使用指令碼發佈影像：

   * 您必須建立此指令碼：其內容取決於您的設定。
   * 指令碼將由以下命令調用：

      ```
      [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
      ```

      其中`[INSTALL]`是Adobe Campaign安裝資料夾的存取路徑。

   * 在Unix中，確保指令碼可執行。

對於影像，它必須從通過&#x200B;**NmsDelivery_ImageSubDirectory**&#x200B;選項指定的「images」資料夾複製到一個或多個前端伺服器。 這些伺服器會儲存影像，以便透過新設定的URL存取。

如果在Adobe Campaign伺服器上發佈，而沒有手動發佈指令碼，預設情況下，傳送的影像會儲存在`$(XTK_INSTALL_DIR)/var/res/img/ directory`中。 對應的URL如下：**`https://server/res/img`**。

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`.對應的URL如下：**`https://server/res/instance`**&#x200B;其中instance是追蹤例項的名稱。

>[!NOTE]
>
>可以更改公共資源儲存目錄。 有關詳細資訊，請參閱[管理公用資源](#managing-public-resources)。

### 同步公共資源 {#synchronizing-public-resources}

此功能允許您在多個備用伺服器上同步公共資源&#x200B;**。**

如果追蹤伺服器上沒有公用資源，或如果資源傳回404錯誤，追蹤伺服器會嘗試在其中一個備用伺服器上尋找資源。

必須在行銷伺服器的&#x200B;**serverConf.xml**&#x200B;檔案中聲明和配置備用伺服器。 **serverConf.xml**&#x200B;中所有可用的參數都列在此[節](../../installation/using/the-server-configuration-file.md)中。

**聲明**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**配置**

對於必須同步的每個公共資源，必須向`<relay>`部分的`<url>`元素添加狀態屬性：

狀態屬性可以是以下三個值之一：

* 備用：公用資源已同步

* 正常：現有行為（無同步）

* 黑名單：如果URL傳回404錯誤，則會新增至封鎖清單。 封鎖清單中URL的持續時間（以秒為單位）由預設值為60s的&#x200B;**timeout**&#x200B;屬性定義。

同步的現成配置為：

```
(extracted from the serverConf.xml file)

<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="false" trackingPassword="">
<spareServer enabledIf="" id="1" url=""/>
</redirection>

....


<relay debugRelay="false" forbiddenCharsInAuthority="?#.@/:" forbiddenCharsInPath="?#/"
           modDir="index.html" startRelay="false" startRelayInModule="true" timeout="60">
   <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/view/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jsp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jssp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/webApp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/report/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/jssp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/strings/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/interaction/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/barcode/*"/>

      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/favicon.*"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.html"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.png"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.jpg"/>

 </relay>
```

## 清除資料 {#purging-data}

部署精靈的最後一個階段可讓您設定自動清除過時資料。 值以天表示。

![](assets/s_ncs_install_deployment_wiz_16.png)

資料會透過資料庫清理工作流程自動刪除。 有關如何配置和操作此工作流以及已刪除項目的詳細資訊，請參閱此[document](../../production/using/database-cleanup-workflow.md)。

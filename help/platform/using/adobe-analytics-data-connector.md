---
title: Adobe Analytics資料連接器
seo-title: Adobe Analytics資料連接器
description: Adobe Analytics資料連接器
seo-description: null
page-status-flag: never-activated
uuid: 5a1de443-04de-49a8-9057-5d8381e48630
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: 5ff1577f-0809-46fd-ac1e-11b24637e35c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20174427735b90129cd4cbd9ee1ba5fd705fa302

---


# Adobe Analytics資料連接器{#adobe-analytics-data-connector}

## 關於資料連接器整合 {#about-data-connector-integration}

>[!CAUTION]
>
>Adobe Analytics Data Connector與交易式訊息（訊息中心）不相容。

資料連接器（先前稱為Adobe Genesis）可讓Adobe Campaign和Adobe Analytics透過 **Web Analytics連接器套件互動** 。 它會以區段形式將資料轉送至Adobe Campaign，內容與電子郵件促銷活動後的使用者行為有關。 相反地，它會將Adobe Campaign傳送的電子郵件促銷活動指標和屬性傳送至Adobe Analytics —— 資料連接器。

Adobe Campaign使用「資料」連接器，可以測量網際網路觀眾(Web Analytics)。 有了這些整合，Adobe Campaign可以恢復行銷活動後一或多個網站的訪客行為資料，並（分析後）執行再行銷活動，以便將其轉換為購買者。 相反地，網頁分析工具可讓Adobe Campaign將指標和促銷活動屬性轉送至其平台。

如需Adobe Analytics與Adobe Campaign整合的詳細資訊，請參閱本文 [件](https://helpx.adobe.com/marketing-cloud/how-to/analytics-ac.html)。

每個工具的操作欄位如下：

* 網頁分析的角色：

   1. 標示使用Adobe Campaign啟動的電子郵件促銷活動，
   1. 以區段的形式儲存收件者在點按促銷活動電子郵件後所瀏覽之網站上的行為。 區段涉及放棄的產品（已檢視但未新增至購物車或已購買）、購買或購物車放棄。

* Adobe Campaign的角色：

   1. 將指標和促銷活動屬性傳送至連接器，接著再將它們轉送至網頁分析工具，
   1. 恢復和分析細分，
   1. 觸發重新行銷促銷活動。

## 設定整合 {#setting-up-the-integration}

若要設定「資料」連接器，您必須連線至您的Adobe Campaign例項並執行下列作業：

* [步驟1:在Analytics中設定整合](#step-1--configure-integration-in-analytics)
* [步驟2:在Campaign中建立外部帳戶](#step-2--create-the-external-account-in-campaign)
* [步驟3:同步化Adobe Campaign和Adobe Analytics](#step-3--synchronize-adobe-campaign-and-adobe-analytics)

### 步驟1:在Analytics中設定整合 {#step-1--configure-integration-in-analytics}

以下步驟詳細說明使用嚮導的資料連接器的配置。

1. 使用Adobe ID或Enterprise ID登入Adobe Experience Cloud。

   ![](assets/adobe_genesis_install_001.png)

1. 從Experience cloud解決方案清單中，選取 **[!UICONTROL Analytics]**。

   ![](assets/adobe_genesis_install_013.png)

1. 從頁籤 **[!UICONTROL Admin]** 中，選擇 **[!UICONTROL Data Connectors]**。

   ![](assets/adobe_genesis_install_002.png)

1. 從合作夥伴清單中，選擇 **[!UICONTROL Neolane - Enterprise Marketing Platform]**。

   ![](assets/adobe_genesis_install_014.png)

1. 在對話方 **[!UICONTROL Add integration]** 塊中，按一下 **[!UICONTROL Activate]**。
1. 選 **[!UICONTROL I accept these terms and conditions]** 中並選擇鏈 **[!UICONTROL Report suite]** 接到此整合併輸入連接器標籤。

   完成後，按一下 **[!UICONTROL Create and configure this integration]**。

   ![](assets/adobe_genesis_install_015.png)

1. 輸入代表連接器接收通知的電子郵件地址，然後複製外部 **[!UICONTROL Account ID]** Adobe Campaign帳戶中顯示的通知(如需詳細資訊，請參閱 [步驟2:在促銷活動中建立外部帳戶](#step-2--create-the-external-account-in-campaign))。

   ![](assets/adobe_genesis_install_005.png)

1. 指定測量電子郵件促銷活動影響所需的識別碼，例如內部促銷活動名稱(cid)和iNmsBroadlog（競標）表格ID。 您也應指定要收集之事件的指標。

   ![](assets/adobe_genesis_install_006.png)

1. 如有必要，請指定個人化區段。

   ![](assets/adobe_genesis_install_007.png)

1. 在中 **[!UICONTROL Data collection]**，選擇恢復資料的方法，在此例中，選擇步驟6中 **[!UICONTROL cid]** 指定 **[!UICONTROL bid]** 的和標識符。

   ![](assets/adobe_genesis_install_009.png)

1. 選取要顯示在控制面板中的資訊。

   ![](assets/adobe_genesis_install_0112.png)

1. 在總結前述步驟的頁面中檢查配置。

   ![](assets/adobe_genesis_install_011.png)

1. 按一下 **[!UICONTROL Activate Now]** 批准配置並激活連接器。

   ![](assets/adobe_genesis_install_012.png)

   「資料」連接器現在已設定。

### 步驟2:在Campaign中建立外部帳戶 {#step-2--create-the-external-account-in-campaign}

將Adobe Campaign整合至Analytics平台時，會使用連接器。 若要同步應用程式，請套用下列程式：

1. 在Adobe Campaign中 **安裝Web Analytics** connectors套件。
1. 前往Adobe **[!UICONTROL Administration > Platform > External accounts]** Campaign樹狀結構的資料夾。
1. 以滑鼠右鍵按一下外部帳戶清單，然 **[!UICONTROL New]** 後在下拉式選單中選取(或按一下外部帳戶 **[!UICONTROL New]** 清單上方的按鈕)。
1. 使用下拉式清單來選取類 **[!UICONTROL Web Analytics]** 型。
1. 選擇連接器的提供器，即 **[!UICONTROL Adobe Analytics - Data Connector]** 在本例中。

   ![](assets/webanalytics_ext_account_create_001.png)

1. 按一 **[!UICONTROL Enrich the formula...]** 下連結以變更URL計算公式，以指定網站分析工具整合資訊（促銷活動ID）和必須追蹤其活動之網站的網域。
1. 指定網站的網域名稱。

   ![](assets/webanalytics_tracking_001.png)

1. 單 **[!UICONTROL Next]** 擊並確保域名已保存。

   ![](assets/webanalytics_tracking_002.png)

1. 如有必要，您必須使計算公式超載。 要執行此操作，請選中該框並直接在窗口中編輯公式。

   ![](assets/webanalytics_tracking_003.png)

   >[!CAUTION]
   >
   >此配置模式保留給專家用戶：此公式中的任何錯誤都可能導致電子郵件傳送停止。

1. 此標 **[!UICONTROL Advanced]** 簽可讓您設定或修改更多技術設定。

   * **[!UICONTROL Lifespan]**:可讓您指定延遲（以天數_為單位），之後Adobe Campaign中的網頁事件會依技術工作流程進行復原。 預設值：180天。
   * **[!UICONTROL Persistence]**:可讓您將所有Web事件（例如購買）歸因於重新行銷促銷活動的期間，預設值：7天。

>[!NOTE]
>
>如果您使用數種對象測量工具，則可在建 **[!UICONTROL Other]** 立外部 **[!UICONTROL Partners]** 帳戶時，在下拉式清單中選取。 您只能在傳送屬性中參考一個外部帳戶：因此，您必須新增Adobe和所有其他測量工具所預期的參數，以調整追蹤URL的公式。

### 步驟3:同步化Adobe Campaign和Adobe Analytics {#step-3--synchronize-adobe-campaign-and-adobe-analytics}

建立外部帳戶後，您需要同步兩個應用程式。

1. 前往您先前建立的外部帳戶。
1. 視需要變 **[!UICONTROL Label]** 更帳戶。
1. 變更 **[!UICONTROL Internal name]** ，使其符合設定「資料 **[!UICONTROL Name]** 連接器」時選擇的項目。

   ![](assets/webanalytics_ext_account_setting_001.png)

1. 按一下 **[!UICONTROL Approve connection]** 連結。

   ![](assets/webanalytics_ext_account_setting_002.png)

   請確定符合 **[!UICONTROL Internal name]** 「資料連 **[!UICONTROL Name]** 接器設定」精靈中指定的項目。

1. 在「資料 **[!UICONTROL Account ID]** 連接器配置」嚮導中輸入。

   ![](assets/webanalytics_ext_account_setting_003.png)

1. 依照「資料連接器」精靈指南的步驟進行，然後返回Adobe Campaign中的外部帳戶。
1. 按一 **[!UICONTROL Next]** 下，以便在Adobe Campaign和Adobe Analytics —— 資料連接器之間進行資料交換。

   同步完成後，將顯示段清單。

   ![](assets/webanalytics_ext_account_setting_004.png)

當Adobe Campaign和Adobe Analytics —— 資料連接器之間的資料同步生效時，Adobe Campaign會復原「資料連接器」精靈中定義的三個預設區段，並可在Adobe Campaign外部帳戶的標籤中存取。 **[!UICONTROL Segments]**

![](assets/webanalytics_segments.png)

如果在「資料連接器」精靈中設定了其他區段，您可以將它們新增至Adobe Campaign。 若要這麼做，請按一下 **[!UICONTROL Update segment list]** 連結，並遵循外部帳戶精靈中概述的步驟。 執行操作後，新區段就會顯示在清單中。

![](assets/webanalytics_segments_update.png)

### 網頁分析程式的技術工作流程 {#technical-workflows-of-web-analytics-processes}

Adobe Campaign與Adobe Analytics —— 資料連接器之間的資料交換是由四個技術工作流程所處理，這些工作流程會以後台工作的方式執行。

這些功能可在Adobe Campaign樹狀結構的資料夾下 **[!UICONTROL Administration > Production > Technical workflows > Web analytics process]** 使用。

![](assets/webanalytics_workflows.png)

* **[!UICONTROL Recovering of web events]**:每小時一次，此工作流程會下載有關特定網站使用者行為的區段，並將其納入Adobe Campaign資料庫，然後啟動重新行銷工作流程。
* **[!UICONTROL Event purge]**:此工作流允許您根據欄位中配置的期間，從資料庫中刪除所有事 **[!UICONTROL Lifespan]** 件。 如需詳細資訊，請參閱 [步驟2:在Campaign中建立外部帳戶](#step-2--create-the-external-account-in-campaign)。
* **[!UICONTROL Identification of converted contacts]**:重新行銷促銷活動後進行購買的訪客的目錄。 此工作流程收集的資料可在報表中存 **[!UICONTROL Re-marketing efficiency]** 取，請參閱此 [頁](#creating-a-re-marketing-campaign)。* **[!UICONTROL Sending of indicators and campaign attributes]**:可讓您使用Adobe Analytics —— 資料連接器，透過Adobe Campaign將電子郵件宣傳指標傳送至Adobe Experience Cloud。 此工作流程每天凌晨4點觸發，資料傳送至Analytics可能需要24小時。

   請注意，此工作流程不應重新啟動，否則將重新傳送所有可能扭曲Analytics結果的先前資料。

   相關指標包括：

   * **[!UICONTROL Messages to deliver]** (@toDeliver)
   * **[!UICONTROL Processed]** (@processed)
   * **[!UICONTROL Success]** (@success)
   * **[!UICONTROL Total count of opens]** (@totalRecipientOpen)
   * **[!UICONTROL Recipients who have opened]** (@recipientOpen)
   * **[!UICONTROL Total number of recipients who clicked]** (@totalRecipientClick)
   * **[!UICONTROL People who clicked]** (@personClick)
   * **[!UICONTROL Number of distinct clicks]** (@recipientClick)
   * **[!UICONTROL Opt-Out]** (@optOut)
   * **[!UICONTROL Errors]** (@error)
   >[!NOTE]
   >
   >傳送的資料是根據最後一個快照的增量，可能會導致量度資料中的負值。

   發送的屬性如下：

   * **[!UICONTROL Internal name]** (@internalName)
   * **[!UICONTROL Label]** (@label)
   * **[!UICONTROL Label]** (operation/@label):只有在安 **裝Campaign** 套件時
   * **[!UICONTROL Nature]** (operation/@nature):只有在安 **裝Campaign** 套件時
   * **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
   * **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
   * **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
   * **[!UICONTROL Contact date]** (scheduling/@contactDate)


* **已轉換聯繫人的標識**:重新行銷促銷活動後進行購買的訪客的目錄。 此工作流程收集的資料可在報表中 **[!UICONTROL Re-marketing efficiency]** 存取(請參 [閱](../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign))。

## 追蹤Adobe Campaign中的傳送 {#tracking-deliveries-in-adobe-campaign}

為了讓Adobe Experience cloud能夠在Adobe Campaign傳送後追蹤網站上的活動，您必須在傳送屬性中參考相符的連接器。 若要這麼做，請套用下列步驟：

1. 開啟要追蹤之促銷活動的傳送。

   ![](assets/webanalytics_delivery_properties_003.png)

1. 開啟傳送屬性。
1. 前往標籤 **[!UICONTROL Web Analytics]** 並選取先前建立的外部帳戶。 請參閱 [步驟2:在促銷活動中建立外部帳戶](#step-2--create-the-external-account-in-campaign))。

   ![](assets/webanalytics_delivery_properties_002.png)

1. 您現在可以在Adobe Analytics中傳送並存取報表。

## 建立再行銷促銷活動 {#creating-a-re-marketing-campaign}

若要準備再行銷促銷活動，只需建立要用於再行銷類型促銷活動的傳送範本。 然後設定您的再行銷促銷活動，並將其連結至區段。 每個區段必須有不同的再行銷促銷活動。

一旦Adobe Campaign完成對分析初始促銷活動所定位人員行為的區段的復原，重新行銷促銷活動就會自動啟動。 如果購物車放棄或檢視產品而未購買，則會傳送遞送給相關收件者，讓其網站瀏覽結束購買。

Adobe Campaign提供個人化的傳送範本，您可使用這些範本或將其建立資料庫，以準備宣傳活動。

1. 從中 **[!UICONTROL Explorer]**，移至Adobe Campaign **[!UICONTROL Resources > Templates > Delivery templates]** 樹狀結構的資料夾。
1. 複製Adobe **[!UICONTROL Email delivery (re-marketing)]** Campaign提供的範本或再行銷範本範例。
1. 個人化範本以符合您的需求並加以儲存。

   ![](assets/webanalytics_delivery_model.png)

1. 建立新促銷活動，並從下 **[!UICONTROL Re-marketing campaign]** 拉式清單中選取範本。

   ![](assets/webanalytics_remarketing_campaign_002.png)

1. 按一下 **[!UICONTROL Configure...]** 連結，指定連結至促銷活動的區段和傳送範本。
1. 選擇先前配置的外部帳戶。

   ![](assets/webanalytics_remarketing_campaign_003.png)

1. 選取相關區段。

   ![](assets/webanalytics_remarketing_campaign_005.png)

1. 選取要用於此重新行銷促銷活動的傳送範本，然後按一下 **[!UICONTROL Finish]** 以關閉視窗。

   ![](assets/webanalytics_remarketing_campaign_006.png)

1. 按一 **[!UICONTROL OK]** 下以關閉促銷活動視窗。

報表 **[!UICONTROL Re-marketing efficiency]** 可透過全域報表頁面存取。 它可讓您檢視與Adobe Campaign再行銷促銷活動後放棄的購物車數量相關的轉換聯絡人數（亦即已購買商品）。 轉換率是每週、每月或自Adobe Campaign與網頁分析工具開始同步起計算。

![](assets/webanalytics_reporting.png)


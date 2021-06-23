---
solution: Campaign Classic
product: campaign
title: Adobe Analytics連接器
description: 深入了解Adobe Analytics connector
feature: 概覽
role: Business Practitioner, Administrator
level: Beginner
exl-id: 5bd12f65-f468-41ab-bbae-e59a6592a803
source-git-commit: c612b47463427751eff27d6092e371c918c87d93
workflow-type: tm+mt
source-wordcount: '1551'
ht-degree: 0%

---

# Adobe Analytics Connector{#adobe-analytics-connector}

## 關於Adobe Analytics Connector整合 {#about-analytics-connector-integration}

Adobe Analytics連接器可讓Adobe Campaign和Adobe Analytics透過&#x200B;**[!UICONTROL Web Analytics connectors]**&#x200B;封裝互動。 它會以關於電子郵件促銷活動後使用者行為的區段形式，將資料轉送至Adobe Campaign。 相反地，它會將Adobe Campaign所傳送電子郵件促銷活動的指標和屬性傳送至Adobe Analytics。

>[!CAUTION]
>
>* Adobe Analytics Connector與交易式訊息（訊息中心）不相容。
   >
   >
* 開始之前，請確定已在Campaign中實作AdobeIdentity Management系統(IMS)。 [在本頁面](../../integrations/using/about-adobe-id.md)深入瞭解。


Adobe Campaign使用Adobe Analytics Connector可測量網際網路受眾(Web Analytics)。 有了這些整合，Adobe Campaign便能復原行銷活動後一或多個網站的訪客行為資料，並（分析後）執行再行銷活動，以便將其轉換為購買者。 反之，Adobe Campaign的網頁分析工具可將指標和行銷活動屬性轉送至其平台。

每個工具的動作欄位如下：

* 網站分析的角色：

   1. 會標籤透過Adobe Campaign啟動的電子郵件行銷活動，
   1. 以區段的形式，儲存收件者在按一下促銷活動電子郵件後所瀏覽的網站上的行為。 區段與放棄的產品（已檢視但未新增至購物車或已購買）、購買或購物車放棄有關。

* Adobe Campaign的角色：

   1. 會將指標和促銷活動屬性傳送至連接器，連接器再將它們轉送至網頁分析工具，
   1. 恢復和分析區段，
   1. 觸發再行銷活動。

## 設定整合 {#setting-up-the-integration}

若要設定Data connector，您必須連線至Adobe Campaign執行個體並執行下列操作：

1. [在Adobe Analytics中建立報表套裝](#report-suite-analytics)
1. [設定轉換變數和成功事件](#configure-conversion-success)
1. [在Adobe Campaign Classic中設定您的外部帳戶](#external-account-classic)

### 在Adobe Analytics中建立報表套裝 {#report-suite-analytics}

若要設定Adobe Analytics/Adobe Campaign Classic整合，您必須連線至您的[!DNL Adobe Analytics]執行個體並執行下列操作：

1. 從[!DNL Adobe Analytics]中，選擇&#x200B;**[!UICONTROL Admin tab]**，然後按一下&#x200B;**[!UICONTROL All admin]**。

   ![](assets/analytics_connnector_1.png)

1. 按一下 **[!UICONTROL Report suites]**。

   ![](assets/analytics_connnector_2.png)

1. 從&#x200B;**[!UICONTROL Report suite manager]**&#x200B;頁面，按一下&#x200B;**[!UICONTROL Create new]**，然後按一下&#x200B;**[!UICONTROL Report suite]**。

   有關建立&#x200B;**[!UICONTROL Report suite]**&#x200B;的詳細過程，請參閱此[節](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=en#prerequisites)。

   ![](assets/analytics_connnector_3.png)

1. 選取範本。

1. 使用下列資訊設定您的新報表套裝：

   * **[!UICONTROL Report Suite ID]**
   * **[!UICONTROL Site Title]**
   * **[!UICONTROL Time Zone]**
   * **[!UICONTROL Go Live Date]**
   * **[!UICONTROL Estimated Page Views Per Day]**

   ![](assets/analytics_connnector_4.png)

1. 配置後，按一下&#x200B;**[!UICONTROL Create report suite]**。

### 設定轉換變數和成功事件 {#configure-conversion-success}

建立&#x200B;**[!UICONTROL Report suite]**&#x200B;後，您需要依照以下方式配置&#x200B;**[!UICONTROL Conversion variables]**&#x200B;和&#x200B;**[!UICONTROL Success events]**:

1. 選取您先前設定的&#x200B;**[!UICONTROL Report suite]**。

1. 從&#x200B;**[!UICONTROL Edit settings]**&#x200B;按鈕中，選擇&#x200B;**[!UICONTROL Conversion]** > **[!UICONTROL Conversion variables]**。

   ![](assets/analytics_connnector_5.png)

1. 按一下&#x200B;**[!UICONTROL Add new]**&#x200B;以建立測量電子郵件促銷活動影響所需的識別碼，即內部促銷活動名稱(cid)和iNmsBroadlog（競標）表格ID。

   若要了解如何編輯&#x200B;**[!UICONTROL Conversion variables]**，請參閱此[小節](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/conversion-variables/t-conversion-variables-admin.html?lang=en#admin-tools)。

   ![](assets/analytics_connnector_6.png)

1. 完成後，按一下&#x200B;**[!UICONTROL Save]**。

1. 然後，要建立&#x200B;**[!UICONTROL Success events]**，請從&#x200B;**[!UICONTROL Edit settings]**&#x200B;按鈕中選擇&#x200B;**[!UICONTROL Conversion]** > **[!UICONTROL Success events]**。

   ![](assets/analytics_connnector_7.png)

1. 按一下&#x200B;**[!UICONTROL Add new]**&#x200B;以配置以下&#x200B;**[!UICONTROL Success events]**:

   * **[!UICONTROL Clicked]**
   * **[!UICONTROL Opened]**
   * **[!UICONTROL Person clicks]**
   * **[!UICONTROL Processed]**
   * **[!UICONTROL Scheduled]**
   * **[!UICONTROL Sent]**
   * **[!UICONTROL Total bounces]**
   * **[!UICONTROL Unique Clicks]**
   * **[!UICONTROL Unique Opens]**
   * **[!UICONTROL Unsubscribed]**

   若要了解如何配置&#x200B;**[!UICONTROL Success events]**，請參閱此[節](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/success-events/t-success-events.html?lang=en#admin-tools)

   ![](assets/analytics_connnector_8.png)

1. 完成後，按一下&#x200B;**[!UICONTROL Save]**。

設定報表套裝後，您需要在Adobe Campaign Classic中設定&#x200B;**[!UICONTROL External accounts]**。

### 在Adobe Campaign Classic中設定您的外部帳戶 {#external-account-classic}

>[!IMPORTANT]
>
> 為了讓此整合發揮作用，您需要在Adobe Campaign中安裝&#x200B;**[!UICONTROL Web Analytics connectors]**&#x200B;套件。
>
>有關軟體包安裝的詳細資訊，請參閱此[page](../../installation/using/installing-campaign-standard-packages.md)。

您現在需要在Adobe Campaign中設定&#x200B;**[!UICONTROL Web Analytics]**&#x200B;外部帳戶，以啟用兩個解決方案之間的同步。

請注意，如果在設定外部帳戶時未顯示&#x200B;**[!UICONTROL Report suite]**、**[!UICONTROL Conversion variables]**&#x200B;或&#x200B;**[!UICONTROL Success events]**&#x200B;之一，這表示您在與使用者相關聯的&#x200B;**[!UICONTROL Product profile]**&#x200B;中缺少此新建立元件的權限。

如需詳細資訊，請參閱[Adobe Analytics的產品設定檔](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/permissions/product-profile.html?lang=en#product-profile-admins)頁面。

1. 前往Adobe Campaign樹的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]**&#x200B;資料夾，然後按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/analytics_connnector_9.png)

1. 使用下拉式清單，從&#x200B;**[!UICONTROL Integration]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Web Analytics]**&#x200B;類型和&#x200B;**[!UICONTROL Adobe Analytics]**。

   ![](assets/analytics_connnector_10.png)

1. 按一下&#x200B;**[!UICONTROL Integration]**&#x200B;下拉式清單旁的&#x200B;**[!UICONTROL Configure]** 。

1. 從&#x200B;**[!UICONTROL Configure Analytics integration]**&#x200B;視窗，將外部帳戶與先前建立的報表套裝對應，並提供下列資訊：

   * **[!UICONTROL E-Mail]**
   * **[!UICONTROL IMS Org]**
   * **[!UICONTROL Analytics Company]**
   * **[!UICONTROL Report Suite]**

1. 從&#x200B;**[!UICONTROL eVars]**&#x200B;類別中，映射在[!DNL Adobe Analytics]中配置的兩個&#x200B;**[!UICONTROL Conversion variables]**。

   ![](assets/analytics_connnector_11.png)

1. 從&#x200B;**[!UICONTROL Events]**&#x200B;類別中，映射[!DNL Adobe Analytics]中配置的10個&#x200B;**[!UICONTROL Success events]**。

1. 完成後，按一下&#x200B;**[!UICONTROL Submit]**。 Adobe Campaign會在對應的Analytics **[!UICONTROL Report Suite]**&#x200B;中建立&#x200B;**[!UICONTROL Data source]**、**[!UICONTROL Calculated metrics]**、**[!UICONTROL Remarketing segments]**&#x200B;和&#x200B;**[!UICONTROL Classifications]**。

   在[!DNL Adobe Analytics]和Adobe Campaign之間同步完成後，您可以關閉視窗。

1. 您可以從&#x200B;**[!UICONTROL Configure Analytics integration]**&#x200B;視窗的&#x200B;**[!UICONTROL Data Settings]**&#x200B;標籤檢視設定。

   使用&#x200B;**[!UICONTROL Sync]**&#x200B;按鈕， [!DNL Adobe Campaign]將同步在[!DNL Adobe Analytics]中完成的名稱更改。 如果在[!DNL Adobe Analytics]中刪除元件，則該元件將在[!DNL Adobe Campaign]中被刪除，或顯示為&#x200B;**未找到**&#x200B;消息。

   ![](assets/analytics_connnector_12.png)

1. 如有需要，您可以從&#x200B;**[!UICONTROL Update Segments]**&#x200B;索引標籤新增或移除區段。

1. 在&#x200B;**[!UICONTROL External account]**&#x200B;中，按一下&#x200B;**[!UICONTROL Enrich the formula...]**&#x200B;連結以變更URL計算公式，以指定網站分析工具整合資訊（促銷活動ID）和必須追蹤其活動的網站網域。

   ![](assets/analytics_connnector_13.png)

1. 指定網站的網域名稱。

   ![](assets/analytics_connnector_14.png)

1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;並確保已保存域名。

   ![](assets/analytics_connnector_15.png)

1. 如有必要，您可以超載計算公式。 要執行此操作，請核取方塊並直接在視窗中編輯公式。

   >[!IMPORTANT]
   >
   >此配置模式為專家用戶保留：此公式中的任何錯誤都可能導致電子郵件傳送停止。

1. **[!UICONTROL Advanced]**&#x200B;標籤可讓您設定或修改更多技術設定。

   * **[!UICONTROL Lifespan]**:可讓您指定延遲（以天為單位），之後技術工作流程便可在Adobe Campaign中復原Web事件。預設值：180天。
   * **[!UICONTROL Persistence]**:可讓您將所有Web事件（例如購買）歸因於再行銷促銷活動的期間，預設值：7天。

>[!NOTE]
>
>如果您使用數個對象測量工具，可在建立外部帳戶時，於&#x200B;**[!UICONTROL Partners]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Other]**。 您只能在傳送屬性中參考一個外部帳戶：因此，您需要借由新增Adobe預期的參數以及所有其他測量工具來調整追蹤URL的公式。

### 網頁分析程式的技術工作流程 {#technical-workflows-of-web-analytics-processes}

Adobe Campaign和Adobe Analytics之間的資料交換由四個技術工作流程處理，以作為背景工作執行。

它們可在Adobe Campaign樹狀結構中的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Web analytics process]**&#x200B;資料夾下使用。

![](assets/webanalytics_workflows.png)

* **[!UICONTROL Recovering of web events]**:每小時一次，此工作流程會下載關於指定網站上使用者行為的區段，並將其納入Adobe Campaign資料庫中，然後開始再行銷工作流程。
* **[!UICONTROL Event purge]**:此工作流程可讓您根據欄位中設定的期間，從資料庫刪除所有 **[!UICONTROL Lifespan]** 事件。如需詳細資訊，請參閱[在Adobe Campaign Classic中設定外部帳戶](#external-account-classic)。
* **[!UICONTROL Identification of converted contacts]**:再行銷活動後購買的訪客目錄。此工作流程收集的資料可在&#x200B;**[!UICONTROL Re-marketing efficiency]**&#x200B;報表中存取，請參閱此[page](#creating-a-re-marketing-campaign)。
* **[!UICONTROL Sending of indicators and campaign attributes]**:可讓您使用Adobe Campaign Connector，透過Adobe Analytics將電子郵件促銷活動指標傳送至Adobe Experience Cloud。此工作流程每天凌晨4:00會觸發，且可能需要24小時才會將資料傳送至Analytics。

   請注意，此工作流程不應重新啟動，否則會重新傳送所有可能扭曲Analytics結果的先前資料。

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
   >傳送的資料是根據上次快照的差值，可能導致量度資料中的負值。

   傳送的屬性如下：

   * **[!UICONTROL Internal name]** (@internalName)
   * **[!UICONTROL Label]** (@label)
   * **[!UICONTROL Label]** (操作/@label):只有在安裝 **** 了Campaign套件時
   * **[!UICONTROL Nature]** (操作/@nature):只有在安裝 **** 了Campaign套件時
   * **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
   * **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
   * **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
   * **[!UICONTROL Contact date]** (排程/@contactDate)



## 在Adobe Campaign中追蹤傳遞 {#tracking-deliveries-in-adobe-campaign}

為了讓Adobe Experience Cloud在Adobe Campaign傳送後能夠追蹤網站上的活動，您必須在傳送屬性中參考相符的連接器。 若要這麼做，請套用下列步驟：

1. 開啟要追蹤之促銷活動的傳送。

   ![](assets/webanalytics_delivery_properties_003.png)

1. 開啟傳送屬性。
1. 前往&#x200B;**[!UICONTROL Web Analytics]**&#x200B;標籤，並選取先前建立的外部帳戶。 請參閱[在Adobe Campaign Classic中設定外部帳戶](#external-account-classic)。

   ![](assets/webanalytics_delivery_properties_002.png)

1. 您現在可以傳送傳遞內容，並在Adobe Analytics中存取報表。

## 建立再行銷行銷活動 {#creating-a-re-marketing-campaign}

若要準備再行銷行銷活動，只需建立要用於再行銷類型行銷活動的傳遞範本。 然後設定再行銷促銷活動，並將其連結至區段。 每個區段必須有不同的再行銷促銷活動。

當Adobe Campaign完成分析初始促銷活動鎖定目標之人員的行為的區段後，就會自動開始再行銷促銷活動。 如果放棄購買或檢視產品而未進行購買，則會傳送傳遞給相關收件者，以便其網站瀏覽結束購買。

Adobe Campaign提供個人化傳遞範本，供您自行使用或建立資料庫，以準備行銷活動。

1. 從&#x200B;**[!UICONTROL Explorer]**，前往Adobe Campaign樹的&#x200B;**[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**&#x200B;資料夾。

1. 複製Adobe Campaign提供的&#x200B;**[!UICONTROL Email delivery (re-marketing)]**&#x200B;範本或再行銷範本範例。

   ![](assets/webanalytics_delivery_model.png)

1. 個人化範本以符合您的需求並加以儲存。

1. 建立新促銷活動，並從下拉式清單中選取&#x200B;**[!UICONTROL Re-marketing campaign]**&#x200B;範本。

   ![](assets/webanalytics_remarketing_campaign_002.png)

1. 按一下&#x200B;**[!UICONTROL Configure...]**&#x200B;連結，以指定連結至促銷活動的區段和傳送範本。

1. 選取先前設定的外部帳戶。

   ![](assets/webanalytics_remarketing_campaign_003.png)

1. 選取相關區段。

   ![](assets/webanalytics_remarketing_campaign_005.png)

1. 選取要用於此再行銷促銷活動的傳送範本，然後按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以關閉視窗。

   ![](assets/webanalytics_remarketing_campaign_006.png)

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;以關閉促銷活動視窗。

**[!UICONTROL Re-marketing efficiency]**&#x200B;報表可透過全域報表頁面存取。 它可讓您檢視與Adobe Campaign再行銷活動後購物車放棄次數相關的轉換連絡人數（亦即已購買商品）。 轉換率是每週、每月或自Adobe Campaign與網頁分析工具開始同步後計算。

![](assets/remarketing_reporting.png)

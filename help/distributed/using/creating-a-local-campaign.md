---
product: campaign
title: 建立本機行銷活動
description: 建立本機行銷活動
feature: Distributed Marketing
exl-id: 17b5865a-5e04-4b3b-8b6a-12d5c1a9c1da
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 1%

---

# 建立本機行銷活動{#creating-a-local-campaign}



本機行銷活動是從清單所參照的範本建立的例項 **[!UICONTROL campaign packages]** 與 **特定執行排程**. 其目的在於使用由中央實體設定和設定的行銷活動範本，滿足本機通訊需求。 實作本機作業的主要階段如下：

**中央實體**

1. 建立本機行銷活動範本。
1. 從範本建立行銷活動套件。
1. 發佈行銷活動套件。
1. 正在核准訂單。

**針對本機實體**

1. 訂購行銷活動。
1. 執行行銷活動。

## 建立本機行銷活動範本 {#creating-a-local-campaign-template}

若要建立行銷活動套件，您必須先建立 **行銷活動範本** 透過 **[!UICONTROL Resources > Templates]** 節點。

若要建立新的本機範本，請複製預設值 **[!UICONTROL Local campaign (opLocal)]** 範本。

![](assets/mkg_dist_local_op_creation.png)

為行銷活動範本命名，並完成可用的欄位。

![](assets/mkg_dist_local_op_creation1.png)

在行銷活動視窗中，按一下 **[!UICONTROL Edit]** 標籤，然後按一下 **[!UICONTROL Advanced campaign settings...]** 連結。

![](assets/mkt_distr_4.png)

### 網頁介面 {#web-interface}

在 **分散式行銷** 標籤，您可以選擇Web介面的型別，並指定當本機實體下訂單時要輸入的預設值和引數。

Web介面對應於由本機實體在訂購行銷活動時填寫的表單。

選取要套用至從範本建立之行銷活動的網頁介面型別：

![](assets/mkt_distr_1.png)

可用的網頁介面有四種型別：

* **[!UICONTROL By brief]** ：本機實體必須提供說明，以便說明行銷活動設定。 訂單獲得核准後，中央實體會設定並執行整個行銷活動。

  ![](assets/mkt_distr_6.png)

* **[!UICONTROL By form]** ：本機實體可存取網路表單，其中他們可使用個人化欄位編輯內容、目標、其大小上限，以及建立和擷取日期（視使用的範本而定）。 本機實體可以評估目標並預覽此網路表單的內容。

  ![](assets/mkt_distr_8.png)

  提供的表單是在Web應用程式中指定的，必須在下拉式清單中從 **[!UICONTROL web Interface]** 範本中的欄位 **[!UICONTROL Advanced campaign settings...]** 連結。 請參閱 [建立本機行銷活動（依表單）](examples.md#creating-a-local-campaign--by-form-).

  >[!NOTE]
  >
  >此範例中使用的Web應用程式為範例。 您必須建立特定的網頁應用程式才能使用表單。 請參閱 [API](../../configuration/using/about-web-services.md).

  ![](assets/mkt_distr_7.png)

* **[!UICONTROL By external form]** ：本機實體可存取其外部網路(非Adobe Campaign)中的促銷活動引數。 這些引數與 **本地行銷活動（依表單）**.
* **[!UICONTROL Pre-set]** ：本機實體會使用預設表單來訂購行銷活動，而不會進行當地語系化。

  ![](assets/mkt_distr_5.png)

### 預設值 {#default-values}

選取 **[!UICONTROL Default values]** 將由本機實體完成。 例如：

* 聯絡與解壓縮日期，
* 目標特性（年齡區段等）。

![](assets/mkg_dist_local_op_creation2.png)

完成 **[!UICONTROL Parent marketing program]** 和 **[!UICONTROL Charge]** 欄位。

![](assets/mkg_dist_local_op_creation3.png)

### 核准 {#approvals}

從 **[!UICONTROL Advanced parameters for campaign entry]** 連結，您可以指定稽核者數目上限。

![](assets/s_advuser_mkg_dist_add_valid_op1.png)

訂購行銷活動時，檢閱者將由本機實體輸入。

![](assets/mkt_distr_5.png)

如果您不想要為行銷活動命名稽核者，請輸入0。

### 文件 {#documents}

您可以允許本機實體運運算元連結檔案（文字檔案、試算表、影像、行銷活動說明等） 至本機行銷活動。 此 **[!UICONTROL Advanced parameters for campaign entry...]** 連結可讓您限制檔案數量。 若要這麼做，只要輸入 **[!UICONTROL Number of documents]** 欄位。

![](assets/s_advuser_mkg_dist_local_docs.png)

訂購行銷活動套件時，表單會建議連結範本中對應欄位所指示數量的檔案。

![](assets/s_advuser_mkg_dist_add_docs.png)

如果您不想顯示檔案上傳欄位，請輸入 **[!UICONTROL 0]** 在 **[!UICONTROL Number of documents]** 欄位。

>[!NOTE]
>
>此 **[!UICONTROL Advanced parameters for campaign entry]** 可透過勾選來停用 **[!UICONTROL Do not display the page used to enter the campaign parameters]**.

![](assets/s_advuser_mkg_dist_disable_op_parameters.png)

### 工作流程 {#workflow}

在 **[!UICONTROL Targeting and workflows]** 索引標籤中，建立收集以下專案的行銷活動工作流程 **[!UICONTROL Default values]** 指定於 **[!UICONTROL Advanced campaign settings...]** 和建立傳送。

![](assets/mkg_dist_local_op_creation4b.png)

按兩下 **[!UICONTROL Query]** 活動，以根據指定的進行設定 **[!UICONTROL Default values]**.

![](assets/mkt_dist_local_campaign_localize_query.png)

### 傳遞 {#delivery}

在 **[!UICONTROL Audit]** 索引標籤，按一下 **[!UICONTROL Detail...]** 圖示以檢視 **[!UICONTROL Scheduling]** 用於選取的傳遞。

![](assets/mkg_dist_local_op_creation4c.png)

此 **[!UICONTROL Scheduling]** 圖示可讓您設定傳送的聯絡人及執行日期。

![](assets/mkg_dist_local_op_creation4d.png)

如有必要，請設定傳遞的大小上限：

![](assets/mkg_dist_local_op_creation4e.png)

找出傳送的HTML。 例如，在 **[!UICONTROL Delivery > Current order > Additional fields]**，使用 **[!UICONTROL Age segment]** 欄位，以根據目標的年齡來找出傳送。

![](assets/mkt_dist_local_campaign_localize_html.png)

儲存您的行銷活動範本。 您現在可以從以下位置使用 **[!UICONTROL Campaign packages]** 在中檢視 **[!UICONTROL Campaigns]** 標籤，按一下 **[!UICONTROL Create]** 按鈕。

![](assets/mkt_distr_9.png)

>[!NOTE]
>
>行銷活動範本及其一般設定會在中詳細說明 [行銷活動範本](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

## 建立行銷活動套件 {#creating-the-campaign-package}

為了讓本機實體可使用行銷活動範本，需將其新增至清單。 為此，中央機構需要建立新套件。

應用以下步驟：

1. 在 **[!UICONTROL Navigation]** 區段於 **行銷活動** 頁面，按一下 **[!UICONTROL Campaign packages]** 連結。
1. 按一下 **[!UICONTROL Create]** 按鈕。

   ![](assets/mkg_dist_add_an_entry.png)

1. 視窗上方的區段可讓您選取 [先前](#creating-a-local-campaign-template) 指定的行銷活動套件範本。

   根據預設， **[!UICONTROL New local campaign package (localEmpty)]** 範本用於本機行銷活動。

1. 指定行銷活動套件的標籤、資料夾和執行排程。

### 日期 {#dates}

開始和結束日期定義行銷活動套件清單中的行銷活動可見期間。

可用日期是促銷活動可供本機實體（訂購）使用的日期。

>[!CAUTION]
>
>如果本機實體未在截止日期前預留行銷活動，則將無法使用。

此資訊可在傳送給當地代理機構的通知訊息中找到，如下所示：

![](assets/s_advuser_mkg_dist_local_notif.png)

### 對象 {#audience}

對於本機行銷活動，中央實體可以透過核取以指定相關的本機實體。 **[!UICONTROL Limit the package to a set of local entities]**.

![](assets/s_advuser_mkg_dist_create_mutual_entry3.png)

### 其他設定 {#additional-settings}

儲存套件後，中央實體即可從編輯它 **[!UICONTROL Edit]** 標籤。

![](assets/mkg_dist_edit_kit.png)

從 **[!UICONTROL General]** 索引標籤中，中央實體可以：

* 從設定行銷活動套件檢閱者 **[!UICONTROL Approval parameters...]** 連結，
* 檢閱執行排程，
* 新增或刪除本機實體。

>[!NOTE]
>
>依預設，每個實體都可以排序 **本地行銷活動** 僅一次。
>   
>檢查 **[!UICONTROL Enable multiple creation]** 允許從行銷活動套件建立數個本機行銷活動的選項。

![](assets/mkg_dist_local_op_multi_crea.png)

### 通知 {#notifications}

當行銷活動可用或達到註冊截止日期時，會傳送訊息給本機通知群組的操作者。 有關詳細資訊，請參閱 [組織實體](about-distributed-marketing.md#organizational-entities).

## 訂購行銷活動 {#ordering-a-campaign}

行銷活動套件一經核准且開始實作期間後，即可供本機實體存取。 本機實體會收到電子郵件，通知他們新的行銷活動套件可供使用（一旦達到可用日期）。

>[!NOTE]
>
>如果在建立行銷活動套件時指定了某些本機實體，則這些實體將是唯一會收到通知的實體。 如果未指定本機實體，則所有本機實體都會收到通知。

![](assets/mkg_dist_local_op_notification.png)

若要使用中央實體提供的行銷活動，本機實體必須加以排序。

若要訂購行銷活動，請執行下列步驟：

1. 按一下 **[!UICONTROL Order campaign]** 或Adobe Campaign中對應的按鈕中設定。

   輸入您的ID和密碼以訂購行銷活動。 介面是由網頁應用程式中定義的一組頁面所組成。

   >[!NOTE]
   >
   >網頁應用程式的詳細資訊，請參閱 [本節](../../web/using/about-web-applications.md).

1. 在第一個頁面中輸入必要資訊（訂購標籤和註解），然後按一下 **[!UICONTROL Next]**.

   ![](assets/mkg_dist_subscribe_step1.png)

1. 完成可用引數並核准訂單。

1. 系統會傳送通知給本機實體所屬之組織實體的經理，以核准此訂單。

   ![](assets/mkg_dist_subscribe_step3.png)

1. 資訊會傳回至本機與中央實體。 雖然本機實體只能檢視自己的訂單，但中央實體可以檢視任何本機實體的所有訂單，如下所示：

   ![](assets/mkg_dist_subscribe_central_view.png)

   操作員可以顯示訂單詳細資料：

   ![](assets/mkg_dist_local_op_catalog_detail_1.png)

   此 **[!UICONTROL Edit]** 索引標籤包含本地實體在訂購行銷活動時輸入的資訊。

   ![](assets/mkg_dist_local_op_catalog_detail_1b.png)

1. 訂單必須由中央實體核准才能完成。

   ![](assets/mkg_dist_local_op_catalog_detail_3.png)

   有關詳細資訊，請參閱 [核准流程](#approval-process) 區段。

1. 接著，本機運運算元會收到行銷活動可用性的通知：行銷活動可用性可在中的行銷活動套件清單中找到 **行銷活動** 標籤。 然後可以使用行銷活動。 有關詳細資訊，請參閱 [存取行銷活動](accessing-campaigns.md).

   此 **[!UICONTROL Start targeting with order approval]** 選項可讓本機實體在核准訂單後立即執行行銷活動。

   ![](assets/mkg_dist_local_op_catalog_use.png)

## 核准訂單 {#approving-an-order}

若要確認行銷活動訂單，中央實體必須核准它。

此 **[!UICONTROL Campaign orders]** 概述，存取： **行銷活動** 索引標籤可讓您檢視行銷活動訂單的狀態並核准它們。

>[!NOTE]
>
>本地實體可以變更訂單，直到核准為止。

### 核准流程 {#approval-process}

#### 電子郵件通知 {#email-notification}

當行銷活動由本機實體訂購時，其稽核者會收到電子郵件通知，如下所示：

![](assets/mkg_dist_valid_notif_email.png)

>[!NOTE]
>
>選取檢閱者會顯示在 [檢閱者](#reviewers) 區段。 他們可以接受或拒絕訂單。

![](assets/mkg_dist_command_valid_web.png)

#### 透過Adobe Campaign主控台核准 {#approving-via-the-adobe-campaign-console}

您也可以在行銷活動訂單總覽中，透過主控台核准訂單。 若要核准訂單，請選取訂單並按一下 **[!UICONTROL Approve the order]**.

![](assets/mkg_dist_local_order_valid.png)

>[!NOTE]
>
>在行銷活動推出日期之前，您仍可編輯及重新設定行銷活動。 本機實體也可以按一下 **[!UICONTROL Cancel]** 按鈕。

#### 建立行銷活動 {#creating-a-campaign}

行銷活動訂單獲得核准後，即可由本機實體設定及執行。

![](assets/mkg_dist_mutual_op_created.png)

有關詳細資訊，請參閱 [存取行銷活動](accessing-campaigns.md).

### 拒絕核准 {#rejecting-an-approval}

負責核准的操作員可以拒絕訂單或行銷活動套件。

![](assets/mkg_dist_do_not_valid.png)

若複查者拒絕訂單，系統會自動將相關通知傳送給相關當地實體：它會顯示拒絕核准之操作員所輸入的註解。

資訊會顯示在行銷活動套件清單頁面或行銷活動訂單頁面上。 如果他們能存取Adobe Campaign主控台，本機實體就會收到此拒絕的通知。

![](assets/mkg_dist_do_not_valid_view.png)

他們可以檢視行銷活動套件中的相關註解 **[!UICONTROL Edit]** 標籤。

![](assets/mkg_dist_do_not_valid_tab.png)

### 檢閱者 {#reviewers}

每次需要核準時，稽核者都會收到電子郵件通知。

對於每個本機實體，會針對行銷活動訂單核准和行銷活動核准選取稽核者。 如需有關選取本機稽核者的詳細資訊，請參閱 [組織實體](about-distributed-marketing.md#organizational-entities).

>[!NOTE]
>
>若要讓此選取成為可能，訂單核准必須尚未生效。

### 取消訂單 {#canceling-an-order}

中央機構可使用以下方式取消訂單： **[!UICONTROL Delete]** 按鈕，位於訂單控制面板上。

![](assets/mkg_dist_local_op_cancel.png)

這會取消中的行銷活動 **[!UICONTROL Campaign orders]** 檢視。

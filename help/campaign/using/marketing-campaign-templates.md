---
title: 行銷宣傳範本
seo-title: 行銷宣傳範本
description: 行銷宣傳範本
seo-description: 行銷宣傳範本
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 行銷活動範本 {#campaign-templates}

促銷活動範本集中在節 **[!UICONTROL Resources > Templates > Campaign templates]** 點中。 預設範本會以標準形式提供。 它可讓您使用所有可用的模組（檔案、工作、種子位址等）建立新的促銷活動，但提供的模組取決於您的權限和Adobe Campaign平台的設定。

## 建立或複製促銷活動範本 {#creating-or-duplicating-a-campaign-template}

要建立新模板，請執行以下步驟：

1. 開啟促銷活 **動總管**。
1. 在「 **資源>範本>促銷活動範本**」中，按一 **下範本清單上方的工具列中的「新增** 」。

   ![](assets/create_campaign_template_1.png)

1. 輸入新促銷活動範本的標籤。
1. 按一 **下「儲存** 」並重新開啟範本。
1. 在「編 **輯** 」索引標籤中，輸 **入「內部名稱** 」和其他值（如果需要）。
1. 選取「 **進階促銷活動設定** 」，將工作流程新增至促銷活動範本。

   ![](assets/create_campaign_template_2.png)

1. 將「定位 **」和工作流程** 值變更 **為「是」**。

   ![](assets/create_campaign_template_3.png)

1. **在「定位**&#x200B;和工作流程&#x200B;**」標籤中，按**&#x200B;一下「新增工作流程……」.

   ![](assets/create_campaign_template_4.png)

1. 填寫「標 **簽** 」欄位，然後單 **擊「確定」**。
1. 根據您的需求建立您的工作流程。
1. 按一下 **儲存**。 您的範本現在已可用於促銷活動。

您也可以複製預設範本，以重複使用並調整其設定。

促銷活動範本的各種標籤和子標籤可讓您存取其設定，如「一般」設定 [所述](#general-configuration)。

![](assets/s_ncs_user_new_op_template_duplicate.png)

## 設定促銷活動範本 {#configuring-a-campaign-template}

促銷活動是以共用一組預先定義參數的模型為基礎。

在預設設定中，促銷活動範本會集中在Adobe **[!UICONTROL Resources > Templates > Campaign templates]** 促銷活動樹狀結構的節點中。

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>按一下首頁上的表徵圖 **[!UICONTROL Explorer]** 時將顯示樹。

提供現成可用的範本，以建立尚未定義特定設定的促銷活動。 您可以建立和設定促銷活動範本，然後從這些範本建立促銷活動。

促銷活動範本的建立與設定會顯示在促銷活動 [範本中](#campaign-templates)。

如需建立促銷活動的詳細資訊，請參 [閱建立促銷活動和電子郵件](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) 。

## 可用模組的配置 {#configuration-of-the-available-modules}

### 模組選擇 {#module-selection}

連結 **[!UICONTROL Advanced campaign settings...]** 可讓您根據此範本啟用和停用促銷活動的工作。 選取您要在此範本所建立之促銷活動中啟用的功能。

![](assets/s_ncs_user_op_template_tab1.3.png)

如果未選取功能，則與程式相關的元素（功能表、圖示、選項、標籤、子標籤等）不會顯示在範本的介面中，也不會顯示在以此範本為基礎的促銷活動中。 促銷活動詳細資料左側的標籤通常與範本中選取的程式一致。 例如，如果未選 **取「費用」和** 「目標」，則基於此范 **[!UICONTROL Budget]** 本的促銷活動中不會顯示對應的標籤。

此外，設定視窗的捷徑會新增至促銷活動控制面板。 啟用功能時，直接連結會從促銷活動控制面板提供存取權。

例如，使用下列設定：

![](assets/s_ncs_user_op_template_tab1.4.png)

促銷活動控制面板中會顯示下列連結( **[!UICONTROL Add a task]** 連結遺失):

![](assets/s_ncs_user_op_template_tab1.3ex.png)

只會顯示下列標籤：

![](assets/s_ncs_user_op_template_tab1.4ex.png)

但是，使用這種配置：

![](assets/s_ncs_user_op_template_tab2.2ex.png)

將會顯示下列連結和標籤：

![](assets/s_ncs_user_op_template_tab2.3ex.png)

### 已啟用模組的類型 {#typology-of-enabled-modules}

* **控制組**

   選取此模組時，會在範本的進階設定和基於此範本的促銷活動中新增另一個標籤。 設定可透過範本定義，或個別定義每個促銷活動。

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **種子地址**

   選取此模組時，會在範本的進階設定和基於此範本的促銷活動中新增另一個標籤。 設定可透過範本定義，或個別定義每個促銷活動。

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **檔案**

   選取此模組後，會在範本的標籤和基於此范 **[!UICONTROL Edition]** 本的促銷活動中新增另一個標籤。 附加的檔案可從範本中新增，或針對每個促銷活動個別新增。

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **大綱**

   選取此模組時，會將子 **[!UICONTROL Delivery outlines]** 標籤新增至標籤，以 **[!UICONTROL Documents]** 定義促銷活動的傳送外框。

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **定位與工作流程**

   當您選取模 **[!UICONTROL Targeting and workflows]** 組時，會新增標籤，讓您根據此範本為促銷活動建立一或多個工作流程。 您也可以根據此範本，針對每個促銷活動個別設定工作流程。

   ![](assets/s_ncs_user_op_template_activate_5.png)

   啟用此模組後，會在促銷活動的進階設定中新增標籤，以定義流程執行順序。

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **核准**

   如果您選擇 **[!UICONTROL Approval]**&#x200B;該流程，則可以選擇要審批的流程以及負責審批的操作員。

   ![](assets/s_ncs_user_op_template_activate_5b.png)

* **支出和目標**

   選取此模組時，會將標籤 **[!UICONTROL Budget]** 新增至範本和促銷活動的詳細資料中，以便選取相關預算。

   ![](assets/s_ncs_user_op_template_activate_7.png)

### 核准工作 {#approval-of-jobs}

您可以選擇是否通過模板高級設定部分的選 **[!UICONTROL Approvals]** 項卡啟用流程批准。 必須批准為其選擇批准的作業，才能獲得消息傳遞的授權。

必須將審核者運算子或運算子組關聯到每個啟用的批准。

## 一般配置 {#general-configuration}

### 範本屬性 {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

當您建立促銷活動範本時，需要輸入下列資訊：

* 輸入 **模板的** 標籤：此標籤預設會指派給透過此範本建立的所有促銷活動。
* 從下拉式清 **單中** ，選取促銷活動性質。 此清單中可用的值是枚舉中保存的 **[!UICONTROL natureOp]** 值。

   >[!NOTE]
   >
   >有關枚舉的詳細資訊，請參 [閱開始](../../platform/using/managing-enumerations.md) 。

* 選擇促 **銷活動類型**:唯一、循環或週期。 依預設，促銷活動範本會套用至獨特的促銷活動。 週期性和週期性促銷活動的詳細資訊，請參閱：週期 [性和週期性促銷活動](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns)。
* 指定促銷活動的持續時間，即促銷活動將發生的天數。 根據此範本建立促銷活動時，促銷活動的開始和結束日期會自動填入。

   如果促銷活動是經常性的，您必須直接在範本中指定促銷活動開始和結束日期。

* 指定范 **本的相關程** 式：基於此範本的促銷活動將連結至選取的方案。

### 範本執行參數 {#template-execution-parameters}

此連 **[!UICONTROL Advanced campaign settings...]** 結可讓您設定範本的進階選項，以處理傳送目標（控制群組、種子位址等）以及促銷活動測量和工作流程執行的設定。

![](assets/s_ncs_user_op_template_tab1.2.png)

## 促銷活動反向排程 {#campaign-reverse-scheduling}

您可以為促銷活動建立反向排程，例如準備事件，其日期事先已知。 促銷活動範本現在可讓您根據促銷活動的結束日期，計算任務的開始日期。

在任務配置框中，轉到該區 **[!UICONTROL Implementation schedule]** 域並選中該 **[!UICONTROL The start date is calculated based on the campaign end date]** 框。 （此處，「開始日期」是任務開始日期）。 轉到該字 **[!UICONTROL Start]** 段並輸入間隔：此任務將在促銷活動結束日期之前很久開始。 如果您輸入的時段比促銷活動設定為最後，則工作會在促銷活動之前開始。

![](assets/mrm_task_in_template_start_date.png)

當您使用此範本建立促銷活動時，系統會自動計算工作開始日期。 不過，您隨時可以稍後變更。

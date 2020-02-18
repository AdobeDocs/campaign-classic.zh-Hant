---
title: 設定行銷促銷活動
seo-title: 設定行銷促銷活動
description: 設定行銷促銷活動
seo-description: null
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
source-git-commit: eee744eb5bc7a43fd412ffb01f0546385146a978

---


# 設定行銷促銷活動{#setting-up-marketing-campaigns}

促銷活動包括動作（傳送）和程式（匯入或擷取檔案），以及資源（行銷檔案、傳送大綱）。 它們用於行銷促銷活動。 促銷活動是方案的一部分，而方案則包含在促銷活動計畫中。

若要建立行銷促銷活動：

1. 建立促銷活動：探索促銷活動及其特性：標籤、類型、開始和結束日期、預算、相關資源、經理和參與者。

   請參閱 [建立促銷活動](#creating-a-campaign)。

1. 定義目標人口：建立具有定位查詢的工作流程。

   請參 [閱選擇目標人口](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)。

1. 建立傳送：選取頻道並定義要傳送的內容。

   請參閱 [建立傳送](../../campaign/using/marketing-campaign-deliveries.md#creating-deliveries)。

1. 核准傳送。

   請參閱 [核准程式](../../campaign/using/marketing-campaign-approval.md#approval-process)。

1. 監控傳送。

   請參閱「 [監視](../../campaign/using/marketing-campaign-monitoring.md)」。

1. 規劃促銷活動和相關成本。

   請參 [閱建立服務提供商及其成本結構](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

完成這些步驟後，您可以開始傳送(請參閱 [Starting a delivery](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery))、檢查與傳送相關的資料、流程和資訊，並視需要管理相關的檔案(請參閱 [Managing associated documents](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents))。 您也可以追蹤促銷活動和傳送的處理階段的執行情況(請參閱 [追蹤](../../campaign/using/marketing-campaign-monitoring.md)。

## 建立計畫和方案層次結構 {#creating-plan-and-program-hierarchy}

要為行銷計畫和方案配置資料夾層次結構，請執行以下操作：

1. 按一下 **首頁上的** 「檔案總管」圖示。
1. 按一下右鍵要在其中建立計畫的資料夾。
1. 選擇 **新增資料夾>促銷活動管理>計畫**。

   ![](assets/create_plan_1.png)

1. 重新命名計畫。
1. **按一下右鍵新建立的計畫，然後選擇「**&#x200B;屬性……」。.

   ![](assets/create_plan_2.png)

1. 在「一 **般** 」標籤中，修改「 **內部名稱** 」以避免在套件匯出期間重複。
1. 按一下 **儲存**。
1. 按一下右鍵新建立的計畫，然後選擇 **建立新的「程式」資料夾**。
1. 重複上述步驟，更名新程式資料夾及其內部名稱。

## 建立促銷活動 {#creating-a-campaign}

### 新增促銷活動 {#adding-a-campaign}

您可以透過促銷活動清單建立促銷活動。 若要顯示此檢視，請選取控 **[!UICONTROL Campaigns]** 制面板中的選 **[!UICONTROL Campaigns]** 單。

![](assets/s_ncs_user_add_an_op_from_list.png)

欄位 **[!UICONTROL Program]** 可讓您選取促銷活動要附加到的方案。 此資訊是強制性的。

![](assets/s_ncs_user_new_op_wz_a.png)

您也可以透過方案建立促銷活動。 要執行此操作，請單 **[!UICONTROL Add]** 擊相關程式 **[!UICONTROL Schedule]** 頁籤中的按鈕。

![](assets/s_ncs_user_add_an_op.png)

當您透過程式的標籤建立促 **[!UICONTROL Schedule]** 銷活動時，促銷活動會自動連結至相關的程式。 在此 **[!UICONTROL Program]** 例中，該欄位是隱藏的。

在促銷活動建立視窗中，選取促銷活動範本並新增促銷活動的名稱和說明。 您也可以指定促銷活動的開始和結束日期。

按一 **[!UICONTROL OK]** 下以建立促銷活動。 它會新增至計畫排程。

![](assets/s_ncs_user_program_planning_with_op.png)

>[!NOTE]
>
>若要篩選要顯示的促銷活動，請按一 **[!UICONTROL Filter]** 下連結並選取要顯示的促銷活動狀態。

![](assets/s_ncs_user_program_planning_filter.png)

### 編輯和設定促銷活動 {#editing-and-configuring-a-campaign}

然後，您可以編輯剛建立的促銷活動，並定義其參數。

若要開啟和設定促銷活動，請從排程中選取促銷活動，然後按一下 **[!UICONTROL Open]**。

![](assets/s_ncs_user_new_op_edit.png)

這會帶您進入促銷活動控制面板。

## 週期性和週期性促銷活動 {#recurring-and-periodic-campaigns}

循環促銷活動是根據特定範本的促銷活動，其工作流程設定為根據關聯的排程執行。 因此，工作流程將會在促銷活動中重複執行。 在每次執行時都會復制定位，並追蹤各種進程和目標人口族群。 您也可以透過自動建立工作流程期間的涵蓋期間，提前執行未來的定位，以便使用目標估計來啟動模擬。

定期促銷活動是根據其範本的執行排程自動建立的促銷活動。

### 建立循環促銷活動 {#creating-a-recurring-campaign}

循環促銷活動是從定義要執行的工作流程範本和執行排程的特定範本建立。

#### 建立循環促銷活動的範本 {#creating-the-campaign-template}

1. 建立促銷 **[!UICONTROL Recurring]** 活動範本。

   >[!NOTE]
   >
   >建議您複製預設範本，而非建立空白範本。

   ![](assets/s_ncs_user_op_template_recur_tab.png)

1. 輸入範本的名稱和促銷活動的持續時間。

   ![](assets/s_ncs_user_op_template_recur_duplicate.png)

1. 對於此類型的促銷活動，會 **[!UICONTROL Schedule]** 新增標籤以建立範本執行排程。

在此標籤中，根據此範本指定促銷活動的計畫執行日期。

![](assets/s_ncs_user_op_template_recur_planning.png)

您可以使用計畫建立嚮導自動填寫所有執行日期。 若要這麼做，請按一下 **[!UICONTROL Complete the execution schedule...]** 表格上方的連結。

![](assets/s_ncs_user_op_template_recur_planning_wz.png)

執行調度的配置模式與工作流的 **[!UICONTROL Scheduler]** 對象一致。 如需詳細資訊，請參閱[本小節](../../workflow/using/executing-a-workflow.md#architecture)。

>[!IMPORTANT]
>
>必須小心執行執行計畫配置，以避免資料庫過載。 循環促銷活動會根據指定的排程，複製其範本的工作流程。 過度頻繁的工作流建立的實現會阻礙資料庫的操作。

1. 在欄位中指定 **[!UICONTROL Create in advance for]** 值，以建立所指定期間的對應工作流程。
1. 根據此範本建立要用於促銷活動的工作流程範本，並包含定位參數和一或多個一般傳送。

   >[!NOTE]
   >
   >此工作流程必須儲存為循環工作流程範本。 若要這麼做，請編輯工作流程屬性，並選取 **[!UICONTROL Recurring workflow template]** 標籤中的 **[!UICONTROL Execution]** 選項。

   ![](assets/s_ncs_user_op_template_recur_wf_option.png)

#### 建立循環促銷活動 {#create-the-recurring-campaign}

若要根據範本中定義的排程建立週期性促銷活動並執行其工作流程，請套用下列程式：

1. 根據循環促銷活動範本建立新促銷活動。
1. 填寫工作流程執行排程。

   ![](assets/s_ncs_user_op_recur_planning.png)

1. 促銷活動排程可讓您輸入每一行的自動工作流程建立或執行開始日期。

   對於每一行，您可以添加以下附加選項：

   * **[!UICONTROL To be approved]** :可讓您在工作流程中強制傳送核准請求。
   * **[!UICONTROL To be started]** :可讓您在到達開始日期時啟動工作流程。
   欄位 **[!UICONTROL Create in advance for]** 可讓您建立涵蓋所輸入期間的所有工作流程。

   執行工作流程時， **[!UICONTROL Jobs on campaigns]** 會根據促銷活動排程中定義的發生次數，建立專用的工作流程。 因此，會為每個執行日期建立工作流。

1. 循環工作流程會自動從促銷活動中出現的工作流程範本建立。 它們可從促銷活動 **[!UICONTROL Targeting and workflows]** 的標籤中顯示。

   ![](assets/s_ncs_user_op_recur_planning_wfs.png)

   循環工作流實例的標籤由其模板標籤和工作流編號組成，其中的#字元介於之間。

   從排程建立的工作流程會自動與其關聯，位 **[!UICONTROL Workflow]** 於標籤的欄 **[!UICONTROL Schedule]** 中。

   ![](assets/s_ncs_user_op_recur_planning_wfs_1.png)

   每個工作流程都可從此標籤進行編輯。

   ![](assets/s_ncs_user_op_recur_planning_wf_edit.png)

   >[!NOTE]
   >
   >與工作流關聯的計畫行的起始日期可從工作流的變數中使用，其語法如下：\
   >`$date(instance/vars/@startPlanningDate)`

### 建立定期促銷活動 {#creating-a-periodic-campaign}

週期性促銷活動是根據特定範本的促銷活動，可讓您根據執行排程建立促銷活動例項。 促銷活動例項會根據定期促銷活動範本自動建立，視範本排程中定義的頻率而定。

#### 建立促銷活動範本 {#creating-the-campaign-template-1}

1. 建立促銷 **[!UICONTROL Periodic]** 活動範本，最好複製現有的促銷活動範本。

   ![](assets/s_ncs_user_op_template_period_create.png)

1. 輸入模板的屬性。

   >[!NOTE]
   >
   >指派範本給的運算元，必須擁有在所選方案中建立促銷活動的適當權限。

1. 建立與此範本關聯的工作流程。 它會複製到範本建立的每個定期促銷活動中。

   ![](assets/s_ncs_user_op_template_period_wf.png)

   >[!NOTE]
   >
   >此工作流是工作流模板。 無法從促銷活動範本執行。

1. 完成循環促銷活動範本的執行排程：按一 **[!UICONTROL Add]** 下按鈕並定義開始和結束日期，或透過連結填寫執行排程。

   ![](assets/s_ncs_user_op_template_period_planning_add.png)

   >[!IMPORTANT]
   >
   >定期促銷活動範本會根據上述定義的排程建立新促銷活動。 因此，必須小心完成，以避免超出Adobe Campaign資料庫的負載。

1. 一旦達到執行開始日期，就會自動建立相符的促銷活動。 它具有其模板的所有特性。

   每個促銷活動都可透過範本排程進行編輯。

   ![](assets/s_ncs_user_op_template_period_planning.png)

每個定期促銷活動都包含相同的元素。 建立後，即會將其管理為標準促銷活動。

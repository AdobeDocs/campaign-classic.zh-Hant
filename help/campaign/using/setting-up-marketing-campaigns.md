---
product: campaign
title: 建立行銷活動
description: 瞭解如何建立和執行行銷活動
role: User
feature: Campaigns, Cross Channel Orchestration, Programs
exl-id: a8fce21f-ffe3-4819-87ca-ac0ad9f21e41
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 5%

---

# 開始使用行銷活動{#setting-up-marketing-campaigns}

行銷活動包括動作 (傳送) 和流程 (匯入或擷取檔案)，以及資源 (行銷文件、傳遞大綱)。 它們會用於行銷活動。 行銷活動是方案的一部分，而方案則包含在行銷活動計畫中。

![](assets/do-not-localize/how-to-video.png) 瞭解如何建立行銷計畫、方案和行銷活動 [在視訊中](#video)

若要建立行銷活動：

1. 建立行銷活動：探索行銷活動及其特性：標籤、型別、開始和結束日期、預算、相關資源、管理員和參與者。 [了解更多](#creating-a-campaign)。

1. 定義目標母體：使用目標查詢建立工作流程。 [了解更多](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)。

1. 建立傳送：選取管道並定義要傳送的內容。 [了解更多](../../campaign/using/marketing-campaign-deliveries.md#creating-deliveries)。

1. 核准傳遞。 [了解更多](../../campaign/using/marketing-campaign-approval.md)。

1. 監視傳遞。 [了解更多](../../campaign/using/marketing-campaign-monitoring.md)。

1. 計畫行銷活動和相關成本。 [了解更多](../../campaign/using/providers-stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

完成這些步驟後，您就可以開始傳送(請參閱 [本節](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery))，檢查與傳遞相關的資料、流程和資訊，並在必要時管理相關檔案(請參閱 [本節](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents))。 您也可以追蹤行銷活動和傳遞的處理階段執行情況(請參閱 [本節](../../campaign/using/marketing-campaign-monitoring.md))。

## 建立計畫和方案階層 {#creating-plan-and-program-hierarchy}

若要設定行銷計畫和方案的資料夾階層：

1. 按一下 **瀏覽器** 圖示加以存取。
1. 在您要建立計畫的資料夾上按一下滑鼠右鍵。
1. 選取 **新增資料夾> Campaign Management >計畫**.

   ![](assets/create_plan_1.png)

1. 重新命名計畫。
1. 在新建立的計畫上按一下滑鼠右鍵，然後選取 **屬性……**.

   ![](assets/create_plan_2.png)

1. 在 **一般** 標籤，修改 **內部名稱** 以避免在套件匯出期間出現重複專案。
1. 按一下「**儲存**」。
1. 在新建立的計畫上按一下滑鼠右鍵，然後選取 **建立新的&#39;Program&#39;資料夾**.
1. 重複上述步驟，重新命名新的程式資料夾及其內部名稱。

## 建立行銷活動 {#creating-a-campaign}

### 新增行銷活動 {#adding-a-campaign}

您可以透過行銷活動清單建立行銷活動。 若要顯示此檢視，請選取 **[!UICONTROL Campaigns]** 功能表 **[!UICONTROL Campaigns]** 儀表板。

![](assets/s_ncs_user_add_an_op_from_list.png)

此 **[!UICONTROL Program]** 欄位可讓您選取要附加行銷活動的方案。 此資訊是強制性的。

![](assets/s_ncs_user_new_op_wz_a.png)

行銷活動也可以透過方案建立。 若要這麼做，請按一下 **[!UICONTROL Add]** 中的按鈕 **[!UICONTROL Schedule]** 相關計畫的索引標籤。

![](assets/s_ncs_user_add_an_op.png)

當您透過建立行銷活動時 **[!UICONTROL Schedule]** 索引標籤中，此行銷活動會自動連結至相關的方案。 此 **[!UICONTROL Program]** 欄位在此情況下是隱藏的。

在行銷活動建立視窗中，選取行銷活動範本並新增行銷活動的名稱和說明。 您也可以指定行銷活動的開始和結束日期。

按一下 **[!UICONTROL OK]** 以建立行銷活動。 它會新增到方案排程中。

![](assets/s_ncs_user_program_planning_with_op.png)

>[!NOTE]
>
>若要篩選要顯示的行銷活動，請按一下 **[!UICONTROL Filter]** 連結並選取要顯示的行銷活動狀態。

![](assets/s_ncs_user_program_planning_filter.png)

### 編輯及設定行銷活動 {#editing-and-configuring-a-campaign}

然後，您可以編輯剛建立的行銷活動並定義其引數。

若要開啟並設定行銷活動，請從排程中選取行銷活動，然後按一下 **[!UICONTROL Open]**.

![](assets/s_ncs_user_new_op_edit.png)

這會將您導向行銷活動控制面板。

## 循環和定期行銷活動 {#recurring-and-periodic-campaigns}

循環行銷活動是基於特定範本的行銷活動，其工作流程已設定為根據關聯的排程執行。 因此，工作流程將在行銷活動中重複出現。 目標定位會在每次執行時重複，並追蹤各種流程和目標母體。 您也可以在自動建立工作流程期間，透過涵蓋期間預先執行未來目標，以啟動目標預估的模擬。

定期行銷活動是根據其範本的執行排程自動建立的行銷活動。

### 建立週期性行銷活動 {#creating-a-recurring-campaign}

循環行銷活動是從定義要執行的工作流程範本和執行排程的特定範本建立。

#### 建立週期性行銷活動的範本 {#creating-the-campaign-template}

1. 建立 **[!UICONTROL Recurring]** 行銷活動範本。

   >[!NOTE]
   >
   >建議您複製預設範本，而非建立空白範本。

   ![](assets/s_ncs_user_op_template_recur_tab.png)

1. 輸入範本名稱和行銷活動的持續時間。

   ![](assets/s_ncs_user_op_template_recur_duplicate.png)

1. 對於此型別的行銷活動， **[!UICONTROL Schedule]** 索引標籤會新增，以建立範本執行排程。

在此索引標籤中，根據此範本指定行銷活動的計畫執行日期。

![](assets/s_ncs_user_op_template_recur_planning.png)

執行排程的設定模式與 **[!UICONTROL Scheduler]** 工作流程的物件。 如需詳細資訊，請參閱[本章節](../../workflow/using/architecture.md)。

>[!IMPORTANT]
>
>必須小心執行執行排程設定，以避免資料庫超載。 週期性行銷活動會根據指定的排程複製其範本的工作流程。 執行過於頻繁的工作流程建立可能會阻礙資料庫的操作。

1. 在 **[!UICONTROL Create in advance for]** 欄位建立指定期間的對應工作流程。
1. 使用目標引數以及一或多個一般傳送，根據此範本建立要用於行銷活動的工作流程範本。

   >[!NOTE]
   >
   >此工作流程必須儲存為週期性工作流程範本。 要執行此操作，請編輯工作流程屬性並選取 **[!UICONTROL Recurring workflow template]** 中的選項 **[!UICONTROL Execution]** 標籤。

   ![](assets/s_ncs_user_op_template_recur_wf_option.png)

#### 建立週期性行銷活動 {#create-the-recurring-campaign}

若要建立週期性行銷活動，並根據範本中定義的排程執行其工作流程，請套用下列程式：

1. 根據週期性行銷活動範本建立新的行銷活動。
1. 填寫工作流程執行排程。

   ![](assets/s_ncs_user_op_recur_planning.png)

1. 行銷活動排程可讓您輸入每行的自動工作流程建立或執行開始日期。

   您可以為每行新增下列其他選項：

   * **[!UICONTROL To be approved]** ：可讓您在工作流程中強制傳送核准請求。
   * **[!UICONTROL To be started]** ：可讓您在到達開始日期時開始工作流程。

   此 **[!UICONTROL Create in advance for]** 欄位可讓您建立涵蓋輸入期間的所有工作流程。

   在執行 **[!UICONTROL Jobs on campaigns]** 工作流程，專用的工作流程會根據行銷活動排程中定義的發生次數來建立。 因此，會為每個執行日期建立工作流程。

1. 循環工作流程是從行銷活動中存在的工作流程範本自動建立。 它們可從以下位置顯示： **[!UICONTROL Targeting and workflows]** 行銷活動的索引標籤。

   ![](assets/s_ncs_user_op_recur_planning_wfs.png)

   循環工作流程例項的標籤由其範本標籤和工作流程編號組成，其中的#字元介於。

   從排程建立的工作流程會自動在 **[!UICONTROL Workflow]** 的欄 **[!UICONTROL Schedule]** 標籤。

   ![](assets/s_ncs_user_op_recur_planning_wfs_1.png)

   每個工作流程都可以從此索引標籤進行編輯。

   ![](assets/s_ncs_user_op_recur_planning_wf_edit.png)

   >[!NOTE]
   >
   >與工作流程相關之排程明細行的開始日期可從工作流程的變數取得，其語法如下：\
   >`$date(instance/vars/@startPlanningDate)`

### 建立定期行銷活動 {#creating-a-periodic-campaign}

定期行銷活動是根據特定範本的行銷活動，可讓您根據執行排程建立行銷活動執行個體。 系統會根據週期性行銷活動範本，根據範本排程中定義的頻率，自動建立行銷活動例項。

#### 建立行銷活動範本 {#creating-the-campaign-template-1}

1. 建立 **[!UICONTROL Periodic]** 行銷活動範本，最好是複製現有的行銷活動範本。

   ![](assets/s_ncs_user_op_template_period_create.png)

1. 輸入範本的屬性。

   >[!NOTE]
   >
   >指派範本的操作者需要具備在選定方案中建立行銷活動的適當許可權。

1. 建立與此範本關聯的工作流程。 範本建立的每個定期行銷活動都會複製該資料。

   ![](assets/s_ncs_user_op_template_period_wf.png)

   >[!NOTE]
   >
   >此工作流程是工作流程範本。 無法從行銷活動範本執行此動作。

1. 完成其對於週期性行銷活動範本的執行排程：按一下 **[!UICONTROL Add]** 按鈕並定義開始和結束日期，或透過連結填寫執行排程。

   ![](assets/s_ncs_user_op_template_period_planning_add.png)

   >[!IMPORTANT]
   >
   >定期行銷活動範本會根據上述定義的排程建立新的行銷活動。 因此，必須小心完成，以避免Adobe Campaign資料庫超載。

1. 一旦達到執行開始日期，就會自動建立相符的行銷活動。 它會使用其範本的所有特性。

   每個行銷活動都可透過範本排程進行編輯。

   ![](assets/s_ncs_user_op_template_period_planning.png)

每個定期行銷活動都包含相同的元素。 建立後，即作為標準行銷活動進行管理。

## 教學課程影片 {#video}

本影片說明如何建立行銷計畫、方案和行銷活動。

>[!VIDEO](https://video.tv.adobe.com/v/35132?quality=12)

提供其他Campaign操作說明影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).

---
product: campaign
title: 建立行銷活動
description: 了解如何建立和執行行銷活動
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
exl-id: a8fce21f-ffe3-4819-87ca-ac0ad9f21e41
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1253'
ht-degree: 6%

---

# 開始使用行銷活動{#setting-up-marketing-campaigns}

![](../../assets/common.svg)

行銷活動包括動作 (傳送) 和流程 (匯入或擷取檔案)，以及資源 (行銷文件、傳遞大綱)。 它們會用於行銷活動。 行銷活動是方案的一部分，而方案則包含在行銷活動計畫中。

![](assets/do-not-localize/how-to-video.png) 了解如何在影片中建立行銷計畫、計畫和行 [銷活動](#video)

若要建立行銷活動：

1. 建立促銷活動：探索行銷活動及其特點：標籤、類型、開始和結束日期、預算、關聯資源、經理和參與者。 [深入瞭解](#creating-a-campaign)。

1. 定義目標人口：使用定位查詢建立工作流程。 [深入瞭解](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)。

1. 建立傳送：選取頻道並定義要傳送的內容。 [深入瞭解](../../campaign/using/marketing-campaign-deliveries.md#creating-deliveries)。

1. 核准傳遞。 [深入瞭解](../../campaign/using/marketing-campaign-approval.md)。

1. 監視傳遞。 [深入瞭解](../../campaign/using/marketing-campaign-monitoring.md)。

1. 規劃促銷活動和相關成本。 [深入瞭解](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

完成這些步驟後，您可以開始傳送（請參閱[此區段](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)），檢查與傳送相關的資料、流程和資訊，並視需要管理相關檔案（請參閱[此區段](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)）。 您也可以追蹤促銷活動和傳送的處理階段的執行（請參閱[此區段](../../campaign/using/marketing-campaign-monitoring.md)）。

## 建立計畫和方案層次結構 {#creating-plan-and-program-hierarchy}

要為市場營銷計畫和方案配置資料夾層次結構：

1. 按一下首頁上的&#x200B;**瀏覽器**&#x200B;表徵圖。
1. 以滑鼠右鍵按一下您要建立計畫的資料夾。
1. 選取&#x200B;**新增資料夾>促銷活動管理>計畫**。

   ![](assets/create_plan_1.png)

1. 更名計畫。
1. 按一下右鍵新建立的計畫，然後選擇&#x200B;**屬性……**。

   ![](assets/create_plan_2.png)

1. 在&#x200B;**General**&#x200B;標籤中，修改&#x200B;**內部名稱**&#x200B;以避免在包導出期間出現重複。
1. 按一下「**儲存**」。
1. 按一下右鍵新建立的計畫，然後選擇&#x200B;**建立新的&#39;Program&#39;資料夾**。
1. 重複上述步驟，更名新程式資料夾及其內部名稱。

## 建立促銷活動 {#creating-a-campaign}

### 新增行銷活動 {#adding-a-campaign}

您可以透過促銷活動清單建立促銷活動。 若要顯示此檢視，請選取&#x200B;**[!UICONTROL Campaigns]**&#x200B;控制面板中的&#x200B;**[!UICONTROL Campaigns]**&#x200B;功能表。

![](assets/s_ncs_user_add_an_op_from_list.png)

**[!UICONTROL Program]**&#x200B;欄位可讓您選取要附加促銷活動的方案。 此資訊是強制性的。

![](assets/s_ncs_user_new_op_wz_a.png)

您也可以透過方案建立促銷活動。 要執行此操作，請按一下相關程式&#x200B;**[!UICONTROL Schedule]**&#x200B;頁簽中的&#x200B;**[!UICONTROL Add]**&#x200B;按鈕。

![](assets/s_ncs_user_add_an_op.png)

當您透過方案的&#x200B;**[!UICONTROL Schedule]**&#x200B;標籤建立促銷活動時，促銷活動會自動連結至相關的方案。 在此情況下， **[!UICONTROL Program]**&#x200B;欄位是隱藏的。

在促銷活動建立視窗中，選取促銷活動範本並新增促銷活動的名稱和說明。 您也可以指定促銷活動的開始和結束日期。

按一下&#x200B;**[!UICONTROL OK]**&#x200B;以建立促銷活動。 它會新增至方案排程。

![](assets/s_ncs_user_program_planning_with_op.png)

>[!NOTE]
>
>若要篩選要顯示的促銷活動，請按一下&#x200B;**[!UICONTROL Filter]**&#x200B;連結，並選取要顯示的促銷活動狀態。

![](assets/s_ncs_user_program_planning_filter.png)

### 編輯和設定促銷活動 {#editing-and-configuring-a-campaign}

然後，您可以編輯您剛建立的促銷活動並定義其參數。

若要開啟並設定促銷活動，請從排程中選取促銷活動，然後按一下&#x200B;**[!UICONTROL Open]**。

![](assets/s_ncs_user_new_op_edit.png)

這會帶您前往促銷活動控制面板。

## 週期性和定期的促銷活動 {#recurring-and-periodic-campaigns}

循環促銷活動是根據特定範本的促銷活動，其工作流程設定為根據關聯的排程執行。 因此，工作流程將會在促銷活動中重複執行。 目標定位會在每次執行時重複，且會追蹤各種程式和目標母體。 您也可以在自動工作流程建立期間，透過涵蓋期間預先執行未來目標設定，以便使用目標估計啟動模擬。

定期促銷活動是根據其範本的執行排程自動建立的促銷活動。

### 建立循環促銷活動 {#creating-a-recurring-campaign}

循環促銷活動是從定義要執行的工作流程範本和執行排程的特定範本建立。

#### 為循環促銷活動建立範本 {#creating-the-campaign-template}

1. 建立&#x200B;**[!UICONTROL Recurring]**&#x200B;促銷活動範本。

   >[!NOTE]
   >
   >建議您複製預設範本，而不要建立空白範本。

   ![](assets/s_ncs_user_op_template_recur_tab.png)

1. 輸入範本名稱和促銷活動期間。

   ![](assets/s_ncs_user_op_template_recur_duplicate.png)

1. 針對此類型的促銷活動，會新增&#x200B;**[!UICONTROL Schedule]**&#x200B;標籤以建立範本執行排程。

在此標籤中，根據此範本指定促銷活動的計畫執行日期。

![](assets/s_ncs_user_op_template_recur_planning.png)

執行調度的配置模式與工作流的&#x200B;**[!UICONTROL Scheduler]**&#x200B;對象一致。 如需詳細資訊，請參閱[本章節](../../workflow/using/architecture.md)。

>[!IMPORTANT]
>
>必須小心執行執行計畫配置，以避免資料庫過載。 根據指定的排程，循環促銷活動會複製其範本的工作流程。 執行過頻繁的工作流建立會阻礙資料庫的操作。

1. 在&#x200B;**[!UICONTROL Create in advance for]**&#x200B;欄位中指定值，以便為所指示的期間建立對應的工作流程。
1. 根據此範本，建立要用於促銷活動的工作流程範本，並搭配目標參數和一或多個一般傳送。

   >[!NOTE]
   >
   >此工作流程必須儲存為循環工作流程範本。 要執行此操作，請編輯工作流屬性，並在&#x200B;**[!UICONTROL Execution]**&#x200B;頁簽中選擇&#x200B;**[!UICONTROL Recurring workflow template]**&#x200B;選項。

   ![](assets/s_ncs_user_op_template_recur_wf_option.png)

#### 建立循環促銷活動 {#create-the-recurring-campaign}

若要根據範本中定義的排程建立週期性促銷活動並執行其工作流程，請套用下列程式：

1. 根據循環促銷活動範本建立新促銷活動。
1. 填入工作流程執行排程。

   ![](assets/s_ncs_user_op_recur_planning.png)

1. 促銷活動排程可讓您輸入每行的自動工作流程建立或執行開始日期。

   您可以為每行新增下列其他選項：

   * **[!UICONTROL To be approved]** :可讓您在工作流程中強制傳送核准請求。
   * **[!UICONTROL To be started]** :可讓您在達到開始日期時啟動工作流程。

   **[!UICONTROL Create in advance for]**&#x200B;欄位可讓您建立涵蓋所輸入期間的所有工作流程。

   執行&#x200B;**[!UICONTROL Jobs on campaigns]**&#x200B;工作流程時，會根據促銷活動排程中定義的發生次數，建立專用的工作流程。 因此，會為每個執行日期建立工作流程。

1. 循環工作流程會從行銷活動中出現的工作流程範本自動建立。 它們會從促銷活動的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤中顯示。

   ![](assets/s_ncs_user_op_recur_planning_wfs.png)

   循環工作流實例的標籤由其模板標籤和工作流編號組成，其中的#字元介於兩者之間。

   從排程建立的工作流程會自動與其在&#x200B;**[!UICONTROL Schedule]**&#x200B;標籤的&#x200B;**[!UICONTROL Workflow]**&#x200B;欄中相關聯。

   ![](assets/s_ncs_user_op_recur_planning_wfs_1.png)

   您可以從此索引標籤編輯每個工作流程。

   ![](assets/s_ncs_user_op_recur_planning_wf_edit.png)

   >[!NOTE]
   >
   >與工作流關聯的計畫行的開始日期可通過工作流的變數使用以下語法：\
   >`$date(instance/vars/@startPlanningDate)`

### 建立定期促銷活動 {#creating-a-periodic-campaign}

定期促銷活動是根據特定範本的促銷活動，可讓您根據執行排程建立促銷活動例項。 根據範本排程中定義的頻率，會根據定期促銷活動範本自動建立促銷活動例項。

#### 建立促銷活動範本 {#creating-the-campaign-template-1}

1. 建立&#x200B;**[!UICONTROL Periodic]**&#x200B;促銷活動範本，最好複製現有的促銷活動範本。

   ![](assets/s_ncs_user_op_template_period_create.png)

1. 輸入模板的屬性。

   >[!NOTE]
   >
   >將範本指派給的運算子，必須擁有在所選方案中建立促銷活動的適當權限。

1. 建立與此範本相關聯的工作流程。 此範本建立的每個定期促銷活動中都會重複該範本。

   ![](assets/s_ncs_user_op_template_period_wf.png)

   >[!NOTE]
   >
   >此工作流程是工作流程範本。 無法從促銷活動範本執行。

1. 完成循環促銷活動範本的執行排程：按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕並定義開始和結束日期，或透過連結填入執行排程。

   ![](assets/s_ncs_user_op_template_period_planning_add.png)

   >[!IMPORTANT]
   >
   >定期促銷活動範本會根據上述定義的排程建立新促銷活動。 因此，必須小心完成，以避免超載Adobe Campaign資料庫。

1. 一旦達到執行開始日期，就會自動建立相符的促銷活動。 它具有其模板的所有特性。

   可透過範本排程編輯每個促銷活動。

   ![](assets/s_ncs_user_op_template_period_planning.png)

每個定期促銷活動都包含相同的元素。 建立後，就會以標準促銷活動來管理。

## 教學課程影片 {#video}

此影片說明如何建立行銷計畫、方案和行銷活動。

>[!VIDEO](https://video.tv.adobe.com/v/35132?quality=12)

您可以在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得其他促銷活動作法影片。

---
product: campaign
title: Campaign 模擬
description: 開始使用Campaign模擬
role: User, Data Engineer
feature: Campaigns
exl-id: 709c64a8-34bf-43fa-a820-238295fb26b8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1245'
ht-degree: 2%

---

# Campaign 模擬{#campaign-simulations}

## 關於模擬 {#about-simulations}

行銷活動最佳化可讓您使用模擬來測試行銷活動計畫的效率。 這可讓您評估行銷活動的潛在成功：產生的收入、根據套用的型別規則的目標數量等。

模擬可讓您監控及比較傳送的影響。

>[!NOTE]
>
>在測試模式下準備的傳送彼此沒有影響，例如在分散式行銷中評估行銷活動時，或只要傳送未在臨時行事曆中排程。\
>這表示壓力和容量規則僅適用於&#x200B;**[!UICONTROL Target estimation and message personalization]**&#x200B;模式的傳遞。 未考慮&#x200B;**[!UICONTROL Estimation and approval of the provisional target]**&#x200B;和&#x200B;**[!UICONTROL Target evaluation]**&#x200B;模式中的傳遞。\
>在傳遞屬性的&#x200B;**[!UICONTROL Typology]**&#x200B;子索引標籤中選擇傳遞模式。

![](assets/simu_campaign_select_delivery_mode.png)

## 設定模擬 {#setting-up-a-simulation}

### 建立模擬 {#creating-a-simulation}

若要建立模擬，請套用下列步驟：

1. 開啟「**[!UICONTROL Campaigns]**」標籤，按一下「**[!UICONTROL Create]**」區段內的「**[!UICONTROL More]**」連結，然後選取「**[!UICONTROL Simulation]**」選項。

   ![](assets/simu_campaign_opti_01.png)

1. 輸入範本和模擬的名稱。 按一下&#x200B;**[!UICONTROL Save]**&#x200B;以建立模擬。

   ![](assets/simu_campaign_opti_02.png)

1. 按一下「**[!UICONTROL Edit]**」標籤以進行設定。

   ![](assets/simu_campaign_opti_edit.png)

1. 在&#x200B;**[!UICONTROL Scope]**&#x200B;索引標籤中，指定您要考慮用於此模擬的傳送。 若要這麼做，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，並指定要考慮的傳遞選擇模式。

   ![](assets/simu_campaign_opti_edit_scope.png)

   您可以逐一選取每個傳遞，或依行銷活動、方案或計畫排序。

   >[!NOTE]
   >
   >如果您透過計畫、方案或行銷活動選取傳送，Adobe Campaign會自動重新整理傳送清單，以便在模擬啟動時加以考慮。 若要這麼做，請核取&#x200B;**[!UICONTROL Refresh the selection of deliveries each time the simulation is started]**&#x200B;選項。
   >  
   >如果您不這麼做，則建立模擬時不會考慮計畫、方案或行銷活動中不可用的任何傳送：稍後新增的傳送將被忽略。

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. 選取要包含在模擬範圍內的元素。 如有必要，請使用SHIFT和CTRL鍵選取多個元素。

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以核准選取專案。

   您可以手動合併屬於計畫、方案或行銷活動的選定傳遞與傳遞。

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   如有必要，您可以透過&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;連結使用動態條件。

   按一下&#x200B;**[!UICONTROL Save]**&#x200B;以核准此組態。

   >[!NOTE]
   >
   >計算模擬時，只考慮已計算目標的傳遞（狀態： **目標就緒**&#x200B;或&#x200B;**準備傳遞**）。

1. 在&#x200B;**[!UICONTROL Calculations]**&#x200B;索引標籤中，選取分析維度，例如收件者綱要。

   ![](assets/simu_campaign_opti_dimension.png)

1. 然後，您可以新增運算式。

   ![](assets/simu_campaign_opti_dimension_02.png)

### 執行設定 {#execution-settings}

模擬的&#x200B;**[!UICONTROL General]**&#x200B;標籤可讓您輸入執行設定：

* 根據所選的優先順序層級，**[!UICONTROL Schedule execution for down-time]**&#x200B;選項會將模擬啟動延遲到較不繁忙的時間段。 例如，模擬會使用大量的資料庫資源，因此非緊急模擬應該排程在夜間執行。
* **[!UICONTROL Priority]**&#x200B;是套用到模擬以延遲其觸發的層級。
* **[!UICONTROL Save SQL queries in the log]**。 SQL記錄檔可讓您在模擬結束時診斷錯誤。 它們也可以幫助您找出模擬太慢的原因。 在&#x200B;**[!UICONTROL Audit]**&#x200B;標籤的&#x200B;**[!UICONTROL SQL logs]**&#x200B;子標籤中進行模擬後，這些訊息將會顯示。

## 執行模擬 {#executing-a-simulation}

### 開始模擬 {#starting-a-simulation}

定義模擬範圍後，即可執行。

若要這麼做，請開啟模擬儀表板，然後按一下&#x200B;**[!UICONTROL Start simulation]**。

![](assets/simu_campaign_opti_start.png)

執行完成後，請開啟模擬，然後按一下&#x200B;**[!UICONTROL Results]**&#x200B;標籤以檢視針對每個傳遞計算的目標。

![](assets/simu_campaign_opti_results.png)

1. **[!UICONTROL Deliveries]**&#x200B;子標籤會列出模擬所考慮的所有傳遞。 它會顯示兩個計數：

   * **[!UICONTROL Initial count]**&#x200B;是在傳遞中的估計期間所計算的目標。
   * **[!UICONTROL Final count]**&#x200B;是模擬後計數的收件者數目。

     初始計數和最終計數之間的差異，反映了模擬之前設定的各種規則或篩選器的套用。

     若要深入瞭解此計算，請編輯&#x200B;**[!UICONTROL Exclusions]**&#x200B;子標籤。

1. **[!UICONTROL Exclusions]**&#x200B;子標籤可讓您檢視排除專案劃分資訊。

   ![](assets/simu_campaign_opti_14.png)

1. **[!UICONTROL Alerts]**&#x200B;子索引標籤會將模擬期間產生的所有警示訊息分組。 在容量超載時（例如，如果鎖定的收件者人數超過設定的容量），可以傳送警報訊息。
1. **[!UICONTROL Exploration of the exclusions]**&#x200B;子標籤可讓您建立結果分析表格。 使用者需要在橫截面/縱座標軸中指出變數。

   如需建立分析表格的範例，請參閱[瀏覽結果](#exploring-results)的結尾。

### 檢視結果 {#viewing-results}

#### 稽核 {#audit}

**[!UICONTROL Audit]**&#x200B;索引標籤可讓您監視模擬執行。 **[!UICONTROL SQL Logs]**&#x200B;子標籤對專家使用者很有用。 它以SQL格式列出執行記錄。 只有在模擬執行前已在&#x200B;**[!UICONTROL General]**&#x200B;索引標籤中選取&#x200B;**[!UICONTROL Save SQL queries in the log]**&#x200B;選項時，才會顯示這些記錄。

![](assets/simu_campaign_opti_11.png)

#### 探索結果 {#exploring-results}

**[!UICONTROL Exploration of the exclusions]**&#x200B;子標籤可讓您分析模擬產生的資料。

描述性分析在[本節](../../reporting/using/about-adobe-campaign-reporting-tools.md)中有詳細說明。

## 模擬的結果 {#results-of-a-simulation}

**[!UICONTROL Log]**&#x200B;和&#x200B;**[!UICONTROL Results]**&#x200B;索引標籤中的指標提供模擬結果的第一個概觀。 如需結果的詳細檢視，請開啟&#x200B;**[!UICONTROL Reports]**&#x200B;標籤。

### 報告 {#reports}

若要分析模擬的結果，請編輯其報表：顯示排除專案和原因。

預設會提供下列報表：

* **[!UICONTROL Detail of simulation exclusions]** ：此報表提供所有相關傳遞的排除原因詳細圖表。
* **[!UICONTROL Simulation summary]** ：此報表會顯示從各種傳送的模擬中排除的母體。
* **[!UICONTROL Summary of exclusions linked to the simulation]** ：此報表顯示模擬導致的排除圖表、套用的型別規則，以及顯示每個規則的排除率的圖表。

>[!NOTE]
>
>您可以建立新報告，並將其新增至所提供的報告。 如需詳細資訊，請參閱[本章節](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

若要存取報告，透過目標模擬的儀表板，按一下該模擬的&#x200B;**[!UICONTROL Reports]**&#x200B;連結。

![](assets/campaign_opt_reporting_edit_from_board.png)

您也可以使用可從模擬控制面板存取的&#x200B;**[!UICONTROL Reports]**&#x200B;連結來編輯報告。

### 比較模擬 {#comparing-simulations-}

每次執行模擬時，結果都會取代之前的任何結果：您無法顯示和比較從一個執行到另一個執行的結果。

若要比較結果，必須使用報表。 事實上，Adobe Campaign可讓您儲存報表歷史記錄，以便稍後再次檢視。 此歷史記錄會在模擬的整個生命週期中儲存。

**範例：**

1. 在套用型別&#x200B;**A**&#x200B;的傳遞上建立模擬。
1. 在&#x200B;**[!UICONTROL Reports]**&#x200B;標籤中，編輯其中一個可用的報告，例如&#x200B;**[!UICONTROL Detail of simulation exclusions]**。
1. 在報表的右上角，按一下圖示以建立新的歷史記錄。

   ![](assets/campaign_opt_reporting_create_hist.png)

1. 關閉模擬並變更型別&#x200B;**A**&#x200B;的設定。
1. 再次執行模擬，並將結果與建立歷史記錄之報表中顯示的結果進行比較。

   ![](assets/campaign_opt_reporting_edit_hist.png)

   您可以視需要儲存儘可能多的報表歷史記錄。

### 報告軸 {#reporting-axes}

**[!UICONTROL Calculations]**&#x200B;索引標籤可讓您定義目標上的報告軸。 這些軸將在結果分析期間使用（請參閱[探索結果](#exploring-results)）。

>[!NOTE]
>
>我們建議在模擬範本中定義計算軸，而不是為每個模擬分別定義計算軸。\
>模擬範本儲存在Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Resources > Templates > Simulation templates]**&#x200B;節點中。

**範例：**

在以下範例中，我們要根據收件者的狀態（「客戶」、「潛在客戶」或無）建立額外的報告軸。

1. 若要定義報表座標軸，請選取包含要在&#x200B;**[!UICONTROL Analysis dimension]**&#x200B;欄位中處理之資訊的表格。 此資訊是強制性的。
1. 在此，我們要選取收件者表格的「區段」欄位。

   ![](assets/simu_campaign_opti_09.png)

1. 可以使用以下選項：

   * **[!UICONTROL Generate target overlap statistics]**&#x200B;可讓您復原模擬報告中的所有重疊統計資料。 重疊是在一個模擬中至少兩次傳遞鎖定的收件者。

     >[!IMPORTANT]
     >
     >選取此選項會大幅增加模擬執行時間。

   * **[!UICONTROL Keep the simulation work table]**&#x200B;可讓您保留模擬追蹤。

     >[!IMPORTANT]
     >
     >自動儲存這些表格需要相當的儲存容量：請確定資料庫夠大。

顯示模擬結果時，所選運算式的資訊將顯示在&#x200B;**[!UICONTROL Overlaps]**&#x200B;子標籤中。

傳遞目標重疊表示在至少兩次模擬傳遞中的目標收件者。

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>此子索引標籤只有在已啟用&#x200B;**[!UICONTROL Generate target recovery statistics]**&#x200B;選項時才會顯示。

報表軸上的資訊可在&#x200B;**[!UICONTROL Exploring exclusions]**&#x200B;子標籤中建立的排除分析報表中處理。 如需詳細資訊，請參閱[探索結果](#exploring-results)。

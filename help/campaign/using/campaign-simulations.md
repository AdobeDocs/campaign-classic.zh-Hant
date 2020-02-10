---
title: 促銷活動模擬
seo-title: 促銷活動模擬
description: 促銷活動模擬
seo-description: null
page-status-flag: never-activated
uuid: d5a090ef-57e5-46b2-b9ad-6d4d964c8e20
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: e8e7a720-c93d-491d-8768-270e47e9c898
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 促銷活動模擬{#campaign-simulations}

## 關於模擬 {#about-simulations}

促銷活動最佳化可讓您使用模擬來測試促銷活動計畫的效率。 這可讓您測量促銷活動的潛在成功：產生的收入、根據套用的類型學規則設定的目標量等。

模擬可讓您監控和比較傳送的影響。

>[!NOTE]
>
>在「測試」模式下準備的傳送不會彼此影響，例如，在分佈式行銷中評估促銷活動時，或只要傳送未排程在臨時日曆中。\
>這表示壓力和容量規則僅適用於模式下的交貨 **[!UICONTROL Target estimation and message personalization]** 。 不會考 **[!UICONTROL Estimation and approval of the provisional target]** 慮在和 **[!UICONTROL Target evaluation]** 模式下的交貨。\
>傳送模式是在傳送屬性 **[!UICONTROL Typology]** 的子標籤中選擇。

![](assets/simu_campaign_select_delivery_mode.png)

## 設定模擬 {#setting-up-a-simulation}

### 建立模擬 {#creating-a-simulation}

要建立模擬，請應用以下步驟：

1. 前往宇宙 **[!UICONTROL Campaigns]** ，按一下區段 **[!UICONTROL More]** 中的連結， **[!UICONTROL Create]** 並選取 **[!UICONTROL Simulation]** 選項。

   ![](assets/simu_campaign_opti_01.png)

1. 輸入模板和模擬的名稱。 按一下 **[!UICONTROL Save]** 建立模擬。

   ![](assets/simu_campaign_opti_02.png)

1. 按一下 **[!UICONTROL Edit]** 標籤以進行設定。

   ![](assets/simu_campaign_opti_edit.png)

1. 在標籤 **[!UICONTROL Scope]** 中，指定您要為此模擬考慮的傳送。 若要這麼做，請按一 **[!UICONTROL Add]** 下按鈕並指定要考慮的傳送選擇模式。

   ![](assets/simu_campaign_opti_edit_scope.png)

   您可以逐一選擇每個傳送，或依促銷活動、方案或計畫排序。

   >[!NOTE]
   >
   >如果您透過計畫、方案或促銷活動選取傳送，Adobe Campaign會自動重新整理傳送清單，以便在模擬啟動時加以考慮。 若要這麼做，請勾選 **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** 選項。
   >  
   >如果您不這樣做，在建立模擬時，計畫、方案或促銷活動中不提供的任何傳送都不會納入考量：稍後新增的傳送將會被忽略。

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. 選擇要包括在模擬範圍中的元素。 如有必要，請使用SHIFT和CTRL鍵選取多個元素。

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   按一 **[!UICONTROL Finish]** 下以核准選擇。

   您可以人工合併屬於計畫、方案或促銷活動的選定交貨和交貨。

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   如有必要，您可以透過連結使用動態條 **[!UICONTROL Edit the dynamic condition...]** 件

   按一 **[!UICONTROL Save]** 下以核准此設定。

   >[!CAUTION]
   >
   >計算模擬時，只會考慮已計算目標的傳送(狀態：Target **就緒** , **或就緒交付**)。

1. 在標籤 **[!UICONTROL Calculations]** 中，選擇分析維，例如收件人方案。

   ![](assets/simu_campaign_opti_dimension.png)

1. 然後，您可以新增運算式。

   ![](assets/simu_campaign_opti_dimension_02.png)

### 執行設定 {#execution-settings}

模 **[!UICONTROL General]** 擬的頁籤可讓您輸入執行設定：

* 選 **[!UICONTROL Schedule execution for down-time]** 項會根據選擇的優先順序，將模擬啟動定義為較不繁忙的時段。 例如，模擬使用大量資料庫資源，因此非緊急模擬應排程在夜間執行。
* 是 **[!UICONTROL Priority]** 應用於模擬以延遲其觸發的級別。
* **[!UICONTROL Save SQL queries in the log]**. SQL日誌可讓您診斷模擬是否以錯誤結束。 它們也可協助您瞭解模擬為何太慢。 這些消息在模擬後會顯示在頁籤 **[!UICONTROL SQL logs]** 的子頁籤中 **[!UICONTROL Audit]** 。

## 執行模擬 {#executing-a-simulation}

### 啟動模擬 {#starting-a-simulation}

一旦定義了模擬範圍，就可以執行它。

若要這麼做，請開啟模擬控制面板，然後按一下 **[!UICONTROL Start simulation]**。

![](assets/simu_campaign_opti_start.png)

執行完成後，開啟模擬並按一下標 **[!UICONTROL Results]** 簽，檢視針對每個傳送計算的目標。

![](assets/simu_campaign_opti_results.png)

1. 子標 **[!UICONTROL Deliveries]** 簽會列出模擬所考慮的所有交貨。 它顯示了兩個計數：

   * 目標 **[!UICONTROL Initial count]** 是在交付時估計目標時計算的目標。
   * 是 **[!UICONTROL Final count]** 經過模擬計算的收件者數。

      初始計數和最終計數之間的差異反映了在模擬之前配置的各種規則或過濾器的應用。

      若要進一步瞭解此計算，請編輯 **[!UICONTROL Exclusions]** 子標籤。

1. 子標 **[!UICONTROL Exclusions]** 簽可讓您檢視排除劃分。

   ![](assets/simu_campaign_opti_14.png)

1. 子選 **[!UICONTROL Alerts]** 項卡將模擬期間生成的所有警報消息分組。 在容量超負荷時（例如，如果目標接收者數量超過設定容量），可以發送警報消息。
1. 子標 **[!UICONTROL Exploration of the exclusions]** 簽可讓您建立結果分析表格。 使用者需要在橫坐標／縱坐標軸中指定變數。

   有關建立分析表的示例，請參閱「瀏覽結果」( [Exploring results)的結尾](#exploring-results)。

### 檢視結果 {#viewing-results}

#### 審計 {#audit}

此標 **[!UICONTROL Audit]** 簽可讓您監控模擬執行。 子標 **[!UICONTROL SQL Logs]** 簽對專家用戶非常有用。 它以SQL格式列出執行日誌。 僅當在模擬執行之前在選 **[!UICONTROL Save SQL queries in the log]** 項卡中選擇了該選 **[!UICONTROL General]** 項時，才會顯示這些日誌。

![](assets/simu_campaign_opti_11.png)

#### 探索成果 {#exploring-results}

子標 **[!UICONTROL Exploration of the exclusions]** 簽可讓您分析模擬產生的資料。

本節將詳述描述 [性分析](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

## 模擬結果 {#results-of-a-simulation}

標籤和標籤中 **[!UICONTROL Log]** 的指 **[!UICONTROL Results]** 示器提供模擬結果的第一個概述。 如需結果的更詳細檢視，請開啟標 **[!UICONTROL Reports]** 簽。

### 報表 {#reports}

若要分析模擬結果，請編輯其報表：它們顯示排除和原因。

預設會提供下列報表：

* **[!UICONTROL Detail of simulation exclusions]** :此報告提供所有相關傳送之排除原因的詳細圖表。
* **[!UICONTROL Simulation summary]** :此報表顯示不同傳送期間，從模擬中排除的人口。
* **[!UICONTROL Summary of exclusions linked to the simulation]** :此報表顯示模擬造成的排除圖表，以及套用的排除類型規則，以及每個規則的排除率圖表。

>[!NOTE]
>
>您可以建立新報表，並將其新增至提供的報表。 如需詳細資訊，請參閱[本小節](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

若要存取報表，請透過其控 **[!UICONTROL Reports]** 制面板按一下目標模擬的連結。

![](assets/campaign_opt_reporting_edit_from_board.png)

您也可以使用可從模擬控制面板 **[!UICONTROL Reports]** 存取的連結來編輯報表。

### 比較模擬 {#comparing-simulations-}

每次執行模擬時，結果會取代任何先前的結果：您無法顯示和比較執行之間的結果。

若要比較結果，您必須使用報表。 事實上，Adobe Campaign可讓您儲存報表歷史記錄，以便稍後再檢視。 在模擬的整個生命週期中都會儲存此歷史記錄。

**例如：**

1. 建立套用類型學 **A的傳送** 模擬。
1. 在標籤 **[!UICONTROL Reports]** 中，編輯其中一個可用報表，例如 **[!UICONTROL Detail of simulation exclusions]** 編輯。
1. 在報表的右上方區段中，按一下圖示以建立新的歷史記錄。

   ![](assets/campaign_opt_reporting_create_hist.png)

1. 關閉模擬並變更類型學 **A的設定**。
1. 再次執行模擬，並將結果與報告中顯示的結果進行比較，該報告中已為其建立歷史記錄。

   ![](assets/campaign_opt_reporting_edit_hist.png)

   您可以視需要儲存多份報表記錄。

### 報告軸 {#reporting-axes}

此標 **[!UICONTROL Calculations]** 簽可讓您定義目標上的報告軸。 這些軸將在結果分析期間使用(請參 [閱瀏覽結果](#exploring-results))。

>[!NOTE]
>
>我們建議在模擬範本中定義計算軸，而不是針對每個模擬分別定義。\
>模擬範本會儲存在Adobe **[!UICONTROL Resources > Templates > Simulation templates]** Campaign樹狀結構的節點中。

**例如：**

在以下範例中，我們想根據收件者的狀態（「客戶」、「潛在客戶」或無）來建立其他報表軸。

1. 要定義報告軸，請選擇包含要在欄位中處理的資訊的 **[!UICONTROL Analysis dimension]** 表。 此資訊是強制性的。
1. 在此，我們要選取收件者表格的「區段」欄位。

   ![](assets/simu_campaign_opti_09.png)

1. 可以使用以下選項：

   * **[!UICONTROL Generate target overlap statistics]** 可讓您復原模擬報表中的所有重疊統計資料。 重疊是在一個模擬中定位至少兩個傳送的接收者。

      >[!CAUTION]
      >
      >選取此選項可大幅增加模擬執行時間。

   * **[!UICONTROL Keep the simulation work table]** 讓你保留模擬痕跡。

      >[!CAUTION]
      >
      >自動保存這些表需要大量儲存容量：確保資料庫足夠大。

顯示模擬結果時，所選表達式的資訊將顯示在子選 **[!UICONTROL Overlaps]** 項卡中。

傳送目標重疊在模擬的至少兩個傳送中指明目標接收者。

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>此子標籤僅在啟用選項 **[!UICONTROL Generate target recovery statistics]** 時顯示。

在子標籤中建立的排除分析報表中，可處理有關報表軸 **[!UICONTROL Exploring exclusions]** 的資訊。 For more on this, refer to [Exploring results](#exploring-results).

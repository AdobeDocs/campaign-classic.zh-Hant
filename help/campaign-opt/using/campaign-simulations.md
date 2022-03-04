---
product: campaign
title: Campaign 模擬
description: 開始活動模擬
feature: Campaigns
exl-id: 709c64a8-34bf-43fa-a820-238295fb26b8
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '1245'
ht-degree: 2%

---

# Campaign 模擬{#campaign-simulations}

![](../../assets/common.svg)

## 關於模擬 {#about-simulations}

市場活動優化允許您使用模擬test市場活動計畫的效率。 這允許您衡量市場活動的潛在成功：生成的收入、基於所應用的類型規則的目標數量等。

模擬可監視和比較交貨的影響。

>[!NOTE]
>
>以Test模式準備的交貨對彼此沒有影響，例如，在分佈式市場營銷中評估市場活動時，或只要臨時日曆中沒有計畫交貨。\
>這意味著壓力和能力規則僅適用於 **[!UICONTROL Target estimation and message personalization]** 的子菜單。 交貨時間 **[!UICONTROL Estimation and approval of the provisional target]** 在 **[!UICONTROL Target evaluation]** 模式未被考慮。\
>在 **[!UICONTROL Typology]** 頁籤。

![](assets/simu_campaign_select_delivery_mode.png)

## 設定模擬 {#setting-up-a-simulation}

### 建立模擬 {#creating-a-simulation}

要建立模擬，請應用以下步驟：

1. 開啟 **[!UICONTROL Campaigns]** 頁籤 **[!UICONTROL More]** 連結 **[!UICONTROL Create]** 的 **[!UICONTROL Simulation]** 的雙曲餘切值。

   ![](assets/simu_campaign_opti_01.png)

1. 輸入模板和模擬的名稱。 按一下 **[!UICONTROL Save]** 建立模擬。

   ![](assets/simu_campaign_opti_02.png)

1. 按一下 **[!UICONTROL Edit]** 頁籤。

   ![](assets/simu_campaign_opti_edit.png)

1. 在 **[!UICONTROL Scope]** 頁籤，指定要為此模擬考慮的交貨。 要執行此操作，請按一下 **[!UICONTROL Add]** 按鈕並指定要考慮的傳遞選擇模式。

   ![](assets/simu_campaign_opti_edit_scope.png)

   您可以逐個選擇每個交貨，或按市場活動、方案或計畫對其排序。

   >[!NOTE]
   >
   >如果您通過計畫、方案或市場活動選擇交貨，Adobe Campaign可以自動刷新交貨清單，以便在模擬啟動時考慮交貨。 要執行此操作，請檢查 **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** 的雙曲餘切值。
   >  
   >如果您不這樣做，則在建立模擬時，計畫、方案或市場活動中不可用的任何交貨將不被考慮在內：以後添加的交貨將被忽略。

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. 選擇要包括在模擬範圍中的元素。 如有必要，請使用SHIFT和CTRL鍵選取多個元素。

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   按一下 **[!UICONTROL Finish]** 的子菜單。

   您可以人工合併屬於計畫、方案或市場活動的選定交貨和交貨。

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   如有必要，可通過 **[!UICONTROL Edit the dynamic condition...]** 的子菜單。

   按一下 **[!UICONTROL Save]** 以批准此配置。

   >[!NOTE]
   >
   >計算模擬時，只考慮已計算目標的交貨(狀態： **目標就緒** 或 **準備交付**)。

1. 在 **[!UICONTROL Calculations]** 頁籤，選擇分析維，例如收件人方案。

   ![](assets/simu_campaign_opti_dimension.png)

1. 然後可以添加表達式。

   ![](assets/simu_campaign_opti_dimension_02.png)

### 執行設定 {#execution-settings}

的 **[!UICONTROL General]** 頁籤，您可以輸入執行設定：

* 的 **[!UICONTROL Schedule execution for down-time]** 選項根據所選優先順序將模擬啟動延遲到較短的忙時段。 模擬使用大量資料庫資源，這就是為什麼非緊急模擬應安排在夜間運行。
* 的 **[!UICONTROL Priority]** 是用於模擬以延遲其觸發的級別。
* **[!UICONTROL Save SQL queries in the log]**。 SQL日誌允許您診斷模擬（如果模擬以錯誤結尾）。 它們還可以幫助你找出模擬速度太慢的原因。 這些消息在中的模擬後可見 **[!UICONTROL SQL logs]** 頁籤 **[!UICONTROL Audit]** 頁籤。

## 執行模擬 {#executing-a-simulation}

### 啟動模擬 {#starting-a-simulation}

定義模擬範圍後，即可執行它。

要執行此操作，請開啟模擬操控板並按一下 **[!UICONTROL Start simulation]**。

![](assets/simu_campaign_opti_start.png)

執行完成後，開啟模擬並按一下 **[!UICONTROL Results]** 頁籤，查看為每個交貨計算的目標。

![](assets/simu_campaign_opti_results.png)

1. 的 **[!UICONTROL Deliveries]** 子頁籤列出模擬所考慮的所有交貨。 它顯示了兩種情況：

   * 的 **[!UICONTROL Initial count]** 是在交付時估計時計算的目標。
   * 的 **[!UICONTROL Final count]** 是模擬後計數的收件人數。

      初始計數和最終計數之間的差異反映了在模擬之前配置的各種規則或過濾器的應用。

      要瞭解有關此計算的詳細資訊，請編輯 **[!UICONTROL Exclusions]** 的子菜單。

1. 的 **[!UICONTROL Exclusions]** 的子菜單。

   ![](assets/simu_campaign_opti_14.png)

1. 的 **[!UICONTROL Alerts]** 子頁籤將模擬期間生成的所有警報消息分組。 在容量超載時（例如，如果目標接收者數量超過設定的容量），可以發送警報消息。
1. 的 **[!UICONTROL Exploration of the exclusions]** 頁籤，用於建立結果分析表。 用戶需要在橫坐標/縱坐標軸中指示變數。

   有關建立分析表的示例，請參閱 [瀏覽結果](#exploring-results)。

### 查看結果 {#viewing-results}

#### 審計 {#audit}

的 **[!UICONTROL Audit]** 頁籤，用於監視模擬執行。 的 **[!UICONTROL SQL Logs]** 子頁籤對專家用戶非常有用。 它列出SQL格式的執行日誌。 僅當 **[!UICONTROL Save SQL queries in the log]** 中 **[!UICONTROL General]** 頁籤。

![](assets/simu_campaign_opti_11.png)

#### 瀏覽結果 {#exploring-results}

的 **[!UICONTROL Exploration of the exclusions]** 子頁籤，用於分析由模擬產生的資料。

描述性分析在 [此部分](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

## 模擬結果 {#results-of-a-simulation}

中的指標 **[!UICONTROL Log]** 和 **[!UICONTROL Results]** 頁籤提供模擬結果的首次概述。 有關結果的更詳細視圖，請開啟 **[!UICONTROL Reports]** 頁籤。

### 報告 {#reports}

要分析模擬結果，請編輯其報告：它們顯示出排他性和原因。

預設情況下提供以下報告：

* **[!UICONTROL Detail of simulation exclusions]** :此報告提供了所有有關交貨的排除原因的詳細圖表。
* **[!UICONTROL Simulation summary]** :此報告顯示了在各種交貨期間從模擬中排除的人口。
* **[!UICONTROL Summary of exclusions linked to the simulation]** :此報表顯示模擬導致的排除的圖表以及應用的類型規則，以及顯示每個規則的排除率的圖表。

>[!NOTE]
>
>您可以建立新報告並將其添加到提供的報告中。 如需詳細資訊，請參閱[本章節](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

要訪問報告，請按一下 **[!UICONTROL Reports]** 目標模擬的連結。

![](assets/campaign_opt_reporting_edit_from_board.png)

您還可以使用 **[!UICONTROL Reports]** 可從模擬儀表板訪問的連結。

### 比較模擬 {#comparing-simulations-}

每次執行模擬時，結果將替換以前的任何結果：無法顯示結果並將結果從一個執行到另一個執行。

要比較結果，您需要使用報告。 事實上，Adobe Campaign允許您保存報告歷史記錄以在以後再次查看。 這一歷史在整個模擬生命週期中都得以保存。

**範例:**

1. 在類型的交貨上建立模擬 **A** 中。
1. 在 **[!UICONTROL Reports]** 頁籤，編輯其中一個可用報表，如 **[!UICONTROL Detail of simulation exclusions]** 例如。
1. 在報告的右上部分，按一下該表徵圖以建立新歷史記錄。

   ![](assets/campaign_opt_reporting_create_hist.png)

1. 關閉模擬並更改類型配置 **A**。
1. 再次執行模擬，並將結果與建立歷史記錄的報告中顯示的結果進行比較。

   ![](assets/campaign_opt_reporting_edit_hist.png)

   您可以根據需要保存盡可能多的報告歷史記錄。

### 報告軸 {#reporting-axes}

的 **[!UICONTROL Calculations]** 頁籤中，您可以定義目標上的報告軸。 在結果分析期間將使用這些軸(請參閱 [瀏覽結果](#exploring-results))。

>[!NOTE]
>
>我們建議在模擬模板中定義計算軸，而不是為每個模擬分別定義計算軸。\
>模擬模板保存在 **[!UICONTROL Resources > Templates > Simulation templates]** Adobe Campaign樹的節點。

**範例:**

在下面的示例中，我們要根據接收人的狀態（「客戶」、「潛在客戶」或「無」）建立附加報告軸。

1. 要定義報表軸，請選擇包含要在 **[!UICONTROL Analysis dimension]** 的子菜單。 此資訊是強制性的。
1. 在此，我們要選擇收件人表的段欄位。

   ![](assets/simu_campaign_opti_09.png)

1. 可以使用以下選項：

   * **[!UICONTROL Generate target overlap statistics]** 用於恢復模擬報告中的所有重疊統計資訊。 重疊是在一個模擬中以至少兩個遞送為目標的接收者。

      >[!IMPORTANT]
      >
      >選擇此選項會大大增加模擬執行時間。

   * **[!UICONTROL Keep the simulation work table]** 讓你保持模擬跟蹤。

      >[!IMPORTANT]
      >
      >自動保存這些表需要大量儲存容量：確保資料庫足夠大。

顯示模擬結果時，所選表達式的資訊將顯示在 **[!UICONTROL Overlaps]** 的子菜單。

傳遞目標重疊表示在模擬的至少兩個傳遞中的目標接收者。

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>僅當 **[!UICONTROL Generate target recovery statistics]** 選項。

有關報告軸的資訊可以在在 **[!UICONTROL Exploring exclusions]** 的子菜單。 有關此內容的詳細資訊，請參閱 [瀏覽結果](#exploring-results)。

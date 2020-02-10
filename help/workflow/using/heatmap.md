---
title: Workflow HeatMap
seo-title: Workflow HeatMap
description: Workflow HeatMap
seo-description: null
page-status-flag: never-activated
uuid: 4d215ff4-a61d-4294-8f15-17c612022577
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 6a71f5ee-c8e0-4ac4-acae-6dffbf799d0c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d6a4d56c595f16f454684b1d6afc7d7323c5914c

---


# Workflow HeatMap {#workflow-heatmap}

Adobe Campaign Workflow HeatMap包含目前執行之所有工作流程的色彩編碼圖形表示法。 它僅適用於實例管理員。

本頁提供其他監控不同促銷活動程式的 [方式](https://helpx.adobe.com/campaign/kb/acc-maintenance.html)。

## 關於Workflow HeatMap {#about-the-workflow-heatmap}

Workflow HeatMap提供並行工作流程數目的快速概覽，讓Adobe Campaign平台管理員可監控執行個體的負載情況，並據此規劃工作流程。

更精確地說，它可協助平台管理員：

* 檢視並瞭解並行工作流程
* 依期間篩選工作流程，以查看哪些工作流程可能遇到問題
* 依期間篩選活動，以查看哪些活動可能遇到問題
* 輕鬆尋找個別工作流程和所有相關活動（包括其持續時間）
* 依工作流程類型搜尋(技[術工作流程](../../workflow/using/building-a-workflow.md#technical-workflows) 或促 [銷活動工作流程](../../workflow/using/building-a-workflow.md#campaign-workflows))
* 尋找要分析的特定工作流程

>[!NOTE]
>
>除了「工作流熱 **圖」外**，您還可以建立工作流程，讓您監控一組工作流程的狀態，並傳送循環訊息給主管。 For more on this, refer to the [dedicated section](../../workflow/using/supervising-workflows.md).

使用Workflow HeatMap需要對下列概念有充分的瞭解：工作 [流程](../../workflow/using/about-workflows.md)、活 [動](../../workflow/using/about-activities.md)[和工作流最佳實務](../../workflow/using/workflow-best-practices.md)。

Adobe Campaign 18.10版本預設提供Workflow HeatMap。 如果您的組建版本介於8700和8977(18.10)之間，您也可以受益於此功能。 若要要求相應的套件，請聯絡 [Adobe客戶服務](https://support.neolane.net/) ，並依照本頁 [的指示](https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html) ，瞭解如何安裝它。

當您第一次存取Worklow HeatMap時，會出現下列快顯視窗。 本合約允許Adobe Campaign在美國的轉讓和儲存，以便：

* 監視實例以調查任何效能問題。
* 收集異常偵測的資料。

請注意，您的資料傳輸僅適用於使用其Adobe ID連線至Adobe Campaign的使用者。

![](assets/wf_monitoring_agreement.png)

有三個選項可供使用：

* **[!UICONTROL Accept]** :接受本合約後，您即授權Adobe Campaign收集您的資料，並將其傳輸至美國，以便在異常偵測時提供協助。
* **[!UICONTROL Refuse]** :拒絕合約後，您的資料將不會傳輸，但您仍可使用「工作流程熱圖」。
* **[!UICONTROL Do not show this message again]** :按一 **[!UICONTROL Do not show this message again]** 下，當存取「工作流程熱圖」時，快顯視窗將停止顯示，但仍可從按鈕 **[!UICONTROL Term of use]** 使用。

這個選項並非最終選項，您隨時都可以按一下按鈕加以 **[!UICONTROL Term of use]** 變更。

## 使用HeatMap {#using-the-heatmap}

>[!NOTE]
>
>只有具有管理權限的使用者才能存取促銷活動工作流程熱圖。

1. 前往並 **[!UICONTROL Monitoring]** 按一下連 **[!UICONTROL Workflow HeatMap]** 結以顯示頁 **[!UICONTROL Campaign Workflow HeatMap]** 面。

   ![](assets/wkf_monitoring_path.png)

1. 按一下日曆以選取日。

   依預設，頁面會顯示當天的工作流程活動。 您可以變更它，並選取過去的任何一天。

   >[!NOTE]
   >
   >只有未被工作流刪除的工作流 **[!UICONTROL Database cleanup]** 才可見。 有關資料庫清理工作流的詳細資訊，請參 [閱本節](../../production/using/database-cleanup-workflow.md)。\
   >預設情況下，Workflow HeatMap時區是為當前管理員用戶定義的時區。 例如，如果您與您所使用的行銷使用者不在相同的區域，您可能會想要變更它。

1. Click the **[!UICONTROL Filters]** button.

   ![](assets/wkf_monitoring_filters.png)

1. 使用滑桿將最短持續時間從0秒設定為1小時。 這可讓您只搜尋執行超過特定秒數或分鐘的工作流程。

   ![](assets/wkf_monitoring_filters_duration.png)

1. 您也可以從清單中選擇特定的工作 **[!UICONTROL Workflows]** 流程。

   ![](assets/wkf_monitoring_filters_workflows.png)

   >[!NOTE]
   >
   >會套 **[!UICONTROL Min duration]** 用篩選。 如果您找不到特定的工作流程，請將最短持續時間重設為0，如此清單中就會顯示所有工作流程。

1. 您也可以篩選 **[!UICONTROL Workflow type]** :

   * **[!UICONTROL Technical]** :只 [會顯示現成可用的技術工作流程](../../workflow/using/building-a-workflow.md#technical-workflows) ，以 [及資料管理工作流程](../../workflow/using/targeting-data.md#data-management) 。
   * **[!UICONTROL Marketing]** :只會顯示連結至行銷促銷活動的工 [作流程](../../workflow/using/building-a-workflow.md#campaign-workflows)，稱為促銷活動工作流程。

1. 要按名稱搜索特定工作流，您也可以使用該 **[!UICONTROL Workflow name filter]** 欄位。

   ![](assets/wkf_monitoring_filters_name.png)

1. 如果您在其間編輯了某些工作流程，請按一 **[!UICONTROL Reload data]** 下按鈕以重新整理顯示在格線中的資料。

## 閱讀熱圖 {#reading-the-heatmap}

「促銷活動工作流程熱圖」是自然可讀的格線，從左上至右下方，讓您找到具有綠色到紅色編碼範圍的「作用區」。

* 較深的紅色儲存格會對應同時執行大量工作流程的期間。
* 灰色儲存格會在沒有執行工作流程時對應期間。

要瞭解如何應用顏色代碼以及如何導航熱圖，請按一下 **[!UICONTROL Help]** 按鈕。

![](assets/wkf_monitoring_legend.png)

每列代表一天的一小時，而每個儲存格代表該小時的5分鐘。

此格線會針對每個5分鐘時段顯示同時執行的所有工作流程。

在以下範例中，在上午8點到上午8點05分之間，有三個工作流程正在執行（不論其個別持續時間）:

![](assets/wkf_monitoring_ex_8am.png)

1. 按一下彩色儲存格，以顯示此期間執行之所有並行工作流程的詳細資訊。

   ![](assets/wkf_monitoring_details.png)

   對於每個工作流，都會列出它包含的所有活動及其持續時間。

1. 按一下工作流程ID或名稱，即可直接開啟工作流程。
1. 要返回視圖， **[!UICONTROL Campaign Workflow HeatMap]** 請按一下該 **[!UICONTROL Home]** 按鈕。

## 使用案例：使用HeatMap採取行動 {#use-cases--using-the-heatmap-to-take-actions}

促銷活動工作流程熱圖可在兩個主要案例中派上用場。

### 減少並行工作流程的數量 {#reducing-the-number-of-concurrent-workflows}

身為促銷活動管理員，Workflow HeatMap可協助您瞭解例項的載入情況，並在適當時間規劃現有或新的工作流程。

1. 在視圖 **[!UICONTROL Campaign Workflow HeatMap]** 中，按一下按 **[!UICONTROL Filters]** 鈕。
1. 將持續時間設為幾秒或幾分鐘。
1. 借由增加持續時間篩選，排除不重要的最短工作流程。

   ![](assets/wkf_monitoring_short_duration.png)

1. 探索結果，瞭解執行個體的負載並採取適當動作：

   * 如果您遇到效能問題，而且在格線中顯示一或多個紅色儲存格，請考慮變更數個工作流程的開始時間。 要求行銷使用者將手動工作流程從繁忙（「熱」）時段移至更多可用時段。 這應該會維持當天的穩定活動水準。
   * 為避免尖峰，避免例項過載，請先查看HeatMap，再規劃新的工作流程，並選擇最佳時間。 考慮網格中與灰色或綠色單元格對應的時隙，以開始新的工作流程。

### 尋找影響效能的長效工作流程 {#finding-long-running-workflows-that-impact-performance}

身為促銷活動管理員，Workflow HeatMap可協助您尋找最長的工作流程，以減緩活動。

1. 在視圖 **[!UICONTROL Campaign Workflow HeatMap]** 中，按一下按 **[!UICONTROL Filters]** 鈕。
1. 將持續時間設為1小時。

   ![](assets/wkf_monitoring_long_duration.png)

1. 透過減少篩選，加入更多 **[!UICONTROL Min duration]** 結果。
1. 探索結果，找出最長的工作流程，這些工作流程可能會對伺服器和資料庫資源（CPU、RAM、網路、IOPS等）產生更大影響。
1. 採取適當的行動：

   * 建議行銷使用者分割最長的工作流程，以縮短處理時間。
   * 對特定工作流程和特定活動（例如JavaScript、匯入、匯出等）進行更深入的分析，以隔離問題並更輕鬆地解決問題。

## 範例：使用HeatMap改善工作流程規劃 {#example--using-the-heatmap-to-improve-workflow-planning}

下列範例說明如何提高規劃的效率，以及使用Adobe Campaign Workflow HeatMap時如何改善效能。

在這種情況下，許多使用者都對工作流程的效能抱怨不已。 您需要檢查哪些因素減緩了活動，以及如何解決問題。

1. 前往並 **[!UICONTROL Monitoring]** 按一下連 **[!UICONTROL Workflows]** 結以顯示頁 **[!UICONTROL Campaign Workflow HeatMap]** 面。
1. 將篩選 **[!UICONTROL Min duration]** 器設為5分鐘。
1. 將篩選 **[!UICONTROL Workflow type]** 器設為 **[!UICONTROL Marketing]** 。
1. 從HeatMap格線中，觀察以下內容：

   ![](assets/wkf_monitoring_without.png)

   * 50個持續時間（超過5分鐘）的促銷活動工作流程在上午10點開始執行。
   * 其中大部分都有擱置狀態（依預設，並行限制設定為20）。
   * 需要每天手動重新啟動待審工作流程。
   * 效能低。

1. 與其說從上午10點開始有50個工作流程，不如將工作流程的開始時間平均分配給一天的其餘時間。
1. 返回頁面 **[!UICONTROL Campaign Workflow HeatMap]** 並按一下按 **[!UICONTROL Reload data]** 鈕。
1. 現在請注意：

   ![](assets/wkf_monitoring_with.png)

   * 上午10時，只有18個長期的宣傳工作流程仍在執行中。
   * 不再有工作流程處於擱置中狀態（並行限制仍設為20）。
   * 工作流程的開始時間會平均分佈在一天中。
   * 不再有使用者抱怨效能問題。

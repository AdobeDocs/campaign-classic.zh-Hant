---
product: campaign
title: 建置工作流程
description: 瞭解如何構建工作流
feature: Workflows
exl-id: 8ba20ccd-b03f-4c4f-87c1-a21e80d8e4be
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1623'
ht-degree: 2%

---

# 建置工作流程 {#building-a-workflow}

![](../../assets/v7-only.svg)

本節詳細介紹了在市場活動中構建工作流的主要原則和最佳做法。

* 建立工作流，請參閱 [建立新工作流](#creating-a-new-workflow)
* 設計工作流圖，請參閱 [添加和連結活動](#adding-and-linking-activities)
* 訪問活動的參數和屬性，請參見 [配置活動](#configuring-activities)
* 設計目標工作流，請參見 [目標工作流](#targeting-workflows)
* 使用工作流執行市場活動，請參閱 [市場活動工作流](#campaign-workflows)
* 訪問和建立技術工作流，請參閱 [技術工作流](#technical-workflows)
* 使用模板建立工作流，請參閱 [工作流模板](#workflow-templates)

## 建立新工作流 {#creating-a-new-workflow}

從 **[!UICONTROL Explorer]**，訪問工作流資料夾。 預設情況下，您可以 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**。

按一下 **[!UICONTROL New]** 按鈕。

![](assets/create_a_wf_icon.png)

或者，您也可以 **[!UICONTROL Create]** 按鈕(**[!UICONTROL Monitoring]** > **[!UICONTROL Workflow]** 連結)。

![](assets/create_a_wf.png)

輸入標籤，然後按一下 **[!UICONTROL Save]**。

>[!NOTE]
>
>修改工作流活動或工作流本身的內部名稱時，請確保在關閉工作流之前保存該工作流，以便正確考慮新的內部名稱。

## 添加和連結活動 {#adding-and-linking-activities}

您現在必須定義各種活動，並將它們在圖表中連結在一起。在此配置階段，我們可以看到表徵圖和工作流狀態（正在編輯）。 窗口的下部僅用於編輯圖。 它包含工具欄、活動元件面板（在左側）和圖本身（在右側）。

![](assets/new-workflow-2.png)

>[!NOTE]
>
>如果未顯示調色板，請按一下工具欄上的第一個按鈕以顯示調色板。

活動按元件面板的不同頁籤中的類別分組。 可用的標籤和活動可能因工作流類型（技術、目標或市場活動工作流）而異。

* 第一個頁籤包含目標和資料操作活動。 這些活動在 [目標活動](about-targeting-activities.md)。
* 第二個頁籤包含計畫活動，這些活動主要用於協調其他活動。 這些活動在 [流控制活動](about-flow-control-activities.md)。
* 第三個頁籤包含可在工作流中使用的工具和操作。 這些活動在 [行動活動](about-action-activities.md)。
* 第四個頁籤包含依賴於給定事件的活動，如接收電子郵件或檔案到達伺服器。 這些活動在 [活動](about-event-activities.md)。

建立圖

1. 通過在調色板中選擇活動並使用拖放操作將其移動到圖來添加活動。

   添加 **開始** 活動，然後 **交貨** 表徵圖

   ![](assets/new-workflow-3.png)

1. 通過拖動 **開始** 活動轉換並將其放到 **交貨** 的子菜單。

   ![](assets/new-workflow-4.png)

   通過將新活動置於轉換結束，可以自動將活動連結到上一個活動。

1. 添加所需活動並將它們連結在一起，如下圖所示。

   ![](assets/new-workflow-5.png)

>[!CAUTION]
>
>您可以在同一工作流中複製和貼上活動。 但是，我們不建議跨不同的工作流複製貼上活動。 附加到「交貨」和「計畫程式」等活動的某些設定在執行目標工作流時可能會導致衝突和錯誤。 相反，我們建議你  **重複** 工作流。 有關詳細資訊，請參見 [複製工作流](#duplicating-workflows)。

可以使用以下元素更改圖表的顯示和佈局：

* **使用工具欄**

   圖編輯工具欄允許您訪問工作流的佈局和執行功能。

   ![](assets/s_user_segmentation_wizard_10.png)

   這允許您調整編輯工具的佈局：調色板的顯示以及圖形對象的概述、大小和對齊方式。

   ![](assets/s_user_segmentation_toolbar.png)

   與進度和日誌顯示相關的表徵圖將在以下各節中詳細介紹：

   * [顯示進度](../../workflow/using/monitoring-workflow-execution.md#displaying-progress)
   * [顯示日誌](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)

* **對象對齊**

   要對齊表徵圖，請選中表徵圖，然後按一下 **[!UICONTROL Align vertically]** 或 **[!UICONTROL Align horizontally]** 表徵圖

   使用 **CTRL鍵** 鍵，以選擇多個分散的活動或取消選擇一個或多個活動。 按一下圖背景以取消選擇所有內容。

* **映像管理**

   可以定製圖的背景影像以及與各種活動相關的背景影像。 請參閱 [更改活動映像](managing-activity-images.md)。

## 配置活動 {#configuring-activities}

按兩下某個活動進行配置，或按一下右鍵並選擇 **[!UICONTROL Open...]**。

>[!NOTE]
>
>市場活動工作流活動的詳細資訊請參閱 [此部分](about-activities.md)。

第一個頁籤包含基本配置。 的 **[!UICONTROL Advanced]** 頁籤包含附加參數，這些參數在遇到錯誤時用於定義行為、指定活動的執行持續時間以及輸入初始化指令碼。

為了更好地瞭解活動並提高工作流的可讀性，您可以在活動中輸入注釋：當操作符滾動到活動上時，將自動顯示這些內容。

![](assets/example1-comment.png)

## 目標定位工作流程 {#targeting-workflows}

目標工作流使您能夠構建多個傳遞目標。 由於工作流活動，您可以建立查詢、根據特定標準定義工會或排除、添加計畫。 此目標的結果可以自動傳送到清單，該清單可用作傳遞操作的目標

除了這些活動外，資料管理選項還允許您處理資料並訪問高級功能，以滿足複雜的目標問題。 有關此內容的詳細資訊，請參閱 [資料管理](targeting-data.md#data-management)。

所有這些活動都可以在第一個工作流頁籤中找到。

>[!NOTE]
>
>目標活動詳見 [此部分](about-activities.md)。

目標工作流可通過 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 或通過 **[!UICONTROL Profiles and Targets > Targeting workflows]** 的子菜單。

![](assets/target_wf.png)

市場活動框架內的目標工作流與所有市場活動工作流一起儲存。

### 建立目標工作流的關鍵步驟 {#implementation-steps-}

建立目標工作流的步驟在以下各節中詳細介紹：

1. **識別** 資料庫中的資料 — 請參見 [建立查詢](targeting-data.md#creating-queries)
1. **準備** 滿足交付需要的資料 — 請參閱 [豐富和修改資料](targeting-data.md#enriching-and-modifying-data)
1. **使用** 要執行更新或交付內的資料 — 請參閱 [更新資料庫](how-to-use-workflow-data.md#updating-the-database)

在目標期間執行的所有內容和所有處理的結果被儲存在個性化欄位中並且可以訪問，特別是在建立個性化消息時使用。 有關此內容的詳細資訊，請參閱 [目標資料](data-life-cycle.md#target-data)

### 定位和篩選維 {#targeting-and-filtering-dimensions}

在資料分段操作期間，將目標鍵映射到過濾維度。 目標維用於定義工序所針對的人口：收件人、合同受益人、操作員、訂戶等。 篩選維允許您根據特定條件選擇填充：合同持有人、通訊訂閱者等。

例如，要選擇擁有人壽保險單超過5年的客戶，請選擇以下目標維： **客戶端** 和以下篩選維： **合同持有人**。 然後，可以在查詢活動中定義篩選條件

在目標維選擇階段，介面中僅提供相容的篩選維。

這兩個維必須相關。 因此， **[!UICONTROL Filtering dimension]** 清單取決於在第一個欄位中指定的目標維。

例如，對於收件人(**收件人**)，以下篩選維將可用：

![](assets/query_filter_target_dimensions_1.png)

為 **Web應用程式**，清單將包含以下篩選維：

![](assets/query_filter_target_dimensions_2.png)

## 市場活動工作流 {#campaign-workflows}

對於每個市場活動，您可以建立要從 **[!UICONTROL Targeting and workflows]** 頁籤。 這些工作流特定於市場活動。

![](assets/wf-in-op-edit-delivery-tab.png)

此頁籤包含與所有工作流相同的活動。 [了解更多](#implementation-steps-)

除了針對市場活動外，市場活動工作流還使您能夠完全為所有可用渠道建立和配置交貨。 一旦在工作流中建立，這些交貨便可從市場活動的控制面板中獲得。 [了解更多](../../campaign/using/marketing-campaign-deliveries.md)

所有市場活動工作流都集中在 **[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]** 的下界。

![](assets/campaigns_wf.png)

市場活動工作流和實施示例在 [此頁](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)。

## 技術工作流程 {#technical-workflows}

技術工作流隨Adobe Campaign提供。 這些操作或作業計畫在伺服器上定期執行。 它們允許您對資料庫進行維護，轉發有關交貨的跟蹤資訊，並設定交貨的臨時流程。 通過 **[!UICONTROL Administration > Production > Technical workflows]** 的下界。

![](assets/navtree.png)

本機模板可用於建立技術工作流。 可以根據您的需要配置這些設備。

的 **[!UICONTROL Campaign process]** 子資料夾集中了在市場活動中執行流程所需的工作流：任務通知、庫存管理、成本計算等。

>[!NOTE]
>
>隨每個模組一起安裝的技術工作流清單可在 [專用段](about-technical-workflows.md)。

您可以在 **[!UICONTROL Administration > Production > Technical workflows]** 樹結構的節點。 但是，此過程保留給專家用戶。

提供的活動與針對工作流的活動相同。 [了解更多](#implementation-steps-)

## 工作流模板 {#workflow-templates}

工作流模板包含屬性的總體配置以及可能連接在圖中的一系列活動。 此配置可重複使用，用於建立包含特定數量的預配置元素的新工作流

您可以基於現有模板建立新的工作流模板，或直接將工作流更改為模板。

工作流模板儲存在 **[!UICONTROL Resources > Templates > Workflow templates]** Adobe Campaign樹的節點。

![](assets/s_advuser_wf_template_tree.png)

除了通常的工作流屬性外，模板屬性還允許您為基於此模板建立的工作流指定執行檔案。

![](assets/s_advuser_wf_template_properties.png)

## 複製工作流 {#duplicating-workflows}

您可以複製不同類型的工作流。 複製之後，不會將工作流程的修改轉存到工作流程的副本中。

>[!CAUTION]
>
>複製貼上在工作流中可用，但我們建議您使用 **重複**。 複製活動後，將保留其整個配置。 對於傳遞活動（電子郵件、SMS、推送通知……），還會複製附加到該活動的傳遞對象，這可能導致崩潰。

1. 按一下右鍵工作流。
1. 按一下 **重複**。

   ![](assets/duplicate-workflows.png)

1. 在工作流窗口中，更改工作流標籤。
1. 按一下 **保存**。

市場活動視圖中不直接提供重複功能。

但是，您可以建立一個視圖來顯示實例上的所有工作流。 在此視圖中，您可以使用 **複製到**。

**建立視圖**

1. 在 **瀏覽器**，轉到在中建立視圖所需的資料夾。
1. 按一下右鍵並轉到 **添加新資料夾** > **進程**&#x200B;選中 **工作流**。

   ![](assets/add-new-folder-workflows.png)

新資料夾 **工作流** 的子菜單。

1. 按一下右鍵並選擇 **屬性**。
1. 在 **限制**&#x200B;選中 **資料夾是視圖** 按一下 **保存**。

   ![](assets/folder-is-a-view.png)

現在，資料夾將填充實例的所有工作流。

**複製市場活動工作流**

1. 在工作流視圖中選擇市場活動工作流。
1. 按一下右鍵 **複製到**。
   ![](assets/duplicate-to-right-click.png)
1. 更改其標籤。
1. 按一下 **保存**。

您可以在工作流視圖中查看重複的工作流。

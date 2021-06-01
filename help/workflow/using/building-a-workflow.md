---
product: campaign
title: 建立工作流程
description: 了解如何建立工作流程
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 8ba20ccd-b03f-4c4f-87c1-a21e80d8e4be
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1624'
ht-degree: 3%

---

# 建立工作流程 {#building-a-workflow}

本節詳細說明在Campaign中建立工作流程的主要原則和最佳實務。

* 建立工作流，請參閱[建立新工作流](#creating-a-new-workflow)
* 設計工作流圖，請參閱[新增和連結活動](#adding-and-linking-activities)
* 存取活動的參數和屬性，請參閱[設定活動](#configuring-activities)
* 設計目標工作流程，請參閱[目標工作流程](#targeting-workflows)
* 使用工作流程執行促銷活動，請參閱[促銷活動工作流程](#campaign-workflows)
* 存取並建立技術工作流程，請參閱[技術工作流程](#technical-workflows)
* 使用模板建立工作流，請參閱[工作流模板](#workflow-templates)

## 建立新工作流{#creating-a-new-workflow}

從&#x200B;**[!UICONTROL Explorer]**，訪問工作流資料夾。 依預設，您可以使用&#x200B;**[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**。

按一下工作流程清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕。

![](assets/create_a_wf_icon.png)

或者，您也可以使用工作流程概述（**[!UICONTROL Monitoring]** > **[!UICONTROL Workflow]**&#x200B;連結）中的&#x200B;**[!UICONTROL Create]**&#x200B;按鈕。

![](assets/create_a_wf.png)

輸入標籤，然後按一下&#x200B;**[!UICONTROL Save]**。

>[!NOTE]
>
>修改工作流活動或工作流本身的內部名稱時，請確保在關閉工作流之前保存該工作流，以便正確考慮新的內部名稱。

## 新增和連結活動 {#adding-and-linking-activities}

您現在必須定義各種活動，並將它們在圖表中連結在一起。在設定的這個階段，我們會看到圖表標籤和工作流程狀態（正在編輯）。 窗口的下部僅用於編輯圖。 它包含工具列、活動浮動視窗（位於左側），以及圖表本身（位於右側）。

![](assets/new-workflow-2.png)

>[!NOTE]
>
>如果浮動視窗未顯示，請按一下工具列上的第一個按鈕以顯示它。

活動會依浮動視窗不同標籤內的類別分組。 可用的標籤和活動可能會依工作流程類型（技術、鎖定目標或行銷活動工作流程）而有所不同。

* 第一個標籤包含定位和資料操控活動。 在[目標活動](../../workflow/using/about-targeting-activities.md)中會詳細說明這些活動。
* 第二個索引標籤包含排程活動，主要用於協調其他活動。 在[流量控制活動](../../workflow/using/about-flow-control-activities.md)中詳細介紹了這些活動。
* 第三個索引標籤包含可在工作流程中使用的工具和動作。 在[動作活動](../../workflow/using/about-action-activities.md)中會詳細說明這些活動。
* 第四個索引標籤包含依賴指定事件的活動，例如收到電子郵件或檔案到達伺服器。 在[事件活動](../../workflow/using/about-event-activities.md)中會詳細說明這些活動。

建立圖表的方式

1. 在浮動視窗中選取活動，並使用拖放操作將其移至圖表，以新增活動。

   新增&#x200B;**開始**&#x200B;活動，然後在圖表上新增&#x200B;**傳送**&#x200B;活動。

   ![](assets/new-workflow-3.png)

1. 將&#x200B;**Start**&#x200B;活動轉變拖曳至&#x200B;**Delivery**&#x200B;活動，將活動連結在一起。

   ![](assets/new-workflow-4.png)

   您可以將新活動放置在轉變結束時，自動將活動連結至上一個活動。

1. 新增您需要的活動，並將它們連結在一起，如下圖所示。

   ![](assets/new-workflow-5.png)

>[!CAUTION]
>
>您可以在相同的工作流程中複製和貼上活動。 不過，我們不建議跨不同的工作流程複製貼上活動。 某些附加至活動（例如傳送和排程器）的設定在執行目標工作流程時可能會導致衝突和錯誤。 反之，我們建議您&#x200B;**複製**&#x200B;工作流程。 如需詳細資訊，請參閱[複製工作流程](#duplicating-workflows)。

您可以使用下列元素來變更圖表的顯示和配置：

* **使用工具列**

   圖表編輯工具列可讓您存取工作流程的版面配置和執行功能。

   ![](assets/s_user_segmentation_wizard_10.png)

   這可讓您調整編輯工具的版面：顯示浮動視窗，以及圖形對象的概述、大小和對齊方式。

   ![](assets/s_user_segmentation_toolbar.png)

   有關追蹤和啟動進階鎖定工作流程的圖示，請參閱本[區段](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)。

* **對象對齊**

   要對齊表徵圖，請選擇它們，然後按一下&#x200B;**[!UICONTROL Align vertically]**&#x200B;或&#x200B;**[!UICONTROL Align horizontally]**&#x200B;表徵圖。

   使用&#x200B;**CTRL**&#x200B;鍵選取多個分散的活動或取消選取一或多個活動。 按一下圖表背景，取消選取所有項目。

* **影像管理**

   您可以自訂圖表的背景影像，以及與各種活動相關的背景影像。 請參閱[管理活動影像](../../workflow/using/managing-activity-images.md)。

## 設定活動 {#configuring-activities}

連按兩下活動以進行設定，或以滑鼠右鍵按一下並選取&#x200B;**[!UICONTROL Open...]**。

>[!NOTE]
>
>[此區段](../../workflow/using/about-activities.md)中會詳細說明促銷活動工作流程活動。

第一個索引標籤包含基本設定。 **[!UICONTROL Advanced]**&#x200B;索引標籤包含其他參數，這些參數尤其用於定義發生錯誤時的行為、指定活動的執行持續時間以及輸入初始化指令碼。

為了更好地了解活動，並提高工作流的可讀性，您可以在活動中輸入注釋：當運算子捲動到活動上時，這些會自動顯示。

![](assets/example1-comment.png)

## 目標工作流程{#targeting-workflows}

目標工作流程可讓您建立數個傳送目標。 由於工作流活動，您可以建立查詢、根據特定條件定義聯合或排除、新增排程。 此定位的結果可自動轉移至清單，作為傳送動作的目標

除了這些活動，資料管理選項還可讓您控制資料並存取進階功能，以滿足複雜的鎖定目標問題。 有關詳細資訊，請參閱[資料管理](../../workflow/using/targeting-data.md#data-management)。

您可以在第一個工作流程索引標籤中找到所有這些活動。

>[!NOTE]
>
>在[此區段](../../workflow/using/about-activities.md)中會詳細說明鎖定目標活動。

您可以透過Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]**&#x200B;節點或首頁的&#x200B;**[!UICONTROL Profiles and Targets > Targeting workflows]**&#x200B;功能表，建立及編輯目標工作流程。

![](assets/target_wf.png)

所有行銷活動工作流程都會儲存行銷活動架構內的目標工作流程。

### 建立目標工作流{#implementation-steps-}的關鍵步驟

建立目標工作流程的步驟在以下章節中詳細說明：

1. **** 識別資料庫中的資料 — 請參閱 [建立查詢](../../workflow/using/targeting-data.md#creating-queries)
1. **** 滿足傳遞需求的Preparedata — 請參閱 [豐富和修改資料](../../workflow/using/targeting-data.md#enriching-and-modifying-data)
1. **** 使用資料執行更新或傳送內 — 請參閱 [更新資料庫](../../workflow/using/how-to-use-workflow-data.md#updating-the-database)

鎖定目標期間執行的所有擴充和所有處理結果都會儲存在個人化欄位中，且可供存取，尤其是用於建立個人化訊息時。 如需詳細資訊，請參閱[Target資料](../../workflow/using/data-life-cycle.md#target-data)

### 定位和篩選維度{#targeting-and-filtering-dimensions}

在資料分段作業期間，目標索引鍵會對應至篩選維度。 目標維度可讓您定義作業鎖定的母體：收件者、合約受益人、營運商、訂閱者等。 篩選維度可讓您根據特定條件選取母體：合約持有者、電子報訂閱者等

例如，要選擇已擁有壽險保單超過5年的客戶，請選擇以下目標維度：**Clients**&#x200B;及下列篩選維度：**合同持有人**。 然後，您可以在查詢活動中定義篩選條件

在目標維度選取階段期間，介面中僅提供相容的篩選維度。

這兩個維度必須相關。 因此，**[!UICONTROL Filtering dimension]**&#x200B;清單的內容取決於第一個欄位中指定的目標維度。

例如，對於收件者(**recipient**)，將可使用下列篩選維度：

![](assets/query_filter_target_dimensions_1.png)

對於&#x200B;**Web應用程式**，清單將包含下列篩選維：

![](assets/query_filter_target_dimensions_2.png)

## 促銷活動工作流程{#campaign-workflows}

對於每個促銷活動，您可以建立要從&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤執行的工作流程。 這些工作流程是行銷活動專屬的。

![](assets/wf-in-op-edit-delivery-tab.png)

此索引標籤包含與所有工作流程相同的活動。 [瞭解更多](#implementation-steps-)

除了鎖定目標促銷活動，促銷活動工作流程還可讓您建立和設定所有可用管道的傳送。 在工作流程中建立後，這些傳送即可從促銷活動的控制面板中使用。 [瞭解更多](../../campaign/using/marketing-campaign-deliveries.md)

所有促銷活動工作流程都集中在&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]**&#x200B;節點下。

![](assets/campaigns_wf.png)

[本頁面](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)中會詳細說明促銷活動工作流程和實作範例。

## 技術工作流程 {#technical-workflows}

Adobe Campaign提供立即可用的技術工作流程。 這些操作或作業計畫在伺服器上定期執行。 它們可讓您對資料庫進行維護、轉送傳送的追蹤資訊，以及設定傳送的臨時程式。 技術工作流程是透過&#x200B;**[!UICONTROL Administration > Production > Technical workflows]**&#x200B;節點設定。

![](assets/navtree.png)

原生範本可用於建立技術工作流程。 可依您的需求加以設定。

**[!UICONTROL Campaign process]**&#x200B;子資料夾會集中執行促銷活動中的程式所需的工作流程：任務通知、庫存管理、成本計算等

>[!NOTE]
>
>隨每個模組安裝的技術工作流程清單可在專用區段[中取得。](../../workflow/using/about-technical-workflows.md)

您可以在樹結構的&#x200B;**[!UICONTROL Administration > Production > Technical workflows]**&#x200B;節點中建立其他技術工作流。 不過，此程式會保留給專家使用者。

提供的活動與目標工作流程的相同。 [瞭解更多](#implementation-steps-)

## 工作流模板{#workflow-templates}

工作流程範本包含屬性的整體設定，以及圖表中串連的可能範圍活動。 此設定可重複用於建立包含特定數量之預先設定元素的新工作流程

您可以根據現有範本建立新的工作流程範本，或直接將工作流程變更為範本。

工作流模板儲存在Adobe Campaign樹的&#x200B;**[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;節點中。

![](assets/s_advuser_wf_template_tree.png)

除了通常的工作流屬性外，模板屬性還允許您為基於此模板建立的工作流指定執行檔案。

![](assets/s_advuser_wf_template_properties.png)

## 複製工作流程 {#duplicating-workflows}

您可以複製不同類型的工作流程。 複製之後，不會將工作流程的修改轉存到工作流程的副本中。

>[!CAUTION]
>
>複製貼上功能在工作流程中可用，但建議您使用&#x200B;**複製**。 複製活動後，會保留其整個設定。 對於傳送活動（電子郵件、簡訊、推播通知……），附加至活動的傳送物件也會複製，而這可能導致當機。

1. 以滑鼠右鍵按一下工作流程。
1. 按一下「**複製**」。

   ![](assets/duplicate-workflows.png)

1. 在工作流程視窗中，變更工作流程標籤。
1. 按一下「**儲存**」。

促銷活動檢視不直接提供重複功能。

不過，您可以建立檢視來顯示執行個體上的所有工作流程。 在此檢視中，您可以使用&#x200B;**複製到**&#x200B;來複製工作流程。

**首先，建立檢視：**

1. 在&#x200B;**Explorer**&#x200B;中，轉至在中建立視圖所需的資料夾。
1. 按一下右鍵並轉至&#x200B;**添加新資料夾** > **Process**，選擇&#x200B;**Workflows**。

   ![](assets/add-new-folder-workflows.png)

已建立新資料夾&#x200B;**Workflows**。

1. 按一下右鍵並選擇&#x200B;**屬性**。
1. 在&#x200B;**Restriction**&#x200B;中，檢查&#x200B;**資料夾是視圖**，然後按一下&#x200B;**Save**。

   ![](assets/folder-is-a-view.png)

資料夾現在會填入您執行個體的所有工作流程。

**複製行銷活動工作流程**

1. 在工作流程檢視中選取促銷活動工作流程。
1. 按一下右鍵&#x200B;**複製到**。
   ![](assets/duplicate-to-right-click.png)
1. 更改其標籤。
1. 按一下「**儲存**」。

您可以在工作流程檢視中查看重複的工作流程。

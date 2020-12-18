---
solution: Campaign Classic
product: campaign
title: 建立工作流程
description: 瞭解如何建立工作流程
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1624'
ht-degree: 3%

---


# 建立工作流程 {#building-a-workflow}

本節詳細說明在Campaign中建立工作流程的主要原則和最佳實務。

* 建立工作流，請參閱[建立新工作流](#creating-a-new-workflow)
* 設計工作流圖，請參閱[添加和連結活動](#adding-and-linking-activities)
* 訪問活動的參數和屬性，請參閱[配置活動](#configuring-activities)
* 設計定位工作流程，請參閱[定位工作流程](#targeting-workflows)
* 使用工作流程執行促銷活動，請參閱[促銷活動工作流程](#campaign-workflows)
* 存取並建立技術工作流程，請參閱[技術工作流程](#technical-workflows)
* 使用範本建立工作流程，請參閱[工作流程範本](#workflow-templates)

## 建立新工作流{#creating-a-new-workflow}

從&#x200B;**[!UICONTROL Explorer]**&#x200B;存取工作流程資料夾。 依預設，您可以使用&#x200B;**[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**。

按一下工作流程清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕。

![](assets/create_a_wf_icon.png)

或者，您也可以使用工作流程概述（**[!UICONTROL Monitoring]** > **[!UICONTROL Workflow]**&#x200B;連結）中的&#x200B;**[!UICONTROL Create]**&#x200B;按鈕。

![](assets/create_a_wf.png)

輸入標籤，然後按一下&#x200B;**[!UICONTROL Save]**。

>[!NOTE]
>
>修改工作流活動或工作流本身的內部名稱時，請確保在關閉工作流之前保存該工作流，以便正確考慮新的內部名稱。

## 新增和連結活動 {#adding-and-linking-activities}

您現在必須定義各種活動，並將它們在圖表中連結在一起。在此配置階段，我們可以看到表徵圖和工作流狀態（正在編輯）。 窗口的下部僅用於編輯圖。 它包含一個工具列、一個活動浮動視窗（在左側）和圖表本身（在右側）。

![](assets/new-workflow-2.png)

>[!NOTE]
>
>如果浮動視窗未顯示，請按一下工具列上的第一個按鈕以顯示它。

活動會依浮動視窗不同標籤內的類別分組。 可用的標籤和活動可能會因工作流程類型（技術、定位或促銷活動工作流程）而異。

* 第一個標籤包含定位和資料操縱活動。 這些活動在[定位活動](../../workflow/using/about-targeting-activities.md)中有詳細說明。
* 第二個標籤包含排程活動，主要用於協調其他活動。 這些活動在[流量控制活動](../../workflow/using/about-flow-control-activities.md)中詳細說明。
* 第三個標籤包含可在工作流程中使用的工具和動作。 這些活動在[Action活動](../../workflow/using/about-action-activities.md)中詳細說明。
* 第四個標籤包含依賴於指定事件的活動，例如收到電子郵件或檔案送達伺服器。 這些活動在[Event活動](../../workflow/using/about-event-activities.md)中有詳細說明。

建立圖

1. 在浮動視窗中選取活動，然後使用拖放操作將其移至圖表，即可新增活動。

   在圖中添加&#x200B;**開始**&#x200B;活動，然後添加&#x200B;**發送**&#x200B;活動。

   ![](assets/new-workflow-3.png)

1. 將&#x200B;**Start**&#x200B;活動轉變拖放到&#x200B;**Delivery**&#x200B;活動，將活動連結在一起。

   ![](assets/new-workflow-4.png)

   您可以將新活動放置在轉場結束時，自動將活動連結至上一個活動。

1. 新增您需要的活動，並將它們連結在一起，如下圖所示。

   ![](assets/new-workflow-5.png)

>[!CAUTION]
>
>您可以複製和貼上相同工作流程中的活動。 不過，我們不建議跨不同的工作流程複製貼上活動。 某些附加至活動（例如「傳送」和「排程器」）的設定，在執行目標工作流程時可能會導致衝突和錯誤。 我們建議您改為&#x200B;**複製**&#x200B;工作流程。 如需詳細資訊，請參閱[複製工作流程](#duplicating-workflows)。

您可以使用下列元素變更圖表的顯示和版面配置：

* **使用工具列**

   圖表編輯工具列可讓您存取工作流程的版面配置和執行功能。

   ![](assets/s_user_segmentation_wizard_10.png)

   這可讓您調整編輯工具的版面配置：浮動視窗的顯示以及圖形物件的概述、大小和對齊方式。

   ![](assets/s_user_segmentation_toolbar.png)

   此[章節](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)中詳述了與追蹤和啟動進階定位工作流程相關的圖示。

* **物件對齊**

   要對齊表徵圖，請選擇它們並按一下&#x200B;**[!UICONTROL Align vertically]**&#x200B;或&#x200B;**[!UICONTROL Align horizontally]**&#x200B;表徵圖。

   使用&#x200B;**CTRL**&#x200B;鍵可選擇多個分散的活動或取消選擇一個或多個活動。 按一下圖背景以取消選擇所有內容。

* **影像管理**

   您可以自訂圖的背景影像以及與各種活動相關的背景影像。 請參閱[管理活動映像](../../workflow/using/managing-activity-images.md)。

## 設定活動 {#configuring-activities}

連按兩下活動以進行設定，或以滑鼠右鍵按一下並選取&#x200B;**[!UICONTROL Open...]**。

>[!NOTE]
>
>促銷活動工作流程活動在[本節](../../workflow/using/about-activities.md)中有詳細說明。

第一個頁籤包含基本配置。 **[!UICONTROL Advanced]**&#x200B;標籤包含其他參數，這些參數尤其用於在遇到錯誤時定義行為、指定活動的執行持續時間以及輸入初始化指令碼。

為了更好地瞭解活動並提高工作流的易懂性，您可以在活動中輸入注釋：當運算子捲動至活動時，這些動作會自動顯示。

![](assets/example1-comment.png)

## 定位工作流程{#targeting-workflows}

定位工作流程可讓您建立數個傳送目標。 您可以建立查詢、根據特定條件定義工會或排除、新增排程，這都要歸功於工作流程活動。 此定位的結果可自動傳送至清單，以做為傳送動作的目標

除了這些活動外，「資料管理」選項還可讓您控制資料並存取進階功能，以滿足複雜的定位問題。 有關詳細資訊，請參閱[資料管理](../../workflow/using/targeting-data.md#data-management)。

所有這些活動都可在第一個工作流程標籤中找到。

>[!NOTE]
>
>[本節](../../workflow/using/about-activities.md)中詳細說明定位活動。

定位工作流程可透過Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]**&#x200B;節點或首頁的&#x200B;**[!UICONTROL Profiles and Targets > Targeting workflows]**&#x200B;功能表來建立和編輯。

![](assets/target_wf.png)

促銷活動架構中的定位工作流程會與所有促銷活動工作流程一起儲存。

### 建立定位工作流程的關鍵步驟{#implementation-steps-}

建立定位工作流程的步驟在下列章節中詳述：

1. **識** 別資料庫中的資料——請參 [閱建立查詢](../../workflow/using/targeting-data.md#creating-queries)
1. **適** 合傳送需求的準備資料——請參閱 [豐富和修改資料](../../workflow/using/targeting-data.md#enriching-and-modifying-data)
1. **使** 用資料執行更新或傳送——請參 [閱更新資料庫](../../workflow/using/how-to-use-workflow-data.md#updating-the-database)

所有在定位期間執行的豐富結果和所有處理的結果都儲存在個性化領域中，並且可以訪問，尤其用於建立個性化消息。 有關詳細資訊，請參閱[目標資料](../../workflow/using/data-life-cycle.md#target-data)

### 定位和篩選維度{#targeting-and-filtering-dimensions}

在資料分段作業期間，定位索引鍵會對應至篩選維度。 定位維度可讓您定義由工序定位的人口：收件者、合約受益人、營運商、訂閱者等。 篩選維度可讓您根據特定條件來選取人口族群：合約持有人、電子報訂閱者等。

例如，若要選取擁有5年以上人壽保險單的客戶，請選取下列定位維度：**Clients**&#x200B;和下列篩選維度：**合約持有人**。 然後，您可以在查詢活動中定義篩選條件

在定位維度選擇階段中，介面中僅提供相容的篩選維度。

這兩個維度必須相關。 因此，**[!UICONTROL Filtering dimension]**&#x200B;清單的內容取決於在第一個欄位中指定的定位維度。

例如，對於收件者(**recipient**)，可使用下列篩選維度：

![](assets/query_filter_target_dimensions_1.png)

對於&#x200B;**Web應用程式**，清單將包含以下過濾維：

![](assets/query_filter_target_dimensions_2.png)

## 促銷活動工作流程{#campaign-workflows}

對於每個促銷活動，您可以從&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤建立要執行的工作流程。 這些工作流程是促銷活動專屬的。

![](assets/wf-in-op-edit-delivery-tab.png)

此標籤包含的活動與所有工作流程相同。 [進一步瞭解](#implementation-steps-)

除了定位促銷活動外，促銷活動工作流程可讓您建立並設定所有可用渠道的傳送。 在工作流程中建立後，這些傳送即可從促銷活動的控制面板中使用。 [進一步瞭解](../../campaign/using/marketing-campaign-deliveries.md)

所有促銷活動工作流程都集中在&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]**&#x200B;節點下。

![](assets/campaigns_wf.png)

[本頁](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)將詳細說明促銷活動工作流程和實作範例。

## 技術工作流程 {#technical-workflows}

Adobe Campaign提供現成可用的技術工作流程。 它們是計畫在伺服器上定期執行的操作或作業。 它們可讓您對資料庫進行維護、轉寄傳送的追蹤資訊，並設定傳送的臨時程式。 技術工作流程是透過&#x200B;**[!UICONTROL Administration > Production > Technical workflows]**&#x200B;節點來設定。

![](assets/navtree.png)

原生範本可用於建立技術工作流程。 您可依您的需求來設定它們。

**[!UICONTROL Campaign process]**&#x200B;子資料夾會集中執行促銷活動中之程式所需的工作流程：任務通知、庫存管理、成本計算等。

>[!NOTE]
>
>隨每個模組安裝的技術工作流清單位於[專用部分](../../workflow/using/about-technical-workflows.md)中。

您可以在樹結構的&#x200B;**[!UICONTROL Administration > Production > Technical workflows]**&#x200B;節點中建立其他技術工作流。 不過，此程式會保留給專家使用者。

提供的活動與定位工作流程相同。 [進一步瞭解](#implementation-steps-)

## 工作流模板{#workflow-templates}

工作流程範本包含屬性的整體設定，可能包含串連在圖中的一系列活動。 此設定可重複用於建立包含特定數目之預先設定元素的新工作流程

您可以根據現有範本建立新的工作流程範本，或直接將工作流程變更為範本。

工作流程範本會儲存在Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;節點中。

![](assets/s_advuser_wf_template_tree.png)

除了一般的工作流程屬性外，範本屬性還可讓您指定根據此範本建立之工作流程的執行檔案。

![](assets/s_advuser_wf_template_properties.png)

## 複製工作流程 {#duplicating-workflows}

您可以複製不同類型的工作流程。 複製之後，不會將工作流程的修改轉存到工作流程的副本中。

>[!CAUTION]
>
>複製貼上功能適用於工作流程，但建議您使用&#x200B;**複製**。 複製活動後，將保留其全部配置。 對於傳送活動（電子郵件、簡訊、推播通知……），也會複製附加至活動的傳送物件，而這可能導致當機。

1. 以滑鼠右鍵按一下工作流程。
1. 按一下&#x200B;**複製**。

   ![](assets/duplicate-workflows.png)

1. 在工作流窗口中，更改工作流標籤。
1. 按一下&#x200B;**保存**。

複製功能無法直接在促銷活動檢視中使用。

不過，您可以建立檢視來顯示執行個體上的所有工作流程。 在此視圖中，可以使用&#x200B;**複製到**&#x200B;複製工作流。

**首先，我們建立一個視圖：**

1. 在&#x200B;**Explorer**&#x200B;中，轉到在中建立視圖所需的資料夾。
1. 按一下右鍵並轉到&#x200B;**添加新資料夾** > **進程**，選擇&#x200B;**工作流**。

   ![](assets/add-new-folder-workflows.png)

將建立新資料夾&#x200B;**Workflows**。

1. 按一下右鍵並選擇&#x200B;**屬性**。
1. 在&#x200B;**Restriction**&#x200B;中，選中&#x200B;**資料夾是視圖** ，然後按一下&#x200B;**保存**。

   ![](assets/folder-is-a-view.png)

資料夾現在會填入您實例的所有工作流程。

**複製促銷活動工作流程**

1. 在工作流程檢視中選取促銷活動工作流程。
1. 按一下右鍵&#x200B;**複製到**。
   ![](assets/duplicate-to-right-click.png)
1. 變更其標籤。
1. 按一下&#x200B;**保存**。

您可以在工作流程檢視中看到重複的工作流程。

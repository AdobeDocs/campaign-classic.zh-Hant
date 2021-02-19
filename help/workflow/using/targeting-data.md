---
solution: Campaign Classic
product: campaign
title: 目標定位資料
description: 進一步瞭解工作流程中的定位資料
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: bb7e3ce726e2c589c033686cf3ab2960de140d91
workflow-type: tm+mt
source-wordcount: '1904'
ht-degree: 3%

---


# 目標定位資料{#targeting-data}

## 建立查詢{#creating-queries}

### 選擇資料{#selecting-data}

**[!UICONTROL Query]**&#x200B;活動可讓您選擇基本資料以建立目標人口。 有關詳細資訊，請參閱[建立查詢](../../workflow/using/query.md#creating-a-query)。

您也可以使用下列活動來查詢和調整資料庫中的資料：[增量查詢](../../workflow/using/incremental-query.md)、[讀清單](../../workflow/using/read-list.md)。

可以收集要在整個工作流生命週期中轉發和處理的附加資料。 有關詳細資訊，請參閱[添加資料](../../workflow/using/query.md#adding-data)和[編輯附加資料](#editing-additional-data)。

### 編輯其他資料{#editing-additional-data}

新增其他資料後，您就可以編輯或使用它來調整查詢活動中定義的目標。

**[!UICONTROL Edit additional data...]**&#x200B;連結可讓您檢視新增的資料，並加以修改或新增。

![](assets/wf_add_data_edit_link.png)

若要將資料新增至先前定義的輸出欄，請在可用欄位清單中選取它。 要建立新的輸出列，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;表徵圖，然後選擇該欄位並按一下&#x200B;**[!UICONTROL Edit expression]**。

![](assets/query_add_an_output_column.png)

為要添加的欄位定義計算模式，例如聚合。

![](assets/query_add_an_output_column_formula.png)

**[!UICONTROL Add a sub-item]**&#x200B;選項可讓您將計算資料附加至系列。 這可讓您從收集中選取其他資料，或定義收集元素的匯總計算。

![](assets/query_add_columns_subscription_sub-element.png)

子元素將會在其映射至之集合的子樹狀結構中呈現。

系列會顯示在&#x200B;**[!UICONTROL Collections]**&#x200B;子標籤中。 您可以按一下所選系列的&#x200B;**[!UICONTROL Detail]**&#x200B;圖示，以篩選收集的元素。 篩選精靈可讓您選取收集的資料，並指定要套用至系列中資料的篩選條件。

![](assets/query_add_columns_collection.png)

### 使用其他資料{#refining-the-target-using-additional-data}細化目標

收集的其他資料可讓您調整資料庫中的資料篩選。 若要這麼做，請按一下&#x200B;**[!UICONTROL Refine the target using additional data...]**&#x200B;連結：這可讓您對新增的資料進行過度篩選。

![](assets/wf_add_data_use_additional_data.png)

### 均化資料{#homogenizing-data}

在&#x200B;**[!UICONTROL Union]**&#x200B;或&#x200B;**[!UICONTROL Intersection]**&#x200B;類型活動中，您可以選擇只保留共用的其他資料以保持資料的一致性。 在這種情況下，此活動的臨時輸出工作台將僅包含所有入站集中找到的其他資料。

![](assets/option-common_additionnal_col_only.png)

### 與其他資料協調{#reconciliation-with-additional-data}

在資料協調階段（**[!UICONTROL Union]**、**[!UICONTROL Intersection]**&#x200B;等）中。 活動)，您可以從其他欄中選擇用於資料協調的欄。 要執行此操作，請在選擇的列上配置協調並指定主集。 然後，選擇窗口下方列中的列，如以下示例所示：

![](assets/select-column-and-join.png)

### 建立子集{#creating-subsets}

**[!UICONTROL Split]**&#x200B;活動可讓您根據透過擷取查詢定義的准則建立子集。 對於每個子集，當您編輯人口族群的篩選條件時，將會存取標準查詢活動，讓您定義目標分段條件。

您只能使用其他資料作為篩選條件，或除了目標資料外，將目標分割為數個子集。 如果您已購買&#x200B;**同盟資料存取**&#x200B;選項，也可以使用外部資料。

有關詳細資訊，請參閱[使用Split活動建立子集。](#creating-subsets-using-the-split-activity)

## 劃分資料{#segmenting-data}

### 組合多個目標（聯合）{#combining-several-targets--union-}

聯合活動可讓您在單一轉換中結合多個活動的結果。 集合不一定必須是同質的。

![](assets/join_reconciliation_options.png)

可使用以下資料協調選項：

* **[!UICONTROL Keys only]**

   如果輸入人口族群相同，則可使用此選項。

* **[!UICONTROL All columns in common]**

   此選項可讓您根據目標不同人口族群的所有共同欄來協調資料。

   Adobe Campaign會根據欄的名稱來識別欄。 接受允差閾值：例如，「電子郵件」欄可識別為與「@email」欄相同。

* **[!UICONTROL A selection of columns]**

   選擇此選項可定義將應用資料協調的列清單。

   首先，選擇主集（包含源資料的集），然後選擇用於聯接的列。

   ![](assets/join_reconciliation_options_01.png)

   >[!CAUTION]
   >
   >在資料協調期間，不會對人口進行去重複化。

   您可以將人口大小限制在指定數量的記錄。 若要這麼做，請按一下適當的選項，並指定要保留的記錄數。

   此外，指定傳入人口族群的優先順序：窗口的下部列出聯合活動的入站轉變，並允許您使用窗口右側的藍色箭頭對它們進行排序。

   記錄將首先從清單中第一個傳入轉變的人口中提取，如果未達到最大值，則從第二個傳入轉變的人口中提取。

   ![](assets/join_limit_nb_priority.png)

### 提取聯合資料（交叉點）{#extracting-joint-data--intersection-}

![](assets/traitements.png)

交叉點可讓您僅恢復傳入轉變的人口族群所共用的線條。 此活動的配置應與工會活動相同。

此外，也可以只保留一系列欄，或僅保留傳入人口所共用的欄。

交叉點活動在[交叉點](../../workflow/using/intersection.md)部分中詳細說明。

### 排除人口（排除）{#excluding-a-population--exclusion-}

排除活動可讓您從不同的目標人口中排除目標的元素。 此活動的輸出定位維度將是主集的輸出定位維度。

如有必要，可操作入站表。 事實上，若要從其他維度排除目標，此目標必須傳回至與主要目標相同的定位維度。 要執行此操作，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕並指定維更改條件。

通過標識符、更改軸或連接執行資料協調。 [使用清單中的資料中有範例：讀取清單](../../platform/using/import-export-workflows.md#using-data-from-a-list--read-list)。

![](assets/exclusion_edit_add_rule_01.png)

### 使用Split活動{#creating-subsets-using-the-split-activity}建立子集

**[!UICONTROL Split]**&#x200B;活動是標準活動，可讓您透過一或多個篩選維度建立所需數量的集合，以及為每個子集產生一個輸出轉換或一個唯一轉換。

由入站轉移傳送的附加資料可用於過濾標準。

若要設定，您必須先選取條件：

1. 在您的工作流程中，拖放&#x200B;**[!UICONTROL Split]**&#x200B;活動。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;標籤中，選取所要的選項：**[!UICONTROL Use data from the target and additional data]**、**[!UICONTROL Use the additional data only]**&#x200B;或&#x200B;**[!UICONTROL Use external data]**。
1. 如果選取&#x200B;**[!UICONTROL Use data from the target and additional data]**&#x200B;選項，定位維度可讓您使用傳入轉場所傳送的所有資料。

   ![](assets/split-general-tab-options.png)

   建立子集時，使用前述的過濾參數。

   要定義過濾條件，請選擇&#x200B;**[!UICONTROL Add a filtering condition on the inbound population]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Edit...]**&#x200B;連結。 然後指定建立此子集的篩選條件。

   ![](assets/split-subset-config-all-data.png)

   [本節](../../workflow/using/cross-channel-delivery-workflow.md)說明如何使用&#x200B;**[!UICONTROL Split]**&#x200B;活動中的篩選條件將目標分段為不同的人口族群。

   **[!UICONTROL Label]**&#x200B;欄位可讓您為新建立的子集指定名稱，此名稱將符合出站轉場。

   您也可以指派區段代碼給子集以識別該子集，並使用它來定位其人口。

   如有需要，您可以針對每個要建立的子集分別變更定位和篩選維度。 若要這麼做，請編輯子集的篩選條件並勾選&#x200B;**[!UICONTROL Use a specific filtering dimension]**&#x200B;選項。

   ![](assets/split-subset-config-specific-filtering.png)

1. 如果選取&#x200B;**[!UICONTROL Use the additional data only]**&#x200B;選項，則僅提供其他資料供子集篩選。

   ![](assets/split-subset-config-additional-data-only.png)

1. 如果&#x200B;**同盟資料存取**&#x200B;選項處於啟用狀態， **[!UICONTROL Use external data]**&#x200B;可讓您處理已配置的外部資料庫中的資料，或建立到資料庫的新連接。

   ![](assets/split-subset-config-add_external_data.png)

   如需詳細資訊，請參閱本[區段](../../installation/using/about-fda.md)。

然後，我們需要添加新子集：

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕並定義篩選條件。

   ![](assets/wf_split_add_a_tab.png)

1. 在活動的&#x200B;**[!UICONTROL General]**&#x200B;標籤中定義篩選維（請參見上面）。預設情況下，它應用於所有子集。

   ![](assets/wf_split_edit_filtering.png)

1. 如有必要，您可以個別變更每個子集的篩選維度。 這可讓您為所有金卡持卡人建立一組資料，其中一個是所有點選最新電子報的收件者，另一個是18至25歲、在過去30天內在店內購買金卡的收件者，全都使用相同的分割活動。 若要這麼做，請選取&#x200B;**[!UICONTROL Use a specific filtering dimension]**&#x200B;選項，然後選取資料篩選內容。

   ![](assets/wf_split_change_dimension.png)

   >[!NOTE]
   >
   >如果您已獲取&#x200B;**同盟資料存取**&#x200B;選項，則可以根據外部基礎中的資訊建立子集。 要執行此操作，請在&#x200B;**[!UICONTROL Targeting dimension]**&#x200B;欄位中選擇外部表的模式。 有關詳細資訊，請參閱[訪問外部資料庫(FDA)](../../workflow/using/accessing-an-external-database--fda-.md)。

在建立子集後，預設情況下，拆分活動顯示的輸出轉變與有子集的輸出轉變相同：

![](assets/wf_split_multi_outputs.png)

您可以將所有這些子集分組到單個輸出過渡中。 在這種情況下，例如，到各個子集的連結將顯示在段代碼中。 若要這麼做，請選取&#x200B;**[!UICONTROL Generate all subsets in the same table]**&#x200B;選項。

![](assets/wf_split_select_option_single_output.png)

例如，您可以放置單一傳送活動，並根據每個收件者集的區段代碼個人化傳送內容：

![](assets/wf_split_single_output.png)

也可使用&#x200B;**[!UICONTROL Cells]**&#x200B;活動建立子集。 有關詳細資訊，請參閱[單元格](../../workflow/using/cells.md)部分。

### 使用目標資料{#using-targeted-data}

在識別並準備好資料後，即可在下列內容中使用：

* 您可以在不同工作流程階段中，依據資料操作來更新資料庫中的資料。

   有關詳細資訊，請[更新資料](../../workflow/using/update-data.md)。

* 您也可以重新整理現有清單的內容。

   有關詳細資訊，請參閱[List update](../../workflow/using/list-update.md)。

* 您可以直接在工作流程中準備或開始傳送。

   有關詳細資訊，請參閱[Delivery](../../workflow/using/delivery.md)、[Delivery control](../../workflow/using/delivery-control.md)和[Continuous delivery](../../workflow/using/continuous-delivery.md)。

## 資料管理{#data-management}

在Adobe Campaign中，資料管理結合一系列活動，透過提供更有效率且更有彈性的工具來解決複雜的定位問題。 這可讓您使用與合約、訂閱、交付反應等相關的資訊，對與聯絡人的所有通訊實施一致的管理。 「資料管理」可讓您在分段作業期間追蹤資料生命週期，尤其是：

* 透過包含未在資料超市中模型化的資料，來簡化及最佳化鎖定過程（建立新的資料表：根據配置，對目標工作流程進行本地擴展）。
* 保持和傳達緩衝區計算，尤其是在目標建構階段或進行資料庫管理時。
* 存取外部資料庫（選用）：在鎖定過程中考慮異質資料庫。

為了實作這些作業，Adobe Campaign提供：

* 資料收集活動：[檔案傳輸](../../workflow/using/file-transfer.md)、[資料載入（檔案）](../../workflow/using/data-loading--file-.md)、[資料載入(RDBMS)](../../workflow/using/data-loading--rdbms-.md)、[更新資料](../../workflow/using/update-data.md)。 收集資料的第一步會準備資料，以便在其他活動中加以處理。 需要監控多個參數，以確保工作流正確執行並提供預期結果。 例如，在匯入資料時，此資料的主鍵(Pkey)必須對每個記錄都是唯一的。
* 使用資料管理選項豐富定位活動：[Query](../../workflow/using/query.md)、[Union](../../workflow/using/union.md)、[Intersection](../../workflow/using/intersection.md)、[Split](../../workflow/using/split.md)。 這可讓您設定來自數個不同定位維度之資料之間的聯合或交叉點，只要資料協調是可能的。
* 資料轉換活動：[Enrichment](../../workflow/using/enrichment.md)、[變更尺寸](../../workflow/using/change-dimension.md)。

>[!CAUTION]
>
>在連結兩個工作流程時，刪除來源表格元素並不表示會刪除所有連結至其的資料。
>  
>例如，透過工作流程刪除收件者並不會導致所有收件者的傳送記錄遭到刪除。 不過，直接在「收件者」資料夾中刪除收件者，確實會刪除與該收件者連結的所有資料。

### 豐富和修改資料{#enriching-and-modifying-data}

除了定位維度外，篩選維度還可讓您指定所收集資料的性質。 請參閱[定位和篩選維度](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions)。

所識別和收集的資料可以被富集、聚集和操作以優化目標結構。 若要這麼做，除了[ Spagening data](#segmenting-data)區段中詳述的資料操縱活動外，請使用下列功能：

* **[!UICONTROL Enrichment]**&#x200B;活動可讓您立即新增欄至架構，並新增資訊至特定元素。 活動儲存庫的[Enrichment](../../workflow/using/enrichment.md)部分中詳述了此問題。
* **[!UICONTROL Edit schema]**&#x200B;活動可讓您修改架構的結構。 在活動儲存庫的[Edit schema](../../workflow/using/edit-schema.md)部分中有詳細說明。
* **[!UICONTROL Change dimension]**&#x200B;活動可讓您在目標建構週期中變更目標維度。 在[更改維](../../workflow/using/change-dimension.md)部分中有詳細說明。


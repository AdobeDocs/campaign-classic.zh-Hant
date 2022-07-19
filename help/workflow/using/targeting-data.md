---
product: campaign
title: 目標定位資料
description: 瞭解有關工作流中目標資料的詳細資訊
feature: Query Editor, Data Management
exl-id: 74b82019-bdab-4442-84cf-5ad18d0db788
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1924'
ht-degree: 3%

---

# 目標資料{#targeting-data}

![](../../assets/v7-only.svg)

## 建立查詢 {#creating-queries}

### 選取資料 {#selecting-data}

A **[!UICONTROL Query]** 「活動」(activity)允許您選擇基本資料以構建目標人口。 有關此內容的詳細資訊，請參閱 [建立查詢](query.md#creating-a-query)。

您還可以使用以下活動來查詢和細化資料庫中的資料： [增量查詢](incremental-query.md)。 [讀取清單](read-list.md)。

可以收集要在工作流的整個生命週期中轉發和處理的其他資料。 有關此內容的詳細資訊，請參閱 [添加資料](query.md#adding-data) 和 [編輯其他資料](#editing-additional-data)。

### 編輯其他資料 {#editing-additional-data}

添加其他資料後，您可以編輯它或使用它來細化查詢活動中定義的目標。

的 **[!UICONTROL Edit additional data...]** 連結，您可以查看添加的資料並修改或添加到其中。

![](assets/wf_add_data_edit_link.png)

要將資料添加到先前定義的輸出列，請在可用欄位清單中選擇它。 要建立新輸出列，請按一下 **[!UICONTROL Add]** 表徵圖，然後選擇該欄位並按一下 **[!UICONTROL Edit expression]**。

![](assets/query_add_an_output_column.png)

定義要添加的欄位的計算模式，例如聚合。

![](assets/query_add_an_output_column_formula.png)

的 **[!UICONTROL Add a sub-item]** 選項，可將計算資料附加到集合。 這允許您從收集中選擇附加資料或定義收集要素的聚合計算。

![](assets/query_add_columns_subscription_sub-element.png)

子元素將在它們映射到的集合的子樹中表示。

集合顯示在 **[!UICONTROL Collections]** 的子菜單。 通過按一下 **[!UICONTROL Detail]** 表徵圖。 通過篩選器嚮導，您可以選擇收集的資料並指定要應用於集合中的資料的篩選條件。

![](assets/query_add_columns_collection.png)

### 使用其他資料細化目標 {#refining-the-target-using-additional-data}

收集的附加資料使您能夠細化資料庫中的資料過濾。 要執行此操作，請按一下 **[!UICONTROL Refine the target using additional data...]** 連結：這允許您對添加的資料進行過濾。

![](assets/wf_add_data_use_additional_data.png)

### 均勻化資料 {#homogenizing-data}

在 **[!UICONTROL Union]** 或 **[!UICONTROL Intersection]** 類型活動，您可以選擇僅保留共用的附加資料以保持資料一致。 在這種情況下，此活動的臨時輸出工作表將只包含所有入站集中找到的其他資料。

![](assets/option-common_additionnal_col_only.png)

### 與其他資料協調 {#reconciliation-with-additional-data}

在資料協調階段(**[!UICONTROL Union]**。 **[!UICONTROL Intersection]**&#x200B;的子菜單。 活動)，可以從附加列中選擇要用於資料協調的列。 要執行此操作，請在選定的列上配置協調並指定主集。 然後，選擇窗口下列中的列，如下例所示：

![](assets/select-column-and-join.png)

### 建立子集 {#creating-subsets}

的 **[!UICONTROL Split]** 活動允許您根據通過抽取查詢定義的條件建立子集。 對於每個子集，在編輯填充上的篩選條件時，將訪問標準查詢活動，該活動允許您定義目標分段條件。

您只能將附加資料用作篩選條件，或將目標資料除外，將目標拆分為多個子集。 如果已購買 **聯合資料存取** 的雙曲餘切值。

有關此內容的詳細資訊，請參閱 [使用「拆分」活動建立子集](#creating-subsets-using-the-split-activity)。

## 段資料 {#segmenting-data}

### 合併多個目標（聯合） {#combining-several-targets--union-}

聯合活動允許您將多個活動的結果組合到一個過渡中。 集合不一定非得是同質的。

![](assets/join_reconciliation_options.png)

以下資料協調選項可用：

* **[!UICONTROL Keys only]**

   如果輸入總體是同質的，則可以使用此選項。

* **[!UICONTROL All columns in common]**

   此選項允許您根據目標的不同總體所共有的所有列協調資料。

   Adobe Campaign根據列的名稱標識列。 接受容差閾值：例如，「Email」列可以識別為與「@email」列相同。

* **[!UICONTROL A selection of columns]**

   選擇此選項可定義要應用資料協調的列清單。

   首先選擇主集（包含源資料的集），然後選擇要用於聯接的列。

   ![](assets/join_reconciliation_options_01.png)

   >[!CAUTION]
   >
   >在資料協調期間，不會消除重複資料。

   您可以將人口規模限制為給定數量的記錄。 為此，請按一下相應的選項並指定要保留的記錄數。

   此外，指定入站總量的優先順序：窗口的下部列出聯合活動的入站轉換，並允許您使用窗口右側的藍色箭頭對它們進行排序。

   記錄將首先從清單中第一個入站轉移的總體中獲取，然後，如果未達到最大值，則從第二個入站轉移的總體中獲取這些記錄，等等。

   ![](assets/join_limit_nb_priority.png)

### 提取關節資料（交集） {#extracting-joint-data--intersection-}

![](assets/traitements.png)

交叉點允許您僅恢復入站過渡總體共用的線。 此活動應配置為與工會活動類似。

此外，可以只保留選定的列，或僅保留入站總體共用的列。

交叉點活動在 [交集](intersection.md) 的子菜單。

### 排除人口（排除） {#excluding-a-population--exclusion-}

排除活動允許您從不同的目標群體中排除目標的元素。 此活動的輸出目標維將是主集的輸出目標維。

必要時，可以處理入站表。 實際上，要從另一個維中排除目標，必須將此目標返回到與主目標相同的目標維。 要執行此操作，請按一下 **[!UICONTROL Add]** 按鈕並指定維更改條件。

通過標識符、更改軸或連接執行資料協調。 有一個示例，請參見 [使用清單中的資料：讀取清單](../../platform/using/import-export-workflows.md#using-data-from-a-list--read-list)。

![](assets/exclusion_edit_add_rule_01.png)

### 使用「拆分」活動建立子集 {#creating-subsets-using-the-split-activity}

的 **[!UICONTROL Split]** activity是一個標準活動，它允許您通過一個或多個篩選維根據需要建立多個集，並為每個子集生成一個輸出轉換或唯一轉換。

通過入站轉換傳送的附加資料可以用在過濾標準中。

要配置它，您首先需要選擇條件：

1. 在工作流中，拖放 **[!UICONTROL Split]** 的子菜單。
1. 在 **[!UICONTROL General]** 頁籤，選擇所需選項： **[!UICONTROL Use data from the target and additional data]**。 **[!UICONTROL Use the additional data only]** 或 **[!UICONTROL Use external data]**。
1. 如果 **[!UICONTROL Use data from the target and additional data]** 選項，使用目標維可以使用入站轉換傳送的所有資料。

   ![](assets/split-general-tab-options.png)

   建立子集時，使用上述過濾參數。

   要定義篩選條件，請選擇 **[!UICONTROL Add a filtering condition on the inbound population]** ，然後按一下 **[!UICONTROL Edit...]** 的子菜單。 然後指定建立此子集的篩選條件。

   ![](assets/split-subset-config-all-data.png)

   一個示例，說明如何在 **[!UICONTROL Split]** 將目標分割到不同群體的活動，如中所述 [此部分](cross-channel-delivery-workflow.md)。

   的 **[!UICONTROL Label]** 欄位中，您可以為新建立的子集指定一個名稱，該名稱將與出站轉移相匹配。

   您還可以為子集指定段代碼以標識該子集，並使用該子集來瞄準其填充。

   如有必要，您可以分別為要建立的每個子集更改目標尺寸和篩選尺寸。 為此，請編輯子集的篩選條件並檢查 **[!UICONTROL Use a specific filtering dimension]** 的雙曲餘切值。

   ![](assets/split-subset-config-specific-filtering.png)

1. 如果 **[!UICONTROL Use the additional data only]** 選項，僅提供用於子集篩選的附加資料。

   ![](assets/split-subset-config-additional-data-only.png)

1. 如果 **聯合資料存取** 選項， **[!UICONTROL Use external data]** 允許您在已配置的外部資料庫中處理資料，或建立到資料庫的新連接。

   ![](assets/split-subset-config-add_external_data.png)

   有關此內容的詳細資訊，請參閱以下各節：

   ![](assets/do-not-localize/v7.jpeg)[  Campaign v7 文件](../../installation/using/about-fda.md)

   ![](assets/do-not-localize/v8.png)[  Campaign v8 文件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html?lang=en)

然後，我們需要添加新的子集：

1. 按一下 **[!UICONTROL Add]** 按鈕並定義篩選條件。

   ![](assets/wf_split_add_a_tab.png)

1. 在 **[!UICONTROL General]** 頁籤（請參閱上面）。預設情況下，它適用於所有子集。

   ![](assets/wf_split_edit_filtering.png)

1. 如有必要，可以單獨更改每個子集的篩選尺寸。 這樣，您就可以為所有金卡持卡者建立一個集，一個適用於所有點擊了最新新聞稿的收件人，另一個適用於18至25歲在過去30天內進行店內採購的人，所有這些人都使用相同的拆分活動。 要執行此操作，請選擇 **[!UICONTROL Use a specific filtering dimension]** 選項，然後選擇資料篩選上下文。

   ![](assets/wf_split_change_dimension.png)

   >[!NOTE]
   >
   >如果你已經 **聯合資料存取** 選項，您可以根據外部基中的資訊建立子集。 為此，請在 **[!UICONTROL Targeting dimension]** 的子菜單。 有關此內容的詳細資訊，請參閱 [訪問外部資料庫(FDA)](accessing-an-external-database--fda-.md)。

建立子集後，預設情況下，拆分活動顯示的輸出過渡與有子集一樣多：

![](assets/wf_split_multi_outputs.png)

可以將所有這些子集分組為單個輸出過渡。 在這種情況下，到各個子集的連結在段代碼中可見，例如。 要執行此操作，請選擇 **[!UICONTROL Generate all subsets in the same table]** 的雙曲餘切值。

![](assets/wf_split_select_option_single_output.png)

例如，您可以放置單個交貨活動，並根據每個收件人集的段代碼個性化交貨內容：

![](assets/wf_split_single_output.png)

也可以使用 **[!UICONTROL Cells]** 的子菜單。 有關詳細資訊，請參閱 [單元格](cells.md) 的子菜單。

### 使用目標資料 {#using-targeted-data}

一旦識別和準備了資料，就可以在以下上下文中使用資料：

* 您可以在不同工作流階段中對資料進行操作後更新資料庫中的資料。

   關於這個， [更新資料](update-data.md)。

* 您還可以刷新現有清單的內容。

   有關此內容的詳細資訊，請參閱 [清單更新](list-update.md)。

* 您可以直接在工作流中準備或開始交貨。

   有關此內容的詳細資訊，請參閱 [交貨](delivery.md)。 [交貨控制](delivery-control.md) 和 [連續交付](continuous-delivery.md)。

## 資料管理 {#data-management}

在Adobe Campaign，資料管理通過提供更高效和更靈活的工具，將一系列活動結合起來，以解決複雜的目標問題。 這使您能夠使用與聯繫人的合同、訂閱、對交貨的反應等相關的資訊，對聯繫人的所有通信實施一致的管理。 資料管理允許您在分段操作期間跟蹤資料生命週期，尤其是：

* 透過包含未在資料超市中模型化的資料，來簡化及最佳化鎖定過程（建立新的資料表：根據配置，對目標工作流程進行本地擴展）。
* 保持和傳達緩衝區計算，尤其是在目標建構階段或進行資料庫管理時。
* 存取外部資料庫（選用）：在鎖定過程中考慮異質資料庫。

為了實施這些操作，Adobe Campaign提供：

* 資料收集活動： [檔案傳輸](file-transfer.md)。 [資料載入（檔案）](data-loading--file-.md)。 [資料載入(RDBMS)](data-loading--rdbms-.md)。 [更新資料](update-data.md)。 收集資料的第一步是準備資料，以便在其他活動中處理資料。 需要監控幾個參數，以確保工作流正確執行並提供預期結果。 例如，在導入資料時，此資料的主鍵(Pkey)對於每個記錄都必須唯一。
* 資料管理選項豐富了針對活動的內容： [查詢](query.md)。 [聯合](union.md)。 [交集](intersection.md)。 [拆分](split.md)。 這允許您配置來自多個不同目標維的資料之間的聯合或交集，只要可以進行資料協調。
* 資料轉換活動： [濃縮](enrichment.md)。 [更改維](change-dimension.md)。

>[!CAUTION]
>
>當兩個工作流連結時，刪除源表元素並不意味著刪除連結到它的所有資料。
>  
>例如，通過工作流刪除收件人不會導致刪除收件人的所有傳遞歷史記錄。 但是，直接在「收件人」資料夾中刪除收件人確實會導致刪除與此收件人連結的所有資料。

### 豐富和修改資料 {#enriching-and-modifying-data}

除目標維外，篩選維還允許您指定所收集資料的性質。 請參閱 [定位和篩選維](building-a-workflow.md#targeting-and-filtering-dimensions)。

所識別和收集的資料可以被富集、聚集和操縱以優化目標構造。 為此，除了在 [分割資料](#segmenting-data) 部分，請使用以下命令：

* 的 **[!UICONTROL Enrichment]** 「活動」(activity)允許您立即將列添加到架構中，並將資訊添加到某些元素中。 在 [濃縮](enrichment.md) 的子菜單。
* 的 **[!UICONTROL Edit schema]** 活動，用於修改架構的結構。 在 [編輯架構](edit-schema.md) 的子菜單。
* 的 **[!UICONTROL Change dimension]** 活動允許您在目標構建週期中更改目標維。 在 [更改維](change-dimension.md) 的子菜單。

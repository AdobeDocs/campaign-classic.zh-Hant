---
title: 查詢
seo-title: 查詢
description: 查詢
seo-description: null
page-status-flag: never-activated
uuid: 32f4f467-5083-414f-8616-1aa4bf2b5867
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: b53d9810-f61f-4257-b410-e4d30f78429d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ab2c133aaa2f754e56fe8fdfc76d10526d4d1ce2

---


# 查詢{#query}

## 建立查詢 {#creating-a-query}

查詢可讓您根據條件選擇目標。 您可以將區段代碼關聯至查詢結果，並將其他資料插入。

>[!NOTE]
>
>本節將介紹查詢 [示例](../../workflow/using/querying-recipient-table.md)。

![](assets/s_user_segmentation_wizard_9.png)

有關使用和管理其他資料的詳細資訊，請參閱添 [加資料](#adding-data)。

連 **[!UICONTROL Edit query...]** 結可讓您以下列方式定義人口族群的定位類型、限制和選擇標準：

1. 選取定位和篩選維度。 依預設，會從收件者選取目標。 限制篩選清單與用於傳送定位的篩選清單相同。

   定位維度與我們將處理的元素類型一致，例如操作所定位的人口。

   篩選維度可以收集這些元素，例如與目標人員相關的資訊（合約、完整和最終結算等）。

   如需詳細資訊，請參閱定位 [和篩選維度](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions)。

   ![](assets/s_user_segmentation_query_edit.png)

   如有必要，查詢可以根據傳入轉場的資料，方法是選擇定位和篩選維 **[!UICONTROL Temporary schema]** 度時進行選取。

   ![](assets/query_temporary_table.png)

1. 使用精靈定義人口族群。 要輸入的欄位可以根據目標類型而有所不同。 您可以使用標籤，以您目前的准則預覽目標人口 **[!UICONTROL Preview]** 族群。

   有關建立和使用篩選器或查詢的詳細資訊，請參閱本 [節](../../platform/using/filtering-options.md)。

   ![](assets/s_user_segmentation_wizard.png)

1. 如果您已在步 **[!UICONTROL Filtering conditions]** 驟1中選取或使用 **[!UICONTROL Filters]** >選 **[!UICONTROL Advanced filter...]** 項，則稍後必須手動新增篩選條件。

   您也可以勾選對應的方塊，以新增資料分組條件。 若要這麼做，篩選維度必須與查詢的定位維度不同。 For more information on grouping, refer to this [section](../../workflow/using/querying-using-grouping-management.md).

   您也可以使用運算式產生器，並結合邏輯選項AND、OR和EXCEPT，來新增更多條件。 然後，您可以預覽 **[!UICONTROL Corresponding SQL query...]** 您的准則組合。 For more on this refer to this [section](../../platform/using/defining-filter-conditions.md#building-expressions).

   如果您日後想要重新使用篩選，請加以儲存。

   ![](assets/s_user_segmentation_query_advanced.png)

## 新增資料 {#adding-data}

附加欄可讓您收集有關目標人口的其他資訊，例如合約編號、電子報訂閱或來源。 此資料可儲存在Adobe Campaign資料庫或外部資料庫中。

連結 **[!UICONTROL Add data...]** 可讓您選取要收集的其他資料。

![](assets/wf_add_data_link.png)

首先，選擇要添加的資料類型：

![](assets/wf_add_data_1st_option.png)

* 選取 **[!UICONTROL Data linked to the filtering dimension]** 以選取Adobe Campaign資料庫中的資料。
* 選擇 **[!UICONTROL External data]** 從外部資料庫添加資料。 只有在您購買了Federated Data Access選項時， **此選項才可用** 。 有關詳細資訊，請參 [閱訪問外部資料庫(FDA)](../../workflow/using/accessing-an-external-database--fda-.md)。
* 選取 **[!UICONTROL An offer proposition]** 選項以新增一組欄，讓您儲存選件引擎產生的最佳提案。 只有在您購買了 **Interaction** 模組時，才可使用此選項。

如果平台上未安裝可選模組，則不顯示此階段。 你會被帶到下一個階段。

若要新增Adobe Campaign資料庫中的資料：

1. 選擇要添加的資料類型。 這可以是屬於篩選維度的資料，或是儲存在連結表格中的資料。

   ![](assets/query_add_columns.png)

1. 如果資料屬於查詢的篩選維，只需在可用欄位清單中選擇它，即可在輸出列中顯示。

   ![](assets/wf_add_data_field_selection.png)

   您可以新增：

   * 根據來自目標人口的資料或匯總（上個月的待定購買數、收據的平均金額等）計算的欄位。 例如，請轉至「選 [擇資料」](../../workflow/using/targeting-data.md#selecting-data)。
   * 使用輸出列清單右 **[!UICONTROL Add]** 側的按鈕建立的新欄位。

      您也可以新增資訊集合，例如合約清單、最後5個交貨等。 系列會與欄位相符，欄位可針對相同的描述檔（1-N關係）有多個值。 如需詳細資訊，請參閱「編 [輯其他資料」](../../workflow/using/targeting-data.md#editing-additional-data)。

要添加連結到目標人口的資訊集，請執行以下操作：

1. 在嚮導的第一個步驟中，選擇以下 **[!UICONTROL Data linked to the filtering dimension]** 選項：
1. 選擇包含要收集的資訊的表，然後按一下 **[!UICONTROL Next]**。

   ![](assets/wf_add_data_linked_table.png)

1. 如有必要，請在欄位中選取其中一個值，以指定您要保留的系列元素 **[!UICONTROL Data collected]** 數。 依預設，系列的所有行都會復原，然後依照下列步驟中指定的條件進行篩選。

   * 如果系列的單一元素與此系列的篩選條件一致，請在欄位 **[!UICONTROL Single row]** 中選 **[!UICONTROL Data collected]** 取。

      >[!CAUTION]
      >
      >此模式優化了由於集合元素上有直接聯繫而生成的SQL查詢。
      >
      >如果不尊重初始條件，結果可能有缺陷（缺少線或重疊線）。

   * 如果選擇恢復幾行(**[!UICONTROL Limit the line count]**)，可以指定要收集的行數。
   * 如果收集的欄包含匯總，例如宣告的失敗次數、網站的平均支出等。 您可以使用 **[!UICONTROL Aggregates]** 值。
   ![](assets/query_add_collection_param.png)

1. 指定系列的子選取範圍。 例如：僅限過去15天內購買。

   ![](assets/query_add_columns_collection_filter.png)

1. 如果您已選取 **[!UICONTROL Limit the line count]** 選項，請定義篩選收集資料的順序。 一旦收集的行數超過您指定要保留的行數，篩選順序就可讓您指定要保留的行。

## 範例：以簡單收件者屬性為目標 {#example--targeting-on-simple-recipient-attributes}

在以下示例中，查詢試圖確定18至30歲在法國生活的男子。 此查詢將用於工作流程中，例如使其成為獨家選件。

>[!NOTE]
>
>本節將提供其他查詢 [示例](../../workflow/using/querying-recipient-table.md)。

1. 為查詢命名，然後選擇 **[!UICONTROL Edit query...]** 連結。
1. 在可 **[!UICONTROL Filtering conditions]** 用篩選器類型清單中選擇。
1. 輸入建議目標的不同標準。 以下條件是使用AND選項組合的。 要納入選舉，接受者必須滿足以下四個條件：

   * 標題為「Mr」的收件者(也可使用「性別」欄位 **找到** ，並選取「 **Male** 」作為值)。
   * 30歲以下的收件者。
   * 18歲以上的收件者。
   * 住在法國的收件者。
   ![](assets/query_example.png)

   您可以查看與條件組合匹配的SQL:

   ![](assets/query_example_sql.png)

1. 您可以在相關標籤中預覽符合您查詢的收件者，以檢查標準是否正確：

   ![](assets/query_example_preview.png)

1. 儲存您的篩選條件，以便您稍後再按一下 **[!UICONTROL Finish]** >再次使 **[!UICONTROL OK]**&#x200B;用。
1. 透過新增其他活動，繼續編輯您的工作流程。 啟動後，上一個查詢步驟完成後，會顯示找到的收件者數。 您可以使用滑鼠快顯功能表(按一下滑鼠右鍵>轉場> **[!UICONTROL Display the target...]**)，顯示更多詳細資訊。

   ![](assets/query_example_result.png)

## 輸出參數 {#output-parameters}

* tableName
* 架構
* recCount

這三個值集標識查詢所定位的人口。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常是nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。

此值是工作表的模式。 此參數對於包含和的所有轉場都 **[!UICONTROL tableName]** 有效 **[!UICONTROL schema]**。

## 最佳化查詢 {#optimizing-queries}

下節提供最佳實務，以最佳化在Adobe Campaign上執行的查詢，以限制資料庫的工作量並改善使用者體驗。

### 連接和索引 {#joins-and-indexes}

* 高效查詢依賴索引。
* 對所有連接使用索引。
* 在架構上定義連結將決定連接條件。 連結的表在主鍵上應有唯一的索引，且連接應在此欄位上。
* 通過在數字欄位上定義鍵（而不是字串欄位）來執行聯接。
* 避免執行外連接。 盡可能使用零ID記錄來實現外連接功能。
* 為聯接使用正確的資料類型。

   確保該 `where` 子句與欄位的類型相同。

   一個常見的錯誤是：其 `iBlacklist='3'` 中 `iBlacklist` 是數值欄位，並 `3` 表示文字值。

   請確定您知道查詢的執行計畫。 避免完整表掃描，尤其是每分鐘執行的即時查詢或近乎即時的查詢。

有關詳細資訊，請參[閱資料模型最佳實踐](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html)[和資料庫映射節](../../configuration/using/database-mapping.md) 。

### 函式 {#functions}

* 小心這種功能 `Lower(...)`。 使用Lower函式時，不使用Index。
* 使用「贊」指令或「上」或「下」指令仔細檢查查詢。 在用戶輸入上應用「上」，而不是在資料庫欄位上。

   For more on functions, refer to [this section](../../platform/using/defining-filter-conditions.md#list-of-functions).

### 篩選維度 {#filtering-dimensions}

使用查詢的篩選維度，而不是使用&quot;exists sach&quot;運算子。

![](assets/optimize-queries-filtering.png)

在查詢中，篩選條件中的「存在（如）」條件不有效。 它們等效於SQL中的子查詢：

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

最佳實務是改用查詢的篩選維度：

![](assets/optimize-queries-filtering2.png)

SQL中的篩選維等效於內部連接：

`select iRecipientId from nmsRecipient INNER JOIN nmsBroadLog ON (...)`

For more on filtering dimensions, refer to [this section](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).

### 建築 {#architecture}

* 建立與生產平台類似的卷、參數和架構開發平台。
* 在開發與生產環境中使用相同的值。 請盡量使用相同的：

   * 作業系統、
   * 版本、
   * 資料、
   * 應用程式、
   * 卷。
   >[!NOTE]
   >
   >在開發環境中運作的功能可能無法在資料可能不同的生產環境中運作。 嘗試找出主要差異，以預測風險並準備解決方案。

* 建立與目標卷匹配的配置。 大卷需要特定配置。 對100,000個收件者有效的設定，可能無法對10,000,000個收件者有效。

   考慮系統上線時的擴展方式。 只是因為某種東西可以小規模運作，並不意味著它適合大量使用。 測試時，應使用與生產卷相似的卷。 您還應評估在尖峰時間、尖峰天數以及整個項目生命週期中卷（調用數、資料庫大小）的更改的影響。

---
product: campaign
title: 查詢
description: 進一步瞭解「查詢」工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity, Query Editor
exl-id: 20d03627-cd56-46da-bc02-73b48a02a350
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1629'
ht-degree: 1%

---

# 查詢{#query}



## 建立查詢 {#creating-a-query}

查詢可讓您根據條件選取目標。 您可以將區段代碼與查詢結果相關聯，並在其中插入其他資料。
如需查詢範例的詳細資訊，請參閱此 [本節](querying-recipient-table.md).

>[!NOTE]
>
>使用Oracle時，查詢活動與CLOB欄位不相容。

![](assets/s_user_segmentation_wizard_9.png)

有關使用和管理其他資料的詳細資訊，請參閱 [新增資料](#adding-data).

此 **[!UICONTROL Edit query...]** 連結可讓您透過下列方式定義母體的目標定位型別、限制和選擇標準：

1. 選取目標定位和篩選維度。 依預設，會從收件者中選取目標。 限制篩選器的清單與用於傳遞目標定位的清單相同。

   目標維度與我們將處理的元素型別（例如作業所定位的母體）一致。

   篩選維度可讓您收集這些元素，例如與目標人員（合約、完整和最終結算等）相關的資訊。

   有關詳細資訊，請參閱 [目標定位和篩選維度](building-a-workflow.md#targeting-and-filtering-dimensions).

   ![](assets/s_user_segmentation_query_edit.png)

   如有需要，可透過選取「 」，以入站轉變中的資料為基礎進行查詢 **[!UICONTROL Temporary schema]** 選擇目標定位和篩選維度時。

   ![](assets/query_temporary_table.png)

1. 使用精靈定義母體。 要輸入的欄位可能會因目標型別而異。 您可以使用目前的條件預覽目標母體 **[!UICONTROL Preview]** 標籤。

   有關建立和使用篩選器或查詢的詳細資訊，請參閱此 [區段](../../platform/using/filtering-options.md).

   ![](assets/s_user_segmentation_wizard.png)

1. 如果您已選取 **[!UICONTROL Filtering conditions]** 在步驟1或使用 **[!UICONTROL Filters]** > **[!UICONTROL Advanced filter...]** 選項，之後您將必須手動新增篩選條件。

   您也可以核取對應的方塊，以新增資料分組條件。 若要這麼做，篩選維度必須與查詢的目標維度不同。 如需分組的詳細資訊，請參閱此 [區段](querying-using-grouping-management.md).

   您也可以使用運算式產生器，並將其與邏輯選項AND、OR和EXCEPT結合，以新增更多條件。 然後，您可以預覽 **[!UICONTROL Corresponding SQL query...]** 您的條件組合。 如需詳細資訊，請參閱此 [區段](../../platform/using/defining-filter-conditions.md#building-expressions).

   如果您稍後要重複使用篩選器，請儲存篩選器。

   ![](assets/s_user_segmentation_query_advanced.png)

## 新增資料 {#adding-data}

其他欄可讓您收集目標母體的其他資訊，例如合約編號、電子報訂閱或來源。 此資料可以儲存在Adobe Campaign資料庫或外部資料庫中。

此 **[!UICONTROL Add data...]** 連結可讓您選取要收集的其他資料。

![](assets/wf_add_data_link.png)

首先，選取要新增的資料型別：

![](assets/wf_add_data_1st_option.png)

* 選取 **[!UICONTROL Data linked to the filtering dimension]** 以選取Adobe Campaign資料庫中的資料。
* 選取 **[!UICONTROL External data]** 從外部資料庫新增資料。 此選項僅在您已購買 **同盟資料存取** 選項。 有關詳細資訊，請參閱 [存取外部資料庫(FDA)](accessing-an-external-database--fda-.md).
* 選取 **[!UICONTROL An offer proposition]** 用於新增一組欄的選項，可讓您儲存優惠方案引擎產生的最佳主張。 此選項僅在您已購買 **互動** 模組。

如果平台上未安裝選用模組，則不會顯示此階段。 您將直接進入下一個階段。

若要從Adobe Campaign資料庫新增資料：

1. 選取您要新增的資料型別。 這可以是屬於篩選維度的資料，或是儲存在連結表格中的資料。

   ![](assets/query_add_columns.png)

1. 如果資料屬於查詢的篩選維度，只需在可用欄位清單中選取它，即可在輸出欄中顯示它。

   ![](assets/wf_add_data_field_selection.png)

   您可以新增：

   * 根據從目標母體或彙總（上個月內未決購買的次數、收據的平均金額等）取得的資料計算的欄位。 例如，前往 [選取資料](targeting-data.md#selecting-data).
   * 新欄位，使用建立 **[!UICONTROL Add]** 輸出欄清單右側的按鈕。

      您也可以新增一組資訊，例如合約清單、最近5次傳遞等。 集合與相同設定檔可以有多個值的欄位一致（1-N關係）。 有關詳細資訊，請參閱 [編輯其他資料](targeting-data.md#editing-additional-data).

若要新增連結至目標母體的資訊集合：

1. 在精靈的第一步，選取 **[!UICONTROL Data linked to the filtering dimension]** 選項：
1. 選取包含您要收集資訊的表格，然後按一下 **[!UICONTROL Next]**.

   ![](assets/wf_add_data_linked_table.png)

1. 如有必要，請選取下列其中一個值，以指定要保留的集合元素數量： **[!UICONTROL Data collected]** 欄位。 依預設，會復原集合的所有行，然後根據下列步驟中指定的條件進行篩選。

   * 如果集合的單一元素符合此集合的篩選條件，請選取 **[!UICONTROL Single row]** 在 **[!UICONTROL Data collected]** 欄位。

      >[!IMPORTANT]
      >
      >此模式會最佳化由於收集元素上的直接連線點而產生的SQL查詢。
      >
      >如果未遵循初始條件，結果可能會有瑕疵（缺少線或重疊線）。

   * 如果您選擇復原數行(**[!UICONTROL Limit the line count]**)您可以指定要收集的行數。
   * 如果收集的欄包含彙總，例如宣告的失敗次數、網站上的平均費用支出等。 您可以使用 **[!UICONTROL Aggregates]** 值。

   ![](assets/query_add_collection_param.png)

1. 指定集合的子選取範圍。 例如：僅限過去15天的購買。

   ![](assets/query_add_columns_collection_filter.png)

1. 如果您已選取 **[!UICONTROL Limit the line count]** 選項，定義篩選所收集資料的順序。 一旦收集的行數超過您指定要保留的行數時，篩選順序可讓您指定要保留的行。

## 範例：對簡單收件者屬性進行目標定位 {#example--targeting-on-simple-recipient-attributes}

在以下範例中，查詢會尋找年齡介於18至30歲之間且居住在法國的男性。 例如，此查詢將用於工作流程，目的是使其成為專屬選件。

>[!NOTE]
>
>其他查詢範例顯示於 [本節](querying-recipient-table.md).

1. 為查詢命名，然後選取 **[!UICONTROL Edit query...]** 連結。
1. 選取 **[!UICONTROL Filtering conditions]** 在可用的篩選器型別清單中。
1. 為建議的目標輸入不同的條件。 這裡的標準是使用AND選項結合的。 收件者必須滿足下列四個條件，才能納入選取範圍：

   * 標題為「先生」的收件者（也可以使用找到）。 **性別** 欄位並選取 **男性** 作為值)。
   * 30歲以下的收件者。
   * 18歲以上的收件者。
   * 居住在法國的收件者。

   ![](assets/query_example.png)

   您可以檢視符合條件組合的SQL：

   ![](assets/query_example_sql.png)

1. 您可以在相關索引標籤中預覽符合您查詢的收件者，以檢查條件是否正確：

   ![](assets/query_example_preview.png)

1. 儲存您的篩選器，以便您日後可以按一下 **[!UICONTROL Finish]** > **[!UICONTROL OK]**.
1. 新增其他活動以繼續編輯工作流程。 一旦啟動且完成先前的查詢步驟，就會顯示找到的收件者數目。 您可以使用滑鼠躍現式選單顯示更多細節(以滑鼠右鍵按一下轉變> **[!UICONTROL Display the target...]**)。

   ![](assets/query_example_result.png)

## 輸出引數 {#output-parameters}

* tableName
* 綱要
* recCount

這組三個值會識別查詢所定位的母體。 **[!UICONTROL tableName]** 是記錄目標識別碼的資料表名稱， **[!UICONTROL schema]** 為母體的結構描述（通常為nms：recipient）和 **[!UICONTROL recCount]** 是表格中的元素數量。

此值是工作表的結構描述。 此引數適用於所有具有下列專案的轉變 **[!UICONTROL tableName]** 和 **[!UICONTROL schema]**.

## 最佳化您的查詢 {#optimizing-queries}

以下章節提供最佳實務，以最佳化Adobe Campaign上執行的查詢，限制資料庫上的工作負載並改善使用者體驗。

### 聯結和索引 {#joins-and-indexes}

* 有效的查詢需要索引。
* 對所有聯結使用索引。
* 在結構描述上定義連結將決定加入條件。 連結的資料表應在主索引鍵上有一個唯一索引，而且聯結應在此欄位上。
* 在數值欄位上定義鍵而非字串欄位，以執行聯結。
* 避免執行外部聯結。 儘可能使用Zero ID記錄來達到外部聯結功能。
* 使用正確的資料型別進行聯結。

   確保 `where` 子句的型別與欄位相同。

   常見的錯誤是： `iBlacklist='3'` 位置 `iBlacklist` 為數值欄位，且 `3` 表示文字值。

   請確定您知道查詢的執行計畫。 避免完整表格掃描，尤其是即時查詢或幾乎每分鐘執行的即時查詢。

   如需詳細資訊，請根據您的Campaign版本，參閱下列章節：

   ![](assets/do-not-localize/v7.jpeg)[  Campaign v7 文件](../../configuration/using/database-mapping.md)

   ![](assets/do-not-localize/v8.png)[  Campaign v8 文件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/shemas-forms/database-mapping.html)

### 函式 {#functions}

* 請注意以下功能： `Lower(...)`. 使用Lower函式時，不會使用Index。
* 仔細檢查使用「like」指示或「upper」或「lower」指示的查詢。 在使用者輸入上套用「Upper」，而不是在資料庫欄位上。

   有關函式的詳細資訊，請參閱 [本節](../../platform/using/defining-filter-conditions.md#list-of-functions).

### 篩選維度 {#filtering-dimensions}

使用查詢的篩選維度，而非使用「存在方式」運運算元。

![](assets/optimize-queries-filtering.png)

在查詢中，篩選條件中的「存在」等條件無效。 它們等同於SQL中的子查詢：

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

最佳實務建議改用查詢的篩選維度：

![](assets/optimize-queries-filtering2.png)

SQL中篩選維度的對等項是內部聯結：

`select iRecipientId from nmsRecipient INNER JOIN nmsBroadLog ON (...)`

如需篩選維度的詳細資訊，請參閱 [本節](building-a-workflow.md#targeting-and-filtering-dimensions).

### 架構 {#architecture}

* 建立開發平台，使用與生產平台類似的磁碟區、引數和架構。
* 在開發和生產環境中使用相同的值。 儘可能使用相同的：

   * 作業系統,
   * 版本,
   * 資料,
   * 應用程式,
   * 磁碟區。

   >[!NOTE]
   >
   >適用於開發環境的功能，在資料可能不同的生產環境中可能無法運作。 嘗試識別主要差異以預測風險並準備解決方案。

* 設定符合目標磁碟區的設定。 大型磁碟區需要特定的設定。 適用於100,000位收件者的設定可能無法適用於10,000,000位收件者。

   考慮系統上線時的擴充方式。 只是因為某些東西在小型上運作並不意味著它適合較大的體積。 應該使用與生產中的磁碟區類似的磁碟區來進行測試。 您也應該評估在高峰時間、尖峰天數和整個專案期限內磁碟區變更（呼叫次數、資料庫大小）的影響。

---
product: campaign
title: 查詢
description: 進一步瞭解查詢工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows, Targeting Activity, Query Editor
exl-id: 20d03627-cd56-46da-bc02-73b48a02a350
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '1638'
ht-degree: 1%

---

# 查詢{#query}



## 建立查詢 {#creating-a-query}

查詢可讓您根據條件選取目標。 您可以將區段代碼與查詢結果相關聯，並插入其他資料。
有關查詢範例的詳細資訊，請參閱以下內容 [本節](querying-recipient-table.md).

>[!NOTE]
>
>使用Oracle時，查詢活動與CLOB欄位不相容。

![](assets/s_user_segmentation_wizard_9.png)

有關使用和管理其他資料的詳細資訊，請參閱 [新增資料](#adding-data).

此 **[!UICONTROL Edit query...]** 連結可讓您透過下列方式定義母體的目標定位型別、限制和選取條件：

1. 選取目標定位和篩選維度。 預設情況下，會從收件者中選取目標。限制篩選器的清單與用於傳送目標定位的清單相同。

   目標維度與我們正在處理的元素型別一致，例如作業所定位的母體。

   篩選維度可讓您收集這些元素，例如與目標人員相關的資訊（合約、完整和最終結算等）。

   有關詳細資訊，請參閱 [目標定位和篩選維度](building-a-workflow.md#targeting-and-filtering-dimensions).

   ![](assets/s_user_segmentation_query_edit.png)

   如有需要，可透過選取「 」以入站轉變的資料為基礎進行查詢 **[!UICONTROL Temporary schema]** 選擇目標定位和篩選維度時。

   ![](assets/query_temporary_table.png)

1. 使用精靈定義母體。 要輸入的欄位可能會因目標型別而異。 您可以使用目前的條件預覽目標母體 **[!UICONTROL Preview]** 標籤。

   有關建立和使用篩選器或查詢的詳細資訊，請參閱此 [區段](../../platform/using/filtering-options.md).

   ![](assets/s_user_segmentation_wizard.png)

1. 如果您已選取 **[!UICONTROL Filtering conditions]** 在步驟1或使用 **[!UICONTROL Filters]** > **[!UICONTROL Advanced filter...]** 選項，之後您將必須手動新增篩選准則。

   您也可以核取對應的方塊，以新增資料分組條件。 若要這麼做，篩選維度必須與查詢的目標維度不同。 如需分組的詳細資訊，請參閱此 [區段](querying-using-grouping-management.md).

   您也可以使用運算式產生器，將其與邏輯選項AND、OR和EXCEPT結合，以新增更多條件。 然後您可以預覽 **[!UICONTROL Corresponding SQL query...]** 您的條件組合。 如需詳細資訊，請參閱本節 [區段](../../platform/using/defining-filter-conditions.md#building-expressions).

   如果您稍後要重複使用篩選器，請儲存篩選器。

   ![](assets/s_user_segmentation_query_advanced.png)

## 新增資料 {#adding-data}

其他欄可讓您收集目標母體的其他資訊，例如合約編號、電子報訂閱或來源。 此資料可儲存在Adobe Campaign資料庫或外部資料庫中。

此 **[!UICONTROL Add data...]** 連結可讓您選取要收集的其他資料。

![](assets/wf_add_data_link.png)

首先，選取要新增的資料型別：

![](assets/wf_add_data_1st_option.png)

* 選取 **[!UICONTROL Data linked to the filtering dimension]** 以選取Adobe Campaign資料庫中的資料。
* 選取 **[!UICONTROL External data]** 從外部資料庫新增資料。 此選項僅在您已購買 **同盟資料存取** 選項。 有關詳細資訊，請參閱 [存取外部資料庫(FDA)](accessing-an-external-database-fda.md).
* 選取 **[!UICONTROL An offer proposition]** 用於新增一組欄的選項，可讓您儲存優惠方案引擎產生的最佳主張。 此選項僅在您已購買 **互動** 模組。

如果平台上未安裝選用模組，則此階段不會顯示。 您將直接進入下一個階段。

若要從Adobe Campaign資料庫新增資料：

1. 選取您要新增的資料型別。 這可以是屬於篩選維度的資料，或是儲存在連結表格中的資料。

   ![](assets/query_add_columns.png)

1. 如果資料屬於查詢的篩選維度，只需在可用欄位清單中選取該資料，即可在輸出欄中顯示該資料。

   ![](assets/wf_add_data_field_selection.png)

   您可以新增：

   * 根據從目標母體或彙總（上個月內未決購買的次數、收款的平均金額等）中取得的資料計算出的欄位。 例如，前往 [選取資料](targeting-data.md#selecting-data).
   * 新欄位，使用建立 **[!UICONTROL Add]** 按鈕在輸出欄清單的右側。

     您也可以新增資訊集合，例如合約清單、最近5次傳遞等。 集合與相同設定檔可以有多個值的欄位一致（1-N關係）。 有關詳細資訊，請參閱 [編輯其他資料](targeting-data.md#editing-additional-data).

若要新增連結至目標母體的資訊集合：

1. 在精靈的第一步，選取 **[!UICONTROL Data linked to the filtering dimension]** 選項：
1. 選取包含要收集資訊的表格，然後按一下 **[!UICONTROL Next]**.

   ![](assets/wf_add_data_linked_table.png)

1. 必要時，請選取下列其中一個值，以指定要保留的集合元素數目： **[!UICONTROL Data collected]** 欄位。 依預設，會復原集合的所有行，然後根據下列步驟指定的條件進行篩選。

   * 如果集合的單一元素與此集合的篩選條件一致，請選取 **[!UICONTROL Single row]** 在 **[!UICONTROL Data collected]** 欄位。

     >[!IMPORTANT]
     >
     >此模式會最佳化由於收集元素上的直接連線而產生的SQL查詢。
     >
     >如果未遵循初始條件，結果可能會有瑕疵（遺漏或重疊線）。

   * 如果您選擇復原數行(**[!UICONTROL Limit the line count]**)您可以指定要收集的行數。
   * 如果收集的欄包含彙總，例如宣告的失敗次數、網站的平均費用性列管等。 您可以使用 **[!UICONTROL Aggregates]** 值。

   ![](assets/query_add_collection_param.png)

1. 指定集合的子選取專案。 例如：僅過去15天的購買。

   ![](assets/query_add_columns_collection_filter.png)

1. 如果您已選取 **[!UICONTROL Limit the line count]** 選項，定義篩選收集資料的順序。 一旦收集的行數超過您指定要保留的行數時，篩選順序可讓您指定要保留的行。

## 範例：在簡單收件者屬性上鎖定目標 {#example--targeting-on-simple-recipient-attributes}

在以下範例中，查詢會尋找年齡介於18至30歲之間且居住在法國的男性。 例如，此查詢將用於工作流程，旨在使其成為專屬選件。

>[!NOTE]
>
>其他查詢範例顯示於 [本節](querying-recipient-table.md).

1. 為查詢命名，然後選取 **[!UICONTROL Edit query...]** 連結。
1. 選取 **[!UICONTROL Filtering conditions]** 在可用的篩選器型別清單中。
1. 為建議的目標輸入不同的條件。 這裡的條件使用AND選項結合。 收件者必須符合下列四個條件，才能納入選取範圍：

   * 標題為&quot;Mr&quot;的收件者（也可使用找到） **性別** 欄位並選取 **男性** 作為值)。
   * 30歲以下的收件者。
   * 18歲以上的收件者。
   * 住在法國的收件者。

   ![](assets/query_example.png)

   您可以檢視符合條件組合的SQL：

   ![](assets/query_example_sql.png)

1. 您可以在相關索引標籤中預覽符合您查詢的收件者，以檢查條件是否正確：

   ![](assets/query_example_preview.png)

1. 儲存您的篩選器，以便日後透過按一下 **[!UICONTROL Finish]** > **[!UICONTROL OK]**.
1. 新增其他活動以繼續編輯工作流程。 一旦啟動且完成先前的查詢步驟後，就會顯示找到的收件者數目。 您可以使用滑鼠躍現式選單(在轉變上按一下滑鼠右鍵> **[!UICONTROL Display the target...]**)。

   ![](assets/query_example_result.png)

## 輸出引數 {#output-parameters}

* tableName
* 綱要
* recCount

這組三個值會識別查詢所定位的母體。 **[!UICONTROL tableName]** 是記錄目標識別碼的資料表名稱， **[!UICONTROL schema]** 是母體的綱要（通常是nms：recipient）和 **[!UICONTROL recCount]** 是表格中的元素數。

此值是工作表的結構描述。 此引數適用於所有具有的轉變 **[!UICONTROL tableName]** 和 **[!UICONTROL schema]**.

## 最佳化查詢 {#optimizing-queries}

下節提供最佳實務，以最佳化Adobe Campaign上執行的查詢，限制資料庫上的工作負載並改善使用者體驗。

### 聯結和索引 {#joins-and-indexes}

* 有效的查詢需要索引。
* 使用索引來連線所有聯結。
* 在架構上定義連結將決定加入條件。 連結資料表的主索引鍵上應該有唯一索引，而且聯結應該在此欄位上。
* 在數值欄位上定義鍵而非字串欄位，以執行聯結。
* 避免執行外部聯結。 只要有可能，請使用Zero ID記錄來實現外部聯結功能。
* 使用正確的資料型別進行聯結。

  確保 `where` 子句與欄位型別相同。

  常見的錯誤是： `iBlacklist='3'` 位置 `iBlacklist` 是數值欄位，且 `3` 表示文字值。

  確定您知道查詢的執行計畫。 避免進行完整的表格掃描，尤其是針對每分鐘執行的即時查詢或近乎即時查詢。

  如需詳細資訊，請參閱Campaign版本的相關章節：

  ![](assets/do-not-localize/v7.jpeg)[Campaign v7檔案](../../configuration/using/database-mapping.md)

  ![](assets/do-not-localize/v8.png)[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/shemas-forms/database-mapping.html)

### 函數 {#functions}

* 請注意以下功能： `Lower(...)`. 使用Lower函式時，不會使用Index。
* 仔細檢查使用「like」指示或「upper」或「lower」指示的查詢。 在使用者輸入上套用「Upper」，而不是在資料庫欄位上套用。

  有關函式的詳細資訊，請參閱 [本節](../../platform/using/defining-filter-conditions.md#list-of-functions).

### 篩選維度 {#filtering-dimensions}

使用查詢的篩選維度，而非使用「存在方式」運運算元。

![](assets/optimize-queries-filtering.png)

在查詢中，篩選器中的「存在（例如）」條件無效。 它們等同於SQL中的子查詢：

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

最佳實務建議改用查詢的篩選維度：

![](assets/optimize-queries-filtering2.png)

SQL中篩選維度的對等項是內部聯結：

`select iRecipientId from nmsRecipient INNER JOIN nmsBroadLog ON (...)`

如需篩選維度的詳細資訊，請參閱 [本節](building-a-workflow.md#targeting-and-filtering-dimensions).

### 架構 {#architecture}

* 使用與生產平台類似的磁碟區、引數和架構來建置開發平台。
* 在開發和生產環境中使用相同的值。 請儘可能使用相同專案：

   * 作業系統，
   * 版本，
   * 資料，
   * 應用程式，
   * 磁碟區。

  >[!NOTE]
  >
  >在開發環境中運作的功能，在資料可能不同的生產環境中可能無法運作。 嘗試識別主要差異以預測風險並準備解決方案。

* 設定符合目標磁碟區的組態。 大型磁碟區需要特定的設定。 100,000位收件者適用的設定可能無法處理10,000,000位收件者。

  考慮系統上線時的擴充方式。 只是因為某個小規模的東西可以運作，並不表示它適合較大的體積。 應該使用與生產中的磁碟區類似的磁碟區來進行測試。 您也應該評估在高峰時間、尖峰天數和整個專案期間磁碟區變更（呼叫數、資料庫大小）的影響。

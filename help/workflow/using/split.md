---
product: campaign
title: 分割
description: 瞭解有關拆分工作流活動的詳細資訊
feature: Workflows, Targeting Activity
exl-id: 4204350a-c2d2-4033-9bdf-87b49d8211b9
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '1935'
ht-degree: 0%

---

# 分割{#split}

![](../../assets/common.svg)

A **拆分**-type活動允許您將目標拆分為多個子集。 該目標是利用所有接收到的結果構建的：因此，必須完成所有以前的活動才能執行此活動。

此活動不會觸發入站總體的聯合。 如果一個拆分活動中出現多個過渡，我們建議插入 **[!UICONTROL Union]** 前面的活動。

有關使用的拆分活動的示例，請參閱 [使用「拆分」活動建立子集](targeting-data.md#creating-subsets-using-the-split-activity)。

有關如何使用「拆分」活動使用篩選條件將目標分割為不同種群的示例的說明，請參見 [此部分](cross-channel-delivery-workflow.md)。

在中提供了一個示例，說明如何在拆分活動中使用實例變數 [此部分](javascript-scripts-and-templates.md)。

要配置此活動，請在 **[!UICONTROL Subsets]** 頁籤，然後選擇 **[!UICONTROL General]** 頁籤。

## 建立子集 {#creating-subsets}

要建立子集：

1. 按一下匹配欄位中的標籤，然後選擇要應用的篩選器。
1. 要篩選入站人口，請選擇 **[!UICONTROL Add a filtering condition]** ，然後按一下 **[!UICONTROL Edit...]** 的子菜單。

   選擇要應用到資料的篩選器類型，以將其包含在此集中。

   該過程與 **查詢**-type活動。

   >[!NOTE]
   >
   >最多可以篩選兩個外部資料庫(FDA)中的資料。

1. 您可以指定要從目標中提取的記錄的最大數量以建立子集。 要執行此操作，請檢查 **[!UICONTROL Limit the selected records]** ，然後按一下 **[!UICONTROL Edit...]** 的子菜單。

   通過嚮導，您可以選擇此子集的記錄的選擇模式。 步驟可在 [限制子集記錄數](#limiting-the-number-of-subset-records)。

   ![](assets/s_user_segmentation_partage4.png)

1. 如果你願意，你可以 **添加其他子集** 使用 **[!UICONTROL Add]** 按鈕

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Enable overlapping of output populations]** 選項，按頁籤的順序建立子集。 使用此窗口右上部分中的箭頭可移動它們。 例如，如果第一個子集恢復了初始種群的70%，那麼下一個子集將只將其選擇標準應用於剩餘的30%，依此類推。

   對於建立的每個子集，將向拆分活動添加出站轉移。

   ![](assets/s_user_segmentation_partage_add2.png)

   您可以選擇生成單個出站轉移（並使用段代碼標識集，例如）:要執行此操作，請選擇 **[!UICONTROL Generate subsets in the same table]** 的上界 **[!UICONTROL General]** 頁籤。

   如果完成，則每個子集的段代碼自動儲存在附加列中。 此列可在交貨級別的個性化欄位中訪問。

## 限制子集記錄數 {#limiting-the-number-of-subset-records}

如果不希望使用子集中包含的全部填充，則可以限制其包含的記錄數。

1. 在子集編輯窗口中，檢查 **[!UICONTROL Limit the selected records]** ，然後按一下 **[!UICONTROL Edit...]** 的子菜單。
1. 選擇所選的限制類型：

   * **[!UICONTROL Activate random sampling]**:此選項取隨機的記錄樣本。 應用的隨機採樣類型取決於資料庫引擎。
   * **[!UICONTROL Keep only the first records after sorting]**:此選項允許您基於一個或多個排序順序定義限制。 如果選擇 **[!UICONTROL Age]** 欄位作為分類標準，100作為限制，只保留最小的100個收件人。
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**:此選項組合了前兩個選項。 它允許您基於一個或多個排序順序定義限制，然後，如果某些記錄的值與定義的標準相同，則對第一個記錄應用隨機選擇。

      例如，如果您選擇 **[!UICONTROL Age]** 欄位作為排序標準，然後您定義限制為100，但資料庫中2000個最年輕的收件者都是18個，然後將從這2000個收件者中隨機選擇100個收件者。
   ![](assets/s_user_segmentation_partage_wz1.png)

1. 如果要定義排序標準，可通過附加步驟定義列和排序順序。

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. 然後選擇資料限制方法。

   ![](assets/s_user_segmentation_partage_wz2.png)

   有幾種方法可以做到這一點：

   * **[!UICONTROL Size (in %)]**:記錄的百分比。 例如，以下配置提取了總人口的10%。

      該百分比適用於初始人口，而不是活動的結果。

   * **[!UICONTROL Size (as a % of the segment)]**:僅與子集而不是與初始種群相關的記錄的百分比。
   * **[!UICONTROL Maximum size]**:最大記錄數。
   * **[!UICONTROL By data grouping]**:您可以根據入站人口的指定欄位中的值設定記錄數限制。 有關此主題的詳細資訊，請參閱 [通過資料分組限制子集記錄數](#limiting-the-number-of-subset-records-by-data-grouping)。
   * **[!UICONTROL By data grouping (in %)]**:您可以根據入站人口的指定欄位中的值使用百分比設定記錄數限制。 有關此主題的詳細資訊，請參閱 [通過資料分組限制子集記錄數](#limiting-the-number-of-subset-records-by-data-grouping)。
   * **[!UICONTROL By data distribution]**:如果您的分組欄位的值太多，或者您希望避免為每個新分解活動再次輸入值，則Adobe Campaign允許您配置 **[!UICONTROL By data distribution]** 限制（可選的分佈式營銷模組）。 有關此內容的詳細資訊，請參閱 [限制每個資料分佈的子集記錄數](#limiting-the-number-of-subset-records-per-data-distribution)。

1. 按一下 **[!UICONTROL Finish]** 以批准記錄選擇條件。 定義的配置隨後顯示在編輯器的中間窗口中。

## 通過資料分組限制子集記錄數 {#limiting-the-number-of-subset-records-by-data-grouping}

您可以按資料分組限制記錄數。 此限制可使用固定值或百分比執行。

例如，如果您選擇 **[!UICONTROL Language]** 欄位作為組欄位，您可以為每個語言定義記錄清單。

1. 選擇資料限制值後，選擇 **[!UICONTROL By data grouping]** 或 **[!UICONTROL By data grouping (as a %)]** 按一下 **[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_partage_wz3.png)

1. 然後選擇分組欄位( **[!UICONTROL Language]** )，然後按一下 **[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_partage_wz4.png)

1. 最後，指定資料分組閾值（使用固定值或百分比，具體取決於先前選擇的分組方法）。 要為每個值設定相同的閾值，例如，如果要將每種語言的記錄數設定為10，請選擇 **[!UICONTROL All data groupings are the same size]** 的雙曲餘切值。 要為每個值設定不同的限制，請選擇 **[!UICONTROL Limitations by grouping value]** 的雙曲餘切值。 這將允許您為英語、法語等選擇其他限制。

   ![](assets/s_user_segmentation_partage_wz5.png)

1. 按一下 **[!UICONTROL Finish]** 以批准限制並返回編輯分解活動。

## 限制每個資料分佈的子集記錄數 {#limiting-the-number-of-subset-records-per-data-distribution}

如果您的分組欄位包含的值太多，或者您希望避免為每個新分解活動重置值，則Adobe Campaign允許您為每個資料分佈建立一個限制。 選擇資料限制值時(有關此主題的詳細資訊，請參閱 [建立子集](#creating-subsets) )，選擇 **[!UICONTROL By data distribution]** 的子菜單。 建立資料分發模板如下所示。

例如 **[!UICONTROL Local approval]** 包含分發模板的活動，請參閱 [使用本地審批活動](using-the-local-approval-activity.md)。

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>要使用此功能，您需要購買「分佈式市場營銷」模組，該模組是「市場活動」選項。 請檢查您的授權合約。

資料分發模板允許您使用分組值清單限制記錄數。 要建立資料分發模板，請應用以下步驟：

1. 要建立資料分發模板，請轉到 **[!UICONTROL Resources > Campaign management > Data distribution]** 按一下 **[!UICONTROL New]**。

   ![](assets/local_validation_data_distribution_1.png)

1. 的 **[!UICONTROL General]** 頁籤，用於輸入分發的標籤和執行上下文（目標維、分發欄位）。

   ![](assets/local_validation_data_distribution_2.png)

   需要輸入以下欄位：

   * **[!UICONTROL Label]**:的子菜單。
   * **[!UICONTROL Targeting dimension]**:輸入要應用資料分佈的目標維， **[!UICONTROL Recipient]** 比如說， 此架構必須始終與目標工作流中使用的資料相容。
   * **[!UICONTROL Distribution field]**:通過目標維選擇欄位。 例如，如果您選擇 **[!UICONTROL Email domain]** 欄位中，收件人清單將按域細分。
   * **[!UICONTROL Distribution type]**:選擇目標限制值在 **[!UICONTROL Distribution]** 頁籤： **[!UICONTROL Percentage]** 或 **[!UICONTROL Set]**。
   * **[!UICONTROL Assignment type]**:選擇資料分發分配類型。 您可以按組或運算子選擇分配，或按本地實體選擇分配。 按本地實體分配 **分佈式營銷**。 有關詳細資訊，請參閱 [節](../../distributed/using/about-distributed-marketing.md)。
   * **[!UICONTROL Approval storage]**:如果你 **[!UICONTROL Local approval]** 目標工作流中的活動(請參閱 [本地批准](local-approval.md))，輸入將儲存批准結果的架構。 必須為每個目標架構指定一個儲存架構。 如果使用 **[!UICONTROL Recipients]** 目標架構，輸入預設值 **[!UICONTROL Local approval of recipients]** 儲存架構。

      如果在未經本地批准的情況下通過資料分組進行簡單限制，則無需輸入 **[!UICONTROL Approvals storage]** 的子菜單。

1. 如果使用 **[!UICONTROL Local approval]** 活動(請參閱 [本地批准](local-approval.md))，輸入 **[!UICONTROL Advanced settings]** 對於分發模板：

   ![](assets/local_validation_data_distribution_3.png)

   需要輸入以下欄位：

   * **[!UICONTROL Approve targeted messages]**:如果希望從收件人清單中預先選擇所有收件人以供審批，請選中此選項。 如果未選中此選項，則不會預選收件人。

      >[!NOTE]
      >
      >預設選中此選項。

      ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**:允許您定義表達式以在返回通知中顯示交貨標籤。 預設表達式提供有關傳遞的標準標籤（計算字串）的資訊。 您可以修改此表達式。

      ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**:此欄位允許您定義用於在審批和退貨通知中顯示接收人的分組。

      ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**:允許您將Web應用程式連結到收件人清單。 在批准和返回通知中，每個收件人都可按一下，並將連結到所選Web應用程式。 的 **[!UICONTROL Parameters]** 欄位(例如 **[!UICONTROL recipientId]**)，用於配置要在URL和Web應用程式中使用的附加參數。

      ![](assets/local_validation_notification_5.png)

1. 的 **[!UICONTROL Breakdown]** 頁籤中，您可以定義通訊組值清單。

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**:輸入分配值。
   * **[!UICONTROL Percentage / Set]**:輸入連結到每個值的記錄限制（固定或百分比）。

      此列由 **[!UICONTROL Distribution type]** 欄位 **[!UICONTROL General]** 頁籤。

   * **[!UICONTROL Label]**:輸入連結到每個值的標籤。
   * **[!UICONTROL Group or operator]**:如果您使用 **[!UICONTROL Local approval]** 活動(請參閱 [本地批准](local-approval.md))，選擇分配給每個分佈值的運算子或運算子組。

      如果在未經本地批准的情況下通過資料分組進行簡單限制，則無需輸入 **[!UICONTROL Group or operator]** 的子菜單。

      >[!IMPORTANT]
      >
      >確保已為運算子分配了相應的權限。

   * **[!UICONTROL Local entity]**:選擇分配給每個分配值的本地實體。 本地實體用於 **分佈式營銷**。 有關詳細資訊，請參閱 [節](../../distributed/using/about-distributed-marketing.md)。

## 篩選參數 {#filtering-parameters}

按一下 **[!UICONTROL General]** 頁籤。 選擇此拆分的目標維和篩選器維。 如有必要，可更改給定子集的這些尺寸。

![](assets/s_user_segmentation_partage_general.png)

檢查 **[!UICONTROL Generate complement]** 的雙曲餘切值。 補數是入站目標減去子集的聯合。 然後，將向活動添加一個額外的出站轉移，如下所示：

![](assets/s_user_segmentation_partage_compl.png)

要使此選項正常工作，入站資料必須具有主鍵。

例如，如果資料是通過外部資料庫直接讀取的，如Netezza（它不支援索引的概念） **[!UICONTROL Data loading (RDBMS)]** 的 **[!UICONTROL Split]** 活動將不正確。

要避免此情況，可拖放 **[!UICONTROL Enrichment]** 活動時間 **[!UICONTROL Split]** 的子菜單。 在 **[!UICONTROL Enrichment]** 活動，檢查 **[!UICONTROL Keep all additional data from the main set]** 並在附加資料中指定要用於配置 **[!UICONTROL Split]** 的子菜單。 來自的入站轉換的資料 **[!UICONTROL Split]** 然後，活動將本地儲存在Adobe Campaign伺服器上的臨時表中，並且可以正確生成補碼。

的 **[!UICONTROL Enable overlapping of output populations]** 選項，您可以管理屬於多個子集的群：

* 如果未選中該框，拆分活動將確保在多個輸出轉換中不能存在收件人，即使它滿足幾個子集的標準。 它們將位於具有匹配條件的第一個頁籤的目標中。
* 選中該框後，如果收件人符合其篩選條件，則可以在多個子集中找到該收件人。 Adobe Campaign建議使用獨家標準。

## 輸入參數 {#input-parameters}

* 表名
* 架構

每個入站事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* 表名
* 架構
* 記錄計數

這組三個值標識了排除所導致的目標。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常為nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。

與補碼相關聯的過渡具有相同的參數。

---
product: campaign
title: 分割
description: 進一步瞭解分割工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: 4204350a-c2d2-4033-9bdf-87b49d8211b9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 0%

---

# 分割{#split}



A **Split**-type活動可讓您將目標分割成數個子集。 使用所有接收的結果建構目標：所有先前的活動都必須已完成，才能執行此活動。

此活動不會觸發入站母體的聯合。 如果數個轉變位於一個分割活動中，建議插入 **[!UICONTROL Union]** 活動在它前面。

如需所使用分割活動的範例，請參閱 [使用分割活動建立子集](targeting-data.md#creating-subsets-using-the-split-activity).

有關說明如何使用「分割」活動，以使用篩選條件將目標分割為不同母體的範例，請參閱 [本節](cross-channel-delivery-workflow.md).

以下提供如何在分割活動中使用執行個體變數的範例： [本節](javascript-scripts-and-templates.md).

若要設定此活動，請在「 」中定義子集內容和標籤 **[!UICONTROL Subsets]** 標籤，然後在中選擇目標維度 **[!UICONTROL General]** 標籤。

## 建立子集 {#creating-subsets}

若要建立子集：

1. 按一下比對欄位中的標籤，然後選取要套用的篩選器。
1. 若要篩選入站母體，請選取 **[!UICONTROL Add a filtering condition]** 選項，然後按一下 **[!UICONTROL Edit...]** 連結。

   選取要套用至資料的篩選器型別，以將其納入此集。

   此程式與的相同 **查詢**-type活動。

   >[!NOTE]
   >
   >您最多可以篩選兩個外部資料庫(FDA)中的資料。

1. 您可以指定要從目標擷取的最大記錄數，以建立子集。 要執行此操作，請核取 **[!UICONTROL Limit the selected records]** 選項，然後按一下 **[!UICONTROL Edit...]** 連結。

   精靈可讓您選擇此子集記錄的選擇模式。 這些步驟可在以下位置找到： [限制子集記錄的數量](#limiting-the-number-of-subset-records).

   ![](assets/s_user_segmentation_partage4.png)

1. 如果您願意，可以 **新增其他子集** 使用 **[!UICONTROL Add]** 按鈕。

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Enable overlapping of output populations]** 選項未核取，則會以索引標籤的順序建立子集。 使用此視窗右上方的箭頭來移動它們。 舉例來說，如果第一個子集復原了初始母體的70%，則下一個子集只會將其選取條件套用至剩餘的30%，以此類推。

   對於每個建立的子集，外站轉變將會新增到分割活動中。

   ![](assets/s_user_segmentation_partage_add2.png)

   您可以選擇產生單一出站轉變（例如，使用區段代碼識別集）：若要這麼做，請選取 **[!UICONTROL Generate subsets in the same table]** 中的選項 **[!UICONTROL General]** 標籤。

   完成後，每個子集的區段代碼會自動儲存在其他欄中。 您可在傳遞層級的個人化欄位中存取此欄。

## 限制子集記錄的數量 {#limiting-the-number-of-subset-records}

如果您不想使用子集包含的整個母體，您可以限制它包含的記錄數。

1. 在子集編輯視窗中，核取 **[!UICONTROL Limit the selected records]** 選項，然後按一下 **[!UICONTROL Edit...]** 連結。
1. 選取您選擇的限制型別：

   * **[!UICONTROL Activate random sampling]**：此選項會從記錄中隨機取樣。 套用的隨機抽樣型別取決於資料庫引擎。
   * **[!UICONTROL Keep only the first records after sorting]**：此選項可讓您根據一或多個排序順序定義限制。 如果您選取 **[!UICONTROL Age]** 欄位做為排序標準，100做為限制，則只會保留最年輕的100位收件者。
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**：此選項會結合前兩個選項。 它可讓您根據一或多個排序順序定義限制，然後在某些記錄具有與定義條件相同的值時，在第一筆記錄上套用隨機選擇。

     例如，如果您選取 **[!UICONTROL Age]** 欄位做為排序標準，然後您定義100的限制，但資料庫中2000個最年輕的收件者皆為18個，則將從這些2000個收件者中隨機選取100個收件者。

   ![](assets/s_user_segmentation_partage_wz1.png)

1. 如果您想要定義排序標準，另一個步驟可讓您定義欄及排序順序。

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. 然後選擇資料限制方法。

   ![](assets/s_user_segmentation_partage_wz2.png)

   有幾種方法可以做到：

   * **[!UICONTROL Size (in %)]**：記錄的百分比。 例如，下列設定會擷取總母體的10%。

     百分比會套用至初始母體，而非活動結果。

   * **[!UICONTROL Size (as a % of the segment)]**：只與子集相關而不與初始母體相關的記錄百分比。
   * **[!UICONTROL Maximum size]**：記錄數上限。
   * **[!UICONTROL By data grouping]**：您可以根據入站母體的指定欄位中的值，設定記錄數限制。 有關本主題的詳細資訊，請參閱 [依資料分組限制子集記錄數量](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data grouping (in %)]**：您可以使用百分比，根據入站母體的指定欄位中的值來設定記錄數限制。 有關本主題的詳細資訊，請參閱 [依資料分組限制子集記錄數量](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data distribution]**：如果您的分組欄位有太多值，或您想避免為每個新的分割活動再次輸入值，Adobe Campaign可讓您設定 **[!UICONTROL By data distribution]** 限制（選用的分散式行銷模組）。 有關詳細資訊，請參閱 [限制每個資料分佈的子集記錄數](#limiting-the-number-of-subset-records-per-data-distribution).

1. 按一下 **[!UICONTROL Finish]** 以核准記錄選取條件。 然後定義的組態會顯示在編輯器的中間視窗中。

## 依資料分組限制子集記錄數量 {#limiting-the-number-of-subset-records-by-data-grouping}

您可以依資料分組限制記錄數量。 此限制可使用固定值或百分比來執行。

例如，如果您選取 **[!UICONTROL Language]** 欄位做為群組欄位，您可以定義每種語言的記錄清單。

1. 選取資料限制值後，選取 **[!UICONTROL By data grouping]** 或 **[!UICONTROL By data grouping (as a %)]** 並按一下 **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz3.png)

1. 然後選取分組欄位( **[!UICONTROL Language]** 欄位)，然後按一下 **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz4.png)

1. 最後，指定資料分組臨界值（使用固定值或百分比，視先前選取的分組方法而定）。 若要為每個值設定相同的臨界值（例如，如果您要將每種語言的記錄數設為10），請選取 **[!UICONTROL All data groupings are the same size]** 選項。 若要為每個值設定不同的限制，請選取 **[!UICONTROL Limitations by grouping value]** 選項。 這可讓您針對英文、法文等選擇不同的限制。

   ![](assets/s_user_segmentation_partage_wz5.png)

1. 按一下 **[!UICONTROL Finish]** 以核准限制並返回編輯分割活動。

## 限制每個資料分佈的子集記錄數 {#limiting-the-number-of-subset-records-per-data-distribution}

如果您的分組欄位包含太多值，或您想避免為每個新的分割活動重設值，Adobe Campaign可讓您為每個資料分佈建立限制。 選取資料限制值時(如需此主題的詳細資訊，請參閱 [建立子集](#creating-subsets) 部分)，選取 **[!UICONTROL By data distribution]** 選項，然後從下拉式選單中選取範本。 建立資料發佈範本的示例如下。

例如 **[!UICONTROL Local approval]** 具有發佈範本的活動，請參閱 [使用本機核准活動](using-the-local-approval-activity.md).

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>若要使用此函式，您必須購買分散式行銷模組，這是行銷活動選項。 請檢查您的授權合約。

資料分佈範本可讓您使用分組值清單來限制記錄數量。 若要建立資料發佈範本，請套用下列步驟：

1. 若要建立資料發佈範本，請前往 **[!UICONTROL Resources > Campaign management > Data distribution]** 節點並按一下 **[!UICONTROL New]**.

   ![](assets/local_validation_data_distribution_1.png)

1. 此 **[!UICONTROL General]** 索引標籤可讓您輸入發佈的標籤和執行內容（目標維度、發佈欄位）。

   ![](assets/local_validation_data_distribution_2.png)

   需要輸入下列欄位：

   * **[!UICONTROL Label]**：發佈範本的標籤。
   * **[!UICONTROL Targeting dimension]**：輸入要套用資料分佈的目標維度， **[!UICONTROL Recipient]** 例如。 此結構描述必須始終與目標工作流程中使用的資料相容。
   * **[!UICONTROL Distribution field]**：透過目標維度選取欄位。 例如，如果您選取 **[!UICONTROL Email domain]** 欄位，收件者清單將依網域劃分。
   * **[!UICONTROL Distribution type]**：選取目標限制值在中劃分的方式 **[!UICONTROL Distribution]** 標籤： **[!UICONTROL Percentage]** 或 **[!UICONTROL Set]**.
   * **[!UICONTROL Assignment type]**：選取資料分佈指派型別。 您可以依群組或運運算元來指定或依本機實體來指定。 使用本機實體的工作分派 **分散式行銷**. 如需詳細資訊，請參閱此 [區段](../../distributed/using/about-distributed-marketing.md).
   * **[!UICONTROL Approval storage]**：如果您使用 **[!UICONTROL Local approval]** 目標工作流程中的活動(請參閱 [本地核准](local-approval.md))，輸入將儲存核准結果的結構描述。 您必須為每個目標結構描述指定一個儲存結構描述。 如果您使用 **[!UICONTROL Recipients]** 目標結構描述，輸入預設值 **[!UICONTROL Local approval of recipients]** 儲存結構描述。

     在未經本機核准而透過資料分組進行簡單限制的情況下，您不需要輸入 **[!UICONTROL Approvals storage]** 欄位。

1. 如果您使用 **[!UICONTROL Local approval]** 活動(請參閱 [本地核准](local-approval.md))，輸入 **[!UICONTROL Advanced settings]** 對於發佈範本：

   ![](assets/local_validation_data_distribution_3.png)

   需要輸入下列欄位：

   * **[!UICONTROL Approve targeted messages]**：如果您希望從要核准的收件者清單預先選取所有收件者，請核取此選項。 如果未核取此選項，則不會預先選取任何收件者。

     >[!NOTE]
     >
     >此選項預設為勾選。

     ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**：可讓您定義運算式，以在回訪通知中顯示傳送標籤。 預設運算式提供有關傳遞標準標籤（計算字串）的資訊。 您可以修改此運算式。

     ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**：此欄位可讓您定義在核准和傳回通知中顯示收件者的分組。

     ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**：可讓您將網頁應用程式連結至收件者清單。 在核准和回訪通知中，每個收件者都將可點按，並連結至選取的網頁應用程式。 此 **[!UICONTROL Parameters]** 欄位(例如 **[!UICONTROL recipientId]**)可讓您設定要在URL和Web應用程式中使用的其他引數。

     ![](assets/local_validation_notification_5.png)

1. 此 **[!UICONTROL Breakdown]** 索引標籤可讓您定義分佈值清單。

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**：輸入分佈值。
   * **[!UICONTROL Percentage / Set]**：輸入連結至每個值的記錄限制（固定或百分比）。

     此欄由 **[!UICONTROL Distribution type]** 欄位(在 **[!UICONTROL General]** 標籤。

   * **[!UICONTROL Label]**：輸入連結至每個值的標籤。
   * **[!UICONTROL Group or operator]**：如果您使用 **[!UICONTROL Local approval]** 活動(請參閱 [本地核准](local-approval.md))，選取指派給每個分佈值的運運算元或運運算元群組。

     在未經本機核准而透過資料分組進行簡單限制的情況下，您不需要輸入 **[!UICONTROL Group or operator]** 欄位。

     >[!IMPORTANT]
     >
     >請確定已指派適當的許可權給運運算元。

   * **[!UICONTROL Local entity]**：選取指派給每個發佈值的本機實體。 本機實體用於 **分散式行銷**. 如需詳細資訊，請參閱此 [區段](../../distributed/using/about-distributed-marketing.md).

## 篩選引數 {#filtering-parameters}

按一下 **[!UICONTROL General]** 索引標籤來輸入活動標籤。 選取此分割的目標和篩選維度。 如有必要，您可以變更指定子集的這些維度。

![](assets/s_user_segmentation_partage_general.png)

檢查 **[!UICONTROL Generate complement]** 選項，以利用剩餘母體。 補充是入站目標減去子集的聯合。 然後，會將額外的出站轉變新增至活動，如下所示：

![](assets/s_user_segmentation_partage_compl.png)

若要讓此選項正確運作，傳入資料必須具有主索引鍵。

例如，如果資料是直接從外部資料庫讀取，例如Netezza （不支援索引的概念），透過 **[!UICONTROL Data loading (RDBMS)]** 活動，由產生的補充 **[!UICONTROL Split]** 活動將會不正確。

若要避免此問題，您可以拖放 **[!UICONTROL Enrichment]** 之前的活動 **[!UICONTROL Split]** 活動。 在 **[!UICONTROL Enrichment]** 活動，請檢查 **[!UICONTROL Keep all additional data from the main set]** 並在其他資料中指定您要用來設定篩選器的欄 **[!UICONTROL Split]** 活動。 來自入站轉變的資料 **[!UICONTROL Split]** 活動接著會儲存在Adobe Campaign伺服器上的暫時表格中，且補碼可以正確產生。

此 **[!UICONTROL Enable overlapping of output populations]** 選項可讓您管理屬於數個子集的母體：

* 如果未核取此方塊，分割活動會確定收件者無法出現在數個輸出轉變中，即使它符合數個子集的條件亦然。 它們會位於具有相符條件的第一個標籤的目標中。
* 核取此方塊後，如果收件者符合篩選條件，則可在數個子集中找到收件者。 Adobe Campaign建議使用專屬條件。

## 輸入引數 {#input-parameters}

* tableName
* 綱要

每個傳入事件都必須指定由這些引數定義的目標。

## 輸出引數 {#output-parameters}

* tableName
* 綱要
* recCount

這組三個值可識別排除所產生的目標。 **[!UICONTROL tableName]** 是記錄目標識別碼的資料表名稱， **[!UICONTROL schema]** 是母體的綱要（通常是nms：recipient）和 **[!UICONTROL recCount]** 是表格中的元素數。

與補充關聯的轉變有相同的引數。

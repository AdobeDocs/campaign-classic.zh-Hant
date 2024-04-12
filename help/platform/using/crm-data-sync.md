---
product: campaign
title: CRM Connectors資料同步
description: 管理Campaign與您的CRM之間的資料
feature: Microsoft CRM Integration, Salesforce Integration
exl-id: 7f9eda15-76e8-40a1-8302-004cea085778
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 1%

---

# 在Campaign和CRM之間同步資料 {#data-synchronization}



Adobe Campaign與CRM之間的資料同步會透過專用的工作流程活動執行： [CRM聯結器](../../workflow/using/crm-connector.md).

例如，若要將Microsoft Dynamics資料匯入Adobe Campaign，請建立下列型別的工作流程：

![](assets/crm_connectors_msdynamics_07.png)

此工作流程會透過Microsoft Dynamics匯入連絡人、將其與現有的Adobe Campaign資料同步、刪除重複的連絡人，以及更新Adobe Campaign資料庫。

此 **[!UICONTROL CRM Connector]** 活動必須設定為同步資料。

![](assets/crm_connectors_msdynamics_08.png)

使用此活動，您可以：

* 從CRM匯入 —  [瞭解更多](#importing-from-the-crm)
* 匯出至CRM - [瞭解更多](#exporting-to-the-crm)
* 匯入在CRM中刪除的物件 —  [瞭解更多](#importing-objects-deleted-in-the-crm)
* 刪除CRM中的物件 —  [瞭解更多](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

選取與您要設定同步的CRM相符的外部帳戶，然後選取要同步的物件：帳戶、商機、銷售機會、聯絡人等。

![](assets/crm_task_select_obj.png)

此活動的設定取決於要執行的程式。 各種設定詳見下文。

## 從CRM匯入 {#importing-from-the-crm}

若要透過Adobe Campaign中的CRM匯入資料，您需要建立以下型別的工作流程：

![](assets/crm_wf_import.png)

針對匯入活動， **[!UICONTROL CRM Connector]** 活動設定步驟如下：

1. 選取 **[!UICONTROL Import from the CRM]** 作業。
1. 前往 **[!UICONTROL Remote object]** 下拉式清單，並選取流程涉及的物件。 此物件與聯結器設定期間在Adobe Campaign中建立的其中一個表格一致。
1. 前往 **[!UICONTROL Remote fields]** 區段，並輸入要匯入的欄位。

   若要新增欄位，請按一下 **[!UICONTROL Add]** 按鈕，然後按一下 **[!UICONTROL Edit expression]** 圖示。

   ![](assets/crm_task_import_add_field.png)

   如有需要，可透過 **[!UICONTROL Conversion]** 欄。 中會詳細說明可能的轉換型別 [資料格式](#data-format).

   >[!IMPORTANT]
   >
   >CRM中記錄的識別碼在CRM和Adobe Campaign中連結物件時是強制性的。 在核准此方塊時自動新增。
   >
   >增量資料匯入也必須遵守CRM端的最後修改日期。

1. 您也可以根據需求篩選要匯入的資料。 若要這麼做，請按一下 **[!UICONTROL Edit the filter...]** 連結。

   在下列範例中，Adobe Campaign將僅匯入自2012年11月1日以來已記錄某些活動的聯絡人。

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >連結至資料篩選模式的限制詳見 [篩選資料](#filtering-data).

1. 此 **[!UICONTROL Use automatic index...]** 選項可讓您根據日期及上次修改時間，自動管理CRM與Adobe Campaign之間的增量物件同步。

   有關詳細資訊，請參閱 [變數管理](#variable-management).

### 管理變數 {#variable-management}

啟用 **[!UICONTROL Automatic index]** 僅收集自上次匯入後修改的物件的選項。

![](assets/crm_task_import_option.png)

依照預設，上次同步化的日期會儲存在組態視窗中指定的選項中： **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>此附註僅適用於類屬 **[!UICONTROL CRM Connector]** 活動。 對於其他CRM活動，此程式是自動的。
>
>此選項必須手動建立並填入 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. 它必須是文字選項，其值必須符合以下格式： **`yyyy/MM/dd hh:mm:ss`**.
> 
>您必須手動更新此選項才能進行進一步的匯入。

您可以指定要考慮的遠端CRM欄位，以識別最近的變更。

依預設，會使用下列欄位（依指定順序）：

* 若為Microsoft Dynamics： **修改**，
* 若為Salesforce.com： **LastModifiedDate**， **SystemModstamp**.

啟用 **[!UICONTROL Automatic index]** 選項會產生三個變數，可用於透過進行的同步工作流程。 **[!UICONTROL JavaScript code]** 輸入活動。 這些活動包括：

* **vars.crmOptionName**：代表包含上次匯入日期之選項的名稱。
* **vars.crmStartImport**：代表上次資料復原的開始日期（含）。
* **vars.crmEndDate**：代表上次資料復原的結束日期（已排除）。

  >[!NOTE]
  >
  >這些日期會以下列格式顯示： **`yyyy/MM/dd hh:mm:ss`**.

### 篩選資料 {#filtering-data}

為確保各種CRM的有效運作，需要使用下列規則建立篩選器：

* 每個篩選層級只能使用一種運運算元型別。
* 不支援AND NOT運運算元。
* 比較可能只涉及null值（&#39;is empty&#39;/&#39;is not empty&#39;型別）或數字。 這表示會評估值（右側欄），且此評估的結果必須是數字。 因此，不支援JOIN型別比較。
* 右側欄中包含的值是在JavaScript中評估。
* 不支援JOIN比較。
* 左側欄中的運算式必須是欄位。 不可由數個運算式、數字等組成。

例如，下列篩選條件對CRM匯入而言將無效，因為OR運運算元與AND運運算元位於相同層級：

* OR運運算元與AND運運算元位於相同層級
* 對文字字串執行比較

![](assets/crm_import_wrong_filter.png)

### 排序依據 {#order-by}

在Microsoft Dynamics和Salesforce.com中，您可以依照遞增或遞減順序來排序要匯入的遠端欄位。

若要這麼做，請按一下 **[!UICONTROL Order by]** 連結並新增欄至清單。

清單中的欄順序是排序順序：

![](assets/crm_import_order.png)

### 記錄識別 {#record-identification}

您可以使用工作流程中預先計算的母體，不必匯入CRM中包含（並可能經過篩選）的元素。

若要這麼做，請選取 **[!UICONTROL Use the population calculated upstream]** 選項並指定包含遠端識別碼的欄位。

然後選取您要匯入之入站母體的欄位，如下所示：

![](assets/crm_wf_import_calculated_population.png)

## 匯出至CRM {#exporting-to-the-crm}

將Adobe Campaign資料匯出至CRM可讓您將整個內容複製到CRM資料庫。

若要將資料匯出至CRM，您需要建立以下型別的工作流程：

![](assets/crm_export_diagram.png)

若要匯出，請將下列組態套用至 **[!UICONTROL CRM Connector]** 活動：

1. 選取 **[!UICONTROL Export to CRM]** 作業。
1. 前往 **[!UICONTROL Remote object]** 下拉式清單，並選取流程涉及的物件。 此物件與聯結器設定期間在Adobe Campaign中建立的其中一個表格一致。

   >[!IMPORTANT]
   >
   >的匯出函式 **[!UICONTROL CRM Connector]** 活動可以在CRM端插入或更新欄位。 若要在CRM中啟用欄位更新，您必須指定遠端表格的主索引鍵。 如果索引鍵遺失，則會插入資料（而非更新）。

1. 檢查 **[!UICONTROL Export in Batches]** 如果您需要更快速的匯出。

   ![](assets/crm_export_config_2.png)

1. 在 **[!UICONTROL Mapping]** 區段，按一下 **[!UICONTROL New]** 以指定要匯出的欄位及其在CRM中的對應。

   ![](assets/crm_export_config.png)

   若要新增欄位，請按一下 **[!UICONTROL Add]** 按鈕，然後按一下 **[!UICONTROL Edit expression]** 圖示。

   >[!NOTE]
   >
   >對於指定欄位，如果CRM端未定義相符專案，則無法更新值：會直接將值插入CRM。

   如有需要，可透過 **[!UICONTROL Conversion]** 欄。 中會詳細說明可能的轉換型別 [資料格式](#data-format).

   >[!NOTE]
   >
   >要匯出的記錄清單和匯出的結果會儲存在暫存檔案中，在工作流程完成或重新啟動之前，該暫存檔案保持可存取狀態。 這可讓您在出現錯誤時再次啟動程式，而不會出現多次匯出相同記錄或遺失資料的風險。

## 其他設定 {#additional-configurations}

### 資料格式 {#data-format}

將資料格式匯入或從CRM匯出時，您可以即時轉換資料格式。

要執行此操作，請選取要在相符欄中套用的轉換。

![](assets/crm_task_import.png)

此 **[!UICONTROL Default]** 模式會套用自動資料轉換，大部份情況下等於複製/貼上資料。 但是，會套用時區管理。

其他可能的轉換包括：

* **[!UICONTROL Date only]**：此模式會刪除日期+時間型別欄位。
* **[!UICONTROL Without time offset]**：此模式會取消在預設模式中套用的時區管理。
* **[!UICONTROL Copy/Paste]**：此模式會使用原始資料，例如字串（無轉換）。

### 錯誤處理 {#error-processing}

在資料匯入或匯出的架構中，您可以將特定程式套用至錯誤和拒絕。 若要這麼做，請選取 **[!UICONTROL Process rejects]** 和 **[!UICONTROL Process errors]** 中的選項 **[!UICONTROL Behavior]** 標籤。

![](assets/crm_export_options.png)

這些選項會放置相符的輸出轉變。

![](assets/crm_export_transitions.png)

然後放置與您要套用之程式相關的活動。

若要處理例項的錯誤，可以新增等待方塊並排程重試。

系統會收集拒絕專案及其錯誤代碼和相關訊息，這表示您可以設定拒絕追蹤以最佳化同步程式。

>[!NOTE]
>
>即使 **[!UICONTROL Process rejects]** 選項未啟用，則會針對每個已拒絕的欄產生警告，其中包含錯誤代碼和訊息。

此 **[!UICONTROL Reject]** 輸出轉變可讓您存取包含與錯誤訊息和程式碼相關之特定欄的輸出結構描述。 若為Salesforce.com，此欄為 **errorSymbol** （錯誤符號，與錯誤碼不同）， **errorMessage** （錯誤內容的說明）。

## 匯入CRM中刪除的物件 {#importing-objects-deleted-in-the-crm}

若要啟用廣泛的資料同步程式設定，您可以將CRM中刪除的物件匯入Adobe Campaign。

若要這麼做，請套用下列步驟：

1. 選取 **[!UICONTROL Import objects deleted in the CRM]** 作業。
1. 前往 **[!UICONTROL Remote object]** 下拉式清單，並選取流程涉及的物件。 此物件與聯結器設定期間在Adobe Campaign中建立的其中一個表格一致。
1. 指定要在中考慮的刪除期間 **[!UICONTROL Start date]** 和 **[!UICONTROL End date]** 欄位。 這些日期將包含在此期間中。

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >元素刪除期間必須符合CRM的特定限制。 這表示以Salesforce.com為例，超過30天前刪除的元素無法復原。

## 刪除 CRM 中的物件 {#deleting-objects-in-the-crm}

若要刪除CRM端的物件，您必須指定要刪除的遠端元素的主索引鍵。

![](assets/crm_delete_in_crm.png)

此 **[!UICONTROL Behavior]** 索引標籤可讓您啟用拒絕處理。 此選項會為產生第二個輸出轉變 **[!UICONTROL CRM connector]** 活動。 有關詳細資訊，請參閱 [處理時發生錯誤](#error-processing).

>[!NOTE]
>
>即使 **[!UICONTROL Process rejects]** 選項已停用，則會為每個已拒絕的欄產生警告。
>

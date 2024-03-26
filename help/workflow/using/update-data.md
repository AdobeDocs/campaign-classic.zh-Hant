---
product: campaign
title: 更新資料
description: 進一步瞭解更新資料工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows, Targeting Activity, Data Management
exl-id: 9f5735d2-73b8-469f-bc10-482c99cdd4a1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 2%

---

# 更新資料{#update-data}



一個 **更新資料**-type活動會大量更新資料庫中的欄位。

## 作業類型 {#operation-type}

此 **[!UICONTROL Operation type]** 欄位可讓您選擇要對資料庫中的資料執行的程式：

* **[!UICONTROL Insert or update]**：新增資料，或更新資料（如果已新增）。
* **[!UICONTROL Insert]**：僅新增資料。
* **[!UICONTROL Update]**：僅更新資料。
* **[!UICONTROL Update and merge collections]**：更新資料並選擇主要記錄，然後連結連結至此主要記錄中重複專案的元素。 然後，可刪除重複專案，而不建立孤立的附加元素。
* **[!UICONTROL Delete]**：刪除資料。

![](assets/s_advuser_update_data_1.png)

此 **[!UICONTROL Batch size]** 欄位可讓您選取要更新的入站轉變元素數量。 例如，如果您宣告500，則處理的前500筆記錄將會更新。

## 記錄識別 {#record-identification}

指定如何識別資料庫中的記錄：

* 如果資料專案與現有目標維度相關，請選取 **[!UICONTROL By directly using the targeting dimension]** 選項，並在 **[!UICONTROL Updated dimension]** 欄位。

  您可以使用以下顯示所選維度的欄位： **[!UICONTROL Edit this link]** 放大鏡按鈕。

* 否則，請指定一或多個連結，以便識別資料庫中的資料或直接使用調解金鑰。

![](assets/s_advuser_update_data_2.png)

## 選取要更新的欄位 {#selecting-the-fields-to-be-updated}

使用 **[!UICONTROL Automatically associate fields with the same name]** 選項，以便Adobe Campaign自動識別要更新的欄位。

![](assets/s_advuser_update_data_3b.png)

您也可以使用 **[!UICONTROL Insert]** 圖示以手動選取要更新的資料庫欄位。

![](assets/s_advuser_update_data_3.png)

選取要更新的所有欄位，並在必要時根據要執行的更新新增條件。 要執行此操作，請使用 **[!UICONTROL Taken into account if]** 欄。條件會逐一套用，並遵循清單中的順序。 使用右邊的箭頭來變更更新順序。

您可以多次使用相同的目的地欄位。

在 **[!UICONTROL Insert or update]** 作業，您可以個別或針對每個欄位選取要套用的行銷活動。 若要這麼做，請在 **[!UICONTROL Operation]** 欄。

![](assets/s_advuser_update_data_5.png)

此 **[!UICONTROL modifiedDate]**， **[!UICONTROL modifiedBy]**， **[!UICONTROL createdDate]** 和 **[!UICONTROL createdBy]** 欄位會在資料更新期間自動更新，除非在欄位更新表中特別設定其管理模式。

僅對包含至少一個差異的記錄執行記錄更新。 如果值相同，則不會執行更新。

此 **[!UICONTROL Advanced parameters]** 連結可讓您指定處理資料更新及管理重複專案的其他選項。 您也可以：

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**. 此選項依預設會自動核取。
* **[!UICONTROL Update all columns with matching names]**.
* 指定考慮來源元素的條件，在 **[!UICONTROL Enabled if]** 欄位。
* 使用運算式指定考慮重複專案的條件。 如果您檢查 **[!UICONTROL Ignore records which concern the same target]** 選項，則只會考慮運算式清單中的第一個。

**[!UICONTROL Generate an outbound transition]**

建立將在執行結束時啟用的出站轉變。 更新通常表示目標工作流程結束，因此預設不會啟用選項。

**[!UICONTROL Generate an outbound transition for the rejects]**

建立外站轉變，其中包含更新後未正確處理的記錄（例如，如果有重複記錄）。 更新通常會標籤目標工作流程的結尾，因此預設不會啟用選項。

## 更新及合併集合 {#updating-and-merging-collections}

更新資料及合併集合可讓您使用一或多個次要記錄的資料，更新記錄中包含的資料，以便在需要時僅保留一項。 這些更新由一組規則管理。

>[!NOTE]
>
>此選項也可讓您從工作流程工作表(targetWorkflow)、傳送(targetDelivery)和清單(targetList)處理次要記錄的參考。 如有需要，這些連結會出現在您選取欄位和集合的清單中。

1. 選取 **[!UICONTROL Update and merge collections]** 作業。

   ![](assets/update_and_merge_collections1.png)

1. 選取連結的優先順序。 這可讓您識別主要記錄。 可用的連結會因入站轉變而異。

   ![](assets/update_and_merge_collections2.png)

1. 選取要移至主要記錄的集合與要更新的欄位。

   輸入一或多個次要記錄識別後套用至這些記錄的規則。 若要這麼做，您可以使用運算式產生器。 如需詳細資訊，請參閱此 [區段](../../platform/using/defining-filter-conditions.md#building-expressions). 例如，指定這是必須保留的所有不同記錄中最近更新的值。

   然後輸入規則要考慮的條件。

   最後，指定要執行的更新型別。 例如，您可以選擇在更新資料之後刪除次要記錄。

   例如，您可以設定合併包含異質性資料（例如收件者的訂閱清單）的集合。 您也可以使用規則從次要記錄訂閱建立新的訂閱歷史記錄，甚至可以將訂閱清單從次要記錄移至主要記錄。

1. 透過選取「 」，指定您要處理次要記錄的順序 **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**.

   ![](assets/update_and_merge_collections3.png)

如果定義的規則適用，次要記錄的資料會與主要記錄相關聯。 根據所選的更新型別，可刪除次要記錄。

## 範例：在擴充後更新資料 {#example--update-data-following-an-enrichment}

此 [步驟2：將擴充資料寫入「購買」表格](creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) 使用案例中詳細說明建立回顧清單的區段，提供擴充活動後資料更新的範例。

## 輸入引數 {#input-parameters}

* tableName
* 綱要

每個傳入事件都必須指定由這些引數定義的目標。

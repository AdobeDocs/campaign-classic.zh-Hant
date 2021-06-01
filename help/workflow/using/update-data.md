---
product: campaign
title: 更新資料
description: 深入了解更新資料工作流程活動
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 9f5735d2-73b8-469f-bc10-482c99cdd4a1
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 2%

---

# 更新資料{#update-data}

**更新資料**&#x200B;類型活動執行對資料庫中欄位的成批更新。

## 操作類型{#operation-type}

**[!UICONTROL Operation type]**&#x200B;欄位可讓您選擇要對資料庫中的資料執行的程式：

* **[!UICONTROL Insert or update]**:新增資料或更新（如果已新增）。
* **[!UICONTROL Insert]**:僅添加資料。
* **[!UICONTROL Update]**:僅更新資料。
* **[!UICONTROL Update and merge collections]**:更新資料並選擇主記錄，然後連結到此主記錄中重複項的元素。然後，可以刪除重複項，而不建立孤立的附加元素。
* **[!UICONTROL Delete]**：刪除資料。

![](assets/s_advuser_update_data_1.png)

**[!UICONTROL Batch size]**&#x200B;欄位可讓您選取要更新的入站轉變元素數量。 例如，如果您指出500，則處理的前500筆記錄將會更新。

## 記錄標識{#record-identification}

指定如何標識資料庫中的記錄：

* 如果資料項與現有目標維相關，請選擇&#x200B;**[!UICONTROL By directly using the targeting dimension]**&#x200B;選項，然後在&#x200B;**[!UICONTROL Updated dimension]**&#x200B;欄位中選擇它。

   您可以使用&#x200B;**[!UICONTROL Edit this link]**&#x200B;放大鏡按鈕顯示所選維度的欄位。

* 否則，指定一個或多個連結，這些連結將啟用資料庫中資料的標識或直接使用協調密鑰。

![](assets/s_advuser_update_data_2.png)

## 選擇要更新的欄位{#selecting-the-fields-to-be-updated}

使用&#x200B;**[!UICONTROL Automatically associate fields with the same name]**&#x200B;選項，讓Adobe Campaign自動識別要更新的欄位。

![](assets/s_advuser_update_data_3b.png)

您也可以使用&#x200B;**[!UICONTROL Insert]**&#x200B;圖示來手動選取要更新的資料庫欄位。

![](assets/s_advuser_update_data_3.png)

選取要更新的所有欄位，並視需要新增條件，視要執行更新而定。 要執行此操作，請使用 **[!UICONTROL Taken into account if]** 欄。條件會逐一套用，並與清單中的順序一致。 使用右側的箭頭來變更更新順序。

您可以使用相同的目的地欄位多次。

在&#x200B;**[!UICONTROL Insert or update]**&#x200B;操作中，您可以選取個別或針對每個欄位套用的促銷活動。 要執行此操作，請在&#x200B;**[!UICONTROL Operation]**&#x200B;欄中選取所需的值。

![](assets/s_advuser_update_data_5.png)

除非在欄位更新表中特別配置了&#x200B;**[!UICONTROL modifiedDate]**、**[!UICONTROL modifiedBy]**、**[!UICONTROL createdDate]**&#x200B;和&#x200B;**[!UICONTROL createdBy]**&#x200B;欄位，否則在資料更新期間會自動更新它們。

僅對包含至少一個差異的記錄執行記錄更新。 如果值相同，則不執行更新。

**[!UICONTROL Advanced parameters]**&#x200B;連結可讓您指定其他選項來處理更新資料及管理重複項目。 您也可以：

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**.預設會自動勾選此選項。
* **[!UICONTROL Update all columns with matching names]**.
* 在&#x200B;**[!UICONTROL Enabled if]**&#x200B;欄位中使用運算式指定考慮源元素的條件。
* 使用運算式指定考慮重複項的條件。 如果勾選&#x200B;**[!UICONTROL Ignore records which concern the same target]**&#x200B;選項，則只會考慮運算式清單中的第一個。

**[!UICONTROL Generate an outbound transition]**

建立將在執行結束時啟動的出站轉變。 更新通常代表目標工作流程結束，因此預設不會啟用選項。

**[!UICONTROL Generate an outbound transition for the rejects]**

建立出站轉變，其中包含更新後未正確處理的記錄（例如，如果有重複記錄）。 更新通常會標籤目標工作流程的結尾，因此預設不會啟動選項。

## 更新和合併集合{#updating-and-merging-collections}

更新資料並合併集合可讓您使用來自一或多個次要記錄的資料來更新記錄中包含的資料，以便只保留一個記錄（如果您想要的話）。 這些更新由一組規則管理。

>[!NOTE]
>
>此選項也可讓您處理來自工作流程工作表(targetWorkflow)、傳送(targetDelivery)和清單(targetList)的次要記錄參考。 如果需要，這些連結會出現在您選取欄位和集合的清單中。

1. 選擇&#x200B;**[!UICONTROL Update and merge collections]**&#x200B;操作。

   ![](assets/update_and_merge_collections1.png)

1. 選取連結的優先順序。 這可讓您識別主要記錄。 可用的連結會根據入站轉變而有所不同。

   ![](assets/update_and_merge_collections2.png)

1. 選擇要移至主要記錄的集合和要更新的欄位。

   輸入一或多個輔助記錄被標識後應用於這些記錄的規則。 若要這麼做，您可以使用運算式產生器。 如需詳細資訊，請參閱本[區段](../../platform/using/defining-filter-conditions.md#building-expressions)。例如，指定這是必須保留的所有不同記錄中最近更新的值。

   然後輸入要考慮規則的條件。

   最後，指定要執行的更新類型。 例如，您可以在更新資料後選擇刪除次要記錄。

   例如，您可以設定包含異類資料的集合合併，例如收件者的訂閱清單。 使用規則，您還可以從輔助記錄訂閱建立新訂閱歷史記錄，甚至將訂閱清單從輔助記錄移動到主記錄。

1. 通過選擇&#x200B;**[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**，指定要處理次記錄的順序。

   ![](assets/update_and_merge_collections3.png)

如果定義的規則適用，則輔助記錄的資料與主記錄相關聯。 根據所選更新的類型，可以刪除次記錄。

## 範例：在擴充{#example--update-data-following-an-enrichment}後更新資料

[步驟2:將擴充資料寫入使用案例的「購買」表](../../workflow/using/creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table)區段，其中詳細說明如何建立重新命名清單，提供擴充活動後資料更新的範例。

## 輸入參數{#input-parameters}

* tableName
* 綱要

每個入站事件都必須指定由這些參數定義的目標。

---
solution: Campaign Classic
product: campaign
title: 更新資料
description: 進一步瞭解「更新資料工作流程」活動
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 2%

---


# 更新資料{#update-data}

**更新資料**&#x200B;類型活動執行資料庫中欄位的大量更新。

## 操作類型{#operation-type}

**[!UICONTROL Operation type]**&#x200B;欄位允許您選擇要對資料庫中的資料執行的進程：

* **[!UICONTROL Insert or update]**:新增資料或更新資料（如果已新增）。
* **[!UICONTROL Insert]**:只新增資料。
* **[!UICONTROL Update]**:僅更新資料。
* **[!UICONTROL Update and merge collections]**:更新資料並選擇主要記錄，然後連結連結至此主要記錄中之重複項目的元素。然後可刪除重複項，而不需建立孤立附加的元素。
* **[!UICONTROL Delete]**：刪除資料。

![](assets/s_advuser_update_data_1.png)

**[!UICONTROL Batch size]**&#x200B;欄位可讓您選取要更新的傳入轉換元素數。 例如，如果您陳述500，則處理的前500個記錄將會更新。

## 記錄標識{#record-identification}

指定如何標識資料庫中的記錄：

* 如果資料條目與現有目標維相關，請選擇&#x200B;**[!UICONTROL By directly using the targeting dimension]**&#x200B;選項，然後在&#x200B;**[!UICONTROL Updated dimension]**&#x200B;欄位中選擇它。

   您可以使用&#x200B;**[!UICONTROL Edit this link]**&#x200B;放大鏡按鈕來顯示選取維度的欄位。

* 否則，請指定一個或多個連結，以便識別資料庫中的資料或直接使用協調密鑰。

![](assets/s_advuser_update_data_2.png)

## 選擇要更新的欄位{#selecting-the-fields-to-be-updated}

請使用&#x200B;**[!UICONTROL Automatically associate fields with the same name]**&#x200B;選項，讓Adobe Campaign自動識別要更新的欄位。

![](assets/s_advuser_update_data_3b.png)

您也可以使用&#x200B;**[!UICONTROL Insert]**&#x200B;表徵圖手動選擇要更新的資料庫欄位。

![](assets/s_advuser_update_data_3.png)

選擇要更新的所有欄位，並根據需要添加條件，具體取決於要執行的更新。 要執行此操作，請使用 **[!UICONTROL Taken into account if]** 欄。條件會逐一套用，並符合清單中的順序。 使用右邊的箭頭來變更更新順序。

您可以多次使用相同的目標欄位。

在&#x200B;**[!UICONTROL Insert or update]**&#x200B;操作中，您可以選擇要單獨應用的促銷活動或為每個欄位應用促銷活動。 若要這麼做，請在&#x200B;**[!UICONTROL Operation]**&#x200B;欄中選取所需的值。

![](assets/s_advuser_update_data_5.png)

**[!UICONTROL modifiedDate]**、**[!UICONTROL modifiedBy]**、**[!UICONTROL createdDate]**&#x200B;和&#x200B;**[!UICONTROL createdBy]**&#x200B;欄位會在資料更新期間自動更新，除非在欄位更新表格中特別設定其管理模式。

記錄更新僅對包含至少一個差異的記錄執行。 如果值相同，則不執行更新。

**[!UICONTROL Advanced parameters]**&#x200B;連結可讓您指定其他選項來處理資料更新以及管理重複項目。 您也可以：

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**.預設會自動勾選此選項。
* **[!UICONTROL Update all columns with matching names]**.
* 在&#x200B;**[!UICONTROL Enabled if]**&#x200B;欄位中指定考慮使用運算式之來源元素的條件。
* 指定使用運算式來考慮複製的條件。 如果您勾選&#x200B;**[!UICONTROL Ignore records which concern the same target]**&#x200B;選項，則只會考慮運算式清單中的第一個選項。

**[!UICONTROL Generate an outbound transition]**

建立將在執行結束時激活的出站轉移。 更新通常表示定位工作流程的結束，因此預設不會啟動選項。

**[!UICONTROL Generate an outbound transition for the rejects]**

建立包含更新後未正確處理的記錄（例如，如果有重複記錄）的出站轉移。 更新通常會標籤定位工作流程的結束，因此預設不會啟動選項。

## 更新和合併系列{#updating-and-merging-collections}

更新資料並合併集合可讓您使用來自一或多個次要記錄的資料來更新記錄中所含的資料，以便在需要時保留一個記錄。 這些更新由一組規則管理。

>[!NOTE]
>
>此選項也可讓您處理來自工作流程工作表(targetWorkflow)、傳送(targetDelivery)和清單(targetList)的次要記錄參考。 如有需要，這些連結會出現在您選取欄位和系列的清單中。

1. 選擇&#x200B;**[!UICONTROL Update and merge collections]**&#x200B;操作。

   ![](assets/update_and_merge_collections1.png)

1. 選取連結的優先順序。 這可讓您識別主要記錄。 可用的連結會依傳入的轉場而有所不同。

   ![](assets/update_and_merge_collections2.png)

1. 選擇要移動至主要記錄的系列和要更新的欄位。

   輸入規則，這些規則應用於這些記錄一次或多個輔助記錄。 若要這麼做，您可以使用運算式產生器。 如需詳細資訊，請參閱本[區段](../../platform/using/defining-filter-conditions.md#building-expressions)。例如，指定它是所有必須保存的不同記錄中最近更新的值。

   然後輸入要考慮規則的條件。

   最後，指定要執行的更新類型。 例如，您可以選擇在更新資料後刪除次要記錄。

   例如，您可以設定包含異構資料（例如收件者的訂閱清單）之集合的合併。 使用規則，您也可以從次要記錄訂閱建立新的訂閱記錄，甚至將訂閱清單從次要記錄移至主要記錄。

1. 通過選擇&#x200B;**[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**，指定要處理次記錄的順序。

   ![](assets/update_and_merge_collections3.png)

如果定義的規則適用，輔助記錄的資料將與主記錄關聯。 根據選擇的更新類型，可以刪除次記錄。

## 範例：在擴充{#example--update-data-following-an-enrichment}後更新資料

[步驟2:將富集資料寫入使用案例的「購買」表](../../workflow/using/creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table)部分，其中詳細資訊建立重新應用清單提供了富集活動後的資料更新示例。

## 輸入參數{#input-parameters}

* tableName
* 架構

每個傳入事件都必須指定由這些參數定義的目標。

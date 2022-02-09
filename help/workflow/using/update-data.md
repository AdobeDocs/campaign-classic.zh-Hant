---
product: campaign
title: 更新資料
description: 瞭解有關更新資料工作流活動的詳細資訊
feature: Data Management
exl-id: 9f5735d2-73b8-469f-bc10-482c99cdd4a1
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 2%

---

# 更新資料{#update-data}

![](../../assets/common.svg)

安 **更新資料**-type活動對資料庫中的欄位執行成批更新。

## 操作類型 {#operation-type}

的 **[!UICONTROL Operation type]** 欄位中，您可以選擇要對資料庫中的資料執行的進程：

* **[!UICONTROL Insert or update]**:添加資料或更新（如果已添加）。
* **[!UICONTROL Insert]**:只添加資料。
* **[!UICONTROL Update]**:只更新資料。
* **[!UICONTROL Update and merge collections]**:更新資料並選擇主記錄，然後連結連結到此主記錄中重複項的元素。 然後，可以刪除重複項，而不建立孤立附加元素。
* **[!UICONTROL Delete]**：刪除資料。

![](assets/s_advuser_update_data_1.png)

的 **[!UICONTROL Batch size]** 欄位，用於選擇要更新的入站轉換元素的數量。 例如，如果您聲明500，則處理的前500條記錄將更新。

## 記錄標識 {#record-identification}

指定如何標識資料庫中的記錄：

* 如果資料條目與現有目標維相關，請選擇 **[!UICONTROL By directly using the targeting dimension]** 的 **[!UICONTROL Updated dimension]** 的子菜單。

   可以使用 **[!UICONTROL Edit this link]** 放大鏡按鈕。

* 否則，指定一個或多個連結，這些連結將允許標識資料庫中的資料或直接使用協調鍵。

![](assets/s_advuser_update_data_2.png)

## 選擇要更新的欄位 {#selecting-the-fields-to-be-updated}

使用 **[!UICONTROL Automatically associate fields with the same name]** 的子菜單。

![](assets/s_advuser_update_data_3b.png)

您還可以使用 **[!UICONTROL Insert]** 表徵圖，以手動選擇要更新的資料庫欄位。

![](assets/s_advuser_update_data_3.png)

選擇要更新的所有欄位，並根據要執行的更新添加條件（如有必要）。 要執行此操作，請使用 **[!UICONTROL Taken into account if]** 欄。條件依次應用，並符合清單中的順序。 使用右側的箭頭更改更新順序。

可以多次使用同一目標欄位。

在 **[!UICONTROL Insert or update]** 工序中，您可以選擇要應用的市場活動（單獨或為每個欄位）。 為此，請在 **[!UICONTROL Operation]** 的雙曲餘切值。

![](assets/s_advuser_update_data_5.png)

的 **[!UICONTROL modifiedDate]**。 **[!UICONTROL modifiedBy]**。 **[!UICONTROL createdDate]** 和 **[!UICONTROL createdBy]** 欄位在資料更新期間自動更新，除非在欄位更新表中專門配置了其管理模式。

僅對包含至少一個差異的記錄執行記錄更新。 如果值相同，則不執行更新。

的 **[!UICONTROL Advanced parameters]** 連結允許您指定其他選項來處理更新資料和管理重複資料。 您也可以：

* **[!UICONTROL Disable automatic key management]**。
* **[!UICONTROL Disable audit]**。
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**。 預設情況下會自動選中此選項。
* **[!UICONTROL Update all columns with matching names]**。
* 指定使用中的表達式考慮源元素的條件 **[!UICONTROL Enabled if]** 的子菜單。
* 使用表達式指定考慮重複的條件。 如果您檢查 **[!UICONTROL Ignore records which concern the same target]** 選項，將只考慮表達式清單中的第一個。

**[!UICONTROL Generate an outbound transition]**

建立將在執行結束時激活的出站轉換。 更新通常表示目標工作流的結束，因此預設情況下不會激活該選項。

**[!UICONTROL Generate an outbound transition for the rejects]**

建立包含更新後未正確處理的記錄（例如，如果有重複記錄）的出站轉移。 更新通常標籤目標工作流的結束，因此預設情況下不會激活該選項。

## 更新和合併集合 {#updating-and-merging-collections}

更新資料和合併集合允許您通過使用來自一個或多個輔助記錄的資料來更新記錄中包含的資料，目的是在需要時僅保留一個。 這些更新由一組規則管理。

>[!NOTE]
>
>此選項還允許您處理對工作流工作表(targetWorkflow)、交貨(targetDelivery)和清單(targetList)中輔助記錄的引用。 如果需要，這些連結將出現在您選擇欄位和集合的清單中。

1. 選擇 **[!UICONTROL Update and merge collections]** 的下界。

   ![](assets/update_and_merge_collections1.png)

1. 選擇連結的優先順序順序。 這允許您標識主記錄。 可用連結因入站轉換而異。

   ![](assets/update_and_merge_collections2.png)

1. 選擇要移動到主要記錄的集合和要更新的欄位。

   輸入規則，這些規則應用於這些規則，以標識一個或多個輔助記錄。 為此，可使用表達式生成器。 如需詳細資訊，請參閱本[區段](../../platform/using/defining-filter-conditions.md#building-expressions)。例如，通過指定它是所有必須保留的不同記錄中最近更新的值。

   然後輸入要考慮規則的條件。

   最後，指定要執行的更新類型。 例如，您可以選擇在更新資料後刪除輔助記錄。

   例如，可以配置包含異構資料的集合的合併，如收件人的訂閱清單。 使用規則，您還可以從輔助記錄訂閱建立新訂閱歷史記錄，甚至可以將訂閱清單從輔助記錄移動到主記錄。

1. 通過選擇 **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**。

   ![](assets/update_and_merge_collections3.png)

如果定義的規則適用，輔助記錄的資料將與主記錄關聯。 根據所選的更新類型，可刪除次記錄。

## 示例：在富集後更新資料 {#example--update-data-following-an-enrichment}

的 [步驟2:將增強的資料寫入「採購」表](creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) 「詳細資訊建立recap清單」(recap list)的使用案例部分提供了一個示例，說明在富集活動之後進行資料更新。

## 輸入參數 {#input-parameters}

* 表名
* 架構

每個入站事件都必須指定由這些參數定義的目標。

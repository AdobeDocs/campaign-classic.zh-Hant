---
product: campaign
title: 關於自訂收件者表格
description: 關於自訂收件者表格
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Custom Resources
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 2%

---

# 使用自訂收件者表格{#about-custom-recipient-table}



本節詳細說明使用自訂（或外部）收件者表格的原則。

依預設，Adobe Campaign提供內建的收件者表格，現成可用的函式和程式會連結至該表格。 內建的收件者表格有許多預先定義的欄位和表格，可使用擴充功能表格輕鬆擴充這些欄位和表格。

如果此擴充功能方法可提供擴充表格的良好彈性，便無法減少表格中的欄位或連結數。 使用非標準表格（或「外部收件者表格」）可提供更大彈性，但在實作時需要採取某些預防措施。

此功能可讓Adobe Campaign處理來自外部資料庫的資料：此資料將用作一組用於傳送的設定檔。 實作此程式需要多個可能根據使用者端需求而相關的精確度。 例如：

* 沒有與Adobe Campaign資料庫之間的更新資料流：您可以透過裝載此資料表的資料庫引擎直接更新此資料表的資料。
* 在現有資料庫上運作的處理程式中沒有變更。
* 使用具有非標準結構的設定檔資料庫：使用單一執行個體，可傳送至以各種結構儲存在各種表格中的設定檔。
* 更新Adobe Campaign資料庫時不需要變更或維護。
* 如果您不需要大部分的表格欄位，或資料庫範本未以收件者為中心，內建的收件者表格就毫無用處。
* 為了有效率，如果您有大量設定檔，則需要包含少量欄位的表格。 此特定案例的內建收件者表格有太多欄位。

本節說明可讓您對應Adobe Campaign中現有表格的要點，以及根據任何表格執行傳送時套用的設定。 最後，說明如何提供使用者查詢介面，使其如同內建收件者表格所提供的介面一樣實用。 若要瞭解本節提供的資料，您必須具備熒幕和結構描述設計原則的良好知識。

## Recommendations和限制 {#recommendations-and-limitations}

使用自訂收件者表格有下列限制：

* Adobe Campaign不支援多個收件者結構描述，也稱為目標定位結構描述，連結到相同的broadlog和/或trackinglog結構描述。 否則，這可能會導致後續的資料協調異常。

   下圖詳細說明每個自訂收件者綱要所需的關聯式結構：
   ![](assets/custom_recipient_limitation.png)

   我們建議：

   * 專用於 **[!UICONTROL nms:BroadLogRcp]** 和 **[!UICONTROL nms:TrackingLogRcp]** 現成可用的結構描述 **[!UICONTROL nms:Recipientschema]**. 這兩個記錄檔表格不應連結至任何其他自訂收件者表格。
   * 為每個新的自訂收件者綱要定義專用的自訂broadlog和trackinglog綱要。 這在設定目標對應時可自動完成，請參閱 [目標對應](../../configuration/using/target-mapping.md).

* 您無法使用標準 **[!UICONTROL Services and Subscriptions]** 在產品中提供。

   這表示整體作業詳述於 [本節](../../delivery/using/managing-subscriptions.md) 不適用。

* 連結與 **[!UICONTROL visitor]** 表格無法運作。

   因此，若要使用 **[!UICONTROL Social Marketing]** 模組您必須設定儲存步驟以參考正確的表格。

   同樣地，使用轉介函式時，必須採用標準的初始訊息傳輸範本。

* 您無法在清單中手動新增設定檔。

   因此，此程式詳述於 [本節](../../platform/using/creating-and-managing-lists.md) 若沒有其他設定，即不適用。

   >[!NOTE]
   >
   >您仍然可以使用工作流程建立收件者清單。 有關詳細資訊，請參閱 [使用工作流程建立設定檔清單](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

我們也建議檢查不同的現成可用設定中使用的預設值：根據使用的功能，必須進行一些調整。

例如：

* 某些標準報告，尤其是由提供的報告 **互動** 和 **行動應用計畫** 必須重新開發。 請參閱 [管理報告](../../configuration/using/managing-reports.md) 區段。
* 某些工作流程活動的預設設定會參考標準收件者表格(**[!UICONTROL nms:recipient]**)：在用於外部收件者表格時，必須變更這些設定。 請參閱 [管理工作流程](../../configuration/using/managing-workflows.md) 區段。
* 標準 **[!UICONTROL Unsubscription link]** 必須調整個人化區塊。
* 必須修改標準傳遞範本的目標對應。
* V4表單與外部收件者表格不相容：您必須使用Web應用程式。

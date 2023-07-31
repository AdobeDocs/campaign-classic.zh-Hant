---
product: campaign
title: 關於自訂收件者表格
description: 關於自訂收件者表格
feature: Configuration, Custom Resources
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 2%

---

# 使用自訂收件者表格{#about-custom-recipient-table}



本節詳細說明使用自訂（或外部）收件者表格的原則。

依預設，Adobe Campaign提供內建的收件者表格，內建函式和程式與之連結。 內建的收件者表格有許多預先定義的欄位和表格，可使用擴充功能表格輕鬆擴充這些欄位和表格。

如果此擴充方法可提供良好的彈性來擴充表格，則不允許減少表格中的欄位或連結數量。 使用非標準表格（或「外部收件者表格」）可提供更大的彈性，但在實作時需採取某些預防措施。

此功能可讓Adobe Campaign處理來自外部資料庫的資料：此資料將用作傳遞的一組設定檔。 實作此程式需要多個精確度，可能會根據使用者端的需求而相關。 例如：

* 沒有傳入Adobe Campaign資料庫的更新串流：此資料表的資料可以直接透過裝載它的資料庫引擎更新。
* 在操作現有資料庫的處理序中沒有變更。
* 使用具有非標準結構的設定檔資料庫：使用單一執行個體，將內容傳送到儲存在具有各種結構的各種表格中的設定檔的可能性。
* 更新Adobe Campaign資料庫時不需要變更或維護。
* 如果您不需要大部分的表格欄位，或資料庫範本未以收件者為中心，內建的收件者表格就毫無用處。
* 為了提高效率，如果您有大量設定檔，則需要包含幾個欄位的表格。 內建的收件者表格中有太多欄位適用於此特定案例。

本節說明可讓您對應Adobe Campaign中現有表格的要點，以及套用以根據任何表格執行傳送的設定。 最後，說明如何提供使用者查詢介面，使其如同內建收件者表格所提供的介面一樣實用。 若要瞭解本節中介紹的材料，您必須精通熒幕和結構描述設計的原則。

## Recommendations和限制 {#recommendations-and-limitations}

使用自訂收件者表格有下列限制：

* Adobe Campaign不支援多個收件者結構描述（也稱為目標定位結構描述），連結至相同的broadlog和/或trackinglog結構描述。 否則，這可能會導致之後資料協調出現異常。

  下圖詳細說明每個自訂收件者綱要所需的關聯式結構：
  ![](assets/custom_recipient_limitation.png)

  我們建議：

   * 專用於 **[!UICONTROL nms:BroadLogRcp]** 和 **[!UICONTROL nms:TrackingLogRcp]** 使用現成可用的結構描述 **[!UICONTROL nms:Recipientschema]**. 這兩個記錄檔表格不應連結至任何其他自訂收件者表格。
   * 為每個新的自訂收件者綱要定義專用的自訂broadlog和trackinglog綱要。 設定目標對應時，可自動完成此作業。請參閱 [目標對應](../../configuration/using/target-mapping.md).

* 您無法使用標準 **[!UICONTROL Services and Subscriptions]** 在產品中提供。

  這表示中詳述的整體作業 [本節](../../delivery/using/managing-subscriptions.md) 不適用。

* 連結與 **[!UICONTROL visitor]** 表格無法運作。

  因此，若要使用 **[!UICONTROL Social Marketing]** 模組您必須設定儲存步驟以參考正確的表格。

  同樣地，使用轉介函式時，必須採用標準的初始訊息傳輸範本。

* 您無法在清單中手動新增設定檔。

  因此，中詳述的程式 [本節](../../platform/using/creating-and-managing-lists.md) 若沒有其他設定，即不適用。

  >[!NOTE]
  >
  >您仍然可以使用工作流程建立收件者清單。 有關詳細資訊，請參閱 [使用工作流程建立設定檔清單](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

我們也建議檢查不同的現成可用設定中使用的預設值：根據使用的功能，必須進行一些調整。

例如：

* 某些標準報告，尤其是由提供的報告 **互動** 和 **行動應用計畫** 必須重新開發。 請參閱 [管理報表](../../configuration/using/managing-reports.md) 區段。
* 某些工作流程活動的預設設定會參考標準收件者表格(**[!UICONTROL nms:recipient]**)：這些設定在用於外部收件者表格時必須變更。 請參閱 [管理工作流程](../../configuration/using/managing-workflows.md) 區段。
* 標準 **[!UICONTROL Unsubscription link]** 必須調整個人化區塊。
* 必須修改標準傳遞範本的目標對應。
* V4表單與外部收件者表格不相容：您必須使用Web應用程式。
